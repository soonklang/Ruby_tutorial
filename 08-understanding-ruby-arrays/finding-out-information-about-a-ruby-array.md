# Finding Out Information about a Ruby Array

- .length() / .size()
- .empty?
- .class

### .length() / .size()

เป็น **Instance Method** ที่ใช้ในการตรวจหาความยาวของ array ที่ต้องการ การใช้ .length เหมือนกับการใช้ .size ทุกประการ โดยในภาษา Ruby จะนำออกเป็นค่า integer ที่มีค่าตั้งเเต่ 0 เป็นต้นไป โดย 0 หมายถึง array ว่างที่ไม่มีสมาชิกอะไรเลย

```ruby
arr.length()
arr.size()
```

**วิธีการใช้งาน**

> Ruby

```ruby
arr1 = [1,2,3,4,5,6,7,8,9]
arr2 = [[1,2,3],[4,5,6],[7,8,9]]

puts arr1.length()
# ค่าที่ได้คือ 9
puts arr2.length()
# ค่าที่ได้คือ 3
puts arr1.size()
# ค่าที่ได้คือ 9
puts arr2.size()
# ค่าที่ได้คือ 3
[].length()
# ค่าที่ได้คือ 0
```

Method นี้ สามารถใช้ร่วมกันกับ String ได้ เเต่จไม่ถูกกล่าวถึงในที่นี้

**ตัวอย่างในภาษาอื่น**

> Python

คำสั่ง len() ใน Python ทำงานเหมือนกันกับ .length() เเละ .size() ใน Ruby เเตกต่างที่การใช้งาน .length() ใน Ruby เเละใน Python เเตกต่างกัน เนื่องจาก .length() ใน Ruby เป็น Instance Method เเต่ len() ใน Python เป็น **Build-in function**

```python
arr1 = [1,2,3,4,5,6,7,8,9]
arr2 = [[1,2,3],[4,5,6],[7,8,9]]

print(len(arr1))
# ค่าที่ได้คือ 9
print(len(arr2))
# ค่าที่ได้คือ 3
```

> Java

คำสั่ง .length ใน java ทำงานเหมือนกันกับ .length() เเละ .size() ใน Ruby ไม่ใช่ Instance Method เหมือนใน Ruby เเต่เป็น **field (property)**

```java
int arr1[] = {1,2,3,4,5,6,7,8,9};
int arr2[][] = {{1,2,3},{4,5,6},{7,8,9}};

System.out.println(arr1.length);
// จะมีค่าเท่ากับ 9
System.out.println(arr2.length);
// จะมีค่าเท่ากับ 3
```

> C

ในภาษา C ไม่มี method หรือ function ในการหาขนาดของ array ได้โดยตรง จึงต้องประยุกต์ใช้ sizeof() ที่ C มีให้อยู่เเล้วเพื่อให้ได้ผลลัพท์เเบบเดียวกันกับ Method .length() ใน Ruby

```c
int arr1[9] = {1,2,3,4,5,6,7,8,9};
int arr2[3][3] = {{1,2,3},{4,5,6},{7,8,9}};

printf("%d\n",sizeof(arr1) / sizeof(arr1[0]));
// จะมีค่าเท่ากับ 9
printf("%d",sizeof(arr2[0]) / sizeof(arr2[0][0]));
// จะมีค่าเท่ากับ 3
```

### .empty?

เป็น **Instance Method** ที่ใช้เช็คว่า array นั้นๆ เป็น array ว่างเปล่าหรือไม่ โดย Method นี้จะคืนค่าเป็น Boolean ออกมา โดยจะเป็น true ก็ต่อเมื่อ array นั้นไม่มีสมาชิกใดๆ เเละจะคืนค่า false ก็ต่อเมื่อ array นั้น มีสมาชิกอย่างน้อย 1 ตัว

```ruby
arr.empty?
```

**วิธีการใช้งาน**

> Ruby

```ruby
arr1 = [1,2,3,4,5,6,7,8,9]
arr2 = [[1,2,3],[4,5,6],[7,8,9]]
arr3 = []

puts arr1.empty?
# ค่าที่ได้คือ false
puts arr2.empty?
# ค่าที่ได้คือ false
puts arr3.empty?
# ค่าที่ได้คือ true
puts [].empty?
# ค่าที่ได้คือ true
```

Method นี้ สามารถใช้ร่วมกันกับ String ได้ เเต่จไม่ถูกกล่าวถึงในที่นี้

**ตัวอย่างในภาษาอื่น**

> Python

ในภาษานี้ไม่มี method .empty? เหมือนใน Ruby โดยตรง เเต่มีหลายวิธีที่สามารถเช็คว่า list นั้นว่างหรือไม่ เช่น

```python
arr1 = [1,2,3,4,5,6,7,8,9]
arr2 = [[1,2,3],[4,5,6],[7,8,9]]
arr3 = []

print(len(arr1) == 0)
# ค่าที่ได้คือ false
print(len(arr2) == 0)
# ค่าที่ได้คือ false
print(len(arr3) == 0)
# ค่าที่ได้คือ true
print(not arr1)
# ค่าที่ได้คือ false
print(not arr2)
# ค่าที่ได้คือ false
print(not arr3)
# ค่าที่ได้คือ true
```

วิธี (not) สามารถใช้ร่วมกันกับ String ได้ เเต่จไม่ถูกกล่าวถึงในที่นี้

> Java

ในภาษานี้ไม่มี method .empty? เหมือนใน Ruby โดยตรง เเต่สามารถเช็คว่า array นี้มีขนาดเท่าไหร่ ถ้าเท่ากับ 0 ก็แปลว่า array นี้ ไม่มีสมาชิก

```java
int arr1[] = {1,2,3,4,5,6,7,8,9};
int arr2[] = {{1,2,3},{4,5,6},{7,8,9}}
int arr3[] = {}

System.out.println(arr1.length == 0);
// ค่าที่ได้คือ false
System.out.println(arr2.length == 0);
// ค่าที่ได้คือ false
System.out.println(arr2.length == 0);
// ค่าที่ได้คือ true
```

ในภาษานี้ไม่มี method อะไรเลย ถ้าต้องการเช็คว่า array นี้มีสมาชิกหรือไม่ ต้องเขียนอัลกอริทึมเช็คเองเท่านั้น

> C

```c
int arr1[9] = {1,2,3,4,5,6,7,8,9};
int arr2[3] = {{1,2,3},{4,5,6},{7,8,9}};
int arr3[0];

printf("%d\n", sizeof(arr) / sizeof(arr1[0]) == 0);
// ค่าที่ได้คือ false
printf("%d\n", sizeof(arr) / sizeof(arr2[0]) == 0);
// ค่าที่ได้คือ false
printf("%d\n", sizeof(arr) / sizeof(arr3[0]) == 0);
// ค่าที่ได้คือ true
```

### .class

จริงๆเเล้ว **Instance Method** นี้ไว้เพ่ื่อใช้เช็คว่า Object ที่เช็คนั้นเป็น class อะไร ในที่นี้ถ้าใช้เช็คกับ array ก็จะคืนค่าออกมาเป็น array

```ruby
arr1.class
```

**วิธีการใชงาน**

> Ruby

```ruby
arr1[] = [1,2,3,4,5,6,7,8,9]
puts arr1.class
# ค่าที่ได้คือ array
```

**ตัวอย่างในภาษาอื่น**

> Python

ในภาษานี้ไม่มี method .Class เหมือนใน Ruby เเต่สามารถใช้ type() เช็คได้เหมือนกัน

```python
arr1[] = [1,2,3,4,5,6,7,8,9]
print(type(arr1))
# ค่าที่ได้คือ <class 'list'>
```

> Java

ในภาษานี้มี .class เเต่ไม่ได้ทำงานเหมือนใน Ruby เนื่องจากใน Java ไม่ได้ทำงานในรูปแบบนั้น หากต้องการเช็คว่าเป็น array ใหมใน Java ต้องใช้ .getClass().isArray() แทน แต่ผลที่ออกมาจะเป็น Boolean เป็น true เมื่อเป็น array เเละเป็น false เมื่อไม่ใช่ array

```java
int arr1[9] = {1,2,3,4,5,6,7,8,9};

System.out.println(arr1.getClass().isArray());
// ค่่าที่ได้คือ true
```

> C

ภาษา C ไม่มี concept ของ .class เพราะ C ไม่ใช่ OOP

# Reference

- Ruby Programming Language - class Array. ​เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://docs.ruby-lang.org/en/master/Array.html​
- RubyDoc.info (ไม่กำหนด) class Array. ​เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://www.ruby-doc.org/core/Array.html​
- IncludeHelp. (ไม่กำหนด).Ruby Array Methods. ​เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://www.includehelp.com/ruby/ruby-array-methods.aspx#google_vignette​
- FreeCodeCamp (27 มกราคม 2020) Most common Ruby array methods you should know. เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://www.freecodecamp.org/news/common-array-methods-in-ruby​
- George, J (1 พฤจิกายน 2015) Ruby array methods. ​เข้าถึงเมื่อ 31 สิงหาคม 2025​ จาก https://webdevjeffus.github.io/projects/cheat-sheet.html​
- Python documentation (31 สิงหาคม 2025) Efficient arrays of numeric values.​ เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://docs.python.org/3/library/array.html​
- Oracle Help Center (ไม่กำหนด) Arrays (Java Platform SE 8) ​เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html​
- W3School (ไม่กำหนด) C Arrays​ เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://www.w3schools.com/c/c_arrays.php​
- GeeksforGeeks (26 กรกฏาคม 2025) C Arrays ​เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://www.geeksforgeeks.org/c/c-arrays​
