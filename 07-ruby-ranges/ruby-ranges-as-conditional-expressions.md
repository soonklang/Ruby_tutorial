# Ruby Ranges as Conditional Expressions

## สารบัญ
| หัวข้อ |
|---------------|
| [Flip-Flop Operator คืออะไร](#flipflop-operator-คืออะไร) |
| [ตัวอย่างใช้งานใน Ruby](#ตัวอย่างใช้งานใน-ruby) |
| [ทำไมมันแตกต่างใน `..` และ `...`](#ทำไมมันแตกต่างใน-`..`-และ-`...`) |
| [ตัวอย่างเพิ่มเติมจากแหล่งอื่น](#ตัวอย่างเพิ่มเติมจากแหล่งอื่น) |
| [เปรียบเทียบกับภาษา C / Java / Python](#เปรียบเทียบกับภาษา-c--java--python) |
| [ตารางเปรียบเทียบโค้ด](#ตารางเปรียบเทียบโค้ด) |
| [Slide & Video](#Slide-&-Video) |
| [แหล่งอ้างอิง](#แหล่งอ้างอิง) |

---

## Flip-Flop Operator คืออะไร

Ruby รองรับการใช้ **Range** (`condition1..condition2` หรือ `condition1...condition2`) ในฐานะ **Conditional Expression** ที่มีสถานะจำไว้ภายใน (persistent state) เรียกว่า **Flip-Flop Operator**

- Ruby flip-flop operator ใช้สัญลักษณ์ `..` หรือ `...` เป็นตัวกำหนดสถานะ on/off (เปิด/ปิด) ภายในเงื่อนไขในลูป
- มันเริ่ม เปิด (true) เมื่อเงื่อนไขซ้าย (`condition1`) เป็นจริง และจะ ปิดทันทีหลังรอบนั้น หากใช้ `..` (inclusive range)
- หากใช้ `...` (exclusive range) เงื่อนไขขวา (`condition2`) จะถูกประเมินในรอบถัดไป ซึ่งส่งผลให้รันบล็อคในรอบนั้นเพิ่มเติมอีกครั้งก่อนปิด
- เหมาะกับงานกรองข้อมูลในช่วง (range), เช่น การเลือกบรรทัดในไฟล์โดยไม่ต้องใช้ตัวแปร `flag` แยกต่างหาก

Flip-flop ทำงานเหมือน *สวิตช์เปิด-ปิด* ที่จดจำสถานะของตัวเอง ซึ่งในภาษาอื่น (C, Java, Python) ต้องใช้ตัวแปร `flag` คอยเก็บสถานะ แต่ Ruby ทำได้สั้นกว่า

---

## ตัวอย่างใช้งานใน Ruby
### ตัวอย่างที่ 1
`(x == 1)..(x == 3)`

ในตัวอย่างนี้ flip-flop จะเปิดเมื่อ `x == 1` และปิดเมื่อ `x == 3` จึงได้ตัวเลขเฉพาะในช่วงดังกล่าว
```ruby
# inclusive flip-flop
[0,1,2,3,4].each do |x|
  if (x == 1)..(x == 3)
    puts "Flip-flop active: #{x}"
  else
    puts "Flip-flop inactive: #{x}"
  end
end

```
**Output**
```
Flip-flop inactive: 0
Flip-flop active: 1
Flip-flop active: 2
Flip-flop active: 3
Flip-flop inactive: 4
```
- Flip-flop จะเปิดเมื่อ `x == 1` และปิดเลยเมื่อตอน `x == 3` (รันในรอบนั้นด้วย)
อีกตัวอย่าง ใช้ `...` (exclusive) 

```ruby
# exclusive flip-flop
[0,1,2,3,4].each do |x|
  if (x == 1)...(x == 3)
    puts "Flip-flop active: #{x}"
  else
    puts "Flip-flop inactive: #{x}"
  end
end
```
**Output**
```
Flip-flop inactive: 0
Flip-flop active: 1
Flip-flop active: 2
Flip-flop active: 3
Flip-flop inactive: 4
```
- ด้วย `...` evaluator จะยังประมวลผลรอบ `x == 3` ก่อนปิด ทำให้ output เหมือนตัวอย่าง inclusive ในเคสนี้
---
### ตัวอย่างที่ 2 
`(x==-1)..(x==1)`
- ใช้ `..` (inclusive)
```ruby
[0,1,2,3,4].each do |x|
    if (x==-1)..(x==1) # first condition never true
        puts "Flip-flop active: #{x}"
    else
        puts "Flip-flop inactive: #{x}"
    end
end
```
- เงื่อนไขซ้ายคือ `(x == -1)` → ซึ่งจะ ไม่เป็นจริงเลย เพราะในลูปมีค่าแค่ `0..4`
- Flip-flop จะเริ่มทำงาน ก็ต่อเมื่อเงื่อนไขซ้ายเป็นจริงครั้งแรก
- เนื่องจากมันไม่เคยเป็นจริงเลย → flip-flop ไม่เคยเปิด → ผลลัพธ์คือ inactive ทุกครั้ง

**Output**
```
Flip-flop inactive: 0
Flip-flop inactive: 1
Flip-flop inactive: 2
Flip-flop inactive: 3
Flip-flop inactive: 4
```

- ใช้ `...` (exclusive)
```ruby
[0,1,2,3,4].each do |x|
    if (x==1)...(x==1) # three-dot operator; if true … true
        puts "Flip-flop active: #{x}"
    else
        puts "Flip-flop inactive: #{x}"
    end
end
```
- ที่ `x=0` → `(0 != 1)` เป็น `false` → flip-flop ยังไม่เริ่ม → `inactive`
- ที่ `x=1` → `(1 == 1)` เป็น `true` → flip-flop เริ่มเปิด → แสดง `active: 1`
- เนื่องจากเป็น `...` (exclusive) มัน ยังไม่ปิดในรอบเดียวกัน แม้เงื่อนไขขวาจะเป็นจริงแล้วจะปิดใน รอบถัดไป
- ที่ `x=2` ถึง `x=4` → flip-flop ยัง “ค้างอยู่ในสถานะเปิด” → จึงยัง active ทั้งหมด
**Output**
```
Flip-flop inactive: 0
Flip-flop active: 1
Flip-flop active: 2
Flip-flop active: 3
Flip-flop active: 4
```
---

## ทำไมมันแตกต่างใน `..` และ `...`

| Operator      | Flip-Flop                            |
|-----------|--------------------------------------------------|
| `..`  | ปิดทันทีในรอบที่เงื่อนไขขวาเป็นจริง                  |
| `...` | ปิดในรอบถัดไปหลังที่เงื่อนไขขวาเป็นจริง |

---

## ตัวอย่างเพิ่มเติมจากแหล่งอื่น

### Parsing ไฟล์
Flip-flop ช่วยเลือกบรรทัดที่อยู่ระหว่างคำว่า `indent` และ `dedent` โดยอัตโนมัติ

```ruby
lines = ["zero indentation", "indent", "inside block", "dedent", "after the block", "indent", "another block", "dedent", "end of file"]
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
zero indentation
  indent
  inside block
  dedent
after the block
  indent
  another block
  dedent
end of file
```

### กรอง code block
ในตัวอย่างนี้จะพิมพ์เฉพาะบรรทัดที่อยู่ระหว่าง `BEGIN` และ `END`

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

---

## เปรียบเทียบกับภาษา C / Java / Python

ใน Ruby เขียนเพียงบรรทัดเดียว ก็เลือกบรรทัดที่อยู่ระหว่าง BEGIN และ END ได้ โดยไม่ต้องใช้ตัวแปร `flag`

```ruby
# Ruby
input = <<~DATA
line 1
BEGIN
inside 1
inside 2
END
line 2
DATA

input.each_line do |l|
  puts l if l =~ /BEGIN/ .. l =~ /END/
end
```
**Output**
```
BEGIN
inside 1
inside 2
END
```

แต่ในภาษา C ต้องใช้ `flag` เพื่อจำสถานะ

```c
#include <stdio.h>
#include <string.h>
int main() {
    const char *lines[] = {
        "line 1",
        "BEGIN",
        "inside 1",
        "inside 2",
        "END",
        "line 2"
    };
    int n = sizeof(lines)/sizeof(lines[0]);
    int on = 0;
    for (int i = 0; i < n; i++) {
        if (strstr(lines[i], "BEGIN")) on = 1;
        if (on) printf("%s\n", lines[i]);
        if (strstr(lines[i], "END")) on = 0;
    }
    return 0;
}
```
**Output**
```
BEGIN
inside 1
inside 2
END
```

โค้ด Java ก็ต้องใช้ `boolean flag`

```java
import java.io.*;
public class FlipFlopDemo {
    public static void main(String[] args) {
        String[] lines = {
            "line 1",
            "BEGIN",
            "inside 1",
            "inside 2",
            "END",
            "line 2"
        };
        boolean on = false;
        for (String line : lines) {
            if (line.contains("BEGIN")) on = true;
            if (on) System.out.println(line);
            if (line.contains("END")) on = false;
        }
    }
}
```
**Output**
```
BEGIN
inside 1
inside 2
END
```

ใน Python ก็เช่นกัน

```python
lines = [
    "line 1",
    "BEGIN",
    "inside 1",
    "inside 2",
    "END",
    "line 2"
]

on = False
for line in lines:
    if "BEGIN" in line:
        on = True
    if on:
        print(line)
    if "END" in line:
        on = False
```
**Output**
```
BEGIN
inside 1
inside 2
END
```

---

## ตารางเปรียบเทียบโค้ด

| ภาษา      | Flip-Flop                            |
|-----------|--------------------------------------------------|
| **Ruby**  | `puts line if /BEGIN/ .. /END/`                  |
| **C / Java / Python** | ต้องใช้ `flag = true/false` เพื่อติดตามสถานะ |

**ข้อสรุป** Ruby ใช้ flip-flop operator ได้ในตัว แต่ C / Java / Python ต้องใช้ตัวแปร flag เพิ่มเติม ดังนั้น Ruby กระชับและอ่านง่ายกว่าในกรณีนี้

---
## Slide & Video

---

## แหล่งอ้างอิง

1. **Ruby Official Documentation – Control Expressions**  
   https://docs.ruby-lang.org/en/master/syntax/control_expressions_rdoc.html  
   - ใช้อธิบายพฤติกรรมของ flip-flop operator

2. **Techotopia – Ruby Ranges (Conditional Expressions section)**  
   https://www.techotopia.com/index.php/Ruby_Ranges  
   - ใช้อธิบาย Range เป็น Conditional Expression และตัวอย่างการอ่านไฟล์ด้วย flip-flop

3. **TutorialsPoint – Ruby Ranges**  
   https://www.tutorialspoint.com/ruby/ruby_ranges.htm  
   - ใช้เสริมตัวอย่าง flip-flop

4. **GeeksforGeeks – Ruby Ranges**  
   https://www.geeksforgeeks.org/ruby/ruby-ranges/  
   - ใช้สนับสนุนคำอธิบาย Range as Conditional Expressions และ inclusive (`..`) กับ exclusive (`...`)

5. **Nithin Bekal – Blog: Ruby Flip-Flop Operator**  
   https://nithinbekal.com/posts/ruby-flip-flop/  
   - ใช้สำหรับตัวอย่าง parsing ไฟล์

6. **Scout APM Blog – Ruby Flip-Flop**  
   https://www.scoutapm.com/blog/ruby-flip-flop  
   - ใช้สำหรับตัวอย่าง `[0,1,2,3,4].each do |x|` และตัวอย่าง flip-flop ที่แสดงความแตกต่างระหว่าง inclusive (`..`) กับ exclusive (`...`)

7. **Stack Overflow Discussions**  
   - [When would a Ruby flip-flop be useful?](https://stackoverflow.com/questions/1111286/when-would-a-ruby-flip-flop-be-useful)  
   - [Why does a flip-flop operator include the second condition?](https://stackoverflow.com/questions/18600011/why-does-a-flip-flop-operator-include-the-second-condition)  
   - ใช้สำหรับกรณีใช้งานจริง เช่น กรองบรรทัดจากไฟล์ และอธิบาย inclusive/exclusive

8. **C Reference (strstr function)**  
   https://en.cppreference.com/w/c/string/byte/strstr  
   - ใช้อ้างอิงการตรวจสอบ substring ในโค้ด C

9. **Java SE Documentation – BufferedReader**  
   https://docs.oracle.com/javase/8/docs/api/java/io/BufferedReader.html  
   - ใช้อ้างอิงวิธีอ่านไฟล์ทีละบรรทัด (ตัวอย่างนี้ใช้ array)

10. **Python Official Docs – Reading and Writing Files**  
    https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files  
    - ใช้อ้างอิงวิธีอ่านไฟล์ line-by-line (ตัวอย่างนี้ใช้ list)
---
