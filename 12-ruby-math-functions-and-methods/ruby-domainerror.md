# Ruby DomainError

ข้อผิดพลาดของโดเมน

### Ruby

_Main::DomainError_

เกิดขึ้นเมื่อฟังก์ชันทางคณิตศาสตร์ได้รับพารามิเตอร์นอกคำจำกัดความทางคณิตศาสตร์

เช่น cos จะส่งคืนค่าในช่วง `[-1, 1]` ฟังก์ชันผกผัน acos จึงถูกกำหนดบนช่วงนั้นเท่านั้น:

```ruby
Math.acos(42)
```

ผลลัพธ์ _:_

```
Math::DomainError: อาร์กิวเมนต์ตัวเลขอยู่นอกโดเมน - "acos"
```

***

### C

เมื่อ #include \<errno.h> จะสามารถใช้ตัวแปร errno ได้ ซึ่งจะเปลี่ยนค่าเป็น error ต่าง ๆ

```c
#include <stdio.h>
#include <math.h>
#include <errno.h>

int main() {
   double invalid_value = 2.0; 

   double result = asin(invalid_value);
   if (errno == EDOM) {
       printf("Arcsine of %f is not defined.\n", invalid_value);
   } else {
       printf("Arcsine of %f = %f radians\n", invalid_value, result);
   }

   return 0;
}
```

ผลลัพธ์:

```
Arcsine of 2.000000 is not defined.
```

จากข้างต้น errno จาก header errno จะเปลี่ยนเป็น EDOM เมื่อมี domain error เกิดขึ้น

และถ้าจะใช้ errno อีกจำเป็นต้องกำหนดค่าเป็น 0 เพราะมันจะไม่กำหนดค่ากลับอัตโนมัติ

```c
#include <stdio.h>
#include <errno.h>
#include <math.h>

int main () {
   double val;

   errno = 0;
   val = sqrt(-10);   
   if(errno == EDOM) {
      printf("Invalid value \n");
   } else {
      printf("Valid value\n");
   }
   
   errno = 0;
   val = sqrt(10);
   if(errno == EDOM) {
      printf("Invalid value\n");
   } else {
      printf("Valid value\n");
   }
   return(0);
}
```

ผลลัพธ์:

```
Invalid value
Valid value
```

***

### Java

ในภาษาเขียนโปรแกรม Java หาก DomianError จะไม่มีตัวจัดการโดยตรง แต่ค่าของฟังก์ชันนั้นจะเป็น NaN แล้วต้องเขียนเงื่อนไขเอง สามารถใช้ร่วมกับการกำหนด IllegalArgumentException เพื่อแจ้งเตือน error ด้วยตนเอง

```java
public class Main{
    public static void main(String[] args) {
        double result = Math.sqrt(-1.0);
        System.out.println(result); // Output: NaN
        if (Double.isNaN(result)) {
            throw new IllegalArgumentException("Input must be >= 0.0");
        }
    }
}
```

ผลลัพธ์:

```
NaN
ERROR!
Exception in thread "main" java.lang.IllegalArgumentException: Input must be >= 0.0
at Erf.main(Main.java:6)
```

***

### Python

ในภาษาเขียนโปรแกรม Python หาก DomianError จะมี ValueError สำหรับจัดการเรื่องนี้ เมื่อใส่ค่านอกโดเมนในฟังก์ชันคณิตศาสตร์จะแจ้ง error ว่า math domain error

```python
import math
math.sqrt(-10)
```

ผลลัพธ์:

```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: math domain error
```
