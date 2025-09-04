# Ruby Math Functions and Methods

การใช้งานฟังก์ชันและเมธอดต่าง ๆ ทางคณิตศาสตร์ของภาษาเขียนโปรแกรม Ruby

ในภาษาเขียนโปรแกรม Ruby มี module ที่ชื่อว่า Math ช่วยให้สามารถใช้งานค่าคงที่และฟังก์ชันทางคณิตศาสตร์ในภาษา Ruby ได้

ซึ่งประกอบไปด้วย

* ค่าคงที่ทางคณิตศาสตร์
* [ruby-math-constants.md](ruby-math-constants.md "mention")
* ฟังก์ชันทางคณิตศาสตร์
* [ruby-math-methods.md](ruby-math-methods.md "mention")
  * [p01.trigonometric-functions.md](ruby-math-methods-and-example/p01.trigonometric-functions.md "mention")
  * [p02.inverse-trigonometric-functions.md](ruby-math-methods-and-example/p02.inverse-trigonometric-functions.md "mention")
  * [p03.hyperbolic-trigonometric-functions.md](ruby-math-methods-and-example/p03.hyperbolic-trigonometric-functions.md "mention")
  * [p04.inverse-hyperbolic-trigonometric-functions.md](ruby-math-methods-and-example/p04.inverse-hyperbolic-trigonometric-functions.md "mention")
  * [p05.exponentiation-and-logarithmic-functions.md](ruby-math-methods-and-example/p05.exponentiation-and-logarithmic-functions.md "mention")
  * [p06.fraction-and-exponent-functions.md](ruby-math-methods-and-example/p06.fraction-and-exponent-functions.md "mention")
  * [p07.root-functions.md](ruby-math-methods-and-example/p07.root-functions.md "mention")
  * [p08.error-functions.md](ruby-math-methods-and-example/p08.error-functions.md "mention")
  * [p09.gamma-functions.md](ruby-math-methods-and-example/p09.gamma-functions.md "mention")
  * [p10.hypotenuse-function.md](ruby-math-methods-and-example/p10.hypotenuse-function.md "mention")
* ข้อผิดพลาดโดเมนคณิตศาสตร์
* [ruby-domainerror.md](ruby-domainerror.md "mention")

## การเพิ่มโมดูลคณิตศาสตร์ในภาษาต่าง ๆ

Ruby

```ruby
include Math
```

C

```c
#include <math.h>
```

Java

```java
import java.lang.Math.*;
```

Python

```python
import math
#or
import cmath # สำหรับจัดการจำนวนเชิงซ้อนจะมีบวกจำนวนเชิงซ้อนต่อท้าย 
#เช่น print(cmath.sqrt(9)) # Output: (3+0j)
#สำหรับเอกสารนี้อธิบายเพียง math
```
