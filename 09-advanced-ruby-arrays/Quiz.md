Quiz
---
- [Combining Array](09-advanced-ruby-arrays/combining-ruby-arrays.md)
  
<mark style ="background-color:#FFECA1;color:#000;border-radius:5px">โจทย์</mark>
ถ้าต้องการรวม Array เข้าด้วยกัน แต่ยังต้องใช้ Array ชุดเดิมอยู่โดยไม่ให้ถูฏแก้ไข ควรใช้วิธีใดใน Ruby?
1. concat
2. <<
3. .+
4. append

<details close>
   <summary><b>เฉลย</b></summary>
 <pre>3. +  เพราะ + จะสร้าง Array ใหม่ขึ้นมาเสมอ โดยไม่ไปแก้ไข Array ชุดเดิม
 </pre>
</details>

---

- [Deleting Array Elements](https://github.com/660710086/Ruby_tutorial/blob/main/09-advanced-ruby-arrays/deleting-array-elements.md)

<mark style ="background-color:#FFECA1;color:#000;border-radius:5px">โจทย์</mark>
สมมุติมีการกำหนดให้มีสมาชิก

```ruby
arr = [10,500,20,30,'c']
```

เราต้องการลบค่า(value)ของ 'c' และลบค่าดัชนี(index) ของ 0
จะมีการเขียนรูปแบบโค้ดแต่ละภาษาอยู่ในรูปแบบไหน

---

- [Sorting Array](09-advanced-ruby-arrays/sorting-arrays.md)

<mark style ="background-color:#FFECA1;color:#000;border-radius:5px">โจทย์</mark>
การ sorting array มีกี่วิธี มีอะไรบ้าง และแต่ละอย่างมีหน้าที่อย่างไร

---

- [Modifying array](https://github.com/soonklang/Ruby_tutorial/blob/main/09-advanced-ruby-arrays/modifying-arrays.md#modifying-array)

<mark style ="background-color:#FFECA1;color:#000;border-radius:5px">โจทย์</mark>
ข้อใดไม่สามารถเข้าถึง Array ใน Ruby ได้\
1.arr[4]= 12\
2.arr.insert(1,6)\
3.arr[4…6] = [7..9]\
4.arr.add(1)\

เฉลย
<details>
4.arr.add(1)
</details>

เพราะ ในภาษา Ruby ไม่มี Method .add() ต้องใช้วิธีอื่นแทน เช่น .insert() หรือ .push() หรือ <<

---

- [ruby-array-comparisons](09-advanced-ruby-arrays/ruby-array-comparisons.md)

<mark style ="background-color:#FFECA1;color:#000;border-radius:5px">โจทย์</mark>
จงดูตัวอย่าง code ที่ให้มาแล้วตอบคำถามด้านล่างให้ถูกต้อง

```ruby
Code : 
A = [10, 20, 30, 40, 50]
B = [10.0, 20.0, 30.0, 40.0, 50.0]
float_A = A.map {|num| num.to_f}

puts float_A.eql?(B)
```

หลังจาก puts ออกมาแล้วเราจะได้ค่าอะไรออกมา และเพราะเหตุใดถึงได้ค่านั้นออกมา (ต้องการ 2 คำตอบ)
Ans.

---

- [pushing-and-popping-array-elements](https://github.com/soonklang/Ruby_tutorial/blob/main/09-advanced-ruby-arrays/pushing-and-popping-array-elements.md)
##  จงบอกผลลัพธ์ของการ pop(3) ของ array นี้ ["Car","Bike","Plane","Train","Boat"]
1. ["Plane","Train","Boat"]
2. ["Boat","Train","Plane"]
3. ["Train","Boat","Plane"]
4. ["Boat","Plane","Train"]
<details close>
   <summary><b>เฉลย</b></summary>
 <pre>1. ["Plane","Train","Boat"]
 </pre>
</details>

---
  
