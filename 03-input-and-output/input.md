# Input
Input คือ ข้อมูลที่โปรแกรมเรารับเข้ามาซึ่งในแต่ละภาษาก็มีวิธีการรับเข้าที่หลากหลาย

รวมถึงภาษา Ruby ที่เรากำลังจะพูดถึงกันในบทความนี้ด้วย ก็มีการนำเข้า Input ที่หลากหลาย

แต่บทความนี้เราจะพูดถึงวิธีการง่ายๆ นั้นก็คือ gets นั่นเอง

gets คืออะไร ทำงานยังไง จะเป็นยังไงก็มาดูกันได้เลย

# gets
พูดสั้นๆให้ได้ใจความก็คือ การรับค่าเข้าแล้วเว้นบรรณทัดเลย ก็คือจะมีการ \n ตามหลัง
ลองมาดูตัวอย่างดีกว่า
```Ruby
print "โปรดใส่ชื่อ: "
name = gets
puts "สวัสดี #{name}!"
```
ถ้าเราใส่ Input ว่า "สุดหล่อ" ผลลัพธ์ ก็คือ
```Ruby
โปรดใส่ชื่อ: สุดหล่อ
สวัสดี สุดหล่อ
!
```
เห็นไหมว่า "!" ก็จะเว้นบรรทัดมาอยู่ข้างล่างเฉยเลย เพราะ gets จะเติม \n ตามหลัง Input นั้นเอง

แล้วทำไงให้ "!" ไปอยู่ข้างบนอะ ก็ต้องใช้วิธีต่อไปนี้ไงล่ะ!!!

# chomp
ผู้เขียนรู้ว่าอธิบายละเอียดไปก็ไม่มีใครจำได้อยู่ ใครจะไปจำรายละเอียดย่อยๆเนอะ 

เข้าเรื่องกันดีกว่า chomp คือ หนึ่งใน Method ของ Ruby ที่จะทำการตัด \n หรือ \r\n 

เพื่อความสวยงามในการแสดงผล(สำหรับบางคน)

```Ruby
print "โปรดใช่ชื่อ:"
name = gets
puts "สวัสดี #{name}!"
```
อิงจากตัวอย่างข้างบน ผลลัพธ์ก็จะเป็นแบบก่อนหน้า
```Ruby
print "โปรดใช่ชื่อ:"
name = gets.chomp #<- รอบนี้เติม .chomp เข้ามา
puts "สวัสดี #{name}!"
```
ใส่ชื่อ "สุดหล่อ" เหมือนเดิม ก็จะได้ผลลัพธ์แบบนี้!!
```Ruby
โปรดใส่ชื่อ: สุดหล่อ
สวัสดี สุดหล่อ!
```
ก็จะสรุปได้ว่า gets นั้นคือการรับเข้าข้อมูลหรือ input โคยจะมาในรูปแบบ input\n

และ chomp คือ Method ที่จะทำการตัด \n ทิ้งเพื่อให้ Input ดูสะอาดขึ้นนั้นเอง

# การเปรียบระหว่าง Java, C, Python
คือตัว Ruby ก็ไม่ใช่ภาษาใหม่อะไร เปิดตัวปี 1995 รุ่นราวคราวเดียวกับ Java

งั้นเรามาลองเปรียบเทียบดีกว่าว่าใน ภาษา Java, C, Python เนี่ยมีการรับข้อมูลที่เหมือนหรือแตกต่างกับ Ruby ยังไง

# Java
ถูกสร้างมาในปีเดียวกัน แต่วิธีรับข้อมูลไม่เหมือนกัน ซึ่งการรับข้อมูลของ Java ก็จะเป็นที่รู้กันดีกว่าต้องใช้ คลาส

นั้นก็คือ คลาส Scanner นั่นเอง โดยจะมี Method nextLine() ที่จะตัด \n ออกให้อัตโนมัติ

มาดูตัวอย่างกันรูปแบบการรับ input ของ java กัน

```Java
import java.util.Scanner;

public class InputExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine();
        System.out.println(input);
    }
}
```

# C
เป็นภาษาที่เก่าที่ในทั้ง 4 ภาษาที่เราพูดถึงในบทความนี้ 1972 อย่างเก่าอะบอกเลย

การรับเข้า Input ที่เรารู้จักกันดีก็คือ scanf นั้นเอง

โดยที่การรับเข้านั้นจะไม่สามารถรับอะไรแบบตรงๆได้เลย เช่น ถ้าจะรับสตริงก็จะต้องประกาศ array ก่อน

ต่างจากตัวเลขที่รับได้เลยตรงๆ ไหนจะ เวลาป้อนค่าสตริง ถ้าเกิดมีการกด spacebar ก็จะจบตรงนั้นอีก

เช่น Hey handsome พอ printf ออกมา ก็จะมาแค่ Hey อีก จริงๆมันก็มีวิธีแก้แต่ไม่ใช่ในบทความนี้อะนะ

เรามาดูตัวอย่างกันดีกว่า

```C
#include <stdio.h>

int main() {
    char name[100];
    printf("ใส่ชื่อตรงนี้จ้า: ");
    scanf("%99s", name); // รับจนกว่าจะเจอ space, tab, หรือ newline
    printf("สวัสดีจ้า %s!\n", name);
    return 0;
}
```
นี้คือตัวอย่างของการรับ String

```C
#include <stdio.h>

int main() {
    int age;
    float salary;

    printf("Enter your age: ");
    scanf("%d", &age);           // รับค่าเป็น int

    printf("Enter your salary: ");
    scanf("%f", &salary);        // รับค่าเป็น float

    printf("Age: %d, Salary: %.2f\n", age, salary);
    return 0;
}
```
และนี้คือตัวอย่างของการรับ integer และ float

จะเห็นว่ามีขั้นตอนและจำนวนบรรทัดที่เยอะมากๆ ด้วยความที่เป็นภาษาที่เก่าที่สุดอะนะ

# Python
มาถึงภาษาสุดท้ายในการเปรียบเทียบในบทความนี้ เป็นภาษาที่เก่าที่สุดเป็นอันดับ 2 สร้างขึ้นในปี 1991

ซึ่งภาษานี้การรับ Input นั้นเข้าใจง่ายที่สุดในทั้งหมด จากความคิดของผู้เขียนบทความ

เพราะว่าแค่ input() ก็รับค่าได้แล้ว แต่ค่าที่ได้มาจะเป็น String

ถ้าอยากได้ค่า integer หรือ float จะต้องทำ type casting หรือแปลงข้อมูลนั้นเอง

เรามาดูตัวอย่างคร่าวๆกันดีกว่า

```Python
text = input("Enter something: ")
print(type(text))  
```
วิธีนี้ตัวโค้ดจะประเภทของค่าที่รับเข้ามา ซึ่งในตัวอย่างก็คือ 'str' หรือ string นั้นเอง

```Python
text = int(input("Enter something: "))
print(type(text))  
```
และนี้คือการแปลงค่าให้เป็น integer 

# ตารางเปรียบเทียบ

| ภาษา | คำสั่งรับ Input | การทำงาน | การลบ\n |
|------|-------------------|-------------------|--------------------------|
| Ruby | gets | รับ Input ที่มี \n มาด้วย | ไม่มี ถ้าอยากจะลบต้อง .chomp |
| Java | คลาส Scanner และ Method nextLine()  | อ่านสตริงทั้งบรรทัด ไม่มี \n | ไม่มีมาด้วยอยู่แล้ว |
| C | scanf | รับ Input ทุกตัวจนกว่าจะเจอ white space | ไม่มี \n อยู่แล้ว | 
| Python | input() | รับ input ในรูปแบบของ String | ไม่มี \n อยู่แล้ว |

จะเห็นว่าแต่ละภาษาที่ยกตัวอย่างมาจะไม่มี \n มาให้ แต่จะมีตัวของ Ruby ที่มี \n มาด้วยเมื่อ gets
ถามว่ามีทำไม ก็เพราะ Ruby นั้นอ่านข้อมูลเป็นทีละบรรทัด ซึ่งถ้าไม่มี \n ในตอนจบ อาจจะมีการสูญหายของข้อมูลนั่นเอง
# Presentation slides
[640710060Ruby-gets-chomp.pptx](https://github.com/user-attachments/files/22426262/640710060Ruby-gets-chomp.pptx)


# อ้างอิงจ้า
ข้อมูลเรื่อง gets ใน Ruby จาก https://www.studytonight.com/ruby/getting-user-input-ruby

ข้อมูลเรื่อง chomp จาก https://www.geeksforgeeks.org/ruby/ruby-string-chomp-method/

ข้อมูลเรื่อง Scanner ใน Java จาก https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html

ข้อมูล scanf ในภาษา C จาก https://www.tutorialspoint.com/c_standard_library/c_function_scanf.htm

วิธีใช้ input() ใน Python ดูเพิ่มเติมที่ https://docs.python.org/3/library/functions.html#input

ข้อมูลประวัติแต่ละภาษา

Ruby https://en.wikipedia.org/wiki/Ruby_(programming_language)

Java https://en.wikipedia.org/wiki/Java_(programming_language)

C https://en.wikipedia.org/wiki/C_(programming_language)

Python https://en.wikipedia.org/wiki/Python_(programming_language)
