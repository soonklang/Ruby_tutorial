# Parallel Assignment
  ในRubyมีสิ่งที่เรียกว่า "การประกาศตัวแปรหลายตัวในบรรทัดเดียวกัน" หรือ "Parallel Asignment" สามารถเพิ่มความสะดวกสบายให้กับผู้ใช้งาน 
  แต่ก็สามารถทำให้ผู้ใช้งานสับสนถ้าไม่รู้เงื่อนไขและsyntaxดังต่อไปนี้

## Syntax :
```ruby
lvalue1,... = rvalue2,...
  lvalue คือนิพจน์ที่มีตำแหน่งในหน่วยความจำ เช่น x
  rvalue คือนิพจน์ชั่วคราวที่ไม่มีตำแหน่งหน่วยความจำ เช่น 10
              x = 10
```
## ตัวอย่างCode
```ruby                     
a, b, c = 2, 3, 4          
puts a, b, c               
```
+ output is
```ruby              
2                          
3                          
4                          
```

## เงื่อนไข :
1.ถ้ามีlvalue 1 ตัว และมีrvalueมากกว่า 1 ตัว Rubyจะสร้างarrayเพื่อเก็บrvalueเหล่านั้น เพื่อเก็บในlvalueในบรรทัดนั้น เช่น
```ruby
x = 2, 3, 4
puts x
```
+ output is
```ruby
2
3
4
```
+แต่ถ้ามีlvalueมากกว่าrvalue Rudyจะsetlvalueที่เกินเป็น "Nil" เช่น
```ruby
x, y, z = 2, 3
puts x, y, z.class
```
+ output is
```ruby
2
3
NilClass
```
2.ถ้ามีlvalueมากกว่า 1 แต่มีarrayแค่อันเดียว Rudyจะนำค่าในarrayแต่ละตัวไปใส่ในlvalueตามลำดับจากซ้ายไปขวา เช่น
```ruby
a, b, c = [ 9, 3, 5 ]
puts a, b, c
```
+ output is
```ruby
9
3
5
```
3.ถ้าlvalueตัวสุดท้ายมี "*" (ดอกจันทร์)อยู่ข้างหน้า(เรียกว่าsplat operator) ค่าทั้งหมดที่เหลืออยู่ของrvaluesจะเป็นarrayของlvalueของตัวนั้น
```ruby
num1, *num2 = 1, 2, 3, 4
puts num2
```
+ output is
```ruby
2
3
4
```
?แล้วถ้ามีlvalueหลังlvalueที่เป็นsplat operatorหล่ะ ->ผลลัพธ์ก็จะเป็นแบบนี้
```ruby
num1, *num2, num3 = 1, 2, 3, 4
puts "num1: #{num1}"
puts "num2: #{num2.inspect}"
puts "num3: #{num3}"
```
+ output is
```ruby
num1: 1
num2: [2, 3]
num3: 4
```
4.ในทำนองเดียวกัน ถ้าrvalueตัวสุดท้ายคือarray สามารถนำหน้าด้วยเครื่องหมายดอกจันทร์(*) เพื่อบอกว่าคือarray(จริงๆแล้วไม่จำเป็นต้องทำก็ได้ เพราะถ้าเป็นrvalueตัวสุดท้ายทางขวามือ จะเป็นarrayโดยอันโนมัติ)
```ruby
num3 = [1, 2, 3, 4]
num1, num2 = 15, *num3
puts num2
```
+ output is
```ruby
1
#เนื่องจากRubyมองว่า*num3ก็คือarrayเหมือนกับที่เราใส่ค่าrvalueเป็นarray num2จึงสามารถดึงค่าตัวแรกใน*num3มาเป็นของตัวเองได้
```
# Paralell Assighment in c | java | python
## In C Language
  ในภาษาcสามารถประกาศได้หลายรูปแบบ ในdata typeที่เหมือนกันดังนี้
1.ประการโดยมีลูกน้ำ หรือcomma(,) ขั้นระหว่างตัวแปรกับค่าที่กำหนดให้ตัวแปรนั้นๆ เช่น
```c
int x = 5, y = 6, z = 50;
```
2.ถ้ามีตัวแปรหลายตัว แต่ทุกตัวมีค่าเท่ากัน สามารถประกาศแบบนี้ได้
```c
int x, y, z;
x = y = z = 50;
```
## In java Language
  ในภาษาjavaก็สามารถประกาศได้หลายรูปแบบ ในdata typeที่เหมือนกันเช่นกัน
1.ประการโดยมีลูกน้ำ หรือcomma(,) ขั้นระหว่างตัวแปรกับค่าที่กำหนดให้ตัวแปลนั้นๆ เช่น
```java
int x = 5, y = 6, z = 50;
```
2.ประกาศแบบหลายตัวแปร แต่มีค่าเท่ากันทุกตัวก็ได้เหมือนภาษา c
```java
int x, y, z;
x = y = z = 50;
```
## In Python Language
  ส่วนในภาษาPythonอนุญาตให้ประกาศตัวแปรหลายตัวในหนึ่งบรรทัดได้
1.ประการโดยมีลูกน้ำ หรือcomma(,) ขั้นระหว่างตัวแปรกับค่าที่กำหนดให้ตัวแปรนั้นๆ เช่น
```python
x, y, z = "Orange", "Banana", "Cherry"
```
2.ประกาศแบบ 1 ค่า หลายตัวแปร
```python
x = y = z = "Orange"
```
3.สามารถประกาศให้rvalueเป็นarrayเหมือนRubyได้
```python
fruits = ["apple", "banana", "cherry"]
x, y, z = fruits
```
## ตารางเปรียบเทียบ
|     เงื่อนไข/รูปแบบ                             | Ruby | C    | Java | Python|
|-----------------------------------------------|------|------|------|--------|
| lvalue 1 ตัว rvalueหลายตัว                     | ✓ |  |   |✓|
| lvalueมากกว่า 1 แต่มีarrayแค่อันเดียว              | ✓ |  |   |✓|
| lvalueตัวสุดท้ายมี "*" ค่าrvalueหลังจากนั้นเป็นarray  | ✓ |  |  |  |
| rvalueตัวสุดท้ายคือarray ใส่ * ได้                 | ✓ |  |  |  |
| lvalueมากกว่าrvalue setlvalueที่เกินเป็น "Nil"     | ✓ |  |  |  |
| int x = 5, y = 6, z = 50;                     |   |✓ |✓|  |
| x = y = z = 50;                               |   | ✓|✓|✓|
## VIDEO
https://drive.google.com/file/d/17vsLNjGC0TUfrqYt-DSj9sOtFMNiN9Ym/view?usp=sharing
## SLIDE
https://drive.google.com/file/d/1OgqllMyRIMrnh4RBM8eSJgKwMNT7vFww/view?usp=sharing
## REFERENCE
1.GeeksforGeeks. 27 Jul 2020. "Parallel Assignment in Ruby". สืบค้นจาก https://www.geeksforgeeks.org/ruby/parallel-assignment-in-ruby/ (สืบค้นวันที่ 2 กันยายน 2568)

2.w3schools. "C Declare Multiple Variables". สืบค้นจาก https://www.w3schools.com/c/c_variables_multiple.php. 
(สืบค้นวันที่ 3 กันยายน 2568)

3.w3schools. "Declare Many Variables". สืบค้นจาก https://www.w3schools.com/java/java_variables_multiple.asp. 
(สืบค้นวันที่ 3 กันยายน 2568)

4.w3schools. "Python Variables - Assign Multiple Values". 
สืบค้นจาก https://www.w3schools.com/python/python_variables_multiple.asp. (สืบค้นวันที่ 3 กันยายน 2568)
