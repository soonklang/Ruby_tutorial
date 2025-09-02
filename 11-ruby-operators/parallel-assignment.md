# Parallel Assignment
  ในRubyมีสิ่งที่เรียกว่า "การประกาศตัวแปลหลายตัวในบรรทัดเดียวกัน" หรือ "Parallel Asignmrnt" สามารถเพิ่มความสะดวกสบายให้กับผู้ใช้งาน 
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
## output is
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
## output is
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
## output is
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
## output is
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
## output is
```ruby
2
3
4
```
?แล้วถ้ามีlvalueหลังlvalueที่เป็นsplat operatorหละ ->ผลลัพธ์ก็จะเป็นแบบนี้
```ruby
num1, *num2 = 1, 2, 3, 4
puts "num1:
puts "num2: 
puts "num3: 
```
## output is
```ruby
num1: 1
num2: [2, 3]
num3: 4
```
