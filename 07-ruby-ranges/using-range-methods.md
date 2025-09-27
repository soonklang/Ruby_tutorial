# Using Range Methods

#### **Range Methods** คือฟังก์ชั้นต่างๆ ที่เราสามารถเรียกใช้กับช่วงค่าพวกนี้ได้ เช่นการหาค่าต่ำสุด สูงสุด การวนลูปผ่านค่าทุกตัวในช่วง ฯลฯ

การสร้าง Range สามารถทำได้ 2 แบบคือ

### <kbd>How to Create Ranges</kbd>

<kbd>Range</kbd> ที่ใช้ <kbd>'..'</kbd> จะเป็นการสร้างที่รวมค่าสุดท้ายของช่วงนั้นเข้าไปด้วย แต่ถ้าหากใช้ <kbd>'...'</kbd> ช่วงสุดท้ายจะไม่ถูกรวมเข้าไป

<pre class="language-ruby"><code class="lang-ruby"><strong>#Ruby
</strong>(1..4)      Output => [1, 2, 3, 4]
('a'..'d')  Output => ["a", "b", "c", "d"]

(1...4)     Output => [1, 2, 3]
('a'...'d') Output => ["a", "b", "c"]
</code></pre>

คือการสร้างช่วงใหม่โดยอิงตามวัตถุที่ถูกกำหนดไว้ได้แก่ <kbd>begin</kbd>, <kbd>end</kbd> ตามลำดับและมีตัว <kbd>exclude\_end</kbd> เพื่อกำหนดว่าเราจะรวมวัตถุตัวสุดท้ายกับช่วงนั้นไหม

```ruby
#Ruby
Range.new(2, 5)            Output => [2, 3, 4, 5]
Range.new(2, 5, true)      Output => [2, 3, 4]
Range.new('a', 'd')        Output => ["a", "b", "c", "d"]
Range.new('a', 'd', true)  Output => ["a", "b", "c"]
```

```python
#Pyton
range1 = range(1, 6)     Output => [1, 2, 3, 4, 5]
range2 = range(1, 5)     Output => [1, 2, 3, 4]
```

```java
#Java
import java.util.stream.IntStream;

public class Main {
	public static void main(String[] args) {
	IntStream range1 = IntStream.range(1, 5);         Output => [1, 2, 3, 4]
	IntStream range2 = IntStream.rangeClosed(1, 5);   Output => [1, 2, 3, 4, 5]
    }
}
```

```c
#C #ต้องสร้างโครงสร้างเองโดยใช้ Loop เข้ามาช่วย
#include <stdio.h>

int main() {
    int start = 1;
    int end = 5;

    for (int i = start; i <= end; i++) {
        printf("%d ", i);  // => 1 2 3 4 5
    }

    return 0;
}
```

### <kbd>**.to\_a**</kbd>

<kbd>to\_a</kbd> เป็นเมธอดที่แปลงวัตถุ <kbd>Range</kbd> ให้เป็น <kbd>Array</kbd> โดยสมาชิกทั้งหมดจะมีอยู่ในช่วงที่กำหนดไว้

```ruby
#Ruby
(1..4).to_a                 Output => [1, 2, 3, 4]
Range.new(2, 5).to_a        Output => [2, 3, 4, 5]
```

```python
#Python
list(range(1, 6))    Output => [1, 2, 3, 4, 5]
list(range(1, 5))    Output => [1, 2, 3, 4]
```

```java
#Java
import java.util.*;
import java.util.stream.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> list = IntStream.rangeClosed(1, 5)
                                      .boxed()
                                      .collect(Collectors.toList());
        System.out.println(list);  Output => [1, 2, 3, 4, 5]

        List<Integer> list2 = IntStream.range(1, 5)
                                       .boxed()
                                       .collect(Collectors.toList());
        System.out.println(list2);  Output => [1, 2, 3, 4]
    }
}
```

```c
#C #ไม่มี Range โดยตรง ต้องสร้างอาร์เรย์และเติมค่าด้วยลูป
#include <stdio.h>

int main() {
    int start = 1, end = 5;
    int size = end - start + 1;
    int arr[size];

    for (int i = 0; i < size; i++) {
        arr[i] = start + i;
    }

    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);  Output => 1 2 3 4 5
    }

    return 0;
}
```

### <kbd>**.to\_s**</kbd>

<kbd>to\_s</kbd> จะเป็นการเปลี่ยนวัตถุ Range ให้เป็น String

<pre class="language-ruby"><code class="lang-ruby"><strong>#Ruby
</strong><strong>(1..4).to_s  # => "1..4"
</strong>(1...4).to_s # => "1...4"
(1..).to_s   # => "1.."
(..4).to_s   # => "..4"
</code></pre>

<pre class="language-python"><code class="lang-python"><strong>#Python
</strong>r = range(1, 6)
print(str(r))  Output => 'range(1, 6)'
</code></pre>

<pre class="language-java"><code class="lang-java"><strong>#Java
</strong>import java.util.*;

public class Main {
    public static void main(String[] args) {
        List&#x3C;Integer> range = Arrays.asList(1, 2, 3, 4, 5);
        System.out.println(range.toString());  Output => [1, 2, 3, 4, 5]
    }
}
</code></pre>

<pre class="language-c"><code class="lang-c"><strong>#C ต้องใช้ sprintf()เพื่อแปลงค่าเป็น string
</strong>#include &#x3C;stdio.h>

int main() {
    int a = 5;
    char buffer[10];

    sprintf(buffer, "%d", a);   // แปลง int เป็น string
    printf("Number as string: %s\n", buffer);  // => "5"
    return 0;
}
</code></pre>

### <kbd>**.begin & .end**</kbd>

begin

Ruby ใช้สำหรับคืนค่าเริ่มต้นของช่วงนั้นๆ

```ruby
#Ruby
(1..4).begin        Output => 1
```

ใน python จะไม่มี Range object แบบเดียวกับ Ruby แต่ใช้ค่าเริ่มต้นจาก range(start, stop) แทน&#x20;

<pre class="language-python"><code class="lang-python"><strong>#Python
</strong>r = range(1, 4)
print(r.start)      Output => 1
</code></pre>

Java ไม่มี Range object ตรง ๆ เช่นกันใช้ IntStream แทน โดย start คือพารามิเตอร์แรกของ range()

```java
#Java
import java.util.stream.IntStream;

public class Main {
    public static void main(String[] args) {
        int start = 1;
        int end = 4;
        IntStream range = IntStream.range(start, end);
        System.out.println("Begin: " + start); Output => 1
    }
}
```

ภาษา C ไม่มี Range หรือ Method ที่ใกล้เคียงจึงต้องกำหนด datatype เอง

```c
C
#include <stdio.h>

int main() {
    int start = 1;
    int end = 4;

    printf("Begin: %d\n", start);  Output => 1

    return 0;
}
```

end

Ruby ใช้สำหรับคืนค่าสุดท้ายของช่วงนั้นๆ

```ruby
#Ruby
(1..4).end         Output => 4
```

ใน Python ค่า stop ใน range หรือ index ตัวที่ 2 จะเป็นค่าสุดท้าย

```python
r = range(1, 5)
print(r.stop)      Output => 5
```

Java จะกำหนดให้ พารามิเตอร์ตัวที่ 2 เป็นจุดสิ้นสุดหรือ end นั้นเอง

<pre class="language-java"><code class="lang-java">#Java
import java.util.stream.IntStream;
public class Main {
    public static void main(String[] args) {
        int start = 1;
<strong>        int end = 5;
</strong>        IntStream range = IntStream.range(start, end);
        System.out.println("End: " + end);
   }
}
</code></pre>

ในส่วนของถาษา C  นั้นไม่มี .end ดังนั้นเราต้องสร้างตัวแปรขึ้นมาเอง

<pre class="language-c"><code class="lang-c"><strong>#C 
</strong>#include &#x3C;stdio.h>

int main() {
    int start = 1;
    int end = 4;
    int count = 0;
    for (int i = start; i &#x3C;= end; i++) {
        count++;
    }

    printf("End: %d\n", end);  Output => 4

    return 0;
}
</code></pre>

### <kbd>**.count**</kbd>

Ruby ใช้สำหรับคืนค่าจำนวนสมาชิกทั้งหมดในช่วงนั้น

```ruby
#Ruby
(1..4).count          Output => 4
('a'..'d').count      Output => 4
```

Python จะใช้วิธีที่คล้ายกับ Ruby แต่จะใช้ len แทน

```python
#Python
range1 = range(1, 5)
print(len(range1))  Output => 4
```

ใน Java เราสารมารถใช้ คำสั่ง .count ได้เลย

<pre class="language-java"><code class="lang-java"><strong>#Java
</strong>import java.util.stream.*;

public class Main {
    public static void main(String[] args) {
        long count = IntStream.rangeClosed(1, 4).count();
        System.out.println(count); Output => 4
    }
}
</code></pre>

ภาษา C นั้นเราต้องคำนวนเองโดยการใช้ ลูป เข้ามาข่วย

```c
#C #ใช้ลูปนับเอง
#include <stdio.h>

int main() {
    int start = 1;
    int end = 4;
    int count = 0;
    for (int i = start; i <= end; i++) {
        count++;
    }

    printf("Count: %d\n", count);  Output => 4

    return 0;
}
```

### <kbd>**.exclude\_end?**</kbd>

เมธอดนี้จะคืนค่าเป็น <kbd>true</kbd> กับ <kbd>false</kbd> โดยจะเช็คว่าช่วงนั้นๆรวมค่าสุดท้ายหรือไม่

```ruby
#Ruby
Range.new(2, 5).exclude_end?       Output => false
Range.new(2, 5, true).exclude_end? Output => true
(2..5).exclude_end?                Output => false
(2...5).exclude_end?               Output => true
```

Python เป็น exclusive เสมอจึงไม่มีเมธอดนี้

Java สามารถลือกใช้ได้ 2 อย่างดังนี้

```java
#Java
IntStream.range(start, end) #ไม่รวมค่าสุดท้าย
IntStream.rangeClosed(start, end) #รวมค่าสุดท้าย
```

### <kbd>**.first & .last**</kbd>

<kbd>first</kbd> อาจจะมีความคล้ายกันกับ [<kbd>begin</kbd>](using-range-methods.md#begin) แต่ทำงานไม่เหมือนกันโดย [<kbd>begin</kbd> ](using-range-methods.md#begin)จะดึงสมาชิกตัวแรกออกมา แต่ first สามารถดึงออกมาได้หลายตัวในเวลาเดียวกันหรือไม่เอาอะไรออกมาเลยก็ได้

```ruby
#Ruby
(1..4).first     Output => 1
('a'..'d').first Output => "a"

(1..10).first(3) Output => [1, 2, 3]
(1..10).first(0) Output => []
```

ใน Python เราสามารถทำได้เหมือนกับ Ruby แต่รูปแบบการเข้าถึงจะคล้ายกับการเข้าถึง array

```python
#Python
r = range(1, 4)
print(r[0])         Output => 1
print(list(r)[:3])  Output => [1, 2, 3]
```

Java นั้นเราจะต้องแปลงเป็น ArrayList ก่อนถึงจะเข้าถึงตำแหน่งได้

<pre class="language-java"><code class="lang-java"><strong>#Java
</strong>import java.util.stream.*;

public class Main {
	public static void main(String[] args) {
	IntStream range = IntStream.rangeClosed(1, 4);
	int first = range.findFirst().getAsInt();  Output => 1
	System.out.println(first);

	range = IntStream.rangeClosed(1, 4);
	int[] firstThree = range.limit(3).toArray();  Output => [1, 2, 3]
	for(int i=0;i&#x3C;firstThree.length;i++){
		System.out.println(firstThree);
	}
    }
}
</code></pre>

ในภาษา C เราจะเข้าถึงแบบ Array เช่นกัน

<pre class="language-c"><code class="lang-c"><strong>#C
</strong>#include &#x3C;stdio.h>

int main() {
    int arr[] = {1,2,3,4};
    printf("%d\n", arr[0]);  Output => 1

    printf("%d %d %d\n", arr[0], arr[1], arr[2]);  Output => 1 2 3
    return 0;
}
</code></pre>

<kbd>last</kbd> ทำหน้าที่คล้ายกับ [<kbd>end</kbd>](using-range-methods.md#end) และมีความสามารถที่เหมือนกับ [<kbd>first</kbd>](using-range-methods.md#first) ในการดึงสมาชิกออกมาได้มากกว่า 1

```ruby
#Ruby
(1..4).last     Output => 4
('a'..'d').last Output => "d"

(1..10).last(3) Output => [8, 9, 10]
(1..10).last(0) Output => []
```

ใน Python ไม่มีเมธอด last เราจึงใช้วิธีเข้าถึงโดยใช้ negative index แทน

```python
#Python
r = range(1, 4)
print(list(r)[-1])       Output => 4 #เข้าถึงโดยการใช้ negative index
```

Java ต้องแปลงเป็น ArrayList แล้ว get index ตำแหน่งสุดท้ายเอาเอง

```java
#Java
import java.util.stream.*;
public class Main {
	public static void main(String[] args) {
	IntStream range = IntStream.rangeClosed(1, 4);
	int[] arr = range.toArray();

	int last = arr[arr.length - 1];  Output => 4 #ต้องแปลงเป็น array แล้วเข้าถึง index สุดท้าย
	System.out.println(last);
    }
}
```

ในส่วนของ C ก็คล้าย Java เลยเข้าถึงแบบ index สุดท้ายเหมือนกัน

```c
#C
#include <stdio.h>

int main() {
    int arr[] = {1,2,3,4};
    int len = sizeof(arr) / sizeof(arr[0]);

    printf("%d\n", arr[len - 1]);  Output => 4 #ต้องเข้าถึง index สุดท้าย
    return 0;
}
```

### <kbd>**.max & .min**</kbd>

&#x20;max ใช้สำหรับการค่าที่มากที่สุดภายในช่วง และ สามารถดึงออกมาได้หลายตัวพร้อมกันอีกด้วยโดยใส่จำนวนเข้าไปนอกจากนี้ยังมีการใช้ block เพื่อกำหนดเงื่อนไขในการหาค่าได้อีกด้วย

```ruby
#Ruby
(1..4).max     Output => 4
('a'..'d').max Output => "d"
(-4..-1).max   Output => -1

(1..4).max(2)     Output => [4, 3]
('a'..'d').max(2) Output => ["d", "c"]
(-4..-1).max(2)   Output => [-1, -2]
(1..4).max(50)    Output => [4, 3, 2, 1]
```

<pre class="language-ruby"><code class="lang-ruby"><a data-footnote-ref href="#user-content-fn-1">#block example</a>

(1..4).max {|a, b| p [a, b]; a &#x3C;=> b } 
จากเงื่อนไขนี้ คือ การเปรียบเทียบค่าจากในช่วง 2 ตัวโดยหาค่าที่มากที่สุดจาก 2 ตัวที่ถูกดึงออกมา
Output
[2, 1] #เปรียบเทียบระหว่าง 1 กับ 2 -> ได้ 2 เพราะ 2 มีค่ามากกว่า 1
[3, 2] #เปรียบเทียบระหว่าง 3 กับ 2 -> ได้ 3 เพราะ 3 มีค่ามากกว่า 2
[4, 3] #เปรียบเทียบระหว่าง 4 กับ 3 -> ได้ 4 เพราะ 4 มีค่ามากกว่า 3
</code></pre>

Python นั้นสามารถใช้คำสั่ง max หาค่าสูงสุดได้เลย

```python
#Python
print(max(range(1, 5)))       Output => 4
print(max(range(1, 4)))       Output => 3
words = ['cat', 'horse', 'dog']
print(max(words, key=len))     Output => 'horse'
```

Java ใช้คำสั่ง IntStream.range().max ได้เลยเหมือนกัน

```java
#Java
import java.util.stream.*;

public class Main {
	public static void main(String[] args) {
	int max = IntStream.rangeClosed(1, 4).max().getAsInt();  Output => 4
	   System.out.println(max);
	   String[] words = {"cat", "horse", "dog"};
	   String longest = java.util.Arrays.stream(words)
    	   .max((a, b) -> Integer.compare(a.length(), b.length()))
    	   .orElse(null);  Output => "horse"
	   System.out.println(longest);
    }
}
```

ส่วน C นั้นเราต้องกำหนดค่าเอง

```c
#C
#include <stdio.h>

int main() {
    int max = 1;
    for (int i = 2; i <= 4; i++) {
        if (i > max)
            max = i;
    }
    printf("Max: %d\n", max);  Output => 4
    return 0;
}
```

min กลับกันจะทำหน้าที่ตรงกันข้ามกับ max โดยจะหาค่าที่น้อยที่สุดออกมา

```ruby
#Ruby
(1..4).min     Output => 1
('a'..'d').min Output => "a"
(-4..-1).min   Output => -4

(1..4).min(2)     Output => [1, 2]
('a'..'d').min(2) Output => ["a", "b"]
(-4..-1).min(2)   Output => [-4, -3]
(1..4).min(50)    Output => [1, 2, 3, 4]
```

<pre class="language-ruby"><code class="lang-ruby"><a data-footnote-ref href="#user-content-fn-1">#block example</a>

(1..4).min {|a, b| p [b, a]; a &#x3C;=> b } 

Output
[1, 2] #เปรียบเทียบระหว่าง 1 กับ 2 -> ได้ 1 เพราะ 1 มีค่าน้อยกว่า 2
[1, 3] #เปรียบเทียบระหว่าง 1 กับ 3 -> ได้ 1 เพราะ 1 มีค่าน้อยกว่า 3
[1, 4] #เปรียบเทียบระหว่าง 1 กับ 4 -> ได้ 1 เพราะ 1 มีค่าน้อยกว่า 4
</code></pre>

Python ทำได้เหมือนตัวของ max เลยเพราะมี คำสั่ง min อยู่แล้ว

```python
#Python
print(min(range(1, 4)))              Output => 1

words = ['cat', 'horse', 'dog']
print(min(words, key=len))           Output => 'cat'
```

Java ใช้คำสั่ง IntStream.range().min ได้เลยได้

```java
#Java
import java.util.stream.*;

public class Main {
	public static void main(String[] args) {
	int min = IntStream.rangeClosed(1, 10).min().getAsInt();  Output => 1
	   System.out.println(min);
	   String[] words = {"cat", "horse", "dog"};
	   String shortest = java.util.Arrays.stream(words)
    	   .min((a, b) -> Integer.compare(a.length(), b.length()))
    	   .orElse(null);  Output  => "cat"
	   System.out.println(shortest);
    }
}
```

ในภาษา C เราต้องวนลูปเพื่อหาค่าที่น้อยที่สุดและเก็บไว้ในตัวแปร

```c
#C
#include <stdio.h>

int main() {
    int min = 10;

    for (int i = 1; i <= 10; i++) {
        if (i < min)
            min = i;
    }
    printf("Min: %d\n", min);  #Output => 1
    return 0;
}
```

### <kbd>**.minmax**</kbd>

เมธอดนี้ใช้สำหรับการคืนค่าที่มากที่สุดและน้อยที่สุดในเวลาเดียวกัน แต่ในกรณีที่ค่าเริ่มต้น begin มีค่าน้อยกว่า end\
หรือมีค่าเท่ากันจะคืนค่าเป็น nil

```ruby
#Ruby
(1..4).minmax      Output => [1, 4]
(1...4).minmax     Output => [1, 3]
('a'..'d').minmax  Output => ["a", "d"]
(-4..-1).minmax    Output => [-4, -1]

(4..1).minmax      Output => [nil, nil]
(1...1).minmax     Output => [nil, nil]

```

Python สามารถใช้คำสั่ง min(), max() ได้เลย

```python
#Python
r = range(1, 4)
print(min(r), max(r))
```

Java ต้องเขียนเองโดยใช้ IntStream เข้ามาช่วยแยก min, max และเก็บไว้ในตัวแปร

```java
#Java
import java.util.stream.*;
public class Main {
   public static void main(String[] args) {
	IntStream stream = IntStream.range(1, 10);
	int min = stream.min().getAsInt();
	int max = IntStream.range(1, 10).max().getAsInt();
	System.out.println("Min: " + min + ", Max: " + max);
    }
}
```

ภาษา C เราต้องหาค่าเองโดยการวนลูปหาค่าและเก็บไว้ในตัวแปร

<pre class="language-c"><code class="lang-c"><strong>#C
</strong><strong>#include &#x3C;stdio.h>
</strong>
int main() {
    int min = 1000, max = -1000;
    for (int i = 1; i &#x3C; 10; i++) {
        if (i &#x3C; min) min = i;
        if (i > max) max = i;
    }
    printf("Min: %d, Max: %d\n", min, max);
    return 0;
}
</code></pre>

### <kbd>**.size**</kbd>

เมธอดนี้ใช้สำหรับคืนค่าจำนวนสมาชิกภายใน Range แต่ต้องเป็นจำนวนเต็มเท่านั้นไม่สามารถใส่เป็๋นทศนิยมได้และจะคืนค่า nil เมื่อใน Range ไม่ใช้ตัวเลข

{% code overflow="wrap" %}
```ruby
#Ruby
(1..4).size      Output => 4
(1...4).size     Output => 3    
(1..).size       Output => Infinity
('a'..'z').size  Output => nil

(0.5..2.5).size  Error
(..1).size       Error
```
{% endcode %}

Python นั้นไม่มีเมธอด size แต่สามารถใช้ len แทน count ได้เหมือนกัน&#x20;

<pre class="language-python"><code class="lang-python"><strong>#Python
</strong>print(len(range(1, 6)))     Output => 5
print(len(range(1, 5)))     Output => 4
</code></pre>

ใน Java ก็เหมือนกันเราจะใช้เมธอด count แทน

```java
#Java
import java.util.stream.*;
public class Main {
public static void main(String[] args) {
	long count = IntStream.range(1, 6).count();  
	System.out.println(count); Output => 5
    }
}
```

C ก็ใช้วิธีการนับค่าเหมือนกันแต่จะต้องวนรูปหาค่าเอง

<pre class="language-c"><code class="lang-c"><strong>#C ต้องนับแล้วเก็บค่าเอง
</strong><strong>#include &#x3C;stdio.h>
</strong>
int main() {
    int start = 1;
    int end = 4;
    int count = 0;
    for (int i = start; i &#x3C;= end; i++) {
        count++;
    }
    printf("Count: %d\n", count);  Output => 4
    return 0;
}
</code></pre>

### <kbd>**.include?**</kbd>

เมธอดนี้จะใช้สำหรับถามว่าสมาชิกตัวนั้นรวมอยู่ในช่วงนี้จริงไหม

```ruby
#Ruby
("A".."G").include?("Z")     Output => false
(1..5).member?(3)            Output => true
```

ใน Python เราตรวจสอบโดยการใช้  n in range()

```python
#Python
print(3 in range(1, 6))     Output => True
print(5 in range(1, 5))     Output => False
```

Java ต้องเขียน logic เอง

```java
#Java
import java.util.stream.*;
public class Main {
public static void main(String[] args) {
	boolean included = IntStream.rangeClosed(1, 5).anyMatch(x -> x == 3); 
	System.out.println(included);  Output => true
    }
}
```

C ก็ต้องเขียนเองเช่นกัน

```c
#C
#include <stdio.h>

int main() {
    int start = 1, end = 5, value = 3;

    if (value >= start && value <= end) {
        printf("true\n");  // => true
    } else {
        printf("false\n");
    }

    return 0;
}
```

### <kbd>**.inspect**</kbd>

inspect ใช้สำหรับแปลี่ยนค่า object ให้เป็น string

```ruby
#Ruby
(1..5).inspect     Output => "1..5"
(1...5).inspect    Output => "1...5"
```

Python สามารถใช้ repr() หรือ str() ได้เลย

```python
#Python
r = range(1, 6)
print(repr(r))    Output => range(1, 6) #สำหรับ python จะคืนออกมาเป็นชื่อคลาสด้วย
print(str(r))     Output => range(1, 6)
```

Java ใช้ toString ได้เลย

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> range = Arrays.asList(1, 2, 3, 4, 5);
        System.out.println(range.toString());  // => [1, 2, 3, 4, 5]
    }
}
```

### <kbd>**.cover?**</kbd>

เป็นเมธอดที่ใช้ถามว่าค่าที่สนใจนั้นครอบอยู่ในช่วงนี้ไหมและคืนค่าเป็น Boolean

<pre class="language-ruby"><code class="lang-ruby"><strong>#Ruby
</strong><strong>r = (1..4)
</strong>r.cover?(1)     # => true
r.cover?(4)     # => true
r.cover?(0)     # => false
r.cover?(5)     # => false
</code></pre>

Python จะใช้วิธีการในการเขียน logic เอง และ Java ก็ใช้การเขียน logic เองเช่นกัน รวม ถึง C ด้วย

<pre class="language-python"><code class="lang-python"><strong>#Python
</strong>x = 4
print(1 &#x3C;= x &#x3C;= 5)    # True
</code></pre>

<pre class="language-java"><code class="lang-java"><strong>#Java
</strong>import java.util.stream.*;

public class Main {
public static void main(String[] args) {
	int x = 4;
        int start = 1, end = 5;
        if (x >= start &#x26;&#x26; x &#x3C;= end) {
            System.out.println("true"); 
        } else {
            System.out.println("false");
        }
    }
}
</code></pre>

<pre class="language-c"><code class="lang-c"><strong>#C
</strong>#include &#x3C;stdio.h>

int main() {
    int x = 4;
    int start = 1, end = 5;
    if (x >= start &#x26;&#x26; x &#x3C;= end) {
        printf("true"); 
    } else {
        printf("false");
    }
    return 0;
}
</code></pre>

### <kbd>**.eql?**</kbd>

เป็นเมธอดที่ใช้สำหรับการเปรียบเทียบ object สองตัวว่ามีค่าเท่ากันไหม

```ruby
#Ruby
a = Range.new(2, 5, false)
b = Range.new(2, 5, false)
a.eql?(b)  Output => true
```

Python จะใช้วิธีการใช้เครื่องหมาย = ในการถาม

<pre class="language-python"><code class="lang-python"><strong>#Python
</strong>a = 5
b = 5.0
print(type(a) == type(b))    # False type ไม่ตรงกัน
</code></pre>

Java ก็สามารถทำได้เหมือนกัน Ruby โดยการใช้คำสั่ง equal ได้เลย

```java
#Java
import java.util.stream.*;

public class Main {
public static void main(String[] args) {
	Integer a = 5;
        Double b = 5.0;

        System.out.println(a.equals(b));  #Output => false
    }
}
```

## Reference

Ruby

* [https://docs.ruby-lang.org/en/master/Range.html#method-i-3D-3D-3D](https://docs.ruby-lang.org/en/master/Range.html#method-i-3D-3D-3D)
* [https://www.geeksforgeeks.org/ruby/ruby-range-class-methods/](https://www.geeksforgeeks.org/ruby/ruby-range-class-methods/)

Python

* Python Ranges\
  [https://docs.python.org/3/library/stdtypes.html?utm\_source=chatgpt.com#typesseq-range](https://docs.python.org/3/library/stdtypes.html?utm_source=chatgpt.com#typesseq-range)\
  [https://www.programiz.com/python-programming/methods/built-in/range](https://www.programiz.com/python-programming/methods/built-in/range)
* Python str()\
  [https://www.programiz.com/python-programming/methods/built-in/str](https://www.programiz.com/python-programming/methods/built-in/str)
* Python Comparisons\
  [https://www.geeksforgeeks.org/python/relational-operators-in-python/](https://www.geeksforgeeks.org/python/relational-operators-in-python/)

Java

* intStrean in Java\
  [https://neesri.medium.com/primitive-type-in-stream-java-8-fb587f5c1e5b](https://neesri.medium.com/primitive-type-in-stream-java-8-fb587f5c1e5b)
* Java Class Object\
  [https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?utm\_source=chatgpt.com#toString--](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?utm_source=chatgpt.com#toString--)\
  [https://docs.oracle.com/javase/8/docs/api/java/lang/String.html?utm\_source=chatgpt.com#compareTo-java.lang.String-](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html?utm_source=chatgpt.com#compareTo-java.lang.String-)\
  [https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?utm\_source=chatgpt.com#equals-java.lang.Object-](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?utm_source=chatgpt.com#equals-java.lang.Object-)

C

* sprintf() in C\
  [https://www.geeksforgeeks.org/c/sprintf-in-c/](https://www.geeksforgeeks.org/c/sprintf-in-c/)

## Presentation
https://drive.google.com/drive/home


## Video

[^1]: 
