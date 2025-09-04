---
description: การใช้งานฟังก์ชันและเมธอดต่าง ๆ ทางคณิตศาสตร์ของภาษาเขียนโปรแกรม Ruby
icon: gem
---

# Ruby Math Functions and Methods

ในภาษาเขียนโปรแกรม Ruby มี module ที่ชื่อว่า Math ช่วยให้สามารถใช้งานค่าคงที่และฟังก์ชันทางคณิตศาสตร์ในภาษา Ruby ได้

ซึ่งประกอบไปด้วย

* ค่าคงที่ทางคณิตศาสตร์
* [ruby-math-constants.md](ruby-math-functions-and-methods/ruby-math-constants.md "mention")
  * [#undefined](ruby-math-functions-and-methods/ruby-math-constants.md#undefined "mention")
  * [#undefined-1](ruby-math-functions-and-methods/ruby-math-constants.md#undefined-1 "mention")
    * [#module](ruby-math-functions-and-methods/ruby-math-constants.md#module "mention")
    * [#undefined-3](ruby-math-functions-and-methods/ruby-math-constants.md#undefined-3 "mention")
* ฟังก์ชันทางคณิตศาสตร์
* [ruby-math-methods.md](ruby-math-functions-and-methods/ruby-math-methods.md "mention")
  * [p01.trigonometric-functions.md](ruby-math-functions-and-methods/ruby-math-methods-1/p01.trigonometric-functions.md "mention")
  * [p02.inverse-trigonometric-functions.md](ruby-math-functions-and-methods/ruby-math-methods-1/p02.inverse-trigonometric-functions.md "mention")
  * [p03.hyperbolic-trigonometric-functions.md](ruby-math-functions-and-methods/ruby-math-methods-1/p03.hyperbolic-trigonometric-functions.md "mention")
  * [p04.inverse-hyperbolic-trigonometric-functions.md](ruby-math-functions-and-methods/ruby-math-methods-1/p04.inverse-hyperbolic-trigonometric-functions.md "mention")
  * [p05.exponentiation-and-logarithmic-functions.md](ruby-math-functions-and-methods/ruby-math-methods-1/p05.exponentiation-and-logarithmic-functions.md "mention")
  * [p06.fraction-and-exponent-functions.md](ruby-math-functions-and-methods/ruby-math-methods-1/p06.fraction-and-exponent-functions.md "mention")
  * [p07.root-functions.md](ruby-math-functions-and-methods/ruby-math-methods-1/p07.root-functions.md "mention")
  * [p08.error-functions.md](ruby-math-functions-and-methods/ruby-math-methods-1/p08.error-functions.md "mention")
  * [p09.gamma-functions.md](ruby-math-functions-and-methods/ruby-math-methods-1/p09.gamma-functions.md "mention")
  * [p.10hypotenuse-function.md](ruby-math-functions-and-methods/ruby-math-methods-1/p.10hypotenuse-function.md "mention")
* ข้อผิดพลาดโดเมนคณิตศาสตร์
* [ruby-domainerror.md](ruby-math-functions-and-methods/ruby-domainerror.md "mention")

## การเพิ่มโมดูลคณิตศาสตร์ในภาษาต่าง ๆ

{% code title="Ruby" %}
```ruby
include Math
```
{% endcode %}

{% code title="C" %}
```c
#include <math.h>
```
{% endcode %}

{% code title="Java" %}
```java
import java.lang.Math.*;
```
{% endcode %}

{% code title="Python" %}
```python
import math
#or
import cmath # สำหรับจัดการจำนวนเชิงซ้อนจะมีบวกจำนวนเชิงซ้อนต่อท้าย 
#เช่น print(cmath.sqrt(9)) # Output: (3+0j)
#สำหรับเอกสารนี้อธิบายเพียง math
```
{% endcode %}
