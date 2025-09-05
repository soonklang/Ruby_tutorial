# Ruby Method Aliases
# บทนำ
  ภาษา Ruby เป็นภาษาเชิงวัตถุ(Object-Oriented Programming Language : OOP) ที่ได้รับความนิยมเป็นอย่างมากในหมู่ผู้พัฒนา เพราะมีโครงสร้างที่ยืดหยุ่น อ่านง่าย และหนึ่งในลักษณะเด่นของ Ruby คือ Method Aliases 

# Method Aliases คืออะไร
Method Aliases คือ การสร้างชื่อใหม่ (alias) เพื่อใช้อ้างอิงเมธอดเดิมที่มีอยู่ในคลาส (class) หรือโมดูล (Module)เดียวกัน โดยเมธอดที่ถูกอ้างอิงด้วยชื่อ alias จะทำงานเหมือนกับเมธอดต้นฉบับทุกประการ
# การสร้าง Method Aliases ใน Ruby มีด้วยกัน 2 วิธี
# 1.alias (keyword)
   ตัวอย่างโค้ด
   ```ruby
class Greeting
  def hello
    puts "Hello, world!"
  end

  alias hi hello   #ส่วนที่มีการใช้ alias (keyword)
  alias :hey :hello #ส่วนที่มีการใช้ alias (keyword)
end

g = Greeting.new
g.hello  # => "Hello, world!"
g.hi     # => "Hello, world!"
g.hey    # => "Hello, world!" 
```
อธิบาย

alias ใช้สร้างชื่อใหม่ให้ method เดิม จากโค้ดตัวอย่างคือ
```
hi ---> alias ของ hello

hey ---> alias ของ hello
```


# 2.alias_method
  ตัวอย่างโค้ด
  ```ruby
  module Mod
  alias_method :orig_exit, :exit  #ส่วนที่มีการใช้ alias_method
  def exit(code=0)
    puts "Exiting with code #{code}"
    orig_exit(code)
  end
end
include Mod
exit(99)
```

อธิบาย

alias_method ใช้สร้างชื่อใหม่ให้ method เดิม จากโค้ดตัวอย่างคือ
```
alias_method :orig_exit, :exit
orig_exit  ---> alias ของ exit
```

# สรุปความแตกต่างระหว่าง alias กับ alias_method

| หัวข้อ | alias | alias_method |
| --------------- | --------------- | --------------- |
| ประเภท | Keyword ของภาษา Ruby | Method ของ Module |
| การใช้งาน | alias new_name old_name | alias_method :new_name, :old_name |
| ประเภทของ Argument | ได้ทั้ง string และ symbol | ได้แค่เฉพาะ symbol |
| การสืบทอด (Inheritance) | ไม่ส่งผลต่อคลาสลูก (subclass) | ส่งผลต่อคลาสลูก |

# เปรียบเทียบกับภาษาอื่นๆ
# 1.ภาษา Python
ในภาษา Python นั้น ไม่มี alias แต่มี Function def(define) ที่ใช้เพื่อสร้างหรือนิยามฟังก์ชัน เมื่อต้องการสร้างฟังก์ชันใหม่ 

โค้ดตัวอย่างการใช้งาน Function def
```python
def greet():
    print("Hello")
#สร้าง alias
say_hello = greet
say_hello()  # => Hello
```
อธิบาย

ในภาษา Python นั้น การสร้าง alias ของฟังก์ชันทำได้ด้วยการ assign(การกำหนดค่าให้กับตัวแปร) ให้ชี้ไปยังฟังก์ชันเดิม ซึ่งในโค้ดตัวอย่างคือ 'say_hello = greet' ทำให้ทั้งสองตัวแปรเรียกฟังก์ชันเดียวกัน แต่หาก reassign(การเปลี่ยนค่าของตัวแปร ไปเป็นค่าใหม่) ฟังก์ชันต้นฉบับ alias จะยังชี้ไปยังฟังก์ชันเดิมที่ถูก assign ก่อนหน้านั้น


# 2.ภาษา Java
ในภาษา Java นั้น ไม่มี alias สำหรับ method แบบ Ruby/Python ทำให้ต้องสร้าง wrapper method ขึ้นมาแทนแทน

**Wrapper method ใน Java คือการสร้างเมธอดใหม่ที่เรียกเมธอดเดิมภายในตัว body ของมัน
```java
public class Greeter {
    public void greet() {
        System.out.println("Hello");
    }
    public void sayHello() {
        greet();  // wrapper method
    }
}
```

อธิบาย

ในโค้ดตัวอย่างนี้ เมธอด sayHello() ทำหน้าที่เป็น alias ของ greet() โดยการเรียก sayHello() จะทำให้เกิดการเรียก greet() ภายใน ซึ่งเป็นวิธีการที่ใช้ใน Java เพื่อให้เมธอดหนึ่งสามารถถูกเรียกด้วยชื่ออื่นได้ (wrapper method)


# สรุปเปรียบเทียบ alias ในภาษาต่างๆ (Python, Java, C)
| ภาษา | การ Alias | วิธีทำ |
| --------------- | --------------- | --------------- |
| Ruby | ✅ มี alias / alias_method | alias, alias_method |
| Python | ✅ มีการ assign | new_name = old_func |
| Java | ❌ ไม่มีการ Alias | wrapper method |
| C | ❌ ไม่มีการ Alias | function pointer |



# แหล่งอ้างอิง
# Ruby :
https://docs.ruby-lang.org/en/3.2/syntax/miscellaneous_rdoc.html  ใช้ในการอ้างอิง alias  , เปรียบเทียบความแตกต่าง

https://www.rubydoc.info/stdlib/core/Module:alias_method  ใช้ในการอ้างอิง alias_method

# Python :
https://docs.python.org/3/tutorial/controlflow.html?utm_source=#defining-functions ใช้ในการอ้างอิง python

# Java
https://docs.oracle.com/javase/specs/jls/se14/html/jls-8.html#jls-8.4   
