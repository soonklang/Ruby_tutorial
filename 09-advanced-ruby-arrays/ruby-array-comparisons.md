# Ruby Array Comparisons
ในส่วน Array Comparisons ของ Ruby จะมีเครื่องหมายเปรียบเทียบอยู่ทั้งหมด 3 รูปแบบ คือ ==, <=>, eql?(..) ในแต่รูปแบบนั้นแตกต่างกันอย่างไร เราไปติดตามกันที่เนื้อหากันดีกว่าครับ o^o

## Syntax ของ Operator
### 1.) Array A == Array B
Operator ของ == เป็นเครื่องหมายเปรียบเทียบเพื่อดูว่า Array ของ A และ B ว่าข้อมูลแต่ละตัวใน Array มีค่าเท่ากันทั้งหมดหรือไม่ ซึ่งสามารถเปรียบเทียบได้ทั้ง String, Integer และ Float

### ตัวอย่าง
```ruby
# Integer
A = [1, 2, 3, 4, 5]
B = [1, 2, 3, 4, 5]
puts A == B  # output : true

A = [1, 2, 3, 4] #หรือ [1, 2, 3, 4, 6]
B = [1, 2, 3, 4, 5]
puts A == B # output : false
#------------------------------------------------------
# String
C = ["wow", "Hello", "world"]
D = ["wow", "Hello", "world"]
puts C == D # output : true

C = ["wow", "Hello"] #หรือ ["welp", "Hello", "world"]
D = ["wow", "Hello", "world"]
puts C == D # output : false
#------------------------------------------------------
# Float
E = [1.0, 2.5, 3.75]
F = [1.0, 2.5, 3.75]
puts E == F # output : true

E = [1.0, 2.5] #หรือ [1.57, 2.5, 3.75]
F = [1.0, 2.5, 3.75]
puts E == F # output : false
```
-----------------------------------------------------------------------------
### 2.) Array A <=> Array B
Operator ของ <=> เป็นเครื่องหมายเปรียบเทียบว่า Array ของ A และ B เพื่อตรวจสอบว่าข้อมูลของแต่ละตัวใน Array ว่าตัวฝั่งไหนมีข้อมูลมากกว่า น้อยกว่า หรือเท่ากันทั้ง 2 Array โดยจะมี output ทั้งหมด 3 แบบคือ <br>***1*** ก็ต่อเมื่อ Array A มีข้อมูลหรือค่ามากกว่า Array B, ***0*** ก็ต่อเมื่อ Array A มีข้อมูลหรือค่าเท่ากันกับ Array B และ ***-1*** ก็ต่อเมื่อ Array A มีข้อมูลหรือค่าน้อยกว่า Array B  <br>ซึ่งเราสามารถเปรียบเทียบได้ทั้ง Integer และ Float แต่ในส่วนของ <mark style="color:blue">String จะเปรียบเทียบจากลำดับคำศัพท์ (lexicographical order) และ ASCII Code</mark>
### ตัวอย่าง
```ruby
A = [5, 7, 8, 9]
B = [1, 2, 3, 4]
puts A <=> B  # output : 1

C = ["halo", "rain", "paper"]
D = ["Cat", "dog"]
puts C <=> D  # output : 1  ในส่วนของ String จะตรวจสอบจากลำดับคำศัพท์ (lexicographical order) และ ASCII Code

E = [5.0, 3.5, 7.5]
F = [2.5, 3.33, 1.75]
puts E <=> F  # output : 1
#------------------------------------------------------
A = [1, 2, 3, 4]
B = [1, 2, 3, 4]
puts A <=> B  # output : 0

C = ["Cat", "dog", "world"]
D = ["Cat", "dog", "world"]
puts C <=> D  # output : 0

E = [5.0, 3.5, 7.5]
F = [5.0, 3.5, 7.5]
puts E <=> F  # output : 0
#------------------------------------------------------
A = [0, 7, 8, 9]
B = [1, 2, 3, 4]
puts A <=> B  # output : -1

C = ["Apple", "rain", "paper"]
D = ["Cat", "dog"]
puts C <=> D  # output : -1

E = [0.25, 3.5]
F = [2.5, 3.33]
puts E <=> F  # output : -1
```
-----------------------------------------------------------------------------
### 3.) Array A.eql?(Array B)
Operator ของ .eql?(..) เป็นเครื่องหมายเปรียบเทียบเพื่อดู Array ของ A และ B ว่ามีค่าเท่ากันและชนิดข้อมูลเดียวกันหรือไม่ <br>(คล้ายกันกับตัว Operator ของ == ในข้อที่ 1.)
```ruby
A = [1, 3, 5]
B = [1, 3, 5]

puts A.eql?(B)  # output : true

A = [1, 3, 5]
B = [1, 3, 5.0]

puts A.eql?(B)  # output : false
#------------------------------------------------------
C = ["Hello", "World"]
D = ["Hello", "World"]

puts C.eql?(D)  # output : true

C = ["Hello", "World"]
D = ["hello", "world"]

puts C.eql?(D)  # output : false
```
-----------------------------------------------------------------------------
### คำถามมีอยู่ว่า <mark style="color:blue">ระหว่าง == กับ .eql?(..)  แตกต่างกันอย่างไร?</mark>
<ins>***Operator ของ ==***</ins> &nbsp;จะทำหน้าที่ตรวจสอบข้อมูลของ Array ทั้ง 2 ว่ามีค่าเท่ากันหรือไม่ ซึ่งส่วนใหญ่ Operator ตัวนี้แค่ตรวจสอบความเท่ากันอย่างเดียว แม้ว่าจะชนิดข้อมูลจะไม่เหมือนกันก็ตาม <ins>ตย.</ins> 10 == 10.0 output ที่ได้ออกมาจะเป็น ***true*** เพราะค่าของข้อมูลมีค่าเท่ากันนั้นเอง
<br><ins>***Operator ของ .eql?(..)***</ins> &nbsp;จะทำหน้าที่ตรวจสอบข้อมูลของ Array ทั้ง 2 ว่ามีค่าเท่ากันและชนิดข้อมูลเดียวกันหรือไม่ <ins>ตย.</ins> 10.eql?(10) output ที่ได้คือ ***true*** เพราะมีค่าเท่ากันและชนิดข้อมูลเป็นชนิดเดียวกัน แต่ถ้าเป็น 10.eql?(10.0) output ที่ได้คือ ***false*** เพราะมีค่าเท่ากัน แต่ชนิดข้อมูลเป็นคนละชนิดนั้นเอง

-----------------------------------------------------------------------------
## การเปรียบเทียบของ Array Comparisons ระหว่าง Java/C/Python
### 1.) Array Comparisons ของ Java
จะมีทั้งหมด 5 แบบ คือ ==, equals(.., ..), deepEquals(.., ..), compare(.., ..) และ mismatch(.., ..)<br>

### 1.1) ==
```java
int[] arr1 = {1, 3, 5};
int[] arr2 = arr1;
int[] arr3 = {1, 3, 5};
System.out.println(arr1 == arr2); //output : true เพราะเป็น object เดียวกัน
System.out.println(arr1 == arr3); //output : false เพราะไม่ใช่ object เดียวกัน
```

### 1.2) equals(.., ..)
```java
import java.util.Arrays;
int[] arr1 = {2, 4, 6};
int[] arr2 = {2, 4, 6};
int[] arr3 = {7, 8, 9};
System.out.println(Arrays.equals(arr1, arr2)); //output : true
System.out.println(Arrays.equals(arr1, arr3)); //output : false
```

### 1.3) deepEquals(.., ..)
> เป็นการเปรียบเทียบแบบ Array หลายมิติ ซึ่งจะเป็นตรวจสอบค่าใน Array หลายมิติ
```java
import java.util.Arrays;
int[] arr1 = {{2, 4}, {6, 8}};
int[] arr2 = {{2, 4}, {6, 8}};
int[] arr3 = {{7, 8}, {9, 10}};
System.out.println(Arrays.deepEquals(arr1, arr2)); //output : true
System.out.println(Arrays.deepEquals(arr1, arr3)); //output : false
```

### 1.4) compare(.., ..)
> เป็นการเปรียบเทียบ Array ทั้ง 2 ตัว ตามหลักของพจนานุกรม โดยจะส่งค่าคือเป็น ***0*** หากมีค่าเท่ากันทั้งสอง Array เท่ากัน, ***เลขจำนวนเต็มลบ*** หากค่าของ Array 1 มีค่าน้อยกว่า Array 2 และ ***เลขจำนวนเต็มบวก*** หากค่าของ Array 1 มีค่ามากกว่า  Array 2 
```java
import java.util.Arrays;
String[] arr1 = {"Hello", "World", "Wow"};
String[] arr2 = {"Hello", "World", "Wow"};
String[] arr3 = {"Apple", "Banana", "Cat"};
System.out.println(Arrays.compare(arr1, arr2)); //output : 0
System.out.println(Arrays.compare(arr1, arr3)); //output : 7
```

### 1.5) mismatch(.., ..)
> เป็นการตรวจสอบตำแหน่งค่าที่ไม่ตรงกันครั้งแรกของข้อมูลทั้งสอง Array ว่าข้อมูลที่ไม่ตรงเท่ากันอยู่ที่ตำแหน่งไหนใน Array ซึ่งจะส่งค่าคืนเป็น ***-1*** หาก Array ทั้งสองตรงกัน
```java
import java.util.Arrays;
int[] arr1 = {1, 2, 3, 4};
int[] arr2 = {1, 2, 5, 4};
System.out.println(Arrays.mismatch(arr1, arr2)); //output : 2 เพราะไม่ตรงกับตำแหน่งที่ 2 ของ Array
```

-----------------------------------------------------------------------------
### 2.) Array Comparisons ของ C
> ในส่วนของภาษา C นั้น ไม่มีตัวดำเนินการโดยตรงในการเปรียบเทียบ Array จึงต้องใช้ Loop ในการตรวจสอบข้อมูลทีละตัวใน Array
