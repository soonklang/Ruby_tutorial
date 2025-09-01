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

>Ruby
```ruby
puts arr1[2]
# คำตอบที่ได้คือ 3
puts arr2[0][2]
# คำตอบที่ได้คือ 3
```

**ตัวอย่างในภาษาอื่น**

>Python
```python
print(arr1[2])
# คำตอบที่ได้คือ 3
print(arr2[0][2])
# คำตอบที่ได้คือ 3
```

>Java
```java
System.out.println(arr1[2]);
# คำตอบที่ได้คือ 3
System.out.println(arr2[0][2]);
# คำตอบที่ได้คือ 3
```

>C
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

>Ruby
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

>Ruby
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

>Ruby
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

>Python
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

>Java
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

>C
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

>Ruby
```ruby
puts arr1.values_at(1,3,4)
# คำตอบที่ได้คือ 2 4 5
p arr2.values_at(0,2)
# คำตอบที่ได้คือ [[1,2,3], [7, 8, 9]]
```

**ตัวอย่างในภาษาอื่น**

ในภาษาอื่นๆเช่น Python, Java, C ไม่มีคำสั่งที่ทำหน้าที่คล้ายหรือเหมือนกับ .values_at() ได้โดยตรง เเต่สามารถพลิกเเพลงใช้วิธีอื่นๆในการทำให้ได้ผลลับเดียวกันออกมาได้ เช่น​

>Python
```python
result = [arr1[i] for i in [1,3,4]​]​
print(result)
#จะมีค่าเท่ากับ [2,4,5]

result = [arr2[i] for i in [0,2]]
print(result)
#จะมีค่าเท่ากับ [[1,2,3],[7,8,9]]
```

>Java
```java
import java.util.Arrays;

int[] result = { arr1[1], arr1[3], arr1[4] };
System.out.println(Arrays.toString(result));
// จะมีค่าเท่ากับ [2, 4, 5]

int[][] result = { arr2[0], arr2[2] };
System.out.println(Arrays.deepToString(result)); 
// จะมีค่าเท่ากับ [[1, 2, 3], [7, 8, 9]]
```

>C
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

ในภาษา Ruby มีคำสั่งที่ใช้ดึงค่าใน array ตั้งเเต่ค่าเเรกสุดจนถึงค่าที่อยู่ใน () ของ .take() โดยเริ่มจาก 1  หากใส่จำนวนที่นอกขอบเขตที่มี จะไม่เเสดงเลขใดๆออกมาเลย
```ruby
arr1.take(3)
arr2.take(2)
```

**วิธีการใช้งาน**

>Ruby
```ruby
puts arr1.take(3)
# คำตอบที่ได้คือ 1 2 3
p arr2.take(2)
# คำตอบที่ได้คือ [[1, 2, 3], [4, 5, 6]]
```

**ตัวอย่างในภาษาอื่น**

ในภาษาอื่นๆเช่น Python, Java, C ไม่มีคำสั่งที่ทำหน้าที่คล้ายหรือเหมือนกับ .take() ได้โดยตรง เเต่สามารถพลิกเเพลงใช้วิธีอื่นๆในการทำให้ได้ผลลับเดียวกันออกมาได้ เช่น​

>Python
```python
print(arr1[:3])
# คำตอบที่ได้คือ 1 2 3
print(arr2[:2][:3])
# คำตอบที่ได้คือ [[1, 2, 3], [4, 5, 6]]
```

>Java
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

>C
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

>Ruby
```ruby
puts arr1.drop(6)
# คำตอบที่ได้คือ 7 8 9
p arr2.drop(2)
# คำตอบที่ได้คือ [[7, 8, 9]]
```

**ตัวอย่างในภาษาอื่น**

ในภาษาอื่นๆเช่น Python, Java, C ไม่มีคำสั่งที่ทำหน้าที่คล้ายหรือเหมือนกับ .drop() ได้โดยตรง เเต่สามารถพลิกเเพลงใช้วิธีอื่นๆในการทำให้ได้ผลลับเดียวกันออกมาได้ เช่น​

>Python
```python
print(arr1[6:])​
#จะมีค่าเท่ากับ [7,8,9]
print(arr2[2:][:])​
#จะมีค่าเท่ากับ [[7, 8, 9]]
```

>Java
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

>C
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

>Ruby
```ruby
puts arr1.fetch(3, "Not Found")
# คำตอบที่ได้คือ 4
p arr2.fetch(99, "Not Found")
# คำตอบที่ได้คือ "Not Found"
```

**ตัวอย่างในภาษาอื่น**

ในภาษาอื่นๆเช่น Python, Java, C ไม่มีคำสั่งที่ทำหน้าที่คล้ายหรือเหมือนกับ .fetch() ได้โดยตรง เเต่สามารถพลิกเเพลงใช้วิธีอื่นๆในการทำให้ได้ผลลับเดียวกันออกมาได้ เช่น​

>Python
```python
index = 2
print(arr1[index] if index < len(arr1) else "Not Found")
# จะมีค่าเท่ากับ 3

index = 99
print(arr2[index] if index < len(arr2) else "Not Found")
# จะมีค่าเท่ากับ Not Found
```

>Java
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

>C
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
