# Changing Directory in Ruby

#### เมื่อเริ่มต้นการใช้งาน Ruby จะมีการทำงานของ Directory ใด Directory หนึ่งภายในไฟล์ จะมีฟังค์ชั่นในการจัดการเกี่ยวกับ Directory นั้นก็คือฟังค์ชั่น Dir

## **เช็ค Directory ปัจจุบัน**

#### เราสามารถเช็คว่า Directory ปัจจุบัน อยู่ที่ไหนได้ด้วยคำสั่ง dir.pwd โดยย่อมาจาก Present Working Directory&#x20;

ที่จะคืนค่า path ปัจจุบัน

```
Dir.pwd
```

#### นอกจากนั้นยังสามารถใช้คำสั่ง Dir.getwd ได้เหมือนกัน

```
Dir.getwd
```

## เปลี่ยน Directory ปัจจุบัน

#### เราสามารถเปลี่ยน Directory ที่ใช้อยู่ในปัจุบันไปใช้ Directory ที่ต้องการได้ด้วยคำสั่ง Dir.chdir (" path ")

```
Dir.chdir("/home/ruby/test")
```

## เปรียบเทียบกับภาษาอื่นๆ

### ภาษา C

#### จะมีการเรียก unistd.h เพื่อสามารถใช้ฟังค์ชั่นในการเปลี่ยน directory&#x20;

```
#include<stdio.h> 
#include<unistd.h> 
int main() 
{ 
    char s[100]; 
    printf("%s\n", getcwd(s, 100)); 
    chdir(".."); 
    printf("%s\n", getcwd(s, 100)); 
    return 0; 
} 
```

### ภาษา Java&#x20;

#### จะมีการเรียกใช้คำสั่ง System.getProperty("user.dir") เพื่อดูว่า directory ปัจจุบันอยู่ที่ไหน

```java
public class JavaApplication {
  public static void main(String[] args) {
    System.out.println("Working Directory = " + System.getProperty("user.dir"));
  }
}
```

### ภาษา Python&#x20;

#### Python จะทำการ import os โดยใช้คำสั่ง os.getcwd() เพื่อเช็ค Directory ปัจจุบัน และใช้คำสั่ง os.chdir( path ) เพื่อเปลี่ยน Directory

```python
import os
cwd = os.getcwd()
os.chdir(path)
```

## ข้อมูลอ้างอิง

Skoglund, K. (2015). Ruby Pocket Reference( 2nd ). O'Reilly Media.

GeeksforGeeks. (2021,11,18). Ruby | Dir Class and its methods. GeeksforGeeks. [https://www.geeksforgeeks.org/ruby/ruby-dir-class-and-its-methods/](https://www.geeksforgeeks.org/ruby/ruby-dir-class-and-its-methods/)

docs ruby. (n.d.). class Dir. docs ruby. [https://docs.ruby-lang.org/en/master/Dir.html](https://docs.ruby-lang.org/en/master/Dir.html)

Techotopia. (2016,10,27). Ruby Directory Handling. Techotopia. [https://www.techotopia.com/index.php/Ruby\_Directory\_Handling](https://www.techotopia.com/index.php/Ruby_Directory_Handling)

Stackoverflow. (2011,2,28). Find the current directory and file's directory \[duplicate]. Stackoverflow. [Find the current directory and file's directory \[duplicate\]](https://stackoverflow.com/questions/5137497/find-the-current-directory-and-files-directory)

IBM. (2021,06,25). chdir() — Change the working directory. IBM. [https://www.ibm.com/docs/en/zos/2.4.0?topic=functions-chdir-change-working-directory](https://www.ibm.com/docs/en/zos/2.4.0?topic=functions-chdir-change-working-directory)

Stackoverflow. (2011,9,29). How to get the current working directory in Java? . Stackoverflow. [https://stackoverflow.com/questions/4871051/how-to-get-the-current-working-directory-in-java](https://stackoverflow.com/questions/4871051/how-to-get-the-current-working-directory-in-java)

