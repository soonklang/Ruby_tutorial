# แบบฝึกหัด
## 1. Creating an Object from a class 
### พิจารณา Code ภาษา Ruby และตอบคำถามต่อไปนี้
#### Q :ถ้าเพิ่มโค้ด cow = Animal.new("Cow","Moo") แล้วเรียก puts cow.speak จะได้ผลลัพธ์เป็นอะไร และเพราะอะไร
```ruby
class Animal
  def initialize(name, sound)
    @name = name
    @sound = sound
  end

  def speak
    "#{@name} says #{@sound}"
  end
end

dog = Animal.new("Dog", "Woof")
cat = Animal.new("Cat", "Meow")

puts dog.speak
puts cat.speak
```
<details>
<summary> เฉลยข้อที่ 1. </summary>
  
## Output
```ruby
  Cow says Moo
```
  #### เพราะ เมื่อสร้าง object cow ตัวแปร @name จะเก็บค่า "Cow" และ @sound จะเก็บ "Moo" ดังนั้น method speak จะ return "Cow says Moo"
</details>

## 2. Define Ruby Class
### Q : ทำไม Ruby ถึงออกแบบ Class เป็น instance ของ Class เอง

<details>
<summary> เฉลยข้อที่ 2. </summary>
  
  #### เพื่อแก้ปัญหาจุดเเริ่มต้น (chicken-egg problem) ที่ทำให้สับสนว่า class ไหนเป็นจุดเริ่มต้น Ruby จึงตัดปัญหานี้ด้วยการทำให้ Class เป็น instance ของตัวเองเพื่อปิดวงจร
</details>

## 4. Instance Methods
```ruby
class BankAccount
  attr_accessor :balance , :rate

  def initialize(balance)
    @balance = balance
    @rate = 0.5
  end

  def calc_interest  # instance method
    interest = @balance * @rate
    puts "Interest on balance #{@balance} at rate #{@rate} is #{interest}"
  end
end
```
### Q : ถ้าเพิ่มโค้ดดังต่อไปนี้ จะได้ผลลัพธ์เป็นอะไร
```ruby
account = BankAccount.new(2000)
account.calc_interest
```
<details>
<summary> เฉลยข้อที่ 4. </summary>

```
Interest on balance 2000 at rate 0.5 is 1000.0
```

</details>

## 5. Instance Variables and Accessor Methods
### Q : จงเขียนโปรแกรมภาษา Ruby ที่มีการสร้างคลาส Animals โดยสัตว์แต่ละตัว รหัสประจำตัว ชนิด ชื่อ อายุ ของสัตว์กำกับไว้ พร้อมแสดงข้อความ
<details>
<summary> เฉลยข้อที่ 5. </summary>
  
```ruby

class Animals
  attr_accessor :animal_id
  attr_accessor :species
  attr_accessor :name
  attr_accessor :age

   def initialize(animal_id, species, name, age)
    @animal_id = animal_id   # รหัสสัตว์
    @species   = species     # ชนิด เช่น ช้าง, สิงโต
    @name      = name        # ชื่อ
    @age       = age         # อายุ
  end
end

animal_1 = Animals.new(1,"elephant","Khan Kluay",5)
animal_2 = Animals.new(2,"lion","Simba",7)

puts "ID: #{animal_1.animal_id}, species: #{animal_1.species}, name: #{animal_1.name}, age: #{animal_1.age} years old"
puts "ID: #{animal_2.animal_id}, species: #{animal_2.species}, name: #{animal_2.name}, age: #{animal_2.age} years old"

```

</details>

## 6. Operator Overloading in Ruby
### Q : จงเขียนคำสั่งในภาษา Ruby ที่เปลี่ยนแปลงการทำงานของ operator `/` เป็นการเชื่อมระหว่าง String และ String โดยมีข้อความ `" and "` คั่นแต่ละ String ที่ทำการ `/` พร้อมแสดงผลข้อความ

```ruby

class OverloadExample

  attr_accessor :text

  def ____
    ____
  end

  def ____
    ____
  end

end

```

<details>
<summary> เฉลยข้อที่ 6. </summary>
  
```ruby
class OverloadExample

  attr_accessor :text

  def initialize(text)
    @text = text
  end

  def /(other)
    OverloadExample.new(@text + " and " + other.text)
  end

end

good = OverloadExample.new("good")
bad = OverloadExample.new("bad")

a = good / bad
puts a.text
```

</details>

## 7. Passing parameters to new method
### พิจารณา Code ภาษา Ruby และตอบคำถามต่อไปนี้
#### Q : ผลลัพธ์ที่ได้จากโปรแกรมนี้คืออะไร และเพราะเหตุใดถึงได้ผลลัพธ์นี้

```ruby
class Rectangle
  def initialize(width, height)
    @width = width
    @height = height
  end

  def area
    @width * @height
  end

  def resize(new_width, new_height)
    @width = new_width
    @height = new_height
  end
end

rect = Rectangle.new(5, 10)
puts rect.area

rect.resize(7, 3)
puts rect.area
```
<details>
<summary><strong>เฉลยข้อที่ 7.</strong></summary>
  
## Output
```ruby
50
21
```
- ครั้งแรก rect = Rectangle.new(5, 10) → area = 5 * 10 = 50
- หลังจาก rect.resize(7, 3) → object ถูกอัปเดตเป็น @width = 7, @height = 3 → area = 7 * 3 = 21
</details>

## 8. Private classes in Ruby
### Q : จากโค้ดตัวอย่างที่ทำให้คลาส Guardians เป็น private หากเราต้องการเรียกใช้เมธอด Quill ของคลาส Guardians ให้ทำงานได้ภายนอกคลาสหลัก(Marvel) โดยไม่แก้ไขหรือลบบรรทัด private_constant :Guardians เราจะต้องเขียนโค้ดเพิ่มเติมอย่างไรและควรเขียนไว้ที่ส่วนใด? พร้อมทั้งอธิบายเหตุผลว่า ทำไมโค้ดที่เพิ่มเข้าไปจึงสามารถทำให้เข้าถึงคลาส Guardians ได้โดยไม่เกิด NameError  

```ruby
class Marvel
  class Guardians
    def Quill
      puts "Legendary outlaw"
    end
  end

  class Avengers
    def Tony
      puts "I am Iron-man"
    end
  end

  private_constant :Guardians
end
```
<details>
<summary><strong>เฉลยข้อที่ 8.</strong></summary>

เราสามารถเรียกใช้เมธอด Quill ของคลาส Guardians ได้โดยการสร้าง public method ขึ้นมาภายในคลาส Marvel เพื่อทำหน้าที่เป็น "ตัวกลาง" ในการเรียกใช้งานคลาส Guardians ที่เป็น private

```ruby
class Marvel
    class Guardians
    def Quill
      puts "Legendary outlaw"
    end
  end

  class Avengers
    def Tony
      puts "I am Iron-man"
    end
  end

  private_constant :Guardians

  # --- ส่วนที่เพิ่มเติม ---
  # สร้าง public method เพื่อเป็นทางเข้าถึง Guardians จากภายใน
  def call_the_guardians
    # ภายในเมธอดนี้ เราสามารถเข้าถึง Guardians ได้โดยตรง
    team = Guardians.new
    team.Quill
  end
  # --------------------
end

marvel_hq = Marvel.new
marvel_hq.call_the_guardians # => ทำงานได้สำเร็จ
```
### output :  
```
Legendary outlaw
```
เนื่องจากเมธอด call_the_guardians ที่เราสร้างขึ้นมานั้นถูกนิยามอยู่ ภายในคลาส Marvel จึงมีสิทธิ์เข้าถึงคลาส Guardians ที่เป็น private class ได้โดยตรง และเนื่องจากเมธอดนี้เป็น public จึงเปรียบเสมือน "ประตู" ที่อนุญาตให้โค้ดภายนอกสามารถสั่งให้คลาส Marvel ไปทำงานกับส่วนที่เป็น private ของตัวเองได้ ซึ่งเป็นหลักการสำคัญของการห่อหุ้มข้อมูล (Encapsulation)
</details>

## 9. Public and Private
### Q : จงเขียนคลาส Car โดยภายในคลาสต้องมีตัวแปรเก็บข้อมูลยี่ห้อรถ (brand) และทะเบียนรถ (license) จากนั้นให้สร้างเมธอด change_brand(new_brand) เป็นแบบ public เพื่อให้สามารถเปลี่ยนยี่ห้อรถได้โดยตรง และให้สร้างเมธอด change_license(new_license) เป็นแบบ private เพื่อไม่ให้ถูกเรียกใช้งานจากภายนอกคลาสโดยตรง แต่ให้มีเมธอด create_license(new_license) ที่เป็นแบบ public ทำหน้าที่เป็นตัวกลางในการเรียกใช้งานเมธอด change_license(new_license) 

<details>
<summary><strong>เฉลยข้อที่ 9. (Ruby)</strong></summary>
<pre>
  
```ruby
class Car 
  def initialize(car_brand, car_license)
    @car_brand = car_brand
    @car_license = car_license
    puts 'This is ' + @car_brand + ' brand and license ' + @car_license
  end
  
  public
  def change_brand(new_brand)
    @car_brand = new_brand
    puts 'Change brand to : ' + @car_brand
  end
  
  def create_license(new_license)
    puts 'This is new license : ' + new_license
    change_license(new_license)
  end
  
  private
  def change_license(new_license)
    @car_license = new_license
    puts 'Change license to ' + @car_license
  end
end

car = Car.new('Nissan', 'A123')
car.change_brand('Toyota')
car.create_license('B231')
```
</pre>
</details>
<details>
<summary><strong>Output</strong></summary>
<pre>
<code>This is Nissan brand and license A123
Change to brand : Toyota
This is new license : B231
Change license to B231</code>
</pre>
</details>

<details>
<summary><strong>Java</strong></summary>
<pre>
  
```java 
public class Car {
    private String carBrand;
    private String carLicense;

    Car(String carBrand, String carLicense) {
        this.carBrand = carBrand;
        this.carLicense = carLicense;
        System.out.println("This is " + carBrand + " brand and license " + carLicense);
    }

    public void changeBrand(String carBrand) {
        this.carBrand = carBrand;
        System.out.println("Change Brand to : " + carBrand);
    }

    public void createLicense(String carLicense) {
        System.out.println("This is new license : " + carLicense);
        changeLicense(carLicense);
    }

    private void changeLicense(String carLicense) {
        this.carLicense = carLicense;
        System.out.println("Change license to : " + carLicense);
    }
    public static void main(String[] args) {
        Car car = new Car("Nissan", "A123");
        car.changeBrand("Toyota");
        car.createLicense("B231");
    }
}
```
</pre>
</details>

<details>
<summary><strong>Python</strong></summary>
<pre>
  
```python
class Car :
    def __init__(self, car_brand, car_license) :
        self.car_brand = car_brand
        self.car_license = car_license
        print("This is " + self.car_brand + " brand and license " + self.car_license)

    def change_brand(self, new_brand) :
        self.car_brand = new_brand
        print("Change brand to : " + self.car_brand)

    def create_license(self, new_license) :
        print("This is new license : " + self.car_license)
        self.__change_license(new_license)
    
    def __change_license(self, new_license) :
        self.car_license = new_license
        print("Change license to : " + self.car_license)

car = Car("Nissan", "A123")
car.change_brand("Toyota")
car.create_license("B231")
```
</pre>
</details>

<details>
<summary><strong>C</strong></summary>
<pre>
  
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

typedef struct {
    char carBrand[50];
    char carLicense[50];
} Car;

Car* createCar(const char* brand, const char* license) {
    Car* car = (Car*) malloc(sizeof(Car));
    strcpy(car->carBrand, brand);
    strcpy(car->carLicense, license);
    printf("This is %s brand and license %s\n", car->carBrand, car->carLicense);
    return car;
}

void changeBrand(Car* car, const char* brand) {
    strcpy(car->carBrand, brand);
    printf("Change Brand to : %s\n", car->carBrand);
}

void changeLicense(Car* car, const char* license) {
    strcpy(car->carLicense, license);
    printf("Change license to : %s\n", car->carLicense);
}

void createLicense(Car* car, const char* license) {
    printf("This is new license : %s\n", license);
    changeLicense(car, license);
}

int main() {
    Car* car = createCar("Nissan", "A123");
    changeBrand(car, "Toyota");
    createLicense(car, "B231");

    free(car); 
    return 0;
}
```
</pre>
</details>

## 11. Ruby Class Variables
### Q : ใน Ruby ถ้าใช้ตัวแปรคลาส (`@@var`) จะมีพฤติกรรมอย่างไรเมื่อมี subclass สืบทอดไป?  

- A) ตัวแปร `@@var` ถูกจำกัดแค่ภายใน class แม่เท่านั้น ไม่แชร์ไป subclass  
- B) Subclass จะได้สำเนาของ `@@var` ของตัวเอง ไม่กระทบค่าใน class แม่  
- C) ค่า `@@var` ถูกแชร์ร่วมกันทั้ง class แม่และ subclass ทุกระดับ  
- D) ตัวแปร `@@var` สามารถถูกเข้าถึงได้เฉพาะ instance ของ subclass เท่านั้น  

<details>
<summary><strong>เฉลย (Ruby)</strong></summary>
  C) ค่า @@var ถูกแชร์ร่วมกันทั้ง class แม่และ subclass ทุกระดับ
</details>

### Q : อธิบายความแตกต่างระหว่าง *Class Variable* (`@@var`) และ *Class Instance Variable* (`@var ระดับ class`) ใน Ruby  

<details>
<summary><strong>เฉลย (Ruby)</strong></summary>

- `@@var` (Class Variable):  
  - ใช้ `@@` นำหน้า  
  - แชร์ค่าร่วมกันระหว่าง instance ทั้งหมดของ class เดียวกัน  
  - ถูกแชร์ข้าม subclass ด้วย → ถ้าเปลี่ยนค่าที่ subclass จะกระทบ class แม่ด้วย  

- `@var` (Class Instance Variable):  
  - ใช้ `@` แต่ประกาศในระดับ class (เช่น `@rate`)  
  - เป็นของ object ระดับ “class” เอง  
  - ไม่ถูกแชร์ข้าม subclass → แต่ละ class มีค่าของตัวเอง  

</details>


## 12. Static Members
### Q : คำถาม: อธิบายความแตกต่างระหว่าง self.get ใน Ruby กับ get ที่เป็น instance method
<details>
<summary><strong>เฉลย (Ruby)</strong></summary>
<pre>
    def self.get → class method ต้องเรียกผ่านชื่อคลาสเท่านั้น
    def get → instance method ต้องสร้าง object ก่อนที่จะใช้method นั้น
</pre>
</details>

### Q : คำถาม: ข้อใดอธิบาย ข้อจำกัดของ static variable ได้ถูกต้องที่สุด?
>
A) ไม่สามารถเข้าถึงได้โดยตรงจาก class
>
B) ไม่สามารถถูกแก้ไขค่าได้หลังจากกำหนด
>
C) ถูกแชร์ร่วมกันระหว่าง object ทั้งหมดของ class เดียวกัน
>
D) จะถูกสร้างใหม่ทุกครั้งเมื่อมีการสร้าง object


<details>
<summary><strong>เฉลย (Ruby)</strong></summary>
  C) ถูกแชร์ร่วมกันระหว่าง object ทั้งหมดของ class เดียวกัน
</details>
