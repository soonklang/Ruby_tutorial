# Ruby Unless and Until

**Until**
> จะทำงานจนกว่าเงื่อนไขเป็นจริง กล่าวคือมันจะทำงานในขณะที่เงื่อนไขเป็นเท็จนั่นเอง ซึ่งตรงกับข้ามกับคำสั่ง while loop ซึ่งทำงานในขณะที่เงื่อนไขเป็นจริง นี่เป็นรูปแบบการใช้งาน
**Basic Syntax**
``` ruby
until condition do
    code
end
```
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
### การเปรียบเทียบกับภาษา Python , Java , C ของคำสั่ง Until

**Unless**
>เงื่อนไขให้โปรแกรมทำงานในบล็อคของคำสั่งยกเว้นแต่ว่าเงื่อนไขจะเป็นจริง หรือกล่าวอีกนัยหนึ่งโปรแกรมจะทำงานเมื่อเงื่อนไขเป็นเท็จนั่นเอง ซึ่งมันเป็นคำสั่งที่ตรงข้ามกับคำสั่ง if ที่จะทำงานเมื่อเงื่อนไขเป็นจริง มาดูตัวอย่างการใช้งาน
``` ruby
unless conditional [then]
   code
[else
   code ]
end
```
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
### การเปรียบเทียบกับภาษา Python , Java , C ของคำสั่ง Unless

### References
* Smyth, N. (2016, October 27). Ruby while and until loops. Techotopia. Retrieved August 30, 2025, from https://www.techotopia.com/index.php/Ruby_While_and_Until_Loops
* Ruby Core Team. (n.d.). Control expressions: while loop. Ruby documentation. Retrieved August 30, 2025, from
https://docs.ruby-lang.org/en/master/syntax/control_expressions_rdoc.html#label-while+Loop
* Cooper, P. (2016). Beginning Ruby: From novice to professional (3rd ed.), Apress. from
https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Beginning%20Ruby%20-%20From%20Novice%20to%20Professional%20-%20Third%20Edition.pdf
* Tutorialspoint. (n.d.). Ruby - loops. Tutorialspoint. Retrieved August 30, 2025, from
https://www.tutorialspoint.com/ruby/ruby_loops.htm
* GeeksforGeeks. (2025, 11 Jul). Ruby loops (for, while, do while, until). GeeksforGeeks. Retrieved August 30, 2025, from
https://www.geeksforgeeks.org/ruby/ruby-loops-for-while-do-while-until/
### 
