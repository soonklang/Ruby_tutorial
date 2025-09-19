# Quiz ประจำบท

## 1. อธิบายความแตกต่างระหว่าง File.ctime, File.mtime และ File.atime


<details>
<summary>เฉลย</summary>


ctime = เวลาที่ไฟล์ถูกสร้าง หรือ metadata มีการเปลี่ยน

mtime = เวลาที่ไฟล์ถูกแก้ไขล่าสุด (เนื้อหาเปลี่ยน)

atime = เวลาที่ไฟล์ถูกเปิดอ่านล่าสุด
</details>

## 2. เขียนโค้ด Ruby ที่พยายามลบไฟล์ files_not_found.txt และจับข้อยกเว้น 

<details>
<summary>เฉลย</summary>

```ruby
begin File.delete(“files_not_found.txt")
  rescue => e
    puts "Error: #{e.message}" 
end
```
</details>

## 3. เขียนโค้ด Python สำหรับเปลี่ยนชื่อไฟล์ current_file_name เป็น new_file_name และลบไฟล์ file_name โดยใช้โมดูล
 

<details>
<summary>เฉลย</summary>

```python
os.rename(current_file_name, new_file_name)
os.remove(file_name)
```
</details>

