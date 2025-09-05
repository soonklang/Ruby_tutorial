# Ruby Class Variables
ก่อนที่เราจะไปทำความรู้จักกับ **Ruby Class Variables** ว่าคืออะไร เรามาทำความรู้จักกับภาษา **Ruby** กันก่อน

---

## Ruby language คือ 

- **ภาษาระดับสูง (High-level):** Ruby เป็นภาษาระดับสูง เพราะโค้ดมีลักษณะคล้ายภาษาอังกฤษปกติ อ่าน เขียน เข้าใจได้ง่าย  
- **ภาษาโปรแกรมเชิงวัตถุ (Object-Oriented Programming Language):** Ruby อนุญาตให้ผู้ใช้จัดการกับโครงสร้างข้อมูลที่เรียกว่า *objects* เพื่อสร้างและรันโปรแกรม  
- **ใช้งานง่าย (Easy to use):** Ruby ถูกออกแบบโดย **Yukihiro Matsumoto (Matz)** ในปี 1995 จุดประสงค์คือสร้างภาษาที่ให้ความสำคัญกับ “ความต้องการของมนุษย์มากกว่าของคอมพิวเตอร์”  

---

## ความรู้เสริม: Instance คืออะไร?

- **Instance** = object ที่ถูกสร้างจาก class ที่เรานิยามเอง  
- การสร้าง object จาก class ใช้ `.new` → object นั้นคือ instance ของ class นั้น  

### Code ตัวอย่างว่า Instace คืออะไร
```ruby
class BankAccount
  def initialize(balance)
    @balance = balance
  end
end

acc1 = BankAccount.new(1000)  # acc1 คือ instance ของ BankAccount
acc2 = BankAccount.new(2000)  # acc2 ก็เป็น instance ของ BankAccount
```
---

## Ruby Class Variables คืออะไร ?

- Class Variable (ตัวแปรคลาส) ใน Ruby คือ **ตัวแปรที่ถูกแชร์ร่วมกันในทุกๆ instance** ของ class เดียวกัน
- เขียนด้วยสัญลักษณ์ `@@` นำหน้า เช่น `@@var`
- การเปลี่ยนแปลง class variables ( `@@var` ) ใน instance หนึ่งของ class **จึงส่งผลต่อ instance ทั้งหมดของคลาสนั้น**
- ตัวแปรคลาส  (Class Variable) สามารถเข้าถึงได้จากClass นั้นเอง อินสแตนซ์ของคลาส และ sub class
- มีการถูกแชร์ร่วมกัน ในลำดับชั้นการสืบทอดทั้งหมดด้วย เช่น sub class ต่างๆ


---

### ตัวอย่างการใช้งาน Class Variables ใน Ruby

```ruby
class BankAccount
  @@interest_rate = 0.05   # class variable

  def initialize(name, balance)
    @name = name           # instance variable
    @balance = balance     # instance variable
  end

  def self.set_rate(new_rate)
    @@interest_rate = new_rate
  end

  def show
    puts "#{@name} has balance #{@balance}, interest rate = #{@@interest_rate}"
  end
end

# การสร้าง object
a = BankAccount.new("Earth", 1000)
b = BankAccount.new("Del", 2000)

# การเรียกเมธอด instance
a.show
b.show

# การเรียกเมธอด class
BankAccount.set_rate(0.1)

# แสดงผลใหม่หลังเปลี่ยนค่า
a.show
b.show
```

---

### Output:

```
Earth has balance 1000, interest rate = 0.05
Del has balance 2000, interest rate = 0.05
Earth has balance 1000, interest rate = 0.1
Del has balance 2000, interest rate = 0.1
```

---

## อธิบายทีละบรรทัด

### ส่วนประกาศ class  
```ruby
class BankAccount
    @@interest_rate = 0.05   # class variable
```
- `class` = คีย์เวิร์ดประกาศคลาส  
- คล้ายกับ `class BankAccount { ... }` ใน Java  

---

### Class variable  
```ruby
@@interest_rate = 0.05
```
- `@@interest_rate` = class variable  
- ค่าเริ่มต้น `0.05` = ดอกเบี้ย 5%  
- ทุก object จะเห็นค่าเดียวกัน  

---

### เมธอด initialize (constructor)  
```ruby
def initialize(name, balance)
  @name = name          # instance variable
  @balance = balance    # instance variable
end
```
- `def initialize(...)` = constructor ของ Ruby (เหมือน `public BankAccount(...)` ใน Java)

- `@name` และ `@balance` → instance variable (ของอ็อบเจ็กต์นั้นๆ)
    - @ ตัวเดียว = ของ object
    - เก็บชื่อและยอดเงินของเจ้าของบัญชี

---

### เมธอด class (static method)  
```ruby
def self.set_rate(new_rate)
  @@interest_rate = new_rate
end
```
- `def self.set_rate(...)` → การเขียน `self. ` จะทำให้กลายเป็น **เมธอดระดับ class (static method)**
- ใช้เพื่อเปลี่ยนค่า `@@interest_rate`

- เทียบกับ Java: `static void setRate(double newRate) { ... }`

---

### เมธอด instance  
```ruby
def show
  puts "#{@name} has balance #{@balance}, interest rate = #{@@interest_rate}"
end
```
- `def show` = instance method  
- `puts` = พิมพ์ออกหน้าจอ (เหมือน `System.out.println`)  
- `"#{...}"` = string interpolation (แทรกค่าตัวแปร)  
- ใช้แสดง:  
  - `@name` → ชื่อเจ้าของบัญชี  
  - `@balance` → ยอดเงินของ object  
  - `@@interest_rate` → ดอกเบี้ยร่วม  

---

### การสร้าง object  
```ruby
a = BankAccount.new("Earth", 1000)  # Earth has 1000 with rate 0.05

b = BankAccount.new("Del", 2000)    # Del has 2000 with rate 0.05
```
- `BankAccount.new(...)` = สร้าง object (เรียก `initialize`)  
- `a` คือ object ตัวแรก, `name = "Earth"`, `balance = 1000`  
- `b` คือ object ตัวที่สอง, `name = "Del"`, `balance = 2000`  

---

### การเรียกเมธอด instance  
```ruby
a.show
b.show
```
- เรียก `show` ของ object `a` และ `b`  
- ทั้งคู่ใช้ `@@interest_rate = 0.05`  
- Output:
```
Earth has balance 1000, interest rate = 0.05
Del has balance 2000, interest rate = 0.05
```
---

### การเรียกเมธอด class  
```ruby
BankAccount.set_rate(0.1) # เปลี่ยน rate
```
- เรียก class method `set_rate` เพื่อแก้ค่า `@@interest_rate` เป็น `0.1`  
- เทียบ Java: `BankAccount.setRate(0.1);`

---

### แสดงผลใหม่หลังเปลี่ยน class variable  
```ruby
a.show
b.show
```
- คราวนี้ `@@interest_rate` = 0.1 แล้ว
- ทั้ง `a` และ `b` เห็นค่าที่เปลี่ยนเหมือนกัน  
- Output: 
```
Earth has 1000 with rate 0.1
Del has 2000 with rate 0.1
```

---

## สิ่งที่ควรระวัง (Ruby-specific quirks)

- `@@` class variable ถูก **แชร์ข้าม subclass**  
- ตัวอย่าง:  
```ruby
class Parent
  @@x = 1
end

class Child < Parent
  @@x = 2
end

puts Parent.class_variable_get(:@@x)  # แสดง 2
```

จาก Code จะเห็นว่า คลาสลูกแก้ค่าตัวแปร @@x (Class Variables) จากเดิมที่มีค่า 1 ให้มีค่าเป็น 2 
แต่พอเมื่อแสดงผล ตัวแปร X ที่อยู่ใน Class แม่ขึ้นมาพบว่าค่าถูกแก้ไปด้วย


**ทางเลือกที่ปลอดภัยกว่า:** ใช้ **class instance variable** (`@var` ที่ระดับ class)  
##### ตัวอย่าง:  
```ruby
class Bank
  @rate = 0.05            # class instance variable: เป็นของคลาสนี้เท่านั้น

  def self.rate; @rate; end
  def self.rate=(r); @rate = r; end
end

class SubBank < Bank
  @rate = 0.2             # แยกของตัวเอง ไม่กระทบ Bank
end

Bank.rate = 0.1
p [Bank.rate, SubBank.rate]   # => [0.1, 0.2]
```

---

## เทียบ Ruby Class Variables กับ Java
Concept class variables คล้ายๆกับ Concept ของ static variable ใน Java ตรงที่ Ruby class variable จะถูกแก้ไขค่าโดย Instance ตัวไหนก็ได้ใน class เดียวกัน โดยใน Java ตัวแปร Static ก็สามารถ ถูกแก้ไขค่าโดย Instance ตัวไหนก็ได้ใน class เดียวกันเช่นกัน

- Ruby `@@var` = Java `static`  
- Ruby `@var` = Java instance field  

```java
class BankAccount {
    String name;
    double balance;
    static double interestRate = 0.05; // class variable (static)

    BankAccount(String n, double b) {
        name = n; balance = b;
    }

    static void setRate(double r) { interestRate = r; }

    void show() {
        System.out.println(name + " has " + balance + " with rate " + interestRate);
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount a = new BankAccount("Earth", 1000);
        BankAccount b = new BankAccount("Del", 2000);
        a.show(); b.show();
        BankAccount.setRate(0.1);
        a.show(); b.show();
    }
}

```
**Output:** (แนวคิดเดียวกับ Ruby)
```
Earth has 1000 with rate 0.05
Del has 2000 with rate 0.05
Earth has 1000 with rate 0.1
Del has 2000 with rate 0.1
```

**สรุปเปรียบเทียบ**

| แนวคิด            | Java   | Ruby |
|--------------------|--------|------|
| Class variable     | static | @@   |
| Instance variable  | @field | @    |

**ต่างกันตรงที่:**
- Java subclass มี static ของตัวเอง (ไม่กระทบแม่)  
- Ruby subclass ใช้ `@@` (กระทบแม่ด้วย)

---

## เทียบกับ C

C ไม่มี “class” แต่มี `static` ตัวแปรที่คงค่า  

```c
#include <stdio.h>

void counter() {
    static int x = 0;
    x++;
    printf("%d\n", x);
}

int main() {
    counter(); // 1
    counter(); // 2
    counter(); // 3
}
```
**Output:**
```
count = 1
count = 2
count = 3
```
ไม่ใช่ class variable แต่เป็นแนวคิด “กองกลางคงค่า” ที่สามารถเข้าถึงและเปลี่ยนค่าได้จากทุกที่ 

---

## เทียบกับ Python

```python
class BankAccount:
   class BankAccount:
    interest_rate = 0.05  # class variable (ของคลาส)

    def __init__(self, name, balance):
        self.name = name          # instance attribute
        self.balance = balance

    @classmethod
    def set_rate(cls, r):
        cls.interest_rate = r

    def show(self):
        print(f"{self.name} has {self.balance} with rate {self.interest_rate}")

a = BankAccount("Earth", 1000)
b = BankAccount("Del", 2000)
a.show(); b.show()
BankAccount.set_rate(0.1)
a.show(); b.show()
```
**Output:**
```
Earth has 1000 with rate 0.05
Del has 2000 with rate 0.05
Earth has 1000 with rate 0.1
Del has 2000 with rate 0.1
```

Python ใช้ `class variable` คล้าย Java  

---

## เมื่อไหร่ควร หรือ ไม่ควรใช้ `@@` ใน Ruby?

- **ควรใช้**: เมื่อค่านั้นคือ ค่าที่แชร์จริงๆ เช่น ตัวนับจำนวน instance  
- **ไม่ควรใช้**: ถ้า subclass ควรมีค่าเป็นของตัวเอง  

---

## Conclusion

- Ruby `@@var` คล้าย Java `static` แต่ **แชร์ทะลุ subclass**  
- ใน Ruby ถ้าไม่อยากแชร์กับลูก ให้ใช้ class instance variable (`@var` ในระดับ class) แทน  
- C ไม่มี class แต่ `static` อธิบายแนวคิด “ค่าคงเดิม”  
- Python ใช้ class variable แบบเดียวกับ Java  

---

## References

- Ruby Core Team. (n.d.). Ruby FAQ: Variables. Ruby-Lang.org. Retrieved August 30, 2025, from https://www.ruby-lang.org/en/documentation/faq/8/
- RuboCop & Contributors. (n.d.). Ruby style guide. Rubystyle.guide. Retrieved August 30, 2025, from https://rubystyle.guide/
- Oracle. (n.d.). Class variables. In The Java™ Tutorials. Oracle. Retrieved August 30, 2025, from https://docs.oracle.com/javase/tutorial/java/javaOO/classvars.html
- Python Software Foundation. (n.d.). Classes. In The Python tutorial (Python 3.12.5 documentation). Retrieved August 30, 2025, from https://docs.python.org/3/tutorial/classes.html


## Presentation
- Link video:
- PDF:
