# Ruby Unless and Until

### Until

> จะทำงานจนกว่าเงื่อนไขเป็นจริง กล่าวคือมันจะทำงานในขณะที่เงื่อนไขเป็นเท็จนั่นเอง ซึ่งตรงกับข้ามกับคำสั่ง while loop ซึ่งทำงานในขณะที่เงื่อนไขเป็นจริง นี่เป็นรูปแบบการใช้งาน


**Basic Syntax**

``` ruby
until condition [do]
    code
end
```

**Example Code**

``` ruby
i = 10
until i == 5 do
    puts i
    i = i - 1
end
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>10
9
8
7
6
</code></pre>
</details>

>ตัวอย่างนี้ เป็นโปรแกรมนับถอยหลังโดยเริ่มจาก 10 ในแต่ละรอบของการทำงานโปรแกรมจะตรวจสอบเงื่อนไข i == 0 และทำงานในลูปถ้าหากเงื่อนไขเป็นเท็จ ในแต่ละรอบของการทำงานใน loop เราได้แสดงค่าในตัวแปรออกมา และลดค่าในตัวแปรลงหนึ่งค่าด้วยคำสั่ง

**Modifier Form**
``` ruby
code until conditional
```

**or**

``` ruby
begin
   code
end until conditional
```
**Example Code**

``` ruby

```

### เปรียบเทียบภาษา Ruby กับภาษา Java , C , Python

**Ruby Example Code**
``` ruby
var = 7
until var == 11 do
  puts var * 10
  var = var + 1
end
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>70
80
90
100
</code></pre>
</details>

**Java Example Code**
``` Java

```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>70
80
90
100
</code></pre>
</details>

**C Example Code**
``` C

```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>70
80
90
100
</code></pre>
</details>

**Python Example Code**
``` Python

```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>70
80
90
100
</code></pre>
</details>

------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Unless

> เงื่อนไขให้โปรแกรมทำงานในบล็อคของคำสั่งยกเว้นแต่ว่าเงื่อนไขจะเป็นจริง หรือกล่าวอีกนัยหนึ่งโปรแกรมจะทำงานเมื่อเงื่อนไขเป็นเท็จนั่นเอง ซึ่งมันเป็นคำสั่งที่ตรงข้ามกับคำสั่ง if ที่จะทำงานเมื่อเงื่อนไขเป็นจริง มาดูตัวอย่างการใช้งาน

**Basic Syntax**

``` ruby
unless conditional [then]
   code
[else
   code ]
end
```

**Example Code**

``` ruby
x = 1
y = 3
unless x == y
    puts "x is not equal to y"
else
    puts "x equal to y"
end
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>x is not equal to y
</code></pre>
</details>

ในตัวอย่างนี้ประกาศสองตัวแปรคือ x และ y และกำหนดค่าที่ไม่เท่ากันให้กับตัวแปร ซึ่งในโปรแกรมนั้นมีหมายความว่าให้แสดงผล ยกเว้นแต่ว่า x มีค่าเท่ากับ y และเนื่องจาก x == y นั้นไม่เป็นจริง ดังนั้นโปรแกรมทำงานในบล็อคของคำสั่ง unless

เราสามารถใช้งานคำสั่ง else ร่วมกับคำสั่ง unless ได้ ซึ่งโปรแกรมจะทำงานในบล็อคคำสั่ง else ถ้าหากเงื่อนไขเป็นจริง แต่โปรดจำไว้ว่าคุณไม่สามารถใช้งานคำสั่ง elsif ร่วมกับคำสั่ง unless ได้

**Modifier Form**

``` ruby
code unless conditional
```

**Example Code**

``` ruby

```

### เปรียบเทียบภาษา Ruby กับภาษา Java , C , Python


**Ruby Example Code**
``` ruby
x = 1 
unless x>=2
   puts "x is less than 2"
 else
   puts "x is greater than 2"
end
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>x is less than 2
</code></pre>
</details>

**Java Example Code**
``` Java

```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>x is less than 2
</code></pre>
</details>

**C Example Code**
``` C

```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>x is less than 2
</code></pre>
</details>

**Python Example Code**
``` Python

```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>x is less than 2
</code></pre>
</details>

## References

* Smyth, N. (2016, October 27). Ruby while and until loops. Techotopia. Retrieved September 2, 2025, from
  https://www.techotopia.com/index.php/Ruby_While_and_Until_Loops

* Ruby Core Team. (n.d.). Control expressions: unless expression. Ruby documentation. Retrieved September 2, 2025, from
  https://docs.ruby-lang.org/en/master/syntax/control_expressions_rdoc.html#label-unless+Expression

* Ruby Core Team. (n.d.). Control expressions: until loop. Ruby documentation. Retrieved September 2, 2025, from
  https://docs.ruby-lang.org/en/master/syntax/control_expressions_rdoc.html#label-until+Loop

* Cooper, P. (2016). Beginning Ruby: From novice to professional (3rd ed.), Apress. from
  https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Beginning%20Ruby%20-%20From%20Novice%20to%20Professional%20-%20Third%20Edition.pdf

* Tutorialspoint. (n.d.). Ruby - loops. Tutorialspoint. Retrieved September 2, 2025, from
  https://www.tutorialspoint.com/ruby/ruby_loops.htm

* Tutorialspoint. (n.d.). Ruby - if...else,case,unless. Tutorialspoint. Retrieved September 2, 2025, from
  https://www.tutorialspoint.com/ruby/ruby_if_else.htm

* GeeksforGeeks. (2025, 11 Jul). Ruby loops (for, while, do while, until). GeeksforGeeks. Retrieved September 2, 2025, from
  https://www.geeksforgeeks.org/ruby/ruby-loops-for-while-do-while-until/

* GeeksforGeeks. (2018, 26 Oct). Ruby unless Statement and unless Modifier. GeeksforGeeks. Retrieved September 2, 2025, from
  https://www.geeksforgeeks.org/ruby/ruby-unless-statement-and-unless-modifier/

*
*
*
