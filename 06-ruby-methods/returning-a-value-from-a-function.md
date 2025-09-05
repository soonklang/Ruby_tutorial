# Returning a Value from a Function

คือ การส่งค่าจากในเมธอดกลับออกมา ซึ่งใน Ruby เมธอดจะส่งค่ากลับเพียง 1 ค่าเสมอ (คือ object หนึ่งตัว) ค่าที่ส่งกลับสามารถเป็น object ใดก็ได้ แม้จะไม่ได้เขียน return ก็จะส่งค่าของบรรทัดสุดท้ายของเมธอดอัตโนมัติ

\*object คือ หน่วยข้อมูลที่เมธอดเรียกทำงานได้ ทุกอย่างใน Ruby เป็น object ทั้งตัวเลข (5), ข้อความ ("Hello"), Array (\[1,2,3]), nil (ย่อมาจาก NilClass หมายถึง ไม่มีค่า,ว่าง)

{% code title="Ruby" %}
```ruby
def say_hello
  "Hello"  

def say_hi
  return "Hi"   
end

def show
  puts "Showing" 
end

puts say_hello 
puts say_hi    
puts show      
```
{% endcode %}


{% code title="Output" lineNumbers="true" %}
```ruby
Hello
Hi
Showing 

```
{% endcode %}

จะเห็นได้ว่าบรรทัดที่ 4 จะพิมพ์บรรทัดว่าง เพราะ คำสั่ง puts จะคืนค่าเป็นค่า nil(บรรทัดว่าง)



{% code title="Ruby" %}
```ruby
def first(a, b, c)
  return a + b + c
  a + b
  c
end

def second(a, b, c)
  return
  a + b + c
  a + b
  c
end

def third(a, b, c)
  a + b + c
  a + b
  c
end

puts first(1, 2, 3)  
puts second(1, 2, 3) 
puts third(1, 2, 3) 
```
{% endcode %}

{% code title="Output" lineNumbers="true" %}
```ruby
6
nil   
3     
```
{% endcode %}

ทำไมใส่ค่า input เหมือนกันแต่ output ไม่เท่ากัน?

&#x20;  เพราะว่าค่าที่ return ออกมาต่างกัน&#x20;

* เมธอด first จะ return ค่าของ a + b + c ออกมา&#x20;
* เมธอด second return ค่า  nil เพราะ ไม่ได้ใส่ค่าอะไรใน return&#x20;
* เมธอด third return ค่าของ c เพราะไม่มีคำสั่ง return  Ruby จะคืนค่าบรรทัดสุดท้ายของเมธอดอัตโนมัติ



{% code title="Ruby" %}
```ruby
def test(a, b)
  ans1 = a / b
  ans2 = a % b
  return ans1, ans2
end

q, r = test(10, 3)
puts q
puts r
```
{% endcode %}

{% code title="Output" %}
```ruby
3
1
```
{% endcode %}

Ruby สามารถ return หลายค่าออกมาแล้วสร้างตัวแปรแต่ละค่าเก็บไว้แยกใช้ได้



เปรียบเทียบกับภาษาอื่นๆ

{% code title="C" %}
```c
#include <stdio.h>

const char* say_hello() {
    return "Hello";  
}

const char* say_hi() {
    return "Hi";    
}

// ฟังก์ชันแบบ void (ไม่มีการคืนค่า)
void show() {
    printf("Showing\n");  
}

int main() {
    printf("%s\n", say_hello()); 
    printf("%s\n", say_hi());  
    show(); 

    return 0; // จบโปรแกรม
}
```
{% endcode %}

{% code title="Output" lineNumbers="true" %}
```c
Hello 
Hi
Showing
```
{% endcode %}



{% code title="Java" %}
```java
public class Main {

    public static String sayHello() {
        return "Hello"; 
    }
    public static String sayHi() {
        return "Hi"; 
    }

    // ฟังก์ชันแบบ void (ไม่มีการคืนค่า)
    public static void show() {
        System.out.println("Showing"); 
    }

    public static void main(String[] args) {
        System.out.println(sayHello());
        System.out.println(sayHi());   
        show();                        

        String result = null;
        System.out.println(result);
    }
}
```
{% endcode %}

{% code title="Output" %}
```
Hello
Hi
Showing
null
```
{% endcode %}

ใน Ruby ถ้าฟังก์ชันไม่มีคำสั่ง return จะคืนค่า nil อัตโนมัติ แต่ใน Java ถ้าฟังก์ชันประกาศเป็น void จะไม่คืนค่าใด ๆ เลยและถ้าต้องการใช้ตัวแปรที่ไม่มีค่า ต้องกำหนดให้เป็น null



{% code title="Python" %}
```python
def say_hello():
    return "Hello"

def say_hi():
    return "Hi"

# ฟังก์ชันที่ไม่คืนค่า (จะคืนค่า None อัตโนมัติ)
def show():
    print("Showing") 
    
# เรียกใช้ฟังก์ชัน
print(say_hello()) 
print(say_hi())     
print(show())      
```
{% endcode %}

{% code title="Output" %}
```python
Hello
Hi
Showing
None
```
{% endcode %}

Python ถ้าไม่มีคำสั่ง return จะคืนค่า None อัตโนมัติ





แหล่งอ้างอิง

*   Ruby Official Docs

    [calling\_methods - Documentation for Ruby 3.5](https://docs.ruby-lang.org/en/master/syntax/calling_methods_rdoc.html)

    ใช้เนื้อหาเกี่ยวกับ syntax ของ method, arguments, return
*   RubyMonstas - Return Values

    [https://ruby-for-beginners.rubymonstas.org/writing\_methods/return\_values.html?utm\_source=chatgpt.com](https://ruby-for-beginners.rubymonstas.org/writing_methods/return_values.html?utm_source=chatgpt.com)

    ใช้เนื้อหาเกี่ยวกับ return value, last evaluated statement(จะคืนค่าบรรทัดคำสั่งสุดท้ายภายในเมธอดเสมอ)
*   Techotopia - Ruby Methods

    [https://www.techotopia.com/index.php/Ruby\_Methods](https://www.techotopia.com/index.php/Ruby_Methods)

    ใช้เนื้อหาเกี่ยวกับ การประกาศเมธอด, return value
*   Microsoft Docs

    [https://learn.microsoft.com/en-us/cpp/c-language/return-statement-c?view=msvc-170\&utm\_source=chatgpt.com](https://learn.microsoft.com/en-us/cpp/c-language/return-statement-c?view=msvc-170\&utm_source=chatgpt.com)

    ใช้เนื้อหาเกี่ยวกับ return ของภาษา C
*   Oracle Java Tutorials

    [https://docs.oracle.com/javase/tutorial/java/javaOO/returnvalue.html?utm\_source=chatgpt.com](https://docs.oracle.com/javase/tutorial/java/javaOO/returnvalue.html?utm_source=chatgpt.com)

    ใช้เนื้อหาเกี่ยวกับ return, เมธอดที่ไม่มีการคืนค่า (void) ของภาษา Java
*   Real Python

    [https://realpython.com/python-return-statement/?utm\_source=chatgpt.com](https://realpython.com/python-return-statement/?utm_source=chatgpt.com)

    ใช้เนื้อหาเกี่ยวกับ return ของภาษา Python

    


\

