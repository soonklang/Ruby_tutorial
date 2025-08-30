# *Quoting Ruby Strings*
สตริง (String) ในภาษา Ruby สามารถกำหนดขอบเขตได้ด้วยเครื่องหมาย ' (Single quote) หรือเครื่องหมาย " (Double quote) 

```ruby
word_1 = 'a'
word_2 = "a"

str_1 = 'This is Ruby Language'
str_2 = "This is Ruby Language"
```

โดยทั้งสองเครื่องหมายทำหน้าที่ในการครอบข้อความให้เป็นสตริงเหมือนกันแต่มีวัตถุประสงค์แตกต่างกัน

## Double Quote (")
เครื่องหมาย double quote จะอนุญาตให้เราใช้ escape sequences ได้หรือก็คือตัวอักษรที่ตามหลัง \ (Backslash) จะถูก Ruby ตีความว่าเป็นตัวอักษรตัวนั้นเลย

```ruby
puts "Hello in Ruby\."
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>Hello in Ruby.</code></pre>
</details>

>จากตัวอย่างด้านบนเราจะเห็นได้ว่า \\. จะแสดงผลเป็น . อย่างเดียว

```ruby
puts "This line already taken\nAlright I'll go to the new line"
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>This line already taken
Alright I'll go to the new line</code></pre>
</details>

>ขึ้นบรรทัดใหม่เนื่องจากภายในสตริงมี \\n อยู่

นอกจากนี้แล้วการใช้เครื่องหมาย double quote ยังสามารถทำให้เราแทรกค่าจากตัวแปรหรือค่าอื่นๆเข้ามาในสตริงได้ด้วย

```ruby
name = "Yukihiro Matsumoto"
puts "The creator of Ruby language is #{name}."
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>The creator of Ruby language is Yukihiro Matsumoto.</code></pre>
</details>

```ruby
puts "2 plus 2 is #{4}"
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>2 plus 2 is 4</code></pre>
</details>

```ruby
puts "Ten minus five equal five : #{10-5}"
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>Ten minus five equal five : 5</code></pre>
</details>

## Single Quote (')
ในส่วนของเครื่องหมาย single quote นั้นเราจะไม่สามารถแทรกค่าหรือใช้ escape sequences ได้
> ยกเว้น \\' และ \\\ ที่สามารถใช้ได้

```ruby
puts 'This line already taken\nAlright I\'ll go to the new line'
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>This line already taken\nAlright I'll go to the new line</code></pre>
</details>


```ruby
name = "Yukihiro Matsumoto"
puts 'The creator of Ruby language is #{name}.'
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>The creator of Ruby language is #{name}.</code></pre>
</details>

>จากตัวอย่างด้านบนจะเห็นว่า Ruby แสดงผลตรงส่วนของ #{name} ออกมาแบบนั้นเลยไม่ได้ไปดึงค่าจากตัวแปร name มา

```ruby
puts 'one plus one is equal #{1+1}.'
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>one plus one is equal #{1+1}.</code></pre>
</details>

ตัวอย่างกรณียกเว้นของ \\' และ \\\ 

- กรณี \\'

```ruby
puts '\'First example of exception\''
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>'First example of exception'</code></pre>
</details>

- กรณี \\\

```ruby
puts 'This is backslash \\'
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>This is backslash \</code></pre>
</details>

# เปรียบเทียบภาษา
## Python
ในภาษา Python เครื่องหมาย Single quote และ Double quote จะสามารถใช้ escape sequences ได้เหมือนกัน

```python
print("Hello\nHi")
print('Hi\nHello')
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>Hello
Hi
Hi
Hello</code></pre>
</details>

>จากตัวอย่างด้านบนเราจะสังเกตเห็นว่าผลลัพธ์ที่ได้เหมือนกันต่างจากภาษา Ruby ที่ Single quote จะไม่สามารถใช้ \\n ได้

ภาษา Python สามารถแทรกค่าหรือค่าจากตัวแปลได้เช่นเดียวกันกับภาษา Ruby

```python
name = "Matz"
print(f" Hi {name}")
print(f' Hello {name}')
print(f" one plus one equal {1+1}")
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>Hi Matz
Hello Matz
one plus one equal 2</code></pre>
</details>

>Python ตอนแทรกค่า/ค่าจากตัวแปรจะใช้เป็น print(f"...") ส่วนใน Ruby จะใช้เป็น #{...}

## C
ในภาษา C จะใช้แค่เครื่องหมาย Double quote ในการครอบสตริง

```c
printf("Hello My Name is\nMatz")
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>Hello My Name is
Matz</code></pre>
</details>

## Java
ใน Java เครื่องหมาย Single quote จะใช้สำหรับ char ส่วนเครื่องหมาย Double quote จะใช้สำหรับครอบสตริงแบบเดียวกันกับภาษา Ruby

```java
char word = 'a';
String str = "Bangkok";
```

>ถ้าใช้เครื่องหมาย single quote ครอบตัวอักษรที่มากกว่าหนึ่งตัวโปรแกรมจะเกิด error 

```java
System.out.println("Hi\nWassup");
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>Hi
Wassup</code></pre>
</details>

ใน Java เราสามารถแทรกค่า/ค่าจากตัวแปรได้เช่นเดียวกันกับ Ruby

```java
int x = 10
System.out.println("I have " + x + " Baht in my bank account.");
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>I have 10 Baht in my bank account.</code></pre>
</details>

>หรืออีกวิธีคือการใช้ String.format()

# *Summary*
การครอบข้อความให้เป็นสตริงสามารถใช้ได้ทั้งเครื่องหมาย Single Quote และ Double Quote แต่มีข้อแตกต่างคือ <br>
1. Single quote จะไม่สามารถใช้ escape sequnces แบบ double quote ได้ (ยกเว้น \\' และ \\\) <br>
2. Single quote ไม่สามารถแทรกค่าได้แบบ double quote ได้  

# *Reference*
#### Ruby
- https://www.techotopia.com/index.php/Ruby_Strings_-_Creation_and_Basics#Quoting_Ruby_Strings
- https://docs.ruby-lang.org/en/master/syntax/literals_rdoc.html#label-String+Literals
- https://blog.appsignal.com/2016/12/21/ruby-magic-escaping-in-ruby.html
#### Python
- https://www.geeksforgeeks.org/python/python-escape-characters/
- https://www.geeksforgeeks.org/python/single-and-double-quotes-python/
- https://www.w3schools.com/python/python_strings_escape.asp
#### C
- https://www.geeksforgeeks.org/c/escape-sequence-in-c/
- https://www.geeksforgeeks.org/c/g-fact/
#### Java
- https://stackoverflow.com/questions/439485/is-there-a-difference-between-single-and-double-quotes-in-java
- https://www.geeksforgeeks.org/java/escape-sequences-in-java/
- https://www.geeksforgeeks.org/java/java-program-to-illustrate-string-interpolation/
