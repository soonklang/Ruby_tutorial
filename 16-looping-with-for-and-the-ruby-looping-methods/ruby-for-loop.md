# Ruby for loop

## นิยามของ for loop

 for loop คือคำสั่งควบคุมการทำงานของโปรแกรมที่ช่วยให้สามารถทำงานซ้ำ ๆ ได้ภายใต้เงื่อนไขที่ผู้เขียนโปรแกรมกำหนด ประโยชน์ที่เราได้จากการใช้ for loop ได้แก่  ทำงานซ้ำตามจำนวนที่แน่นอน เช่น พิมพ์ข้อความ 10 ครั้ง ลดความซ้ำซ้อนของโค้ด ไม่ต้องเขียนคำสั่งเดิม ๆ หลายบรรทัด, แก้ไขหรืออัปเดตเงื่อนไขได้เพียงจุดเดียว ทำให้โค้ดอ่านง่าย 

## for loop ในภาษา Ruby

for loop ของ Ruby มักถูกใช้งานเมื่อต้องการให้ชุดคำสั่งทำงานซ้ำ โดยสามารถวนผ่านคอลเลกชันของข้อมูล เช่น อาเรย์ (Array) หรือ เรนจ์ (Range) ได้โดยตรงโดย
ในการวนซ้ำ จะมี ตัววน (iterator) ทำหน้าที่เข้าถึงค่าทีละตัว เพื่อนำค่าไปใช้ในการคำนวณ การนับ การอัปเดตค่า หรือการประมวลผลอื่น ๆ ตามที่กำหนด

## Basic Syntax
``` ruby
for variable_name in expression 

   # actions

end
```
>
>+ for :คือคีย์เวิร์ดที่ใช้เพื่อเริ่มต้นการทำงานของลูป
>
>+ variable_name :คือตัวแปรที่ทำหน้าที่เป็น ตัววน (iterator) โดยเป็นตัวแปรที่ทำหน้าที่ในการเข้าถึงข้อมูลแต่ละตัว
>
>+ in :คือคีย์เวิร์ดที่บอกว่าเราจะวนซ้ำแบบไหนเช่น ช่วง(Range)  หรือ อาเรย์(Array)  เป็นต้น
>
>+ expression :คือนิพจน์ที่จะกำหนดชนิดข้อมูลที่เราจะนำมาวน เช่น 1..5 หรือ [10, 20, 30] 
>
>+ end: ใช้เพื่อปิดบล็อกคำสั่งที่อยู่ภายในลูป
>

<br>

``` ruby
for i in 1..5
    puts i
end
```
<details>
<summary>Output</summary>
<pre>
1<br>2<br>3<br>4<br>5
</pre>
</details>

<br>

>
>ซึ่งการใช้ Range นั้นจะมีการใช้งาน 2 แบบคือ
>
>1. การที่ใช้ 2 จุดคือ 1..5 => เราจะได้ตัวเลขมา 5 ตัวคือ 1 2 3 4 5 
>
>2. การที่ใช้ 3 จุดคือ 1...5 => จะได้ตัวเลขมาคือ 1 2 3 4
>

<br>

# ตัวอย่างการใช้งาน  for loop


## Range

 ``` ruby
for i in 1...10
    print "#{i} "
end
```
<details>
<summary>Output</summary>
<pre>
1 2 3 4 5 6 7 8 9
</pre>
</details>



## Array
 ``` ruby
languages = ["Ruby","Python", "Java", "C"]

for i in languages 
    puts i
end
```
<details>
<summary>Output</summary>
<pre>
Ruby<br>Python<br>Java<br>C
</pre>
</details>



## Hash
 ``` ruby
movies = {"Star Wars": 1, "Avatar": 2, "Harry Potter": 3}

for k, v in movies
    puts "#{k} => #{v}"
end
```
<details>
<summary>Output</summary>
<pre>
Star Wars => 1<br>Avatar => 2<br>Harry Potter => 3
</pre>
</details>

<br>

# .each Method ในภาษา Ruby

ในภาษา Ruby คำสั่ง  each ใช้สำหรับวนลูปผ่านทุกองค์ประกอบในอาเรย์หรือแฮช โดยไม่จำเป็นต้องใช้ดัชนี (index) เพื่อเข้าถึงค่าในแต่ละรอบของการวนลูปเพื่อความสะดวกสบายและทำให้โค้ดมีความสะอาดตามากขึ้น


## Basic Syntax

``` ruby
collection.each do |variable|
  # actions
end
---------------------------------------------------------------------------
collection.each { |element| action }
```

>ทั้งสองมีอันแตกต่างกันคือด้านบนอันแรกจะเป็น  การเขียนแบบเต็มส่วนอันที่สองจะเป็นการเขียนแบบ Short-hand
> - collection :คือคอลเลกชันข้อมูล เช่น Array, Range, Hash หรือ object ที่ Enumerable รองรับ
> - .each : คือเมธอดที่ใช้วนซ้ำผ่านสมาชิกใน collection ทีละตัว
> - do : ใช้กำหนดบล็อกของโค้ดที่จะรันซ้ำ ไม่จำเป็นต้องมีก็ได้ถ้าเขียนเป็น {...} แทน
> - variable : คือตัวแปรที่ใช้แทนค่าของสมาชิกแต่ละตัวในคอลเลกชัน
> - end : ใช้ปิดบล๊อกคำสั่ง .each ไม่จำเป็นต้องมีก็ได้ถ้าเขียนเป็น {...} แทน
>



# ตัวอย่างการใช้งาน  .each method


## Range

 ``` ruby
(1...10).each do |i|
  print "#{i} "
end

```
<details>
<summary>Output</summary>
<pre>
1 2 3 4 5 6 7 8 9
</pre>
</details>



## Array
 ``` ruby
languages = ["Ruby","Python", "Java", "C"]

languages.each do |lang|
  puts lang
end

```
<details>
<summary>Output</summary>
<pre>
Ruby<br>Python<br>Java<br>C
</pre>
</details>



## Hash
 ``` ruby
movies = {"Star Wars": 1, "Avatar": 2, "Harry Potter": 3}

movies.each do |k, v|
  puts "#{k} => #{v}"
end

```
<details>
<summary>Output</summary>
<pre>
Star Wars => 1<br>Avatar => 2<br>Harry Potter => 3
</pre>
</details>



# การเปรียบเทียบ Ruby กับภาษาชนิดอื่น

## C
``` c
int main() {
int i; 
for (i = 1; i < 5; i++) {
        printf("%d\n", i);
    }
return 0;
}
```
<details>
<summary>Output</summary>
<pre>
1<br>2<br>3<br>4
</pre>
</details>


## JAVA (for loop)
``` java
class Main {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            System.out.println(i);
        }
    }
}
```
<details>
<summary>Output</summary>
<pre>
1<br>2<br>3<br>4
</pre>
</details>


## JAVA (for each loop)
``` java
class Main {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};

        for (int num : numbers) {
            System.out.println(num);
        }
    }
}

```
<details>
<summary>Output</summary>
<pre>
1<br>2<br>3<br>4<br>5
</pre>
</details>

## PYTHON
``` python
for i in range(1, 5):   
   print(i)
```
<details>
<summary>Output</summary>
<pre>
1<br>2<br>3<br>4
</pre>
</details>

<br>

# สรุปความแตกต่าง

## C  และ java for loop กับ for loop ของ Ruby
#### โดยจากการที่ได้นำโค้ดด้านบนนำมาเปรียบเทียบแล้วเราสามารถสรุปได้ว่า ภาษา C และ java จะมีความคล้ายหรือใกล้เคียงกันซึ่งภาษาทั้งสองนี้จะไม่มี คำสั่ง end อยู่บรรทัดสุดท้ายเพื่อเป็นการบอกว่าจบ loop เหมือนกับ Ruby แต่จะเป็นการใช้ {} (Braces)  แทนเพื่อเป็นจำกัดขอบเขตของ Block และยังมีส่วนที่ต่างอีกอย่างคือตรงภาษา C และ java จะมี  ; (semi colon)  คั่นตรงกลางระหว่าง expression รวมถึง ในภาษา C และ java จะมีการกำหนดตัวแปรเพื่อเป็นการนับเพือให้ครบจำนวนรอบและยังมีอีกข้อ คือทั้งสองภาษานี้จะมี ; (semi colon) ตามหลังเสมอ ส่วนตรงอื่นๆจะมีความคล้ายกันอยู่


## python for loop กับ for loop ของ Ruby
#### ส่วนภาษา python นั้นจะมีความแตกต่างจากภาษา Ruby คือมีการใช้ : (colon) มาอยู่หลัง  for และยังมีการ Tab ด้านหน้าเพื่อเป็นการกำหนดว่าอยู๋ใน loop และยังไม่มี end ต่อท้ายเหมือนกับ Ruby ส่วนอื่นๆนั้นจะมีความคล้ายคลึงกันกับ ภาษา Ruby เลย
  

 ## java for each กับ .each ของ  Ruby
 #### ทั้งสองภาษามีความคล้ายกันตรงที่ไม่ต้องมีตัวแปร index หรือตัวนับ loop โดยจะ  เน้นที่การวนผ่านค่าที่อยู่ใน collection โดยตรง ทำให้โค้ดอ่านง่ายและกระชับกว่า for loop แบบปกติ
<br>

# แหล่งอ้างอิง

## Ruby 
- Technopia. (27 ตุลาคม 2016). Looping with for and the Ruby Looping Methods. สืบค้นวันที่ 2 กันยายน 2025, จาก https://www.techotopia.com/index.php/Looping_with_for_and_the_Ruby_Looping_Methods  
- GeeksforGeeks. (11 กรกฎาคม 2025). Ruby | Loops (for, while, do..while, until). สืบค้นวันที่ 2 กันยายน 2025, จาก https://www.geeksforgeeks.org/ruby/ruby-loops-for-while-do-while-until/#2-for-loop
- EXPERT-PROGRAMMING-TUTOR. (ไม่มีวันที่). Ruby | Loops การใช้งาน For Each ในภาษา Ruby แบบง่ายๆ. สืบค้นวันที่ 2 กันยายน 2025, จาก https://expert-programming-tutor.com/tutorial/article/KC0330093004_for_each_in_Ruby.php
- carmatec. (27 สิงหาคม 2025). How to Use the Ruby Each Method (With Examples). สืบค้นวันที่ 2 กันยายน 2025, จาก https://www.carmatec.com/blog/how-to-use-the-ruby-each-method-with-examples/

## C
- TutorialsPoint. (ไม่มีวันที่). C - for loop statement. สืบค้นวันที่ 2 กันยายน 2025, จาก https://www.tutorialspoint.com/cprogramming/c_for_loop.htm  
- Programiz. (ไม่มีวันที่). C for Loop. สืบค้นวันที่ 2 กันยายน 2025, จาก https://www.programiz.com/c-programming/c-for-loop  
- W3Schools. (ไม่มีวันที่). C for Loop. สืบค้นวันที่ 2 กันยายน 2025, จาก https://www.w3schools.com/c/c_for_loop.php 


## Java
- W3Schools. (ไม่มีวันที่). Java for Loop. สืบค้นวันที่ 2 กันยายน 2025, จาก https://www.w3schools.com/java/java_for_loop.asp  
- TutorialsPoint. (ไม่มีวันที่). Java - for Loop. สืบค้นวันที่ 2 กันยายน 2025, 
จาก https://www.tutorialspoint.com/java/java_for_loop.htm 
- GeeksforGeeks. (14 เมษายน 2025). For-Each Loop in Java. สืบค้นวันที่ 2 กันยายน 2025, จาก https://www.geeksforgeeks.org/java/for-each-loop-in-java/

## Python
- Python Documentation. (ไม่มีวันที่). The for statement. สืบค้นวันที่ 2 กันยายน 2025, จาก https://docs.python.org/3/tutorial/controlflow.html#for-statements  
- W3Schools. (ไม่มีวันที่). Python for Loops. สืบค้นวันที่ 2 กันยายน 2025, จาก https://www.w3schools.com/python/python_for_loops.asp  
- GeeksforGeeks. (30 กรกฎาคม 2021). For Loops in Python. สืบค้นวันที่ 2 กันยายน 2025, จาก https://www.geeksforgeeks.org/for-loops-in-python/  


# Slide

# Link Youtube



