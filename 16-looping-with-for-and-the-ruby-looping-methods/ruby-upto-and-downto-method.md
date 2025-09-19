# Ruby upto and downto Method

## upto Method

เมธอด **upto** ในภาษา **ruby** สามารถใช้งานได้บนคลาส **Interger, String, และ Date** ซึ่ง **upto method** สามารถใช้แทน **for loop** ได้ โดยเป็นการเพิ่มค่าของสิ่งที่เราต้องการจากไปทีละ 1 ค่าจากจุดเริ่มต้นไปยังจุดสิ้นสุด และสามารถใช้เป็นจำนวนรอบในการวนซ้ำได้อีกด้วย โดยถ้าค่าเริ่มต้นน้อยกว่าค่าสิ้นสุด method จะไม่ทำงาน

## Syntax พื้นฐาน

<pre class="language-ruby"><code class="lang-ruby"><strong>(number).upto(limit) do.....
</strong></code></pre>

* number คือ ค่าเริ่มต้นของสิ่งที่เราต้องการจะเรียงลำดับ
* limit คือ จุดสิ้นสุดของสิ่งที่เราต้องการจะเรียงลำดับ
* do คือ คำสั่งที่เราต้องการจะทำซ้ำ

## ตัวอย่างการใช้งาน upto Method

### 1. Integer

```ruby
8.upto(11) {|i| puts i}
```

### Output

```
8
9
10
11
```

### 2. String

```ruby
"a".upto("f") {|s| print s, ' ' }
```

### Output

a b c d e f

### 3. Date

```ruby
require 'date'

start_date = Date.new(2025, 1, 1)
end_date = Date.new(2025, 1, 5)

start_date.upto(end_date) do |date|
  puts date.strftime("%Y-%m-%d")
end
```

### Output

```
2025-01-01
2025-01-02
2025-01-03
2025-01-04
2025-01-05
```

### 4. ใช้งานแทน for loop

```ruby
5.upto(10) do
   puts "hello"
end
```

### Output

```
hello
hello
hello
hello
hello
hello
```

## เปรียบเทียบโค้ดกับภาษาต่างๆ

### Ruby (upto Method)

```ruby
1.upto(5) {|i| puts i}
```

### C (for loop)

```c
#include <stdio.h>

int main() {
    for (int i = 1; i <= 5; i++) {
        printf("%d\n", i);
    }
    return 0;
}

//เนื่องจากภาษา C ไม่มี upto Method จึงต้องใช้ for loop แทน
```

### Java (for loop)

```java
public class LoopExample {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            System.out.println(i);
        }
    }
}

//เนื่องจากภาษา Java ไม่มี upto Method จึงต้องใช้ for loop แทน
```

### Python (for loop)

```python
for i in range(1, 6):
    print(i)

##เนื่องจากภาษา Python ไม่มี upto Method จึงต้องใช้ for loop แทน       
```



## downto Method

ทุกอย่างเหมือนกับ **upto method** แต่ไม่สามารถใช้กับคลาส **String** ได้ และเปลี่ยนจากเพิ่มค่าขึ้นทีละ 1 เป็นลดลงจากจุดเริ่มต้นทีละ 1 ไปจนถึงจุดสิ้นสุดแทน และถ้าหากค่าเริ่มต้นมากกว่ากว่าค่าสิ้นสุด method จะไม่ทำงาน

## Syntax พื้นฐาน

```ruby
(number).downto(limit) do.....
```

* number คือ ค่าเริ่มต้นของสิ่งที่เราต้องการจะเรียงลำดับ
* limit คือ จุดสิ้นสุดของสิ่งที่เราต้องการจะเรียงลำดับ
* do คือ คำสั่งที่เราต้องการจะทำซ้ำ

## ตัวอย่างการใช้งาน downto Method

### 1. Integer

```ruby
11.downto(8) {|i| puts i}
```

### Output

```
11
10
9
8
```

### 2. Date

```ruby
require 'date'
start_date = Date.new(2025, 1, 5)
end_date = Date.new(2025, 1, 1)

start_date.downto(end_date) do |date|
  puts date.strftime("%Y-%m-%d")
end
```

### Output

```
2025-01-05
2025-01-04
2025-01-03
2025-01-02
2025-01-01
```

### 3. ใช้งานแทน for loop

```ruby
10.downto(5) do
   puts "hello"
end
```

```
hello
hello
hello
hello
hello
hello
```

## เปรียบเทียบโค้ดกับภาษาต่างๆ

### Ruby (downto)

```ruby
11.downto(8) {|i| puts i}
```

### C (for loop)

```c
#include <stdio.h>

int main() {
    for (int i = 11; i >= 8; i--) {
        printf("%d\n", i);
    }
    return 0;
}

//เนื่องจากภาษา C ไม่มี downto Method จึงต้องใช้ for loop แทน
```

### Java (for loop)

```java
public class LoopExample {
    public static void main(String[] args) {
        for (int i = 11; i >= 8; i--) {
            System.out.println(i);
        }
    }
}

//เนื่องจากภาษา Java ไม่มี downto Method จึงต้องใช้ for loop แทน
```

### Python (for loop)

```python
for i in range(11, 7, -1):
    print(i)
    
 ##เนื่องจากภาษา Python ไม่มี downto Method จึงต้องใช้ for loop แทน   
```

## แหล่งอ้างอิง&#x20;

### Ruby

* APIdock. (ไม่มีวันที่). Method upto class String. สืบค้นวันที่ 1 กันยายน 2025, จาก  [https://apidock.com/ruby/v2\_2\_9/String/upto](https://apidock.com/ruby/v2_2_9/String/upto) &#x20;
* Technopia. (27 ตุลาคม 2016). Looping with for and the Ruby Looping Methods. สืบค้นวันที่ 1 กันยายน 2025, จาก [https://www.techotopia.com/index.php/Looping\_with\_for\_and\_the\_Ruby\_Looping\_Methods](https://www.techotopia.com/index.php/Looping_with_for_and_the_Ruby_Looping_Methods)
* GeeksforGeeks. (9 มกราคม 2020). Ruby | Date downto() function. สืบค้นวันที่ 1 กันยายน 2025, จาก [https://www.geeksforgeeks.org/ruby/ruby-date-downto-funtion/](https://www.geeksforgeeks.org/ruby/ruby-date-downto-funtion/)
* GeeksforGeeks. (12 กรกรกฎาคม 2025). Ruby | Integer upto() function. สืบค่นวันที่ 1 กันยายน 2025, จาก [https://www.geeksforgeeks.org/ruby/ruby-integer-upto-function/](https://www.geeksforgeeks.org/ruby/ruby-integer-upto-function/)

### C

* W3Schools. (ไม่มีวันที่). C for loop. สืบค้นวันที่ 1 กันยายน 2025, จาก [https://www.geeksforgeeks.org/ruby/ruby-integer-upto-function/](https://www.geeksforgeeks.org/ruby/ruby-integer-upto-function/)

### Java

* GeeksforGeeks. (12 กรกฏาคม 2025). Java For Loop. สืบค้นวันที่ 1 กันยายน 2025, จาก [https://www.geeksforgeeks.org/java/java-for-loop-with-examples/](https://www.geeksforgeeks.org/java/java-for-loop-with-examples/)

### Python

* Withoutcoffee Icantbedev. (24 กุมภาพันธ์  2023). การใช้งาน For Loop ในภาษา Python. สืบค้นวันที่ 1 กันยายน 2025, จาก [https://devhub.in.th/blog/python-for-loop](https://devhub.in.th/blog/python-for-loop)

## Slide

## Clip
