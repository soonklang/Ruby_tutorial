# Ruby Math Constants
ใน module Math ของภาษาเขียนโปรแกรม Ruby มีค่าคงที่ทางคณิตศาสตร์ที่ใช้กันทั่วไป 2 ค่า

## <mark style="color:$danger;">ค่าคงที่ทางคณิตศาสตร์มีอะไรบ้าง</mark>

สามารถใช้เมธอด <mark style="color:yellow;">constants</mark> ของ module <mark style="color:$primary;">Math</mark> เพื่อดูค่าคงที่ภายใน module <mark style="color:$primary;">Math</mark>

<pre class="language-ruby"><code class="lang-ruby"><strong>Math.constants # PI E
</strong></code></pre>

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

สังเกตได้ว่าจะมี <mark style="color:blue;">PI E</mark> และ <mark style="color:blue;">DomainError</mark>&#x20;

ค่าคงที่มีเพียงค่าพาย <mark style="color:blue;">PI</mark> (π) และค่าออยเลอร์ <mark style="color:blue;">E</mark> (e) มีชนิดข้อมูลเป็น float

ส่วน <mark style="color:blue;">DomainError</mark> เป็นเพียง Exception สำหรับ error เมื่อค่าตัวเลขที่ใส่ลงไปในฟังก์ชันคณิตศาสตร์ ไม่สามารถเป็นโดเมนได้

***

## <mark style="color:$danger;">การเรียกใช้งานค่าคงที่ทางคณิตศาสตร์</mark>

สามารถเรียกใช้งานผ่าน module Math โดยเรียกผ่านเครื่องหมาย ::                                                                      หรือ include module <mark style="color:$primary;">Math</mark> แล้วจะสามารถเรียกได้โดยตรง

เรียกผ่าน module
```ruby
Math::PI   # => 3.141592653589793
Math::E   # => 2.718281828459045
```

เรียกโดยตรง
```ruby
include Math
PI   # => 3.141592653589793
E   # => 2.718281828459045
```

<div data-full-width="false"><figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure></div>

***

### <mark style="color:$danger;">C</mark>

ค่าคงที่ทางคณิตศาสตร์ไม่ได้ถูกกำหนดไว้ในภาษา C มาตรฐาน

ในการใช้ค่าคงที่เหล่านี้ คุณต้อง `#define _USE_MATH_DEFINES` แล้ว `#include<math.h>` ลงไป

```c
#define _USE_MATH_DEFINES // for C 
#include <math.h>
```

เมื่อทำตามขั้นตอนข้างต้นจะสามารถใช้ M\_PI สำหรับค่าพาย และ M\_E สำหรับค่าออยเลอร์

```c
M_PI // 3.14159265358979323846
M_E // 2.71828182845904523536
```

***

### <mark style="color:$danger;">Java</mark>

ในภาษาเขียนโปรแกรม Java <mark style="color:$info;">ถึงจะไม่</mark> <mark style="color:$info;"></mark><mark style="color:$info;">`import java.lang.math;`</mark> <mark style="color:$info;"></mark><mark style="color:$info;">ก็สามารถใช้ค่าคงที่ทางคณิตศาสตร์ได้เลย</mark>    เพราะ java.lang จะถูก import อัตโนมัติ เหมือนมี `import java.lang.*;` ที่จุดเริ่มต้นของ compiler ทันทีหลังจาก`package`ใดก็ตาม สามารถใช้ Math.PI สำหรับค่าพาย และ Math.E สำหรับค่าออยเลอร์

```java
Math.PI // 3.141592653589793
Math.E // 2.718281828459045
```

***

### <mark style="color:$danger;">Python</mark>

ในภาษาเขียนโปรแกรม Python module Math เป็น module มาตรฐานของ Python ที่สามารถใช้สำหรับการทำงานทางคณิตศาสตร์ การใช้ค่าคงที่จะต้อง `import math` ก่อน

```python
import math
```

เมื่อทำตามขั้นตอนข้างต้นจะสามารถใช้ math.pi สำหรับค่าพาย และ math.e สำหรับค่าออยเลอร์

```python
math.pi # 3.141592653589793
math.e # 2.718281828459045
```
