# Returning a Value from a Function

คือ การส่งค่าจากในเมธอดกลับออกมา ซึ่งใน Ruby เมธอดจะส่งค่ากลับเพียง 1 ค่าเสมอ (คือ object หนึ่งตัว) ค่าที่ส่งกลับสามารถเป็น object ใดก็ได้ (แม้จะไม่ได้เขียน return ก็จะส่งค่าของบรรทัดสุดท้ายอัตโนมัติ)

\*object คือ หน่วยข้อมูลที่เมธอดเรียกทำงานได้ ทุกอย่างใน Ruby เป็น object ทั้งตัวเลข (5), ข้อความ ("Hello"), Array (\[1,2,3]), nil (ย่อมาจาก NilClass หมายถึง ไม่มีค่า,ว่าง)

{% code title="Ruby" %}
```ruby
def say_hello
  "Hello"   # คืนค่า "Hello"
end

def say_hi
  return "Hi"   # คืนค่า "Hi"
end

def show
  puts "Showing"  # พิมพ์ออก แต่คืนค่าเป็น nil
end

puts say_hello # output=> Hello
puts say_hi     # output=> Hi
puts show      # output=> Showing \n nil

```
{% endcode %}

{% code title="Ruby" %}
```ruby
def first_var_of_sum(a, b, c)
  return a + b + c
  a + b
  c
end

def second_var_of_sum(a, b, c)
  return
  a + b + c
  a + b
  c
end

def third_var_of_sum(a, b, c)
  a + b + c
  a + b
  c
end

puts first_var_of_sum(1, 2, 3)  # => 6
puts second_var_of_sum(1, 2, 3) # => nil (explicit return ไม่มีค่า)
puts third_var_of_sum(1, 2, 3)  # => 3 (implicit return ของบรรทัดสุดท้าย)

```
{% endcode %}

เปรียบเทียบกับภาษาอื่นๆ

{% code title="C" %}
```c
#include <stdio.h>

// ฟังก์ชันคืนค่า string
const char* say_hello() {
    return "Hello";   // คืนค่า "Hello"
}

const char* say_hi() {
    return "Hi";      // คืนค่า "Hi"
}

// ฟังก์ชันแบบ void (ไม่มีการคืนค่า)
void show() {
    printf("Showing\n");  // แค่แสดงข้อความ
}

int main() {
    // เรียกฟังก์ชัน และพิมพ์ค่าที่ได้ออกมา
    printf("%s\n", say_hello()); // แสดง Hello
    printf("%s\n", say_hi());    // แสดง Hi

    show(); // เรียกฟังก์ชัน show → แสดง Showing

    return 0; // จบโปรแกรม
}

```
{% endcode %}

{% code title="Java" %}
```java
public class Main {

    // เมธอดคืนค่า String
    public static String sayHello() {
        return "Hello";   // คืนค่า "Hello"
    }

    public static String sayHi() {
        return "Hi";      // คืนค่า "Hi"
    }

    // เมธอดแบบ void (ไม่มีการคืนค่า)
    public static void show() {
        System.out.println("Showing");  // แค่พิมพ์ข้อความ
    }

    public static void main(String[] args) {
        // เรียกใช้เมธอด และแสดงผล
        System.out.println(sayHello()); // output => Hello
        System.out.println(sayHi());    // output => Hi
        show();                         // output => Showing

        // ใน Ruby ฟังก์ชันที่ไม่คืนค่า จะคืน nil อัตโนมัติ
        // แต่ใน Java ไม่มี concept "nil" → ถ้าอยากเหมือนกัน ใช้ null ได้
        String result = null;
        System.out.println(result);     // output => null
    }
}

```
{% endcode %}

{% code title="Python" %}
```python
# ฟังก์ชันคืนค่า string
def say_hello():
    return "Hello"   # คืนค่า "Hello"

def say_hi():
    return "Hi"      # คืนค่า "Hi"

# ฟังก์ชันที่ไม่คืนค่า (จะคืนค่า None อัตโนมัติ)
def show():
    print("Showing")  # แค่พิมพ์ข้อความออกมา

# เรียกใช้ฟังก์ชัน
print(say_hello())  # output => Hello
print(say_hi())     # output => Hi
print(show())       # output => Showing \n None


```
{% endcode %}

## Declaring and Calling Ruby Method

{% code title="The syntax of a Ruby method" %}
```ruby
def name( arg1, arg2, arg3, ... )
   .. ruby code ..
   return value
end

```
{% endcode %}

* def คือ การประกาศเมธอด
* name คือ ชื่อเมธอด ใช้เรียกใช้งานเมธอดนั้น
* arg1, arg2, ... → arguments  คือ ค่าที่ถูกส่งเข้าไปในฟังก์ชันเพื่อประมวณผล
* ruby code คือ ส่วนของเนื้อหาการทำงานในเมธอด
* return value คือ การส่งค่ากลับไปยังโค้ดที่เรียกใช้เมธอด (ถ้าไม่ใส่ return เมธอดจะคืนค่าบรรทัดสุดท้าย)
*   end คือ ปิดการประกาศเมธอด (ถ้าไม่ใส่จะทำให้รันไม่ได้ เพราะ Ruby ไม่รู้ว่าเมธอดจบตรงไหน)

    \
    ตัวอย่าง 1 :

{% code title="Ruby" %}
```ruby
def saysomething()
    "Hello"   # คืนค่า "Hello"
end

puts saysomething  # => Hello
```
{% endcode %}

{% code title="" %}
```ruby
def geeks
  puts "Welcome to GFG portal"
end

geeks #output => Welcome to GFG portal

```
{% endcode %}

เปรียบเทียบกับภาษาอื่นๆ

{% code title="C" %}
```c
#include <stdio.h>

// ฟังก์ชันคืนค่า string
const char* saysomething() {
    return "Hello";  // คืนค่า "Hello"
}

int main() {
    printf("%s\n", saysomething()); // => Hello
    return 0;
}

```
{% endcode %}

{% code title="Java" %}
```java
public class Main {
    // เมธอดคืนค่า String
    static String saysomething() {
        return "Hello";  // คืนค่า "Hello"
    }

    public static void main(String[] args) {
        System.out.println(saysomething()); // => Hello
    }
}

```
{% endcode %}

{% code title="Python" %}
```python
# ฟังก์ชันคืนค่า string
def saysomething():
    return "Hello"  # คืนค่า "Hello"

print(saysomething())  # => Hello

```
{% endcode %}

## Passing Arguments to a Method

การส่งค่า arguments เข้าไปยังเมธอด จากตัวอย่าง 1 จะยังไม่มีการส่งค่าใด ๆ เข้ากับเมธอด แต่โดยทั่วไปแล้ว เมธอดมักถูกออกแบบให้ทำงานกับค่าที่ส่งเข้ามา ดังเช่นตัวอย่างต่อไปนี้

ตัวอย่าง 2:

{% code title="Ruby" %}
```ruby
def multiply(val1, val2)
    result = val1 * val2
    puts result
end

# เรียกใช้งานเมธอดหลายครั้ง
multiply(2, 10)   # output=> 20
multiply(4, 20)   # output=> 80
multiply(6, 7)    # output=> 42

```
{% endcode %}

* (val1, val2) คือ arguments คือค่าที่ส่งเข้ามาในเมธอดเพื่อใช้คำนวณ
* def multiply คือ การประกาศเมธอดชื่อ multiply&#x20;
* result = val1 \* val2 คือ  การคำนวณผลคูณของ val1 และ val2 แล้วเก็บในตัวแปร result
* puts result คือ แสดงผลลัพธ์ออกหน้าจอ
* end คือ ปิดการประกาศเมธอด
*   การเรียก multiply(...) หลายครั้ง → ใช้เมธอดซ้ำ ๆ ไม่ต้องเขียนโค้ดซ้ำหลายบรรทัด

    \


    จะเห็นได้ว่าถ้าไม่ใช้เมธอด จะต้องเขียนโค้ดซ้ำถึง 3 ครั้ง แต่การเขียนโค้ดไว้ในเมธอดแล้วเรียกใช้งานซ้ำ ๆ จะช่วย ประหยัดเวลา และ เพิ่มประสิทธิภาพ ของโค้ด

    \


<pre class="language-ruby" data-title="Ruby"><code class="lang-ruby"><strong>def add_one(value)
</strong>  value + 1
end

def add_one(a, b = 1)
  a + b
end

puts add_one(5) # output=> 6
puts add_one(5, 10) # output=> 15

</code></pre>

เปรียบเทียบกับภาษาอื่นๆ

{% code title="C" %}
```c
#include <stdio.h>

// ฟังก์ชันแบบ void ไม่คืนค่า
void multiply(int val1, int val2) {
    int result = val1 * val2;
    printf("%d\n", result);
}

int main() {
    multiply(2, 10);  // => 20
    multiply(4, 20);  // => 80
    return 0;
}

```
{% endcode %}

{% code title="Java" %}
```java
public class Main {
    // เมธอดแบบ void ไม่คืนค่า
    static void multiply(int val1, int val2) {
        int result = val1 * val2;
        System.out.println(result);
    }

    public static void main(String[] args) {
        multiply(2, 10);  // => 20
        multiply(4, 20);  // => 80
    }
}

```
{% endcode %}

{% code title="Python" %}
```python
def multiply(val1, val2):
    result = val1 * val2
    print(result)

# เรียกใช้งาน
multiply(2, 10)   # => 20
multiply(4, 20)   # => 80

```
{% endcode %}

## Passing a Variable Number of Arguments to a Method

การส่งจำนวน arguments ที่ไม่แน่นอนเข้าไปยังเมธอด ในตัวอย่างที่ 2 เป็นการกำหนดจำนวน arguments คงที่ที่เมธอดได้รับ แต่บางครั้งเราไม่รู้ว่าจะต้องใช้ arguments กี่ตัว&#x20;

Ruby แก้ปัญหานี้โดยใช้ \*args เมื่อประกาศเมธอด arguments ที่ส่งเข้าเมธอดจะถูกเก็บไว้ใน Array

{% code title="Ruby" %}
```ruby
def displaystrings(*args)
  args.each do |item|
    puts item
  end
end

# เรียกใช้งานเมธอด
displaystrings("Red")
# output=> Red

displaystrings("Red", "Green", "Blue")
# output=> Red
# Green
# Blue

```
{% endcode %}

args.each do |item| ... end

* do ... end ใช้เหมือน { ... }
* .each ใช้เพื่อวนลูปทีละค่าใน array args
*   |item| คือ ตัวแปรแทนค่าของสมาชิกหนึ่งตัว (element) ของ array ในแต่ละรอบ

    \


เปรียบเทียบกับภาษาอื่นๆ

{% code title="C" %}
```c
#include <stdio.h>
#include <stdarg.h>

void displaystrings(int count, ...) {
    va_list args;
    va_start(args, count);

    for (int i = 0; i < count; i++) {
        const char* item = va_arg(args, const char*);
        printf("%s\n", item);
    }

    va_end(args);
}

int main() {
    displaystrings(1, "Red");                     // => Red
    displaystrings(3, "Red", "Green", "Blue");    // => Red \n Green \n Blue
    return 0;
}

```
{% endcode %}

{% code title="Java" %}
```java
public class Main {
    static void displaystrings(String... args) {
        for (String item : args) {
            System.out.println(item);
        }
    }

    public static void main(String[] args) {
        displaystrings("Red");                     // => Red
        displaystrings("Red", "Green", "Blue");    // => Red \n Green \n Blue
    }
}

```
{% endcode %}

{% code title="Python" %}
```python
def displaystrings(*args):
    for item in args:
        print(item)

displaystrings("Red")                 # => Red
displaystrings("Red", "Green", "Blue")
# => Red
# => Green
# => Blue

```
{% endcode %}

## Returning a Value from a Function

การส่งค่ากลับจากเมธอด โดยใช้ return

{% code title="Ruby" %}
```ruby
def multiply(val1, val2)
  result = val1 * val2
  return result
end

value = multiply(10, 20)
puts value
# output=> 200

```
{% endcode %}

* &#x20;return result คือ การส่งค่าที่เก็บไว้ใน result ออกมา
* value = multiply(10, 20) คือ การเรียกใช้เมธอด multiply แล้วส่งค่า  10 และ 20 เข้าไปในเมธอด แล้วเก็บค่าที่ส่งกลับไว้ในตัวแปร value



เปรียบเทียบกับภาษาอื่นๆ

{% code title="C" %}
```c
#include <stdio.h>

// ฟังก์ชันคืนค่า int
int multiply(int val1, int val2) {
    int result = val1 * val2;
    return result;
}

int main() {
    int value = multiply(10, 20);
    printf("%d\n", value);  // => 200
    return 0;
}

```
{% endcode %}

{% code title="Java" %}
```java
public class Main {
    // เมธอดคืนค่า int
    static int multiply(int val1, int val2) {
        int result = val1 * val2;
        return result;
    }

    public static void main(String[] args) {
        int value = multiply(10, 20);
        System.out.println(value);  // => 200
    }
}

```
{% endcode %}

{% code title="Python" %}
```python
def multiply(val1, val2):
    result = val1 * val2
    return result

value = multiply(10, 20)
print(value)  # => 200


```
{% endcode %}

## Ruby Method Aliases

การสร้างชื่อเรียกสำรองให้เมธอดใน Ruby คือ การสร้างชื่อเรียกสำรองของเมธอด โดยทั้งชื่อเดิมและชื่อใหม่จะเรียกใช้เมธอดเดียวกัน&#x20;



ทำไมถึงต้องมีชื่อสำรอง ?

เพราะ ในบางครั้งเมธอดอาจต้องใช้ชื่่อเรียกแบบอื่นเพื่อให้อ่านเข้าใจได้ง่ายกว่าแต่การทำงานภายในยังเหมือนเดิม Alias จึงเป็นคำสั่งที่ช่วยให้ไม่ต้องทำสำเนาโค้ดซ้ำเพื่อเปลี่ยนชื่อเรียก และลดการทำงานซ้ำของโค้ด



{% code title="Syntax" %}
```ruby
alias nename old_name
alias :new_name :old_name

```
{% endcode %}

<pre class="language-ruby" data-title="Ruby"><code class="lang-ruby">def multiply(val1, val2)
<strong>  result = val1 * val2
</strong>  return result
end

alias docalc multiply  # สร้าง alias ชื่อ docalc ให้เรียกเมธอด multiply ได้

docalc(10, 20)
# output=> 200

multiply(10, 20)
# output=> 200

</code></pre>



เปรียบเทียบกับภาษาอื่นๆ

{% code title="C" %}
```c
#include <stdio.h>

// ฟังก์ชัน multiply
int multiply(int val1, int val2) {
    return val1 * val2;
}

// สร้าง alias ด้วย pointer
int (*docalc)(int, int) = multiply;

int main() {
    printf("%d\n", docalc(10, 20));   // => 200
    printf("%d\n", multiply(10, 20)); // => 200
    return 0;
}

```
{% endcode %}

{% code title="Java" %}
```java
public class Main {

    static int multiply(int val1, int val2) {
        return val1 * val2;
    }

    // สร้าง alias โดยให้เรียก multiply
    static int docalc(int val1, int val2) {
        return multiply(val1, val2);
    }

    public static void main(String[] args) {
        System.out.println(docalc(10, 20));   // => 200
        System.out.println(multiply(10, 20)); // => 200
    }
}

```
{% endcode %}

{% code title="Python" %}
```python
def multiply(val1, val2):
    return val1 * val2

# สร้าง alias
docalc = multiply

print(docalc(10, 20))   # => 200
print(multiply(10, 20)) # => 200


```
{% endcode %}

แหล่งอ้างอิง

*   Ruby Official Docs

    [calling\_methods - Documentation for Ruby 3.5](https://docs.ruby-lang.org/en/master/syntax/calling_methods_rdoc.html)

    ใช้เนื้อหาเกี่ยวกับ syntax ของ method, arguments, return
*   RubyMonstas - Return Values

    [https://ruby-for-beginners.rubymonstas.org/writing\_methods/return\_values.html?utm\_source=chatgpt.com](https://ruby-for-beginners.rubymonstas.org/writing_methods/return_values.html?utm_source=chatgpt.com)

    ใช้เนื้อหาเกี่ยวกับ return value, last evaluated statement(จะคืนค่าบรรทัดคำสั่งสุดท้ายภายในเมธอดเสมอ)
*   Techotopia - Ruby Methods

    [https://www.techotopia.com/index.php/Ruby\_Methods](https://www.techotopia.com/index.php/Ruby_Methods)

    ใช้เนื้อหาเกี่ยวกับ การประกาศเมธอด, การส่ง arguments, return value, alias

\
