# Creating New Directories

#### การสร้าง Directory ในภาษา Ruby นั้นใช้ class Dir ด้วยฟังค์ชั่น mkdir โดยจะตั้งชื่อ Directory และตั้งค่าสิทธิ (Permission)

## การสร้าง Directory

```
Dir.mkdir "dir_name", permission
```

## การลบ Directory

#### Directory ที่สร้างมาแล้วสามารถลบได้ด้วยคำสั่งที่หลากหลายได้แก่ Dir.delete , Dir.rmdir และ Dir.unlink

```
Dir.delete "dir_name"
```

```
Dir.rmdir "dir_name"
```

```
Dir.unlink " Dir_name"
```

## การเปรียบเทียบกับภาษาอื่นๆ

### ภาษา C

#### ภาษา C จะใช้คำสั่ง mkdir เหมือนกับภาษา Ruby เลยโดยจะเป็นการใช้ mkdir แล้วตามด้วยชื่อและ Permission

```
#include <conio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>

void main()
{
    int check;
    char* dirname = "geeksforgeeks";
    clrscr();

    check = mkdir(dirname,0777);

    if (!check)
        printf("Directory created\n");
    else {
        printf("Unable to create directory\n");
        exit(1);
    }

    getch();

    system("dir");
    getch();
}
```

### ภาษา Java

#### ภาษา Java จะใช้คำสั่ง mkdir จากClass File เหมือนกับภาษาRuby แต่จะเกิด exception หากไม่มี Parent Directory

```
    import java.io.File;
    public class GFG {
        public static void main(String[] args) {
            String directoryName = "My_Learning";
            
            String currentDirectory = System.getProperty("user.dir");
        
            String directoryPath = currentDirectory + File.separator + directoryName;
        
            File directory = new File(directoryPath);
        
            boolean directoryCreated = directory.mkdir();
        
            if (directoryCreated) {
                System.out.println("Directory created successfully at: " + directoryPath);
            } else {
                System.out.println("Failed to create directory. It may already exist at: " + directoryPath);
        }
    }
}
```

}

### ภาษา Python

#### ภาษา Python ก็ยังใช้คำสั่ง mkdir เหมือนๆกลับภาษา C Java และ Rubyเช่นกัน

<pre><code>import os

directory_name = "GFG"

try: 
<strong>    os.mkdir(directory_name) 
</strong>    print(f"Directory '{directory_name}' created successfully.") 
except FileExistsError: 
    print(f"Directory '{directory_name}' already exists.") 
except PermissionError: 
    print(f"Permission denied: Unable to create '{directory_name}'.") 
except Exception as e: 
    print(f"An error occurred: {e}")
</code></pre>

## Slide

[https://drive.google.com/file/d/1bYwRICNhNw3CIYsh275toZnVC9Yyq0kc/view?usp=sharing](https://drive.google.com/file/d/1bYwRICNhNw3CIYsh275toZnVC9Yyq0kc/view?usp=sharing)

## Video

[https://drive.google.com/file/d/1S7eaqkgy5VOfIE-OwNgapp5gw5KZCJ3C/view?usp=sharing](https://drive.google.com/file/d/1S7eaqkgy5VOfIE-OwNgapp5gw5KZCJ3C/view?usp=sharing)

## ข้อมูลอ้างอิง

Skoglund, K. (2015). Ruby Pocket Reference( 2nd ). O'Reilly Media.\
docs ruby. (n.d.). class Dir. docs ruby. [https://docs.ruby-lang.org/en/master/Dir.html](https://docs.ruby-lang.org/en/master/Dir.html)\
Techotopia. (2016,10,27). Ruby Directory Handling. Techotopia. [https://www.techotopia.com/index.php/Ruby\_Directory\_Handling](https://www.techotopia.com/index.php/Ruby_Directory_Handling)\
GeeksforGeeks. (2021,11,18). Ruby | Dir Class and its methods. GeeksforGeeks. [https://www.geeksforgeeks.org/ruby/ruby-dir-class-and-its-methods/](https://www.geeksforgeeks.org/ruby/ruby-dir-class-and-its-methods/)

GeeksforGeeks. (2022,11,30). Create Directory or Folder with C/C++ Program. GeeksforGeeks. [https://www.geeksforgeeks.org/linux-unix/create-directoryfolder-cc-program/](https://www.geeksforgeeks.org/linux-unix/create-directoryfolder-cc-program/)

GeeksforGeeks. (2025,7,23). How to Create a Directory in Java?. GeeksforGeeks. [https://www.geeksforgeeks.org/java/how-to-create-a-directory-in-java/](https://www.geeksforgeeks.org/java/how-to-create-a-directory-in-java/)

GeeksforGeeks. (2025,7,12). Create a directory in Python. GeeksforGeeks. [https://www.geeksforgeeks.org/python/create-a-directory-in-python/](https://www.geeksforgeeks.org/python/create-a-directory-in-python/)

