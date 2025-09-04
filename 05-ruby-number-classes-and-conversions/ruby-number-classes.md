# Ruby Number Classes 
 Ruby Number Classes and conversions คือ แทบทุกอย่างภายใน Ruby มันคือวัตถุ (object) บางทีสิ่งที่น่าประหลาดใจมากที่สุด นั่นก็คือ มันเป็นจำนวนคู่ (even) หรือ ตัวเลขคู่ เป็น วัตถุ (object) ใน Ruby และ ภาษาโปรแกรมอื่นๆ โดยส่วนใหญ่แล้วจะถือว่า ตัวเลข (numbers) เป็น primitive (ชนิดข้อมูลพื้นฐาน) ไม่ใช่ วัตถุ (object) หรือโดยที่พื้นฐานหรือสาระสำคัญเลยจะหมายถึง พวกมันเป็นส่วนประกอบพื้นฐาน (building blocks) จากสิ่งที่วัตถุ(object) สร้างขึ้น และถัดมา แต่ละประเภทตัวเลข (number type) จะมีความหมายที่เกี่ยวข้อง คลาสของตัวเลข(number class) และ สามารถ ถูกจัดการหรือถูกนำไปใช้ โดยใช้ เมธอดที่อยู่ในคลาสนั้น 
# Content
Ruby Number Classes คือ Ruby นั้นมีคลาสตัวเลขหลายคลาสและฟังก์ชั่นหลายอย่างที่มาพร้อมใช้งานในตัว ในส่วนนี้เราจะมาศึกษาคลาสตัวเลข (number classes) ที่ใช้บ่อยใน Ruby โดยที่ Ruby Number Classes หรือแบบที่เข้าใจง่ายๆ คือ คลาสตัวเลข ใน Ruby มันก็คือ กลุ่มของชนิดข้อมูลตัวเลขที่ Ruby ใช้จัดการค่าต่างๆ โดยจะมีดังนี้ 
1.1) Integer Class
1.2) Fixnum Class
1.3) Bignum Class
1.4) Float Class
1.5) Rational Class

# Integer Class
   ในภาษา Ruby คลาส Integer เป็นคลาสหลัก(The Base Class)ที่ใช้รองรับจะการทำงานเกี่ยวกับจำนวนเต็ม โดยเป็นคลาสแม่ของ 2 คลาสย่อยที่ใช้เก็บค่าจำนวนเต็ม ได้แก่

Fixnum คือ ใช้เก็บค่าจำนวนเต็มที่อยู่ในช่วงที่สามารถแสดงผลได้ด้วยขนาดของหน่วยคำ (machine word) ตามสถาปัตยกรรม(arcitecture)ของเครื่อง

Bignum คือ ใช้เก็บค่าจำนวนเต็มที่มีค่ามากเกินกว่าขอบเขตที่ Fixnum รองรับได้
คลาส Integer สืบทอดมาจากคลาส Numeric และมีการกำหนดเมธอด (methods) จำนวนมากเพื่อใช้ดำเนินการต่าง ๆ เกี่ยวกับตัวเลขจำนวนเต็ม
 ## list of methods that defined under integer class (รายชื่อเมธอดที่สำคัญในคลาส Interger):
### 1.) to_i
 คือ เมธอดนี้ใช้สำหรับแปลงค่าที่รับมาเป็นจำนวนเต็ม (integer) โดยมีเมธอด to_int เป็นอีกชื่อหนึ่งที่มีความหมายเหมือนกัน
 
#### โครงสร้าง (Syntax):
int.to_i

### 2.) chr
คือ เมธอดนี้ใช้สำหหรับแปลงค่าจำนวนเต็มให้เป็น ตัวอักษร ตามรหัส ASCII ของค่าที่กำหนด
#### โครงสร้าง (Syntax):
int.chr
#### ตัวอย่าง:
puts 65.chr

puts ?a.chr
#### ผลลัพธ์:
A

a
### 3. downto
คือ เมธอดนี้ใช้สำหรับ วนซ้ำค่าจากตัวเลข int ลงมาจนถึงค่าที่กำหนด (integer) โดยจะส่งค่าผ่านไปยัง iterator blockที่เขียนไว้

#### โครงสร้าง (Syntax):
int.downto(integer) { |i| block }
#### ตัวอย่าง:

6.downto(1) { |i| print i, "..." }

print "stop"
#### ผลลัพธ์:
6...5...4...3...2...1...stop

### 4. floor

คือ เมธอดนี้จะคืนค่าจำนวนเต็มที่ น้อยกว่าหรือเท่ากับ ค่าที่กำหนด โดยมีผลลัพธ์เหมือนกับการใช้ to_i

#### โครงสร้าง (Syntax):

int.floor
#### ตัวอย่าง:
puts 1.floor

puts (-1).floor
#### ผลลัพธ์:
1

-1

### 5. integer?
 คือ เมธอดนี้ใช้สำหรับ ตรวจสอบว่าค่าที่กำหนดเป็นจำนวนเต็มหรือไม่ โดยจะคืนค่า true หากเป็นจำนวนเต็ม และคืนค่า false หากไม่ใช่
#### โครงสร้าง (Syntax):
int.integer?

#### ตัวอย่าง:
puts 2.integer?

puts 0.1.integer?

#### ผลลัพธ์:
true

false

### 6. next / succ

คือ เมธอดนี้จะคืนค่าจำนวนเต็มถัดไปจากค่าปัจจุบัน (+1)
succ เป็นชื่ออีกแบบหนึ่งที่ทำงานเหมือนกับ next
#### โครงสร้าง (Syntax):
int.next

int.succ
#### ตัวอย่าง:
puts 5.next

puts -20.next

#### ผลลัพธ์:
6

-19

### 7. times
คือ เมธอดนี้ใช้สำหรับ วนซ้ำบล็อกโค้ดตามจำนวนครั้งที่กำหนด โดยเริ่มจากค่า 0 ไปจนถึง int - 1

##### โครงสร้าง (Syntax):

int.times { |i| block }

#### ตัวอย่าง:
6.times do |i|

  print i, " "
  
end
#### ผลลัพธ์:

0 1 2 3 4 5

### 8. upto
คือ เมธอดนี้ใช้สำหรับ วนซ้ำบล็อกโค้ดจากค่าที่กำหนด (int) ไปจนถึงค่าที่กำหนดในวงเล็บ (integer)

#### โครงสร้าง (Syntax):

int.upto(integer) { |i| block }

#### ตัวอย่าง:
20.upto(25) { |a| print a, "... " }

#### ผลลัพธ์:
20... 21... 22... 23... 24... 25...

### 9. round

คือ เมธอดนี้ใช้สำหรับ ปัดเศษ จำนวนไปยังค่าที่ใกล้ที่สุด

#### โครงสร้าง (Syntax):
int.round

#### ตัวอย่าง:
puts 2.round

puts (29.67).round

#### ผลลัพธ์:
2

30
### สรุป
คลาส Integer ใน Ruby มีเมธอดมากมายที่ช่วยให้การจัดการจำนวนเต็ม เช่น
การแปลงค่า (to_i)

การวนซ้ำ (times, upto, downto)

การปัดเศษ (round, floor)

การตรวจสอบชนิดข้อมูล (integer?)

การทำงานกับรหัส ASCII (chr)
 
 
 
# Fixnum Class
 A Fixnum เก็บค่าเลขจำนวนเต็มที่สามารถแทนค่าหรือแสดงค่าได้ ภายในคำสั่งเครื่อง (Machine word) ของระบบ (minus bit) โดยแท้จริงแล้งหรือในทางปฏิบัติ หมายถึง ว่าขอบเขต(range)สูงสุด ของ ค่า Fixnum ขึ้นอยู่กับ สถาปัตยกรรมของระบบที่ code กำลังทำงานอยู่(executing)

  ถ้ามีการดำเนินการใดๆ บน Fixnum แล้วผลลัพธ์เกินขอบเขต(range) ที่กำหนด โดยขนาดคำของคำสั่งของเครื่อง(machine word) ค่าดังกล่าวจะถูกแปลงโดยอัตโนมัติโดยตัว inperpreter ให้กลายเป็น Bignum  

### คุณสมบัติของ Fixnum

1.)เป็น Immediate Value → ค่าวัตถุ (object) จะถูกส่งโดยตรง ไม่ใช่การส่ง reference

2.)การกำหนดค่าตัวแปรใหม่ ไม่ได้สร้างสำเนาหรือ alias ของ object เดิม แต่เป็นการอ้างอิงค่าจริง

3.)สำหรับค่าจำนวนเต็มหนึ่งค่า จะมีเพียง Fixnum object เดียวที่แทนค่าในระบบ

4.)ไม่สามารถเพิ่ม singleton method ให้กับวัตถุของ Fixnum ได้

## list of methods that defined under Fixnum class (รายชื่อเมธอดที่สำคัญในคลาส Fixnum):

### 1. เมธอดการคำนวณทางคณิตศาสตร์ (Arithmetic Operations)

รองรับการคำนวณพื้นฐานเหมือนการทำงานกับจำนวนเต็มทั่วไป:

#### ตัวอย่าง
fix  +  aNumeric	บวก (Addition)

fix  -  aNumeric	ลบ (Subtraction)

fix  *  aNumeric	คูณ (Multiplication)

fix  /  aNumeric	หาร (Division)

fix  %  aNumeric	หารเอาเศษ (Modulo)

fix  **  aNumeric	ยกกำลัง (Exponentiation)

#### ตัวอย่าง:

puts 10 + 5      # 15

puts 10 - 5      # 5

puts 10 * 5      # 50

puts 10 / 5      # 2

puts 10 % 3      # 1

puts 2 ** 3      # 8

### 2. เมธอดการคำนวณบิต (Bit Operations)

ใช้สำหรับการจัดการตัวเลขในรูปแบบ เลขฐานสอง (Binary)

#### ตัวอย่างการใช้	
~ fix			       (Invert bits)

fix	|	aNumeric (Bitwise OR)

fix & aNumeric	AND บิต (Bitwise AND)

fix ^ aNumeric	XOR บิต (Bitwise EXCLUSIVE OR)

fix << aNumeric	เลื่อนบิตไปทางซ้าย (Left Shift)

fix >> aNumeric	เลื่อนบิตไปทางขวา (Right Shift)


#### ตัวอย่าง:

puts 5 | 3   # 7   => 0101 | 0011 = 0111

puts 5 & 3   # 1   => 0101 & 0011 = 0001

puts 5 ^ 3   # 6   => 0101 ^ 0011 = 0110

puts 5 << 1  # 10  => เลื่อนซ้าย 1 บิต

puts 5 >> 1  # 2   => เลื่อนขวา 1 บิต


### 3. การเปรียบเทียบ (<=>)

เมธอดนี้ใช้สำหรับเปรียบเทียบค่าระหว่างตัวเลขสองตัว และคืนค่าดังนี้:

-1 → ถ้า fix น้อยกว่า aNumeric

0 → ถ้า fix เท่ากับ aNumeric

1 → ถ้า fix มากกว่า aNumeric

#### ตัวอย่าง:

puts 5 <=> 10    # -1

puts 10 <=> 10   # 0

puts 15 <=> 10   # 1

### 4. การเข้าถึงบิตเดี่ยว ([])

สามารถเข้าถึงบิตในตำแหน่งที่ต้องการได้ โดยตำแหน่งเริ่มจาก 0 (บิตน้อยสุด)

#### ตัวอย่าง:

a = 0b11001100101010

30.downto(0) { |n| print a[n] }


#### ผลลัพธ์:

0000000000000000011001100101010

### 5. id2name

เมธอดนี้จะคืนชื่อสัญลักษณ์ (Symbol name) ที่มี ID เท่ากับค่าของ fix
ถ้าไม่มีสัญลักษณ์ที่ตรงกับ ID จะคืนค่า nil

#### ตัวอย่าง:

symbol = :@inst_var

id = symbol.to_i

puts id.id2name

#### ผลลัพธ์:

@inst_var

### 6. size

แสดงจำนวน ไบต์ ที่ใช้เก็บค่าของ Fixnum ในหน่วยความจำ

#### ตัวอย่าง:

puts 42.size


#### ผลลัพธ์ (ขึ้นกับสถาปัตยกรรมเครื่อง):

8

### 7. to_f

แปลงค่า Fixnum ให้เป็น Float

#### ตัวอย่าง:

puts 10.to_f    # 10.0

### 8. to_i

คืนค่าตัวเองในรูปแบบจำนวนเต็ม (Integer) — ไม่มีการเปลี่ยนแปลงค่า

#### ตัวอย่าง:

puts 42.to_i    # 42

### 9. to_s

แปลงค่าตัวเลขเป็น สตริง (String)

#### ตัวอย่าง:

puts 123.to_s    # "123"


# Bignum Class
  วัตถุ Bignum จะเก็บจำนวนเต็มที่อยู่นอกขอบเขตของคลาส Fixnum ของ Ruby เมื่อการคำนวณใดๆ ที่เกี่ยวข้องกับวัตถุ Bignum คืนค่า ผลลัพธ์ที่สามารถเก็บใน Fixnum ได้ ผลลัพธ์นั้นจะถูกแปลงเป็น Fixnum อัตโนมัติ 

#### ตัวอย่าง
----

# Float Class
----
#### ตัวอย่าง
---- 

# Rational Class
----
#### ตัวอย่าง 
------


## Referenes
[1] “Ruby Number Classes and Conversions,” *Techotopia*, Techotopia.com. [Online]. Available: https://www.techotopia.com/index.php/Ruby_Number_Classes_and_Conversions. [Accessed: 4-Sep-2025].

[2] “Ruby | Integer Class,” *GeeksforGeeks*, Last updated 11 Jul. 2025. [Online]. Available:
https://www.geeksforgeeks.org/ruby/ruby-integer-class/. [Accessed: 4-Sep-2025].

[3] *Programming Ruby – The Pragmatic Programmer’s Guide*, “class Fixnum < Integer,” Phrogz.net. [Online]. Available: https://phrogz.net/programmingruby/ref_c_fixnum.html. [Accessed: 4-Sep-2025].

