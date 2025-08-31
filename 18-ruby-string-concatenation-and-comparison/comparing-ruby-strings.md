# Comparing Ruby Strings

ใน Ruby เราจะมีการเปรียบเทียบ(Comparing) ข้อความ(String) ได้หลายวิธีมาก เพื่อการนำไปใช้ต่อ หรือแม้กระทั่งใช้ประโยชน์ในการ เรียงข้อมูล(Sort) ได้ด้วย ซึ่งในบทความนี้จะพูดถึงการ เปรียบเทียบข้อความแบบ Case-sensitive  &#x20;

## การใช้ ==

การใช้ == ในภาษา Ruby เป็นการใช้ตรวจสอบค่า (content) ของ ข้อความ 2 ข้อความ ว่าเท่ากันและเหมือนกันทุกประการหรือไม่

### ตัวอย่างการใช้ ==

```
str1 = "Hello"
str2 = "hello"

puts str1 == str2

#output :
false
```

ในตัวอย่างนี้เราจะเห็นว่า เราได้เทียบ str1 ที่มีค่า "Hello" กับ str2 ที่มีค่า "hello"  แล้วได้ค่า false เพราะว่า&#x20;

H และ h ถือว่าเป็นตัวอักษรคนละตัวกัน &#x20;

```
str1 = "Hello"
str3 = "Hello , World"

puts str1 == str3

#output :
false
```

ในตัวอย่างนี้เราจะเห็นว่า เราได้เทียบ str1 ที่มีค่า "Hello" กับ str3 ที่มีค่า "Hello , World" แล้วได้ค่า false เพราะว่า

str1 มีค่าไม่เหมือนกับ str3 &#x20;

```
str1 = "Hello"

puts str1 == "Hello"

#output :
true
```

ในตัวอย่างนี้เราจะเห็นว่า เราได้เทียบ str1 ที่มีค่า "Hello" กับ "Hello" แล้วได้ค่า true เพราะว่า&#x20;

str1 มีค่าเป็น "Hello" เหมือนข้อความที่เรานำไปเทียบ&#x20;



## การใช้ eql?

การใช้ eql? จะคล้ายกับ == แต่มีข้อแตกต่างตรงที่ eal? จะเทียบทั้งค่าและ ประเภทข้อชนิดข้อมูล (Data Types)&#x20;

### ตัวอย่างการใช้ eql?

```
var1 = "1234"
var2 = 1234

puts var1 == var2

#output :
false
```

ในตัวอย่างนี้เราจะเห็นว่า เราได้เทียบ var1 ที่มีค่า "1234" กับ var2 ที่มีค่า 1234 แล้วได้ค่า false\
เพราะ แม้ค่าข้างในของ var1 และ var2 จะมีค่าเหมือนกัน แต่ว่า var1 มีชนิดข้อมูลเป็น String แต่ var2 มีชนิดข้อมูล\
เป็น Integer จึงทำให้ได้ false&#x20;

```
str1 = "Ruby!"

puts str1.eql?("Ruby!")

#output :
true
```

ในตัวอย่างนี้เราจะเห็นว่า เราได้เทียบ str1 ที่มีค่า "Ruby!" กับ "Ruby!" แล้วได้ค่า true\
เพราะ ค่าของ str1 กับ "Ruby!" เหมือนกัน และ str1 มีชนิดข้อมูลเป็น String คำว่า "Ruby!" ก็มีชนิดข้อมูลเป็น String\
จึงทำให้ได้ true

```
str1 = "Ruby!"

puts str1.eql?("ruby!")

#output :
false
```

ในตัวอย่างนี้เราจะเห็นว่า เราได้เทียบ str1 ที่มีค่า "Ruby!" กับ "ruby!" แล้วได้ค่า false\
เพราะแม้ str1 กับ "ruby!" จะเป็นชนิดข้อมูลเดียวกันและเป็นข้อความที่เหมือนกัน แต่ R กับ r ถือว่าเป็นคนละตัวอักษร\
จึงทำให้ได้ false



## การใช้ <=>

การใช้ <=>  (spaceship) เป็นการเทียบข้อความที่ไม่ได้คืนผลลัพธ์เป็น true หรือ false แต่คืนผลลัพธ์เป็นตัวเลข \
-1 , 0 และ 1 โดย spaceship จะเป็นการเทียบ ลำดับของตัวอักษรทีละตัวอักษรของข้อความ โดยจะเทียบจนกว่าจะเจอ\
ผลลัพธ์ที่แตกต่าง หรือ จนกว่าข้อความนั้นจะสิ้นสุด โดยที่

1 จะเป็นการบอกว่า ข้อความด้านขวา มีค่ามากกว่า ด้านซ้าย

0 จะเป็นการบอกว่า ข้อความด้านซ้าย และ ข้อความด้านขวา เหมือนกันทุกประการ

-1 จะเป็นการบอกว่า ข้อความด้านซ้าย มีค่าน้อยกว่า ด้านขวา\
\
\*\* ค่ามากกว่า / ค่าน้อยกว่าในที่นี้หมายถึง ค่าลำดับของตัวอักษร เช่น A และ B\
เราจะทราบว่า A มาถึงก่อน B \
ถ้าเรานำ A <=> B เราจะได้ -1 เพราะ ลำดับของ A น้อยกว่า ลำดับของ B\
ถ้าเรานำ B <=> A เราจะได้ 1 เพราะ ลำดับของ B มากกว่า ลำดับของ A \






### ตัวอย่างการใช้ <=>&#x20;

```
str1 = "Ant"
str2 = "ant"

puts str1 <=> str2

puts str2 <=> str1

#output :
-1
1
```

กรณีที่ 1 \
ค่าด้านซ้ายคือ "Ant" และ ค่าด้านขวาคือ "ant" เมื่อทำมาเปรียบเทียบโดยการใช้ spaceship จะได้ว่าลำดับของ A มากกว่า ลำดับของ a \
จึงได้ค่าเป็น -1

กรณีที่ 2 \
ค่าด้านซ้ายคือ "ant" และ ค่าด้านขวาคือ "Ant" เมื่อทำมาเปรียบเทียบโดยการใช้ spaceship จะได้ว่าลำดับของ a     น้อยกว่า ลำดับของ A \
จึงได้ค่าเป็น 1

```
str1 = "Meow"

puts str1 <=> "Meow"

#output:
0
```

ในตัวอย่างนี้จะเห็นว่า ได้นำ str1 ที่มีค่า "Meow" มาเทียบกับ "Meow" โดย spaceship จะเทียบทีละตัวอักษรจะเห็นได้ว่า ข้อความ 2 ข้อความนี้เหมือนกันทุกประการ จึงได้ผลลัพธ์เป็น 0

```
str1 = "Cat"
str2 = "Cats"

puts str1 <=> str2

#output:
-1
```

ในตัวอย่างนี้จะเห็นว่า ได้นำ str1 ที่มีค่า "Cat" มาเทียบกับ str2 ที่มีค่า "Cats" โดย spaceship จะเทียบทีละตัวอักษร\
แต่เราจะเห็นได้ว่า str1 สิ้นสุดก่อน จึงทำให้ spaceship ทำการเทียบค่า "" (Empty String) กับ "s" จึงได้ว่า \
ลำดับของ "" น้อยกว่า ลำดับของ "s" จึงได้ผลลัพธ์ -1



## การเปรียบเทียบกับภาษา C , Java และ Python

### การใช้ ==

> C

```
#include <stdio.h>
#include <string.h>

void main() {
    char str1[] = "hello";
    char str2[] = "hello";
    
    if (str1==str2) {
        printf("true")
    } else {
        printf("false");
    }
    
}

#output:
false
```

ในภาษา C เราจะใช้ == กับ String จะเป็นวิธีที่ผิด เพราะว่า โปรแกรมจะเทียบที่อยู่ของหน่วยความจำ ซึ่ง str1 กับ str2 มี\
ที่อยู่ของหน่วยความจำที่ต่างกันจึงได้ค่า false

> Java

```
String str1 = "hello";
String str2 = "hello";
String str3 = new String("hello");
        
System.out.println(str1==str2);

System.out.println(str1==str3);

#output:
true
false
```

ในภาษา java == เป็นการเทียบ ที่อยู่ของหน่วยความจำ ที่เก็บข้อความนั้นไว้เท่านั้น ถ้าเราสร้าง Object String                  ตัวใหม่ขึ้นมา แม้จะมีข้อความ เหมือนกันทุกประการ แต่จะได้ค่า false เพราะ ที่อยู่ของหน่วยความจำ ที่นำมาเทียบกันไม่ใช่ในตำแหน่งเดียวกัน

> Python

```
str1 = "hello"
str2 = "Hello"

print(str1==str2)
print(str1=="hello")

#output:
false
true
```

ในภาษา python สามารถใช้ == เทียบได้เหมือนภาษา ruby



### การใช้ eql?

> C

<pre><code><strong>#include &#x3C;stdio.h>
</strong>#include &#x3C;string.h>

void main() {
    char data1[] = "Hello World";
    char data2[] = "Hello Coder";
    
    int result = memcmp(data1 , data2 , sizeof(data1));
    printf("%d",result);
}

#output:
20
</code></pre>

ในภาษา C ไม่มี eql? แต่มี memcmp ที่มีการทำงานคล้ายๆ spaceship และ eql? memcmp สามารถใช้เปรียบเทียบข้อมูลชนิดใดก็ได้ ไม่จำเป็นต้องเป็น String เท่านั้น&#x20;

> Java

```
int str1 = "123";
String str2 = "123";

System.out.println(str1.equals(str2));
```

ในภาษา Java String มี method ชื่อ equals ซึ่งแตกต่างจาก == ตรงที่ equals จะเป็นการเทียบข้อความจริงๆ\
ไม่ใช่ที่อยู่ของหน่วยความจำ

> Python

```
var1 = "1234"
var2 = 1234

print(var1 == var2)
print(type(var1) == type(var2))

#output:
false
false
```

ในภาษา python ไม่มี eql? แต่ว่า เราสามารถใช้ == เพื่อเทียบค่า และใช้ type เพื่อเปรียบเทียบชนิดข้อมูลได้ เมื่อใช้ 2 อย่างคู่กันจะได้การทำงานแบบ eql? ในภาษา Ruby



### การใช้ <=>&#x20;

> C

```
#include <stdio.h>
#include <string.h>

void main() {
    char str1[] = "hello";
    char str2[] = "hello";

    if (strcmp(str1, str2) == 0) {
        printf("true"); 
    } else {
        printf("false");
    }
}

#output:
true
```

ในภาษา C มีการใช้ strcmp เพื่อนำ String 2 ตัวมาเทียบกันเหมือน spaceship ถ้าได้ค่า 0 แปลว่า ข้อความที่นำมา\
เทียบกัน เหมือนกันทุกประการ

> Java

```
String str1 = "Ant";
String str2 = "Cat";

System.out.println(str1.compareTo(str2));

#output:
-2
```

ในภาษา Java มีการใช้ compareTo ซึ่งทำงานเหมือน spaceship แต่ค่าที่คืนไม่ใช่ 0 , -1 , 1 เหมือน Ruby แต่จะเป็น\
ค่าที่เป็นความต่างระหว่างตัวอักษรที่นำมาเทียบ เช่น A กับ C ต่างกันอยู่ 2 ลำดับ ทำให้ผลลัพธ์ออกมาเป็น -2

> Python

```
animals = ["Cat" , "Ant" , "Bat"]
animals.sort()

print(animals)

#output:
['Ant' , 'Bat' , 'Cat']
```

ในภาษา Python ไม่มีการทำงานที่เหมือน spaceship แต่ว่า เราสามารถใช้ sort ได้เพื่อให้ข้อความใน list ถูกเรียงตามตัวอักษรจาก น้อย > มาก&#x20;



## Reference

> Ruby

Ruby-Doc.org. (ม.ป.ป.). _Class: String (Ruby 3.5.0)_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://docs.ruby-lang.org/en/master/String.html](https://docs.ruby-lang.org/en/master/String.html)

Techotopia. (27 ตุลาคม 2559). _Ruby String Concatenation and Comparison_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://www.techotopia.com/index.php/Ruby\_String\_Concatenation\_and\_Comparison](https://www.techotopia.com/index.php/Ruby_String_Concatenation_and_Comparison)

Stack Overflow. (2552). _What is the Ruby spaceship operator?_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://stackoverflow.com/questions/827649/what-is-the-ruby-spaceship-operator](https://stackoverflow.com/questions/827649/what-is-the-ruby-spaceship-operator)

Khalid, H. (18 เมษายน 2561). _Difference between eql?, ==, equal? in Ruby_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://medium.com/@khalidh64/difference-between-eql-equal-in-ruby-2ffa7f073532](https://medium.com/@khalidh64/difference-between-eql-equal-in-ruby-2ffa7f073532)

GeeksforGeeks. (12 ธันวาคม 2562). _Ruby String eql? Method_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://www.geeksforgeeks.org/ruby/ruby-string-eql-method/](https://www.geeksforgeeks.org/ruby/ruby-string-eql-method/)

> Python

W3Schools. (ม.ป.ป.). _Python list sort() Method_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://www.w3schools.com/python/ref\_list\_sort.asp](https://www.w3schools.com/python/ref_list_sort.asp)

W3Schools. (ม.ป.ป.). _Python type() Function_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://www.w3schools.com/python/ref\_func\_type.asp](https://www.w3schools.com/python/ref_func_type.asp)

> C

GeeksforGeeks. (8 มกราคม 2568). _memcmp() in C_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://www.geeksforgeeks.org/c/memcmp-in-c/](https://www.geeksforgeeks.org/c/memcmp-in-c/)

W3Schools. (ม.ป.ป.). _C String Functions_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://www.w3schools.com/c/ref\_string\_strcmp.php](https://www.w3schools.com/c/ref_string_strcmp.php)

> Java

GeeksforGeeks. (20 มกราคม 2568). _Java String compareTo() Method with Examples_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://www.geeksforgeeks.org/java/java-string-compareto-method-with-examples/](https://www.geeksforgeeks.org/java/java-string-compareto-method-with-examples/)

GeeksforGeeks. (4 มกราคม 2568). _Difference Between == Operator and equals() Method in Java_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://www.geeksforgeeks.org/java/difference-between-and-equals-method-in-java/](https://www.geeksforgeeks.org/java/difference-between-and-equals-method-in-java/)

W3Schools. (ม.ป.ป.). _Java String equals() Method_. สืบค้นเมื่อ 31 สิงหาคม 2568, จาก [https://www.w3schools.com/java/ref\_string\_equals.asp](https://www.w3schools.com/java/ref_string_equals.asp)



## Presentation



## Video
