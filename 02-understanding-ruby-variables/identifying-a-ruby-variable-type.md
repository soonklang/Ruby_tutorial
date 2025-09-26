ใน Ruby เราสามารถตรวจสอบได้ว่าตัวแปรเป็นชนิดข้อมูลอะไร หรืออยู่ในคลาสไหน โดยใช้ 2 วิธีหลัก:

## 1. ใช้เมธอด kind_of? (เช็คว่าตัวแปรเป็นชนิดข้อมูลใดหรือไม่)

kind_of? ใช้เพื่อตรวจสอบว่า ตัวแปร เป็นชนิดข้อมูล (class) ที่เราต้องการหรือไม่ และจะ คืนค่าเป็น true หรือ false

### ตัวอย่างใน Ruby


y = 10

puts y.kind_of?(Integer)   # true

puts y.kind_of?(String)    # false

puts y.kind_of?(Numeric)   # true


- อธิบาย

 - y = 10 → ตัวแปร y เป็น Integer

 - y.kind_of?(Integer) → true เพราะ 10 เป็นตัวเลขจำนวนเต็ม

 - y.kind_of?(String) → false เพราะไม่ใช่สตริง

 - y.kind_of?(Numeric) → true เพราะ Integer เป็นลูกของ Numeric

## 2. ใช้เมธอด class (บอกว่าตัวแปรอยู่ในคลาสใด)

class ใช้เพื่อดูว่า ตัวแปรนี้สร้างมาจากคลาสอะไร และจะ คืนค่าเป็นชื่อคลาสโดยตรง

### ตัวอย่างใน Ruby


  y = 10

  puts y.class    # Integer


- ผลลัพธ์


  Integer


---


  s = "hello"

  puts s.class    # String


- ผลลัพธ์


  String


---


  pi = 3.14

  puts pi.class   # Float


- ผลลัพธ์


  Float


----

- อธิบาย

 - .class จะแสดงชื่อคลาสที่แท้จริงของตัวแปร

 - ตัวเลขจำนวนเต็ม (10) → Integer

 - ตัวเลขทศนิยม (3.14) → Float

​- ตัวอักษร ("hello") → String

## เปรียบเทียบกับภาษาอื่น

### สรุปเข้าใจง่าย

| วิธี        | ใช้เมื่อ                                              | ค่าที่ได้                          |

|-------------|--------------------------------------------------------|------------------------------------|

| .kind_of? | เช็คว่าตัวแปรเป็นชนิดข้อมูลนี้หรือไม่               | true / false                       |

| .class    | ดูว่าตัวแปรอยู่ในคลาสอะไร                            | ชื่อคลาส เช่น Integer              |

 

| ภาษา        | หมายเหตุ                                               | ตรวจสอบได้ |

|-------------|--------------------------------------------------------|------------|

| Ruby        | ยืดหยุ่นที่สุด ตรวจสอบได้ทั้งเชิงลึกและเชิงกว้าง   | ✅         |

| Python      | ใช้ type() และ isinstance() คล้าย Ruby           | ✅         |

| Java        | ใช้ instanceof หรือ getClass()                    | ✅         |

| C           | ต้องรู้ตั้งแต่ประกาศตัวแปร ไม่มีการเช็คแบบ Runtime | ❌         |

 

---

## คลิปนำเสนอ

- https://www.youtube.com/watch?v=GZ_XQgjtXEk

## slide

- https://docs.google.com/presentation/d/1GRoHa0OlBTuGy_g0IeqlrReLeL5_9MzW/edit?usp=sharing&ouid=102001044287525741600&rtpof=true&sd=true

## References :

### Ruby

- Techotopia. (n.d.). Understanding Ruby Variables. Techotopia. Retrieved September 5, 2025, from https://www.techotopia.com/index.php/Understanding_Ruby_Variables

- Ruby Documentation. (n.d.). Object#kind_of?. Ruby Doc. Retrieved September 5, 2025, from https://ruby-doc.org/core/Object.html#method-i-kind_of-3F

- Ruby Documentation. (n.d.). Object#class. Ruby Doc. Retrieved September 5, 2025, from https://ruby-doc.org/core/Object.html#method-i-class

### Python

- Python Software Foundation. (n.d.). type(). Python 3.11. Retrieved September 5, 2025, from https://docs.python.org/3/library/functions.html#type

- Python Software Foundation. (n.d.). isinstance(). Python 3.11. Retrieved September 5, 2025, from https://docs.python.org/3/library/functions.html#isinstance

### Java

- Oracle. (2014). Java™ Platform, Standard Edition 8 API Specification: Class Object. Oracle. Retrieved September 5, 2025, from https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html#getClass--

- Oracle. (2014). Java™ Language Specification, Java SE 8 Edition: 15.20.2 instanceof Operator. Oracle. Retrieved September 5, 2025, from https://docs.oracle.com/javase/specs/jls/se8/html/jls-15.html#jls-15.20.2

### C

- cppreference.com. (n.d.). C reference. Retrieved September 5, 2025, from https://en.cppreference.com/w/c

- TutorialsPoint. (n.d.). C Programming – Data Types. TutorialsPoint. Retrieved September 5, 2025, from https://www.tutorialspoint.com/cprogramming/c_data_types.htm

