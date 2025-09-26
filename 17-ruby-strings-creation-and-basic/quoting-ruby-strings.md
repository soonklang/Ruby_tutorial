# Quoting Ruby Strings

จัดทำโดย 660710599 ตุลธร ศรจังหวัด

## _Quoting Ruby Strings_

Quoting string คือการกำหนดขอบเขตของสตริง (String)

### Double Quote (")

เครื่องหมาย double quote จะอนุญาตให้เราใช้ escape sequences ได้

> ถ้าตัวอักษรที่ตามหลังเครื่องหมาย \ (backslash) ไม่ใช่ escape sequences ภาษา Ruby จะแสดงผลออกมาเป็นตัวอักษรตัวนั้นเลย

```ruby
puts "Hello in Ruby\."
```

<details>

<summary><strong>Output</strong></summary>

```
Hello in Ruby.
```

</details>

> จากตัวอย่างด้านบนเราจะเห็นได้ว่า \\. จะแสดงผลเป็น . อย่างเดียวเนื่องจาก \\. ไม่ใช่ escape sequences

```ruby
puts "This line already taken\nAlright I'll go to the new line"
```

<details>

<summary><strong>Output</strong></summary>

```
This line already taken
Alright I'll go to the new line
```

</details>

> ขึ้นบรรทัดใหม่เนื่องจากภายในสตริงมี \n อยู่ (\n เป็น escape sequences)

นอกจากนี้แล้วการใช้เครื่องหมาย double quote ยังสามารถทำให้เราแทรกค่าหรือค่าจากตัวแปร (interpolation of other values) เข้ามาในสตริงได้ด้วย

```ruby
name = "Yukihiro Matsumoto"
puts "The creator of Ruby language is #{name}."
```

<details>

<summary><strong>Output</strong></summary>

```
The creator of Ruby language is Yukihiro Matsumoto.
```

</details>

```ruby
puts "2 plus 2 is #{4}"
```

<details>

<summary><strong>Output</strong></summary>

```
2 plus 2 is 4
```

</details>

```ruby
puts "Ten minus five equal five : #{10-5}"
```

<details>

<summary><strong>Output</strong></summary>

```
Ten minus five equal five : 5
```

</details>

### Single Quote (')

ในส่วนของเครื่องหมาย single quote นั้นเราจะไม่สามารถแทรกค่าหรือใช้ escape sequences ได้

> ยกเว้น \\' และ \\\ ที่สามารถใช้ได้

```ruby
puts 'This line already taken\nAlright I\'ll go to the new line'
```

<details>

<summary><strong>Output</strong></summary>

```
This line already taken\nAlright I'll go to the new line
```

</details>

```ruby
name = "Yukihiro Matsumoto"
puts 'The creator of Ruby language is #{name}.'
```

<details>

<summary><strong>Output</strong></summary>

```
The creator of Ruby language is #{name}.
```

</details>

> จากตัวอย่างด้านบนจะเห็นว่า Ruby แสดงผลตรงส่วนของ #{name} ออกมาแบบนั้นเลยไม่ได้ไปดึงค่าจากตัวแปร name มาใส่ในสตริง

```ruby
puts 'one plus one is equal #{1+1}.'
```

<details>

<summary><strong>Output</strong></summary>

```
one plus one is equal #{1+1}.
```

</details>

ตัวอย่างกรณียกเว้นของ \\' และ \\\\

* กรณี \\'

```ruby
puts '\'First example of exception\''
```

<details>

<summary><strong>Output</strong></summary>

```
'First example of exception'
```

</details>

* กรณี \\\\

```ruby
puts 'This is backslash \\'
```

<details>

<summary><strong>Output</strong></summary>

```
This is backslash \
```

</details>

### Alternative Quotes

อีกหนึ่งวิธีในการครอบสตริงคือ alternative quotes โดยวิธีนี้จะคล้ายกับการใช้เครื่องหมาย ' และ " แต่จะมีข้อแตกต่างกันเล็กน้อย\
%q (Alternative single quote) ทำงานเหมือนกับเครื่อง Single quote แต่จะเกิดการ escape sequences เฉพาะ \ ตามด้วย delimiters ที่ใช้\
%Q หรือ % (Alternative double quote) และ % ทำงานเหมือนกับเครื่องหมาย Double quote สามารถแทรกค่าและใช้ escape sequences ได้

```ruby
str = "Hello Ruby"
puts %Q[#{str}]
puts %[#{str}]
puts %q[#{str}\nHi Ruby]
```

<details>

<summary><strong>Output</strong></summary>

```
Hello Ruby
Hello Ruby
#{str}\nHi Ruby
```

</details>

สิ่งที่แตกต่างจากเครื่องหมาย single quote และ double quote คือ alternative quote เราสามารถเปลี่ยนตัว delimiter ได้ทำให้อ่านได้ง่ายขึ้นเวลาที่ต้องการจะใช้ ' หรือ " ภายในสตริง

```ruby
puts 'I\'m from Thailand.'
puts %q!I'm from Thailand\.!
puts %q!I'm from Thailand\!!
```

<details>

<summary><strong>Output</strong></summary>

```
I'm from Thailand.
I'm from Thailand\.
I'm from Thailand!
```

</details>

> จากตัวอย่างด้านบนจะเห็นได้ว่า \\. ไม่เกิด escape sequences เนื่องจากตัว delimiter ที่ใช้คือเครื่องหมาย !\
> ต่างจาก single quote ที่จะเกิด escape sequences แค่เฉพาะกับ \\\ และ \\'

```ruby
puts %Q^Hi I\'m Zen\.^
puts %^Hi I\'m Zen\.^
```

<details>

<summary><strong>Output</strong></summary>

```
Hi I'm Zen.
Hi I'm Zen.
```

</details>

## _เปรียบเทียบภาษา_

### Python

ในภาษา Python เครื่องหมาย Single quote และ Double quote จะสามารถใช้ escape sequences ได้เหมือนกัน

```python
print("Hello\nHi")
print('Hi\nHello')
```

<details>

<summary><strong>Output</strong></summary>

```
Hello
Hi
Hi
Hello
```

</details>

> จากตัวอย่างด้านบนเราจะสังเกตเห็นว่าผลลัพธ์ที่ได้เหมือนกันต่างจากภาษา Ruby ที่ Single quote จะไม่สามารถใช้ \n ได้

ภาษา Python สามารถแทรกค่าหรือค่าจากตัวแปลได้เช่นเดียวกันกับภาษา Ruby

```python
name = "Matz"
print(f" Hi {name}")
print(f' Hello {name}')
print(f" one plus one equal {1+1}")
```

<details>

<summary><strong>Output</strong></summary>

```
Hi Matz
Hello Matz
one plus one equal 2
```

</details>

> Python ตอนแทรกค่า/ค่าจากตัวแปรจะใช้เป็น print(f"...") ส่วนใน Ruby จะใช้เป็น #{...}

### C

ในภาษา C จะใช้แค่เครื่องหมาย Double quote ในการครอบสตริงส่วนเครื่องหมาย Single quote จะใช้ในการครอบตัวอักษร (char)

```c
printf("Hello My Name is\nMatz")
```

<details>

<summary><strong>Output</strong></summary>

```
Hello My Name is
Matz
```

</details>

> ภาษา C ไม่สามารถทำการแทรกค่าลงสตริงได้ (String interpolation)

### Java

ใน Java เครื่องหมาย Single quote จะใช้สำหรับครอบตัวอักษร (char) ส่วนเครื่องหมาย Double quote จะใช้สำหรับครอบสตริงแบบเดียวกันกับภาษา Ruby

```java
char word = 'a';
String str = "Bangkok";
```

> ถ้าใช้เครื่องหมาย single quote ครอบตัวอักษรที่มากกว่าหนึ่งตัวโปรแกรมจะเกิด error

```java
System.out.println("Hi\nWassup");
```

<details>

<summary><strong>Output</strong></summary>

```
Hi
Wassup
```

</details>

ใน Java เราสามารถแทรกค่า/ค่าจากตัวแปรได้เช่นเดียวกันกับ Ruby

```java
int x = 10
System.out.println("I have " + x + " Baht in my bank account.");
```

<details>

<summary><strong>Output</strong></summary>

```
I have 10 Baht in my bank account.
```

</details>

> หรืออีกวิธีคือการใช้ String.format() และอื่นๆ

## _Summary_

การครอบข้อความให้เป็นสตริงสามารถใช้ได้ทั้งเครื่องหมาย Single Quote และ Double Quote แต่มีข้อแตกต่างคือ


1. Single quote จะไม่สามารถใช้ escape sequnces แบบ double quote ได้ (ยกเว้น \\' และ \\\\)

2. Double quote สามารถแทรกค่าได้และใช้ escape sequences ได้

Aternative quote ทำงานเหมือนเครื่องหมาย single quote และ double quote ต่างตรงที่ alternative quote สามารถเปลี่ยนตัว delimiters ได้

## _Reference_

**Ruby**

* Smyth, N. (2016, October 27). Quoting Ruby Strings. Techotopia. Retrieved August 30,2025, From\
  https://www.techotopia.com/index.php/Ruby\_Strings\_-\_Creation\_and\_Basics#Quoting\_Ruby\_Strings
* Ruby Core Team. (n.d.). Literals: String Literals. Ruby documentation. Retrieved August 30, 2025, From\
  https://docs.ruby-lang.org/en/master/syntax/literals\_rdoc.html#label-String+Literals
* de Bruijn, T. (2016, December 21). Escaping characters in Ruby. Appsignal. Retrieved August 30, 2025, From\
  https://blog.appsignal.com/2016/12/21/ruby-magic-escaping-in-ruby.html
* Wikibooks. (2022, August 22). Ruby Programming/Alternate quotes. Retrieved August 31, 2025, From\
  https://en.wikibooks.org/wiki/Ruby\_Programming/Alternate\_quotes
* Codecademy. (2013). Single and Double Quotation Marks in Ruby and Escaping. Retrieved August 31, 2025, From\
  https://www.codecademy.com/forum\_questions/51d1f89d8c1cccd6ab0004f4

**Python**

* GeeksforGeeks. (2025, April 28). Python Escape Characters. GeeksforGeeks. Retrieved August 30, 2025, From\
  https://www.geeksforgeeks.org/python/python-escape-characters/
* GeeksforGeeks. (2023, Mar 31). Single and Double Quotes | Python. GeeksforGeeks. Retrieved August 30, 2025, From\
  https://www.geeksforgeeks.org/python/single-and-double-quotes-python/
* W3Schools. (n.d.). Python - Escape Characters. W3School. W3Schools. Retrieved August 30, 2025, From\
  https://www.w3schools.com/python/python\_strings\_escape.asp

**C**

* GeeksforGeeks. (2025, July 23). Escape Sequence in C. GeeksforGeeks. Retrieved August 30, 2025, From\
  https://www.geeksforgeeks.org/c/escape-sequence-in-c/
* Wikipedia. (2025 August 28). String interpolation. Wikipedia. Retrieved August 30, 2025, From\
  https://en.wikipedia.org/wiki/String\_interpolation

**Java**

* Stack Overflow. (2009, January 13). Is there a difference between single and double quotes in Java? . Stack Overflow. Retrieved August 30, 2025, From\
  https://stackoverflow.com/questions/439485/is-there-a-difference-between-single-and-double-quotes-in-java
* GeeksforGeeks. (2023, November 1). Escape Sequences in Java. GeeksforGeeks. Retrieved August 30, 2025, From\
  https://www.geeksforgeeks.org/java/escape-sequences-in-java/
* GeeksforGeeks. (2025, July 23). String Interpolation in Java. GeeksforGeeks. Retrieved August 30, 2025, From\
  https://www.geeksforgeeks.org/java/java-program-to-illustrate-string-interpolation/

## _Presentation_
[Quoting String.pdf](https://github.com/user-attachments/files/22564342/Quoting.String.pdf)

## _Video_
https://youtu.be/8E-nh5k_sVo
