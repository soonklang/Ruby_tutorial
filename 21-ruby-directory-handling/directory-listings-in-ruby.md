# Directory Listings in Ruby

#### เมื่อเราเข้ามาใน Directory ที่ต้องการแล้วอยากดูข้อมูลใน Directory ที่ต้องการสามารถดูข้อมูลได้ด้วยคำสั่ง Dir.entires ("") โดยจะมีการคืนค่าเป็นอาร์เรย์

## ดูข้อมูลใน Directory

```
Dir.entries(".") // แทน . เป็น path ปัจจุบัน
```

```
#output
["techotopia_stats.jpg", "toolButton.png", ".", "..", "techotopia_stats_since_start.jpg", "music_728x90_1.jpg", 
"music_468x60_a.jpg", "Fedora_essentials.jpg"]
```

## เทคนิคจาก **Understanding Ruby Arrays**

#### นอกจากนี้ยังสามารถใช้เทคนิค Understanding Ruby Arrays เพื่อนำข้อมูลออกจากอาร์เรย์ได้ด้วยคำสั่ง dirListing

```
dirListing.each { |file| puts file }
```

<pre><code><strong>#output
</strong><strong>techotopia_stats.jpg
</strong>toolButton.png
.
..
techotopia_stats_since_start.jpg
music_728x90_1.jpg
music_468x60_a.jpg
Fedora_essentials.jpg
</code></pre>

#### คำสั่ง Dir.foreach(" . ")  { | file | puts file} ก็สามารถดูข้อมูลได้แบบเดียวกับคำสั่ง dirListing เลย

```
Dir.foreach(".") { |file| puts file }
```

```
#output
techotopia_stats.jpg
toolButton_IST.png
.
..
techotopia_stats_since_start.jpg
music_728x90_1.jpg
music_468x60_a.jpg
Fedora_essentials.jpg
```



## เปรียบเทียบกับภาษาอื่นๆ

### ภาษา C

#### ภาษา C จะมีความต่างกับภาษา Ruby โดยจะใช้คำต่างที่เยอะกว่า เช่น การใช้คำสั่ง opendir ( ) เพื่อเปิด Directory และใช้ readdir ( ) เพื่อหาข้อมูลใน Directory แล้วลูปแสดงข้อมูลจากนั้นจะใช้คำสั่ง closedir  ( ) เพื่อปิด Directory

```
#include <stdio.h>
#include <dirent.h>
int main(void)
{
struct dirent *de; // Pointer for directory entry 
DIR *dr = opendir(".");

if (dr == NULL)  // opendir returns NULL if couldn't open directory
{
    printf("Could not open current directory" );
    return 0;
}

// Refer https://pubs.opengroup.org/onlinepubs/7990989775/xsh/readdir.html
// for readdir()
while ((de = readdir(dr)) != NULL)
        printf("%s\n", de->d_name);

closedir(dr);    
return 0;
}
```

### ภาษา Java

#### ภาษา Java จะใช้ listFiles() จากการเรียกผ่านแพ็กเกจ java.io.File เพื่อเรียกดูข้อมูลโดยจะคืนค่าเป็นอาร์เรย์

```
// Java program list all files in a directory using listFiles()
import java.io.File;
public class ListFilesExample
{
  public static void main(String[] args)
  {
    // Path of the specific directory 
    String directoryPath = "C:/Users/GFG0354/Documents/JavaCode";
    
    // Using File class create an object for specific directory
    File directory = new File(directoryPath);
    
    // Using listFiles method we get all the files of a directory 
    // return type of listFiles is array
    File[] files = directory.listFiles();
    
    // Print name of the all files present in that path
    if (files != null) {
      for (File file : files) {
        System.out.println(file.getName());
      }
    }
  }
}
```

### ภาษา Python

ภาษา Python มีคำสั่งที่สามารถใช้ได้ 3 วิธีคือ os.listdir() , os.walk() , os.scandir() ซึ่งแตกต่างกับภาษา Ruby อยู่เยอะ

#### **os.listdir()**

```
import os

path = "C://Users//Vanshi//Desktop//gfg" 
dir_list = os.listdir(path) 
print("Files and directories in '", path, "' :")

print(dir_list)
```

**os.walk()**

```
import os

path = "C://Users//Vanshi//Desktop//gfg"

list = []

# dirs=directories
for (root, dirs, file) in os.walk(path):
    for f in file:
        if '.txt' in f:
            print(f)
```

**os.scandir()**

```
import os

path = "C://Users//Vanshi//Desktop//gfg"

# Scan the directory and get
# an iterator of os.DirEntry objects
# corresponding to entries in it
# using os.scandir() method
obj = os.scandir(path)

# List all files and directories in the specified path
print("Files and Directories in '% s':" % path)
for entry in obj:
    if entry.is_dir() or entry.is_file():
        print(entry.name)
```

## Silde



## Video



## ข้อมูลอ้างอิง

Skoglund, K. (2015). Ruby Pocket Reference( 2nd ). O'Reilly Media.\
docs ruby. (n.d.). class Dir. docs ruby. [https://docs.ruby-lang.org/en/master/Dir.html](https://docs.ruby-lang.org/en/master/Dir.html)\
Techotopia. (2016,10,27). Ruby Directory Handling. Techotopia. [https://www.techotopia.com/index.php/Ruby\_Directory\_Handling](https://www.techotopia.com/index.php/Ruby_Directory_Handling)\
GeeksforGeeks. (2021,11,18). Ruby | Dir Class and its methods. GeeksforGeeks. [https://www.geeksforgeeks.org/ruby/ruby-dir-class-and-its-methods/](https://www.geeksforgeeks.org/ruby/ruby-dir-class-and-its-methods/)

GeeksforGeeks. (2025,7,23). C Program to list all files and sub-directories in a directory. GeeksforGeeks. [https://www.geeksforgeeks.org/c/c-program-list-files-sub-directories-directory/](https://www.geeksforgeeks.org/c/c-program-list-files-sub-directories-directory/)

GeeksforGeeks. (2025,4,28). How to List all Files in a Directory in Java?. GeeksforGeeks. [https://www.geeksforgeeks.org/java/how-to-list-all-files-in-a-directory-in-java/](https://www.geeksforgeeks.org/java/how-to-list-all-files-in-a-directory-in-java/)

GeeksforGeeks. (2025,7,23). Python - List Files in a Directory. GeeksforGeeks. [https://www.geeksforgeeks.org/python/python-list-files-in-a-directory/](https://www.geeksforgeeks.org/python/python-list-files-in-a-directory/)

