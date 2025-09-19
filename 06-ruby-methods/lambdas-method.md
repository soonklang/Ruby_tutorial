# Lambdas Method
## บทนำ 
- Lambdas คืออะไร?
  - คือ วัตถุ (Object) ชนิดหนึ่งของคลาส Proc Lambdas เป็น Proc ชนิดพิเศษ
    Lambdas ไว้เก็บชุดคำสั่งไว้ในตัวแปรที่ตั้งขึ้น ไว้ในการนำมาใช้ซ้ำโดยไม่ต้องเขียนซ้ำขึ้นมาใหม่
- Proc คืออะไร?
  - Proc หรือ Procedure คือ วัตถุ (Object) ที่ใช้เก็บชุดคำสั่งที่สามารถ เรียกมาใช้ซ้ำใหม่ได้โดยไม่ต้องเขียนซ้ำ
  - Lambdas คือหนึ่งในวิธีสร้าง ใน Proc
## ตัวอย่าง โค๊ด Lambdas
### ตัวอย่างที่ 1 
```ruby
say_hello = lambda { puts "โย่ววว" }
say_hello.call
```
- อธิบาย
   - เซ็ตว่าตัวแปร say_hello จะเก็บคำสั่ง แสดง คำว่า "โย่ววว" ออกมา
   - say_hello.call เป็นการเรียกใช้คำสั่ง say_hello ออกมา โดยไม่ต้องเขียนคำสั่งซ้ำ
### ตัวอย่างที่ 2 แบบใช้ตัว -> แทน lamda
```ruby
say_hello = -> { puts "โย่ววว" }
say_hello.call
```
- อธิบาย
   - เซ็ตว่าตัวแปร say_hello จะเก็บคำสั่ง แสดง คำว่า "โย่ววว" ออกมา
   - say_hello.call เป็นการเรียกใช้คำสั่ง say_hello ออกมา โดยไม่ต้องเขียนคำสั่งซ้ำ
### ตัวอย่างที่ 3 
```ruby
say_bye = ->(name) { puts "โชคดี #{name}" }

say_bye.call("พี")  
```
- อธิบาย 
   - เซ็ตว่าตัวแปร say_bye จะเก็บคำสั่ง แสดง คำว่า "โชคดี" พร้อมกับชื่อ ที่รับ input จากผู้ใช้ออกมาเป็นชือที่ผู้ใช้ใส่เข้ามา
   - say_ฺbye.call เป็นการเรียกใช้คำสั่ง say_bye ออกมาโดยไม่ต้องเขียนคำสั่งซ้ำ
### ตัวอย่างที่ 4 lamda ข้อมูลหลายๆคัว
```ruby
names = ["P", "Oat", "Teh"]

say_hi = ->(name) { "สวัสดี #{name}" }

names.each do |n|
  puts say_hi.call(n)
end
```
- อธิบาย
  - สร้างตัว lamda ไว้ใช้เก็บคำสั่ง ไว้ สวัสดี ชื่่อคนที่ใส่เข้ามาทั้ง สาม ชื่อ
  - และวนลูป สวัสดีทุกคน
### ตัวอย่างที่ 5 method ปกติ ที่ไม่ใช่ lamda
```ruby
def say_hello(name)
  puts "สวัสดี #{name}"
end

say_hello("พี")   
```
- อธิบาย
  - ปกติจะเก็บไว้ใน ฟังก์ชัน แต่ lamda จะเก็บไว้ในตัวแปรจะใช้ได้ยืดหยุ่นกว่า
## Lambdas ต่างยังไงกับ Proc
- Lambdas และ Proc เป็นรูปแบบ วัตถุ (Object) เหมือนกัน
- Lambda ต้องส่งจำนวน argument (จำนวนตัวแปรรับค่า) เข้าตามที่ได้เขียนคำสั่งไว้ ถ้าส่งน้อยหรือเกินที่ตั้งไว้จะ error
- Proc ส่ง argument น้อยหรือเกินจำนวนที่ตั้งไว้ได้
- Proc เวลา return จะออกจาก method หลักเลย แต่ Lambdas เวลา return จะออกแค่ในตัวของ Lambda เลย
## ตัวอย่าง Proc
```ruby
p = Proc.new { |a, b| "#{a} กับ #{b}" }

puts p.call(1, 2)       # => "1 กับ 2"
puts p.call(1)          # => "1 กับ "   (b เป็น nil)
puts p.call(1, 2, 3)    # => "1 กับ 2" (argument ที่เกินมาถูกละทิ้ง)
```
- อธิบาย
  - ในตัวนี้รับ argument มา 2 ค่า ถ้าส่งค่ามา 2 ค่า เช่น (1 , 2) ก็จะแสดงผลเป็น "1 กับ 2"
  - ถ้าส่งค่า 1 ค่า เช่น (1) ก็จะแสดงผลเป็น "1 กับ "
  - ถ้าส่งค่า เกิน 2 ค่า เช่น (1,2,3) ก็จะแสดงผลเป็น "1 กับ 2" (ค่าที่ส่งเกินมาจะถูกทิ้ง)
## เปรียบเทียบ Lambdas ในภาษา Java/C/Python 
 ### Python 
 ```Python
# สร้าง lambda
add = lambda x, y: x + y

# เรียกใช้งาน
add(3, 5)   # => 8
 ```
 -อธิบาย เปรียบเทียบกับ Ruby
  - Python สามารถสร้าง lambda ได้เลยโดยไม่จำเป็นต้องเขียน def เหมือนกับ Ruby
  - Python เขียน ได้แค่ expression(นิพจน์) บรรทัดเดียว แต่ Ruby เขียนได้หลายบรรทัด
  - Python lambda เหมาะกับการเขียนสั้นๆไม่สามารถเขียน logic เช่น if, for, while, try-except ได้ ต่างกับ Ruby ที่สามารถเขียนได้
### Java (เวอร์ชั่น 8 ขึ้นไป)
 ```Java
// ประกาศ Functional Interface 
@FunctionalInterface
interface MathOp {
    int operate(int x, int y);
}

// ประกาศ lambda
MathOp add = (x, y) -> x + y;
System.out.println(add.operate(2, 3)); // 5
 ```
-อธิบาย เปรียบเทียบกับ Ruby
  - Java ต้องประกาศ Functional Interface ไว้ผูกกับตัวของ lambda ไม่เหมือนกับ Ruby ที่ประกาส lambda ได้เลย
  - Java Syntax จะไม่ง่ายเหมือนกับตัว Python และ Ruby
  - Java ใช้งานได้หลายบรรทัดเหมือน Ruby ไม่เหมือนกับ Python ที่เขียน Logic ซับซ้อนไม่ได้
### C (ไม่มี Lambda)
 ```C
// สร้างฟังก์ชันปกติ
int add(int x, int y) {
    return x + y;
}

// ส่ง pointer ไปยัง function ได้
int calc(int (*op)(int, int), int a, int b) {
    return op(a, b);
}

printf("%d\n", calc(add, 2, 3)); // 5
 ```
-อธิบาย เปรียบเทียบกับ Ruby
  - C ในภาษานี้จะไม่มีตัว lambda ไม่สามารถสร้างได้เหมือนตัวอื่นๆ เช่น Java,Pythonm,Ruby
  - C ต้องนิยาม function ปกติก่อน แล้วส่งpointerไปที่ function ได้ ไม่สามารถเก็บฟังชั่นได้เหมือนตัว lambda
## คลิปนำเสนอ
   https://drive.google.com/file/d/19-oNJAaLRk7oijknkB5uEy58weSBfvhx/view?usp=drive_link
## Presentation (slides)
   https://docs.google.com/presentation/d/1Lcl3X-SVmpzf_I3J6crufOhmldzyWegC/edit?usp=sharing&ouid=104204840378548053209&rtpof=true&sd=true
## แหล่งที่มาอ้างอิง
### Ruby
-เว็บ geeksforgeeks | https://www.geeksforgeeks.org/ruby/lambda-function-ruby/ เนื้อหาส่วน lambda-function-ruby
-เว็บ ruby-doc.org | https://ruby-doc.org/3.4.1/Proc.html เนื้อหาส่วน class Proc
-เว็บ ocs.ruby-lang.org | https://docs.ruby-lang.org/en/master/Prism/LambdaNode.html เนื้อหาส่วน LambdaNode
### Python 
-เว็บ w3schools | https://www.w3schools.com/python/python_lambda.asp เนื้อหาส่วน Python Lambda
-เว็บ docs.python.org | https://docs.python.org/3/reference/expressions.html#lambda เนื้อหาส่วน Lambdas Expressions
### Java 
-เว็บ oracle | https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html เนื้อหาส่วน Lambda Expressions
-เว็บ w3schools | https://www.w3schools.com/java/java_lambda.asp เนื้อหาส่วน Java Lambda Expressions
### C
-เว็บ stackoverflow | https://stackoverflow.com/questions/2173210/synchronizing-sound 
