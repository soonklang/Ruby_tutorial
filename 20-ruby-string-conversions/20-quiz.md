#. เเบบฝึกหัด เรี่อง Ruby String Conversions
### 1 จงแยกชื่อไฟล์และนามสกุลออกจากกัน รวมถึงนับว่ามีทั้งหมดกี่ไฟล์ที่ใส่เข้ามา
โจทย์ String
```ruby
files = "a.txt,b.txt,c.jpg,d.png,e.jpg,f.doc,g.docx"
```
เฉลย
<details>
   <summary>Guildline ภาษา Ruby</summary>
    
```ruby
files = "a.txt,b.txt,c.jpg,d.png,e.jpg,f.doc,g.docx"
# ขั้นตอนที่ 1 + ผลลัพธ์
all_files = files.split(",")
p all_files
# => ["a.txt", "b.txt", "c.jpg", "d.png", "e.jpg", "f.doc", "g.docx"]

# ขั้นตอนที่ 2 + ผลลัพธ์
# ในส่วนนี้อยากจะลองปรับเปลี่ยนแล้วประยุกต์เอา loop มาใช้ด้วยก็ได้
p all_files[0].split(".")  # ["a", "txt"]
p all_files[1].split(".")  # ["b", "txt"]
p all_files[2].split(".")  # ["c", "jpg"]
p all_files[3].split(".")  # ["d", "png"]
p all_files[4].split(".")  # ["e", "jpg"]
p all_files[5].split(".")  # ["f", "doc"]
p all_files[6].split(".")  # ["g", "docx"]

# ขั้นตอนที่ 3 + ผลลัพธ์
p "มีไฟล์ทั้งหมด #{all_files.size} ไฟล์"
# => "มีไฟล์ทั้งหมด 7 ไฟล์"
 ```
</details>

<details>
   <summary>Guildline ภาษา C</summary>
    
```c
#include <stdio.h>
#include <string.h>

int main() {
    char files[] = "a.txt,b.txt,c.jpg,d.png,e.jpg,f.doc,g.docx";

    // ขั้นตอนที่ 1
    char *all_files[100];
    int count = 0;

    char *token = strtok(files, ",");
    while (token != NULL) {
        all_files[count++] = token;
        token = strtok(NULL, ",");
    }

    printf("ไฟล์ทั้งหมด:\n");
    for (int i = 0; i < count; i++) {
        printf("%s\n", all_files[i]);
    }

    // ขั้นตอนที่ 2
    printf("\nชื่อกับนามสกุลของแต่ละไฟล์:\n");
    for (int i = 0; i < count; i++) {
        char temp[100];
        strcpy(temp, all_files[i]);
        char *name = strtok(temp, ".");
        char *ext = strtok(NULL, ".");
        printf("[%s, %s]\n", name, ext);
    }

    // ขั้นตอนที่ 3
    printf("\nมีไฟล์ทั้งหมด %d ไฟล์\n", count);

    return 0;
}
 ```

> **NOTE** <br>
> เนื่องจาก strtok() เป็น destructive function ทำให้จำเป็นต้องประยุกต์ใช้กับ strcpy() เพื่อเก็บข้อความที่แยกมาแล้วนั้นแล้วเอาไปใช้ต่อได้โดยไม่ได้ใช้ตัวที่ถูกเปลี่ยนต้นฉบับไปแล้ว


output
```c
ไฟล์ทั้งหมด:
a.txt
b.txt
c.jpg
d.png
e.jpg
f.doc
g.docx

ชื่อกับนามสกุลของแต่ละไฟล์:
[a, txt]
[b, txt]
[c, jpg]
[d, png]
[e, jpg]
[f, doc]
[g, docx]

มีไฟล์ทั้งหมด 7 ไฟล์
```

</details>

<details>
   <summary>Guildline ภาษา Java</summary>
    
```Java
public class FileSplitExample {
    public static void main(String[] args) {
        String files = "a.txt,b.txt,c.jpg,d.png,e.jpg,f.doc,g.docx";

        // ขั้นตอนที่ 1
        String[] allFiles = files.split(",");
        System.out.println("ไฟล์ทั้งหมด:");
        for (String f : allFiles) {
            System.out.println(f);
        }

        // ขั้นตอนที่ 2
        System.out.println("\nชื่อกับนามสกุลของแต่ละไฟล์:");
        for (String f : allFiles) {
            String[] parts = f.split("\\.");  // ต้อง escape dot
            System.out.println("[" + parts[0] + ", " + parts[1] + "]");
        }

        // ขั้นตอนที่ 3
        System.out.println("\nมีไฟล์ทั้งหมด " + allFiles.length + " ไฟล์");
    }
}
 ```

output
```Java
ไฟล์ทั้งหมด:
a.txt
b.txt
c.jpg
d.png
e.jpg
f.doc
g.docx

ชื่อกับนามสกุลของแต่ละไฟล์:
[a, txt]
[b, txt]
[c, jpg]
[d, png]
[e, jpg]
[f, doc]
[g, docx]

มีไฟล์ทั้งหมด 7 ไฟล์
```
</details>

<details>
   <summary>Guildline ภาษา Python</summary>
    
```Python
files = "a.txt,b.txt,c.jpg,d.png,e.jpg,f.doc,g.docx"

# ข้ันตอนที่ 1
all_files = files.split(",")
print("ไฟล์ทั้งหมด:")
for f in all_files:
    print(f)

# ขั้นตอนที่ 2
print("\nชื่อกับนามสกุลของแต่ละไฟล์:")
for f in all_files:
    name, ext = f.split(".")  # split อีกครั้ง
    print([name, ext])

# ขั้นตอนที่ 3
print(f"\nมีไฟล์ทั้งหมด {len(all_files)} ไฟล์")
 ```

output
```Python
ไฟล์ทั้งหมด:
a.txt
b.txt
c.jpg
d.png
e.jpg
f.doc
g.docx

ชื่อกับนามสกุลของแต่ละไฟล์:
['a', 'txt']
['b', 'txt']
['c', 'jpg']
['d', 'png']
['e', 'jpg']
['f', 'doc']
['g', 'docx']

มีไฟล์ทั้งหมด 7 ไฟล์
```
</details>

### 2
```ruby

```
### 3. กำหนดตัวแปร String width = "12.5" และ String height = "3.2" ให้เขียนโปรแกรมแปลงค่าเป็น Float แล้วคำนวณพื้นที่ จากนั้นพิมพ์ผลลัพธ์
<details close>
   <summary><b>ภาษา Ruby</b></summary>
    
```ruby
width = "12.5"
height = "3.2"

puts "Area = #{width.to_f * height.to_f}"

 ```
Output
```ruby

Area = 40.0

 ```
        
</details>

<details close>
   <summary><b>ภาษา Java</b></summary>
    
```java
    public class Main {
    public static void main(String[] args) {
        String width = "12.5";
        String height = "3.2";

        System.out.println("Area = " + (Double.parseDouble(width) * Double.parseDouble(height)));
    }
}

 ```
Output
```java

Area = 40.0

 ```
        
</details>

<details close>
   <summary><b>ภาษา C</b></summary>
    
```C
#include <stdio.h>
#include <stdlib.h>

int main() {
    char width[] = "12.5";
    char height[] = "3.2";

    printf("Area = %.1f\n", atof(width) * atof(height));
    return 0;
}

 ```
Output
```C

Area = 40.0

 ```
        
</details>

<details close>
   <summary><b>ภาษา Python</b></summary>
    
```python
width = "12.5"
height = "3.2"

print("Area =", float(width) * float(height))

 ```
Output
```python

Area = 40.0

 ```
        
</details>


