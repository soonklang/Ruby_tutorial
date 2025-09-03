# Ruby Class Inheritance
---
## Class Inheritance คืออะไร?

Inheritance(การสืบทอด) คือ การที่เราสามารถสร้าง class ใหม่ขึ้นมาโดยใช้ class ที่มีอยู่แล้วเป็นต้นแบบ โดยยังมี variable และ method ของของ class นั้นๆอยู่ เพื่อนำมาสร้าง class ที่มีความคล้ายกันแต่สามารถเพิ่ม variable และ method ใหม่ๆได้

### ประเภทของ Inheritance
- **Single inheritance(การสืบทอดเดี่ยว)** คือ class หนึ่งสืบทอดมาจาก class เพียง class เดียว
- **Multiple inheritance(การสืบทอดหลายรายการ)** คือ class หนึ่งสามารถสืบทอดมาจาก หลายๆ class พร้อมกันได้
- **Multilevel inheritance(การสืบทอดหลายระดับ)** คือ class หนึ่งสืบทอดมาจากอีก class ที่สืบทอด class อื่นมาอีกที
- **Hierarchical inheritance(การสืบทอดแบบลำดับชั้น)** คือ มีหลาย class สืบทอดมาจาก class เพียง class เดียว 
- **Hybrid inheritance(การสืบทอดแบบผสม)** คือ การรวมกันระหว่างประเภทของ Inheritance ตั้งแต่ 2 ขึ้นไป
 
โดยภาษา Ruby นั้นไม่รองรับ **Multiple inheritance** แต่ว่าสามารถใช้ **Mixins** (via Modules) แทนได้

### Keywords
- **Super Class** คือ
- **Sub Class** คือ

---

## การใช้งาน Class Inheritance ในภาษา Ruby

- การสืบทอดใน Ruby สามารถทำได้โดยใช้เครื่องหมาย `<`
### Syntax ตัวอย่าง
```ruby
class subclass_name < superclass_name 
```

### ตัวอย่าง Code การใช้งาน Class Inheritance ในภาษา Ruby
```ruby
# Superclass 
class ThisIsSuperClass 

    # constructor of superclass
    def initialize 
        
        puts "Creating class"
    end
    
    # method of the Superclass
    def super_method
        
        puts "Method of Superclass"
    end
end

# Subclass
class ThisIsSubClass < ThisIsSuperClass 

end

# creating object from superclass
ThisIsSuperClass.new

# creating object from subclass
test_obj = ThisIsSubClass.new

# calling the method of superclass from subclass
test_obj.super_method
```

<details>

<summary>Output</summary>

> Creating class\
> Creating class\
> Method of Superclass

</details>
จากตัวอย่าง Code การใช้งาน Class Inheritance จะเห็นว่า ThisIsSubClass สืบทอดมาจาก ThisIsSuperClass ทำให้ test_obj ที่สร้างมาจาก ThisIsSubClass สามารถใช้ method initialize และ super_method ได้แม้ใน ThisIsSubClass ไม่ได้เขียนขึ้นมาใหม่



### การใช้งาน Class Inheritance ในภาษาอื่นๆ
- ### Java
- ### Python
- ### C

---

## Method Overriding
 Method Overriding คือ การที่เราสามารถเขียนทับ method ใน subclass ที่สืบทอดมาจาก superclass ได้โดยชื่อ method ยังคงเดิมแต่การดำเนินการใน method นั้นเปลี่ยนไปจาก superclass 
 ### ตัวอย่าง Code การใช้งาน Method Overriding ในภาษา Ruby
```ruby
class Lion
  
  def roar
    print "ROAR!"
  end
end

class Cat < Lion
  
  def roar #Overriding
    print "meow!"
  end
end

c = Cat.new
c.roar
```
<details>

<summary>Output</summary>

> meow!


</details>
จากตัวอย่าง Code การใช้งาน Method Overriding จะเห็นว่า แม้ว่า object c สร้างมาจาก class Cat ที่สืบทอดมาจาก class Lion มี method roar เหมือนกันแต่ class Cat ได้ Overriding method roar ไปแล้วทำให้ผลลัพธ์จากที่ควรจะเป็น ROAR! กลายเป็น meow! แทน

### การใช้งาน Method Overriding ในภาษาอื่นๆ
- ### Java
- ### Python
- ### C

---

## Super method
Super method ใช้ใน Sub Class เพื่อเรียก method ของ Super Class มาใช้ โดยมีการส่ง parameter ที่ใช้สำหรับ Super method นั้นๆในลักษณะที่แตกต่างกันไป สามารถดูตัวอย่างข้างล่างเพื่อง่ายต่อความเข้าใจได้
### ตัวอย่าง Code การใช้งาน Super method ในภาษา Ruby
```ruby
class Super_Original
  
    def display a = 0, b = 0
        puts "Parent class, 1st Parameter: #{a}, 2nd Parameter: #{b}"
    end
end

class Super_Copy < Super_Original
  
    def display a, b
        
        super
        
        super a
        
        super a, b
        
        super()
        
        puts "This is subclass method"
    end
end

obj = Super_Copy.new
obj.display "ONE", "TWO"
```
<details>

<summary>Output</summary>

>Parent class, 1st Parameter: ONE, 2nd Parameter: TWO\
>Parent class, 1st Parameter: ONE, 2nd Parameter: 0\
>Parent class, 1st Parameter: ONE, 2nd Parameter: TWO\
>Parent class, 1st Parameter: 0, 2nd Parameter: 0\
>This is subclass method

</details>
จากตัวอย่าง Code การใช้งาน Super method obj ได้ส่ง parameter "ONE" และ "TWO" ไปใน display ของ Super_Copy เพราะ obj สร้างมาจาก class Super_Copy จะเห็นได้ว่า ผลลัพธ์ของแต่ละ super จะออกมาไม่เหมือนกัน โดยมีลักษณะดังนี้

- **super** จะส่ง parameter ที่ได้มาจาก obj.display ก็คือ "ONE" และ "TWO" ไปใน display ของ Super Class **โดยอัตโนมัติ**
- **super a** จะส่งไปแค่ parameter "ONE" ทำให้ค่า parameter ของ b=0 ตามที่ display ของ Super Class กำหนดไว้
- **super a, b** จะส่ง parameter ที่ได้มาจาก obj.display ก็คือ "ONE" และ "TWO" ไปใน display ของ Super Class
- **super()** จะไม่ส่งอะไรไปเลย แค่เรียกใช้ method display ของ Super Class ทำให้ค่า parameter ของ a = 0 และ b=0 ตามที่ display ของ Super Class กำหนดไว้

### การใช้งาน Super method ในภาษาอื่นๆ
- ### Java
- ### Python
- ### C

---

## Class Inheritance across different files
ในตัวอย่าง code ต่างๆที่ได้แสดงให้ดูไปเป็นการสืบทอดที่สามารถทำได้หากเราประกาศ class ไว้ไฟล์เดียวกัน แต่เราก็สามารถที่จะสืบทอด class จาก class ที่ประกาศไว้ในไฟล์อื่นๆได้เหมือนกัน โดย

- **require_relative** ใช้เมื่อไฟล์ของ class ที่อยากจะสืบทอด(Super Class)อยู่ใน Folder เดียวกันกับ Sub Class
- **require** ใช้เมื่อไฟล์ของ class ที่อยากจะสืบทอด(Super Class)อยู่ใน Folder คนละ Folder กับ Sub Class

### ตัวอย่าง
ต้องการที่จะ สร้าง class Cat ในไฟล์ cat.rb โดยสืบทอดมาจาก class Lion ในไฟล์ lion.rb ที่อยู่ใน Drive D ใน folder ชื่อ ruby

- อยู่ใน Folder เดียวกัน
 
  ```ruby
  # in cat.rb
  require_relative 'lion' 

  class Cat < Lion
  
  end
  ```
- อยู่คนละ Folder กัน
 
  ```ruby
  # in cat.rb
  require 'D:/folder/ruby/lion'

  class Cat < Lion
  
  end
  ```
---

## References
- 1
- 2
- 3
- 4

---
