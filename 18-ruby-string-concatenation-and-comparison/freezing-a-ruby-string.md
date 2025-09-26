# Freezing a Ruby String

# เนื้อหา
ปกติในภาษา Ruby การแก้ไข String หนึ่งจะสามารถทำได้ทันที (Mutable Object เช่น String , Array , Hash)

แต่ถ้าอยากให้แก้ไขไม่ได้จะต้องทำการ Freeze ใส่ String หรือวัตถุนั้นๆ


- โดยเราจะต้องใช้คำสั่ง .freeze กับ String หรือ Object ใดๆ 

- จะเหมือนเป็นการล็อก String นั้นไว้ ไม่ให้แก้ค่าได้


-> ตัวอย่างโค้ด
<pre>s = "Hello"
s << " World"
puts s </pre>

จากโค้ด 3 บรรทัดบน ถ้ารันจะพบว่า Output = "Hello World" เนื่องจาก String นั้นยัง mutable by default (ยังแก้ไขค่าได้อยู่)

<pre>s = "Hello"
s << " World"
s.freeze
s << " Peace" </pre>

จากโค้ด 4 บรรทัดบน ถ้ารันจะพบ Error = can't modify frozen String: "Hello World" (FrozenError)

ที่เกิด error ดังกล่าวเพราะว่า เราพยายามแก้ String ที่ถูก freeze ไปแล้ว (.freeze) ซึ่งจะเป็น error ชนิดที่ชื่อว่า FrozenError


ซึ่งถ้าอยากแก้ไข อาจทำได้โดยการสร้าง String ใหม่ แล้วแก้แทน


-> ตัวอย่างโค้ด
<pre>str = "Hello World"
str.freeze
new_str = str + "!"
puts new_str </pre>

#### จากแหล่งที่มา https://www.techotopia.com/index.php/Ruby_String_Concatenation_and_Comparison#Freezing_a_Ruby_String



ส่วนการคืนค่าของ String ที่ Freeze แล้วนั้นสามารถทำได้โดยใช้ -@ กับ +@

; "-@" จะเป็นการคืนค่า String ที่ Freeze แล้ว

- โดยถ้า freeze แล้วจะคืนตัวเดิม แต่ถ้ายังไม่ freeze จะทำการ freeze แล้วถึงค่อยคืน


-> ตัวอย่างโค้ด
<pre>a = "Hello"
b = -a
b << "World" </pre>

โค้ดนี้จะ error บรรทัดที่ 3 เนื่องจาก b นั้นคือออบเจกต์เดียวกับ a แต่ถูก freeze ไว้แล้ว จึงเปลี่ยนค่าไม่ได้ (FrozenError)



; "+@" จะเป็นการคืนค่า String ที่ไม่มีการ freeze

- โดยถ้ายังไม่ถูก freeze จะคืน obj เดิม แต่ถ้า freeze อยู่จะทำการ dup สำเนาใหม่ที่ไม่ froze


-> ตัวอย่างโค้ด
<pre>a = "Hello".freeze
b = +a
b << "World"
puts b </pre>

โค้ดนี้ไม่เกิด error เพราะเป็นการเปลี่ยน string ที่ถูกทำให้ไม่ freeze แล้ว

#### จากแหล่งที่มา https://www.techotopia.com/index.php/Ruby_String_Concatenation_and_Comparison#Freezing_a_Ruby_String




# เปรียบเทียบกับภาษา Java/C/Python

## - Java

ในภาษา Java นั้นได้ถูกออกแบบมาให้ obj บางชนิดเป็น immutable อยู่แล้ว (by default) เช่น String

( Immutable = once it is created, it cannot be changed. )

<pre>String s1 = "knowledge";
String s2 = s1;
s1 = s1.concat(" base");
System.out.println(s1); </pre>

จากโค้ดบนจะ output : knowledge base

ซึ่งเมื่อเรา concat (ต่อสตริง) มันจะสร้างสตริง "knowledge base" และใส่เข้า s1 ซึ่งสตริงเดิม (original) จะยังไม่ถูกเปลี่ยน (The original string remains unchanged.)

#### จาก https://www.geeksforgeeks.org/java/java-string-is-immutable-what-exactly-is-the-meaning/



คำว่า "final" เป็น non-access modifier ซึ่งจะใช้เพื่อป้องกันการแก้ไขข้อมูล

ใช้กับตัวแปร = ค่าไม่เปลี่ยน , ใช้กับเมธอด = ไม่สามารถถูกเขียนทับได้ในคลาสลูก , ใช้กับคลาส = สืบทอดไม่ได้ (cannot be extended)

<pre>final String b = "Hello";
b = "Hola";; </pre>

จากบนจะ error : The final local variable b cannot be assigned. It must be blank and not using a compound assignment

เพราะถ้าตัวแปรถูกประกาศเป็น final แล้วจะ กำหนดค่าให้มันได้เพียงครั้งเดียวเท่านั้น

หลังจากนั้นจะเปลี่ยนค่าไม่ได้อีก

#### จาก https://www.geeksforgeeks.org/java/final-keyword-in-java/



## - C

ในภาษาซีจะไม่มีการสร้างสตริงโดยตรง แต่จะเป็นการสร้างอาร์เรย์ จาก char

ซึ่งจะมีการใช้ const ทำให้ไม่สามารถแก้ไขค่าได้ (ทำให้ variable เป็นแบบ read-only)

<pre>const char s[] = "Hello";
s[0] = 'h';</pre>

จากโค้ดจะ error : error: assignment of read-only variable เพราะพยายามแก้ไข string ที่ immutable เหมือน freeze ไปแล้ว

#### จาก https://www.geeksforgeeks.org/c/const-qualifier-in-c/



## - Python

ในภาษาไพธอน string จะมีความเป็น immutable อยู่แล้ว (คล้ายจาวา)

พูดง่ายๆ เราไม่สามารถแก้ไขตัวอักษรภายใน string เดิมได้ ซึ่งการเปลี่ยน string จะสร้าง string ใหม่ ไม่ใช่แก้ไข string เดิม

<pre>s = "Hello"
s.upper()
print(s)
s = s.upper()
print(s) </pre>

จากโค้ดบน output บรรทัด 3 = Hello , output บรรทัด 5 = HELLO



การใช้ Final ในไพธอน ก็สามารถทำได้เหมือนจาวา แต่แค่มันไม่ built in เราจึงต้อง import ก่อนใช้

<pre>from typing import Final
NAME: Final = "607"
NAME = 608 </pre>

จากโค้ดจะขึ้น Error: can't assign to final attribute



## เปรียบเทียบการ “Freezing String” ใน Ruby, Java, C, Python  

| ภาษา     | String ปกติเป็น mutable? | วิธีทำให้ “freeze”                 | พฤติกรรมเมื่อแก้ไขหลัง freeze                   | หมายเหตุ |
|----------|----------------------|------------------------------------|--------------------------------------------------|-----------|
| Ruby | mutable (<<) | ใช้ .freeze                     | ขึ้น `FrozenError`                         | -@ = คืน string ที่ freeze แล้ว และ +@ คืน string ที่ไม่มีการ freeze |
| Java | immutable (String แก้ไม่ได้อยู่แล้ว) | ไม่ต้อง freeze แต่อาจมีการป้องกันไม่ให้ตัวแปรเปลี่ยนด้วย final | สตริงเดิมไม่ถูกแก้ แต่การ concat จะสร้าง string ใหม่ | final กับตัวแปร = เปลี่ยนค่าไม่ได้, กับ method = override ไม่ได้, กับ class = inherit ไม่ได้ |
| C    | mutable (char array) | ใช้ const char[] | จะเกิด compile-time error (assignment of read-only variable) | string literal เก็บใน read-only memory; const ทำให้แก้ไม่ได้ |
| Python | immutable (เหมือน Java) | ไม่ต้อง freeze แต่อาจมีการใช้ Final (ต้อง import เพิ่ม) | การแก้จะสร้าง string ใหม่แทน | ใช้ Final ได้ แต่จะเป็น type checker ไม่ใช่ runtime |

[ไฟล์ Slide PDF](https://drive.google.com/file/d/1mXw1s9w6qAV3H645ag8ZgmJImHiUVyVm/view?usp=drive_link)

[ไฟล์ Slide PPTX](https://docs.google.com/presentation/d/1gYQQqxRACCdtWzDjj6Zw5aOqAij2K4-6)

[ลิงค์ Youtube](https://www.youtube.com/watch?v=ICTjlLDF75Y)
