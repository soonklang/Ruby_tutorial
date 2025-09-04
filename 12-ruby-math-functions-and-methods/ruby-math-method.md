# Ruby Math Methods
ใน module Math ของภาษาเขียนโปรแกรม Ruby มีฟังก์ชันทางคณิตศาสตร์ที่ใช้ผ่านเมธอด

<mark style="color:$success;">**Domain**</mark>**&#x20;แทนช่วงค่าที่สามารถใส่ได้**

<mark style="color:$warning;">**Range**</mark>**&#x20;แทนช่วงค่าที่ส่งกลับมาให้**

**ฟังก์ชันตรีโกณมิติ** ฟังก์ชันตรีโกณมิติผกผัน ฟังก์ชันตรีโกณมิติไฮเพอร์โบลิก ฟังก์ชันตรีโกณมิติไฮเพอร์โบลิกผกผัน **ทั้งหมดจะใช้เป็นระบบเรเดียน**

### <mark style="color:$danger;">Ruby</mark>

การเรียกใช้ฟังก์ชันคณิตศาสตร์ในภาษาเขียนโปรแกรม Ruby สามารถเรียกผ่าน Math.เมธอดที่ต้องการ หรือ เมื่อ include Math แล้วจะสามารถเรียกใช้เมธอดฟังก์ชันทางคณิตศาสตร์ได้โดยตรง

{% tabs %}
{% tab title="เรียกผ่าน module" %}
```ruby
Math.sin(0.0) # => 0.0
Math.cos(0.0) # => 1.0
```
{% endtab %}

{% tab title="เรียกโดยตรง" %}
```ruby
include Math
sin(0.0) # => 0.0
cos(0.0) # => 1.0
```
{% endtab %}
{% endtabs %}

{% include "../../.gitbook/includes/line.md" %}

### <mark style="color:$danger;">C</mark>

ภาษาเขียนโปรแกรม C ก็มีฟังก์ชันทางคณิตศาสตร์เช่นกัน

เมื่อ #include \<math.h> แล้วจะสามารถเรียกใช้เมธอดฟังก์ชันทางคณิตศาสตร์ได้โดยตรง

```c
sin(M_PI/4) // 0.707107
cos(M_PI/4) // 0.707107
tan(M_PI/4) // 1.000000
```

นอกจากนี้ ตั้งแต่ C99 เป็นต้นไป หากใช้ฟังก์ชันคณิตศาสตร์ที่เติม f หรือ l ต่อท้ายจะสามารถระบุชนิดค่าส่งคืนที่ต้องการได้

```c
sinf( float arg ); // return float
sin( double arg ); // return double
sinl( long double arg ); // return long double
```

{% include "../../.gitbook/includes/line.md" %}

### <mark style="color:$danger;">Java</mark>

การใช้ฟังก์ชันทางคณิตศาสตร์ในภาษาเขียนโปรแกรม **Java** <mark style="color:$info;">ถึงจะไม่</mark> <mark style="color:$info;"></mark><mark style="color:$info;">`import java.lang.math;`</mark> <mark style="color:$info;"></mark><mark style="color:$info;">ก็สามารถใช้ค่าคงที่ทางคณิตศาสตร์ได้เลย</mark> เพราะ java.lang จะถูก import อัตโนมัติ เหมือนมี `import java.lang.*;` ที่จุดเริ่มต้นของ compiler ทันทีหลังจาก`package`ใดก็ตาม

ใช้ฟังก์ชันทางคณิตศาสตร์ได้โดยการใช้ Math.เมธอดที่ต้องการ

```java
Math.sin(Math.PI/4) // 0.7071067811865475
Math.cos(Math.PI/4) // 0.7071067811865475
Math.tan(Math.PI/4) // 0.9999999999999999 
```

{% include "../../.gitbook/includes/line.md" %}

### <mark style="color:$danger;">Python</mark>

ภาษาเขียนโปรแกรม **Python** ก็มีฟังก์ชันทางคณิตศาสตร์เช่นกัน

เมื่อ import math แล้วจะสามารถเรียกใช้เมธอดฟังก์ชันทางคณิตศาสตร์ได้

ใช้ฟังก์ชันทางคณิตศาสตร์ได้โดยการใช้ math.เมธอดที่ต้องการ

```python
math.sin(math.pi/4) # 0.7071067811865475
math.cos(math.pi/4) # 0.7071067811865476
math.tan(math.pi/4) # 0.9999999999999999 
```
