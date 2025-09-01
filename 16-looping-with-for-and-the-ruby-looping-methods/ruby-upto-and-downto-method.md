# Ruby upto and downto Method

## upto Method

เมธอด **upto** ในภาษา **ruby** สามารถใช้งานได้บนคลาส **Interger, String, และ Date** ซึ่ง **upto method** สามารถใช้แทน **for loop** ได้ โดยเป็นการเพิ่มค่าของสิ่งที่เราต้องการจากไปทีละ 1 ค่าจากจุดเริ่มต้นไปยังจุดสิ้นสุด และสามารถใช้เป็นจำนวนรอบในการวนซ้ำได้อีกด้วย

## Syntax พื้นฐาน

<pre class="language-ruby"><code class="lang-ruby"><strong>start.upto(end) do.....
</strong></code></pre>

* start คือ ค่าเริ่มต้นของสิ่งที่เราต้องการจะเรียงลำดับ
* end คือ จุดสิ้นสุดของสิ่งที่เราต้องการจะเรียงลำดับ
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

### 3. ใช้งานแทน for loop

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

### Ruby (ีupto Method)

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
