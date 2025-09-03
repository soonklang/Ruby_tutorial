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



แหล่งอ้างอิง

*   Ruby Official Docs

    [calling\_methods - Documentation for Ruby 3.5](https://docs.ruby-lang.org/en/master/syntax/calling_methods_rdoc.html)

    ใช้เนื้อหาเกี่ยวกับ syntax ของ method, arguments, return
*   RubyMonstas - Return Values

    [https://ruby-for-beginners.rubymonstas.org/writing\_methods/return\_values.html?utm\_source=chatgpt.com](https://ruby-for-beginners.rubymonstas.org/writing_methods/return_values.html?utm_source=chatgpt.com)

    ใช้เนื้อหาเกี่ยวกับ return value, last evaluated statement(จะคืนค่าบรรทัดคำสั่งสุดท้ายภายในเมธอดเสมอ)
*   Techotopia - Ruby Methods

    [https://www.techotopia.com/index.php/Ruby\_Methods](https://www.techotopia.com/index.php/Ruby_Methods)

    ใช้เนื้อหาเกี่ยวกับ การประกาศเมธอด, การส่ง arguments, return value

\
