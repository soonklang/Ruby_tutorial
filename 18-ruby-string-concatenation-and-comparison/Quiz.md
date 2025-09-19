## Acessing String Elements


## Case Insensitive String Compairsions

## Comparing Ruby String (Case Sensitive)

ผลลัพธ์ของการใช้ spaceship ระหว่าง "Cat" กับ "cat" คืออะไร

```
str1 = "Cat"
str2 = "cat"

puts str1 == str2

```
<details close>
<summary><b>output</b></summary>
  <pre> -1
 </pre>
</details>


## Concatenating String in Ruby

จงบอกผลลัพธ์ที่ได้จากโปรแกรมนี้
```
a = "When is your " 
b = "daughter's "
c = "graduation "
d = "ceremony?"

puts a.concat(b).concat(c)+d
puts a

```
<details close>
<summary><b>output</b></summary>
<pre> 
 When is your daughter's graduation ceremony?
 When is your daughter's graduation 
</pre>
</details>

## Freezing a Ruby String
ในภาษา Ruby สตริงแต่ละตัวมีสถานะถูก Freeze อยู่หรือไม่?
```ruby
s1 = "ruby"
s2 = s1.freeze
s3 = +s1
s4 = -s1
s5 = +s2
s6 = -s2

puts s1.frozen?
puts s2.frozen?
puts s3.frozen?
puts s4.frozen?
puts s5.frozen?
puts s6.frozen?
```
<details>
<summary> เฉลย </summary>
  
```ruby
  puts s1.frozen? == True เพราะ ถูก freeze ด้วย s1.freeze
  puts s2.frozen? == True เพราะ เป็น reference ของ s1 → frozen เหมือนกัน
  puts s3.frozen? == False เพราะ +s1 คืนค่า mutable copy
  puts s4.frozen? == True เพราะ -s1 คืนค่า frozen copy
  puts s5.frozen? == False เพราะ +s2 คืนค่า mutable copy แม้ต้นฉบับ frozen
  puts s6.frozen? == True เพราะ -s2 คืนค่า frozen copy
```
</details>
