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
- ในภาษา C array ไม่สามารถ push หรือ pop ได้เหมือน Ruby
- โดยทั่วไปจะสร้าง ฟังก์ชัน push/pop ขึ้นมาเอง

```c
#include <stdio.h>
#define MAX_SIZE 100

int stack[MAX_SIZE];
int top = 0;

void push(int value) {
    if (top >= MAX_SIZE - 1) {
        printf("Stack overflow\n");
        return;
    }
    stack[++top] = value;
}

int pop() {
    if (top <= 0) {
        printf("Stack underflow\n");
        return -1;
    }
    return stack[top--];
}

void main(){
    push(5);
    push(10);
    push(20);

    printf("all value in stack: ");
    for(int i=1; i<=top; i++){
        printf("%d ", stack[i]);
    }
    printf("\n");

    int poppedValue = pop();

    printf("pop value: %d\n", poppedValue);
    printf("all value in stack after pop: ");
    for(int i=1; i<=top; i++){
        printf("%d ", stack[i]);
    }
    printf("\n");
}
```
<details close>
   <summary><b>Output</b></summary>
 <pre>all value in stack: 5 10 20 
pop value: 20
all value in stack after pop: 5 10 
 </pre>
</details>

### ภาษา Java
- ในภาษา java ไม่มี push หรือ pop ใน array ธรรมดา
- ต้องใช้ libary ตัวหนึ่งชื่อว่า Stack (java.util) หริอจะใข้ Arraylist (java.util) + add(), remove() ก็ได้
- สร้างตัวแปรจาก class stack
```java
import java.util.Stack;
public class pushandpop {
  public static void main(String[] args) {
    Stack<Integer> stack = new Stack<>();
    System.out.println(stack);

    stack.push(5);
    stack.push(10);
    stack.push(15);
    System.out.println(stack);

    int poppedValue = stack.pop();
    System.out.println("Popped value: " + poppedValue);
    System.out.println(stack);
  }
}
```
<details close>
   <summary><b>Output</b></summary>
 <pre>[]
[5, 10, 15]
Popped value: 15
[5, 10]]
 </pre>
</details>

### ภาษา Python
ในภาษา Python ใช้ list เป็น dynamic array ซึ่งมีเมธอดที่ใช้งานได้คล้ายกันอยู่ คือ append() กับ pop()
```python
stack = []
# push
stack.append(10)
stack.append(20)
stack.append(30)

print(stack)

# pop
poppedValue = stack.pop()
print("Pop:", poppedValue)

print(stack)                    
```
<details close>
   <summary><b>Output</b></summary>
 <pre>[10, 20, 30]
Pop: 30
[10, 20]
 </pre>
</details>

# สรุป

| Language | Structure Used | Push (เพิ่มข้อมูล) | Pop (นำข้อมูลออก) | Notes |
|----------|----------------|---------------------|--------------------|-------|
| **Ruby** | `Array` (dynamic array) | `array.push(value)` หรือ `array << value` | `array.pop` | ใช้ง่าย มีเมธอดตรง ๆ |
| **C**    | Array (manual implementation) | `stack[++top] = value;` | `value = stack[top--];` | ต้องเขียนโค้ดจัดการเอง (overflow/underflow) |
| **Java** | `Stack<E>` (`java.util`) | `stack.push(value)` | `stack.pop()` | เป็นคลาสสำเร็จรูป ใช้งานง่าย แต่ปัจจุบันนิยม `ArrayList` + `add/remove` มากกว่า |
| **Python** | `list` (dynamic array) | `list.append(value)` | `list.pop()` | `pop(index)` ได้ด้วย เช่น `pop(0)` |

# Reference
- [ push และ pop ของ ruby ] https://www.techotopia.com/index.php/Advanced_Ruby_Arrays
- [ push และ pop ของ ruby ] https://www.studytonight.com/ruby/push-and-pop-in-ruby
- [ push และ pop ของ ruby ] https://ruby-doc.org/core-2.7.2/Array.html#method-i-push
- [ ภาษา C stack ] https://www.geeksforgeeks.org/c/implement-stack-in-c/
- [ ภาษา C stack ] https://www.digitalocean.com/community/tutorials/stack-in-c
- [ ภาษา java libary Stack] https://docs.oracle.com/javase/8/docs/api/java/util/Stack.html
- [ ภาษา java libary ArrayList] https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html
- [ ภาษา python list] https://docs.python.org/3/tutorial/datastructures.html

# *Slide*
[Pushing and Popping Array Elements](https://github.com/user-attachments/files/22563022/PushingAndPoping.pdf)


# *Video Presentation*
[Video](https://youtu.be/Okpl21xvU2k)
