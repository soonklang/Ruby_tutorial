


Copy of Introduction to Ruby ConStant
630710128 นาย ณัฐนนท์ อ้นเพ็ชร
​
Ruby Constant
Constant (ค่าคงที่) ในภาษา Ruby คือชื่อที่อ้างถึงค่าที่ ไม่ควรถูกเปลี่ยน ระหว่างการทำงานของโปรแกรม โดยตามปกติจะตั้งชื่อด้วยตัวพิมพ์ใหญ่ทั้งหมด เช่น MAX_USERS, DEFAULT_PORT. หากกำหนดใหม่ Ruby จะขึ้นคำเตือน (warning) เพื่อบอกว่าไม่ควรทำ
กฎการตั้งชื่อ
ชื่อขึ้นต้นด้วยตัวอักษรพิมพ์ใหญ่ (A–Z); ส่วนที่เหลือใช้ตัวอักษร/ตัวเลข/ขีดล่าง _ ได้
ชื่อตัวพิมพ์เล็กถือเป็นตัวแปรปกติ ไม่ใช่ Constant
นิยมใช้ตัวพิมพ์ใหญ่ทั้งหมดคั่นด้วย _ เช่น APP_NAME
Scope และการอ้างอิง
เมื่ออยู่ใน module หรือ class สามารถอ้างอิงได้ด้วยเครื่องหมาย :: เช่น MathConstants::PI. ถ้า Constant อ้างถึงอ็อบเจ็กต์ที่แก้ไขภายในได้ (เช่น Array/Hash) การแก้ไขภายในจะไม่เตือน — ควรใช้ freeze เพื่อป้องกัน
ตัวอย่าง
พื้นฐาน
PI = 3.14159
RADIUS = 5
area = PI * RADIUS**2
puts "พื้นที่วงกลมรัศมี #{RADIUS} คือ #{area}"
# => 78.53975
การกำหนดใหม่ (จะมีคำเตือน)
MAX_USERS = 100
MAX_USERS = 200  # warning: already initialized constant MAX_USERS
Grouping ด้วย Module
module MathConstants
  PI = 3.14159
  E  = 2.71828
end
puts MathConstants::PI  # => 3.14159
ป้องกันการแก้ไขภายใน
WEEKDAYS = %w[Mon Tue Wed Thu Fri].freeze
# WEEKDAYS << "Sat"  # error: can't modify frozen Array
เปรียบเทียบกับภาษา Java / C / Python
​
ภาษา

การประกาศ

คำอธิบาย


Ruby
PI = 3.14159
ชื่อขึ้นต้นพิมพ์ใหญ่ เตือนเมื่อ reassign

Java
public static final double PI = 3.14159;
ใช้ final (มักคู่กับ static) บังคับคงค่าตามไวยากรณ์

C
#define PI 3.14159
const double E = 2.71828;
#define คือแมโครก่อนคอมไพล์; const คือตัวแปรอ่านอย่างเดียว

Python
PI = 3.14159
from typing import Final
E: Final = 2.71828
ไม่มี constant ตามไวยากรณ์ ใช้ธรรมเนียมชื่อพิมพ์ใหญ่ และ Final ช่วย lint/type checker

คลิปนำเสนอ
Presentation (Slides)
รายการอ้างอิง (APA Style) 
• Ruby. (n.d.). Assignment — Constants. Ruby official documentation. Retrieved September 3, 2025, from 
https://docs.ruby-lang.org/en/master/syntax/assignment_rdoc.html#label-Constants
 
• Bozhidar Batsov. (n.d.). Ruby Style Guide — Constants. Retrieved September 3, 2025, from 
https://rubystyle.guide/#constants
 
• Oracle. (n.d.). Java SE Specifications. Retrieved September 3, 2025, from 
https://docs.oracle.com/javase/specs/
 
• cppreference.com. (n.d.). const (C language). Retrieved September 3, 2025, from 
https://en.cppreference.com/w/c/language/const
 
• Python Software Foundation. (2019). PEP 591 – Final qualifier for variables. Retrieved September 3, 2025, from 
https://peps.python.org/pep-0591/
 
• Ruby Association. (n.d.). Ruby Programming Language. Retrieved September 3, 2025, from 
https://www.ruby-lang.org/en/
 
• RubyGems.org. (n.d.). RubyGems Package Manager. Retrieved September 3, 2025, from 
https://rubygems.org/
 
• Bundler.io. (n.d.). Bundler: The best way to manage a Ruby application’s gems. Retrieved September 3, 2025, from 
https://bundler.io/
Previous
Introduction to Ruby ConStant
onpet_n
Last modified 16h ago
