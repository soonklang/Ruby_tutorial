
# Creating a New File with Ruby


การสร้างไฟล์ใหม่ขึ้นในภาษา Ruby จะใช้เมธอดของคลาส File เมธอดนี้รับค่ามาสองค่า คือค่าแรกคือชื่อไฟล์ที่จะสร้าง และค่าที่สองคือโหมดที่จะเปิดไฟล์


## ตารางโหมดต่างๆ

| mode               | คำอธิบาย                                                                     
|---|----------------------------------------|
| r	       |  จำกัดสิทธิ์ของผู้เปิดไฟล์เป็นแบบอ่านอย่างเดียวต้องมีชื่อไฟล์ชื่อเดียวกันถ้าไม่มีจะเกิด **`Errno::ENOENT`**    (File not found)  | 
| r+       |  จำกัดสิทธิ์ของผู้เปิดไฟล์เป็นแบบอ่านและเขียนได้ต้องมีชื่อไฟล์ชื่อเดียวกัน ถ้าไม่มีจะเกิด **`Errno::ENOENT`**    (File not found)  | 
| w       | จะสร้างไฟล์ใหม่ขึ้นมาให้เขียนได้อย่างเดียวหากยังไม่มีไฟล์ชื่อเดียวกัน หากมีไฟล์ชื่อเดียวกันอยู่แล้วไฟล์ที่มีอยู่จะถูกเขียนทับ
| w+       |จะสร้างไฟล์ใหม่ขึ้นมาให้ อ่านและเขียนได้ หากยังไม่มีไฟล์ชื่อเดียวกัน ถ้ามีไฟล์ชื่อเดียวกันอยู่แล้วข้อมูลเก่าจะถูกเขียนทับ
| a       | จะสร้างไฟล์ใหม่ขึ้นมาหากยังไม่มีไฟล์ชื่อเดียวกัน แต่ถ้ามีไฟล์ชื่อเดียวกันอยู่จะเป็นการเขียนต่อข้อมูลเดิม
| a+       | จะสร้างไฟล์ใหม่ขึ้นมาหากยังไม่มีไฟล์ชื่อเดียวกัน แต่ถ้ามีไฟล์ชื่อเดียวกันอยู่จะเป็นการเขียนต่อข้อมูลเดิม สามารถอ่านและเขียนได้
| b       | โหมดไฟล์ไบนารี ใช้ร่วมกับโหมดข้างต้น เฉพาะ Windows/DOS  
----
โดยที่modeต่างๆไม่ได้มีเเค่โหมดในการสร้างไฟล์ใหม่อย่างเดียวแต่มีโหมดเพื่อเอาไว้เปิดไฟล์และจำกัดสิทธ์การเข้าถึงของผู้เปิดไฟล์ได้อีกด้วย

## ตัวอย่างโค้ดภาษา Ruby

	//สร้างไฟล์ใหม่ "myfile.txt"
	File.open("myfile.txt", "w") do |file|
	file.puts "Hello Ruby!"
	end
 
	file = File.new("myfile.txt", "w")
	file.puts "Hello Ruby!"
	file.close


## ความแตกต่างในการสร้างไฟล์ ใน Ruby กับ python , c , java

 - ภาษา C
			
	ใน C สามารถสร้าง เปิด อ่าน และเขียนไฟล์ได้โดยใช้ฟังก์ชัน fopen()
	โดยจะรับพารามิเตอร์ 2 ตัว คือ ชื่อไฟล์และโหมดที่ต้องการใช้
	ในการสร้างไฟล์ สามารถใช้โหมด w ภายในฟังก์ชัน fopen() ได้
	โหมด w ใช้สำหรับเขียนข้อมูลลงในไฟล์ ถ้าหากไฟล์นั้นไม่มีอยู่ C จะสร้างไฟล์ใหม่ขึ้นมาให้
	
	ตัวอย่างโค้ด:
			
		#include <stdio.h>

			int main() {
			   FILE *fp = fopen("example.txt", "w");
			   fputs("Hello, C!\n", fp); // เขียนข้อมูลลงไฟล์
			   fclose(fp);                // ปิดไฟล์
			   return 0;
			}
	// fclose() เป็นการปิดไฟล์อย่างถูกต้อง เพื่อป้องกันข้อมูลเสียหาย

 - ภาษา python
	
	ใน python สามารถสร้าง เปิด อ่าน และเขียนไฟล์ได้โดยใช้ฟังก์ชัน open()
	โดยจะรับพารามิเตอร์ 2 ตัว คือ ชื่อไฟล์และโหมดที่ต้องการใช้
	python จะมีโหมด "x" อยู่ด้วยหมายถึงโหมด exclusive โดยที่ถ้ายังไม่มีไฟล์นี้อยู่จะไม่ถูกเขียนทับ แต่จะจะเกิด 
**FileExistsError** เพื่อป้องกันการถูกเขียนทับ
	
	ตัวอย่างโค้ด:
				
			new_file = open("myfile.txt", "w")  // "w" = write mode
			new_file.write("Hello, Python!\n") // เขียนข้อความลงไฟล์
			new_file.close() // ปิดไฟล์อย่างถูกต้อง

- ภาษา Java
  
  Java นั้น จะใช้Method createNewFile() โดยจะreturnเป็นboolean **True** ถ้าไฟล์สร้างได้สำเร๊จ **False** ถ้าไฟล์สร้างไม่สำเร็จ ใน Java การใช้ File.createNewFile() จำเป็นต้อง import class java.io.File เสมอ

	  ตัวอย่างโค้ด:
      import java.io.File;
      import java.io.IOException;
		public class CreateNewFile {
    	public static void main(String[] args) {
        try {
            File file = new File("example.txt");
            if (file.createNewFile()) {
                System.out.println("File created: " + file.getName());
            } else {
                System.out.println("File already exists.");
            }
        } catch (IOException e) {
            System.out.println("An error occurred.");
        }
      }


## ตารางเปรียบเทียบกับภาษา (Java, C, Python)

| ภาษา       | วิธีสร้างไฟล์ใหม่                          | ถ้าไฟล์มีอยู่แล้ว         | โหมดที่ใช้/ เมธอด         |
|------------|--------------------------------------------|---------------------------|-----------------------------|
| **Ruby**   | `File.new("temp.txt", "w")`            | จะถูกเขียนทับ   | `"w"` (write) |
| **Java**   | `File.createNewFile()`                     | return `false`            | เมธอด `createNewFile()`    |
| **Python** | `open("example.txt", "x")`                 | `FileExistsError`         | `"x"` (write)   |
| **C**      | `fopen("example.txt", "w")`       | จะถูกเขียนทับ            | `"w"` (write) |

---

### คลิปนำเสนอ
[click](https://youtu.be/9g1zP3QP4CQ)
------
### Presentation (slides)
[click](https://github.com/user-attachments/files/22569922/660710623rubynew.pdf)


---

## แหล่งที่มา
{Ruby Working with Files]
https://www.techotopia.com/index.php/Working_with_Files_in_Ruby

[Ruby Create new Files] 
https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/File.html#createNewFile()

[Python file handling ] 
https://www.freecodecamp.org/news/file-handling-in-python/

[Python file write]
https://www.w3schools.com/python/python_file_write.asp

[Java files]
https://www.w3schools.com/java/java_files.asp

[Java createNewFile()]
https://docs.oracle.com/en/java/javase/24/docs/api/java.base/java/io/File.html#createNewFile()

[C files]
https://www.w3schools.com/c/c_files.php

[C file handling ] 
https://www.geeksforgeeks.org/c/basics-file-handling-c/

