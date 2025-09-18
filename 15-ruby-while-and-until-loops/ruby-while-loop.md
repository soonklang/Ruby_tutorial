# Ruby While Loop

**ความหมาย และหลักการทำงาน**

> While Loop เป็นcontrol expression ที่ควบคุมการทำซ้ำ โดยจะตรวจสอบเงื่อนไขทุกครั้งก่อนทำคำสั่งในบล็อก while loop ถ้าเงื่อนไขเป็นจริงจะทำคำสั่งลูป แต่ถ้าเป็นเท็จจะออกจากลูป

**Flow Chart**

![Image](https://github.com/user-attachments/assets/d1cd0950-c875-4667-bc9e-2a00c5aa98c1)

**Basic Syntax**
``` ruby
while condition do
  # code block
end
```
``` ruby
count = 1
while count <= 5
  puts count
  count += 1
end
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>1
2
3
4
5
</code></pre>
</details>

>* while ต้องมี end ปิดเสมอ
>* condition(เงื่อนไข) : มีค่าเป็นจริง(true) หรือเท็จ(false)
>  
>    ตัวอย่างค่า condition เช่น true, false , 1<2 , !numbers.empty? && numbers.first < 4 , nil เป็นต้น
>* do จะเขียนหรือไม่เขียนก็ได้

ใน Ruby nil เป็นอ็อบเจ็กต์หนึ่งของคลาส NilClass และใช้สื่อถึงความว่างเปล่าหรือไม่มีข้อมูลในตัวแปรนั้น เช่นเดียวกับ null ใน java ,NULL ใน C,C++,nil ใน Go
```ruby
puts nil == false     # false   (nil ไม่เท่ากับ false)
```
>ดังนั้น nil ไม่ได้มีค่าเป็น false แต่แค่ถูกพิจารณาให้เป็น false ตอนเช็คเงื่อนไข

**Modifier Form**
```ruby
statement while condition
```
```ruby
i = 0
puts i += 1 while i < 3
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>1
2
3
</code></pre>
</details>

>เป็นการเขียนย่อแบบbasic syntax โดยไม่ต้องเขียน end

**begin...end while**
```ruby
begin
  # code
end while condition
```
>เนื่องจากRubyไม่มี do-while loop สามารถใช้ begin-while loop แทนได้(จะทำในบล็อกอย่างน้อย 1 รอบ)
```ruby
i = 0
begin
  puts "i = #{i}"
  i += 1
end while i < 3
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>i = 0
i = 1
i = 2
</code></pre>
</details>

**Return Value**
```ruby
result = while false
  "never executed"
end
puts result  # Output: nil

result = while true
  break "hello"
end
puts result  # Output: "hello"
```
>while loop จะreturnค่า nil เว้นแต่จะใช้ break เพื่อส่งค่าออกมา

**ข้อดี : เหมาะกับงานทำซ้ำที่ไม่ทราบจำนวนรอบที่แน่นอน**

**ข้อควรระวัง : การเกิดลูปไม่รู้จบ(infinite loop)**

**วิธีแก้**
* เพิ่มตัวแปรนับรอบลูป
``` ruby
i = 0 
while i < 10
  puts i
  i += 1  # i=i+1 
end
``` 
* ใช้คำสั่ง break
``` ruby
while true
  puts "Enter number (0 to stop):"
  input = gets.to_i
  break if input == 0
end
``` 
> gets ใช้รับ input จากคีย์บอร์ด , to_i ใช้แปลง string เป็น integer 

### การเปรียบเทียบแต่ละภาษา(Python,Java,C)

**Ruby**
``` Ruby
i = 1
while i <= 5
  puts "The number is: #{i}"
  i += 1
end 
puts "Loop finished."
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>The number is: 1
The number is: 2
The number is: 3
The number is: 4
The number is: 5
Loop finished.</code></pre>
</details>

**Python**
``` Python
i = 1
while i <= 5:
    print(f"The number is: {i}")
    i += 1
print("Loop finished.")
```
> สิ่งที่ต่างจากRubyคือ
>* การใช้เครื่องหมาย : ต่อท้ายเงื่อนไขของ while
>* ใช้ indentation ในการบอกขอบเขต


**Java**
``` Java
public class WhileLoopExample {
    public static void main(String[] args) {
        int i = 1;
        while (i <= 5) {
            System.out.println("The number is: " + i);
            i++;
        }
        System.out.println("Loop finished.");
    }
}
```
> สิ่งที่ต่างจากRubyคือ
>* เงื่อนไขของต้องอยู่ในวงเล็บ ()
>* ใช้ {} เพื่อกำหนดขอบเขตของ loop

**C**
``` C
#include <stdio.h>
int main() {
    int i = 1;
    while (i <= 5) {
        printf("The number is: %d\n", i);
        i++;
    }
    printf("Loop finished.\n");
    return 0; //คือการบอก Operating System ว่าโปรแกรมทำงานเสร็จสิ้นโดยไม่มีข้อผิดพลาด ซึ่งเป็นมาตรฐานของภาษา C
}
```
> สิ่งที่ต่างจากRubyคือ
>* เงื่อนไขของต้องอยู่ในวงเล็บ ()
>* ใช้ {} เพื่อกำหนดขอบเขตของ loop

### References
Ruby
* Smyth, N. (2016, October 27). Ruby while and until loops. Techotopia. Retrieved August 30, 2025, from https://www.techotopia.com/index.php/Ruby_While_and_Until_Loops
* Ruby Core Team. (n.d.). Control expressions: while loop. Ruby documentation. Retrieved August 30, 2025, from https://docs.ruby-lang.org/en/master/syntax/control_expressions_rdoc.html#label-while+Loop
* Cooper, P. (2016). Beginning Ruby: From novice to professional (3rd ed.), Apress. from https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Beginning%20Ruby%20-%20From%20Novice%20to%20Professional%20-%20Third%20Edition.pdf
* Tutorialspoint. (n.d.). Ruby - loops. Tutorialspoint. Retrieved August 30, 2025, from https://www.tutorialspoint.com/ruby/ruby_loops.htm
* GeeksforGeeks. (2025, 11 Jul). Ruby loops (for, while, do while, until). GeeksforGeeks. Retrieved August 30, 2025, from https://www.geeksforgeeks.org/ruby/ruby-loops-for-while-do-while-until/
* Codecademy. (n.d.). The while loop. In Learn Ruby: Loops & iterators. Codecademy. Retrieved August 30, 2025, from https://www.codecademy.com/courses/learn-ruby/lessons/loops-iterators
* Chongnguluam, W. (2020, January 6). Ruby nil object. Dev.to. Retrieved August 30, 2025, from https://dev.to/iporsut/ruby-nil-object-16fm
* How.dev. (n.d.). What is the difference between nil and false in Ruby? How.dev. Retrieved August 30, 2025, from https://how.dev/answers/what-is-the-difference-between-nil-and-false-in-ruby
  
Python
* Python Software Foundation. (n.d.). The while statement. In The Python Language Reference (Python 3). Retrieved August 30, 2025, from https://docs.python.org/3/reference/compound_stmts.html#while
* W3Schools. (n.d.). Python while loops. W3Schools. Retrieved August 30, 2025, from https://www.w3schools.com/python/python_while_loops.asp

Java
* Oracle. (2023). The while statement. In Java Language Specification: Java SE 20 Edition (Section 14.12). Oracle Corporation. Retrieved August 30, 2025, from https://docs.oracle.com/javase/specs/jls/se20/html/jls-14.html#jls-14.12
* W3Schools. (n.d.). Java while loop. W3Schools. Retrieved August 30, 2025, from https://www.w3schools.com/java/java_while_loop.asp

C
* Ritchie, D. M. (n.d.). C reference manual. Bell Telephone Laboratories. Retrieved August 30, 2025, from https://www.nokia.com/bell-labs/about/dennis-m-ritchie/cman.pdf
* W3Schools. (n.d.). C while loop. W3Schools. Retrieved August 30, 2025, from https://www.w3schools.com/c/c_while_loop.php

### Presentation
[RUBY_WHILE_LOOP.pdf](https://github.com/user-attachments/files/22409811/RUBY_WHILE_LOOP.pdf)

### Video
https://youtu.be/Av6HNJVW-Qw

**จัดทำโดย**
ชนาธินาถ เรืองวิทยานนท์ 660710589
