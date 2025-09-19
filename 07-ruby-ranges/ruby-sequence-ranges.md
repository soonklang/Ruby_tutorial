# Ruby Sequence Ranges
คือการสร้างช่วงที่เป็นลำดับของค่าที่ต่อเนื่องกัน โดยจะมีการกำหนดค่าเริ่มต้นและค่าสิ้นสุด ซึ่งค่าที่กำหนดนั้นเป็นได้ทั้ง ตัวเลข อักขระ strings หรือobjects ต่างๆ ค่าที่แสดงออกมาจะเป็นค่าที่อยู่ในเฉพาะช่วงที่กำหนด แต่ค่าสิ้นสุดที่แสดงออกมาจะแตกต่างกันขึ้นอยู่กับรูปแบบที่เราสร้าง 

### การสร้างช่วงของ Ranges ใน Ruby มี 2 แบบ 
#### แบบที่ 1 ใช้ (..) คั่นระหว่างค่าเริ่มต้นและค่าสิ้นสุด จะแสดงค่าตั้งแต่ค่าเริ่มต้น - ค่าสิ้นสุด 
```
ตัวอย่าง

  (1..10).to_a => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]     #แปลง Ranges เป็น Array

  ('A'..'F').to_a => ["A", "B", "C", "D", "E", "F"]   #สร้างช่วงตามอักขระ

  ('bar'..'bat').to_a => ["bar", "bas", "bat"]        #สร้างช่วงตามค่าstrings
```
```
ตัวอย่าง

myrange = 4..8                                    #กำหนด Ranges

maxv = myrange.max                                #ใช้เมธอด .max หาค่ามากที่สุดใน Ranges
puts "Maximum value from range = #{maxv}"         #ใช้ puts แสดงผลข้อความ และ ใช้ #{maxv} คือ string interpolation แทนค่า maxv ลงใน string

minv = myrange.min                                #ใช้เมธอด .min หาค่าน้อยที่สุดใน Ranges
puts "Minimum value from range = #{minv}"         #ใช้ puts แสดงผลข้อความ และ ใช้ #{minv} คือ string interpolation แทนค่า minv ลงใน string

ผลลัพธ์
Maximum value from range = 8
Minimum value from range = 4
```


#### แบบที่ 2 ใช้(...) คั่นระหว่างค่าเริ่มต้นและค่าสิ้นสุด จะแสดงค่าตั้งแต่ค่าเริ่มต้น - ค่าก่อนค่าสิ้นสุด
```
ตัวอย่าง

(1...10).to_a => [1, 2, 3, 4, 5, 6, 7, 8, 9]      #แปลง Ranges เป็น Array

('A'...'F').to_a => ["A", "B", "C", "D", "E"]     #สร้างช่วงตามอักขระ

('bar'..'bat').to_a => ["bar", "bas"]             #สร้างช่วงตามค่าstring
```
```
ตัวอย่าง

myrange = 4...8                                  #กำหนด Ranges

maxv = myrange.max                               #ใช้เมธอด .max หาค่ามากที่สุดใน Ranges
puts "Maximum value from range = #{maxv}"        #ใช้ puts แสดงผลข้อความ และ ใช้ #{maxv} คือ string interpolation แทนค่า maxv ลงใน string

minv = myrange.min                               #ใช้เมธอด .min หาค่าน้อยที่สุดใน Ranges
puts "Minimum value from range = #{minv}"        #ใช้ puts แสดงผลข้อความ และ ใช้ #{minv} คือ string interpolation แทนค่า minv ลงใน string

ผลลัพธ์
Maximum value from range = 7
Minimum value from range = 4
```

#### ถ้าใช้ Object ใน Range 
```
  - ต้องรู้ว่าค่าต่อไปคือค่าอะไรผ่าน เมธอด succ
  - ต้องสามารถเปรียบเทียบค่าของ Object ใน Range โดยใช้ <=> ได้
```

### Beginless Ranges ช่วงที่ไม่มีค่าเริ่มต้น แต่มีค่าสิ้นสุด 
    -  nil ที่แสดงออกมาจากผลลัพธ์  เพราะไม่มีค่าเริ่มต้นที่กำหนดไว้
    - ค่าเริ่มต้นที่สามารถเป็นค่าอะไรก็ได้ทุกค่าที่น้อยกว่าหรือเท่ากับค่าสิ้นสุดที่กำหนด สำหรับรูปแบบ (..)
    - ค่าเริ่มต้นที่สามารถเป็นค่าอะไรก็ได้ทุกค่าที่น้อยกว่าค่าสิ้นสุดที่กำหนด สำหรับรูปแบบ (...)
```
ตัวอย่าง

r = (..4)                => nil..4    # ค่าเริ่มต้นไม่ได้กำหนด , ค่าสิ้นสุดเป็น 4
r.begin                  => nil       # ค่าเริ่มต้นเป็น nil เพื่อสื่อว่าไม่ได้กำหนดค่าเริ่มต้นแน่นอน
r.end                    => 4         # ค่าสิ้นสุดเป็น 4
r.include?(-50)          => true      # ใช้ เมธอด  include? เช็คว่าค่านั้นอยู่ใน Ranges หรือไม่ ผลลัพธ์ออกมาเป็น true เพราะ -50 มีค่าน้อยกว่า 4 ที่เป็นค่าสิ้นสุด
r.include?(4)            => true      # ผลลัพธ์ออกมาเป็น true เพราะ 4 มีค่าเท่ากับ 4 ที่เป็นค่าสิ้นสุด

r = (...4)               => nil...4   # ค่าเริ่มต้นไม่ได้กำหนด , ค่าสิ้นสุดเป็น 4
r.include?(4)            => false     # ผลลัพธ์ออกมาเป็น false เพราะใช้รูปแบบ (...) ต้องเป็นค่าที่น้อยกว่าค่าสิ้นสุดที่กำหนด

Range.new(nil, 4)        => nil..4    # ใช้สร้าง Beginless Ranges สำหรับรูปแบบ (..)
Range.new(nil, 4, true)  => nil...4   # ใช้สร้าง Beginless Ranges สำหรับรูปแบบ (...)

```

#### Beginless range สามารถใช้กับช่วงของ array ได้

```
 ตัวอย่าง
    a = [1, 2, 3, 4]                       # สร้าง array
    r = (..2)               => nil..2      # กำหนดช่วงแบบ beginless ใช้(..) มี index  0 - 2
    a[r]                    => [1, 2, 3]   # index 0 ค่า = 1 , index 1 ค่า = 2 , index 2 ค่า = 3 
    r = (...2)              => nil...2     # กำหนดช่วงแบบ beginless ใช้(...) มี index  0 - 2
    a[r]                    => [1, 2]      # index 0 ค่า = 1 , index 1 ค่า = 2
```
#### หมายเหตุ Beginless ไม่สามารถใช้กับ เมธอด .each ได้

### Endless Ranges ช่วงที่มีค่าเริ่มต้น แต่ไม่มีค่าสิ้นสุด 
    ไม่มีค่าสิ้นสุดโดยเป็นได้ทุกค่าที่มากกว่าหรือเท่ากับค่าเริ่มต้นที่กำหนด ทั้งรูปแบบ (..) และ (...)

   
```

ตัวอย่าง
    r = (1..)            => 1..
    r.end                => nil
    r.include?(50)       => true
    Range.new(1, nil)    => 1..

```
#### Endless range สามารถใช้กับช่วงของ array ได้
```
 ตัวอย่าง
    a = [1, 2, 3, 4]
    r = (2..)               => 2..
    a[r]                    => [3, 4]
```

#### Endless range สามารถใช้เมธอด .each ได้ 
```
    a = []
    r = (1..)
    r.each do |i|
      a.push(i) if i.even?
      break if i > 10
    end
    a                              => [2, 4, 6, 8, 10]
```
#### ถ้าช่วงเป็น beginless และ endless
```
จะต้องระบุ nil
ตัวอย่าง
    (nil..)         => (nil..nil)
    (..nil)         => (nil..nil)
    (nil..nil)      => (nil..nil)

    r = (nil..nil)
    r.include?(100)      => true
    r.include?(-999)     => true
```

    
## เปรียบเทียบกับภาษา Java/C/Python
### ภาษา Java
Range เมธอดใน Java ใช้คลาส  IntStream (32 บิต) หรือ LongStream (64 บิต) ใช้พารามิเตอร์ของฟังก์ชันระบุช่วงลำดับ มี 2 พารามิเตอร์ คือ startInclusive(รวมค่าเริ่มต้น)  และ endExclusive (ไม่รวมค่าเริ่มต้น) โดยใช้ เมธอด range() หรือ rangeClosed() หาค่าช่วงลำดับที่ต้องการ

### range

เมธอดที่เริ่มจากค่าเริ่มต้นไม่รวมค่าสุดท้าย

ตัวอย่าง

```java
// IntStream range implementation using Java
import java.util.*;
//import the package for IntStream
import java.util.stream.IntStream;
public class RangeExample {
// main method
public static void main(String[] args)
{
// Create an IntStream
IntStream st = IntStream.range(32, 45);
// Display the elements in the range mentioned as 32 and 45 where 32 is included and 45 is excluded
System.out.println("The elements are:");
st.forEach(System.out::println);
} }
ผลลัพธ์
The elements are:
32  
33  
34  
35  
36  
37  
38  
39  
40  
41  
42  
43  
44
```
ตัวอย่าง  LongStream
```java
// LongStream range implementation using Java
import java.util.*;
//import the package for LongStream
import java.util.stream.LongStream;
public class RangeExample {
// main method
public static void main(String[] args)
{
// Create a LongStream
LongStream st = LongStream.range(1000001L, 1000010L);
// Display the elements in the range mentioned as 1000001L and 1000010L where 1000001L is included and 1000010L is excluded
System.out.println("The elements are:");
st.forEach(System.out::println);
} }
ผลลัพธ์
The elements are:
1000001  
1000002  
1000003  
1000004  
1000005  
1000006  
1000007  
1000008  
1000009 
```
Java ใช้คนละเมธอดในการเลือกรวมหรือไม่รวมตัวสุดท้าย ในการใช้คลาสต้องนำเข้าแพคเกจ และJava ไม่มี built-in อาจต้องใช้ loop หรือสร้างเงื่อนไข

### rangeClosed 

เมธอดที่เริ่มจากค่าเริ่มต้นไปจนถึงค่าสุดท้าย

ตัวอย่าง

```java
package com.javabrahman.java8.streams;
import java.util.stream.IntStream;
import java.util.stream.LongStream;
public class RangeNRangeClosedExample {

  public static void main(String args[]){
    //IntStream.range() and IntStream.rangeClosed() examples
    System.out.println("Using IntStream.range() & IntStream.rangeClosed()");
    IntStream.range(1, 10).forEach(i -> System.out.print(i + " "));
    System.out.println();
    IntStream.rangeClosed(1, 10).forEach(i -> System.out.print(i + " "));
    
    //LongStream.range() and LongStream.rangeClosed() examples    
    System.out.println("\n Using LongStream.range() & LongStream.rangeClosed()");
    LongStream.range(1000000L, 1000005L).forEach(i -> System.out.print(i + " "));
    System.out.println();
    LongStream.rangeClosed(1000000L, 1000005L).forEach(i -> System.out.print(i + " "));
  }
}
```
ผลลัพธ์

<img width="581" height="203" alt="Screenshot 2025-09-04 214319" src="https://github.com/user-attachments/assets/ee4ecba3-6f29-4cf4-8d72-cff8e074ab51" />


### ภาษา Python
Range ใน Python จะต้องใช้ loop เพื่อแสดงผล กำหนดค่าเริ่มต้น และค่าสุดท้าย โดยใช้ for i in range(start,end) แต่ผลลัพธ์ที่ออกมาจะเริ่มต้นที่ตัวแรกแต่ไม่รวมค่าสุดท้าย ถ้าอยากได้ค่าสุดท้ายต้องนำค่าสุดท้ายไป +1 
```python
for i in range(5, 20):
    print(i, end=" ")
ผลลัพธ์
5 6 7 8 9 10 11 12 13 14 15 16 17 18 19
```

```python
fruits = ["apple", "banana", "cherry", "date"]

for i in range(len(fruits)):
    print(fruits[i])
ผลลัพธ์
apple
banana
cherry
date
```
### ภาษา C 
ใน ภาษา C ไม่มี Range แบบกำหนดค่าเริ่มต้นสิ้นสุดได้เหมือน Ruby แต่สามารถใช้ loop  ในการค้นหาช่วงทั้งหมดได้เหมือนกัน
```C
include <stdio.h>

int main() {
  int i = 0;
  
  while (i < 5) {
    printf("%d\n", i);
    i++;
  }
  
  return 0;
}
ผลลัพธ์
0
1
2
3
4
```

## อ้างอิง
### Ruby
class Range , Beginless Ranges , Endless Ranges (เนื้อหา, ตัวอย่าง)

https://docs.ruby-lang.org/en/3.4/Range.html?utm_source=chatgpt.com

Github : the-best-ruby-books/books/The Ruby Programming Language.pdf (เนื้อหา Ranges หน้าที่ 68-69)

https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/The%20Ruby%20Programming%20Language.pdf

Ranges as Sequences (ตัวอย่าง)

https://www.includehelp.com/ruby/ranges.aspx?utm_source=chatgpt.com

Ruby - Ranges (เนื้อหา, ตัวอย่าง)

https://www.tutorialspoint.com/ruby/ruby_ranges.htm

Ruby Ranges (หัวข้อ, เนื้อหา, ตัวอย่าง)

https://www.techotopia.com/index.php/Ruby_Ranges

Beginless Ranges , Endless Ranges (ตัวอย่าง)

https://rubyapi.org/3.4/o/range?utm_source=chatgpt.com

### Java
Range in Java (เนื้อหา, ตัวอย่าง)

https://www.educba.com/range-in-java/

IntStream range (เนื้อหา)

https://docs.oracle.com/javase/8/docs/api/java/util/stream/IntStream.html

IntStream rangeClosed() method in Java (เนื้อหา)

https://www.tutorialspoint.com/intstream-rangeclosed-method-in-java

How to use range() and rangeClosed() methods (เนื้อหา, ตัวอย่าง)

https://www.javabrahman.com/java-8/java-8-how-to-use-range-rangeclosed-methods-of-intstream-longstream-with-examples/

### Python
Python range() Function (เนื้อหา, ตัวอย่าง)

https://python.land/deep-dives/python-range 

Python range() function (ตัวอย่าง)

https://www.geeksforgeeks.org/python/python-range-function/

### C 
C Do/While Loop (เนื้อหา, ตัวอย่าง)

https://www.w3schools.com/c/c_do_while_loop.php





