# Finding Out Information about a Ruby Array

ในภาษา **Ruby** มีเมธอด (methods) และคำสั่งมากมายที่สามารถใช้ร่วมกับ **Arrays** ได้  
โดยสามารถแบ่งการใช้งานออกเป็น 5 ประเภทใหญ่ ๆ ดังนี้:

1. **Access / Retrieval** (การเข้าถึงข้อมูล)
2. **Query / Information** (ตรวจสอบ / หาข้อมูล)
3. **Modification / Mutation** (แก้ไขค่าใน Array)
4. **Enumeration / Iteration** (วน loop / map / filter)
5. **Advanced / Combinatorics / Utilities** (การใช้งานขั้นสูง / การคำนวณ / สถิติ)

---

## 1. Access / Retrieval (การเข้าถึงข้อมูล)

- []
- .at()
- .dig()
- .first()
- .last()
- .value_at()
- .take()
- .drop()
- .fetch()
- .dig()

**ยกตัวอย่างการสร้าง array**

```ruby
arr1 = [1,2,3,4,5,6,7,8,9]
arr2 = [[1,2,3],[4,5,6],[7,8,9]]
```

การเข้าถึง array สามารถทำได้ 2 วิธี คือ

1. การเข้าถึงเเบบปกติ

เป็นวิธีที่นิยมใช้มากที่สุดในการเขียนโปรเเกรม โดยโปรเเกรมจะนำค่าตำเเหน่งที่อยู่ใน [] ไปหาค่าใน array โดยจะเริ่มจาก 0

```ruby
arr1[2]
arr2[0][2]
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr1[2]
# คำตอบที่ได้คือ 3
puts arr2[0][2]
# คำตอบที่ได้คือ 3
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
print(arr1[2])
# คำตอบที่ได้คือ 3
print(arr2[0][2])
# คำตอบที่ได้คือ 3
```

> Java

```java
System.out.println(arr1[2]);
# คำตอบที่ได้คือ 3
System.out.println(arr2[0][2]);
# คำตอบที่ได้คือ 3
```

> C

```c
printf("%d", arr1[2]);
# คำตอบที่ได้คือ 3
printf("%d", arr2[0][2]);
# คำตอบที่ได้คือ 3
```

2. การเข้าถึงเเบบใช้ .at()

เป็นอีกวิธีในRubyที่สามารถใช้ได้กับ array 1 มิติเท่านั้น โดยโปรเเกรมจะนำค่าตำเเหน่งที่อยู่ใน () ไปหาค่าใน array โดยจะเริ่มจาก 0

```ruby
arr1.at(2)
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr1.at(2)
# คำตอบที่ได้คือ 3
```

**ตัวอย่างในภาษาอื่น**

ในภาษา Python Java เเละ C ไม่มีคำสั่งนี้้ จึงมักใช้ในเเบบที่ 1 เป็นปกติ

เเต่หากเป็น array เเบบ 2 มิติ จะใช้คำสั่ง .dig() ได้ โดย .dig() ใช้สำหรับหาค่าใน array 2 มิติ ตามเลขที่ใส่ในส่วนเเรกของ () โดยเริ่มจาก 0 จะเข้าไปในชั้นเเรกของ array เเละจะเข้าสู่ตำเเหน่งตามส่วนสองของ () โดยเริ่มจาก 0 หากไม่พบ จะคืนค่า nil

```ruby
arr2.dig(1, 2)
```

**วิธีการใช้งาน**

> Ruby

```ruby
p arr2.dig(1, 2)
# คำตอบที่ได้คือ 6
```

**ตัวอย่างในภาษาอื่น**

ในภาษา Python Java เเละ C ไม่มีคำสั่งนี้้ จึงมักใช้ในเเบบที่ 1 เป็นปกติ

ในภาษา Ruby ยังมีการเข้าถึงตำเเหน่งเเรกเเละสุดท้ายโดยการใช้คำสั่ง .first() เเละ .last() อีกด้วย

```ruby
arr1.first()
arr1.last()
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr1.first()
# คำตอบที่ได้คือ 1
puts arr1.last()
# คำตอบที่ได้คือ 9

puts arr2.first()
# คำตอบที่ได้คือ 1 2 3
puts arr2.last()
# คำตอบที่ได้คือ 7 8 9
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
print(arr1[0])
# คำตอบที่ได้คือ 1
print(arr1[-1])
# คำตอบที่ได้คือ 9

print(arr2[0])
# คำตอบที่ได้คือ [1, 2, 3]
print(arr2[-1])
# คำตอบที่ได้คือ [7, 8, 9]
```

> Java

```java
import java.util.Arrays;

System.out.println(arr1[0]);
// คำตอบที่ได้คือ 1
System.out.println(arr1[arr1.length - 1] );
// คำตอบที่ได้คือ 9

System.out.println(Arrays.toString(arr2[0]));
// คำตอบที่ได้คือ [1,2,3]
System.out.println(Arrays.toString(arr2[arr2.length - 1]));
// คำตอบที่ได้คือ [7,8,9]
```

> C

```c
printf("%d", arr1[0]);
// คำตอบที่ได้คือ 1
printf("%d \n", arr1[(sizeof(arr1)/sizeof(arr1[0]))-1]);
// คำตอบที่ได้คือ 9

printf("[ ");
for (int i = 0;i < 3;i++){
    printf("%d ", arr2[0][i]);
}
printf("]");
// คำตอบที่ได้คือ [ 1 2 3 ]

printf("[ ");
for (int i = 0;i < 3;i++){
    printf("%d ", arr2[2][i]);
}
printf("]");
// คำตอบที่ได้คือ [ 7 8 9 ]

// การสร้าง array ในภาษา C มีการกำหนดขนาดเป็นเเบบ Fix อยู่เเล้ว
```

ในภาษา Ruby มีคำสั่งที่ใช้ดึงค่ามากกว่า 1 ค่าใน array อยู่ด้วย นั่นคือคำสั่ง .value_at() โดยจะเริ่มจาก 0 หากไม่มีค่าในตำเเหน่งนั้นผลลัพท์จะออกเป็น nil

```ruby
arr1.values_at(1)
arr2.values_at(1,2)
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr1.values_at(1,3,4)
# คำตอบที่ได้คือ 2 4 5
p arr2.values_at(0,2)
# คำตอบที่ได้คือ [[1,2,3], [7, 8, 9]]
```

**ตัวอย่างในภาษาอื่น**

ในภาษาอื่นๆเช่น Python, Java, C ไม่มีคำสั่งที่ทำหน้าที่คล้ายหรือเหมือนกับ .values_at() ได้โดยตรง เเต่สามารถพลิกเเพลงใช้วิธีอื่นๆในการทำให้ได้ผลลับเดียวกันออกมาได้ เช่น​

> Python

```python
result = [arr1[i] for i in [1,3,4]​]​
print(result)
#จะมีค่าเท่ากับ [2,4,5]

result = [arr2[i] for i in [0,2]]
print(result)
#จะมีค่าเท่ากับ [[1,2,3],[7,8,9]]
```

> Java

```java
import java.util.Arrays;

int[] result = { arr1[1], arr1[3], arr1[4] };
System.out.println(Arrays.toString(result));
// จะมีค่าเท่ากับ [2, 4, 5]

int[][] result = { arr2[0], arr2[2] };
System.out.println(Arrays.deepToString(result));
// จะมีค่าเท่ากับ [[1, 2, 3], [7, 8, 9]]
```

> C

```c
int indices[] = {1,3,4};
int result[3];
for (int i = 0; i < 3; i++){
    result[i] = arr1[indices[i]];
}
for (int i = 0; i < 3; i++) {
    printf("%d ", result[i]);
}
// จะมีค่าเท่ากับ 2 4 5

int indices[] = {0,2};
int result[2][3];
for (int i = 0; i < 2; i++) {
    for (int j = 0; j < 3; j++) {
        result[i][j] = arr2[indices[i]][j];
    }
}
for (int i = 0; i < 2; i++) {
    printf("[");
    for (int j = 0; j < 3; j++) {
        printf("%d", result[i][j]);
        if (j < 2) printf(",");
    }
    printf("]");
}
// จะมีค่าเท่ากับ [1, 2, 3][7, 8, 9]
```

ในภาษา Ruby มีคำสั่งที่ใช้ดึงค่าใน array ตั้งเเต่ค่าเเรกสุดจนถึงค่าที่อยู่ใน () ของ .take() โดยเริ่มจาก 1 หากใส่จำนวนที่นอกขอบเขตที่มี จะไม่เเสดงเลขใดๆออกมาเลย

```ruby
arr1.take(3)
arr2.take(2)
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr1.take(3)
# คำตอบที่ได้คือ 1 2 3
p arr2.take(2)
# คำตอบที่ได้คือ [[1, 2, 3], [4, 5, 6]]
```

**ตัวอย่างในภาษาอื่น**

ในภาษาอื่นๆเช่น Python, Java, C ไม่มีคำสั่งที่ทำหน้าที่คล้ายหรือเหมือนกับ .take() ได้โดยตรง เเต่สามารถพลิกเเพลงใช้วิธีอื่นๆในการทำให้ได้ผลลับเดียวกันออกมาได้ เช่น​

> Python

```python
print(arr1[:3])
# คำตอบที่ได้คือ 1 2 3
print(arr2[:2][:3])
# คำตอบที่ได้คือ [[1, 2, 3], [4, 5, 6]]
```

> Java

```java
for (int i = 0;i < 3;i++){​
    System.out.print(arr1[i] + " ");​
}
// คำตอบที่ได้คือ 1 2 3

for (int i = 0;i < 2;i++){
    System.out.print("[");
    for (int j = 0;j < 3;j++){
        System.out.print(arr2[i][j]);
        if (j < 2){
           System.out.print(" ");
        }
    }
    System.out.print("]");
}
// คำตอบที่ได้คือ [1 2 3][4 5 6]
```

> C

```c
for (int i = 0;i < 3;i++){​
    printf("%d ", arr1[i]);​
}
// คำตอบที่ได้คือ 1 2 3

for (int i = 0;i < 2;i++){
    printf("[")
    for (int j = 0;j < 3;j++){
        printf("%d",arr2[i][j])
        if (j < 2){
           System.out.print(" ");
        }
    }
    printf("]")
}
// คำตอบที่ได้คือ [1 2 3][4 5 6]
```

มีคำสั่งที่ใช้ดึงค่าใน array ตั้งเเต่ค่าที่อยู่ใน () ของ .drop() โดยเริ่มจาก 1 จนถึงค่าท้ายสุด หากใส่จำนวนที่นอกขอบเขตที่มี จะไม่เเสดงเลขใดๆออกมาเลย

```ruby
arr1.drop(6)
arr2.drop(2)
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr1.drop(6)
# คำตอบที่ได้คือ 7 8 9
p arr2.drop(2)
# คำตอบที่ได้คือ [[7, 8, 9]]
```

**ตัวอย่างในภาษาอื่น**

ในภาษาอื่นๆเช่น Python, Java, C ไม่มีคำสั่งที่ทำหน้าที่คล้ายหรือเหมือนกับ .drop() ได้โดยตรง เเต่สามารถพลิกเเพลงใช้วิธีอื่นๆในการทำให้ได้ผลลับเดียวกันออกมาได้ เช่น​

> Python

```python
print(arr1[6:])​
#จะมีค่าเท่ากับ [7,8,9]
print(arr2[2:][:])​
#จะมีค่าเท่ากับ [[7, 8, 9]]
```

> Java

```java
for (int i = 6;i < arr1.length;i++){​
    System.out.print(arr1[i] + " ");​
}​
// จะมีค่าเท่ากับ 7 8 9

for (int i = 1;i < arr2.length;i++){
    System.out.print("[");
    for (int j = 0;j < arr2[i].length;j++){
        System.out.print(arr2[i][j]);
        if (j < arr2[i].length-1){
            System.out.print(" ");
        }
    }
    System.out.print("]");
}
// จะมีค่าเท่ากับ [4 5 6][7 8 9]
```

> C

```c
for (int i = 6;i < arr1.length;i++){​
    printf("%d ", arr1[i]);
}​
// จะมีค่าเท่ากับ 7 8 9

for (int i = 1;i < arr2.length;i++){
    printf("[");
    for (int j = 0;j < arr2[i].length;j++){
        printf("%d", arr2[i][j]);
        if (j < arr2[i].length-1){
            printf(" ");
        }
    }
    printf("]");
}
// จะมีค่าเท่ากับ [4 5 6][7 8 9]
```

ใน Ruby มีคำสั่งที่ใช้สำหรับหาค่าใน array ตามเลขที่ใส่ในส่วนเเรกของ () ใน .fetch() โดยเริ่มจาก 1 หากใส่จำนวนที่นอกขอบเขตที่มี จะเเสดงข้อความในส่วนที่สองของ ()

```ruby
arr1.fetch(3, "Not Found")
arr2.fetch(3, "Not Found")
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr1.fetch(3, "Not Found")
# คำตอบที่ได้คือ 4
p arr2.fetch(99, "Not Found")
# คำตอบที่ได้คือ "Not Found"
```

**ตัวอย่างในภาษาอื่น**

ในภาษาอื่นๆเช่น Python, Java, C ไม่มีคำสั่งที่ทำหน้าที่คล้ายหรือเหมือนกับ .fetch() ได้โดยตรง เเต่สามารถพลิกเเพลงใช้วิธีอื่นๆในการทำให้ได้ผลลับเดียวกันออกมาได้ เช่น​

> Python

```python
index = 2
print(arr1[index] if index < len(arr1) else "Not Found")
# จะมีค่าเท่ากับ 3

index = 99
print(arr2[index] if index < len(arr2) else "Not Found")
# จะมีค่าเท่ากับ Not Found
```

> Java

```java
int index = 2;
if (index >= 0 && index < arr1.length) {​
    System.out.println(arr1[index]);​
} else {​
    System.out.println("Not Found");​
}
// จะมีค่าเท่ากับ 3

import java.util.Arrays;
int Index = 99;
if (Index >= 0 && Index < arr2.length) {
    System.out.println(Arrays.toString(arr2[Index]));
} else {
    System.out.println("Not Found");
}
// จะมีค่าเท่ากับ Not Found
```

> C

```c
int index = 2;
if (index >= 0 && index < arr1.length) {​
    printf("%d",arr1[index]);
} else {​
    printf("Not Found");
}
// จะมีค่าเท่ากับ 3
int cols = sizeof(arr2[0]) / sizeof(arr2[0][0]);
int Index = 99;
if (Index >= 0 && Index < row) {
    printf("[");
        for (int j = 0; j < cols; j++) {
            printf("%d", arr2[Index][j]);
            if (j < cols-1) printf(", ");
        }
    printf("]\n");
} else {
    printf("Not Found");
}
// จะมีค่าเท่ากับ Not Found
```

## 2. Query / Information (ตรวจสอบ / หาข้อมูล)​

- .length() / .size()
- .empty?
- .include?
- .index() / .rindex()
- .count()
- .any? / .all? / .none?

**ยกตัวอย่างการสร้าง array**

```ruby
arr1 = [1,2,3,4,5,6,7,8,9]
arr2 = [[1,2,3],[4,5,6],[7,8,9]]
arr3 = []
arr4 = [1,1,1,2,2,2,3,3,3]
```

ในภาษา Ruby มีหลายคำสั่งที่ใช้สำหรับการตรวจสอบ array สิ่งที่ใช้บ่อยมากสิ่งหนึ่งก็คือ .length() เเละ .size()

.length() / .size() ทำหน้าที่บอกขนาดของ array นั้นๆ โดยขนาดเล็กที่สุดคือ 1

```ruby
arr1.length()
arr2.size()
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr1.length()
# จะมีค่าเท่ากับ 9
puts arr1.size()
# จะมีค่าเท่ากับ 9

puts arr2.length()
# จะมีค่าเท่ากับ 3
puts arr2.size()
# จะมีค่าเท่ากับ 3
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
print(len(arr1))
# จะมีค่าเท่ากับ 9
print(len(arr2))
# จะมีค่าเท่ากับ 3
```

> Java

```java
System.out.println(arr1.length);
// จะมีค่าเท่ากับ 9
System.out.println(arr2.length);
// จะมีค่าเท่ากับ 3
```

ในภาษา C ไม่มีคำสั่งสำเร็จรูปเเบบ 2 ภาษาข้างต้น เเต่สามารถใช้อัลกอริทึมอื่นๆช่วยเพื่อให้ได้ผลลัพท์ที่คล้ายกันได้ ดังนี้

> C

```c
printf("%d\n",sizeof(arr1) / sizeof(arr1[0]));
// จะมีค่าเท่ากับ 9
printf("%d",sizeof(arr2[0]) / sizeof(arr2[0][0]));
// จะมีค่าเท่ากับ 3
```

หากใน array นั้นไม่มีข้อมูลใดๆเลย จะนำค่า 0 ออกมา เเต่ใน Ruby มีวิธีที่ง่ายกว่านั้น นั่นคือคำสั่ง .empty?

.empty? ใช้เพื่อเช็คว่า array นั้นมีค่าอยู่ภายในนั้นหรือไม่ โดยค่าผลลัพท์ที่ออกมาจะเป็น boolean เท่านั้น เป็น true เมื่อ มีข้อมูลอยู่ภายใน array อย่างน้อย 1 ค่า เเละเป็น false เมื่อไม่มีค่าใดๆเลย

```ruby
arr1.empty?
arr2.empty?
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr1.empty?
# จะมีค่าเท่ากับ false
puts arr3.empty?
# จะมีค่าเท่ากับ true
```

**ตัวอย่างในภาษาอื่น**

ในภาษาอื่นๆเช่น Python, Java ไม่มีคำสั่งที่ทำหน้าที่คล้ายหรือเหมือนกับ .empty? ได้โดยตรง เเต่สามารถพลิกเเพลงใช้วิธีอื่นๆในการทำให้ได้ผลลับเดียวกันออกมาได้ เช่น​

> Python

```python
print(not arr1)
# จะมีค่าเท่ากับ False
print(not arr3)
# จะมีค่าเท่ากับ True
```

> Java

```java
System.out.println(arr1.length == 0);
// จะมีค่าเท่ากับ False
System.out.println(arr3.length == 0);
// จะมีค่าเท่ากับ True
```

array ในภาษา C ไม่ใช่ array เเบบ dynamic array จึงไม่สามารถ/จำเป็น ต้องเช็คว่า array นี้ว่างหรือไม่ เพราะยังไงเราก็ต้องกำหนดค่าเริ่มต้นให้อยู่เเล้ว จึงไม่มีทางที่ array จะว่างได้

ใน Ruby หากเราต้องการ search ว่าค่านั้นๆมีอยู่ใน array ของเราหรือไม่ ใน Ruby สามารถทำได้โดยใช้คำสั่ง .include?() โดย Ruby จะค้นหาค่าที่อยู่ใน () ว่ามีอยู่ใน array ของเราหรือไม่ เเล้วจะคืนค่าออกมาเป็น boolean

```ruby
arr1.include?(5)
arr2.include?([4,5,6])
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr1.include?(5)
# จะมีค่าเท่ากับ true
puts arr2.include?([4,5,6])
# จะมีค่าเท่ากับ true
puts arr2[1].include?(5)
# จะมีค่าเท่ากับ true
```

**ตัวอย่างในภาษาอื่น**

ในภาษาอื่นๆเช่น Python, Java ไม่มีคำสั่งที่ทำหน้าที่คล้ายหรือเหมือนกับ .include? ได้โดยตรง เเต่สามารถพลิกเเพลงใช้วิธีอื่นๆในการทำให้ได้ผลลับเดียวกันออกมาได้ เช่น​

> Python

```python
print(5 in arr1)
# จะมีค่าเท่ากับ True
print([4,5,6] in arr2)
# จะมีค่าเท่ากับ True
print(5 in arr2[1])
# จะมีค่าเท่ากับ True
```

> Java

```java
import java.util.Arrays;
import java.util.List;

List<Integer> list1 = Arrays.asList(arr1);
List<List<Integer>> arr2 = Arrays.asList(
    Arrays.asList(1,2,3),
    Arrays.asList(4,5,6),
    Arrays.asList(7,8,9)
);

System.out.println(list1.contains(5));
// จะมีค่าเท่ากับ true
System.out.println(arr2.contains(Arrays.asList(4,5,6)));
// จะมีค่าเท่ากับ true
System.out.println(arr2.get(1).contains(5));
// จะมีค่าเท่ากับ true
```

ใน C ไม่มี ฟังก์ชั่นสำเร็จรูปเลย จึงจำเป็นต้องเขียนเอง

เเต่ถ้าเราอยากได้ตำเเหน่งในค่าที่เจอด้วยต้องใช้คำสั่ง .index() หรือ .rindex() โดยสองตัวนี้เเตกต่างกันที่ .index() จะออกผลลัพเป็นตำเเหน่งเเรกที่พบเจอ เเต่ .rindex() จะเป็นตำเเหน่งสุดท้ายที่เจอ

```ruby
arr1.index(5)
arr2.index([4,5,6])
arr4.rindex(2)
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr1.index(5)
# จะมีค่าเท่ากับ 4
puts arr2.index([4,5,6])
# จะมีค่าเท่ากับ 1
puts arr4.rindex(2)
# จะมีค่าเท่ากับ 5
```

**ตัวอย่างในภาษาอื่น**

ในภาษาอื่นๆเช่น Python ไม่มีคำสั่งที่ทำหน้าที่คล้ายหรือเหมือนกับ .include? ได้โดยตรง เเต่สามารถพลิกเเพลงใช้วิธีอื่นๆในการทำให้ได้ผลลับเดียวกันออกมาได้ เช่น​

> Python

```python
print(arr1.index(5))
# จะมีค่าเท่ากับ 4
print(arr2.index([4,5,6]))
# จะมีค่าเท่ากับ 1
print(len(arr4) - 1 - arr4[::-1].index(2))
# จะมีค่าเท่ากับ 5
```

ในภาษา java เเละ c ไม่มีคำสั่งสำเร็จรูปที่ทำหน้าที่คล้ายกันเลย จึงต้องเขียนอัลกอริทึมขึ้นมาใหม่

ในภาษา Ruby หากต้องการนับจำนวนค่าที่เราต้องการสามารถใช้คำสั่ง .count() ได้ โดยใส่ค่าที่ต้องการลงไปใน ()

```ruby
arr4.count(2)
```

**วิธีการใช้งาน**

> Ruby

```ruby
puts arr4.count(2)
# จะมีค่าเท่ากับ 3
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
print(arr4.count(2))
# จะมีค่าเท่ากับ 3
```

ถ้าเป็น array เเบบปกติ จะต้องเขียน loop เพื่อนับเอง เเต่มีคำสั่งสำเร็จเมื่อใช้ List

> Java

```java
import java.util.List;
List<Integer> arr4 = Arrays.asList(1,1,1,2,2,2,3,3,3);
System.out.println(Collections.frequency(arr4, 2));
// จะมีค่าเท่ากับ 3
```

ในภาษา C จะต้องเขียน loop เพื่อนับเอง

> C

```c
int count(int arr[], int size, int value) {
    int c = 0;
    for (int i = 0; i < size; i++) {
        if (arr[i] == value) c++;
    }
    return c;
}

printf("%d", count(arr4, sizeof(arr4) / sizeof(arr4[0]), 2));
```

ในภาษา Ruby มีการตรวจสอบเงื่อนไขใน array เเบบสั้นๆได้ด้วย 3 คำสั่งนี้

- **any?** หมายถึง ตรวจสอบว่า มี element ใดบ้าง ที่เป็นจริงตามเงื่อนไขหรือไม่
  - ถ้าเจอ อย่างน้อย 1 ตัว -> คืนค่า true
  - ถ้าไม่เจอเลย -> คืนค่า false

```ruby
arr1.any? { |x| x > 3 }
arr1.any? { |x| x > 10 }
```

- **all?** หมายถึง ตรวจสอบว่า ทุก element เป็นจริงตามเงื่อนไขหรือไม่
  - ถ้าทุกตัวผ่าน -> คืนค่า true
  - ถ้ามีแม้แต่ 1 ตัวไม่ผ่าน -> คืนค่า false

```ruby
arr1.all? { |x| x.even? }
arr1.all? { |x| x > 3 }
```

- **none?** หมายถึง ตรวจสอบว่า ไม่มี element ใดเลย ที่ตรงตามเงื่อนไข
  - ถ้าไม่เจอสักตัว -> คืนค่า true
  - ถ้าเจอแม้แต่ 1 ตัว -> คืนค่า false

```ruby
arr1.none? { |x| x.even? }
arr1.none? { |x| x > 4 }
```

**วิธีการใช้งาน**

> Ruby

```ruby
# any?
puts arr1.any? { |x| x > 3 }
# จะมีค่าเท่ากับ true
puts arr1.any? { |x| x > 10 }
# จะมีค่าเท่ากับ false

# all?
puts arr1.all? { |x| x.even? }
# จะมีค่าเท่ากับ false
puts arr1.all? { |x| x > 3 }
# จะมีค่าเท่ากับ false

#none?
puts arr1.none? { |x| x.even? }
# จะมีค่าเท่ากับ false
puts arr1.none? { |x| x > 4 }
# จะมีค่าเท่ากับ false
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
# any?
print(any(x > 3 for x in arr1))
# จะมีค่าเท่ากับ true
print(any(x > 10 for x in arr1))
# จะมีค่าเท่ากับ false

# all?
print(all(x % 2 == 0 for x in arr1))
# จะมีค่าเท่ากับ false
print(all(x > 3 for x in arr1))
# จะมีค่าเท่ากับ false

# none?
print(not any(x % 2 == 0 for x in arr1))
# จะมีค่าเท่ากับ false
print(not any(x > 4 for x in arr1))
# จะมีค่าเท่ากับ false
```

ในภาษา java ต้องimport List เเละ Stream เพิ่มเติม

> Java

```java
import java.util.*;
import java.util.stream.*;

List<Integer> arr1 = Arrays.asList(1,2,3,4,5,6,7,8,9);

// any?
System.out.println(arr1.stream().anyMatch(x -> x > 3));
// จะมีค่าเท่ากับ true
System.out.println(arr1.stream().anyMatch(x -> x > 10));
// จะมีค่าเท่ากับ false

// all?
System.out.println(arr1.stream().allMatch(x -> x % 2 == 0));
// จะมีค่าเท่ากับ false
System.out.println(arr1.stream().allMatch(x -> x > 3));
// จะมีค่าเท่ากับ false

// none?
System.out.println(arr1.stream().noneMatch(x -> x % 2 == 0));// จะมีค่าเท่ากับ false
System.out.println(arr1.stream().noneMatch(x -> x > 4));// จะมีค่าเท่ากับ false
```

ในภาษา C ต้องเขียน loop เช็คเองทั้งหมด

## 3. Modification / Mutation (แก้ไขค่าใน Array)

- .push() / <<
- .pop()
- .shift()
- .unshift()
- .insert()
- .selete() / .delete_at()
- .compact! / .uniq! / .reverse! / .sort!

**ยกตัวอย่างการสร้าง array**

```ruby
arr1 = [1,2,3,4,5,6,7,8,9]
arr2 = [[1,2,3],[4,5,6],[7,8,9]]
arr3 = []
arr4 = [1,1,1,2,2,2,3,3,3]
```

อธิบายหัวข้อนี้เเบบง่ายๆคือ คำสั่งที่ใช้ เพิ่ม ลบ เปลี่ยนค่า ใน array

.push() หรือ << ใช้เพิ่มค่าลงท้าย array

```ruby
arr1.push(10)
arr2.push([10])

arr1 << 10
arr2 << [10]
```

**วิธีการใช้งาน**

> Ruby

```ruby
arr1.push(10)
arr2.push([10])
p arr1
# จะมีค่าเท่ากับ [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
p arr2
# จะมีค่าเท่ากับ [[1, 2, 3], [4, 5, 6], [7, 8, 9], [10]]

arr1 << 10
arr2 << [10]
p arr1
# จะมีค่าเท่ากับ [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
p arr2
# จะมีค่าเท่ากับ [[1, 2, 3], [4, 5, 6], [7, 8, 9], [10]]
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
arr1.append(10)
arr2.append([10])

print(arr1)
# จะมีค่าเท่ากับ [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(arr2)
# จะมีค่าเท่ากับ [[1, 2, 3], [4, 5, 6], [7, 8, 9], [10]]
```

ในภาษา java จะต้อง import arraylist เพิ่มเติม

> Java

```java
import java.util.ArrayList;
List<Integer> arr1 = new ArrayList<>(Arrays.asList(1,2,3,4,5,6,7,8,9));
List<List<Integer>> arr2 = new ArrayList<>();
arr2.add(Arrays.asList(1,2,3));
arr2.add(Arrays.asList(4,5,6));
arr2.add(Arrays.asList(7,8,9));

arr1.add(10);
arr2.add(Arrays.asList(10));

System.out.println(arr1);
// จะมีค่าเท่ากับ [1,2,3,4,5,6,7,8,9,10]
System.out.println(arr2);
// จะมีค่าเท่ากับ [[1,2,3],[4,5,6],[7,8,9],[10]]
```

ในภาษา c จะต้องใช้ dynamic array ถึงจะสามารถเพิ่มค่าได้เเบบเดียวกันกับpush เเล้วจะต้องเขียน function เองเท่านั้น ไม่มีคำสั่งสำเร็จรูปให้

ถ้าจะนำออก ให้ใช้ .pop() จะเป็นการลบค่าที่อยู่ด้านหลังออกก่อน

```ruby
arr1.pop()
arr2.pop()
```

**วิธีการใช้งาน**

> Ruby

```ruby
arr1.pop()
arr2.pop()
p arr1
# จะมีค่าเท่ากับ [1, 2, 3, 4, 5, 6, 7, 8]
p arr2
# จะมีค่าเท่ากับ [[1, 2, 3], [4, 5, 6]]
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
arr1.pop()
arr2.pop()

print(arr1)
# จะมีค่าเท่ากับ [1, 2, 3, 4, 5, 6, 7, 8]
print(arr2)
# จะมีค่าเท่ากับ [[1, 2, 3], [4, 5, 6]]
```

ในภาษา java จะต้อง import arraylist เพิ่มเติม

> Java

```java
import java.util.ArrayList;
ArrayList<Integer> arr1 = new ArrayList<>(Arrays.asList(1,2,3,4,5,6,7,8,9));
ArrayList<ArrayList<Integer>> arr2 = new ArrayList<>(
    Arrays.asList(
        new ArrayList<>(Arrays.asList(1,2,3)),
        new ArrayList<>(Arrays.asList(4,5,6)),
        new ArrayList<>(Arrays.asList(7,8,9))
    )
);

arr1.remove(arr1.size()-1);
arr2.remove(arr2.size()-1);

System.out.println(arr1);
// จะมีค่าเท่ากับ [1, 2, 3, 4, 5, 6, 7, 8]
System.out.println(arr2);
// จะมีค่าเท่ากับ [[1, 2, 3], [4, 5, 6]]
```

ในภาษา c จะต้องใช้ dynamic array ถึงจะสามารถเพิ่มค่าได้เเบบเดียวกันกับpush เเล้วจะต้องเขียน function เองเท่านั้น ไม่มีคำสั่งสำเร็จรูปให้

เเต่ถ้าหากต้องการนำตัวเเรกของ array ออก สามารถใช้คำสั่ง .shift() ได้เลย

```ruby
arr1.shift()
arr2.shift()
```

**วิธีการใช้งาน**

> Ruby

```ruby
arr1.shift()
arr2.shift()

p arr1
# จะมีค่าเท่ากับ [2, 3, 4, 5, 6, 7, 8, 9]
p arr2
# จะมีค่าเท่ากับ [[4, 5, 6],[7, 8, 9]]
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
arr1.pop(0)
arr2.pop(0)

print(arr1)
# จะมีค่าเท่ากับ [2, 3, 4, 5, 6, 7, 8, 9]
print(arr2)
# จะมีค่าเท่ากับ [[4, 5, 6],[7, 8, 9]]
```

ในภาษา java จะต้อง import arraylist เพิ่มเติม

> Java

```java
import java.util.ArrayList;
ArrayList<Integer> arr1 = new ArrayList<>(Arrays.asList(1,2,3,4,5,6,7,8,9));
ArrayList<ArrayList<Integer>> arr2 = new ArrayList<>(
    Arrays.asList(
        new ArrayList<>(Arrays.asList(1,2,3)),
        new ArrayList<>(Arrays.asList(4,5,6)),
        new ArrayList<>(Arrays.asList(7,8,9))
    )
);

arr1.remove(0);
arr2.remove(0);

System.out.println(arr1);
// จะมีค่าเท่ากับ [2, 3, 4, 5, 6, 7, 8, 9]
System.out.println(arr2);
// จะมีค่าเท่ากับ [[4, 5, 6], [7, 8, 9]]
```

ในภาษา c จะต้องใช้ dynamic array ถึงจะสามารถเพิ่มค่าได้เเบบเดียวกันกับpush เเล้วจะต้องเขียน function เองเท่านั้น ไม่มีคำสั่งสำเร็จรูปให้

เเละด้วยคำสั่งคล้ายกันสามรถเพิ่มค่าที่ตำเเหน่งเเรกสุดได้ด้วยคำสั่ง .unshift()

```ruby
arr1.unshit(99)
arr2.unshift([99, 98, 97])
```

**วิธีการใช้งาน**

> Ruby

```ruby
arr1.unshit(99)
arr2.unshift([99, 98, 97])

p arr1
# จะมีค่าเท่ากับ [99, 1, 2, 3, 4, 5, 6, 7, 8, 9]
p arr2
# จะมีค่าเท่ากับ [[99, 98, 97], [1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
arr1.insert(0, 1)
arr2.insert(0, [1,2,3])

print(arr1)
# จะมีค่าเท่ากับ [99, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print(arr2)
# จะมีค่าเท่ากับ [[99, 98, 97], [1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

ในภาษา java จะต้อง import arraylist เพิ่มเติม

> Java

```java
import java.util.ArrayList;
ArrayList<Integer> arr1 = new ArrayList<>(Arrays.asList(1,2,3,4,5,6,7,8,9));
ArrayList<ArrayList<Integer>> arr2 = new ArrayList<>(
    Arrays.asList(
        new ArrayList<>(Arrays.asList(1,2,3)),
        new ArrayList<>(Arrays.asList(4,5,6)),
        new ArrayList<>(Arrays.asList(7,8,9))
    )
);

arr1.add(0,99);
arr2.add(0,new ArrayList<>(Arrays.asList(99, 98, 97)));

System.out.println(arr1);
// จะมีค่าเท่ากับ [99, 1, 2, 3, 4, 5, 6, 7, 8, 9]
System.out.println(arr2);
// จะมีค่าเท่ากับ [[99, 98, 97], [1, 2, 3][4, 5, 6], [7, 8, 9]]
```

ในภาษา c จะต้องใช้ dynamic array ถึงจะสามารถเพิ่มค่าได้เเบบเดียวกันกับpush เเล้วจะต้องเขียน function เองเท่านั้น ไม่มีคำสั่งสำเร็จรูปให้

ถ้าอยากเเทรกให้อยู่ระหว่าง array ใช้คำสั่ง .insert() โดยต้องใส่ พารามิเตอร์ 2 ตัว ตัวเเรกคือตำเเหน่งที่ต้องการเเทรก ตัวที่สองคือ ค่าที่ต้องการเเทรก

```ruby
arr1.insert(3, 4)
```

**วิธีการใช้งาน**

> Ruby

```ruby
arr1.insert(3,99)
arr2.insert(2,[99,98,97])

p arr1
# จะมีค่าเท่ากับ [1, 2, 3, 99, 4, 5, 6, 7, 8, 9]
p arr2
# จะมีค่าเท่ากับ [[1, 2, 3], [4, 5, 6], [99, 98, 97], [7, 8, 9]]
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
arr1.insert(3, 99)
arr2.insert(2,[99,98,97])

print(arr1)
# จะมีค่าเท่ากับ [1, 2, 3, 99, 4, 5, 6, 7, 8, 9]
print(arr2)
# จะมีค่าเท่ากับ [[1, 2, 3], [4, 5, 6], [99, 98, 97], [7, 8, 9]]
```

ในภาษา java จะต้อง import arraylist เพิ่มเติม

> Java

```java
import java.util.ArrayList;
ArrayList<Integer> arr1 = new ArrayList<>(Arrays.asList(1,2,3,4,5,6,7,8,9));
ArrayList<ArrayList<Integer>> arr2 = new ArrayList<>(
    Arrays.asList(
        new ArrayList<>(Arrays.asList(1,2,3)),
        new ArrayList<>(Arrays.asList(4,5,6)),
        new ArrayList<>(Arrays.asList(7,8,9))
    )
);

arr1.add(3,99);
arr2.add(2,new ArrayList<>(Arrays.asList(99, 98, 97)));

System.out.println(arr1);
// จะมีค่าเท่ากับ [1, 2, 3, 99, 4, 5, 6, 7, 8, 9]
System.out.println(arr2);
// จะมีค่าเท่ากับ [[1, 2, 3], [4, 5, 6], [99, 98, 97], [7, 8, 9]]
```

ในภาษา c จะต้องใช้ dynamic array ถึงจะสามารถเพิ่มค่าได้เเบบเดียวกันกับpush เเล้วจะต้องเขียน function เองเท่านั้น ไม่มีคำสั่งสำเร็จรูปให้

ถ้าต้องการลบสมาชิกเเบบกำหนดค่าหรือกำหนดตำเเหน่ง ต้องใช้คำสั่ง .delete()/.delete_at() ตามลำดับ

```ruby
arr1.delete(2)
arr1.delete_at(2)
```

**วิธีการใช้งาน**

> Ruby

```ruby
arr1.delete(2)
arr2.delete([4,5,6])
p arr1
# จะมีคาเท่ากับ [1, 3, 4, 5, 6, 7, 8, 9]
p arr2
# จะมีคาเท่ากับ [[1, 2, 3], [7, 8, 9]]

arr1.delete_at(5)
arr2.delete(0)
p arr1
# จะมีคาเท่ากับ [1, 2, 3, 4, 5, 7, 8, 9]
p arr2
# จะมีคาเท่ากับ [[4, 5, 6], [7, 8, 9]]
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
arr1.remove(2)
arr2.remove([4, 5, 6])


print(arr1)
# จะมีคาเท่ากับ [1, 3, 4, 5, 6, 7, 8, 9]
print(arr2)
# จะมีคาเท่ากับ [[1, 2, 3], [7, 8, 9]]

arr1.pop(5)
arr2.pop(0)

print(arr1)
# จะมีคาเท่ากับ [1, 2, 3, 4, 5, 7, 8, 9]
print(arr2)
# จะมีคาเท่ากับ [[4, 5, 6], [7, 8, 9]]
```

ในภาษา java จะต้อง import arraylist เพิ่มเติม

> Java

```java
List<Integer> arr1 = new ArrayList<>(Arrays.asList(1,2,3,4,5,6,7,8,9));
List<List<Integer>> arr2 = new ArrayList<>();
arr2.add(Arrays.asList(1,2,3));
arr2.add(Arrays.asList(4,5,6));
arr2.add(Arrays.asList(7,8,9));

arr1.remove(Integer.valueOf(2));
arr2.remove(Arrays.asList(4,5,6));

System.out.println(arr1);
// จะมีคาเท่ากับ [1, 3, 4, 5, 6, 7, 8, 9]
System.out.println(arr2);
// จะมีคาเท่ากับ [[1, 2, 3], [7, 8, 9]]

arr1.remove(5);
arr2.remove(0);

System.out.println(arr1);
// จะมีคาเท่ากับ [1, 2, 3, 4, 5, 7, 8, 9]
System.out.println(arr2);
// จะมีคาเท่ากับ [[4, 5, 6], [7, 8, 9]]
```

ในภาษา c จะต้องใช้ dynamic array ถึงจะสามารถเพิ่มค่าได้เเบบเดียวกันกับpush เเล้วจะต้องเขียน function เองเท่านั้น ไม่มีคำสั่งสำเร็จรูปให้

ในภาษา Ruby มีคำสั่งในการเเก้ปัญหาเฉพาะได้เช่น ลบ nil ลบค่าซ้ำ หรือ เปลี่ยนเเปลงลำดับเป็นเเบบกลับหลัง หรือเรียงค่าจากน้อยไปมากได้ สามารถใช้คำสั่ง .compact! / .uniq! / .reverse! / .sort! ตามลำดับ

```ruby
arr1 = [1, nil, 2, nil, 3]
arr2 = [1,1,1,2,2,2,3,3,3]
arr3 = [1,2,3,4,5]
arr4 = [5,7,9,4,2,3,1]
```

**วิธีการใช้งาน**

> Ruby

```ruby
arr1 = [1, nil, 2, nil, 3]
arr2 = [1,1,1,2,2,2,3,3,3]
arr3 = [1,2,3,4,5]
arr4 = [5,7,9,4,2,3,1]

p arr1.compact!
# จะมีค่าเท่ากับ [1, 2, 3]
p arr2.uniq!
# จะมีค่าเท่ากับ [1, 2, 3]
p arr3.reverse!
# จะมีค่าเท่ากับ [5, 4, 3, 2, 1]
p 4.sort!
# จะมีค่าเท่ากับ [1, 2, 3, 4, 5, 7, 9]
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
arr1[:] = [x for x in arr1 if x is not None]
print(arr1)
# จะมีค่าเท่ากับ [1, 2, 3]
arr2[:] = list(dict.fromkeys(arr2))  # ลบซ้ำ + คงลำดับ
print(arr2)
# จะมีค่าเท่ากับ [1, 2, 3]
arr3.reverse()
print(arr3)
# จะมีค่าเท่ากับ [5, 4, 3, 2, 1]
arr4.sort()
print(arr4)
# จะมีค่าเท่ากับ [1, 2, 3, 4, 5, 7, 9]
```

ในภาษา java จะต้อง import arraylist เพิ่มเติม

> Java

```java
List<Integer> arr1 = new ArrayList<>(Arrays.asList(1, null, 2, null, 3));
List<Integer> arr2 = new ArrayList<>(Arrays.asList(1,1,1,2,2,2,3,3,3));
List<Integer> arr3 = new ArrayList<>(Arrays.asList(1,2,3,4,5));
List<Integer> arr4 = new ArrayList<>(Arrays.asList(5,7,9,4,2,3,1));

arr1.removeIf(Objects::isNull);
System.out.println(arr1);
// จะมีค่าเท่ากับ [1, 2, 3]
LinkedHashSet<Integer> set = new LinkedHashSet<>(arr2);
arr2.clear();
arr2.addAll(set);
System.out.println(arr2);
// จะมีค่าเท่ากับ [1, 2, 3]
Collections.reverse(arr3);
System.out.println(arr3);
// จะมีค่าเท่ากับ [5, 4, 3, 2, 1]
Collections.sort(arr4);
System.out.println(arr4);
// จะมีค่าเท่ากับ [1, 2, 3, 4, 5, 7, 9]
```

ในภาษา c จะต้องใช้ dynamic array ถึงจะสามารถเพิ่มค่าได้เเบบเดียวกันกับpush เเล้วจะต้องเขียน function เองเท่านั้น ไม่มีคำสั่งสำเร็จรูปให้

## 4. Enumeration / Iteration (วน loop / map / filter)

- .each
- .map() / .collect()
- .select() / .filter()
- .reject()
- .find() / .detect()
- .reduce() / .inject()
- .each_with_index()

**ยกตัวอย่างการสร้าง array**

```ruby
arr1 = [1,2,3,4,5]
arr2 = [[1,2,3],[4,5,6],[7,8,9]]
```

ปกติเเล้วการเขียนลูปโดยวนทุกตัว เราจะต้องเขียนเองเเต่ในภาษา Ruby มีคำสั่งลัดทีทำให้เองเลย นั่นคือ .each()

```ruby
arr1.each do |x|
end
arr2.each do |x|
end
```

**วิธีการใช้งาน**

> Ruby

```ruby
arr1.each do |x|
    print x , " "
end
# จะมีค่าเท่ากับ 1 2 3 4 5
arr2.each do |x|
    print x , " "
end
# จะมีค่าเท่ากับ 1 2 3 4 5 6 7 8 9
```

**ตัวอย่างในภาษาอื่น**

> Python

```python
for x in arr1:
    print(x, end=" ")
print()
# จะมีค่าเท่ากับ 1 2 3 4 5

for sublist in arr2:
    for x in sublist:
        print(x, end=" ")
print()
# จะมีค่าเท่ากับ 1 2 3 4 5 6 7 8 9
```

ในภาษา java จะต้อง import arraylist เพิ่มเติม

> Java

```java
List<Integer> arr1 = Arrays.asList(1,2,3,4,5);
List<List<Integer>> arr2 = Arrays.asList(
    Arrays.asList(1,2,3),
    Arrays.asList(4,5,6),
    Arrays.asList(7,8,9)
);

for (int x : arr1) {
    System.out.print(x + " ");
}
System.out.println();
// จะมีค่าเท่ากับ 1 2 3 4 5

for (List<Integer> sublist : arr2) {
    for (int x : sublist) {
        System.out.print(x + " ");
    }
}
System.out.println();
// จะมีค่าเท่ากับ 1 2 3 4 5 6 7 8 9
```

>C
```c
int arr1[] = {1,2,3,4,5};
int size1 = 5;

int arr2[][3] = {{1,2,3},{4,5,6},{7,8,9}};
int rows = 3, cols = 3;

for(int i=0; i<size1; i++) {
    printf("%d ", arr1[i]);
}
printf("\n");
// จะมีค่าเท่ากับ 1 2 3 4 5

for(int i=0; i<rows; i++) {
    for(int j=0; j<cols; j++) {
        printf("%d ", arr2[i][j]);
    }
}
printf("\n");
// จะมีค่าเท่ากับ 1 2 3 4 5 6 7 8 9
```

ใช้สำหรับลูปแล้วแปลงค่าใน array คือสำคั่ง .map / .collect
```ruby
arr1.map { |x| x + 10 }
arr1.collect { |x| x * 2 }
```

**วิธีการใช้งาน**
>Ruby
```ruby
new_arr = arr1.map { |x| x + 10 }
p new_arr
# จะมีค่าเท่ากับ [11,12,13,14,15]
new_arr2 = arr1.collect { |x| x * 2 }
p new_arr2
# จะมีค่าเท่ากับ [2,4,6,8,10]
```

**ตัวอย่างในภาษาอื่น**
>Python
```python
new_arr = [x + 10 for x in arr1]
print(new_arr)
# จะมีค่าเท่ากับ [11,12,13,14,15]
new_arr2 = list(map(lambda x: x*2, arr1))
print(new_arr2)
# จะมีค่าเท่ากับ [2,4,6,8,10]
```
ในภาษา java จะต้อง import arraylist เเละ stream.Collectors เพิ่มเติม
>Java
```java
import java.util.*;
import java.util.stream.Collectors;

List<Integer> arr1 = Arrays.asList(1,2,3,4,5);
List<Integer> newArr = arr1.stream().map(x -> x + 10).collect(Collectors.toList());
System.out.println(newArr);
// จะมีค่าเท่ากับ [11,12,13,14,15]

List<Integer> newArr2 = arr1.stream().map(x -> x * 2).collect(Collectors.toList());
System.out.println(newArr2);
// จะมีค่าเท่ากับ [2,4,6,8,10]
```

ในภาษา c จะต้องใช้ dynamic array ถึงจะสามารถเพิ่มค่าได้เเบบเดียวกันกับpush เเล้วจะต้องเขียน function เองเท่านั้น ไม่มีคำสั่งสำเร็จรูปให้

หากต้องการเลือกค่าใน array ให้เป็นค่าที่เลือก


## 5. Advanced / Combinatorics / Utilities (การใช้งานขั้นสูง / การคำนวณ / สถิติ)

# Reference

- Ruby Programming Language - class Array. ​เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://docs.ruby-lang.org/en/master/Array.html​
- RubyDoc.info (ไม่กำหนด) class Array. ​เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://www.ruby-doc.org/core/Array.html​
- IncludeHelp. (ไม่กำหนด).Ruby Array Methods. ​เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://www.includehelp.com/ruby/ruby-array-methods.aspx#google_vignette​
- FreeCodeCamp (27 มกราคม 2020) Most common Ruby array methods you should know. เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://www.freecodecamp.org/news/common-array-methods-in-ruby​
- George, J (1 พฤจิกายน 2015) Ruby array methods. ​เข้าถึงเมื่อ 31 สิงหาคม 2025​ จาก https://webdevjeffus.github.io/projects/cheat-sheet.html​
- Python documentation (31 สิงหาคม 2025) Efficient arrays of numeric values.​ เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://docs.python.org/3/library/array.html​
- Oracle Help Center (ไม่กำหนด) Arrays (Java Platform SE 8) ​เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html​
- W3School (ไม่กำหนด) C Arrays​ เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://www.w3schools.com/c/c_arrays.php​
- GeeksforGeeks (26 กรกฏาคม 2025) C Arrays​เข้าถึงเมื่อ 31 สิงหาคม 2025 ​จาก https://www.geeksforgeeks.org/c/c-arrays​
