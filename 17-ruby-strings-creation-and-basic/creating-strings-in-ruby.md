#  Creating Strings in Ruby
What is String in Ruby?
>String ใน Ruby นั้นถูกจัดเก็บโดยใช้ object นอกจากจะใช้เก็บสตริงแล้วยังมี method อีกมากที่ใช้จัดการกับ String ซึ่งมีลำดับอักขระหนึ่งตัวหรือมากกว่านั้น จะเป็นตัวเลข ตัวอักษร หรือสัญลักษณ์ก็ได้
> 
## วิธีสร้าง String ใหม่ใช้วิธี new method ของ String class:
 ```ruby
myString = String.new
=> ""
```
>จากตัวอย่างนี้ได้สร้างสตริงว่างเปล่าขึ้นมา
## วิธีสร้างเริ่มต้นโดยการส่ง String เป็น argument ไปยัง new method:
 ```ruby
myString = String.new("This is my string. Get your own string")
str = String.new('Another string.')
```
>จากตัวอย่างข้างต้นเป็นการสร้าง String ว่าง
## วิธีสร้างโดยเลือกใช้ method ที่เตรียมไว้โดย Kernel:
 ```ruby
myString = String("This is also my string")
```
## หรือวิธีที่ง่ายที่สุดในการสร้างคือกำหนด String ให้กับชื่อตัวแปร :
 ```ruby
myString = "This is also my string"
myString_1 = 'This is also my string'
```
>เมื่อกำหนด Ruby จะจัดการส่วนที่เหลือให้เอง ซึ่งที่กำหนดที่ใช้ทั้ง " " และ ' ' นั้นทำงานได้เหมือนกัน
#  เปรียบเทียบกับภาษาอื่น
## Python❗
>Python ไม่มี new String()  แต่ว่า String นั้นจะถูกสร้างขึ้นโดย literal โดยตรง หรือโดยฟังชันก์ str()
### ตัวอย่างการใช้ literal โดยตรง
```python
string1 = "Python programming"
string2 = 'Python programming'
```
>ใช้งานได้ทั้ง " " และ ' '
### ตัวอย่างการใช้ str()
>Python ใช้ str() เมื่อต้องแปลงหรือสร้างวัตถุอื่นๆ
```python
print(str('Adam'))
```
<details close>
   <summary><b>output</b></summary>
 <pre>
  Adam
 </pre>
</details>

```python
name = str('Luke')
print(name)
```
<details close>
   <summary><b>output</b></summary>
 <pre>
Luke
 </pre>
</details>

```python
age = str(40)
print(age)
```
<details close>
   <summary><b>output</b></summary>
 <pre>
40
 </pre>
</details>

## Java❗
>มีอยู่２วิธีหลักในการสร้าง String คือใช้ String literal และ new String (constructor)
### ตัวอย่างการใช้ String literal
```java
String greeting = "Hello"
System.out.println(greeting);
```
<details close>
   <summary><b>output</b></summary>
 <pre>
  Hello
 </pre>
</details>

>การสร้าง String แบบ literal ของ Java จะใช้ได้เพียง " "
### ตัวอย่างการใช้ new String (constructor)
```java
String str = new String("abc");
```
>จะสร้าง object  ใหม่เสมอ ช้ากว่า literal ส่วนมากไม่ใช้ หากไม่จำเป็น

### หากต้องการสร้าง String โดย string() ที่เป็น method ของ Kernel
```java
String myString = String.valueOf("This is also my string");
```
>String.valueOf() สามารถรับ object, primitive หรือ char array ได้แล้วแปลงเป็น String ได้เหมือน Ruby String()

## C❗
>มีความแตกต่างตรงที่ภาษา C ไม่มีชนิดข้อมูล String แต่จะถูกนำไปใช้เป็น arrays ของ char
>arrays ของ char จะลงท้ายด้วยอักขระพิเศษ '\0' (อักขระ null) ใช้เป็นจุดสิ้นสุดของ String
### อาร์เรย์ของ `char` แบบ string literal
```c
char c[] = "c string";
```
>C ใช้ char array เพื่อเก็บ string แบบ null-terminated โดย C จะใส่  '\0'  ให้เองที่ท้ายเสมอ

### ตัวอย่างสร้างจากลิสต์ของตัวอักษร + null
```c
char greeting[] = {'H','e','l','l','o','\0'};
```

# *Reference*
#### Ruby
- W3schools.io. (n.d.). *Ruby Strings*. W3schools.io. Retrieved September 1, 2025, from<br>
https://www.w3schools.io/ruby-strings/
- Ruby-lang.org. (n.d.). *String — Ruby master*. Ruby-lang.org. Retrieved September 1, 2025, from<br>
https://docs.ruby-lang.org/en/master/String.html
- GeeksforGeeks. (2024, May 20). *Ruby | String Basics*. GeeksforGeeks. Retrieved September 1, 2025, from<br>
https://www.geeksforgeeks.org/ruby/ruby-string-basics/
- Smyth, N. (2016, November 2). *Ruby Strings - Creation and Basics*. Techotopia. Retrieved September 1, 2025, from<br>
https://www.techotopia.com/index.php/Ruby_Strings_-_Creation_and_Basics

#### Python
- Programiz. (n.d.). _Python String (Strings in Python with Examples)_. Programiz. Retrieved September 1, 2025, from <br>
https://www.programiz.com/python-programming/string
- Programiz. (n.d.). Python str(). Programiz. Retrieved September 1, 2025, from <br>
https://www.programiz.com/python-programming/methods/built-in/str
- Python Software Foundation. (n.d.). string — Common string operations. Python 3 documentation. Retrieved September 1, 2025, from<br>
https://docs.python.org/3/library/string.html
- Google for Education. (n.d.). Python Strings. Google Developers. Retrieved September 1, 2025, from<br>
https://developers.google.com/edu/python/strings?hl=th

#### Java
- W3Schools. (n.d.). Java Strings. W3Schools. Retrieved September 1, 2025, from<br>
https://www.w3schools.com/java/java_strings.asp
- Oracle. (n.d.). Strings (The Java™ Tutorials – Learning the Java Language). Retrieved September 1, 2025, from<br>
https://docs.oracle.com/javase/tutorial/java/data/strings.html
- Stack Overflow. (2010, July 21). Difference between String object and String literal [online forum]. Retrieved September 1, 2025, from<br>
https://stackoverflow.com/questions/3297867/difference-between-string-object-and-string-litera
- Baeldung. (n.d.). Guide to Java String Pool. Baeldung. Retrieved September 1, 2025, from<br>
https://www.baeldung.com/java-string-pool

#### C
- W3Schools. (n.d.). _C Strings_. W3Schools. Retrieved September 1, 2025, from <br>[https://www.w3schools.com/c/c_strings.php](https://www.w3schools.com/c/c_strings.php?utm_source=chatgpt.com)
- TutorialsPoint. (n.d.). _Strings in C_. TutorialsPoint. Retrieved September 1, 2025, from <br>[https://www.tutorialspoint.com/cprogramming/c_strings.htm](https://www.tutorialspoint.com/cprogramming/c_strings.htm?utm_source=chatgpt.com)
- Programiz. (n.d.). _C Programming Strings_. Programiz. Retrieved September 1, 2025, from <br>[https://www.programiz.com/c-programming/c-strings](https://www.programiz.com/c-programming/c-strings?utm_source=chatgpt.com)
- GeeksforGeeks. (2025, July 25). _Strings in C_. GeeksforGeeks. Retrieved September 1, 2025, from<br> [https://www.geeksforgeeks.org/c/strings-in-c/](https://www.geeksforgeeks.org/c/strings-in-c/?utm_source=chatgpt.com)

# *Presentation*
[Creating Strings in Ruby](https://github.com/user-attachments/files/22299095/660710598.pdf.pdf)

# *Video*
