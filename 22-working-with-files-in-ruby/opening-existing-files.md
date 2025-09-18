# Opening Existing Files

เราสามารถนำไฟล์ที่มีอยู่บนเครื่องมาเปิดได้ด้วยเมธอด open() ของคลาส File ซึ่งจะรับพารามิเตอร์ 2 ตัว คือ ชื่อของไฟล์และ mode การเข้าถึง แต่พารามิเตอร์ mode ไม่จำเป็นต้องระบุก็ได้

### สมมติว่า ข้อมูลภายในไฟล์ text.txt คือ 

>
```
Fred Bloggs,Manager,Male,45
Laura Smith,Cook,Female,23
Debbie Watts,Professor,Female,38
```

### ตัวอย่างที่ 1 :
```ruby
File.open("example.txt").each { |line| puts line } # แสดงข้อความที่ดึงมาจากไฟล์ทีละบรรทัด
```

### output 
```
 > Fred Bloggs,Manager,Male,45
Laura Smith,Cook,Female,23
Debbie Watts,Professor,Female,38
```
### ตัวอย่างที่ 2 :
```ruby
 File.open("text.txt").each(',') { |line| puts line } # แสดงข้อความที่ดึงมาจากไฟล์ทีละบรรทัด โดยจะตัดประโยคด้วย ","
```

### output
```
	> Fred Bloggs,
Manager,
Male,
45
Laura Smith,
Cook,
Female,
23
Debbie Watts,
Professor,
Female,
38
```

### ตัวอย่างที่ 3 :
```ruby
 File.open("text.txt") do |f| 
  2.times { puts f.gets } # แสดงข้อความที่ดึงมาจากไฟล์ทีละบรรทัด จำนวน 2 ประโยค
end 
```

### output
```
> Fred Bloggs,Manager,Male,45
Laura Smith,Cook,Female,23
```

เราสามารถกำหนด  mode การเข้าถึงไฟล์ได้ด้วยการระบุพารามิเตอร์ที่ 2  ซึ่งหากไม่ได้มีการกำหนด 
> "r" จะเป็น mode default ตั้งต้น 
ยกตัวอย่างเช่น เรากำหนดการเข้าถึงไฟล์ให้อยู่ในโหมด "r" หรือการอ่านได้เพียงอย่างเดียว

### ตัวอย่างที่ 4 :

```ruby
file = File.open("text.txt", "r")
	puts file.read
file.close
```
### output
```
	> Fred Bloggs,Manager,Male,45
Laura Smith,Cook,Female,23
Debbie Watts,Professor,Female,38
```
เรายังสามารถตรวจสอบสถานะของไฟล์ได้ด้วยว่า ไฟล์นั้นเปิดอยู่หรือไม่ด้วยการใช้เมธอด .closed? ซึ่งจะคืนค่าเป็น Boolean 

### ตัวอย่างที่ 5 :
```ruby
file.closed? # => False  
```

สุดท้าย เปิดไฟล์โดยไม่ใช้ block เราต้องปิดไฟล์ด้วย .close  แต่หากเราเปิดไฟล์โดยใช้ block syntax กับ File.open Ruby จะจัดการปิดไฟล์ให้อัตโนมัติหลังจาก block ทำงานเสร็จ

```ruby
# เปิดไฟล์ด้วยสถานะ อ่านอย่างเดียว
file = File.open("text.txt", "r")
	data = file.read # อ่านเนื้อหาภายในไฟล์แล้วเก็บไว้ภายในตัวแปร
	puts data # แสดงข้อความ
file.close # ปิดไฟล์
```

> การปิดไฟล์จะเป็นการคืนทรัพยากรให้กับระบบ เพราะการเปิดไฟล์จะใช้ทรัพยากร เช่น memory และ file descriptor


# การเปิดไฟล์ในภาษาอื่นๆ
## JAVA 

คลาส File จาก แพ็กเกจ java.io ทำให้เราสามารถทำงานร่วมกับไฟล์ต่างๆได้ โดยการสร้างวัตถุของคลาส File แล้วระบุชื่อและนามสกุลของไฟล์ 

### ตัวอย่างที่ 1
```java
import java.io.File;  // Import คลาส File

File myObj = new File("filename.txt"); // สร้างวัตถุของคลาส File ในชื่อ myObj
```

### ตัวอย่างที่ 2
```java
// Import คลาส File
import java.io.File; // Import คลาส File

class Geeks 
{
    public static void main(String[] args)
    {
        // ใส่ชื่อและนามสกุลไฟล์ให้ถูกต้อง
        File obj = new File("myfile.txt"); // สร้างวัตถุของคลาส File ในชื่อ obj
        System.out.println("File Created!"); // => File Created!
    }
}
```


## C

เราสามารถเปิดไฟล์ด้วยการสร้างตัวชี้ประเภท FILE และใช้ฟังก์ชัน fopen() ซึ่งจะรับพารามิเตอร์ 2 ตัว ได้แก่ ชื่อของไฟล์และโหมดการเข้าถึง

### ตัวอย่างที่ 1
```C
FILE *fptr;

fptr = fopen(filename, mode);
```

### ตัวอย่างที่ 2
```C
#include <stdio.h>
#include <stdlib.h>

int main() {
    
    // ตัวชี้ที่จะรับค่าที่ถูก return มาจากฟังก์ชัน fopen()
    FILE* fptr;

    // เปิดไฟล์ด้วยสถานะ อ่านอย่างเดียว
    fptr = fopen("filename.txt", "r");

    // ตรวจสอบว่าการเปิดไฟล์สำเร็จหรือไม่
    if (fptr == NULL) {
        printf("The file is not opened.");
    }
    return 0;
}
```


## Python

ใช้ฟังก์ชัน open() ซึ่งจะรับพารามิเตอร์ 2 ตัว ได้แก่ ชื่อของไฟล์และโหมดการเข้าถึง แล้วจะ return วัตถุไฟล์ 

### ตัวอย่างที่ 1
```python
file = open("geeks.txt", "r")
content = file.read()
print(content)
file.close()
```
### Output
	> Hello world
GeeksforGeeks
123 456

ในกรณีที่ไฟล์นั้นอยู่ที่ตำแหน่งอื่น ต้องระบุตำแหน่งของไฟล์ให้ชัดเจน

### ตัวอย่างที่ 2
```python
f = open("D:\\myfiles\welcome.txt")
print(f.read())
```

ในการอ่านไฟล์ประเภท CSV จำเป็นจะต้อง import pandas จากนั้นจึงใช้ เมธอด read.csv() เหมาะสำหรับการวิเคราะห์ข้อมูล

### ตัวอย่างที่ 3
```python
import pandas as pd
data = pd.read_csv("test.csv")
data.head(5)
```

# คลิปนำเสนอ


# Slide บรรยาย
https://drive.google.com/file/d/1U2tr_q1G20_20SgfL7DnG2pXYoiWZ5e7/view?usp=drive_link

# แหล่งอ้างอิง
### ภาษา Ruby
Beginning Ruby From Novice to Professional Third Edition (Copyright © 2016 by Peter Cooper) - Chapter 9 : Files and Databases

Ruby Data Processing - Using Map, Reduce, and Select (Copyright © 2018 by Jay Godse) - Chapter 1 Basic Ruby/ Reading from Files

Techopia (27 October, 2016) - Working with Files in Ruby 
[Working with Files in Ruby - Techotopia](https://www.techotopia.com/index.php/Working_with_Files_in_Ruby)

useful.codes (19 Jan, 2025) - Opening Files with Ruby
[[Java Files](https://www.w3schools.com/java/java_files.asp)](https://useful.codes/opening-files-with-ruby/)

### ภาษา  JAVA
W3School - Java Files
[Java Files](https://www.w3schools.com/java/java_files.asp)

GeeksforGeeks (28 Aug, 2025) - File handling in JAVA
[File Handling in Java - GeeksforGeeks](https://www.geeksforgeeks.org/java/file-handling-in-java/)

Codecademy (Jul 29, 2022) - Java Files
[Java | Files | Codecademy](https://www.codecademy.com/resources/docs/java/files)


### ภาษา C
W3School - C File 
[C Files - File Handling and How To Create Files](https://www.w3schools.com/c/c_files.php)

GeeksforGeeks (02 Aug, 2025) - Basics of File Handling in C
[Basics of File Handling in C - GeeksforGeeks](https://www.geeksforgeeks.org/c/basics-file-handling-c/)


### ภาษา PYTHON
W3School - Python File Open
[Python File Open](https://www.w3schools.com/python/python_file_handling.asp)

GeeksforGeeks (23 Jul, 2025) - File handling in Python
[File Handling in Python - GeeksforGeeks](https://www.geeksforgeeks.org/python/file-handling-python/)

Codecademy (Updated Aug 11, 2023) - Python Files
[Python | Files | Codecademy](https://www.codecademy.com/resources/docs/python/files)

Python 3.13.7 documentation (© Copyright 2001-2025,)
[Built-in Functions — Python 3.13.7 documentation](https://docs.python.org/3/library/functions.html#open)

