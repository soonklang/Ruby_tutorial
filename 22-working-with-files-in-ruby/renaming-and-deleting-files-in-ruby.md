# Renaming and Deleting Files in Ruby

บทความนี้ทำขึ้นเพื่อให้ความรู้ ในการเปลี่ยนชื่อและลบไฟล์ด้วยโปรแกรมภาษา Ruby โดยใช้เมธอด rename() และ delete() ซึ่งการดำเนินการเหล่านี้มีความสำคัญอย่างมากเมื่อต้องจัดการไฟล์ภายในระบบแฟ้มข้อมูล (file system) 

---

### การลบไฟล์โดยใช้ delete()

```ruby
puts File.delete("sample1.txt")
```
### การเปลี่ยนชื่อไฟล์โดยใช้ rename() 

```ruby
puts File.rename("sample1.txt” ,"newSample.txt“)
```

---

เมื่อทำการเปลี่ยนชื่อหรือลบไฟล์ สิ่งสำคัญคือต้องจัดการข้อยกเว้น (exceptions) เพื่อรองรับข้อผิดพลาดที่อาจเกิดขึ้น ตัวอย่างเช่น หากไฟล์ไม่มีอยู่จริง การพยายามเปลี่ยนชื่อหรือลบไฟล์นั้นจะทำให้เกิดข้อผิดพลาดได้ เพื่อจัดการกรณีเหล่านี้ สามารถใช้โครงสร้าง begin...rescue...end ได้
### ตัวอย่าง:
```ruby
begin
	File.delete(“not_found.txt”)
	puts “File deleted successfully.”
      rescue => e
	puts “Error: #{e.message}”
end
```
### Output (หากไฟล์ไม่มีอยู่จริง) :

```ruby
Error: No such file or directory @ unlink_internal - not_found.txt
```

---

## ความแตกต่างของการเปลี่ยนชื่อไฟล์และลบไฟล์ในภาษา Ruby กับ ภาษา C, Java, Python

* ภาษา C
```c
#include <stdio.h>
int rename (const char *old_name, const char *new_name); //การเปลี่ยนชื่อไฟล์
int remove(const char *filename); //การลบชื่อไฟล์
//  return 0 ถ้าสำเร็จ, -1 ถ้าไม่สำเร็จ
```

* ภาษา Java
```java
import java.io.File;
// การเปลี่ยนชื่อไฟล์
File f1 = new File("oldname.txt");
File f2 = new File("newname.txt");
boolean b = f1.renameTo(f2);
// ถ้า b เป็นจริง ไฟล์ถูกเปลี่ยนชื่อสำเร็จแล้ว

// การลบชื่อไฟล์
File f1 = new File("garbage.txt");
boolean b = f1.delete();
// ถ้า b เป็นจริง ไฟล์ถูกลบสำเร็จแล้ว

```

* ภาษา Python

  
ในการเปลี่ยนชื่อและลบไฟล์ ใช้ฟังก์ชันที่มีอยู่แล้วในโมดูล os 
```python
import os
#ชื่อไฟล์ปัจจุบัน
current_name = "oldfile.txt"
#การเปลี่ยนชื่อไฟล์
new_name = "newfile.txt" 
os.rename(current_file_name, new_file_name) 

import os
#ระบุชื่อไฟล์ที่จะถูกลบ
file_name = "file_to_delete.txt"
#การลบไฟล์
os.remove(file_name) 
print("File deleted successfully!")
```

---

## ตารางเปรียบเทียบภาษา Ruby VS C, Java, Python

|          | Ruby          | C            | Java          | Python          |
|------------------|---------------------------|-------------------------|-------------------------------|---------------------------|
| Module/class | File | stdio.h | java.io.File | os |
| Rename    |  File.rename("sample.txt","newSample.txt") | int rename (const char *old_name, const char *new_name); | File f1 = new File("oldname.txt"); <br>File f2 = new File("newname.txt");<br>boolean b = f1.renameTo(f2); | os.rename(current_file_name, new_file_name) |
| Delete file  | File.delete("sample1.txt") | int remove(const char *filename); | File f1 = new File("garbage.txt");<br>boolean b = f1.delete(); | os.remove(file_name) |



จากการเปรียบเทียบจะเห็นว่า Ruby และ Python ใช้คำสั่งสำเร็จรูป ไม่ต้องจัดการไฟล์โดยตรง สามารถสั่งงานได้เลย 

## คลิปนำเสนอ


## สไลด์บรรยาย


## แหล่งที่มา
GeeksforGeeks. (2019, November 29). File handling in Ruby. GeeksforGeeks. https://www.geeksforgeeks.org/ruby/file-handling-in-ruby/

Ruby - File I/O. (n.d.). https://www.tutorialspoint.com/ruby/ruby_input_output.htm

Ruby - Deleting or renaming files. (n.d.). https://www.learnerslesson.com/Ruby/Ruby-Deleting-or-Renaming-Files.htm

Wahaj, S. (2023, July 4). Renaming and deleting files in Python ~. https://techkluster.com/python/renaming-and-deleting-files/

GeeksforGeeks. (2023, September 21). rename function in C. GeeksforGeeks. https://www.geeksforgeeks.org/c/rename-function-in-ccpp/

Sanfoundry. (n.d.). remove() and rename() Functions in C. https://www.sanfoundry.com/c-tutorials-file-manipulation-functions/

Renaming and deleting a file in Java. (n.d.). https://www.inf.unibz.it/~calvanese/teaching/ip/lecture-notes/uni09/node12.html

Nilanchala. (2025, August 31). How to delete and rename a file in java. StackTips. https://stacktips.com/articles/how-to-delete-and-rename-a-file-in-java


