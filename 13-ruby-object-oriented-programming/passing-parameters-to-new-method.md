# Passing Parameters to new Method
## Passing Parameters to new Method คืออะไร
ในภาษา Ruby Passing Parameters to new Method คือการส่งอาร์กิวเมนต์ (arguments) เข้าไปใน constructor ของคลาส เวลาที่เราเรียก ClassName.new(...) เพื่อสร้างอินสแตนซ์ใหม่ของคลาสนั้น
โดยพื้นฐานแล้ว เมื่อเรียก .new ของคลาสใด ๆ ใน Ruby มันจะ:  
1.สร้างออบเจกต์ใหม่  
2.เรียกเมธอด initialize ภายในคลาสนั้น  
3.ส่งพารามิเตอร์ที่คุณส่งเข้า .new(...) ไปให้ initialize(...)  
## ตัวอย่าง Ruby
```ruby
class Person
  def initialize(name, age)
    @name = name
    @age = age
  end

  def display
    puts "Name: #{@name}, Age: #{@age}"
  end
end

person1 = Person.new("Alice", 25)
person1.display

```
## Output
```ruby
Name: Alice, Age: 25
```
## คำอธิบาย
- Person.new("Alice", 25) เป็นการเรียกเมธอด new ซึ่งจะสร้างอ็อบเจกต์ใหม่และเรียก initialize พร้อมส่งพารามิเตอร์ name และ age  
- ค่าที่ส่งเข้ามาจะถูกเก็บไว้ในตัวแปรอินสแตนซ์ @name และ @age  
- เมธอด display ใช้แสดงผลค่าที่เก็บไว้  
## ตัวอย่าง Java
```java
public class Person {
    String name;
    int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }

    public static void main(String[] args) {
        Person person1 = new Person("Alice", 25);
        person1.display();
    }
}

```
## Output
```java
Name: Alice, Age: 25
```
## ความแตกต่าง Java และ Ruby
- ไม่มี new method ที่ override ได้ – new เป็น คำสงวน ที่ใช้เรียก constructor โดยตรง
- Constructor ต้องมีชื่อเดียวกับคลาส และสามารถ overload ได้
- ต้องกำหนดชนิดข้อมูลพารามิเตอร์แบบชัดเจน (static typing)
- Verbose มากกว่า Ruby และ Python เนื่องจากต้องประกาศชนิดตัวแปรทุกตัว
- ไม่สามารถเปลี่ยนพฤติกรรมของ new ได้ (ไม่เหมือน Ruby)
## ตัวอย่าง Python
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def display(self):
        print(f"Name: {self.name}, Age: {self.age}")

person1 = Person("Alice", 25)
person1.display()

```
## Output
```python
Name: Alice, Age: 25
```
## ความแตกต่าง Python และ Ruby
- ไม่มีเมธอด new ที่ใช้โดยทั่วไป – การสร้างอ็อบเจกต์เรียกผ่าน Class(...) ซึ่งจะเรียก __init__
- Constructor ใช้ชื่อ __init__ และสามารถ overload โดยใช้ default arguments หรือ *args ได้
- ไม่ต้องประกาศชนิดของพารามิเตอร์ (dynamic typing)
- กระชับ (concise) เหมือน Ruby
- สามารถ override __new__() ได้ในบางกรณีหากต้องการควบคุมการสร้างอ็อบเจกต์
## ตัวอย่าง C++
```C++
#include <iostream>
using namespace std;

class Person {
private:
    string name;
    int age;

public:
    Person(string n, int a) {
        name = n;
        age = a;
    }

    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Person person1("Alice", 25);
    person1.display();
    return 0;
}

```
## Output
```C++
Name: Alice, Age: 25
```
## ความแตกต่าง C++ และ Ruby
- ไม่มี new method เหมือน Ruby – ใช้ new เป็น คำสั่ง สำหรับการจองหน่วยความจำ (pointer allocation)
- Constructor มีชื่อเดียวกับคลาส และสามารถ overload ได้
- ต้องประกาศชนิดของพารามิเตอร์ (static typing)
- มีความซับซ้อนเรื่อง memory (ต้อง delete ถ้าใช้ new)
- ไม่สามารถเปลี่ยนพฤติกรรมของ new ได้ง่ายเหมือน Ruby
## Video
## Slides
## References
- O’Reilly Media. (n.d.). Object creation and initialization. In The Ruby programming language. O'Reilly Media.
สืบค้นเมื่อ 3 กันยายน 2025, จาก https://www.oreilly.com/library/view/the-ruby-programming/9780596516178/ch07s04.html  
- Ruby for Beginners. (n.d.). Initializing objects. Ruby Monstas.
สืบค้นเมื่อ 3 กันยายน 2025, จาก https://ruby-for-beginners.rubymonstas.org/writing_classes/initializers.html  
- Useful Codes. (2025, January 19). Function parameters and arguments in Ruby. Useful.Codes.
สืบค้นเมื่อ 3 กันยายน 2025, จาก https://useful.codes/function-parameters-and-arguments-in-ruby/  
- Alchemists.io. (n.d.). Ruby method parameters and arguments. Alchemists.
สืบค้นเมื่อ 3 กันยายน 2025, จาก https://www.alchemists.io/articles/ruby_method_parameters_and_arguments/  
- Educative.io. (n.d.). Passing parameters to methods - The handbook for Ruby developers. Educative.
สืบค้นเมื่อ 3 กันยายน 2025, จาก https://www.educative.io/courses/handbook-ruby-developers/passing-parameters-to-methods  
- Stack Overflow. (n.d.). Does ruby call initialize method automatically? สืบค้นเมื่อ 3 กันยายน 2025, จาก Stack Overflow: https://stackoverflow.com/questions/16245315/does-ruby-call-initialize-method-automatically?utm_source=chatgpt.com
Stack Overflow
- Stack Overflow. (n.d.). In Ruby, what's the relationship between 'new' and 'initialize'? How to return nil while initializing? สืบค้นเมื่อ 3 กันยายน 2025, จาก Stack Overflow: https://stackoverflow.com/questions/10383535/in-ruby-whats-the-relationship-between-new-and-initialize-how-to-return-n?utm_source=chatgpt.com
Stack Overflow
