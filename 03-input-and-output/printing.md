# Printing

คือเมธอดที่ใช้ในการแสดงผลลัพธ์ออกมาบนหน้าจอ โดยในภาษา Ruby นั้นนิยมใช้อยู่ทั้งหมด 3 เมธอดคือ print, puts และ p
ซึ่งแต่ละตัวนั้นมีจุดสำคัญเหมือนกันคือการแสดงผลลัพธ์ แต่มึจุดประสงค์ในการใช้ค่อนข้างต่างกัน แต่ละเมธอดเหมาะกับการใช้ในสถานการณ์ไหน
สามารถดูได้ตามตัวอย่างด้านล่างดังนี้

## print
คือเมธอดแสดงผลลัพธ์ออกมาบนหน้าจอ แต่หลังจากที่แสดงผลลัพธ์แล้วจะไม่มีการขึ้นบรรทัดใหม่ ดังตัวอย่างนี้
```ruby
print "Hello, "
print "world! "
print "Welcome to Ruby tutorial project"

#ผลลัพธ์ที่ได้ออกมาจะเป็น
Hello, world! Welcome to Ruby tutorial project
```
เห็นได้ว่าหลังจากแสดงผลแล้วไม่มีการขึ้นบรรทัดใหม่เลย หากเราอยากให้มีการขึ้นบรรทัดใหม่ เราสามารถใช้ \n ต่อท้ายในส่วนที่เราต้องการให้ขึ้นบรรทัดใหม่เมื่อจบการแสดงผลในบรรทัดนั้น ดังตัวอย่างนี้
```ruby
print "Hello, "
print "world!\n"
print "Welcome to Ruby tutorial project"

#ผลลัพธ์ที่ได้ออกมาจะเป็น
Hello, world!
Welcome to Ruby tutorial project
```
หลังจากที่เราใส่ \n เข้าได้ด้านหลังในส่วนที่เราต้องการให้ขึ้นบรรทัดใหม่หลังจบการแสดงผลแล้ว มันก็จะขึ้นบรรทัดใหม่ให้

## puts
คือเมธอดแสดงผลผลลัพธ์ที่เหมือนกับ print เลย แต่ต่างกันเล็กน้อยตรงที่ puts นั้นหลังจากจบจากการแสดงผลตัวนั้นๆแล้วจะมีการขึ้นบรรทัดใหม่เสมอ ทำให้มีความสะดวกในการใช้มากกว่า print ดังตัวอย่างนี้
```ruby
puts "Hello, world!"
puts "Welcome to Ruby tutorial project"

#ผลลัพธ์ที่ได้ออกมาจะเป็น
Hello, world!
Welcome to Ruby tutorial project
```
กล่าวได้ง่ายๆก็คือ puts หลังจากทำการแสดงผลแล้วจะทำการขึ้นบรรทัดใหม่ให้เลยเราไม่ต้องทำการ \n ใส่หลังในส่วนที่เราต้องการให้ขึ้นบรรทัดใหม่แล้ว

## p
คือเมธอดที่ใช้ในการแสดงผลลัพธ์เหมือนกับ 2 ตัวด้านบน แต่ค่อนข้างจะแตกต่างกันอย่างมากตรงที่ p นั้นผลลัพธ์ที่ได้ออกมานั้นจะเป็นข้อมูลดิบ เพราะ p จะเรียกเมธอด inspect กับ object ซึ่งเหมาะกับการ debug โดยตรงดังตัวอย่างนี้
```ruby
#สมมติเรามี 3 ตัวแปรนี้ที่เก็บออบเจ็กต์ต่างเอาไว้
name = "Kwon Ji Yong"
age = 37
arr = [1, 2, 3]
#ถ้าเราใช้ puts ในการแสดงผลตัวแปรเหล่านี้จะรู้ได้ยังไงว่าออบเจ็กต์ที่ถูกเก็บไว้เป็น int, String หรือ array ดังนั้นเมธอด p จึงช่วยได้มากในสถานการณ์แบบนี้

p name
p age
p arr

#ผลลัพธ์ที่ได้ออกมาจะเป็น
"Kwon Ji Yong"
37
[1, 2, 3]
```
สรุปได้ว่าจากเมธอดทั้ง 3 ตัวนี้นั้นมีจุดประสงค์ในการใช้ที่ต่างกัน โดย 2 ตัวแรกอย่าง print และ puts นั้นค่อนข้างจะ user-friendly เหมาะกับผู้ใช้ทั่วไป ในขณะที่ p นั้นไม่เหมาะกับผู้ใช้ทั่วไปเลย เหมาะกับโปรแกรมเมอร์มากกว่า ดังนั้นเราสามารถเลือกใช้ได้ตามสถานการณ์ที่ต้องการ
# ภาษาอื่นๆอย่าง Java, C และ Python ทำได้ไหม?
## Java
ในภาษา Java นั้นมีเมธอดที่เหมือนกับ print, puts และ p อยู่นั่นคือ
- System.out.print ที่เหมือนกับ print ใน Ruby ที่จะไม่มีการขึ้นบรรทัดใหม่หลังจากจบการแสดงผล
- System.out.println ที่เหมือนกัน puts ใน Ruby ที่จะขึ้นบรรทัดใหม่หลังจากแสดงผลอ็อบเจ็กต์นั้นๆเสร็จ
- toString ที่เหมือนกับ p ใน Ruby ที่จะแสดงค่าข้อมูลดิบที่อยู่ในอ็อบเจ็กต์ออกมา
### ตัวอย่าง
```java
#System.out.print
public class Main {
    public static void main(String[] args) {
        System.out.print("Hello, world! ");
        System.out.print("Welcome to Ruby tutorial project");
    }
}
#ผลลัพธ์ที่ได้ออกมาจะเป็น
Hello, world! Welcome to Ruby tutorial project

#System.out.println
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, world!");
        System.out.println("Welcome to Ruby tutorial project");
    }
}
#ผลลัพธ์ที่ได้ออกมาจะเป็น
Hello, world!
Welcome to Ruby tutorial project

#toString
import java.util.Arrays;
public class Main {
    public static void main(String[] args) {
        int[] arr = {1,2,3};
        System.out.println(Arrays.toString(arr));
    }
}
#ผลลัพธ์ที่ได้ออกมาจะเป็น
[1,2,3]
```
## C
ในภาษา C นั้น มีเมธอดที่เหมือนกัน print และ puts อยู่แต่ไม่มีเมธอดที่เหมือนกับ p ต้องเขียนฟีลด์ขึ้นมาใหม่เอง
- printf นั้นเหมือนกับ print ใน Ruby ที่จะไม่มีการขึ้นบรรทัดใหม่หลังจากจบการแสดงผล
- printf..\n นั้นเหมือนกัน puts ใน Ruby ที่จะขึ้นบรรทัดใหม่หลังจากแสดงผลอ็อบเจ็กต์นั้นๆเสร็จ
- ส่วน p ในภาษา C ไม่มีเมธอดที่คล้ายคลึงกับ p
### ตัวอย่าง
```c
#printf
#include <stdio.h>

int main() {
    printf("Hello, world! ");
    printf("Welcome to Ruby tutorial project");
    return 0;
}

#ผลลัพธ์ที่ได้ออกมาจะเป็น
Hello, world! Welcome to Ruby tutorial project

#print ..\n
#include <stdio.h>

int main() {
    printf("Hello, world!\n");
    printf("Welcome to Ruby tutorial project");
    return 0;
}

#ผลลัพธ์ที่ได้ออกมาจะเป็น
Hello, world!
Welcome to Ruby tutorial project

#ตัวอย่างในการ inspect object ใน ภาษา C
#include <stdio.h>

typedef struct {
    char name[32];
    int age;
} Person;

void inspect_person(Person p) {
    printf("Person{name=%s, age=%d}\n", p.name, p.age);
}

int main() {
    Person kwonjiyong = {"Kwon Ji Yong", 37};
    inspect_person(kwonjiyong);
    return 0;
}

#ผลลัพธ์ที่ได้ออกมาจะเป็น
Person{name=Kwon Ji Yong, age=37}
```
## Python
ในภาษา Java นั้นมีเมธอดที่เหมือนกับ print, puts และ p อยู่นั่นคือ
- print(..., end=" ") ที่เหมือนกับ print ใน Ruby ที่จะไม่มีการขึ้นบรรทัดใหม่หลังจากจบการแสดงผล
- print ที่เหมือนกัน puts ใน Ruby ที่จะขึ้นบรรทัดใหม่หลังจากแสดงผลอ็อบเจ็กต์นั้นๆเสร็จ
- print(repr(...)) ที่เหมือนกับ p ใน Ruby ที่จะแสดงค่าข้อมูลดิบที่อยู่ในอ็อบเจ็กต์ออกมา
### ตัวอย่าง
```python
#print(..., end=" ")
print("Hello, world!", end=" ")
print("Welcome to Ruby tutorial project", end=" ")

#ผลลัพธ์ที่ได้ออกมาจะเป็น
Hello, world! Welcome to Ruby tutorial project

#print
print("Hello, world!")
print("Welcome to Ruby tutorial project")

#ผลลัพธ์ที่ได้ออกมาจะเป็น
Hello, world!
Welcome to Ruby tutorial project

#print(repr(...))
arr = [1, 2, 3, 4, 5]
print(repr(arr))

#ผลลัพธ์ที่ได้ออกมาจะเป็น
[1, 2, 3, 4, 5]
```
# ตารางเปรียบเทียบ
| Ruby | Java | C | Python |
|------|-------------------|-------------------|--------------------------|
| print | System.out.print | printf | print(..., end=" ") |
| puts | System.out.println | printf..\n | print |
| p | toString | ไม่มี | print(repr(...)) |

# References
- GeeksforGeeks. (2024). How to print output in Ruby? https://www.geeksforgeeks.org/ruby/how-to-print-output-in-ruby/
- GeeksforGeeks. (2025). System.out.println in Java https://www.geeksforgeeks.org/java/system-out-println-in-java/
- GeeksforGeeks. (2025). Object toString() Method in Java https://www.geeksforgeeks.org/java/object-tostring-method-in-java/
- GeeksforGeeks. (2025). Basic Input and Output in C https://www.geeksforgeeks.org/c/basic-input-and-output-in-c/
- GeeksforGeeks. (2025). C Structures https://www.geeksforgeeks.org/c/structures-c/
- GeeksforGeeks. (2025). How to Print without newline in Python? https://www.geeksforgeeks.org/python/print-without-newline-python/
- GeeksforGeeks. (2025). Python repr() Function https://www.geeksforgeeks.org/python/python-repr-function/
