# Converting Numbers in Ruby

การแปลงชนิดของข้อมูลของภาษา Ruby จากชนิดหนึ่งไปอีกชนิดได้ จะต้องวใช้ Method และ รับค่าที่จะแปลงเข้าไป
ตัวอย่างต่อไปนี้เราจะมีการเปรียบเทียบกับ Java C Python

โดยการแปลงค่าของแต่ละภาษามีความแตกต่างกันอยู่นิดหน่อย 

ตัวอย่างในการ Converting ในแต่ละภาษา

# Convert to an Integer

Floating Point

```
#ruby
Integer(11.111) // จะได้ค่าเป็น 11

#Java
(int)11.111; // จะได้ค่าเป็น 11

#C
(int)11.111 // จะได้ค่าเป็น 11

#Python
int(11.111) // จะได้ค่าเป็น 11
```

ภาษา C กับ Java โดยการใช้ Type Casting

ภาษา Ruby โดยเรียก Module Kernel ในส่วนของการ Converting

ภาษา Python เรียกใช้ Built-in Function ในการ Converting

___

String

```
#ruby
"123".to_i  // จะได้ค่าเป็น 123 ใช้แต่กับตัวเลขถ้าเป็น Character จะได้ค่าเป็น 0

Integer("123") // จะได้ค่าเป็น 123

#Java
Integer.parseInt("123"); // จะได้ค่าเป็น 123 เป็นการคื่นค่าเป็น Primitive Type
 
Integer.valueOf("123"); // จะได้ค่าเป็น 123 เป็นการคืนค่าเป็น Object
 
#C
atoi("123"); // จะได้ค่าเป็น 123

#Python
int("123") // จะได้ค่าเป็น 123
```

ภาษา C กับ Java เป็นการเรียกใช้ Method

ภาษา Ruby Convert โดยเรียก Module Kernel กับอีกวิธีคือการใช้ Method to_i

ภาษา Python เรียกใช้ Built-in Function

___

Base Number

```
Hexadecimal Number

#ruby
Integer(0xA4F5D) // จะได้ค่าเป็น 675677

#Java
int x = 0xA4F5D; // จะได้ค่าเป็น 675677

#C
int x = 0xA4F5D; // จะได้ค่าเป็น 675677

#Python
int("A4F5D", 16) // จะได้ค่าเป็น 675677

Octal Number

#ruby
Integer(01231) // จะได้ค่าเป็น 665

#Java
int x = 01231; // จะได้ค่าเป็น 665

#C
int x = 01231; // จะได้ค่าเป็น 665

#Python
int("01231", 8) // จะได้ค่าเป็น 665

Binary Number

#ruby
Integer(0b01110101) // จะได้ค่าเป็น 117

#Java
int x = 0b01110101; // จะได้ค่าเป็น 117

#C
int x = 0b01110101; // จะได้ค่าเป็น 117

#Python
int("0b01110101", 2) // จะได้ค่าเป็น 117
```

ภาษา C กับ Java กำหนดค่าโดยตรง

ภาษา Ruby Convert โดยเรียก Module Kernel

ภาษา Python เรียกใช้ Built-in Function

___

Character to the ASCII Character Code

```
#ruby
For Ruby version 1.8 or earlier:
Integer(?e) // จะได้ค่าเป็น 101

For Ruby version 1.9 or later:
"e".ord // จะได้ค่าเป็น 101

#Java
(int)'e'; // จะได้ค่าเป็น 101
 
#C
(int)'e'; // จะได้ค่าเป็น 101

#Python
ord('e') // จะได้ค่าเป็น 101
```

ภาษา C กับ Java โดยการใช้ Type Casting

ภาษา Ruby

 -version 1.8 หรือต่ำกว่า โดยเรียก Module Kernel และทำการ ใส่เครื่องหมาย ? หน้า character เพื่อให้แปลงเป็นรหัส ASCII ของอักษรนั้นทันที

 -version 1.9 หรือใหม่กว่า จะเป็นการเรียกใช้ Method

ภาษา Python เรียกใช้ Built-in Function ในการ Converting

___

# Convert to Floating Point

Integer

```
#ruby
Float(10) // จะได้ค่าเป็น 10.0

#Java
(float)10; // จะได้ค่าเป็น 10.0
 
#C
(float)10; // จะได้ค่าเป็น 10.0

#Python
float(10) // จะได้ค่าเป็น 10.0
```

ภาษา C กับ Java โดยการใช้ Type Casting

ภาษา Ruby โดยเรียก Module Kernel ในส่วนของการ Converting

ภาษา Python เรียกใช้ Built-in Function ในการ Converting

___

String

```
#ruby
"10.09889".to_f  // จะได้ค่าเป็น 10.09889 ใช้แต่กับตัวเลขถ้าเป็น Character จะได้ค่าเป็น 0.0

Float("10.09889") // จะได้ค่าเป็น 10.09889

#Java
Float.parseFloat("10.09889"); // จะได้ค่าเป็น 10.09889 เป็นการคื่นค่าเป็น Primitive Type

Float.valueOf("10.09889"); // จะได้ค่าเป็น 10.09889 เป็นการคืนค่าเป็น Object
 
#C
atof("10.09889"); // จะได้ค่าเป็น 10.09889

#Python
float("10.09889") // จะได้ค่าเป็น 10.09889
```

ภาษา C กับ Java เป็นการเรียกใช้ Method

ภาษา Ruby Convert โดยเรียก Module Kernel กับอีกวิธีคือการใช้ Method to_f

ภาษา Python เรียกใช้ Built-in Function

___

Base Number

```
Hexadecimal Number

#ruby
Float(0xA4F5D) // จะได้ค่าเป็น 675677.0

#Java
(float)0xA4F5D; // จะได้ค่าเป็น 675677.0

#C
(float)0xA4F5D; // จะได้ค่าเป็น 675677.0

#Python
float.fromhex("0xA4F5D") // จะได้ค่าเป็น 675677.0

Octal Number

#ruby
Float(01231) // จะได้ค่าเป็น 665.0

#Java
(float)01231; // จะได้ค่าเป็น 665.0

#C
(float)01231; // จะได้ค่าเป็น 665.0

#Python
float(int("1231", 8)) // จะได้ค่าเป็น 665.0

Binary Number

#ruby
Float(0b01110101) // จะได้ค่าเป็น 117.0

#Java
(float)0b01110101; // จะได้ค่าเป็น 117.0

#C
(float)0b01110101; // จะได้ค่าเป็น 117.0

#Python
float(int("01110101", 2)) // จะได้ค่าเป็น 117.0
```

ภาษา C กับ Java กำหนดค่าโดยตรง

ภาษา Ruby Convert โดยเรียก Module Kernel

ภาษา Python เรียกใช้ Built-in Function โดยแปลงจาก เลขฐานเป็น Integer ก่อนแล้วนำมาแปลงเป็น Float

แต่ Hexadecimal Number ต้องใช้ Method float.fromhex ในการแปลงค่า

___

# Reference

Java 
- Type Casting - https://marcuscode.com/lang/java/type-conversions
- Convert String to an Integer - https://www.geeksforgeeks.org/java/how-to-convert-string-to-int-in-java/
- Convert String to Float - https://www.geeksforgeeks.org/java/how-to-convert-a-string-value-to-float-value-in-java-with-examples/
- Base Number to an Integer - https://beginnersbook.com/2019/04/java-hexadecimal-to-decimal-conversion/

C 
- Type Casting - https://www.geeksforgeeks.org/c/c-typecasting/
- Convert String to an Integer - https://www.geeksforgeeks.org/c/convert-string-to-int-in-c/
- Convert String to Float - https://www.ibm.com/docs/en/i/7.4.0?topic=functions-atof-convert-character-string-float
- Base Number to and Integer - https://www.quora.com/How-do-I-convert-hexadecimal-to-decimal-in-C

Python 
- Built-in Functions - https://docs.python.org/3/library/functions.html
- Convert hex string to float in Python - https://www.geeksforgeeks.org/python/convert-hex-string-to-float-in-python/

Ruby 
- Module Kernel - https://ruby-doc.org/3.4.1/Kernel.html#module-Kernel-label-Converting
- Integer Class - https://www.geeksforgeeks.org/ruby/ruby-integer-class/
