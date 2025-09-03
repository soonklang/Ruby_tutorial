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

---

## การใช้งาน Class Inheritance ในภาษาอื่นๆ
- ### Java
- ### Python
- ### C

---

## Method Overriding
