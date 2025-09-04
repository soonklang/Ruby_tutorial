# Define Ruby Class

## Object คืออะไร
object (วัตถุ) ในภาษาโปรแกรมเชิงวัตถุ (Object-Oriented Programming: OOP) คือ สิ่งที่เป็นตัวแทนของข้อมูลที่เราต้องการสร้าง โดย OOP มีองค์ประกอบ 6 อย่างได้แก่
  1. Encapsulation ส่วนที่ไว้ครอบคลุมข้อมูลและ method เอาไว้ในที่ที่เดียว
  2. Inheritance ใช้ในการสืบทอดคุณลักษณะให้แก่อีกคลาส เพื่อลดความซับซ้อน
  3. Abstraction ส่วนที่แสดงฟีเจอร์ที่สำคัญให้ user โดยซ่อนรายละเอียดการทำงานเบื้องหลัง
  4. Polymorphism ส่วนที่ช่วยในการลดการเขียนโค้ดซ้ำ เพิ่มความยืดหยุ่นในการ
  5. Object สิ่งที่เป็นตัวแทนของข้อมูลที่เราต้องการสร้าง
  6. Class คือพิมพ์เขียนหรือต้นแบบสำหรับใช้ผู้ใช้ไว้สร้างวัตถุ

     ---
<br>โดยแต่ละ object จะมีองค์ประกอบที่สำคัญอยู่ 3 ส่วน ได้แก่ 
  1. Identity (เอกลักษณ์เฉพาะตัว): โดยแต่ละ object จะมีตัวระบุเป็นของตัวเอง ซึ่งสามารถแตกต่างจาก object อื่นๆก็ได้
  2. State/Attribute (สถานะ/คุณสมบัติ):
     - attribute ของ object คือลักษณะของ object อย่างเช่นสีของ object โดยสามารถมีได้หลากหลาย attribute ใน object เดียว
     - state คือสถานะที่บ่งบอกว่า object มีสถานะใด เช่นสีของ object เป็นสีแดง 
  3. Behavior (พฤติกรรม): พฤติกรรมของ object เป็นเหมือนสิ่งที่ object สามารถทำหรือตอบสนองได้
## Object ในภาษา Ruby
Ruby เป็นภาษาโปรแกรมเชิงวัตถุอย่างสมบูรณ์ เนื่องจากทุกอย่างในภาษานี้ล้วนเป็น object ไม่ว่าจะเป็นตัวเลข สตริง หรือฟังก์ชัน <br>ทุก object สืบทอดจาก BasicObject ซึ่งเป็น root ของ object ทั้งหมด และมีโมดูล kernel เป็นตัวช่วยทำให้เขียนโค้ดสั้นลง เนื่องจากโมดูลนี้รวมคำสั่งที่ใช้บ่อยไว้ ซึ่งใน Ruby ตัวโมดูลนี้ถูกรวมกับ object ทำให้ object สามารถเรียกใช้เมธอดได้โดยตรงเช่น การสั่ง `puts 1` จะเป็นการแสดงค่า `1` แทนที่จะต้องเขียน `Kernel.puts 1` ข้อควรระวังสำหรับการใช้ BasicObject คือ BasicObject ถูกออกแบบมาสำหรับเป็น class เบาหรือก็คือเป็น class ที่มี method น้อยมาก ทำให้ในนั้นไม่มีโมดูล kernel รวมอยู่ด้วยจึงต้องเขียน `Kernel.` ก่อนเพื่อให้ทำงาน<br> การสร้าง object ใน Ruby จะต้องใช้ method `new` 
## ตัวอย่างการสร้าง Object ในภาษา Ruby แบบทั่วไป
```ruby
class Dog
  attr_accessor :color, :age
  def initialize(color, age) # constructor
    @color = color
    @age = age
  end

  def bark # method (behavior)
    puts "The-#{@age}-year-old #{@color} dog: Bao! Bao!"
  end
end

my_dog = Dog.new("white", 1) # create object
my_dog.bark
```
## ผลลัพธ์
```
The-1-year-old white dog: Bao! Bao!
```
## ตัวอย่างการสร้าง Object ในภาษา Ruby แบบใช้ BasicObject
```ruby
class Dog < BasicObject
attr_accessor :color, :age
  def initialize(color, age) # constructor
    @color = color
    @age = age
  end

  def bark # method (behavior)
    Kernel.puts "The-#{@age}-year-old #{@color} dog: Bao! Bao!" 
  end
end

my_dog = Dog.new("white", 1) # create object
my_dog.bark 
````
## ผลลัพธ์
```
The-3-year-old white dog: Bao! Bao!
```
## Object ในภาษา C
C ไม่มี object เนื่องจากไม่ได้ถูกออกแบบมาให้มีการ encapsulation ซึ่งเป็นส่วนสำคัญของการเป็นภาษาโปรแกรมเชิงวัตถุ ถึงใน C จะมี struct ที่สามารถเก็บข้อมูลแทนได้ แต่ก็ต้องมากำหนด pointer เข้าฟังก์ชันเอง
## ตัวอย่างการจำลองการสร้าง Object ในภาษา C 
```C
#include <stdio.h>
#include <string.h>

typedef struct { // class
    char color[10];
    int age;
} Dog;

void bark(Dog* dog) {// method Dog* dog encap
    printf("The-%d-year-old %s dog: Bao! Bao!\n", dog->age, dog->color); //dog-> attribute
}

int main() {
    Dog my_dog; // create object
    strcpy(my_dog.color, "white");  
    my_dog.age = 2;                 

    // เรียก method
    bark(&my_dog);

    return 0;
}

```
## ผลลัพธ์
```
The-2-year-old white dog: Bao! Bao!
```
## Object ในภาษา Python
หลักการ Object ในภาษา python มีความคล้ายกันกับของภาษา Ruby เป็นอย่างมากตรงที่ข้อมูลทุกอย่างในโปรแกรมภาษา python ถูกมองเป็น object และโดยแต่ละ object จะมีองค์ประกอบ 3 ส่วน ได้แก่
  1. Identity เปรียบเสมือนเป็น address ของ object เพราะเมื่อใดที่มันถูกสร้างค่าของมันจะไม่มีทางเปลี่ยน
  2. Type คือชนิดของ object บอกว่า object รองรับ operation แบบไหน
  3. Value คือข้อมูลที่ถูกเก็บอยู่ใน object มี 2 แบบ คือ แบบเปลี่ยนค่าได้ และ เปลี่ยนค่าไม่ได้<br>
สิ่งที่ Python ไม่เหมือน Ruby จะเป็นตรง attribute ที่จะใช้ self แทน @ การใช้ self เป็นเหมือนการบ่งบอกว่าชี้ไปที่ตัวแปรปัจจุบัน แต่ไม่จำเป็นต้องใช้ชื่อ self ก็ได้เพราะไม่ใช่คำสงวนแต่เป็นคำที่คนทั่วไปให้การยอมรับ
## ตัวอย่างการสร้าง Object ในภาษา Python
```python
class Dog:
    def __init__(self, color, age):
        self.color = color  # attribute
        self.age = age      # attribute

    def bark(self):        # method
        print(f"The-{self.age}-year-old {self.color} dog: Bao! Bao!")

my_dog = Dog("white", 3) # create object
my_dog.bark()
```
## ผลลัพธ์
```
The-3-year-old white dog: Bao! Bao!
```
## Object ในภาษา Java
Java มี object ที่คล้ายกับ Ruby และ Python ตรงที่ object เป็น instance of the Class เหมือนกัน แต่มีความต่างที่ตอนที่สร้าง class ขึ้นมาการสร้าง pointer ขึ้นมาชี้ค่าตัวแปร จะไม่เหมือน @ และ self ตรงที่ .this ของ java ตรงที่ java แยก `primitive` หรือก็คือเป็นการแทนค่าเข้าไปในพวก `int` `boolean` `float` ก็คืออย่างเช่นเวลาเราเขียน 
``` Java 
int x = 5;
int y = x;
int y = 10
ค่าของ x จะเท่าเดิมก็คือ 5
```
แต่กรณี `reference` เป็น `object` จะเก็บ pointer/ที่อยู่ของ object อย่างเช่น
```Java
Dog a = new Dog();
Dog b = a;
b.color = "white";
ค่าของ a.color จะเป็น white ด้วย
```
Python และ Ruby จะถูกเปลี่ยนเป็นแบบกรณี object ของ Java เสมอ เพราะทั้งคู่มีเป็น object ทั้งหมด
## ตัวอย่างการสร้าง Object ในภาษา Java
```Java
public class Dog {
    String color;
    int age;

    public Dog(String color, int age) {
        this.color = color;
        this.age = age;
    }

    public void bark() {
        System.out.println("The-" + age + "-year-old " + color + " dog: Bao! Bao!");
    }

    public static void main(String[] args) {
        Dog myDog = new Dog("white", 4); // create object
        myDog.bark();                    
    }
}
```
## ผลลัพธ์
```
The-4-year-old white dog: Bao! Bao!
```
## Class คืออะไร
Class คือ พิมพ์เขียวหรือต้นแบบสำหรับ object โดยกำหนด attribute และ behavior ไว้ก่อน ก็จะทำให้สามารถสร้าง object มาได้หลาย object ที่มี attribute และ behavior เหมือนกัน
object เป็น instance of Class หรือก็คือวัตถุเป็นสิ่งที่ถูกสร้างมาจาก Class ตอนที่เราเขียน class ขึ้นมา หน่วยความจำจะยังไม่ถูกใช้ แต่จะถูกใช้ก็ต่อเมื่อ object ถูกสร้างขึ้น (instantiation)<br> 
## ตัวอย่าง Class ของภาษา Ruby
```Ruby
class Dog
  attr_accessor :color, :age
  def initialize(color, age) # constructor
    @color = color
    @age = age
  end

  def bark # method (behavior)
    puts "The-#{@age}-year-old #{@color} dog: Bao! Bao!"
  end
end
```
## Define Ruby Class
