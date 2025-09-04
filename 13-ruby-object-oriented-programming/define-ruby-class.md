# Define Ruby Class

## Object คืออะไร
object (วัตถุ) ในภาษาโปรแกรมเชิงวัตถุ (Object-Oriented Programming: OOP) คือ สิ่งที่เป็นตัวแทนของข้อมูลที่เราต้องการสร้าง   
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

my_dog = Dog.new("white", 3) # create object
my_dog.bark
```
## ผลลัพธ์
```
The-3-year-old white dog: Bao! Bao!
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

my_dog = Dog.new("white", 3) # create object
my_dog.bark 
````
## ผลลัพธ์
```
The-3-year-old white dog: Bao! Bao!
```
## Class คืออะไร
object เป็น instance of Class หรือก็คือวัตถุเป็นสิ่งที่ถูกสร้างมาจาก Class
หน่วยความจำสำหรับ object จะถูกจัดสรรก็ต่อเมื่อ object ถูกสร้างขึ้น (instantiation)<br> 
## Define Ruby Class
