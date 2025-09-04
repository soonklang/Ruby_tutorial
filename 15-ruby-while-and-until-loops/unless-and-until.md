# Ruby Unless and Until

### Until

> คำสั่ง until นั้นจะทำงานก็ต่อเมื่อในขณะนั้นเงื่อนไขเป็นเท็จและก็จะทำงานจนกว่าเงื่อนไขจะเป็นจริง ซึ่งคำสั่ง until นั้นจะตรงกับข้ามกับคำสั่ง while ที่จะทำงานก็ต่อเมื่อเงื่อนไขในขณะนั้นเป็นจริง Syntax ของคำสั่ง until นั้นจะเหมือนกับคำสั่ง while ต่างกันแค่เงื่อนไขที่จะทำงาน กับเปลี่ยนคำว่า while เป็นคำว่า until แทน


**Basic Syntax**

``` ruby
until condition do
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

> จากตัวอย่างเป็นโปรแกรมนับถอยหลังโดยที่เริ่มจาก 10 ในแต่ละรอบการทำงานโปรแกรมนั้นจะตรวจสอบเงื่อนไขว่าเป็นจริงหรือเป็นเท็จ และถ้าหากเงื่อนไขเป็นเท็จก็ทำงานภายใน loop จนกว่าเงื่อนไข i == 5 นั้นจะเป็นจริง ในแต่ละรอบการทำงานใน loop จะแสดงค่าในตัวแปรออกมา และลดค่าในตัวแปรลงหนึ่งค่าจากคำสั่ง i = i -1 คำสั่งนี้จะทำให้ค่าของ i ลดลงเรื่อยๆจนถึง 5 ทำให้ loop หยุดทำงานเพราะเงื่อนไขเป็นจริงแล้ว

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
i = 10
begin
  puts i
    i = i - 1
end until i == 5
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

> เป็นการเขียนคำสั่ง until ในอีกรูปแบบหนึ่งซึงจะทำให้ code กระชับขึ้น

### เปรียบเทียบภาษา Ruby กับภาษา Java , C , Python

**Ruby Example Code**
``` ruby
var = 7
until var == 11 do
  puts var * 10
  var = var + 1
end
```

**Java Example Code**
``` Java
public class UntilExample {
    public static void main(String[] args) {
        int var = 7;
        while (!(var == 11)) {
            System.out.println(var * 10);
            var = var + 1;
        }
    }
}
```

**C Example Code**
``` C
#include <stdio.h>

int main() {
    int var = 7;
    while (var != 11) {
        printf("%d\n", var * 10);
        var = var + 1;
    }
    return 0;
}
```

**Python Example Code**
``` Python
var = 7
while var != 11:
    print(var * 10)
    var = var + 1
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>70
80
90
100
</code></pre>
</details>

> ในภาษา java , c , python นั้นไม่มีคำสั่ง until ถ้าต้องการใช้งานให้ได้ผลลัพธ์แบบเดียวกันต้องใช้ผ่านคำสั่ง while ที่ตั้งเงื่อนตรงกันข้ามกับคำสั่ง while ปกติ ซึ่งก็คือการตั้งเงื่อนไขเริ่มต้นที่จะทำให้โปรเเกรมทำงานนั้นเป็นเท็จนั้นเอง

------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Unless

> คำสั่ง uless นั้นจะทำงานก็ต่อเมื่อเงื่อนไขเป็นเท็จ ซึ่งจะเป็นคำสั่งที่ตรงข้ามกับคำสั่ง if ที่คำสั่ง if นั้นจะทำงานก็ต่อเมื่อเงื่อนไขนั้นเป็นจริง

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

> ในตัวอย่างประกาศสองตัวแปรคือ x และ y และกำหนดค่าของตัวแปรทั้งสองไม่ให้เท่ากัน โปรแกรมนี้จะแสดงผล ยกเว้นว่า x และ y นั้นมีค่าเท่ากัน และเนื่องจากที่ x == y นั้นไม่เป็นจริง ดังนั้นโปรแกรมทำงานตาม code คำสั่ง unless สามารถใช้งานคำสั่ง else ร่วมกับคำสั่ง unless ได้ ซึ่งโปรแกรมจะทำงานคำสั่ง else ถ้าหากเงื่อนไขนั้นเป็นจริง แต่ว่าไม่สามารถใช้งานคำสั่ง elsif ร่วมกับคำสั่ง unless ได้

**Modifier Form**

``` ruby
code unless conditional
```

**Example Code**

``` ruby
x = 1
y = 3
puts "x is not equal to y" unless x == y
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>x is not equal to y
</code></pre>
</details>

> เป็นการเขียนคำสั่ง unless ในอีกรูปแบบหนึ่งซึ่งจะทำให้ code กระชับขึ้น

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


**Java Example Code**
``` Java
public class UnlessExample {
    public static void main(String[] args) {
        int x = 1;
        if (!(x >= 2)) {
            System.out.println("x is less than 2");
        } else {
            System.out.println("x is greater than 2");
        }
    }
}
```


**C Example Code**
``` C
#include <stdio.h>

int main() {
    int x = 1;
    if (!(x >= 2)) {
        printf("x is less than 2\n");
    } else {
        printf("x is greater than 2\n");
    }
    return 0;
}
```


**Python Example Code**
``` Python
x = 1
if not (x >= 2):
    print("x is less than 2")
else:
    print("x is greater than 2")

```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>x is less than 2
</code></pre>
</details>

> เช่นเดียวกับคำสั่ง until ในภาษา java , c , python นั้นก็ไม่มีคำสั่ง unless เช่นกัน ดังนั้นถ้าต้องการใช้งานให้ได้ผลลัพธ์แบบเดียวกันต้องใช้คำสั่ง if ที่จะทำเมื่อเงื่อนไขเป็นเท็จแทน java , c จะใช้ ! ในเงื่อนไข ในขณะที่ python จะใช้ คำสั่ง if not

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

### JAVA , C , PYTHON

* Python Software Foundation. (n.d.). The while statement. In Python documentation (version 3). Retrieved September 3, 2025, from
https://docs.python.org/3/reference/compound_stmts.html#the-while-statement

* Oracle. (n.d.). The while statement. In The Java™ Tutorials. Retrieved September 3, 2025, from
https://docs.oracle.com/javase/tutorial/java/nutsandbolts/while.html

* cppreference.com. (n.d.). while statement (C). Retrieved September 3, 2025, from
https://en.cppreference.com/w/c/language/while.html

* Oracle. (n.d.). The if-then-else Statement. Oracle Java Tutorials.Retrieved September 3, 2025, from
https://docs.oracle.com/javase/tutorial/java/nutsandbolts/if.html

* ISO C / cppreference. if statement (C). Retrieved September 3, 2025, from
https://en.cppreference.com/w/c/language/if.html

* Python Software Foundation. (n.d.). The if statement. Python Docs. Retrieved September 3, 2025, from
https://docs.python.org/3/reference/compound_stmts.html#if
