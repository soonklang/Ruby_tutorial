# Ruby Method Aliases
# บทนำ
  ภาษา Ruby เป็นภาษาเชิงวัตถุ(Object-Oriented Programming Language : OOP) ที่ได้รับความนิยมเป็นอย่างมากในหมู่ผู้พัฒนา เพราะมีโครงสร้างที่ยืดหยุ่น อ่านง่าย และหนึ่งในลักษณะเด่นของ Ruby คือ Method Aliases 

# Method Aliases คืออะไร
Method Aliases คือ การสร้างชื่อใหม่ (alias) เพื่อใช้อ้างอิงเมธอดเดิมที่มีอยู่ในคลาสหรือโมดูลเดียวกัน โดยเมธอดที่ถูกอ้างอิงด้วยชื่อ alias จะทำงานเหมือนกับเมธอดต้นฉบับทุกประการ
# การสร้าง Method Aliases ใน Ruby มีด้วยกัน 2 วิธี
1.alias (keyword)
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
alias ใช้สร้าง ชื่อใหม่ให้ method เดิม
hi ---> alias ของ hello
hey ---> alias ของ hello
