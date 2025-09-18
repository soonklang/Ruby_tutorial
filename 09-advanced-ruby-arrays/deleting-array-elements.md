
# Deleting Array Elements

---

คือการลบขนาดของ _array ตามค่า(value) หรือ ดัชนี (index)_

<details>
    <summary>Note</summary>
    <p>เนื่องจากเราจะมีการอ้างอิงประเภท <mark style ="background-color:#E7DDFF;color:#000;border-radius:5px">array - Ruby</mark> เป็นหลัก พบว่าทางอาร์เรย์เป็น array ประเภท <span style="border-bottom: 2px solid #D1CBFE;">Dynamic Array  + heterogeneous (multi type array)</span> จึงสามารถทำให้ภาษาอื่นมีรูปแบบการ Deleting Array Elements อาจจะทำต่างกันไปได้ เราจึงทำในรูปแบบเปรียบเทียบเพื่อเห็นภาพชัดขึ้นน</p>
</details>

---

## **การเทียบ <mark style ="background-color:#E7DDFF;color:#000;border-radius:5px">array - Ruby deleting Array Element</mark> แต่ละภาษา**

> <mark style ="background-color:#FFECA1;color:#000;border-radius:5px">ruby</mark> - เป็น array ประเภท <span style="border-bottom: 2px solid #FE9900;">Dynamic Array </span> เราสามารถใช้ method เฉพาะคือ `.delete(value)` สำหรับลบค่าสมาชิกในอาร์เรย์ (value) , `.delete_at(index)` ในการลบดัชนีของอาร์เรย์ (index)

> <mark style ="background-color:#FFECA1;color:#000;border-radius:5px">c</mark> - ในภาษา C เนื่องจาก Array เป็น <span style="border-bottom: 2px solid #FE9900;">Static Array</span> ซึ่งทำให้ไม่สามารถให้ method ที่จะช่วยการขยายทางสมาชิกอาร์เรย์ เราเลยแก้ปัญหาโดยการสร้าง fn ถึงมาทำงานแทน
> โดยเราจะอ้างอิงหลักการของ Dynamic Array โดยถ้าค่าในช่องอาร์เรย์เกิดเต็มจะมีการคูณ 2 เพื่อพื้นอาร์เรย์ไว้แล้วมีการ copy ค่าลงใน array และพร้อมใส่ค่าที่เพิ่มเข้ามาใหม่แทน โดยจะวิธีมีการเฉพาะที่ต่างโดยเราอ้างอิงจาก Array - Ruby ทำให้การลบหลักๆเรามี 2 รูปแบบ คือการลบตามค่าของสมาชิกใน array (value) และลบตามดัชนีของ Array (index) โดยมี method ทางภาษา C ในการทำงาน(Dynamic Array)เฉพาะมีดังนี้

| ฟังก์ชัน               | การทำงานหลัก                                                                                                        | ค่าเริ่มต้น                                                                                                                                                                         | ใช้เมื่อไหร่                                                                                                                                                                                                          |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| __malloc__             | จองหน่วยความจำตาม byte                                                                                              | ค่าไม่กำหนด (garbage)                                                                                                                                                               | เมื่อไม่สนใจค่าเริ่มต้น                                                                                                                                                                                               |
| __calloc__             | จองหน่วยความจำ + เคลียร์ค่าเป็นศูนย์                                                                                | 0                                                                                                                                                                                   | เมื่ออยากได้ array ที่เริ่มต้นเป็นศูนย์                                                                                                                                                                               |
| __realloc__            | ปรับขนาดพื้นที่ที่จองมาแล้ว                                                                                         | ข้อมูลเดิมคงอยู่, ส่วนที่เพิ่มเป็น garbage                                                                                                                                          | เมื่ออยากขยาย/ย่อ array ที่ใช้อยู่                                                                                                                                                                                    |
| __free()__             | __คืน__ บล็อกหน่วยความจำที่ถูกจองไว้กลับคืนสู่ระบบ<br>pointerที่เคยชี้ไปยังบล็อกนั้นจะกลายเป็น __dangling pointer__ | __ไม่กำหนด__ (เป็นค่าขยะ)<br>แต่ไม่สามารถเข้าถึงได้แล้ว                                                                                                                             | ใช้เมื่อไม่ต้องการใช้ข้อมูลใน Dynamic Array แล้ว เพื่อป้องกัน __Memory Leak__                                                                                                                                         |
| __fprintf__            | ใช้สำหรับเขียนข้อมูลที่ถูกจัดรูปแบบ (formatted data) ลงใน __สตรีม (stream)__ ที่ระบุ                                | -                                                                                                                                                                                   | - เมื่อต้องการพิมพ์ข้อความไปยังปลายทางที่แตกต่างจากหน้าจอปกติ เช่น การพิมพ์ข้อความแสดงข้อผิดพลาดไปยัง `stderr` เพื่อให้แยกออกจากเอาต์พุตปกติ <br>- เมื่อคุณต้องการเขียนข้อมูลที่จัดรูปแบบลงในไฟล์                     |
| __exit(EXIT_FAILURE)__ | ใช้สำหรับ __ยุติการทำงานของโปรแกรมอย่างไม่ปกติ__ และส่งค่าสถานะความล้มเหลว (failure status) กลับไปยังระบบปฏิบัติการ | __`EXIT_FAILURE`__ เป็นค่าคงที่ที่ถูกกำหนดไว้ล่วงหน้าในไลบรารี `<stdlib.h>` โดยมีค่าเป็น 1 หรือค่าอื่นที่ไม่ใช่ 0 ซึ่งเป็นมาตรฐานที่บอกให้ระบบปฏิบัติการรู้ว่าโปรแกรมทำงานไม่สำเร็จ | - เมื่อโปรแกรมพบข้อผิดพลาดร้ายแรงที่ไม่สามารถกู้คืนได้ เช่น __จองหน่วยความจำล้มเหลว__ (ซึ่งเป็นสถานการณ์ที่คุณเคยเจอในตัวอย่างก่อนหน้า) <br>- เมื่อพารามิเตอร์ที่ผู้ใช้ป้อนมาไม่ถูกต้องและโปรแกรมไม่สามารถทำงานต่อได้ |

> <mark style ="background-color:#FFECA1;color:#000;border-radius:5px">java</mark> - มี Array ที่สอดคล้องกับของ Ruby คือ <span style="border-bottom: 2px solid #FE9900;"> ArrayList </span> เพราะ List ลักษณะ Array ที่เหมือน Ruby มากที่สุด

> <mark style ="background-color:#FFECA1;color:#000;border-radius:5px">Python</mark> - มี Array ที่เป็นประเภทเดียวกับ Ruby <span style="border-bottom: 2px solid #FE9900;">"list"</span> เพราะว่าทาง list ไพธอนมีขนาดที่ยืดหดได้ แถมสามารถเก็บหลาย type อยู่ใน Array เดียวกันได้ โดยเราจะใช้ method ที่คล้ายกัน เช่น การลบขนาดค่า(value)ของอาร์เรย์ `.remove(value)` และมีการลบตามดัชนี `.pop(index)`

---

## ตัวอย่าง Deleting Array Elements 🪻

### 🪼 ลบตามค่า (value)

### 🌼 ruby (●'◡'●) - `.delete(value)`

> ในภาษา Ruby การลบสมาชิกตามค่าใน array สามารถใช้ method `.delete(value)` โดย value คือค่าที่เป็นสมาชิกในอาร์เรย์

```ruby
arr = ["red", 10 , 20 , "blue"]
arr.delete(10)#ลบค่า 10
puts arr
```

<details>
    <summary>Output</summary>
    <p> red<br>
	20<br>
	blue</p>
</details>

### 🌼 C (❁´◡`❁)

> ในภาษา C ไม่เป็น Dynamic Array จึงสร้าง Custom Dynamic Array
>
> มีการสร้าง Dynamic Array
> โดยมีการกำหนดขนาด array เบื้องต้นก่อนโดยใช้ fn : createDynamicArray(กำหนดความจุ)
> มีการเพิ่มขนาดตัว capacity ตามหลัการ fn:resizeDynamicArray(DynamicArry)
> มีการเพิ่มสมาชิก array โดย fn:addElement(DynamicArry , value)
> มีการลบข้อมูลตาม value โดย fn:removeElementAtValue(DynamicArry , value)
> มีการปริ้นข้อมูล Array โดย fn:printDynamicArray(DynamicArry)

```C
#include <stdio.h>
#include <stdlib.h>

// สร้าง struct สำหรับ Dynamic Array
typedef struct {
    int *array;
    size_t size;
    size_t capacity;
} DynamicArray;

// ฟังก์ชันสำหรับสร้าง Dynamic Array ใหม่
DynamicArray* createDynamicArray(size_t initialCapacity) {
    DynamicArray *da = (DynamicArray *)malloc(sizeof(DynamicArray));
    if (da == NULL) {
        fprintf(stderr, "Memory allocation failed.\n");
        exit(EXIT_FAILURE);
    }
    da->size = 0;
    da->capacity = initialCapacity;
    da->array = (int *)malloc(da->capacity * sizeof(int));
    if (da->array == NULL) {
        fprintf(stderr, "Memory allocation for array failed.\n");
        free(da);
        exit(EXIT_FAILURE);
    }
    return da;
}

// ฟังก์ชันสำหรับเพิ่มขนาด Dynamic Array
void resizeDynamicArray(DynamicArray *da) {
    da->capacity *= 2;
    da->array = (int *)realloc(da->array, da->capacity * sizeof(int));
    if (da->array == NULL) {
        fprintf(stderr, "Memory reallocation failed.\n");
        exit(EXIT_FAILURE);
    }
    printf("Array resized. New capacity: %zu\n", da->capacity);
}

// ฟังก์ชันสำหรับเพิ่มข้อมูลลงใน Dynamic Array
void addElement(DynamicArray *da, int value) {
    if (da->size >= da->capacity) {
        resizeDynamicArray(da);
    }
    da->array[da->size++] = value;
}


// ฟังก์ชันใหม่: ลบข้อมูลตาม value
void removeElementAtValue(DynamicArray *da, int value) {
    size_t newSize = 0;
    int foundCount = 0;

    for (size_t i = 0; i < da->size; i++) {
        if (da->array[i] != value) {
            // ถ้าค่าปัจจุบันไม่ใช่ค่าที่ต้องการลบ ให้ย้ายไปตำแหน่งใหม่
            da->array[newSize++] = da->array[i];
        } else {
            foundCount++;
        }
    }

    if (foundCount == 0) {
        printf("Element with value %d not found.\n", value);
    } else {
        da->size = newSize; // ปรับขนาดของอาร์เรย์
        printf("%d instances of value %d removed.\n", foundCount, value);
    }
}


// ฟังก์ชันสำหรับแสดงผลข้อมูลใน Dynamic Array
void printDynamicArray(DynamicArray *da) {
    printf("Array elements (size: %zu, capacity: %zu): ", da->size, da->capacity);
    for (size_t i = 0; i < da->size; i++) {
        printf("%d ", da->array[i]);
    }
    printf("\n");
}

// ฟังก์ชันสำหรับคืนหน่วยความจำที่จองไว้
void freeDynamicArray(DynamicArray *da) {
    free(da->array);
    free(da);
}

int main() {
    DynamicArray *myArray = createDynamicArray(1);

    // เพิ่มข้อมูลลงในอาร์เรย์
    addElement(myArray, 10);
    addElement(myArray, 20);
    addElement(myArray, 30);
    addElement(myArray, 40);
    addElement(myArray, 50);

    printf("--- Before removal ---\n");
    printDynamicArray(myArray); // แสดงผลก่อนลบ

    // ลบข้อมูลที่ value 50
    removeElementAtValue(myArray, 50);

    printf("--- After removal ---\n");
    printDynamicArray(myArray); // แสดงผลหลังลบ

    // เพิ่มข้อมูล 20 เข้าไปอีกครั้งเพื่อทดสอบการลบค่าซ้ำ
    addElement(myArray, 20);
    addElement(myArray, 60);

    printf("--- Before removing duplicate 20s ---\n");
    printDynamicArray(myArray);

    // ลบข้อมูลที่ value = 20 
    removeElementAtValue(myArray, 20);
    
    printf("--- After removing duplicate 20s ---\n");
    printDynamicArray(myArray);

    // คืนหน่วยความจำ
    freeDynamicArray(myArray);

    return 0;
}
```

<details>
    <summary>Output</summary>
    <p>--- Before removal ---
Array elements (size: 5, capacity: 5): 10 20 30 40 50<br>
Element at index 50 removed.<br>
--- After removal ---<br>
Array elements (size: 4, capacity: 5): 10 20 30 40<br>
</details>

### 🌼 Python ^3^ - `.remove(value)`

> ในภาษา Python การลบสมาชิกตามค่าใน array สามารถใช้ method `.remove(value)` โดย value คือค่าที่เป็นสมาชิกในอาร์เรย์

```python
arr = [10,20,30,'c' , 51]
arr.remove('c')#ลบค่า c
print(arr)
```

<details>
    <summary>Output</summary>
    <p>[10, 20, 30, 51]</p>
</details>

### 🌼 Java <3 -`remove(Object.valueOf(value))`

> ในภาษา Java การลบสมาชิกตามค่าใน array สามารถใช้ method `remove(Object.valueOf(value))` โดย value คือค่าที่เป็นสมาชิกในอาร์เรย์

```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<Object> fruitColor = new ArrayList<Object>();
        
        // เพิ่มค่า
        fruitColor.add("apple");
        fruitColor.add(30);
        fruitColor.add("grape");
        fruitColor.add("light green");
        
        // ลบข้อมูล "apple"
        fruitColor.remove("apple");
        
        // แสดงผลลัพธ์
        System.out.println(fruitColor);
    }
}
```

<details>
    <summary>Output</summary>
    <p>[30, grape, light green]</p>
</details>

## 🪼 ลบตามดัชนี (index)

### 🌼 Ruby (●'◡'●) -`.delete_at(index)`

> ในภาษา Ruby การลบสมาชิกตามดัชนีใน array สามารถใช้ method `.delete_at(index)` โดย index คือค่าที่เป็นดัชนีในอาร์เรย์

```ruby
arr = ["red", 10 , 20 , "blue"]
arr.delete_at(1)#ลบ index (1) [10]
puts arr
```

<details>
    <summary>Output</summary>
    <p> red<br>
	20<br>
	blue</p>
</details>

### 🌼 C (❁´◡`❁)

> ในภาษา C ไม่เป็น Dynamic Array จึงสร้าง Custom Dynamic Array
>
> มีการสร้าง Dynamic Array
> โดยมีการกำหนดขนาด array เบื้องต้นก่อนโดยใช้ fn : createDynamicArray(กำหนดความจุ)
> มีการเพิ่มขนาดตัว capacity ตามหลัการ fn:resizeDynamicArray(DynamicArry)
> มีการเพิ่มสมาชิก array โดย fn:addElement(DynamicArry , value)
> มีการลบข้อมูลตาม index โดย fn:removeElementAtValue(DynamicArry , index)
> มีการปริ้นข้อมูล Array โดย fn:printDynamicArray(DynamicArry)

```c
#include <stdio.h>
#include <stdlib.h>

// สร้าง struct สำหรับ Dynamic Array
typedef struct {
    int *array;
    size_t size;
    size_t capacity;
} DynamicArray;

// ฟังก์ชันสำหรับสร้าง Dynamic Array ใหม่
DynamicArray* createDynamicArray(size_t initialCapacity) {
    DynamicArray *da = (DynamicArray *)malloc(sizeof(DynamicArray));
    if (da == NULL) {
        fprintf(stderr, "Memory allocation failed.\n");
        exit(EXIT_FAILURE);
    }
    da->size = 0;
    da->capacity = initialCapacity;
    da->array = (int *)malloc(da->capacity * sizeof(int));
    if (da->array == NULL) {
        fprintf(stderr, "Memory allocation for array failed.\n");
        free(da);
        exit(EXIT_FAILURE);
    }
    return da;
}

// ฟังก์ชันสำหรับเพิ่มขนาด Dynamic Array
void resizeDynamicArray(DynamicArray *da) {
    da->capacity *= 2;
    da->array = (int *)realloc(da->array, da->capacity * sizeof(int));
    if (da->array == NULL) {
        fprintf(stderr, "Memory reallocation failed.\n");
        exit(EXIT_FAILURE);
    }
    printf("Array resized. New capacity: %zu\n", da->capacity);
}

// ฟังก์ชันสำหรับเพิ่มข้อมูลลงใน Dynamic Array
void addElement(DynamicArray *da, int value) {
    if (da->size >= da->capacity) {
        resizeDynamicArray(da);
    }
    da->array[da->size++] = value;
}


// ฟังก์ชันใหม่: ลบข้อมูลตาม Index
void removeElementAtIndex(DynamicArray *da, size_t index) {
    // ตรวจสอบ Index ว่าอยู่ในช่วงที่ถูกต้องหรือไม่
    if (index >= da->size) {
        fprintf(stderr, "Error: Index out of bounds.\n");
        return;
    }

    // วนลูปเพื่อย้ายข้อมูลที่อยู่หลัง index ที่ต้องการลบ
    // ทุกองค์ประกอบจะถูกเลื่อนมาข้างหน้าหนึ่งตำแหน่ง
    for (size_t i = index; i < da->size - 1; i++) {
        da->array[i] = da->array[i + 1];
    }

    da->size--; // ลดขนาดของอาร์เรย์ลง 1
    printf("Element at index %zu removed.\n", index);
}

// ฟังก์ชันสำหรับแสดงผลข้อมูลใน Dynamic Array
void printDynamicArray(DynamicArray *da) {
    printf("Array elements (size: %zu, capacity: %zu): ", da->size, da->capacity);
    for (size_t i = 0; i < da->size; i++) {
        printf("%d ", da->array[i]);
    }
    printf("\n");
}

// ฟังก์ชันสำหรับคืนหน่วยความจำที่จองไว้
void freeDynamicArray(DynamicArray *da) {
    free(da->array);
    free(da);
}

int main() {
    DynamicArray *myArray = createDynamicArray(1);

    // เพิ่มข้อมูลลงในอาร์เรย์
    addElement(myArray, 10);
    addElement(myArray, 20);
    addElement(myArray, 30);
    addElement(myArray, 40);
    addElement(myArray, 50);

    printf("--- Before removal ---\n");
    printDynamicArray(myArray); // แสดงผลก่อนลบ

    // ลบข้อมูลที่ index 2 (ค่า 30)
    removeElementAtIndex(myArray, 2);

    printf("--- After removal ---\n");
    printDynamicArray(myArray); // แสดงผลหลังลบ

    // คืนหน่วยความจำ
    freeDynamicArray(myArray);

    return 0;
}
```

<details>
    <summary>Output</summary>
    <p>--- Before removal ---<br>
Array elements (size: 5, capacity: 5): 10 20 30 40 50<br>
Element at index 2 removed.<br>
--- After removal ---<br>
Array elements (size: 4, capacity: 5): 10 20 40 50
</details>

### 🌼 Python ^3^ - `.pop(index)`

> ในภาษา Python การลบสมาชิกตามดัชนีใน array สามารถใช้ method `.pop(index)` โดย index คือค่าที่เป็นดัชนีในอาร์เรย์

```python
arr = [10,20,30,40,50,60]
arr.pop(2)#ลบindex(2)[30]
print(arr)
```

<details>
    <summary>Output</summary>
    <p>[10, 20, 40, 50, 60]</p>
</details>

### 🌼 Java <3 - `remove(index)

> ในภาษา Python การลบสมาชิกตามดัชนีใน array สามารถใช้ method `.remove(index)` โดย index คือค่าที่เป็นดัชนีในอาร์เรย์

```java
import java.util.ArrayList;

public class Main { 
  public static void main(String[] args) { 
    ArrayList<Object> fruitColor = new ArrayList<>();
    //เพิ่มค่า array
    fruitColor.add("apple");
    fruitColor.add(20);
    fruitColor.add("grape");
    fruitColor.add("light green");
    fruitColor.remove(0);//ลบ index (0) ["apple"]
    System.out.println(fruitColor);
  } 
}
```

<details>
    <summary>Output</summary>
    <p>[20, grape, light green]</p>
</details>

---
## Silde
- https://www.canva.com/design/DAGxt7edsjQ/chEN7GB1zZdF8zM-AtW5zA/edit?utm_content=DAGxt7edsjQ&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton
## VDO
- https://youtu.be/MSUxsl0mxac
---

# แหล่งอ้างอิง

#### Dynamic Array

- [Dynamic array | Data Structures and Algorithms Manual - ใช้หลักการ Dynamic Array ใน C -**https://calebkoy.github.io/** [ไม่พบวันที่เขียนในหน้าเว็บไซต์]สืบค้นวันที่ 1/9/2025 ](https://calebkoy.github.io/data-structures-and-algorithms-manual/data-structures/dynamic-array.html)

##### Ruby

- [[ Deleting Array Elements (ถูกอ้างอิงเป็นหัวข้อหลักในการหา method)] - __techotopia.com ถูกในวันที่เขียน__วันพฤหัสบดีที่ 27 ตุลาคม 2559** ทำการสืบค้นในวันที่ 30 /08/ 2025 ](https://www.techotopia.com/index.php/Advanced_Ruby_Arrays)
- [[Removing Items from an [Array] method delete(value), delete_at(index) ถูกใช้เป็นตัวอย่างหลักการเขียนเพื่อเชื่อมมั่นได้ + หลักการของ method - __Class: Array (Ruby 3.0.1)__ เขียน ณ วันที่ 22 มีมาคม 2021 สอบค้นในวันที่ 30/8/2025](https://ruby-doc.org/core-3.0.1/Array.html)

##### C

- [Dynamic memory management [method ที่ใช้ใน Dynamic โดยมีการอธิบายความหมาย method ที่ชัดเจน ] - **cppreference.com ** ถูกแก้ไขล่าสุดเมื่อ วันที่ 18 กันยายน 2022 เวลา 10:41 สอบค้นในวันที่ 30/8/2025](https://en.cppreference.com/w/c/memory.html)
- [[malloc - c ( Dynamic memory management ถูกใช้ในหลักการเขียนเพื่อประยุกต์ในรูปแบบ <span style="border-bottom: 2px solid #FE9900;">Dynamic Array </span> ยังไง ) ]- **cppreference.com **(ถูกแก้ไขล่าสุดเมื่อ วันที่ 18 กันยายน 2022 เวลา 10:41) สอบค้นวันที่ 30/8/2025 ](https://en.cppreference.com/w/c/memory/malloc?utm_source=chatgpt.com)
- [[calloc - c ( Dynamic memory management) ถูกใช้ในหลักการเขียนเพื่อประยุกต์ในรูปแบบ <span style="border-bottom: 2px solid #FE9900;">Dynamic Array </span> ยังไง]- **cppreference.com **(ถูกแก้ไขล่าสุดเมื่อ **วันที่ 18 กันยายน 2022 เวลา 10:41) สอบค้นวันที่ 30/8/2025 ](https://en.cppreference.com/w/c/memory/calloc.html)
- [[realloc - c ( Dynamic memory management) ถูกใช้ในหลักการเขียนเพื่อประยุกต์ในรูปแบบ <span style="border-bottom: 2px solid #FE9900;">Dynamic Array </span> ยังไง] - **cppreference.com ** (ถูกแก้ไขล่าสุดเมื่อ วันที่ 18 กันยายน 2022 เวลา 10:41) สอบค้นวันที่ 30/8/2025 ](https://en.cppreference.com/w/c/memory/realloc.html)
- [c_lib/c/Kernighan, Ritchie - The C Programming Language อธิบายหลักการ method + library -> ไม่วันที่แน่ชัด วันที่สืบค้น 31/8/2025](https://github.com/media-lib/c_lib/blob/master/c/Kernighan%2C%20Ritchie%20-%20The%20C%20Programming%20Language%2C%202nd%20edition.pdf)

##### python

- [Python Remove Array Item ถูกใช้เป็นตัวหลักการคิดในการใช้ - GeeksforGeeks ไม่ถูกพบเวลาเขียนในหน้าเว็บ](https://www.geeksforgeeks.org/python/python-remove-array-item/)
- [python library method array (หา method ที่ใช้ในการลบอาร์เรย์ แถมมีการอธิบายว่าแต่ละ method แถมอธิบาย method ว่ามีหน้าที่อะไร )- **docs.python.org**(วันที่มีการแก้ไขล่าสุด 29 สิงหาคม 2025 ) วันที่สืบค้น 30/8/2025 ](https://docs.python.org/3/library/array.html)

##### java

- [ArrayList-methond + หลักการของ remove ของ java (Java Platform SE 8 ) - **docs.oracle.com** ไม่พบข้อมูลที่เขียนหรืออัปเดตล่าสุดและถูกสืบค้นในวันที่30/8/2025](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html)
- [ตัวอย่างการใช้  method ->Java ArrayList remove() Method - __w3schools.com__ ไม่พบวันเวลาที่ถูกเขียน + เวลาที่อัปเดตเว้บไซต์ล่าสุด และมีการถูกสืบค้นในวันที่ 30/8/2025 ](https://www.w3schools.com/java/ref_arraylist_remove.asp)

