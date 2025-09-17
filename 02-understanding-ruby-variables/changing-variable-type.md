# Changing Variable Type

วิธีที่ง่ายที่สุดในการเปลี่ยนชนิดของตัวแปรคือการใส่ค่าใหม่ให้มัน Ruby จะเปลี่ยนตัวแปรนั้นให้ตรงกับค่าที่เราใส่เองโดยอัตโนมัติ ทำให้ตัวแปรสามารถเก็บค่าได้หลายประเภท เช่น จำนวนเต็ม(Integer), ข้อความ(String), อาเรย์(Array) และHash นอกจากนี้ ตัวแปรเดียวกันก็สามารถเก็บค่าแบบทศนิยม (Float) หรือช่วงของตัวเลข (Range) ได้ด้วย 

## ตัวอย่างการเปลี่ยนชนิดตัวแปรในภาษาRuby

### 1.การเปลี่ยนชนิดตัวแปรจาก Integer → String

```ruby
x = 10        // x เป็น Integer
puts x.class  // => Integer

x = "hello"   // เปลี่ยนค่าใหม่เป็น String
puts x.class  // => String

```
- ตอนแรก x เป็นตัวเลข (Integer) แต่พอเราใส่ค่า "hello" แทน Ruby จะเปลี่ยนชนิดของ x ให้เป็น String โดยอัตโนมัติ

### 2.การเปลี่ยนชนิดตัวแปรจาก String → Array
```ruby
str = "Ruby"         // String
puts str.class       // => String

str = ["R", "u", "b", "y"]  // Array
puts str.class       // => Array
```
- ตัวแปร str เปลี่ยนจาก String เป็น Array ได้เลยไม่ต้องแปลงค่าใดๆ เพราะภาษาRuby เป็น Dynamic Typing ซึ่งก็คือตัวแปรเดียวสามารถเก็บค่าชนิดต่างๆ ได้ตามที่เรากำหนด

### 3.การเปลี่ยนชนิดตัวแปรจากArray → Hash
```ruby
arr = [1, 2, 3]               //Array
puts arr.class                //=> Array

arr = { "one" => 1, "two" => 2 }  // Hash
puts arr.class                //=> Hash
```
- ตัวแปรเดียวกันสามารถเก็บ Hash แทน Array ได้เลยทันที

### 4.การเปลี่ยนชนิดตัวแปรจากInteger → Range
```ruby
num = 1                // Integer
puts num.class         // => Integer

num = (1..5)           // Range
puts num.class         // => Range
```
- ตัวแปร num เปลี่ยนจาก Integer เป็น Range เพื่อเก็บช่วงของตัวเลข
### ข้อควรระวัง
- การใช้ตัวแปรที่เปลี่ยนชนิดบ่อยอาจทำให้เกิด TypeError ถ้าเรานำค่าที่ไม่ตรงชนิดมาประมวลผล เช่น "Hello" + 10

## เปรียบเทียบกับภาษา Java / C / Python 
### การเปลี่ยนตัวแปรในภาษาJava
- ตัวอย่าง : ภาษา Java เป็น Static Typing Language ตัวแปรถูกกำหนดชนิดตั้งแต่ประกาศ และไม่สามารถเปลี่ยนเป็นชนิดอื่นได้ ถ้าต้องการเก็บข้อมูลประเภทใหม่ ต้องประกาศตัวแปรใหม่
  ```java
       public class Main {
        public static void main(String[] args) {

        int x = 10;  // x เป็น Integer
        System.out.println("x = " + x);

        // x = "Hello"; 
        // ❌ Error: ไม่สามารถใส่ String ให้กับ int ได้

        String y = "Hello";  // ประกาศตัวแปรใหม่ y เป็น String
        System.out.println("y = " + y);

    } }
**Output:**
 ```
 x = 10
 y = Hello
```
- จากตัวอย่าง ตัวแปร x ที่ประกาศเป็น int ไม่สามารถเปลี่ยนไปเก็บค่าเป็น String ได้ ถ้าต้องการใช้งานข้อมูลประเภทอื่นจะต้องประกาศตัวแปรใหม่
### การเปลี่ยนตัวแปรในภาษา C
- ตัวอย่าง : ภาษาC เป็น Static Typing Language  ทุกตัวแปรจะต้องกำหนดชนิดข้อมูลอย่างชัดเจนตั้งแต่เริ่มต้น และไม่สามารถเปลี่ยนเป็นชนิดข้อมูลอื่นได้โดยตรง
  ```c
    #include <stdio.h>
    int main() {
    int x = 10;          // x เป็นตัวเลขจำนวนเต็ม (Integer)
    printf("x = %d\n", x);

    // x = "Hello";  ❌ Error: ไม่สามารถกำหนด String ให้กับ int ได้

    char y[] = "Hello";  // ประกาศตัวแปรใหม่ y เป็น String
    printf("y = %s\n", y);

    return 0; }
**Output**
 ```
x = 10
y = Hello
 ```
- ตัวแปรที่ประกาศชนิด  int ไม่สามารถเก็บค่าที่เป็นข้อความได้ จะต้องประกาศตัวแปรใหม่ชนิด char[] หรืออื่น ๆ ที่ต้องการใช้
### การเปลี่ยนตัวแปรในภาษา Python
- ตัวอย่าง : ภาษา Python เป็น Dynamic Typing Language ตัวแปรสามารถเปลี่ยนชนิดข้อมูลได้ตามค่าที่ได้รับ โดยไม่ต้องประกาศไว้ก่อน
 ```python
   x = 10
print("x =", x, "| type:", type(x))  # int

x = "Hello"       # เปลี่ยนเป็น String ได้ทันที
print("x =", x, "| type:", type(x))  # str

x = [1, 2, 3]     # เปลี่ยนเป็น List
print("x =", x, "| type:", type(x))  # list
 ```
**Output**
 ```
x = 10 | type: <class 'int'>
x = Hello | type: <class 'str'>
x = [1, 2, 3] | type: <class 'list'>
 ```
- ตัวแปรเดียวกันสามารถเก็บค่าได้หลายชนิด ขึ้นอยู่กับค่าที่เราให้มันในช่วงเวลานั้น ๆ
### ​สรุปเปรียบเทียบภาษา Ruby / Java / C / Python
| ภาษา   | ลักษณะการจัดการตัวแปร                 | การเปลี่ยนชนิดตัวแปร                   |
|--------|------------------------------------|--------------------------------------|
| Ruby   | Dynamic Typing  | เปลี่ยนได้ทันที โดยการกำหนดค่าใหม่       |
| Java  | Static Typing                    | เปลี่ยนไม่ได้ ต้องประกาศตัวแปรใหม่       |
| C    | Static Typing    | เปลี่ยนไม่ได้ ต้องประกาศตัวแปรใหม่       |
| Python     | Dynamic Typing                    | เปลี่ยนได้ทันที โดยการกำหนดค่าใหม่       |
------------
### สรุป
#### ภาษาRuby เป็นDynamic Typing นั่นก็หมายความว่า ตัวแปร ไม่จำเป็นต้องประกาศตัวแปรชนิดข้อมูล่วงหน้า ดังนั้นการเปลี่ยนชนิดตัวแปรในภาษาRuby คือการกำหนดค่าใหม่ให้กับตัวแปร โดยที่Rubyจะปรับชนิดตัวแปรให้ตรงกับชนิดของค่าที่ได้รับโดยอัตโนมัติ และตัวแปรเดียวกันก็ยังสามารถเก็บค่าได้หลากหลายประเภท ทำให้การจัดการข้อมูลมีความยืดหยุ่นสูงและสะดวกต่อการเขียนโปรแกรม
------
### คลิปนำเสนอ
-
------
### Presentation (slides)

---
### Reference 
- Understanding Ruby variables. (2016, October 27). Techotopia.https://www.techotopia.com/index.php/Understanding_Ruby_Variables​
- W3Schools. (n.d.). Ruby numbers. W3Schools. https://www.w3schools.io/ruby-numbers/​
- Ruby Language. (n.d.). Documentation. Ruby-lang.org.https://www.ruby-lang.org/en/documentation/​
- GeeksforGeeks. (2021). Dynamic typing in Python. GeeksforGeeks. https://www.geeksforgeeks.org/python/dynamic-typing-python​
- GeeksforGeeks. (2024). Static variables in C. GeeksforGeeks. https://www.geeksforgeeks.org/c/static-variables-in-c​
- Analytics Vidhya. (2020). Static typing in Java compared to dynamic languages. Medium. https://medium.com/analytics-vidhya/static-typing-in-java-compared-to-dynamic-languages-1e408fc5bc9f​
