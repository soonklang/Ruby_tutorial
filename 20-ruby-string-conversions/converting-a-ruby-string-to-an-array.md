# Converting a Ruby String to an Array
#### การแปลง String ในภาษา Ruby ให้เป็น Array

### Split() ในภาษา Ruby
สำหรับตัวของ split นั้นถือว่าเป็น method ที่มีประโยชน์อย่างมากของ String ที่มีวัตถุประสงค์ในการเอามาแยกประโยคต่าง ๆ ให้เป็น Array ที่ประกอบด้วย **'คำ'** หรือ **'ตัวอักษร'** ที่ถูกแยกออกมา โดยมีรูปแบบการใช้ดังต่อไปนี้
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

> [!IMPORTANT]
> **strtok(str, delimiter)** <br>
> `strtok()` ฟังก์ชันนี้อยู่ในไลบารี <string.h> ถูกใช้เพื่อแบ่ง string ออกเป็น token ตามตัวคั่นที่ตั้งขึ้นมา

> [!WARNING]
> 1. `strtok()` จะทำให้ผลลัพธ์ที่ออกมาของ string นั้นเปลี่ยนไป เพราะฟังก์ชันนี้มีลักษณะเป็น destructive ที่จะเข้าไปเปลี่ยนแปลงข้อมูลต้นฉบับโดยตรง ไม่ใช่เพียงแค่อ่านข้อมูลเฉย ๆ โดยภาษา C จะเขียน `\0` ลงไปแทนที่ตัวคั่นที่เราตั้งเอาไว้
> 2. ภาษา C ไม่รองรับตัวคั่น delimiter patchwork/regex หลายแบบเหมือนภาษาอื่น ๆ ได้ แต่ก็ยังสามารถใส่เป็น string ที่มีหลายตัวอักษรได้ เช่น `",;|"`
> 3. `strtok()` ในภาษา C ไม่มีพารามิเตอร์ limit โดยตรงเหมือนกับ Ruby แต่มันจะวนลูปแยกจนกว่าจะเหลือค่าเป็น NULL หรือวนลูปไปเรื่อย ๆ เท่าที่ข้อมูล string เดิมจะยังมี delimiter ที่กำหนดเอาไว้
> 4. หากต้องการกำหนดค่า limit ในภาษา C นั้น จะต้องเขียนโค้ดออกมาเอง อาจจะใช้หลักการของการจำกัดรอบลูปแล้ว break ออกมาเมื่อได้จำนวนที่ต้องการแล้ว

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

### Java
ภาษา Java นั้นมีเมธอดที่ชื่อว่า split ของ String ที่สามารถแยกข้อความออกมาเป็น Array ตามตัวคั่นเช่นเดียวกับ Ruby เลย

> [!IMPORTANT]
> **public String[] split(String regex, int limit)** <br>
> - limit จะกำหนดหรือไม่ก็ได้ (สำหรับข้อควรระวังของ limit ในภาษา Java เป็นแบบเดียวกับของ [Ruby](#ข้อควรระวัง))

> [!WARNING]
> - ตัวคั่นของภาษา Java จะต้องเป็นรูปแบบ regex เท่านั้น
> - หากว่าตัวคั่นนั้นมีความหมายพิเศษในตัวของมัน เช่น `. | ^ () $ ? *` เป็นต้น จำเป็นต้องใช้ `\\` เพื่อ escape และสื่อสารกับโปรแกรมว่า **หมายถึงตัวอักษรเหล่านี้จริง ๆ ไม่ใช่ความหมายพิเศษ**



ตัวอย่าง
```Java
String text = "apple,banana,cherry";
String[] result = text.split(",");
System.out.println(Arrays.toString(result));
```
<details>
<summary>Output: </summary>

<pre>[apple, banana, cherry]</pre>
</details>

```Java
String text2 = "a.b.c";
String[] result2 = text2.split("\\.");
System.out.println(Arrays.toString(result2));
```
<details>
<summary>Output: </summary>

<pre>[a, b, c]</pre>
</details>

<br>

### Python
สำหรับภาษา Python เองก็มีเมธอดที่ชื่อ split ของ str เพื่อนำมาใช้แยกข้อความหรือคำตามตัวคั่นเช่นกันกับภาษา Ruby และ Java หากแต่มีข้อแตกต่างบางส่วน

> [!IMPORTANT]
> **str.split(sep=None, maxsplit=-1)** <br>
> - sep ในที่นี้มีค่าเท่ากับคำว่า pattern ของภาษา Ruby นั่นคือการกำหนดค่าตัวคั่นว่าอยากให้คั่นด้วยตัวอะไร แต่หากไม่กำหนดจะถือว่าคั่นด้วย white space
> - maxsplit ในที่นี้มีค่าเท่ากับคำว่า limit ของภาษา Ruby นั่นคือการกำหนด 'จำนวนครั้งสูงสุดที่จะแยก' โดยมีข้อควรระวังดังนี้
>    - maxsplit = 0 จะหมายความว่า 'ไม่แยกคำเลย' (โปรแกรมจะคืนค่า str ทั้งหมดเป็นตัวเดียวกัน)
>    - maxsplit > 0 แยกตามจำนวนที่กำหนดสูงสุด
>    - ไม่กำหนด maxsplit (ค่า maxsplit เป็น default = -1) จะหมายถึงแบ่งค่าได้แบบไม่จำกัด

ตัวอย่าง
```Python
s = "This is an example"
parts = s.split()
print(parts)
```
<details>
<summary>Output: </summary>

<pre>['This', 'is', 'an', 'example']</pre>
</details>

```Python
s = "a,b,c,d"
parts = s.split(",", 2)
print(parts)
```
<details>
<summary>Output: </summary>

<pre>['a', 'b', 'c,d']</pre>
</details>

```Python
s = "v1.v2.v3"
print(s.split("."))
```
<details>
<summary>Output: </summary>

<pre>['v1', 'v2', 'v3']</pre>
</details>

> [!NOTE]
> - Python สามารถตัดช่องว่างที่ซ้อนกันได้เองโดยใช้เพียง `.split()`
> - Python สามารถใช้ delimiter ตามตัวอักษรได้เลยโดยไม่ต้องใช้ escape เหมือนภาษา Java
> - split ของ Python ไม่รองรับ regex โดยตรง หากอยากใช้ สามารถใช้ `re.splite()` แทน
> - Python มีอีกหนึ่งเมธอดที่ใช้สำหรับการแบ่ง หากแต่ใช้เพื่อแบ่งบรรทัดใหม่เท่านั้น! นั่นคือ `splitlines()` โดยไม่สามารถกำหนดตัวคั่นได้เลย รวมไปถึงไม่สามารถใช้ร่วมกัน maxsplit ได้

สามารถศึกษาเมธอดที่อ้างอิงมาโดยละเอียดได้ที่ https://docs.python.org/3/contents.html


---
<br>
ตารางเปรียบเทียบความแตกต่างการใช้ split แต่ละภาษา

| ภาษา  | ฟังก์ชัน | ตั้ง delimiter เอง  | รองรับ regex | ตั้ง limit/maxlimit  | result |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| Ruby  | "str".split(pattern=nil, [limit]) | /  | / | /  | Array |
| C  | strtok(str, delim) | /  | X | X  | char * (pointer) |
| Java  | str.split(regex, limit) | /  | / | /  | String[] |
| Python  | str.split(sep=None, maxsplit=-1) | /  | X | /  | list |


***
### Video Presentation
[video](https://drive.google.com/file/d/15BySJaA7vZTbIe23EjwCECN1DgcdwUkX/view?usp=sharing)
***
### Slide Presentation
[slide](https://docs.google.com/presentation/d/1Y4KxL4jWHO61t4r2nlQvEHRVEfwSta8E/edit?usp=drive_link&ouid=109744363200621257075&rtpof=true&sd=true) 
***
### Reference
Carmatec. (n.d.). Ruby’s string split: A complete guide with examples. https://www.carmatec.com/blog/rubys-string-split-a-complete-guide-with-examples/<br>
cppreference.com. (n.d.). strtok. https://en.cppreference.com/w/c/string/byte/strtok<br>
Flanagan, D., & Matsumoto, Y. (2008). The Ruby Programming Language (p. 305). O’Reilly Media.<br>
GeeksforGeeks. (n.d.). Java String split() method with examples. https://www.geeksforgeeks.org/java/split-string-java-examples/<br>
GeeksforGeeks. (n.d.). Ruby | String split() method with examples. https://www.geeksforgeeks.org/ruby/ruby-string-split-method-with-examples/<br>
Ghosh, S. S. (2017). Comprehensive Ruby Programming (pp. 48–51). Packt Publishing.<br>
Loosemore, S., Stallman, R. M., McGrath, R., Oram, A., & Drepper, U. (2019). The GNU C library reference manual (pp. 129–131). Free Software Foundation. https://www.gnu.org/software/libc/manual/pdf/libc.pdf<br>
Oracle. (n.d.). Pattern (Java Platform SE 8). In Java SE Documentation. https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html<br>
Oracle. (n.d.). String: split (Java Platform SE 8). In Java SE Documentation. https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#split-java.lang.String-<br>
Python Software Foundation. (n.d.). str.split. In Python 3 Standard Library. https://docs.python.org/3/library/stdtypes.html#str.split<br>
Ruby-Doc.org. (n.d.). Class: String (Ruby 1.9.1). https://ruby-doc.org/core-1.9.1/String.html<br>
Ruby-Doc.org. (n.d.). Class: String (Ruby 2.4.5). https://ruby-doc.org/core-2.4.5/String.html<br>
Ruby-Doc.org. (n.d.). Class: String (Ruby 3.0.7). https://ruby-doc.org/3.0.7/String.html<br>
Techotopia. (n.d.). Ruby string conversions. Techotopia. https://www.techotopia.com/index.php/Ruby_String_Conversions<br>
Shaw, J. (2022, July 18). Python split(): How to split a string in Python. Real Python. https://realpython.com/python-split-string/<br>
The Open Group. (n.d.). strtok - split string into tokens. In The Open Group Base Specifications Issue 7, IEEE Std 1003.1-2017. https://pubs.opengroup.org/onlinepubs/9699919799/functions/strtok.html<br>
Thomas, D., Fowler, C., & Hunt, A. (2013). Programming Ruby 1.9 & 2.0: The Pragmatic Programmers’ Guide (Fourth Edition, p. 685). Pragmatic Bookshelf.<br>

