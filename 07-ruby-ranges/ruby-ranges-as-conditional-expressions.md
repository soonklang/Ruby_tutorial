# Ruby Ranges as Conditional Expressions

## สารบัญ
| หัวข้อ |
|---------------|
| [Flip‑Flop Operator คืออะไร](#Flip‑Flop-Operator-คืออะไร) |
| [ตัวอย่างใช้งานใน Ruby](#ตัวอย่างใช้งานใน-Ruby) |
| [ตัวอย่างเพิ่มเติมจากแหล่งอื่น](#ตัวอย่างเพิ่มเติมจากแหล่งอื่น) |
| [เปรียบเทียบกับภาษา C / Java / Python](#เปรียบเทียบกับภาษา-C-/-Java-/-Python) |
| [ตารางเปรียบเทียบโค้ด](#ตารางเปรียบเทียบโค้ด) |
| [แหล่งอ้างอิง](#แหล่งอ้างอิง) |

---

## Flip‑Flop Operator คืออะไร

Ruby รองรับการใช้ **Range** (`expr1..expr2` หรือ `expr1...expr2`) ในฐานะ **Conditional Expression** ที่มีสถานะจำไว้ภายใน (persistent state) เรียกว่า **Flip‑Flop Operator**

- `expr1..expr2` (inclusive): เปิดเมื่อ `expr1` เป็นจริง และปิดใน **รอบเดียวกัน** ที่ `expr2` เป็นจริง  
- `expr1...expr2` (exclusive): เปิดเมื่อ `expr1` เป็นจริง และปิดใน **รอบถัดไป** หลัง `expr2` เป็นจริง  
- เหมาะกับงานกรองข้อมูลในช่วง (range), เช่น การเลือกบรรทัดในไฟล์โดยไม่ต้องใช้ตัวแปร `flag` แยกต่างหาก

---

## ตัวอย่างใช้งานใน Ruby

```ruby
(1..10).each do |x|
  puts x if (x == 2)..(x == 8)
end
```
  **Output**
```
2
3
4
5
6
7
8
```

```ruby
(1..10).each do |x|
  puts x if (x == 4)...(x == 9)
end
```
  **Output**
```
4
5
6
7
8
```

---

## ตัวอย่างเพิ่มเติมจากแหล่งอื่น

- **Parsing ไฟล์เพื่อเพิ่ม indent**  
```ruby
lines = ["start", "indent here", "dedent now", "end"]
lines.each do |line|
  if line =~ /^indent/ .. line =~ /^dedent/
    puts "  " + line
  else
    puts line
  end
end
```
**Output**
```
start
  indent here
  dedent now
end
```

- **กรอง code block**
```ruby
lines = ["text", "BEGIN", "inside block", "END", "after"]
lines.each do |line|
  if line =~ /BEGIN/ .. line =~ /END/
    puts line
  end
end
```
**Output**
```
BEGIN
inside block
END
```

**เปรียบเทียบ inclusive vs exclusive**
- **inclusive**
```ruby
picked = []
0.upto(5) { |v| picked << v if (v == 2)..(v == 5) }
p picked
```
**Output**
```
[2, 3, 4, 5]
```
- **exclusive**
```ruby
picked = []
0.upto(5) { |v| picked << v if (v == 2)...(v == 5) }
p picked
```
**Output**
```
[2, 3, 4]
```

---

## เปรียบเทียบกับภาษา C / Java / Python
- **Ruby**
```ruby
# Ruby
ARGF.each_line { |l| puts l if l =~ /BEGIN/ .. l =~ /END/ }
```
**Output**
```
BEGIN
... เนื้อหาระหว่าง ...
END
```
- **C**
```c
// C
#include <stdio.h>
#include <string.h>
int main() {
    char line[256];
    int on = 0;
    while (fgets(line, sizeof(line), stdin)) {
        if (strstr(line, "BEGIN")) on = 1;
        if (on) printf("%s", line);
        if (strstr(line, "END")) on = 0;
    }
    return 0;
}
```
**Output**
```
BEGIN
... เนื้อหาระหว่าง ...
END
```
- **Java**
```java
// Java
import java.io.*;
public class FlipFlopDemo {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new FileReader("input.txt"));
        String line;
        boolean on = false;
        while ((line = br.readLine()) != null) {
            if (line.contains("BEGIN")) on = true;
            if (on) System.out.println(line);
            if (line.contains("END")) on = false;
        }
        br.close();
    }
}
```
**Output**
```
BEGIN
... เนื้อหาระหว่าง ...
END
```
- **Python**
```python
# Python
on = False
with open("input.txt") as f:
    for line in f:
        if "BEGIN" in line:
            on = True
        if on:
            print(line, end="")
        if "END" in line:
            on = False
```
**Output**
```
BEGIN
... เนื้อหาระหว่าง ...
END
```

---

## ตารางเปรียบเทียบโค้ด

| ภาษา      | Flip‑Flop Equivalent                            |
|-----------|--------------------------------------------------|
| **Ruby**  | `puts ... if /BEGIN/ .. /END/`                   |
| **C / Java / Python** | ต้องใช้ `flag = true/false`, โค้ดยาวกว่า |

---

## แหล่งอ้างอิง

1. **Ruby Official Documentation – Control Expressions**  
   https://docs.ruby-lang.org/en/master/syntax/control_expressions_rdoc.html  
   - ใช้สำหรับอธิบายพฤติกรรมของ **flip-flop operator** (`expr1..expr2` , `expr1...expr2`) และตัวอย่าง `selected << value if value == 2..value == 8`

2. **Techotopia – Ruby Ranges (Conditional Expressions section)**  
   https://www.techotopia.com/index.php/Ruby_Ranges  
   - ใช้สำหรับอธิบาย **Range เป็น Conditional Expression** และตัวอย่างการอ่านไฟล์ด้วย flip-flop

3. **TutorialsPoint – Ruby Ranges**  
   https://www.tutorialspoint.com/ruby/ruby_ranges.htm  
   - ใช้ในการเสริมตัวอย่าง flip-flop และการอธิบาย inclusive (`..`) vs exclusive (`...`)

4. **GeeksforGeeks – Ruby Ranges**  
   https://www.geeksforgeeks.org/ruby/ruby-ranges/  
   - ใช้สนับสนุนคำอธิบายว่า Range สามารถใช้ตรวจสอบช่วงค่าได้

5. **Nithin Bekal – Blog: Ruby Flip-Flop Operator**  
   https://nithinbekal.com/posts/ruby-flip-flop/  
   - ใช้สำหรับตัวอย่างการ **parsing ไฟล์และเพิ่ม indent** โดยใช้ flip-flop

6. **Scout APM Blog – Ruby Flip-Flop**  
   https://www.scoutapm.com/blog/ruby-flip-flop  
   - ใช้สำหรับตัวอย่าง loop `(1..10).each do |x| ...` และอธิบายการทำงานของ flip-flop

7. **Stack Overflow Discussions**  
    - [When would a Ruby flip-flop be useful?](https://stackoverflow.com/questions/1111286/when-would-a-ruby-flip-flop-be-useful)  
    - [Why does a flip-flop operator include the second condition?](https://stackoverflow.com/questions/18600011/why-does-a-flip-flop-operator-include-the-second-condition)  
        ใช้สำหรับอธิบาย **กรณีใช้งานจริง** เช่น การกรองบรรทัดจากไฟล์ และการอธิบายพฤติกรรม inclusive vs exclusive

8. **C Reference (strstr function)**  
    https://en.cppreference.com/w/c/string/byte/strstr  
    - ใช้อ้างอิงการตรวจสอบ substring ในโค้ดตัวอย่างภาษา C

9. **Java SE Documentation – BufferedReader**  
    https://docs.oracle.com/javase/8/docs/api/java/io/BufferedReader.html  
    - ใช้อ้างอิงวิธีอ่านไฟล์ทีละบรรทัดในโค้ดตัวอย่าง Java

10. **Python Official Docs – Reading and Writing Files**  
    https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files  
    - ใช้อ้างอิงวิธีอ่านไฟล์แบบ line-by-line ในตัวอย่างภาษา Python

