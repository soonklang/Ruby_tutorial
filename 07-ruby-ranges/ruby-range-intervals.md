# Ruby Range Intervals

Ruby Range Intervals คือ การกำหนดช่วงของค่า เช่น เลข 1 ถึง 20 หรือ ตัวอักษร a ถึง z เป็นต้น เพื่อให้เราสามารถตรวจสอบได้ว่าสิ่งที่เราสนใจอยู่ในช่วงนั้นหรือไม่ โดยจะใช้ "===" เพื่อตรวจสอบ

ตัวอย่างที่ 1 :

```ruby
# ตัวอย่างเลขของค่าที่กำหนด อยู่ในช่วงของค่า
if ((1..10) === 5) # หากอยู่ในช่วงจะทำตามคำสั่งใน if
   puts "5 lies in (1..10)" # แสดงผลลัพธ์
end
# ตัวอย่างเลขของค่าที่กำหนด ไม่ได้อยู่ในช่วงของค่า
if ((1..10) === 12) # หากอยู่ในช่วงจะทำตามคำสั่งใน if
   puts "12 is not lies in (1..10)" # แสดงผลลัพธ์
end
# ตัวอย่างตัวอักษรของค่าที่กำหนด อยู่ในช่วงของค่า
if (('a'..'j') === 'c') # หากอยู่ในช่วงจะทำตามคำสั่งใน if
   puts "c lies in ('a'..'j')" # แสดงผลลัพธ์
end
# ตัวอย่างตัวอักษรของค่าที่กำหนด ไม่ได้อยู่ในช่วงของค่า
if (('a'..'j') === 'z') # หากอยู่ในช่วงจะทำตามคำสั่งใน if
   puts "z is not lies in ('a'..'j')" # แสดงผลลัพธ์
end
```

***

## เปรียบเทียบกับภาษา Java, C และ Python

### Java

ในภาษา Java นั้นไม่มี feature built-in แบบเดียวกับ Ruby แต่ใน Java สามารถทำในสิ่งที่คล้ายๆกันได้ ซึ่งมีหลากหลายวิธี เช่น การเขียนเงื่อนไข ( if-else ) หรือ การใช้ IntStream ซึ่งอาจจะคล้ายกับ Ruby Range Intervals ในการทำงานกับตัวเลข โดยการใช้ method range() หรือ rangeClosed()

ตัวอย่างที่ 1 ในภาษา Java :&#x20;

```java
import java.util.stream.IntStream;

public class Demo {
   public static void main(String[] args) {
      IntStream intStream = IntStream.rangeClosed(15, 25);
      intStream.forEach(System.out::println);
   }
}
```

หากนำมาประยุกต์ใช้จะได้ดังนี้

ตัวอย่างที่ 2 ในภาษา Java :&#x20;

```java
import java.util.stream.IntStream;

public class Demo {
   public static void main(String[] args) {
      boolean isInRane = IntStream.rangeClosed(1, 10).anyMatch(n -> n == 5);
      if(isInRange){
         System.out.println("5 5 lies in (1..10)");
      }
   }
}
```

### C

ในภาษา C นั้นไม่มี feature built-in แบบเดียวกับ Ruby แต่ใน C สามารถทำในสิ่งที่คล้ายๆกันได้ ซึ่งมีหลากหลายวิธี เช่น การใช้ for-loop หรือ เขียน function ขึ้นมาเอง เป็นต้น

ตัวอย่างที่ 1 ในภาษา C : &#x20;

```c
#include <stdio.h>

int main() {
    int x = 5;
    for (int i = 1; i <= 10; i++) {
        if(i == x){
            printf("%d lies in (1..10)\n", x);
        }
    }
    return 0;
}
```

### Python

ในภาษา Python นั้นไม่มี feature built-in แบบเดียวกับ Ruby แต่ใน Python สามารถทำในสิ่งที่คล้ายๆกันได้ ซึ่งมีหลากหลายวิธี เช่น การใช้ range() หรือใช้ เงื่อนไข ( if-else ) เป็นต้น

ตัวอย่างที่ 1 ในภาษา Python :&#x20;

```python
for i in range(5):
    print(i, end=" ")
print()
```

หากนำมาประยุกต์ใช้จะได้ดังนี้

ตัวอย่างที่ 2 ในภาษา Python :&#x20;

```python
x = 5
if x in range(1, 11):
    print(f"{x} lies in (1..10)")
```

***

## อ้างอิง

**Techotopia**. _Ruby Ranges_. Techotopia, n.d.,\
[https://www.techotopia.com/index.php/Ruby\_Ranges](https://www.techotopia.com/index.php/Ruby_Ranges)

**Tutorialspoint**. _Ruby – Ranges_. Tutorialspoint, n.d.,\
[ps://www.tutorialspoint.com/ruby/ruby\_ranges.htm](https://www.tutorialspoint.com/ruby/ruby_ranges.htm)

**Tutorialspoint**. _IntStream rangeClosed() method in Java_. Tutorialspoint, 30 July 2019,\
[https://www.tutorialspoint.com/intstream-rangeclosed-method-in-java](https://www.tutorialspoint.com/intstream-rangeclosed-method-in-java)

**Oracle**. _IntStream_. _Java Platform, Standard Edition 8 API Specification_, Oracle, 2014,\
[https://docs.oracle.com/javase/8/docs/api/java/util/stream/IntStream.html#range-int-int-](https://docs.oracle.com/javase/8/docs/api/java/util/stream/IntStream.html#range-int-int-)

**GeeksforGeeks**. _Python range() function_. GeeksforGeeks, 11 July 2025, \
[https://www.geeksforgeeks.org/python/python-range-function/](https://www.geeksforgeeks.org/python/python-range-function/)

***

## Slide Presentation
- [Slide](https://github.com/nueyy/video-slide-download/blob/main/650710837_Slide.pdf)

***

## Video
- [Video](https://www.youtube.com/watch?v=aBKeur6dQyE)
