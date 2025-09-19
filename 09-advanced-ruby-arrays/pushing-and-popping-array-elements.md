# Pushing and Popping Array Elements

Array ใน Ruby สามารถเป็น Stack แบบ Last in First Out (LIFO) ซึ่งสามารถ pop และ push ได้

## Syntax 
### 1.) การ push
>
array.push(element1, element2, ...)
> 1. ไม่จำเป็นต้องใส่ "()" ก็สามารถ push ได้ตามปกติ
>
### 2.) การ pop
array.pop()

array.pop(int)
>1. ไม่จำเป็นต้องใส่ "()" ก็สามารถ pop ได้ตามปกติ
>2. การใส่ค่า int คือการกำหนดว่าจะเอากี่ตัวสุดท้ายออกมาจาก array

## ตัวอย่าง
### สร้าง array ชื่อ fruits มีสามาชิกตาม code ด้านล่าง
```ruby
fruits = ["Apple","Banana","Mango","Orange"]
p fruits
```
<details close>
   <summary><b>Output</b></summary>
 <pre>["Apple", "Banana", "Mango", "Orange"]
 </pre>
</details>

### การ push
แบบที่ 1
```ruby
fruits.push "Grape","Pineapple"
p fruits
```
<details close>
   <summary><b>Output</b></summary>
 <pre>["Apple", "Banana", "Mango", "Orange", "Grape", "Pineapple"]
 </pre>
</details>

แบบที่ 2
```ruby
fruits.push("Kiwi")
p fruits
```

<details close>
   <summary><b>Output</b></summary>
 <pre>["Apple", "Banana", "Mango", "Orange", "Grape", "Pineapple", "Kiwi"]
 </pre>
</details>

### การ pop
แบบที่ 1
```ruby
p fruits
element = fruits.pop
p element
p fruits
```

<details close>
   <summary><b>Output</b></summary>
 <pre>["Apple", "Banana", "Mango", "Orange", "Grape", "Pineapple", "Kiwi"]
"Kiwi"
["Apple", "Banana", "Mango", "Orange", "Grape", "Pineapple"]
 </pre>
</details>

แบบที่ 2
```ruby
p fruits
element = fruits.pop(2)
p element
p fruits
```

<details close>
   <summary><b>Output</b></summary>
 <pre>["Apple", "Banana", "Mango", "Orange", "Grape", "Pineapple", "Kiwi"]
["Pineapple", "Kiwi"]
["Apple", "Banana", "Mango", "Orange", "Grape"]
 </pre>
</details>

>ข้อควรระวังผลลัพธ์ที่ได้จากการ pop แบบใส่ค่า int คือ array ที่นับ 2 ตัวสุดท้าย ไม่ใช้นับจากตัวสุดท้ายมา 2 ตัว
>
>สมมติว่านี่คือ array fruits ["Apple", "Banana", "Mango", "Orange", "Grape", "Pineapple", "Kiwi"]
>
>fruits.pop(2) จะให้ค่า ["Pineapple", "Kiwi"] แทนที่จะเป็น ["Kiwi","Pineapple"]

## เปรียบเทียบกับภาษาอื่น
### ภาษา C
- ในภาษา C **array มีขนาดคงที่** ไม่สามารถ **push** หรือ **pop** ได้เหมือน Ruby
- ถ้าต้องการเพิ่มหรือลบ ต้องใช้การจัดการหน่วยความจำ **malloc** ( กำหนดพื้นที่เริ่มต้น memory allocate ) / **realloc** ( กำหนดพื้นที่ใหม่ re-allocate )
- โดยทั่วไปจะสร้าง **ฟังก์ชัน** push/pop ขึ้นมาเอง

```c
#include <stdio.h> // Libary สำหรับ printf
#include <stdlib.h> // Libary สำหรับ malloc+realloc

// ฟังก์ชัน print array
void printArr(int *arr, int size) {
    printf("array : [");
    for (int i = 0; i < size; i++) {
        if (i) printf(", ");
        printf("%d", arr[i]);
    }
    printf("]\n");
}

int main() {
    int size = 0, capacity = 3; // กำหนด size ไว้ติดตามขนาด array ปัจจุบัน + สร้างตัวแปรกำหนดขนาด array
    int *arr = malloc(capacity * sizeof(int)); // จองพื้นที่ขนาดint 3 ตัว (12 bytes )

    // ทดลองเพิ่ม 3 ค่า 1,2,3
    for (int v = 1; v <= 3; v += 1) {
        // ตรวจสอบว่า array เต็มรึยัง ถ้าเต็มให้ *2 ขนาด array
        if (size == capacity) {
            capacity *= 2;
            arr = realloc(arr, capacity * sizeof(int));
        }
        
        // push ค่าลงไป
        arr[size++] = v;
        printArr(arr, size);
    }

    // pop ค่าสุดท้ายออกมา
    int last = arr[--size];
    printf("Pop: %d\n", last);
    printArr(arr, size);

    free(arr); //ปล่อย memory ที่จองไว้เมื่อไม่ได้ใช้แล้ว
    return 0;
}

```
<details close>
   <summary><b>Output</b></summary>
 <pre>array : [1]
array : [1, 2]
array : [1, 2, 3]
Pop: 3
array : [1, 2]
 </pre>
</details>

หลักการทำงานคือ
- จองพื้นที่ใน memory
- ถ้าจะ push ให้เช็คพื้นที่ว่าพอไหม ถ้าพอให้ เพิ่มค่าลงไปใน array ถ้าไม่พอให้เพิ่มขนาด array ก่อนแล้วค่อยเพิ่มค่าลง array
- pop คือเอาค่าตัวสุดท้ายออกมาและทำการลดตัวนับขนาด array ลงไป 1

### ภาษา Java
- ในภาษา java ไม่มี push หรือ pop ใน array ธรรมดา แต่มี libary ที่สามารถใช้ทำ ได้ทำเหมือนกันเลยนั้นคือ 
Deque ( Double Ended Queue ) คู่กับ ArrayDeque
```java
import java.util.ArrayDeque;
import java.util.Deque;

class Main {
    public static void main(String[] args) {
        Deque<String> stack = new ArrayDeque<>();
        //push
        stack.push("Apple");   
        stack.push("Banana");
        stack.push("Kiwi");
        
        System.out.println(stack);
        
        //pop
        System.out.println(stack.pop()); 
        
        System.out.println(stack);
    }
}

```
<details close>
   <summary><b>Output</b></summary>
 <pre>array : [Kiwi, Banana, Apple]
Kiwi
[Banana, Apple]
 </pre>
</details>

>Array ใน Deque ตัวที่ add เข้าไปล่าสุดจะอยู่ทางซ้ายของ array

### ภาษา Python
ใน Python ไม่มี **push** และ **pop** ใน array ธรรมดา แต่ **list** ใน Python เป็น dynamic array (เหมือน Ruby array) ซึ่งมีเมธอดที่ใช้งานได้คล้ายกันอยู่ คือ append() กับ pop()
```python
fruits = ["Apple", "Banana", "Mango"]

print(fruits)

# push
fruits.append("Orange")         
print(fruits)

# pop
last = fruits.pop()              
print("Pop:", last)
print(fruits)

last = fruits.pop()           
print("Pop:", last) 
print(fruits)                    
```
<details close>
   <summary><b>Output</b></summary>
 <pre>['Apple', 'Banana', 'Mango']
['Apple', 'Banana', 'Mango', 'Orange']
Pop: Orange
['Apple', 'Banana', 'Mango']
Pop: Mango
['Apple', 'Banana']
 </pre>
</details>

# Reference
- [ push และ pop ของ ruby ] https://www.techotopia.com/index.php/Advanced_Ruby_Arrays
- [ push และ pop ของ ruby ] https://www.studytonight.com/ruby/push-and-pop-in-ruby
- [ push และ pop ของ ruby ] https://ruby-doc.org/core-2.7.2/Array.html#method-i-push
- [ ภาษา C stack ] https://www.geeksforgeeks.org/c/implement-stack-in-c/
- [ ภาษา C Dynamic array ] https://www.geeksforgeeks.org/c/dynamic-memory-allocation-in-c-using-malloc-calloc-free-and-realloc/
- [ ภาษา java libary Deque] https://docs.oracle.com/javase/8/docs/api/java/util/Queue.html
- [ ภาษา java libary ArrayDeque] https://docs.oracle.com/javase/8/docs/api/java/util/ArrayDeque.html
- [ ภาษา python list] https://docs.python.org/3/tutorial/datastructures.html

# *Slide*
[Pushing and Popping Array Elements](https://github.com/user-attachments/files/22411652/PushAndPopArray.pdf)

# *Video Presentation*
[Video](https://youtu.be/Okpl21xvU2k)
