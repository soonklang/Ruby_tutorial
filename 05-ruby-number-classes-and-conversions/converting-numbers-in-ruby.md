# Converting Numbers in Ruby

การแปลงชนิดของข้อมูลของภาษา Ruby จากชนิดหนึ่งไปอีกชนิดได้ จะต้องวใช้ Method และ รับค่าที่จะแปลงเข้าไป
ตัวอย่างต่อไปนี้เราจะมีการเปรียบเทียบกับ Java C Python

โดยการแปลงค่าของแต่ละภาษามีความแตกต่างกันอยู่นิดหน่อย 

ตัวอย่างในการ Converting ในแต่ละภาษา

# Convert to an Integer

Floating Point

```
#ruby
Integer(11.111)
 จะได้ค่าเป็น 11

#Java
(int)11.111;
 จะได้ค่าเป็น 11

#C
(int)11.111
 จะได้ค่าเป็น 11

#Python
int(11.111)
 จะได้ค่าเป็น 11
```

ภาษา C กับ Java โดยการใช้ Type Casting

ภาษา Ruby โดยเรียก Module Kernel ในส่วนของการ Converting

ภาษา Python เรียกใช้ Built-in Function ในการ Converting

___

String

```
#ruby
"123".to_i  // จะได้ค่าเป็น 123

Integer("123") // จะได้ค่าเป็น 123

#Java
String str = "123";
int num = Integer.parseInt(str); // จะได้ค่าเป็น 123 เป็นการคื่นค่าเป็น Primitive Type
 
String str = "123";
Integer num = Integer.valueOf(str); // จะได้ค่าเป็น 123 เป็นการคืนค่าเป็น Object
 
#C
char* str1 = "123";
int num1 = atoi(str1); // จะได้ค่าเป็น 123

#Python
int(10.898)
 จะได้ค่าเป็น 11
```

ภาษา C กับ Java เป็นการเรียกใช้ Method

ภาษา Ruby Convert โดยเรียก Module Kernel กับอีกวิธีคือการใช้ Method to_i

ภาษา Python เรียกใช้ Built-in Function

___

Base Number

```
Hexadecimal Number

#ruby
Integer(0xA4F5D)
 จะได้ค่าเป็น 675677

#Java
int x = 0xA4F5D;
 จะได้ค่าเป็น 675677

#C
int x = 0xA4F5D;
 จะได้ค่าเป็น 675677

#Python
int("A4F5D", 16)
 จะได้ค่าเป็น 675677
```

ภาษา C กับ Java กำหนดค่าโดยตรง

ภาษา Ruby Convert โดยเรียก Module Kernel

ภาษา Python เรียกใช้ Built-in Function

___

# Reference

Java 
- Type Casting - https://marcuscode.com/lang/java/type-conversions
- Convert String to an Integer - https://codegym.cc/th/groups/posts/th.679.withi-plng-string-pen-int-n-java
- Base Number to an Integer - https://beginnersbook.com/2019/04/java-hexadecimal-to-decimal-conversion/

C 
- Type Casting - https://www.geeksforgeeks.org/c/c-typecasting/
- Base Number to and Integer - https://www.quora.com/How-do-I-convert-hexadecimal-to-decimal-in-C

Python 
- Built-in Functions - https://docs.python.org/3/library/functions.html

Ruby 
- Module Kernel - https://ruby-doc.org/3.4.1/Kernel.html#module-Kernel-label-Converting
- Integer Class - https://www.geeksforgeeks.org/ruby/ruby-integer-class/
