# Ruby Method Aliases
# บทนำ
  ภาษา Ruby เป็นภาษาเชิงวัตถุ(Object-Oriented Programming Language : OOP) ที่ได้รับความนิยมเป็นอย่างมากในหมู่ผู้พัฒนา เพราะมีโครงสร้างที่ยืดหยุ่น อ่านง่าย และหนึ่งในลักษณะเด่นของ Ruby คือ Method Aliases 

# Method Aliases คืออะไร
Method Aliases คือ การสร้างชื่อใหม่ (alias) เพื่อใช้อ้างอิงเมธอดเดิมที่มีอยู่ในคลาสหรือโมดูลเดียวกัน โดยเมธอดที่ถูกอ้างอิงด้วยชื่อ alias จะทำงานเหมือนกับเมธอดต้นฉบับทุกประการ
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
