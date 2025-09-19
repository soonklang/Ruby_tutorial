# **Ruby Number Classes**
 Ruby Number Classes and conversions คือ แทบทุกอย่างภายใน Ruby มันคือวัตถุ บางทีสิ่งที่น่าประหลาดใจมากที่สุด นั่นก็คือ มันเป็นจำนวนคู่  หรือ ตัวเลขคู่ เป็น วัตถุ ใน Ruby และ ภาษาโปรแกรมอื่นๆ โดยส่วนใหญ่แล้วจะถือว่า ตัวเลข เป็น primitive (ชนิดข้อมูลพื้นฐาน) ไม่ใช่ วัตถุ หรือโดยที่พื้นฐานหรือสาระสำคัญเลยจะหมายถึง พวกมันเป็นส่วนประกอบพื้นฐาน (building blocks) จากสิ่งที่วัตถุ สร้างขึ้น และถัดมา แต่ละประเภทตัวเลข จะมีความหมายที่เกี่ยวข้อง คลาสของตัวเลข และ สามารถ ถูกจัดการหรือถูกนำไปใช้ โดยใช้ เมธอดที่อยู่ในคลาสนั้น 
# Content
Ruby Number Classes คือ Ruby นั้นมีคลาสตัวเลขหลายคลาสและฟังก์ชั่นหลายอย่างที่มาพร้อมใช้งานในตัว ในส่วนนี้เราจะมาศึกษาคลาสตัวเลข ที่ใช้บ่อยใน Ruby โดยที่ Ruby Number Classes หรือแบบที่เข้าใจง่ายๆ คือ คลาสตัวเลข ใน Ruby มันก็คือ กลุ่มของชนิดข้อมูลตัวเลขที่ Ruby ใช้จัดการค่าต่างๆ โดยจะมีดังนี้ 

 ```
1.1) Integer Class
1.2) Fixnum Class
1.3) Bignum Class
1.4) Float Class
1.5) Rational Class
 ```


# Integer Class
   ในภาษา Ruby คลาส Integer เป็นคลาสหลัก(The Base Class)ที่ใช้รองรับจะการทำงานเกี่ยวกับจำนวนเต็ม โดยเป็นคลาสแม่ของ 2 คลาสย่อยที่ใช้เก็บค่าจำนวนเต็ม ได้แก่
 ```
Fixnum คือ ใช้เก็บค่าจำนวนเต็มที่อยู่ในช่วงที่สามารถแสดงผลได้ด้วยขนาดของหน่วยคำ (machine word) ตามสถาปัตยกรรม(arcitecture)ของเครื่อง

Bignum คือ ใช้เก็บค่าจำนวนเต็มที่มีค่ามากเกินกว่าขอบเขตที่ Fixnum รองรับได้

 ```
คลาส Integer สืบทอดมาจากคลาส Numeric และมีการกำหนดเมธอด (methods) จำนวนมากเพื่อใช้ดำเนินการต่าง ๆ เกี่ยวกับตัวเลขจำนวนเต็ม

 ## list of methods that defined under integer class (รายชื่อเมธอดที่สำคัญในคลาส Interger):
### 1.) to_i
 คือ เมธอดนี้ใช้สำหรับแปลงค่าที่รับมาเป็นจำนวนเต็ม (integer) โดยมีเมธอด to_int เป็นอีกชื่อหนึ่งที่มีความหมายเหมือนกัน
 
#### โครงสร้าง (Syntax):
int.to_i

--- 
### 2.) chr
คือ เมธอดนี้ใช้สำหหรับแปลงค่าจำนวนเต็มให้เป็น ตัวอักษร ตามรหัส ASCII ของค่าที่กำหนด

#### โครงสร้าง (Syntax):
 ```
int.chr
 ```
#### ตัวอย่าง:
 ```
puts 65.chr

puts ?a.chr
 ```
#### ผลลัพธ์:
 ```
A

a
 ```

---
### 3. downto
คือ เมธอดนี้ใช้สำหรับ วนซ้ำค่าจากตัวเลข int ลงมาจนถึงค่าที่กำหนด (integer) โดยจะส่งค่าผ่านไปยัง iterator blockที่เขียนไว้

#### โครงสร้าง (Syntax):
 ```
int.downto(integer) { |i| block }
 ```
#### ตัวอย่าง:
 ```
6.downto(1) { |i| print i, "..." }

print "stop"

 ```
#### ผลลัพธ์:
 ```
6...5...4...3...2...1...stop
 ```

---
### 4. floor

คือ เมธอดนี้จะคืนค่าจำนวนเต็มที่ น้อยกว่าหรือเท่ากับ ค่าที่กำหนด โดยมีผลลัพธ์เหมือนกับการใช้ to_i

#### โครงสร้าง (Syntax):
 ```

int.floor
 ```
#### ตัวอย่าง:
 ```
puts 1.floor

puts (-1).floor
 ```
#### ผลลัพธ์:

 ```
1

-1
 ```

---

### 5. integer?
 คือ เมธอดนี้ใช้สำหรับ ตรวจสอบว่าค่าที่กำหนดเป็นจำนวนเต็มหรือไม่ โดยจะคืนค่า true หากเป็นจำนวนเต็ม และคืนค่า false หากไม่ใช่
 
#### โครงสร้าง (Syntax):
 ```
int.integer?
 ```
#### ตัวอย่าง:
 ```
puts 2.integer?

puts 0.1.integer?

 ```

#### ผลลัพธ์:
 ```
true

false
 ```

---

### 6. next / succ

คือ เมธอดนี้จะคืนค่าจำนวนเต็มถัดไปจากค่าปัจจุบัน (+1)
succ เป็นชื่ออีกแบบหนึ่งที่ทำงานเหมือนกับ next

#### โครงสร้าง (Syntax):
 ```
int.next

int.succ

 ```

#### ตัวอย่าง:
 ```
puts 5.next

puts -20.next
 ```

#### ผลลัพธ์:
 ``` 
6

-19
 ```

---

### 7. times
คือ เมธอดนี้ใช้สำหรับ วนซ้ำบล็อกโค้ดตามจำนวนครั้งที่กำหนด โดยเริ่มจากค่า 0 ไปจนถึง int - 1

##### โครงสร้าง (Syntax):

 ```
int.times { |i| block }

 ```
#### ตัวอย่าง:

 ```
6.times do |i|

  print i, " "
  
end

 ```

#### ผลลัพธ์:
 ```

0 1 2 3 4 5

 ```

---
### 8. upto
คือ เมธอดนี้ใช้สำหรับ วนซ้ำบล็อกโค้ดจากค่าที่กำหนด (int) ไปจนถึงค่าที่กำหนดในวงเล็บ (integer)

#### โครงสร้าง (Syntax):
 ```
int.upto(integer) { |i| block }
 ```
#### ตัวอย่าง:
 ```
20.upto(25) { |a| print a, "... " }

 ```

#### ผลลัพธ์:

 ```
20... 21... 22... 23... 24... 25...

 ```

---
### 9. round

คือ เมธอดนี้ใช้สำหรับ ปัดเศษ จำนวนไปยังค่าที่ใกล้ที่สุด

#### โครงสร้าง (Syntax):

 ```
int.round

 ```
#### ตัวอย่าง:
 ```
puts 2.round

puts (29.67).round
 ```

#### ผลลัพธ์:

 ```
2

30

```
### สรุป
คลาส Integer ใน Ruby มีเมธอดมากมายที่ช่วยให้การจัดการจำนวนเต็ม เช่น
การแปลงค่า (to_i)

การวนซ้ำ (times, upto, downto)

การปัดเศษ (round, floor)

การตรวจสอบชนิดข้อมูล (integer?)

การทำงานกับรหัส ASCII (chr)
 
 
 ---
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
 ``` 
fix  +  aNumeric	บวก (Addition)

fix  -  aNumeric	ลบ (Subtraction)

fix  *  aNumeric	คูณ (Multiplication)

fix  /  aNumeric	หาร (Division)

fix  %  aNumeric	หารเอาเศษ (Modulo)

fix  **  aNumeric	ยกกำลัง (Exponentiation)
 ```
#### ตัวอย่าง:
 ```

puts 10 + 5      # 15

puts 10 - 5      # 5

puts 10 * 5      # 50

puts 10 / 5      # 2

puts 10 % 3      # 1

puts 2 ** 3      # 8
 ```

---
### 2. เมธอดการคำนวณบิต (Bit Operations)

ใช้สำหรับการจัดการตัวเลขในรูปแบบ เลขฐานสอง (Binary)

#### ตัวอย่างการใช้	
 ```
~ fix			       (Invert bits)

fix	|	aNumeric (Bitwise OR)

fix & aNumeric	AND บิต (Bitwise AND)

fix ^ aNumeric	XOR บิต (Bitwise EXCLUSIVE OR)

fix << aNumeric	เลื่อนบิตไปทางซ้าย (Left Shift)

fix >> aNumeric	เลื่อนบิตไปทางขวา (Right Shift)

 ```
#### ตัวอย่าง:
 ```
puts 5 | 3   # 7   => 0101 | 0011 = 0111

puts 5 & 3   # 1   => 0101 & 0011 = 0001

puts 5 ^ 3   # 6   => 0101 ^ 0011 = 0110

puts 5 << 1  # 10  => เลื่อนซ้าย 1 บิต

puts 5 >> 1  # 2   => เลื่อนขวา 1 บิต

 ```

---
### 3. การเปรียบเทียบ (<=>)

เมธอดนี้ใช้สำหรับเปรียบเทียบค่าระหว่างตัวเลขสองตัว และคืนค่าดังนี้:
 ```

-1 → ถ้า fix น้อยกว่า aNumeric

0 → ถ้า fix เท่ากับ aNumeric

1 → ถ้า fix มากกว่า aNumeric
 ```

#### ตัวอย่าง:
 ```

puts 5 <=> 10    # -1

puts 10 <=> 10   # 0

puts 15 <=> 10   # 1
 ```
---
### 4. การเข้าถึงบิตเดี่ยว ([])

สามารถเข้าถึงบิตในตำแหน่งที่ต้องการได้ โดยตำแหน่งเริ่มจาก 0 (บิตน้อยสุด)

#### ตัวอย่าง:
 ```

a = 0b11001100101010

30.downto(0) { |n| print a[n] }

 ```
#### ผลลัพธ์:
 ```
0000000000000000011001100101010
 ```

---
### 5. id2name

เมธอดนี้จะคืนชื่อสัญลักษณ์ (Symbol name) ที่มี ID เท่ากับค่าของ fix
ถ้าไม่มีสัญลักษณ์ที่ตรงกับ ID จะคืนค่า nil

#### ตัวอย่าง:
 ```

symbol = :@inst_var

id = symbol.to_i

puts id.id2name

 ```
#### ผลลัพธ์:

 ```
@inst_var
 ```
---
### 6. size

แสดงจำนวน ไบต์ ที่ใช้เก็บค่าของ Fixnum ในหน่วยความจำ

#### ตัวอย่าง:
 ```

puts 42.size
 ```

#### ผลลัพธ์ (ขึ้นกับสถาปัตยกรรมเครื่อง):
 ```
8
 ```
---

### 7. to_f

แปลงค่า Fixnum ให้เป็น Float

#### ตัวอย่าง:
 ```

puts 10.to_f    # 10.0
 ```

### 8. to_i

คืนค่าตัวเองในรูปแบบจำนวนเต็ม (Integer) — ไม่มีการเปลี่ยนแปลงค่า

#### ตัวอย่าง:

 ```

puts 42.to_i    # 42

 ```

---
### 9. to_s

แปลงค่าตัวเลขเป็น สตริง (String)

#### ตัวอย่าง:
 ```

puts 123.to_s    # "123"

 ```
# Bignum Class
   วัตถุ Bignum จะเก็บจำนวนเต็มที่อยู่นอกขอบเขตของคลาส Fixnum ของ Ruby เมื่อการคำนวณใดๆ ที่เกี่ยวข้องกับวัตถุ Bignum คืนค่า ผลลัพธ์ที่สามารถเก็บใน Fixnum ได้ ผลลัพธ์นั้นจะถูกแปลงเป็น Fixnum อัตโนมัติ 
 หรือ ในภาษา Ruby คลาส Bignum ถูกใช้สำหรับเก็บค่าจำนวนเต็มที่มีค่ามากเกินกว่าที่คลาส Fixnum รองรับได้โดยอัตโนมัติ เช่น ถ้าเราคำนวณตัวเลขแล้วผลลัพธ์มีค่ามากจนเกินช่วงของ Fixnum ระบบจะเปลี่ยนไปใช้ Bignum ให้ทันที และถ้าผลลัพธ์กลับมาอยู่ในช่วงที่ Fixnum จัดเก็บได้ ก็จะเปลี่ยนกลับเป็น Fixnum อีกครั้งโดยไม่ต้องเขียนโค้ดเพิ่มเอง

   ข้อแตกต่างระหว่าง Fixnum และ Bignum คือ Fixnum จะจัดเก็บค่าเป็น immediate value หมายความว่าเมื่อเราส่งตัวเลขไปยังฟังก์ชันหรือกำหนดค่าให้ตัวแปร จะเป็นการส่งค่าตัวเลขจริง ๆ ไปเลย ในขณะที่ Bignum จะทำงานผ่าน การอ้างอิงออบเจกต์ (object reference) ซึ่งอาจใช้หน่วยความจำมากกว่าเล็กน้อยเมื่อเทียบกับ Fixnum

## คุณสมบัติสำคัญของ Bignum
 ```

1.)ใช้สำหรับจัดเก็บจำนวนเต็มขนาดใหญ่เกินกว่าที่ Fixnum รองรับ

2.)สร้างขึ้นโดยอัตโนมัติเมื่อผลลัพธ์การคำนวณเกินขอบเขตของ Fixnum

3.)สามารถทำงานร่วมกับ bitwise operations เช่น AND, OR, XOR, NOT ได้

4.)รองรับการเลื่อนบิต (bit shifting) ทั้งซ้ายและขวา

5.)สามารถเข้าถึงค่าบิตในตำแหน่งที่ต้องการได้โดยใช้ตัวดำเนินการ [ ]

6.)รองรับการแปลงข้อมูลเป็น Float, String และแปลงเป็นเลขฐานต่าง ๆ ได้

7.)เมื่อเรียกใช้ไลบรารี mathn จะให้ผลลัพธ์การคำนวณที่แม่นยำมากขึ้น โดยเฉพาะการหารและการยกกำลัง

 ```
##  Public Instance Methods

## 1. เมธอดการคำนวณพื้นฐาน

**big + other → Numeric**

### คำอธิบาย:
บวกค่าระหว่างตัวแปร Bignum กับค่าที่กำหนด

### ตัวอย่าง:
 ```

10_000_000_000 + 5 #=> 10000000005
 ```
---

**big - other → Numeric**

### คำอธิบาย:
ลบค่าของตัวแปร Bignum ด้วยค่าที่กำหนด

### ตัวอย่าง:
 ```

1_000_000_000 - 500 #=> 999999500
 ```

---
**big * other → Numeric**

### คำอธิบาย:
คูณค่าของตัวแปร Bignum กับค่าที่กำหนด

### ตัวอย่าง:
 ```
999_999_999 * 2 #=> 1999999998
 ```

---

**big / other → Numeric**

### คำอธิบาย:
หารค่าของ Bignum ด้วยตัวเลขที่กำหนด
ประเภทผลลัพธ์ขึ้นอยู่กับชนิดข้อมูลของตัวหาร

### ตัวอย่าง:

 ```

20_000 / 3 #=> 6666

 ```

---

**big % other → Numeric**

### คำอธิบาย:
หาผลลัพธ์ เศษ จากการหาร

### ตัวอย่าง:
 ```
15 % 4 #=> 3
 ```

---

**big ** exponent → Numeric**

### คำอธิบาย:
ยกกำลังค่าของตัวแปร Bignum ตามเลขชี้กำลังที่กำหนด

### ตัวอย่าง:

 ```

123456789 ** 2 #=> 15241578750190521
 ```
---
## 2. เมธอดการเปรียบเทียบ

**big < real → Boolean**

### คำอธิบาย:
คืนค่า true ถ้าค่าของ big น้อยกว่า real

### ตัวอย่าง:
 ```
10 < 20 #=> true
 ```

---

**big <= real → Boolean**

### คำอธิบาย:
ตรวจสอบว่าค่าน้อยกว่าหรือเท่ากับ

### ตัวอย่าง:
 ```

5 <= 5 #=> true
 ```

---
**big > real → Boolean**

### คำอธิบาย:
คืนค่า true ถ้าค่าของ big มากกว่า real

### ตัวอย่าง:
 ```
20 > 10 #=> true
 ```

---
**big >= real → Boolean**

### คำอธิบาย:
ตรวจสอบว่าค่ามากกว่าหรือเท่ากับ

### ตัวอย่าง:
 ```

100 >= 50 #=> true

 ```

---

**big == obj → Boolean**

### คำอธิบาย:
ตรวจสอบว่าค่าของ big เท่ากับ obj หรือไม่
(มีการแปลงชนิดข้อมูลก่อนเปรียบเทียบ)

### ตัวอย่าง:

 ```

68719476736 == 68719476736.0 #=> true

 ```

---
**big.eql?(obj) → Boolean**

### คำอธิบาย:
ตรวจสอบความเท่ากัน โดยไม่แปลงชนิดข้อมูล

### ตัวอย่าง:
 ```
68719476736.eql?(68719476736.0) #=> false
 ```

---
**big <=> numeric → Integer / nil**

### คำอธิบาย:
เปรียบเทียบค่าระหว่าง big และ numeric
 ``` 
คืน -1 ถ้า big < numeric

คืน 0 ถ้าเท่ากัน

คืน 1 ถ้า big > numeric

คืน nil ถ้าเปรียบเทียบไม่ได้
 ```
### ตัวอย่าง:
 ```

10 <=> 5 #=> 1

 ```

---

## 3. การทำงานเกี่ยวกับบิต (Bitwise Operations)


**big & numeric → Numeric**

### คำอธิบาย:
ทำ AND ของตัวเลขสองตัวในรูปแบบบิต

### ตัวอย่าง:
 ```
12 & 7 #=> 4

 ```
---

**big | numeric → Numeric**

### คำอธิบาย:
ทำ OR ของตัวเลขสองตัวในรูปแบบบิต

### ตัวอย่าง:
 ```
12 | 7 #=> 15
 ```
---


**big ^ numeric → Numeric**

### คำอธิบาย:
ทำ XOR ของตัวเลขสองตัวในรูปแบบบิต

### ตัวอย่าง:
 ```
12 ^ 7 #=> 11
 ```

---
**big << n → Numeric**

### คำอธิบาย:
เลื่อนบิตไปทางซ้าย n ตำแหน่ง

### ตัวอย่าง:

 ```
5 << 2 #=> 20
 ```

---
**big >> n → Numeric**

### คำอธิบาย:
เลื่อนบิตไปทางขวา n ตำแหน่ง

### ตัวอย่าง:

 ```
20 >> 2 #=> 5
 ```

---

**~big → Numeric**

### คำอธิบาย:
กลับค่าบิตทั้งหมด
(บิตที่เป็น 1 จะกลายเป็น 0 และกลับกัน)

### ตัวอย่าง:
 ```

~5 #=> -6

 ```

---

## 4. การหารแบบพิเศษ

**div(other) → Integer**

### คำอธิบาย:
หารแล้วปัดเศษ ลง ให้ผลลัพธ์เป็นจำนวนเต็ม

### ตัวอย่าง:

 ```

10.div(3) #=> 3
 ```

---
**divmod(numeric) → [Integer, Integer]**

### คำอธิบาย:
คืนค่าผลหารและเศษในรูปแบบ Array

### ตัวอย่าง:
 ```

10.divmod(3) #=> [3, 1]

 ```

---

**fdiv(numeric) → Float**

### คำอธิบาย:
หารแบบให้ผลลัพธ์เป็น ทศนิยม

### ตัวอย่าง:
 ```
10.fdiv(3) #=> 3.3333333333
 ```

---

**remainder(numeric) → Numeric**

### คำอธิบาย:
คืนค่าเศษจากการหาร โดย เครื่องหมายตามตัวตั้ง

### ตัวอย่าง:
 ```

-123.remainder(10) #=> -3
 ```

## 5. เมธอดการตรวจสอบและแปลงค่า

**even? → Boolean**

### คำอธิบาย:
ตรวจสอบว่าค่าเป็นเลขคู่หรือไม่

### ตัวอย่าง:
 ```

100.even? #=> true
 ```

---

**odd? → Boolean**

### คำอธิบาย:
ตรวจสอบว่าค่าเป็นเลขคี่หรือไม่

### ตัวอย่าง:
 ```

101.odd? #=> true
 ```

---
**abs → Numeric**

### คำอธิบาย:
คืนค่าค่าสัมบูรณ์ของตัวเลข

### ตัวอย่าง:
 ```

-123.abs #=> 123
 ```

---
**size → Integer**

### คำอธิบาย:
คืนค่าจำนวน ไบต์ ที่ใช้ในการเก็บตัวเลข

### ตัวอย่าง:
 ```

(256**10 - 1).size #=> 12
 ```
---
**to_f → Float**

### คำอธิบาย:
แปลงค่าตัวเลขเป็น ทศนิยม

### ตัวอย่าง:
 ```

(1234567890).to_f #=> 1.23456789e9
 ```

---
**to_s(base = 10) → String**

### คำอธิบาย:
แปลงเป็นสตริงตามฐานที่กำหนด (ระหว่าง 2 ถึง 36)

### ตัวอย่าง:
 ```

12345654321.to_s(16) #=> "2dfdbbc31"
 ```
---
**inspect → String**

### คำอธิบาย:
คืนค่ารูปแบบสตริงของตัวเลข (เหมือน to_s)

###ตัวอย่าง:
 ```
100.inspect #=> "100"
 ```

---
## 6. ตัวอย่างการใช้งานจริง
 ```
a = 9**15
50.downto(0) do |n|
  print a[n]
end
 
# Output:
# 000101110110100000111000011110010100111100010111001
 ```


----

# Float Class

 ในภาษา Ruby ชนิดข้อมูล Float ใช้สำหรับแทนตัวเลขทศนิยม หรือจำนวนจริง (real number) ที่ไม่สามารถเก็บได้แบบแม่นยำ 100% เนื่องจาก Ruby ใช้การแทนค่าด้วย double-precision floating point ตามสถาปัตยกรรมของเครื่องคอมพิวเตอร์ ซึ่งเป็นมาตรฐานที่พบได้ทั่วไป

เนื่องจากการเก็บข้อมูลแบบทศนิยมของคอมพิวเตอร์เป็นแบบประมาณค่า (inexact number) ดังนั้นเวลาเราทำการคำนวณด้วย Float อาจเจอปัญหาเกี่ยวกับความแม่นยำเล็กน้อย ตัวอย่างเช่น ค่าที่ควรจะได้เป็น 10.0 อาจถูกเก็บเป็น 9.9999999999 แทน

## ค่าคงที่ (Constants) ที่เกี่ยวข้องกับ Float ## 

### Ruby มีค่าคงที่ที่ใช้กับ Float หลายตัวที่ควรรู้จัก เช่น: ###

**1. DIG** 

จำนวนหลักทศนิยมที่มีความแม่นยำสูงสุด ที่สามารถเก็บได้ในตัวแปรชนิด Float

**ค่าปกติ: 15**
 ```
Float::DIG  #=> 15
 ```
---
**2. EPSILON**

ค่าความแตกต่างที่เล็กที่สุด ระหว่างเลข 1.0 กับค่าที่ใหญ่กว่า 1.0 นิดเดียว
ใช้ตรวจสอบความแม่นยำของการคำนวณทศนิยม

**ค่าปกติ: 2.2204460492503131e-16**
 ```
Float::EPSILON  #=> 2.220446049250313e-16
 ```
**3. INFINITY**

นิพจน์ที่แทนค่าบวกอนันต์ (+∞) มักเกิดจากการหารด้วยศูนย์
 ```
Float::INFINITY    #=> Infinity
1.0 / 0.0          #=> Infinity
 ```
---
**4. MANT_DIG**

จำนวนบิตในส่วนแมนทิสซา (Mantissa) ของตัวเลขทศนิยมแบบ Double-Precision
เป็นตัวกำหนดความละเอียดสูงสุดที่ตัวเลขเก็บได้

**ค่าปกติ: 53**

 ```
Float::MANT_DIG  #=> 53
 ```

---
**5. MAX**

ค่ามากที่สุดที่เก็บได้ ในชนิดข้อมูล Float ก่อนที่จะเกิด Overflow

**ค่าปกติ: 1.7976931348623157e+308**

 ```
Float::MAX  #=> 1.7976931348623157e+308
 ```
---

 **6. MAX_10_EXP**

เลขชี้กำลังฐาน 10 ที่มากที่สุด ที่สามารถใช้ได้ใน Float
หมายความว่าค่าของ 10 ** Float::MAX_10_EXP จะยังอยู่ในขอบเขตของ Float

**ค่าปกติ: 308**
 ```

Float::MAX_10_EXP  #=> 308
 ```
---
**7. MAX_EXP**

เลขชี้กำลังฐาน 2 ที่มากที่สุด ใน Float

**ค่าปกติ: 1024**

 ```
Float::MAX_EXP  #=> 1024
 ```
---

**8. MIN**

ค่าบวกที่เล็กที่สุดแบบปกติ ที่สามารถเก็บได้ใน Float

**ค่าปกติ: 2.2250738585072014e-308**
 ```

Float::MIN  #=> 2.2250738585072014e-308

 ```

---
### OR ###
 ```

0.0.next_float  #=> 5.0e-324
 ```
---

**9. MIN_10_EXP**

เลขชี้กำลังฐาน 10 ที่ติดลบมากที่สุด ที่ยังสามารถแทนค่าได้

**ค่าปกติ: -307**
 ```
Float::MIN_10_EXP  #=> -307
 ```
---
**10. MIN_EXP**

เลขชี้กำลังฐาน 2 ที่ติดลบมากที่สุด

**ค่าปกติ: -1021**
 ```
Float::MIN_EXP  #=> -1021
 ```
**11. NAN**

นิพจน์ที่แทนค่าที่ไม่ใช่ตัวเลข หรือ Not a Number
มักเกิดจากการคำนวณที่ไม่สามารถกำหนดค่าได้ เช่น 0.0 / 0.0
 ```
Float::NAN     #=> NaN
0.0 / 0.0      #=> NaN
 ```
---
**12. RADIX**

ฐานของการแทนค่าตัวเลขทศนิยม ซึ่งในระบบส่วนใหญ่จะเป็น ฐาน 2
หมายถึงการเก็บข้อมูลในระดับบิต

**ค่าปกติ: 2**

---

## Public Instance Methods ##

**1. float % other → float**

คืนค่าผล modulo หลังจากการหาร float ด้วย other
```
6543.21.modulo(137)      #=> 104.21000000000004
6543.21.modulo(137.24)   #=> 92.92999999999961
```

---
**2. float * other → float**

คืนค่า Float ใหม่ซึ่งเป็นผลคูณของ float และ other**

---

**3. float ** other → float**

ยกกำลัง float ด้วยค่า other

```
2.0**3   #=> 8.0
```
---

**4. float + other → float**

คืนค่า Float ใหม่ซึ่งเป็นผลบวกของ float และ other

---

**5. float - other → float**

คืนค่า Float ใหม่ซึ่งเป็นผลลบของ float และ other

---

**6. -float → float**

คืนค่า float ที่มีเครื่องหมายตรงข้าม (ค่าติดลบหรือบวก)

---

**7. float / other → float**

คืนค่า Float ใหม่ที่เป็นผลลัพธ์ของการหาร float ด้วย other

---

**8. float < real → true or false**

คืนค่า true ถ้า float น้อยกว่า real

*หมายเหตุ: หากค่าทั้งสองเป็น NaN ผลลัพธ์จะไม่สามารถคาดเดาได้*

---

**9. float <= real → true or false**

คืนค่า true ถ้า float น้อยกว่าหรือเท่ากับ real

---

**10. float <=> real → -1, 0, +1, or nil**

```
เปรียบเทียบค่า float กับ real


คืนค่า -1 ถ้า float น้อยกว่า real


คืนค่า 0 ถ้าเท่ากัน


คืนค่า +1 ถ้า float มากกว่า real


คืนค่า nil ถ้าเปรียบเทียบไม่ได้

```

---

**11. float == obj → true or false**

คืนค่า true ก็ต่อเมื่อ obj มีค่าเท่ากับ float

```

1.0 == 1   #=> true

```

*หมายเหตุ: การเปรียบเทียบ NaN == NaN ไม่สามารถกำหนดผลลัพธ์ได้*

---

**12. abs → float**

คืนค่าตัวเลขบวกของ float

```
(-34.56).abs   #=> 34.56
34.56.abs      #=> 34.56
```


**Alias: magnitude**

---

**13. ceil([ndigits]) → integer or float**

คืนค่าจำนวนเต็มที่ มากที่สุด แต่ ไม่เกิน ค่าของ float
รองรับการปัดทศนิยมตามจำนวน ndigits ที่กำหนด

```
1.2.ceil      #=> 2
(-1.2).ceil   #=> -1
1.234567.ceil(3)   #=> 1.235
```

---
**14. floor([ndigits]) → integer or float**

คืนค่าจำนวนเต็มที่ น้อยที่สุด แต่ ไม่เกิน ค่าของ float
```
1.2.floor      #=> 1
(-1.2).floor   #=> -2
1.234567.floor(2)   #=> 1.23
```
---
**15. round([ndigits]) → integer or float**

ปัดค่าของ float ให้ใกล้ค่าที่สุดตามหลักทศนิยมที่กำหนด
```
1.5.round      #=> 2
1.234567.round(2)   #=> 1.23
```

---
**16. truncate([ndigits]) → integer or float**

ตัดค่าทศนิยมออกตามจำนวนหลักที่ระบุ (ปัดเข้าหาศูนย์)
```
2.8.truncate   #=> 2
34567.89.truncate(-2)  #=> 34500
```

---

**17. nan? → true or false**

คืนค่า true หาก float เป็นตัวเลขที่ไม่ถูกต้องตามมาตรฐาน IEEE

```
a = 0.0/0.0   #=> NaN
a.nan?        #=> true
```

---
**18. infinite? → -1, 1, or nil**

ตรวจสอบว่าค่าเป็นอนันต์ไหม
```

คืนค่า 1 ถ้าเป็น +Infinity

คืนค่า -1 ถ้าเป็น -Infinity

คืนค่า nil ถ้าไม่ใช่อนันต์

```

---

**19. positive? → true or false**

คืนค่า true ถ้า float มากกว่า 0

---

**20. negative? → true or false**

คืนค่า true ถ้า float น้อยกว่า 0

---

**21. zero? → true or false**

คืนค่า true ถ้า float เท่ากับ 0.0

---

**22. next_float และ prev_float**
```

next_float → คืนค่าจำนวนทศนิยมตัวถัดไปที่สามารถแทนได้

prev_float → คืนค่าจำนวนทศนิยมตัวก่อนหน้าที่สามารถแทนได้
```
---
---- 

# Rational Class

คลาส Rational ใน Ruby ใน Ruby มีคลาสชื่อ Rational ซึ่งใช้เก็บตัวเลขแบบ เศษส่วน หรือ Rational number

ตัวเลขแบบ Rational คือ ตัวเลขที่สามารถเขียนเป็นเศษส่วน p/q ได้ โดยที่:
```
p คือ ตัวเศษ (numerator)

q คือ ตัวส่วน (denominator)

q ไม่เท่ากับ 0
```
ตัวเลขแบบนี้จะเก็บค่าได้ชัดเจนและแม่นยำ เพราะเป็นการเก็บเป็นเศษส่วนตรง ๆ

ตัวเลขที่ ไม่สามารถเขียนเป็นเศษส่วนได้ เช่น √2 หรือ π จะเรียกว่า ตัวเลขไม่เป็น rational หรือ Irrational number

## Syntax ##
```
Rational(num, den)
```

*num* คือ ตัวเศษ

*den* คือ ตัวส่วน ค่าเริ่มต้นคือ 1 ถ้าไม่ระบุ


**ฟังก์ชันนี้จะคืนค่าเป็น Rational object ซึ่งเก็บค่าตัวเลขเศษส่วนได้อย่างแม่นยำกว่า Float**

### ตัวอย่างการใช้งาน ###

**ตัวอย่างที่ 1: ระบุเฉพาะตัวเศษ**
```
rat = Rational(4)
puts rat
```

**ผลลัพธ์:**
```
4/1
```

เพราะไม่ได้ระบุส่วน ค่าเริ่มต้นคือ 1

---

**ตัวอย่างที่ 2: ระบุทั้งตัวเศษและตัวส่วน**
```
rat = Rational(4, 5)
puts rat
```

**ผลลัพธ์:**
```
4/5
```

เราจะได้ Rational object แทนค่า 4/5

---

#### ข้อดีของการใช้ Rational() ###


1.)แม่นยำกว่า Float


เพราะเก็บเป็นเศษส่วนตรง ๆ ไม่ใช่ทศนิยม ทำให้ไม่เจอปัญหา precision


2.)ใช้ง่าย


แค่ระบุเศษหรือเศษกับส่วนก็สร้าง Rational object ได้


3.)เหมาะกับการคำนวณเชิงคณิตศาสตร์


สามารถบวก ลบ คูณ หาร กับ Rational object ได้ตรงตามหลักคณิตศาสตร์


สามารถแปลงเป็นทศนิยมได้เมื่อจำเป็น

```
rat = Rational(4,5)
puts rat.to_f   #=> 0.8
```
---
## สรุป Ruby Number Classes ##

**Fixnum**  
```

จำนวนเต็มที่พอดีกับขนาดของเครื่อง 

หมายเหตุ : ถ้าเลขเกินขนาด Fixnum ระบบจะเปลี่ยนเป็น Bignum อัตโนมัติ 

```
**Bignum**  
```
จำนวนเต็มที่เกินขนาดของ Fixnum   

หมายเหตุ : ถ้าผลลัพธ์เล็กลงจนพอดี ระบบจะเปลี่ยนกลับเป็น Fixnum
```

**Integer** 
```

จำนวนเต็มทั้งหมด          

หมายเหตู : เป็น superclass ของ Fixnum และ Bignum (รวมเลขเต็มเล็กและใหญ่)
```

**Float**   
```
ตัวเลขทศนิยม                     

หมายเหตู : เก็บแบบ double-precision ตามสถาปัตยกรรมของเครื่อง อาจมีความไม่แม่นยำเล็กน้อย 
```
---

# เปรียบเทียบ Ruby Number Classes กับทั้ง 4 ภาษา #
**ได้แก่ ภาษา Ruby , C ,Java, Python**

*Ruby Number Classes มีดังนี้*
```
1.1) Integer Class
1.2) Fixnum Class
1.3) Bignum Class
1.4) Float Class
1.5) Rational Class
```
## Ruby ##
ภาษา Ruby
```
# Integer
int_num = 42
puts "Integer: #{int_num}"  # => 42

# Float
float_num = 3.14
puts "Float: #{float_num}"  # => 3.14

# Rational
rat_num = Rational(4, 5)
puts "Rational: #{rat_num}"  # => 4/5

```
*อธิบาย*

Integer แทนจำนวนเต็ม

Float แทนตัวเลขทศนิยมแบบ double-precision

Rational แทนตัวเลขในรูปเศษส่วน [Ruby Docs, 2025]

---

## C ##

ภาษา C
```
#include <stdio.h>

int main() {
    int i = 42;
    float f = 3.14;

    printf("int: %d\n", i);     // => 42
    printf("float: %.2f\n", f); // => 3.14
    return 0;
}
```

*อธิบาย*

int แทนจำนวนเต็ม

float แทนตัวเลขทศนิยมแบบ single-precision

C ไม่มีชนิดข้อมูลเศษส่วนโดยตรง [GeeksforGeeks, 2025]

---
## Java ##

ภาษา Java
```
import java.math.BigInteger;
import java.math.BigDecimal;

public class NumberDemo {
    public static void main(String[] args) {
        int i = 42;
        double d = 3.14;
        BigInteger bigInt = new BigInteger("1234567890123456789");
        BigDecimal bigDec = new BigDecimal("3.1415926535");

        System.out.println("int: " + i);          // => 42
        System.out.println("double: " + d);       // => 3.14
        System.out.println("BigInteger: " + bigInt); // => 1234567890123456789
        System.out.println("BigDecimal: " + bigDec); // => 3.1415926535
    }
}
```

*อธิบาย*

int และ double แทนตัวเลขทั่วไป

BigInteger และ BigDecimal สำหรับตัวเลขขนาดใหญ่หรือทศนิยมแม่นยำสูง

Java ไม่มีคลาสสำหรับเศษส่วนโดยตรง [Oracle Docs, 2025]

---
## Python ##

ภาษา Python

```
from fractions import Fraction

# Integer
i = 42
print("Integer:", i)  # => 42

# Float
f = 3.14
print("Float:", f)    # => 3.14

# Fraction
frac = Fraction(4, 5)
print("Fraction:", frac)  # => 4/5
```

*อธิบาย*

int และ float เหมือนกับ Ruby

Fraction แทนเศษส่วน [Python Docs, 2025]

---

# คลิปนำเสนอ
## https://youtu.be/yvU3zuXZqlc?si=ri2DjvUEa0DHhFJI
# Presentations
## https://drive.google.com/drive/folders/1kRDSQxWGpZfXGEgTTT0Lx1BLtrNOp98q

## Referenes
### content ##
[1] “Ruby Number Classes and Conversions,” *Techotopia*, Techotopia.com. [Online]. Available: https://www.techotopia.com/index.php/Ruby_Number_Classes_and_Conversions. [Accessed: 1-Sep-2025].

## content and Example ##

[2] “Ruby | Integer Class,” *GeeksforGeeks*, Last updated 11 Jul. 2025. [Online]. Available:
https://www.geeksforgeeks.org/ruby/ruby-integer-class/. [Accessed: 1-Sep-2025].

[3] *Programming Ruby – The Pragmatic Programmer’s Guide*, “class Fixnum < Integer,” Phrogz.net. [Online]. Available: https://phrogz.net/programmingruby/ref_c_fixnum.html. [Accessed: 2-Sep-2025].

[4] Matz, "Class: Bignum," *Ruby 2.0.0 Documentation*, 2013. [Online]. Available: https://docs.ruby-lang.org/en/2.0.0/Bignum.html. [Accessed: 2-Sep-2025].

[5] “Ruby | Float Class,” *Ruby 3.0.3 Documentation*, 2025. [Online]. Available: https://ruby-doc.org/core-3.0.3/Float.html. [Accessed: 4-Sep-2025].

[6] G. Dave, "Ruby | Rational rational() function," GeeksforGeeks, 12 Jul. 2025. [Online]. Available: https://www.geeksforgeeks.org/ruby/ruby-rational-rational-function/
. [Accessed: 4-Sep-2025].

## Ruby vs C vs Java vs Python: Number Class Comparison ##

## Ruby ##
[7] “Float Class,” Ruby 3.0.3 Documentation, 2025. [Online]. Available: https://ruby-doc.org/core-3.0.3/Float.html. [Accessed: 5-Sep-2025].

[8] “Integer Class,” Ruby 3.0.3 Documentation, 2025. [Online]. Available: https://ruby-doc.org/core-3.0.3/Integer.html. [Accessed: 5-Sep-2025].

[9] “Fixnum Class,” Ruby 3.0.3 Documentation, 2025. [Online]. Available: https://ruby-doc.org/core-3.0.3/Fixnum.html. [Accessed: 5-Sep-2025].

[10] “Bignum Class,” Ruby 3.0.3 Documentation, 2025. [Online]. Available: https://ruby-doc.org/core-3.0.3/Bignum.html. [Accessed: 5-Sep-2025].

[11] G. Dave, "Ruby | Rational rational() function," GeeksforGeeks, 12 Jul. 2025. [Online]. Available: https://www.geeksforgeeks.org/ruby/ruby-rational-rational-function/. [Accessed: 5-Sep-2025].

## C ##

[12] “Data Types in C,” GeeksforGeeks, Last updated 22 Jun. 2025. [Online]. Available: https://www.geeksforgeeks.org/data-types-in-c/. [Accessed: 5-Sep-2025].

[13] “C Floating Point Types,” TutorialsPoint, 2025. [Online]. Available: https://www.tutorialspoint.com/cprogramming/c_data_types.htm. [Accessed: 5-Sep-2025].

## Java ##

[14] “Java Primitive Data Types,” Oracle, 2025. [Online]. Available: https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html. [Accessed: 5-Sep-2025].

[15] “Java Rational Numbers,” Baeldung, Last updated 15 Aug. 2025. [Online]. Available: https://www.baeldung.com/java-rational-numbers. [Accessed: 5-Sep-2025].

## Python ##

[16] “Numeric Types — int, float, complex,” Python 3 Documentation, 2025. [Online]. Available: https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex. [Accessed: 5-Sep-2025].

[17] “Python Fractions Module,” GeeksforGeeks, Last updated 18 Jul. 2025. [Online]. Available: https://www.geeksforgeeks.org/python-fractions-module/. [Accessed: 5-Sep-2025].

