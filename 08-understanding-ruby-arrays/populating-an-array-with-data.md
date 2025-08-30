# Populating an Array with Data
คือ การนำข้อมูลมาใส่ใน array ที่สร้าง หรือ มีอยู่เเล้ว สามารถเติมข้อมูลใน array หรือ แก้ไขได้ ได้ เช่น push,,manual,loop,input,file 
เราจําเป็นต้องเพิ่มข้อมูลบางส่วนลงไป เก็บหลายชนิดพร้อมกันได้ Ruby ใช้ dynamic array (list) ไม่จำเป็นต้องกำหนดขนาดล่วงหน้า ขยายได้อัตโนมัติ

# ตัวอย่างการใช้งาน (Initialization)
> Ruby
```ruby
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hi", 3.14, true]  # เก็บหลายชนิดพร้อมกันได้
```
>Java
```java
int[] numbers = {1, 2, 3, 4, 5};
```
>C
```c
int numbers[] = {1, 2, 3, 4, 5};
```
>Python
```python
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hi", 3.14, True]
```

# ตัวอย่าง code array ที่แก้ไขข้อมูล
```ruby
days_of_week = Array.new(7, "today")
=> ["today", "today", "today", "today", "today", "today", "today"]


days_of_week = Array[ "Mon", "Tues", "Wed", "Thu", "Fri", "Sat", "Sun" ]
=> ["Mon", "Tues", "Wed", "Thu", "Fri", "Sat", "Sun"]
```
# เติมข้อมูลแบบกำหนดเองในภาษา Ruby
>Ruby
```ruby
arr = []
arr << 10
arr.push(20)
arr[2] = 30
puts arr.inspect   # => [10, 20, 30]
```
# เติมข้อมูลแบบกำหนดเองในภาษา Java/C/Python
>Java
```java
int[] arr = new int[3];
arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
```
>Java ใช้ static array (ต้องกำหนดขนาดตอนสร้าง) และข้อมูลต้องเป็นชนิดเดียวกัน ถ้าต้องการ dynamic ต้องใช้ ArrayList

>C
```c
#include <stdio.h>

int main() {
    int arr[3];
    arr[0] = 10;
    arr[1] = 20;
    arr[2] = 30;
    return 0;
}
```
>C ก็เป็น static array ไม่สามารถขยายขนาด array ได้ ต้องใช้ pointer + malloc/free แทน

>Python
```python
arr = []
arr.append(10)
arr.append(20)
arr[2:3] = [30]
print(arr)  # [10, 20, 30]
```
# การเติมข้อมูลด้วย loop ในภาษา Ruby
>Ruby
```ruby
numbers = []
(1..5).each { |i| numbers << i * 2 }
puts numbers.inspect   # => [2, 4, 6, 8, 10]
```
# การเติมข้อมูลด้วย loop ในภาษา Java/C/Python
>Java
```java
int[] arr = new int[3];
arr[0] = 10;
arr[1] = 20;
arr[2] = 30;

// ใช้ loop
for (int i = 0; i < arr.length; i++) {
    arr[i] = i * 2;
}
```
>C
```c
#include <stdio.h>

int main() {
    int arr[3];
    arr[0] = 10;
    arr[1] = 20;
    arr[2] = 30;

    for (int i = 0; i < 3; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
```
>Python
```python
numbers = [i * 2 for i in range(5)]
print(numbers)  # [0, 2, 4, 6, 8]
```
# การรับค่าจากผู้ใช้ในภาษา Ruby
>Ruby
```ruby
arr = []
3.times do
  print "Enter number: "
  arr << gets.chomp.to_i
end
puts arr.inspect
```
# การรับค่าจากผู้ใช้ในภาษา Java/C/Python
>Java
```java
import java.util.Scanner;
public class Main {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int[] arr = new int[3];
    for (int i = 0; i < arr.length; i++) {
      System.out.print("Enter number: ");
      arr[i] = sc.nextInt();
    }
  }
}
```
>C
```c
#include <stdio.h>
int main() {
    int arr[3];
    for (int i = 0; i < 3; i++) {
        printf("Enter number: ");
        scanf("%d", &arr[i]);
    }
    return 0;
}
```
>Python
```python
arr = []
for i in range(3):
    num = int(input("Enter number: "))
    arr.append(num)
print(arr)
```
# การอ่านค่าจากไฟล์ในภาษา Ruby
>Ruby
```ruby
arr = []
File.foreach("data.txt") { |line| arr << line.to_i }
puts arr.inspect
```
# การอ่านค่าจากไฟล์ในภาษา Java/C/Python
>Java
```java
import java.io.*;
import java.util.*;
public class Main {
  public static void main(String[] args) throws Exception {
    Scanner sc = new Scanner(new File("data.txt"));
    List<Integer> arr = new ArrayList<>();
    while (sc.hasNextInt()) {
        arr.add(sc.nextInt());
    }
    System.out.println(arr);
  }
}
```
>Java ยาวกว่า ต้องใช้ Scanner/BufferedReader

>C
```c
#include <stdio.h>
int main() {
    FILE *f = fopen("data.txt", "r");
    int arr[100], i = 0;
    while (fscanf(f, "%d", &arr[i]) == 1) {
        i++;
    }
    fclose(f);
    return 0;
}

```
>C ซับซ้อน ต้องใช้ fscanf

>Python
```python
with open("data.txt") as f:
    arr = [int(line) for line in f]
print(arr)
```
# การหาความยาวของ Array ใน Ruby
>Ruby
```ruby
arr = [1, 2, 3, 4, 5]

puts arr.length   # => 5
puts arr.size     # => 5
puts arr.count    # => 5
```
# การหาความยาวของ Array ใน Java/C/Python
>Java
```java
int[] arr = {1, 2, 3, 4, 5};
System.out.println(arr.length);  // 5

```
>C
```c
#include <stdio.h>

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int length = sizeof(arr) / sizeof(arr[0]);
    printf("%d\n", length);  // 5
    return 0;
}
```
>C Static array → ไม่มี property length, ต้องใช้ sizeof แปลงเป็นจำนวน element

>Python
```python
arr = [1, 2, 3, 4, 5]

print(len(arr))  # 5

```
# การหาว่า Array ว่างมั้ยใน Ruby
>Ruby
```ruby
arr = []
if arr.empty?
  puts "Array ว่าง"
else
  puts "Array มีข้อมูล"
end
# Output: Array ว่าง
```
# การหาว่า Array ว่างมั้ยใน Java/C/Python
>Java
```java
int[] arr = {};
if(arr.length == 0){
    System.out.println("Array ว่าง");
}
```
```java
import java.util.ArrayList;

ArrayList<Integer> list = new ArrayList<>();
if(list.isEmpty()){
    System.out.println("ArrayList ว่าง");
}

```
>C
ไม่มี method, ต้องตรวจสอบด้วยความยาว

>Python
```python
arr = []
if len(arr) == 0:
    print("Array ว่าง")
else:
    print("Array มีข้อมูล")
# Output: Array ว่าง
```
# แหล่งอ้างอิง:
*<https://www.rubyguides.com/2015/05/ruby-arrays/?utm_>*
*<https://www.tutorialspoint.com/ruby/ruby_arrays.htm?utm_>*
*<https://www.geeksforgeeks.org/ruby-arrays/?utm_>*
*<https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html?utm_>*
*<https://www.geeksforgeeks.org/arrays-in-c-cpp/?utm_>*
*<https://www.tutorialspoint.com/cprogramming/c_arrays.htm?utm_>*
*<https://www.w3schools.com/python/python_arrays.asp>*

# Presentation
