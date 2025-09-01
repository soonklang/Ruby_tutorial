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
-W3schools.io. (n.d.). *Ruby Strings*. W3schools.io. Retrieved September 1, 2025, from<br>
https://www.w3schools.io/ruby-strings/
- Ruby-doc.org. (n.d.). *Class: String (Ruby 2.6.9)*. Ruby-doc.org. Retrieved September 1, 2025, from<br>
https://ruby-doc.org/core-2.6.9/String.html
-  DigitalOcean. (2022, August 3). *How To Work With Strings in Ruby*. DigitalOcean. Retrieved September 1, 2025, from<br>
https://www.digitalocean.com/community/tutorials/how-to-work-with-strings-in-ruby
- Ruby-lang.org. (n.d.). *String — Ruby master*. Ruby-lang.org. Retrieved September 1, 2025, from<br>
https://docs.ruby-lang.org/en/master/String.html
- TutorialsPoint. (n.d.). *Ruby – Strings*. TutorialsPoint. Retrieved September 1, 2025, from<br>
https://www.tutorialspoint.com/ruby/ruby_strings.htm
- GeeksforGeeks. (2024, May 20). *Ruby | String Basics*. GeeksforGeeks. Retrieved September 1, 2025, from<br>
https://www.geeksforgeeks.org/ruby/ruby-string-basics/
- Codecademy. (n.d.). *Data Types: Numbers, Strings, and Booleans*. Codecademy. Retrieved September 1, 2025, from<br>
https://www.codecademy.com/courses/learn-ruby/lessons/introduction-to-ruby/exercises/data-types-numbers-strings-booleans
- Smyth, N. (2016, November 2). *Ruby Strings - Creation and Basics*. Techotopia. Retrieved September 1, 2025, from<br>
https://www.techotopia.com/index.php/Ruby_Strings_-_Creation_and_Basics
#### Python
#### C
#### Java
# *Presentation*
# *Video*
