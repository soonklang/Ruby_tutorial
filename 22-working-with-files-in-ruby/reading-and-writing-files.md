# Reading and Writing Files 
> หากยังไม่ได้ติดตั้ง Ruby สามารถติดตั้งได้ที่ [RubyInstaller](https://rubyinstaller.org/)

เนื้อหาในที่นี้เราจะพูดถึงการอ่านและการเขียนไฟล์ผ่าน File class ของ ruby เป็นหลัก
### Read
> output ของ read ทั้งหมดจะเป็น Hello world เนื่องจากใน example.txt มีข้อความ Hello world

ในการทำอะไรกับไฟล์เราจำเป็นต้องกำหนดสิทธิในการเข้าถึงไฟล์นั้นๆก่อนด้วย เช่น **r**, **w**, **a**  และการอ่านจะสามารถทำได้จาก 2 คลาส คือ  

1. **File**  
2. **IO**  

> IO เป็นคลาสแม่ของ File  

วิธีการอ่านไฟล์มีหลายแบบ เช่น:  
- **อ่านทั้งไฟล์ทีเดียว** → `File.read` หรือ `IO.read` (คืนค่าเป็น String และโหลดเข้า memory ทั้งหมด)  
- **อ่านทีละบรรทัด/ทีละตัว** → `IO.foreach`, `file.each_line`, `file.gets` (ประหยัด memory เพราะไม่โหลดทั้งหมด)  


#### ประเภทของการอ่าน  

| Mode   | Description |
|--------|-------------|
| `"r"`   | อ่านเท่านั้น pointer ชี้จุดเริ่มต้นของไฟล์ |
| `"r+"`  | อ่านและเขียน pointer ชี้จุดเริ่มต้นของไฟล์ |
| `"w"`   | เขียนเท่านั้น หากไม่มีไฟล์จะทำการเขียนขึ้นมาใหม่ หากมีอยู่แล้วจะเขียนทับ |
| `"w+"`  | อ่านและเขียน หากไม่มีไฟล์จะทำการเขียนขึ้นมาใหม่ หากมีอยู่แล้วจะเขียนทับ |
| `"a"`   | เขียนเท่านั้น pointer ชี้ท้ายของไฟล์ หากไม่มีไฟล์จะเขียนมาใหม่ |
| `"a+"`  | อ่านและเขียน pointer ชี้ท้ายของไฟล์ หากไม่มีไฟล์จะเขียนมาใหม่ |
| `"b"`   | ใช้เป็นโหมด binary เช่น `rb`, `wb` |


### File
เป็นคลาสย่อยของ IO และใช้เพื่ออ่านไฟล์โดยเฉพาะ  
ต่างจาก IO ที่ใช้ในระดับ OS  

```ruby
fileobject = File.new("example.txt", "r")

# อ่านทั้งไฟล์ 
puts fileobject.read

# อ่านทีละบรรทัด
fileobject.each { |line| puts line }

fileobject.close
```
### IO 
ไม่ค่อยนิยมใช้ในการอ่านไฟล์ เพราะใช้ยาก ในที่นี้จะใช้ File แทนทั้งหมด
```ruby
fd = IO.sysopen("example.txt", "r")  # เปิดไฟล์แบบ system call
fileByIO = IO.new(fd)                # สร้าง IO object จาก fd

# อ่านทั้งไฟล์
puts fileByIO.read

fileByIO.rewind  # ย้าย pointer กลับไปต้นไฟล์

# อ่านทีละบรรทัด
fileByIO.readlines.each { |line| puts line }

fileByIO.close
```
### Write
ในการเขียน Ruby จะทำผ่าน File โดยจะต้องสร้างไฟล์ก่อน ถ้าไม่มีจะสร้างให้อัตโนมัตตาม permission ที่ตั้งให้ เช่น
> เรื่องควรรู้ หากไม่มี + จะไม่ทำการสร้างไฟล์อัตโนมัต ถ้าหากไฟล์ไม่มีอยู่ และหากไม่ใส่ close ก็จะไม่ทำการ write กับไฟล์นั้นๆ

w+ เขียนทับไฟล์เดิมเลย

a+ เขียนลงท้ายไฟล์


```ruby
fileobject = File.new("example.txt", "a+")

# เขียนโดยผ่าน System โดยตรง ไม่เพิ่มบรรทัดใหม่ 
fileobject.syswrite("direct write")

# เขียนโดยผ่าน buffer ของ ruby ไม่เพิ่มบรรทัดใหม่
fileobject.write("Write by buffer")

# เขียนปกติ โดยเพิ่มบรรทัดใหม่ 
fileobject.puts "normal writing"
fileobject.close      
```

### Compare to other language
  <details>
    <summary>Ruby</summary>
  
  ```ruby
    begin
      fileobject = File.new("example.txt", "r+")
    
      # Read
      puts fileobject.read
    
      # Write
      puts "What text do you want to replace:"
      fileobject.syswrite("new Text")
    
    rescue Errno::ENOENT
      puts "Error: File not found!"
    
    rescue Errno::EACCES
      puts "Error: Permission denied!"
    
    rescue => e
      puts "Unexpected error: #{e.message}"
    
    ensure
      fileobject.close if fileobject
    end
   ```
  </details>
<details>
  <summary>Java</summary>

```java
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

class rw {
    public static void main(String[] args) {
        // Read
        try (FileReader fr = new FileReader("example.txt")) {
            int ch;
            while ((ch = fr.read()) != -1) {
                System.out.print((char) ch);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }

        // Write
        try (FileWriter fw = new FileWriter("example.txt")) {
            fw.write("new text");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
ใน java มีหลายตัวที่สามารถใช้ได้ในการอ่าน File ได้ เช่น Scanner FileReader Byte BufferReader โดยแต่ละตัวก็จะมีสิ่ง่ที่เป็นเอกลักษณ์ของมัน เช่น 

Scanner -> อ่านทั้งไฟล์

FileReader -> อ่านทีละตัวอักษร

BufferReader -> อ่านทีละบรรทัด

ยังมีอีกหลายตัวที่ใช้แทนกันได้มันจะมีความหลากหลายได้การใช้ แต่ Ruby จะมีแค่ File กับ IO ซึ่งมีน้อยกว่าแต่ก็แลกกับการเขียนได้ง่าย
</details> 

  <details>
    <summary>C</summary>
  
  ```c
  #include <stdio.h>
  
  int main()
  {
      FILE *fptr;
      char filename[100];
      char text[100];
      int ch;
  
      fptr = fopen("example.txt", "r+");
      if (fptr == NULL)
      {
          printf("File not found!\n");
          return 1;
      }
      // Read
      while ((ch = fgetc(fptr)) != EOF)
      {
          putchar(ch);
      }
      printf("\n");
  
      // Write
      printf("Enter text: ");
      scanf(" %[^\n]", text);
      fseek(fptr, 0, SEEK_END);
      fputs(text, fptr);
  
      fclose(fptr);
      return 0;
  }
   ```
เนื่องจาก C เป็น low language มันจะค่อนข้างอ่านยาก เนื่องจากเป็นการอ่านไฟล์โดยใช้ pointer ชี้และอ่านค่าจาก pointer แปลงเป็น char และเมื่อใช้เสร็จจำเป็นต้อง rewind pointer กลับเข้าจุดตั้งเดิม เนื่องด้วยไม่มี Class ช่วยเลย  จะเห็นได้เลยว่า Ruby นั้นง่ายกว่า เพราะมี Class File รองรับ
  </details>

  </details> 
  
  <details>
    <summary>Python</summary>
  
  ```python
try:
    with open("example.txt", "r+") as file:
        # Read
        content = file.read()
        print(content)

        # Write at the end
        text = input("What do you want to write: ")
        file.write("\n" + text)

except FileNotFoundError:
    print("Error: File was not found!")

   ```
python เป็นภาษาที่ออกกแบบมาให้ดูง่าย เมื่อใช้ with ทำให้ file close อัตโนมัต ทำให้โค้ดดูสะอาดและเขียนง่าย ต่างจาก Ruby ที่อาจจะดูยากหน่อย แต่โดยรวมค่อนข้างคล้ายกัน
  </details>
  
### Example

<details>
  <summary>Ruby</summary>
  
  ```ruby
   def rwCheck()
    puts File.file?("example.txt")
    puts File.readable?("example.txt")
    puts File.writable?("example.txt")  
end 

def rwFile
    print "What name of file to work with (.txt) : "
    name = gets.chomp
    while true 
      puts 'What your Command
  1.read
  2.write
  3.exit'
      print "Type number or keyword : "
      command = gets.chomp 
      case command
        when "read" , "1"
          begin
            if !File.file?(name) 
              puts "Create the file first"
            else
              fileobject = File.new(name, "r")
              puts fileobject.read
              fileobject.close
            end
          rescue => e
            puts "Error: #{e.message}"
          end
  
        when "write", "2"
          begin
            fileobject = File.new(name, "w")
            puts "What text do u want to replace"
            newText = gets.chomp
            fileobject.syswrite(newText)
            fileobject.close
          rescue => e
            puts "Error: #{e.message}"
          end
        when "exit", "3"
          break
        else
          puts "Unknown command!"
        end
        puts ""
      end
end

rwFile
  ```

</details>
<details>
  <summary>Java</summary>
  
  ```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.util.Scanner;

public class rw {
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {
        System.out.print("Enter the file name to work with (.txt): ");
        String filename = sc.nextLine();
        while (true) {
            System.out.println("""
                    1.Check
                    2.FileReader and FileWriter
                    3.Byte
                    4.BufferReader and BufferWriter
                    5.Exit""");
            System.out.print("type number for command : ");
            String command = sc.nextLine();
            switch (command) {
                case "check", "1":
                    checkRW(filename);
                    break;
                case "2":
                    byFileReaderandFileWriter(filename);
                    break;
                case "3":
                    readByBtye(filename);
                    break;
                case "4":
                    readByBufferReaderandBufferWriter(filename);
                    break;
                case "exit", "5":
                    sc.close();
                    return;
                default:
                    System.out.println("Wrong command");

            }
        }
    }

    static void checkRW(String filename) {
        Path path = Paths.get(filename);
        if (Files.exists(path)) {
            System.out.println("Readable : " + Files.isReadable(path));
            System.out.println("Writable : " + Files.isWritable(path));
        }
    }
    static void setrwxToFalse(String filename){
        File file = new File(filename);
        file.setReadable(false);
        file.setWritable(false);
        file.setExecutable(false);
    }

    static void byFileReaderandFileWriter(String filename) {
        System.out.print("read or write : ");
        String command = sc.nextLine();
        int ch;
        if (command.equals("read")) {
            try (FileReader fr = new FileReader(filename)) {
                System.out.println("--- Output ---");

                while ((ch = fr.read()) != -1) {
                    System.out.print((char) ch);
                }
                System.out.println("--------------");
            } catch (IOException e) {
                e.printStackTrace();
            }
        } else {
            try (FileWriter fw = new FileWriter(filename)) {
                System.out.println("What text u want to type in : ");
                String text = sc.nextLine();
                fw.write(text);
                fw.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }

    }

    static void readByBtye(String filename) {

        Path path = Paths.get(filename);
        System.out.print("read or write : ");
        String command = sc.nextLine();
        if (command.equals("read")) {
            try {
                System.out.println("--- Output ---");

                byte[] fileArray = Files.readAllBytes(path);
                for (byte b : fileArray) {
                    System.out.print((char) b);
                }
                System.out.println("--------------");

            } catch (IOException e) {
                e.printStackTrace();
            }
        } else {
            try {
                byte[] text = sc.nextLine().getBytes();
                Files.write(path, text);
            } catch (IOException e) {
                e.printStackTrace();
            }
        }

    }

    static void readByBufferReaderandBufferWriter(String filename) {
        Path path = Paths.get(filename);
        Charset charset = Charset.forName("US-ASCII");
        System.out.print("read or write : ");
        String command = sc.nextLine();
        if (command.equals("read")) {
            try (BufferedReader reader = Files.newBufferedReader(path, charset)) {
                String line = null;
                System.out.println("--- Output ---");
                while ((line = reader.readLine()) != null) {
                    System.out.println(line);
                }
                System.out.println("--------------");
            } catch (IOException e) {
                e.printStackTrace();
            }
        } else {
            try (BufferedWriter writer = Files.newBufferedWriter(path, charset)) {
                String text = sc.nextLine();
                writer.write(text.toCharArray(), 0, text.length());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }

}
  ```

</details>
<details>
  <summary>C</summary>
  
  ```c
   
#include <stdio.h>

int main()
{
    FILE *fptr;
    char filename[100];
    char text[100];
    int command;

    printf("Enter the file name to work with (.txt): ");
    scanf("%s", filename);

    fptr = fopen(filename, "r+");
    if (fptr == NULL){
        printf("File not found!\n");
        return 1;
    }

    while (1){
        printf("1.read\n2.write\n3.exit : ");
        scanf("%d", &command);

        if (command == 1){
            char ch;
            rewind(fptr);
            while ((ch = fgetc(fptr)) != EOF)
            {
                putchar(ch);
            }
            printf("\n");
        }
        else if (command == 2){
            printf("Enter text: ");
            scanf(" %[^\n]", text);
            fseek(fptr, 0, SEEK_END);
            fputs(text, fptr);
            fflush(fptr);
        }
        else if (command == 3){
            break;
        }
        else{
            printf("Invalid command!\n");
        }
    }

    fclose(fptr);
    return 0;
}
  ```

</details>
<details>
  <summary>Python</summary>
  
  ```python
filename = input("Enter the file name to work with (.txt): ")

while True:
    try:
        with open(filename, "r+") as file:
            command = input("read or write or exit : ")

            if command == "read":
                file.seek(0)
                print(file.read())

            elif command == "write":
                text = input("What do u want write : ")
                file.write(text)

            elif command == "exit":
                break

    except FileNotFoundError:
        print(f"Error: File '{filename}' was not found!")
        break
  ```

</details>


## Media

- [Slide](https://www.canva.com/design/DAGzUu5a_jk/GCMqv2SZibwTXuVh9lg4XQ/edit?utm_content=DAGzUu5a_jk&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)  
- [YouTube Video](https://www.youtube.com/watch?v=wvbc7j5ahX0)


## ข้อมูลอ้างอืง

### Ruby

https://docs.ruby-lang.org/en/master/File.html

https://www.techotopia.com/index.php/Working_with_Files_in_Ruby

### Java

https://www.geeksforgeeks.org/java/file-handling-java-using-filewriter-filereader/

https://docs.oracle.com/javase/tutorial/essential/io/file.html

### C

https://www.programiz.com/c-programming/c-file-input-output

https://en.cppreference.com/w/c/io/fgetc

### Python

https://docs.python.org/3/tutorial/inputoutput.html

https://www.geeksforgeeks.org/python/read-a-file-line-by-line-in-python/
