# Freezing a Ruby String

# เนื้อหา
Ruby การแก้ไข String จะสามารถทำได้ทันที (Mutable)

ถ้าอยากให้แก้ไขไม่ได้จะต้องทำการ Freeze ใส่ String หรือวัตถุนั้นๆ


-  ใช้คำสั่ง .freeze กับ String

- จะเหมือนเป็นการล็อก String นั้นไว้ ไม่ให้แก้ค่าได้


-> ตัวอย่าง
<pre>s = "Hello“
s << " World“
puts s </pre>

Output = "Hello World"

-> ตัวอย่าง
<pre>s = "Hello“
s << " World“
s.freeze
s << " Peace" </pre>

Output = Error can't modify frozen String: "Hello World" (FrozenError)

เพราะว่า เราพยายามแก้ String ที่ถูก freeze ไปแล้ว (.freeze) ซึ่งจะเป็น error ชนิดที่ชื่อว่า FrozenError


ซึ่งถ้าอยากแก้ไข อาจทำได้โดยการสร้าง String ใหม่  , แล้วค่อยแก้แทน


-> ตัวอย่าง
<pre>str = "Hello World“
str.freeze
new_str = str + "!“
puts new_str </pre>

#### จากแหล่งที่มา https://www.techotopia.com/index.php/Ruby_String_Concatenation_and_Comparison#Freezing_a_Ruby_String



การคืนค่าของ String

; "-@" จะเป็นการคืนค่า String ที่ Freeze แล้ว

- โดยถ้า freeze แล้วจะคืนตัวเดิม แต่ถ้ายังไม่ freeze จะทำการ freeze แล้วถึงค่อยคืน


-> ตัวอย่าง
<pre>a = "Hello"
b = -a
b << "World" </pre>

จะ error บรรทัด 3 เนื่องจาก b นั้นคือออบเจกต์เดียวกับ a แต่ถูก freeze ไว้แล้ว จึงเปลี่ยนค่าไม่ได้ (FrozenError)



; "+@" จะเป็นการคืนค่า String ที่ไม่มีการ freeze




-> ตัวอย่างโค้ด
<pre>a = "Hello".freeze
b = +a
b << "World"
puts b </pre>

ไม่เกิด error เพราะเป็นการเปลี่ยน string ที่ไม่ freeze

#### จากแหล่งที่มา https://www.techotopia.com/index.php/Ruby_String_Concatenation_and_Comparison#Freezing_a_Ruby_String




# เปรียบเทียบกับภาษา Java/C/Python

## - Java

String ใน Java เป็น Immutable อยู่แล้ว


-> ตัวอย่าง
<pre>String s = "Hello";
s.concat(" World");
System.out.println(s); 
</pre>

Output: Hello

-> ตัวอย่าง
<pre>s = s.concat(" World");
System.out.println(s); 
</pre>

Output: Hello World



#### จาก https://www.geeksforgeeks.org/java/java-string-is-immutable-what-exactly-is-the-meaning/



ใช้ "final" 

ป้องกันการเปลี่ยนแปลงค่าโดยไม่ตั้งใจ 

-> ตัวอย่าง
<pre>final String a = "Hello";
a = “Hi”; 
</pre>

Output = error : The final local variable b cannot be assigned.

เพราะเป็น final จะ กำหนดค่าได้เพียงครั้งเดียวเท่านั้น
หลังจากนั้นจะเปลี่ยนค่าไม่ได้อีก


#### จาก https://www.geeksforgeeks.org/java/final-keyword-in-java/



## - C

ไม่มีการสร้างสตริง แต่จะเป็นการสร้างอาร์เรย์ จาก char
- ใช้ const ทำให้ไม่สามารถแก้ไขค่าได้ (read-only)

-> ตัวอย่าง
<pre>const char s[] = "Hello";
s[0] = ‘h’;
</pre>

Output = error: assignment of read-only variable เพราะแก้ไข string ที่ immutable แล้ว

#### จาก https://www.geeksforgeeks.org/c/const-qualifier-in-c/



## - Python

ในภาษาไพธอน string จะมีความเป็น immutable อยู่แล้ว 
(คล้ายจาวา)

พูดง่ายๆ เราไม่สามารถแก้ไขตัวอักษรภายใน string เดิมได้ ซึ่งการเปลี่ยน string จะสร้าง string ใหม่ ไม่ใช่แก้ไข string เดิม

-> ตัวอย่าง
<pre>s = "Hello"
s.upper()
print(s)
s = s.upper()
print(s) </pre>

จากโค้ดบน output บรรทัด 3 = Hello , output บรรทัด 5 = HELLO



ในไพธอน สามารถทำใช้ Final ได้แต่ต้อง Import

-> ตัวอย่าง
<pre>from typing import Final
NAME: Final = "607"
NAME = 608 </pre>

Output = error: Cannot assign to final name "x" 



## เปรียบเทียบการ “Freezing String” ใน Ruby, Java, C, Python  

| ภาษา     | String ปกติเป็น mutable? | วิธีทำให้ “freeze”                 | พฤติกรรมเมื่อแก้ไขหลัง freeze                   | หมายเหตุ |
|----------|----------------------|------------------------------------|--------------------------------------------------|-----------|
| Ruby | mutable  | ใช้ .freeze                     | ขึ้น `FrozenError`                         | -@ = คืน string ที่ freeze แล้ว และ +@ คืน string ที่ไม่มีการ freeze |
| Java | immutable (String แก้ไม่ได้อยู่แล้ว) | ไม่ต้อง freeze แต่อาจมีการป้องกันไม่ให้ตัวแปรเปลี่ยนด้วย final | สตริงเดิมไม่ถูกแก้ แต่จะสร้าง string ใหม่แทน | final กับตัวแปร = เปลี่ยนค่าไม่ได้, กับ method = override ไม่ได้, กับ class = inherit ไม่ได้ |
| C    | mutable (char array) | ใช้ const char[] | จะเกิด compile-time error (assignment of read-only variable) | string literal เก็บใน read-only memory; const ทำให้แก้ไม่ได้ |
| Python | immutable (เหมือน Java) | ไม่ต้อง freeze แต่อาจมีการใช้ Final (ต้อง import เพิ่ม) | การแก้จะสร้าง string ใหม่แทน | ใช้ Final ได้ แต่จะเป็น type checker ไม่ใช่ runtime |

[ไฟล์ Slide PDF](https://drive.google.com/file/d/1LQWBZHEEOt0C_fXZwEyf8NdGr7pP6Qq3)

[ไฟล์ Slide PPTX](https://docs.google.com/presentation/d/1CaTPo1svv6tO9WSD0ZKCgshqN4vBUzTX)

[ลิงค์ Youtube](https://www.youtube.com/watch?v=ICTjlLDF75Y)
