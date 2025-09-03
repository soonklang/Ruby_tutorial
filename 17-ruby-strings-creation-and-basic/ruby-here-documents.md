# Ruby Here Documents

## บทนำ

Here document  หรือบางคนเรียกสั้นๆ ว่า Heredoc คือวิธีที่ช่วยให้เราเขียนข้อความยาวๆ หลายบรรทัดแบบง่ายๆ ไม่ต้องยุ่งยาก ไม่ต้องมาต่อ string ทีละบรรทัด นิยมใช้ในการประมวลผลข้อความขนาดใหญ่ หรือเขียนโค้ดที่เน้นความอ่านง่าย

---

## หลักการของ Here Document ในแต่ละภาษา

### Heredoc ใน Ruby ใช้งานยังไง?

ใน Ruby ถ้าอยากเขียนข้อความยาวๆ หลายบรรทัด ก็แค่ใช้เครื่องหมาย `<<` ตามด้วยชื่ออะไรก็ได้ แล้วพิมพ์ข้อความที่เราต้องการได้เลย พอพิมพ์จบเเล้วก็ใส่ชื่อเดิมที่เราพิมพ์ต่อจากเครื่องหมาย `<<`

**ตัวอย่าง:**

```ruby
str = <<TEXT
Hello, Welcome to heredoc.
This supports interpolation.
TEXT

puts str
```

**ผลลัพธ์:**
```
Hello, Welcome to heredoc.
This supports interpolation.
```

**สรุปง่ายๆ:** 
- พิมพ์ข้อความยาวแค่ไหนก็ได้   
- อ่านง่าย เขียนง่าย ไม่ต้องต่อ string เยอะ

---

## Interpolation คืออะไร?

**Interpolation** คือการแทรกค่าของตัวแปรหรือข้อความลงไปใน string ได้เลย เช่น ถ้ามีตัวแปรชื่อ `name` แล้วอยากให้มันไปอยู่ในข้อความ ก็ใช้ `#{name}` แบบนี้

**ตัวอย่าง:**

```ruby
age = 15
str = <<TEXT
สวัสดี ฉันอายุ #{age} ปี
TEXT

puts str
```

**ผลลัพธ์:**
```
สวัสดี ฉันอายุ 15 ปี
```

**สรุปง่ายๆ:**  
- ใน `#{...}` ไม่จำกัดว่าจะต้องเป็น datatype อะไร เพราะ Ruby จะเรียก to_s หรือการเเปลงเป็น String ของผลลัพธ์นั้นให้อัตโนมัติ
- ใช้ `#{...}` เพื่อแทรกค่าในตัวแปรที่เราลงในข้อความ
- ช่วยให้ข้อความดูดีและเปลี่ยนแปลงตามค่าตัวแปรได้เลย

---

## Single-Quoted Heredoc กับ Double-Quoted Heredoc ต่างกันยังไง?

เวลาเขียน heredoc ใน Ruby เราสามารถเลือกได้ว่าจะให้มันทำงานเหมือน string แบบไหน  
- แบบ **double-quoted** (ใช้ `<<IDENTIFIER` หรือ `<<"IDENTIFIER"`) จะให้แทรกตัวแปรได้  
- แบบ **single-quoted** (ใช้ `<<'IDENTIFIER'`) จะไม่แทรกตัวแปร ทุกอย่างจะเป็นข้อความตรงๆ

**ตัวอย่าง Double-Quoted Heredoc (แทรกตัวแปรได้):**

```ruby
name = "Ruby"
str = <<"TEXT"
Hello, #{name}!
TEXT

puts str
```

**ผลลัพธ์:**
```
Hello, Ruby!
```

**ตัวอย่าง Single-Quoted Heredoc (แทรกตัวแปรไม่ได้):**

```ruby
name = "Ruby"
str = <<'TEXT'
Hello, #{name}!
TEXT

puts str
```

**ผลลัพธ์:**
```
Hello, #{name}!
```

**สรุปง่ายๆ:**  
- **double-quoted**: แทรกตัวแปรได้  
- **single-quoted**: แทรกตัวแปรไม่ได้ ทุกอย่างเป็นข้อความตรงๆ

---

## Indentation ใน Heredoc คืออะไร?

**Indentation** คือช่องว่างหรือ tab ที่นำหน้าแต่ละบรรทัดของข้อความ เวลาพิมพ์ heredoc บางทีเราอยากให้ข้อความใน heredoc ขยับไปตามโค้ดที่อยู่ข้างใน เราสามารถใช้ `<<-IDENTIFIER` หรือ `<<~IDENTIFIER` เพื่อให้ Ruby ตัดช่องว่าง (space) ข้างหน้าข้อความออกให้เอง

**ตัวอย่าง Indentation แบบมีตัดช่องว่าง (ใช้ <<~):**

```ruby
str = <<~TEXT
      สวัสดี
      ข้อความนี้จะอยู่ชิดซ้ายหมดเลย
      แม้ว่าในโค้ดจะมีช่องว่างข้างหน้า
TEXT

puts str
```

**ผลลัพธ์:**
```
สวัสดี
ข้อความนี้จะอยู่ชิดซ้ายหมดเลย
แม้ว่าในโค้ดจะมีช่องว่างข้างหน้า
```

**ถ้าใช้ <<- หรือ << เฉยๆ ช่องว่างหน้าข้อความจะไม่ถูกตัดออก**

**สรุปง่ายๆ:**  
- ถ้าอยากให้ข้อความใน heredoc ชิดซ้ายตลอด ใช้ `<<~IDENTIFIER`  
- ถ้าไม่ใช้ ช่องว่างจะติดไปกับข้อความด้วย

---

## ภาษาอื่นๆ เขาทำกันยังไง?

### C

C ไม่มี here document โดยตรง ต้องใช้การเชื่อม string เองทีละบรรทัด

**ตัวอย่าง:**

```c
#include <stdio.h>

int main() {
    char *str = "Hello, C!\n"
                "No heredoc support.\n"
                "Strings must be concatenated.";
    printf("%s\n", str);
    return 0;
}
```

**ผลลัพธ์:**
```
Hello, C!
No heredoc support.
Strings must be concatenated.
```

**คำอธิบาย:**  
- ไม่มี syntax เฉพาะสำหรับ heredoc  
- ต้องใช้การเชื่อม string หลายบรรทัดแบบ manual  
- ไม่รองรับ interpolation โดยตรง

---

### Java

Java เวอร์ชั่นใหม่ๆ (Java 15 ขึ้นไป) มีฟีเจอร์คล้าย heredoc เรียกว่า Text Block ใช้เครื่องหมาย `"""` ได้

**ตัวอย่าง:**

```java
public class Main {
    public static void main(String[] args) {
        String str = """
            Hello, Java!
            This is a text block.
            Multiline string supported.
            """;
        System.out.println(str);
    }
}
```

**ผลลัพธ์:**
```
Hello, Java!
This is a text block.
Multiline string supported.
```

**คำอธิบาย:**  
- Text block (`"""`) เป็น multiline string  
- ไม่รองรับ interpolation แบบ Ruby  
- Syntax ใกล้เคียง heredoc

---

### Python

Python เขียนข้อความหลายบรรทัดได้ง่ายๆ ด้วย triple quotes (`"""` หรือ `'''`) แถมถ้าอยากใส่ตัวแปรก็ใช้ f-string ได้เลย

**ตัวอย่าง:**

```python
name = "Python"
str = f"""Hello, {name}!
This is a triple-quoted string.
Supports interpolation with f-string.
"""
print(str)
```

**ผลลัพธ์:**
```
Hello, Python!
This is a triple-quoted string.
Supports interpolation with f-string.
```

**คำอธิบาย:**  
- ใช้ triple quotes สร้าง string หลายบรรทัด  
- รองรับ interpolation ด้วย f-string  
- Syntax ไม่เหมือน heredoc แต่ผลลัพธ์คล้ายกัน

---

## เปรียบเทียบความเหมือนและแตกต่าง

| ภาษา    | Syntax เฉพาะ | รองรับ Multiline | Interpolation | ความอ่านง่าย |
|---------|--------------|------------------|---------------|--------------|
| Ruby    | มี (<<)      | มี               | มี            | ดี           |
| C       | ไม่มี        | มี (เชื่อมเอง)   | ไม่มี         | น้อย         |
| Java    | มี (""")     | มี               | ไม่มี         | ดี           |
| Python  | มี (""")     | มี               | มี (f-string) | ดี           |

---

## แหล่งข้อมูลอ้างอิง

1. [Ruby Here Document - Ruby Documentation](https://ruby-doc.org/core-2.7.0/doc/syntax/literals_rdoc.html#label-Here+Documents) *(น่าเชื่อถือ)*
2. [Java Text Blocks - Oracle Documentation](https://docs.oracle.com/en/java/javase/17/language/text-blocks.html) *(น่าเชื่อถือ)*
3. [Python String Literals - Python Docs](https://docs.python.org/3/reference/lexical_analysis.html#string-and-bytes-literals) *(น่าเชื่อถือ)*
4. [C String Literals - C Reference](https://en.cppreference.com/w/c/language/string_literal)
5. [Ruby Heredoc Guide - TutorialsPoint](https://www.tutorialspoint.com/ruby/ruby_strings.htm)

---

# Presentation

# Slide

