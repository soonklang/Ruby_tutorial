# Converting a Ruby String to an Array
## การแปลง String ในภาษา Ruby ให้เป็น Array

สำหรับตัวของ split นั้นถือว่าเป็น method ที่มีประโยชน์มากของ String ที่มีวัตถุประสงค์ในการเอามาแยกประโยคต่าง ๆ ให้เป็น Array ที่ประกอบด้วย **'คำ'** หรือ **'ตัวอักษร'** ที่ถูกแยกออกมา โดยมีรูปแบบการใช้ดังต่อไปนี้
> [!IMPORTANT]
> **split(pattern=nil, [limit])**<br>
> - pattern=nil เป็นตัวที่เราใช้เพื่อบอกว่าจะ 'ตัด' ตามรูปแบบไหนหรือตัวไหน <br>
> - [limit] จำนวนชิ้นสูงสุดที่ตัดได้ (โดยจะกำหนดหรือไม่ก็ได้)

สำหรับรูปแบบที่ใช้แยกหรือตัดคำนั้นมีหลากหลายแบบให้ใช้ ยกตัวอย่างต่อไปนี้<br>
**แบบที่ 1 (ไม่ใส่ค่าของ pattern ใดใดเลย)**<br>
```Ruby
#แยกตาม whitespace (ช่องว่าง, tab, newline)
# str.split
"ABCDEFGHIJKL".split         #=> [ABCDEFGHIJKL]
"hello world ruby".split     #=> ["hello", "world", "ruby"]
```
***
**แบบที่ 2 (ใช้รูปแบบ string ในการแบ่ง)**<br>
```Ruby
# str.split("string")
"ABCDEFGHIJKL".split("F")    #=> ["ABCDE","GHIJKL"]
"a,b,c".split(",")           #=> ["a", "b", "c"]
```
***
**แบบที่ 3 (ใช้รูปแบบ regex ในการแบ่ง)**<br>
<details>
<summary>ตัวอย่างรูปแบบของ regex ที่พบเจอได้บ่อย</summary>

- `//` regex ว่าง ใช้เพื่อแยกตัวอักษรทุกตัว
- `/ /` ใช้เพื่อแยกตาม white space
- `\d` ใช้เพื่อแยกเมื่อเจอตัวเลข
- `/\s+/` ใช้เพื่อแยกเมื่อเจอ white space หลายตัว
</details>

```Ruby
# str.split(/regex/)
"one two three".split(/\s+/)          #=> ["one", "two", "three"]
"cat123dog456mouse".split(/\d+/)      #=> ["cat", "dog", "mouse"]
```
***
**แบบที่ 4 (ใช้ limit เข้ามาช่วย)**<br>
```Ruby
# str.split(pattern, [limit])
"a,b,c,d".split(",", 2)    #=> ["a", "b,c,d"]
"1,2,3,".split(",", -1)    #=> ["1", "2", "3", ""]
```
> [!WARNING]
> #### ข้อควรระวัง
> เมื่อมีการใช้ limit เข้ามาเกี่ยวข้อง จะมีเรื่องที่ควรใส่ใจนั่นคือ Trailing empty fields (ช่องว่างที่เกิดจากการแบ่งต่อท้าย string) โดยมีเงื่อนไขดังต่อไปนี้
> - ค่า limit >= 0 หรือไม่ใส่ ภาษา Ruby จะตัด Trailing empty fields ทิ้งอัตโนมัติ
> - ค่า limit < 0  ภาษา Ruby จะเก็บ Trailing empty fields ไว้

***
<br>

> [!TIP]
➕ split สามารถเอามาปรับใช้กับความเรียงต่าง ๆ ได้ด้วยเช่นกัน เนื่องจากคำที่ถูกแยกออกมาจะมีการจัดเก็บเป็น Array แล้วหลังจากนั้นก็ใช้ `array.size()` เพื่อทำให้สามารถนับจำนวนคำได้ที่อยู่ใน Array ได้<br>
```Ruby
str = "Lorem Ipsum is simply dummy text"
p str.split.size
```
<details>
<summary>Output: </summary>

<pre>6</pre>
</details>

> [!TIP]
➕ เช่นเดียวกันกับการแยกตัวอักษร หากว่าเราอยากรู้ว่าในประโยคหรือความเรียงนั้นมีตัวหนังสือทั้งหมดกี่ตัว เราเองก็สามารถประยุกต์ใช้ split และ size ได้<br>
```Ruby
str = "Lorem Ipsum is simply dummy text"
p str.split(//).size
```
<details>
<summary>Output: </summary>

<pre>32</pre>
</details>

***


<br>

### การเปรียบเทียบ Split กับภาษาอื่น ๆ
### C
ภาษา C ไม่ได้มี method ที่ชื่อว่า split อยู่เลย แต่สำหรับการแยกหรือตัดแบ่งข้อความนั้น มี method อื่นที่ถูกสร้างมาเพื่อใช้ในวัตถุประสงค์เดียวกัน<br>
`strtok()` ฟังก์ชันนี้อยู่ในไลบารี <string.h> ถูกใช้เพื่อแบ่ง string ออกเป็น token ตามตัวคั่นที่ตั้งขึ้นมา

> [!IMPORTANT]
> 1. `strtok()` จะทำให้ผลลัพธ์ที่ออกมาของ string นั้นเปลี่ยนไป เพราะฟังก์ชันนี้มีลักษณะเป็น destructive ที่จะเข้าไปเปลี่ยนแปลงข้อมูลต้นฉบับโดยตรง ไม่ใช่เพียงแค่อ่านข้อมูลเฉย ๆ โดยภาษา C จะเขียน `\0` ลงไปแทนที่ตัวคั่นที่เราตั้งเอาไว้
> 2. ภาษา C ไม่รองรับตัวคั่น delimiter patchwork/regex หลายแบบเหมือนภาษาอื่น ๆ ได้ แต่ก็ยังสามารถใส่เป็น string ที่มีหลายตัวอักษรได้ เช่น `",;|"`

ตัวอย่าง
```C
#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "apple,banana,cherry";
    char *delimiter = ",";
    char *token;

    token = strtok(str, delimiter);
    while (token != NULL) {
        printf("%s\n", token);
        token = strtok(NULL, delimiter);
    }
    return 0;
}
```

<details>
<summary>Output: </summary>

<pre>apple
banana
cherry</pre>
</details>

<br>

### JAVA
ภาษา JAVA นั้นมีเมธอดที่ชื่อว่า split ของ String ที่สามารถแยกข้อความออกมาเป็น Array ตามตัวคั่นเช่นเดียวกับ Ruby เลย

> [!WARNING]
> - ตัวคั่นของภาษา JAVA จะต้องเป็นรูปแบบ regex เท่านั้น
> - หากว่าตัวคั่นนั้นมีความหมายพิเศษในตัวของมัน เช่น `. | ^ () $ ? *` เป็นต้น จำเป็นต้องใช้ `\\` เพื่อ escape และสื่อสารกับโปรแกรมว่า **หมายถึงตัวอักษรเหล่านี้จริง ๆ ไม่ใช่ความหมายพิเศษ**

> [!IMPORTANT]
> **public String[] split(String regex, int limit)** <br>
> limit จะกำหนดหรือไม่ก็ได้ (สำหรับข้อควรระวังของ limit ในภาษา JAVA เป็นแบบเดียวกับของ [Ruby](#ข้อควรระวัง))



***
### Video Presentation
***
### Reference
Carmatec. (n.d.). Ruby’s string split: A complete guide with examples. https://www.carmatec.com/blog/rubys-string-split-a-complete-guide-with-examples/<br>
cppreference.com. (n.d.). strtok. https://en.cppreference.com/w/c/string/byte/strtok<br>
Flanagan, D., & Matsumoto, Y. (2008). The Ruby Programming Language (p. 305). O’Reilly Media.<br>
GeeksforGeeks. (n.d.). Ruby | String split() method with examples. https://www.geeksforgeeks.org/ruby/ruby-string-split-method-with-examples/<br>
Ghosh, S. S. (2017). Comprehensive Ruby Programming (pp. 48–51). Packt Publishing.<br>
Loosemore, S., Stallman, R. M., McGrath, R., Oram, A., & Drepper, U. (2019). The GNU C library reference manual (pp. 129–131). Free Software Foundation. https://www.gnu.org/software/libc/manual/pdf/libc.pdf<br>
Ruby-Doc.org. (n.d.). Class: String (Ruby 1.9.1). https://ruby-doc.org/core-1.9.1/String.html<br>
Ruby-Doc.org. (n.d.). Class: String (Ruby 2.4.5). https://ruby-doc.org/core-2.4.5/String.html<br>
Ruby-Doc.org. (n.d.). Class: String (Ruby 3.0.7). https://ruby-doc.org/3.0.7/String.html<br>
Techotopia. (n.d.). Ruby string conversions. Techotopia. https://www.techotopia.com/index.php/Ruby_String_Conversions<br>
The Open Group. (n.d.). strtok - split string into tokens. In The Open Group Base Specifications Issue 7, IEEE Std 1003.1-2017. https://pubs.opengroup.org/onlinepubs/9699919799/functions/strtok.html<br>
Thomas, D., Fowler, C., & Hunt, A. (2013). Programming Ruby 1.9 & 2.0: The Pragmatic Programmers’ Guide (Fourth Edition, p. 685). Pragmatic Bookshelf.<br>



<pre>python<br>print("Hi")<br></pre>
`inline code`
```
ภาษา
โค้ดตรงนี้
```
ตัวอย่าง

<pre>| A | B |
|---|---|
| 1 | 2 |</pre>

| หัวข้อ1 | หัวข้อ2 |
|---------|---------|
| แถว1คอลัมน์1 | แถว1คอลัมน์2 |
| แถว2คอลัมน์1 | แถว2คอลัมน์2 |

<details>
<summary>Click to toggle contents of `code`</summary>

```
CODE!
```
</details>
Link to the sample section: [Link Text](#sample-section).
