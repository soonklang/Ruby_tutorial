#  Creating Strings in Ruby
What is String in Ruby?
>String ใน Rubyนั้นถูกจัดเก็บโดยใช้ object นอกจากจะใช้เก็บสตริงแล้วยังมี method อีกมากที่ใช้จัดการกับ String ซึ่งมีลำดับอักขระหนึ่งตัวหรือมากกว่านั้น จะเป็นตัวเลข ตัวอักษร หรือสัญลักษณ์ก็ได้
> 
## วิธีสร้าง String ใหม่ใช้วิธี new method ของ String class:
 ```ruby
myString = String.new
=> ""
```
>จากตัวอย่างนี้ได้สร้างสตริงว่างเปล่าขึ้นมา
## วิธีสร้างโดยและเริ่มต้นโดยการส่ง String เป็น argument ไปยัง new method:
 ```ruby
myString = String.new("This is my string. Get your own string")
str = String.new('Another string.')
```
>จากตัวอย่างข้างต้นเป็นการสร้าง String ว่าง
## วิธีสร้างโดยเลือกใช้ method ที่เตรียมไว้โดย Kernel:
 ```ruby
myString = String("This is also my string")
```
## หรือวิธีที่ง่ายที่สุดในการสร้างคือกำหนด String ให้กับชื่อตัวแปร :
 ```ruby
myString = "This is also my string"
myString_1 = 'This is also my string'
```
>เมื่อกำหนด Ruby จะจัดการส่วนที่เหลือให้เอง ซึ่งที่กำหนดที่ใช้ทั้ง " " และ ' ' นั้นทำงานได้เหมือนกัน 
# *Reference *
#### Ruby
- https://www.w3schools.io/ruby-strings/
- https://ruby-doc.org/core-2.6.9/String.html
- https://www.digitalocean.com/community/tutorials/how-to-work-with-strings-in-ruby
- https://docs.ruby-lang.org/en/master/String.html
- https://www.tutorialspoint.com/ruby/ruby_strings.htm
- https://www.geeksforgeeks.org/ruby/ruby-string-basics/
- https://www.codecademy.com/courses/learn-ruby/lessons/introduction-to-ruby/exercises/data-types-numbers-strings-booleans
- https://www.techotopia.com/index.php/Ruby_Strings_-_Creation_and_Basics
#### Python
#### C
#### Java
# *Presentation*
# *Video*
