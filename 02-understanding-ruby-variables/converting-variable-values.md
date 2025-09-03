# Converting Variable Values
Converting variable values  คือ การแปลงค่าของตัวแปรจากข้อมูลชนิดหนึ่งไปเป็นอีกชนิดหนึ่งซึ่งเป็นงานที่เกิดขึ้นบ่อยในภาษา ruby โดยเฉพาะเมื่อต้องทำงานกับข้อมูลหลายชนิด 
การจะเขียนโปรแกรม Ruby ให้ได้อย่างมีประสิทธิภาพนั้น จึงต้องเข้าใจวิธีการแปลงค่าของตัวแปรเหล่านี้


### ทำไมถึงต้องแปลงค่าตัวแปร?
ภาษา ruby ถูกจัดว่าเป็นภาษาที่ dynamically-typed คือ ไม่ได้รู้ชนิดข้อมูลของตัวแปรตั้งแต่ช่วงแรก หรือ compile time แต่จะรู้ชนิดข้อมูลของตัวแปรในช่วง run time
ซื่งแปลว่าเวลาโค้ดทำงานถ้าส่งค่าชนิดข้อมูลของตัวแปรผิดโปรแกรมอาจพังได้เลย ดังนั้นจึงต้องแก้ไขด้วยการแปลงค่าชนิดของข้อมูลให้เป็นชนิดที่ต้องการ


### วิธีการแปลงค่าตัวแปรจากชนิดข้อมูลใน Ruby
วิธีการแปลงค่าตัวแปรในภาษา ruby มีด้วยกัน 2 วิธีคือ

1.Implicit Conversion 
เป็นการแปลงค่าที่เกิดขึ้นอัตโนมัติโดยตัวแปลภาษา Compiler เพื่อให้โปรแกรมสามารถทำงานต่อไปได้โดยไม่เกิดข้อผิดพลาด มักจะเกิดขึ้นเมื่อมีการดำเนินการระหว่างข้อมูลคนละชนิด และการแปลงนั้นปลอดภัยไม่ทำให้ข้อมูลสูญหาย

2.Explicit Conversion
เป็นการแปลงค่าที่ผู้ใช้แปลงค่าเอง ซึ่งบ่อยครั้งเป็นการแปลงที่อาจไม่ปลอดภัย หรือทำให้ข้อมูลสูญหายได้


# ตัวอย่าง
### แปลงค่าตัวแปร String → Integer หรือ Float
คำอธิบาย:
เป็นการกำหนดค่าของตัวอักษรแล้วแปลงค่าของตัวอักษรให้เป็นตัวเลขจำนวนเต็ม และทศนิยม โดยใช้เมธอด .to_i และ .to_f
```ruby   
num_str = "123"
int_str = str.to_i
float_str = str.to_f

puts num_str
put num_str.class
puts int_str
put int_str.class
puts float_str
put float_str.class
```
ผลลัพธ์:
```
"123"
String
123
Integer
123.0
Float
```

### แปลงค่าตัวแปร Integer หรือ Float → String
```ruby   
num_int = 123
num_float = 3.14
str_int = num_int.to_s
str_float = num_float.to_s

puts str_int
put str_int.class
puts str_float
put str_float.class
```
ผลลัพธ์:
```
"123"
String
"3.14"
String
```
คำอธิบาย:
เป็นการกำหนดค่าของเลขจำนวนเต็ม และเลขทศนิยม แล้วแปลงค่าให้เป็นตัวตัวอักษร โดยใช้เมธอด .to_s

### แปลงค่าตัวแปร Array → String
```ruby   
arr = [1, 2, 3, 4, 5]
str = arr.join(", ")

puts str
```
ผลลัพธ์:
```
"1, 2, 3, 4, 5"
```
คำอธิบาย:
เป็นการกำหนดค่าของอาเรย์ แล้วแปลงค่าให้เป็นตัวตัวอักษร โดยใช้เมธอด .join()

# เปรียบเทียบภาษา ruby กับภาษา Java/C/Python


# References
[1] K. Newton, "Ruby type conversion," KDD Newton, Sep. 9, 2021. [Online]. Available: https://kddnewton.com/2021/09/09/ruby-type-conversion.html. [Accessed: Sep. 3, 2025].

[2] K. Newton, "Variables: declaration and usage in Ruby," MarcusCode, Sep. 25, 2019. [Online]. Available: https://marcuscode.com/lang/ruby/variables-basic. [Accessed: Sep. 3, 2025].

[3] K. Newton, "Understanding Ruby variables," Techotopia. [Online]. Available: https://www.techotopia.com/index.php/Understanding_Ruby_Variables. [Accessed: Sep. 3, 2025].

[4] GeeksforGeeks, "How To Convert Data Types in Ruby?," GeeksforGeeks, Mar. 26, 2024. [Online]. Available: https://www.geeksforgeeks.org/ruby/how-to-convert-data-types-in-ruby/. [Accessed: Sep. 3, 2025].

[5] "String#to_i," Ruby-doc.org, 2025. [Online]. Available: https://ruby-doc.org/3.4.1/String.html#method-i-to_i. [Accessed: Sep. 3, 2025].

[6] K. Sonmez, *Introduction to Programming with Ruby*. Launch School, 2017. [Online]. Available: https://launchschool.com/books/ruby/read/basics#typeconversion. [Accessed: Sep. 3, 2025].

