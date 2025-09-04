# Converting a Ruby String to an Array
## การแปลง String ในภาษา Ruby ให้เป็น Array

สำหรับตัวของ split นั้นถือว่าเป็น method ที่มีประโยชน์มากของ String ที่มีวัตถุประสงค์ในการเอามาแยกประโยคต่าง ๆ ให้เป็น Array ที่ประกอบด้วย **'คำ'** หรือ **'ตัวอักษร'** ที่ถูกแยกออกมา โดยมีรูปแบบการใช้ดังต่อไปนี้

### ✏ split(pattern=nil, [limit])
> **pattern=nil** เป็นตัวที่เราใช้เพื่อบอกว่าจะ 'ตัด' ตามรูปแบบไหนหรือตัวไหน <br>
> **[limit]** จำนวนชิ้นสูงสุดที่ตัดได้ (โดยจะกำหนดหรือไม่ก็ได้)

สำหรับรูปแบบที่ใช้แยกหรือตัดคำนั้นมีหลากหลายแบบให้ใช้ ยกตัวอย่างต่อไปนี้<br>
**แบบที่ 1 (ไม่ใส่ค่าของ pattern ใดใดเลย)**<br>
```
#แยกตาม whitespace (ช่องว่าง, tab, newline)
# str.split
"ABCDEFGHIJKL".split         #=> [ABCDEFGHIJKL]
"hello world ruby".split     #=> ["hello", "world", "ruby"]
```
***
**แบบที่ 2 (ใช้รูปแบบ string ในการแบ่ง)**<br>
```
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

```
# str.split(/regex/)
"one two three".split(/\s+/)          #=> ["one", "two", "three"]
"cat123dog456mouse".split(/\d+/)      #=> ["cat", "dog", "mouse"]
```
***
**แบบที่ 4 (ใช้ limit เข้ามาช่วย)**<br>
```
# str.split(pattern, [limit])
"a,b,c,d".split(",", 2)    #=> ["a", "b,c,d"]
"1,2,3,".split(",", -1)    #=> ["1", "2", "3", ""]
```
ข้อควรระวัง: เมื่อมีการใช้ limit เข้ามาเกี่ยวข้อง จะมีเรื่องที่ควรใส่ใจนั่นคือ Trailing empty fields (ช่องว่างที่เกิดจากการแบ่งต่อท้าย string) โดยมีเงื่อนไขดังต่อไปนี้
- ค่า limit >= 0 หรือไม่ใส่ ภาษา Ruby จะตัด Trailing empty fields ทิ้งอัตโนมัติ
- ค่า limit < 0  ภาษา Ruby จะเก็บ Trailing empty fields ไว้
***
<br>

### เพิ่มเติม
➕ split สามารถเอามาปรับใช้กับความเรียงต่าง ๆ ได้ด้วยเช่นกัน เนื่องจากคำที่ถูกแยกออกมาจะมีการจัดเก็บเป็น Array แล้วหลังจากนั้นก็ใช้ `array.size()` เพื่อทำให้สามารถนับจำนวนคำได้ที่อยู่ใน Array ได้<br>
```
str = "Lorem Ipsum is simply dummy text"
p str.split.size
```
<details>
<summary>Output: </summary>

<pre>6</pre>
</details>

➕ เช่นเดียวกันกับการแยกตัวอักษร หากว่าเราอยากรู้ว่าในประโยคหรือความเรียงนั้นมีตัวหนังสือทั้งหมดกี่ตัว เราเองก็สามารถประยุกต์ใช้ split และ size ได้<br>
```
str = "Lorem Ipsum is simply dummy text"
p str.split(//).size
```
<details>
<summary>Output: </summary>

<pre>32</pre>
</details>






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
