# Getting Information About Files

ในการเป็นนักพัฒนาโปรแกรม การทำงานกับไฟล์ไม่ได้สนใจเฉพาะกับแค่การอ่านและเขียนข้อมูลภายในเท่านั้น แต่เราต้องทำการตรวจสอบคุณสมบัติหรือข้อมูลของไฟล์นั้นๆ ด้วย ไม่ว่าจะเป็นขนาด, วันที่สร้าง, วันที่แก้ไข, หรือสิทธิ์การเข้าถึง ข้อมูลเหล่านี้มีส่วนสำคัญในการจัดการไฟล์ให้มีประสิทธิภาพ ช่วยให้เราสามารถตรวจสอบความถูกต้อง,จัดระเบียบ,และจัดการระบบไฟล์ให้ดีขึ้นได้

บทความนี้เราจะนำเสนอวิธีการเข้าถึงข้อมูลพื้นฐานและข้อมูลเกี่ยวกับไฟล์ โดยใช้คำสั่งที่หลากหลาย ซึ่งช่วยให้เราเข้าใจและสามารถจัดการกับไฟล์ต่างๆได้อย่างเป็นระบบระเบียบมากยิ่งขึ้นอย่างแน่นอน

---

### 1. ตรวจสอบไฟล์และโฟลเดอร์มีอยู่จริงหรือไม่

```ruby
File.exist?("report.pdf")    # => true ถ้ามีไฟล์อยู่จริง
File.file?("report.pdf")       # => true ถ้าเป็นไฟล์ธรรมดา  
File.directory?("my_folder") # => true ถ้าเป็นโฟลเดอร์  
```

> **คำอธิบาย**  
> -`exist` ตรวจสอบว่ามีไฟล์นี้อยู่จริงมั้ย
> 
> -`file` ตรวจสอบว่าเป็นไฟล์หรือไม่ (เอกสาร, รูปภาพ, โปรแกรม)
> 
> -`directory` ตรวจสอบว่าเป็นโฟลเดอร์หรือไม่
---

### 2. ตรวจสอบสิทธิ์เข้าถึงไฟล์

```ruby
File.readable?("report.pdf")    # => true ถ้าอ่านไฟล์นี้ได้
File.writable?("report.pdf")    # => true ถ้าเขียนไฟล์นี้ได้
File.executable?("report.pdf")  # => true ถ้าหากรันไฟล์นี้ได้
```

> **คำอธิบาย**  
> ใช้เช็คก่อนทำงานกับไฟล์ว่าเรามีสิทธิ์ทำอะไรได้บ้าง(อ่าน,เขียน,รันไฟล์)
---

### 3. ตรวจสอบขนาดไฟล์

```ruby
File.size("report.pdf")    # => 99 
File.zero?("report.pdf")   # => true ถ้าไฟล์ขนาด 0 bytes
```

> **คำอธิบาย**  
> -`size` ดูขนาดไฟล์หน่วยเป็น (bytes)
> 
> -`zero` เช็คว่าไฟล์ขนาด 0 bytes ใช่ไหม
---

### 4. ตรวจสอบเวลาไฟล์

```ruby
File.ctime("report.pdf")   # => 15/01/2024 09:30
File.mtime("report.pdf")   # => 16/01/2024 14:45
File.atime("report.pdf")   # => 17/01/2024 08:20
```

> **คำอธิบาย**  
> -`ctime` ดูเวลาที่ไฟล์ถูกสร้าง
> 
> -`mtime` ดูเวลาที่เนื้อหาในไฟล์ถูกแก้ไขล่าสุด
>
> -`atime` ดูเวลาที่ไฟล์ถูกเปิดอ่านล่าสุด
---

### 5. การจัดการ Path 

```ruby
File.basename("/path/to/report.pdf")       # => "report.pdf"
File.dirname("/path/to/report.pdf")        # => "/Users/john/ocuments"
File.extname("/path/to/report.pdf")        # => ".pdf"
File.expand_path("../report.pdf")          # => "/home/user/documents/report.pdf"
File.absolute_path("report.pdf")           # => "/Users/john/documents/report.pdf"
```



> **คำอธิบาย**  
> -`basename` ใช้ดึงชื่อไฟล์ออกมา
> 
> -`dirname` ใช้ดึง path ของโฟลเดอร์ที่ไฟล์อยู่
>
> -`extname` ใช้ดึงนามสกุลไฟล์ออกมา
>
> -`expand_path` ใช้แปลง relative path เป็น absolute path
> 
> -`absolute_path` ใช้สร้าง absolute path จาก current directory
---

## เปรียบเทียบกับภาษา (Java, C, Python)

| การตรวจสอบ                | Ruby                                    | Java                                               | C                        | Python                                           |
|----------------------------|----------------------------------------|---------------------------------------------------|---------------------------------|------------------------------------------------|
| ตรวจสอบไฟล์มีอยู่จริง        | `File.exist?`                          | `Files.exists(path)`| `access(path, F_OK)`            | `os.path.exists(path)` / `pathlib.Path(path).exists()` |
| ตรวจสอบไฟล์/โฟลเดอร์        | `File.file?` / `File.directory?`       | `Files.isRegularFile(path)` / `Files.isDirectory(path)` | `S_ISREG` / `S_ISDIR` | `os.path.isfile(path)` / `os.path.isdir(path)` |
| ตรวจสอบสิทธิ์อ่าน/เขียน/รัน | `File.readable?` / `File.writable?` / `File.executable?` | `Files.isReadable(path)` / `Files.isWritable(path)` / `Files.isExecutable(path)` | `access(path, R_OK)` / `access(path, W_OK)` / `access(path, X_OK)` | `os.access(path, os.R_OK)` / `os.access(path, os.W_OK)` / `os.access(path, os.X_OK)` |
| ขนาดไฟล์                    | `File.size`                           | `Files.size(path)`                               | `st_size`              | `os.path.getsize(path)` |
| เวลา (สร้าง/แก้ไข/เข้าถึง)    | `File.ctime` / `File.mtime` / `File.atime` | `Files.getLastModifiedTime(path)` / `Files.getAttribute(path, "creationTime")` *(ไม่มี access time โดยตรง)* | `st_ctime` / `st_mtime` / `st_atime` | `os.stat(path).st_ctime` / `os.stat(path).st_mtime` / `os.stat(path).st_atime` |
| Path Operations             | `File.basename` / `File.dirname` / `File.extname` | `Paths.get(path).getFileName()` / `Paths.get(path).getParent()` *(ไม่มี extension โดยตรง)* | `basename(path)` / `dirname(path)` *(ไม่มีใน POSIX standard)* | `os.path.basename(path)` / `os.path.dirname(path)` / `os.path.splitext(path)` |

---

## คลิปนำเสนอ 
*(ลิงก์ YouTube)*

---

## Presentation (slides)
*(ใส่ลิงก์ ไฟล์ PDF )*

---

## แหล่งที่มาอ้างอิง
- ภาษา ruby ตัวอย่างคำสั่งทั้งหมดของภาษา ruby
- (https://ruby-doc.org/3.4.1/File.html) 
- ภาษา java  ใช้ในการอธิบายตารางตรวจสอบไฟล์มีอยู่จริง,ตรวจสอบไฟล์หรือโฟลเดอร์, ตรวจสอบสิทธิ์ ,ดูขนาดไฟล์ ,ดูเวลา,Path operations
- (https://docs.oracle.com/javase/8/docs/api/java/nio/file/Files.html)
- ภาษา c ใช้ในการอธิบายการตรวจสอบไฟล์มีอยู่จริง,ตรวจสอบไฟล์หรือโฟลเดอร์, ตรวจสอบสิทธิ์ ,ดูขนาดไฟล์ ,ดูเวลา,การจัดการ path
- (https://pubs.opengroup.org/onlinepubs/009695299/functions/access.html)
- (https://pubs.opengroup.org/onlinepubs/009695299/basedefs/sys/stat.h.html)
- ภาษา Python ใช้ในการอธิบายการตรวจสอบไฟล์มีอยู่จริง,ตรวจสอบไฟล์หรือโฟลเดอร์, ตรวจสอบสิทธิ์ ,ดูขนาดไฟล์ ,ดูเวลา,การจัดการ path
- (https://docs.python.org/3/library/os.path.html)
- (https://docs.python.org/3/library/pathlib.html)
- (https://docs.python.org/3/library/stat.html)
