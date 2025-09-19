# Ruby and Variable Dynamic Typing
ใน Ruby ตัวแปรไม่ได้มีชนิดตายตัว (dynamically typed):  
โฟกัสที่ **“ทำอะไรได้”** มากกว่า **“เป็นชนิดอะไร”**
## ตัวอย่าง
### 1.ผูกค่าใหม่ → ชนิดเปลี่ยนตามค่า

```ruby
# dynamic binding
x = 42       # Integer
x = "42"     # String
x = 3.14     # Float
x = [1, 2, 3]# Array
```
### 2.โฟกัสที่ความสามารถ (duck typing)

```ruby
def stringify_2_things(a, b)
  [a, b].map(&:to_s).join(", ")
end

stringify_2_things(123, :ok)    # => "123, ok"
stringify_2_things(Time.now, 7) # => "2025-09-03 12:34:56 +0700, 7"
```
ใช้เมธอด `to_s` โดยไม่ต้องรู้ชนิดที่แน่นอน — แนวทางนี้สอดคล้องกับ duck typing
### 3.ตรวจความสามารถด้วย respond_to?
```ruby
user = "Aom"
user.respond_to?(:upcase)   # => true
user.respond_to?(:nonstop)  # => false
```
### 4.ใช้ method_missing เพื่อ Metaprogramming
```ruby
class Lazy
  def method_missing(name, *args, &blk)
    "No method '#{name}', but I'll handle it anyway."
  end
end

Lazy.new.anything
# => "No method 'anything', but I'll handle it anyway."
```
## เปรียบเทียบกับ Java / C / Python
| ภาษา   | ลักษณะการจัดการตัวแปร                 | ตัวอย่างการประกาศใช้                 |
|--------|------------------------------------|--------------------------------------|
| Ruby   | ไดนามิก, เน้น duck typing           | x = 10x = "ten"|
| Java   | Static Typing    | int n = 10;   n = "ten";  // ❌ คอมไพล์ไม่ผ่าน   |
| C      | Static Typing    | int n = 10;    n = "ten";  // ❌ ผิดชนิดตั้งแต่คอมไพล์  |
| Python | Dynamic Typing   | x: int = 3     # ไม่บังคับขณะรัน  x = "three"  # ทำได้ แต่ตัวตรวจประเภท (เช่น mypy) จะแจ้งเตือน      |
------------
## ข้อควรระวังเมื่อใช้ Dynamic Typing
- บั๊กเล็ดรอด:การเปลี่ยนชนิดโดยไม่ตั้งใจทำให้บั๊กโผล่ตอนรัน → แนะนำให้เขียนเทสต์และใช้ respond_to? แทนการเช็คชนิดตรง ๆ
- De Facto Interface: สื่อสารสัญญาของเมธอดผ่าน README/คอมเมนต์/ชื่อเมธอดที่ชัดเจน
- การแปลงชนิด: ใช้เมธอดครอบ เช่น Integer(str), Float(str), to_s เพื่อควบคุมให้ชัดเจน
-----
### คลิปนำเสนอ
https://www.canva.com/design/DAGzbKeRxcA/bnCF4jYXVOxO0iLwOkJjtw/edit?utm_content=DAGzbKeRxcA&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton
-----
### Presentation (slides)
-----
### Reference 
- docs.ruby-lang.org. (n.d.). Documentation for Ruby (master). Ruby Language.
เข้าข้ถึงถึเมื่อ September 03, 2025, จาก https://docs.ruby-lang.org/en/master/
- Ruby stdlib. (n.d.). Object#respond_to?. เข้าข้ถึงถึเมื่อ September 03, 2025, จาก
https://www.rubydoc.info/stdlib/core/Object%3Arespond_to%3F
- Ruby stdlib. (n.d.). BasicObject#method_missing. เข้าข้ถึงถึเมื่อ September 03,
2025, จาก https://rubydoc.info/stdlib/core/BasicObject%3Amethod_missing
- Oracle. (2013). The Java® Language Specification, Java SE 7 Edition —
Chapter 4: Types, Values, and Variables. เข้าข้ถึงถึเมื่อ September 03, 2025, จาก
https://docs.oracle.com/javase/specs/jls/se7/html/jls-4.html
- cppreference.com. (2025, January 8). C language — Type (compatible type).
เข้าข้ถึงถึเมื่อ September 03, 2025, จาก
https://en.cppreference.com/w/c/language/compatible_type.html
- Van Rossum, G., Lehtosalo, J., & Langa, Ł. (2014). PEP 484 — Type Hints.
Python Software Foundation. เข้าข้ถึงถึเมื่อ September 03, 2025, จาก
https://peps.python.org/pep-0484/
- Python Software Foundation. (2025). typing — Support for type hints. เข้าข้ถึงถึ
เมื่อ September 03, 2025, จาก https://docs.python.org/3/library/typing.html
- Smyth, N. (2012). Ruby Essentials. Techotopia. เข้าข้ถึงถึเมื่อ September 03, 2025,
จาก https://www.techotopia.com/index.php/Ruby_Essentials
- TutorialsPoint. (n.d.). Ruby Tutorial. เข้าข้ถึงถึเมื่อ September 03, 2025, จาก
https://www.tutorialspoint.com/ruby/index.htm
