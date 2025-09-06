# Passing a Variable Number of Arguments to a Method
การส่งจำนวน (argument) ที่ไม่แน่นอนไปยัง method โดยในภาษา Ruby สามารถใช้ * นำหน้าหน้าชื่อ (parameter) ใน method เพื่อให้สามารถรับ argument ที่ส่งเข้ามากี่จำนวนก็ได้ โดย argument ที่รับเข้ามาจะถูกนำไปเก็บใน array ซึ่งจะสามารถเข้าถึงและใช้งานได้ใน method
### ตัวอย่างที่ 1 (Ruby)
```Ruby
def method(*arguments)
    p arguments
end

method(1)
method(1, 2, 3)
method(true, false, 5, 1.23)
method("PHP", "Ruby", "Python", "Java")
```    
### ผลลัพธ์
```Ruby
[1]
[1, 2, 3]
[true, false, 5, 1.23]
["PHP", "Ruby", "Python", "Java"]
```
### คำอธิบาย
จากตัวอย่างที่ 1 จะเห็นว่าภาษา Ruby มี method ที่ใช้ (*arguments) จึงสามารถรับค่า argument ที่ส่งมาในจำนวนที่ไม่แน่นอนได้ไม่ว่าจะส่งมากี่ตัวก็ตาม จากนั้นจะนำ argument ที่รับเข้ามาไปเก็บใน array แล้วจึงนำออกมาแสดงผล
##
## การเปรียบเทียบกับภาษาอื่นๆ
### ตัวอย่าง 1 (Python)
```Python
def sum_all(*args):
    result = 0
    for num in args:
        result += num
        return result
print(sum_all(1, 2, 3, 4, 5))
```
### ผลลัพธ์
```Python
15
```
### คำอธิบาย
จากตัวอย่างที่ 1 จะเห็นได้ว่าในภาษา Python มีการใช้ * นำหน้าชื่อ parameter ใน method เหมือนกันกับในภาษา Ruby จึงทำให้ function sum_all สามารถรับค่า argument กี่จำนวนก็ได้เช่นเดียวกัน แต่ในภาษา Python จะนำ argument ที่รับมาไปเก็บในรูปแบบ tuple แล้วบวกค่า argument ทุกตัวที่อยู่ใน tuple แล้วนำค่าที่ได้ไปเก็บที่ตัวแปร result แล้วจึงนำมาแสดงผล
##
### ตัวอย่าง 2 (๋Java)
```java
import java.io.*;
class Geeks {
public static void Names(String... n) {
    for (String i : n) {
        System.out.print(i + " "); 
    }
    System.out.println(); 
}

public static void main(String[] args) {
    Names("geek1", "geek2");           
    Names("geek1", "geek2", "geek3");   
}
}
```
### ผลลัพธ์
```java
geek1 geek2 
geek1 geek2 geek3
```
### คำอธิบาย
จากตัวอย่างที่ 2 จะเห็นว่าในภาษา Java จะใช้ ... หรือเรียกว่า ellipsis ต่อท้ายชนิดข้อมูลใน method และทำให้ method สามารถรับค่า argument ได้ไม่จำกัดเหมือนกันและนำ argument ไปเก็บใน array แล้วจึงนำผลลัพธ์ออกมาแสดงผล
##
### ตัวอย่าง 3 (๋C)
```C
#include <stdio.h>
#include <stdarg.h>

void print(int n, ...) {
    va_list args;
    va_start(args, n);  
    for (int i = 0; i < n; i++) 
        printf("%d ", va_arg(args, int));
    printf("\n");
    va_end(args);
}

int main() {

print(3, 1, 2, 3);
print(5, 1, 2, 3, 4, 5);
return 0;
}
```
### ผลลัพธ์
```C
1 2 3 
1 2 3 4 5
```
### คำอธิบาย
จากตัวอย่างที่ 3 ในภาษา C จะใช้ Variadic function ซึ่งจะช่วยทำให้ function สามารถรับ argrument ได้ไม่จำกัด แต่ในภาษา C จะมีข้อแต่งต่างจากภาษา Ruby Python และ Java ตรงที่ใน function จะต้องกำหนด argument ไว้อย่างน้อย 1 ตัวและหลังจากนั้นจะส่ง argument มาเพิ่มกี่ตัวก็ได้แล้วก็นำมาเก็บใน list จากนั้นก็จะวนลูปนำข้อมูลในลิสต์ออกมาแสดงผล
##
## ตารางเปรียบเทียบ
| ภาษา | วิธีส่งค่า argument แบบไม่จำกัดจำนวน | การกำหนด argument ไว้ก่อน| การเก็บค่า argument ที่รับมา  |
|------|--------------------------------|-----------------------------|---------------------------|
|`Ruby`|`ใช้ * นำหน้า parameter ใน method`|`ไม่ต้องกำหนด argument`|`array`|
|`Python`|`ใช้ * นำหน้า parameter ใน method`|`ไม่ต้องกำหนด argument`|`tuple`|
|`Java`|`ใช้ ... หรือเรียกว่า ellipsis ต่อท้ายชนิดข้อมูลใน method`|`ไม่ต้องกำหนด argument`|`array`|
|`C`|`ใช้ Variadic function`|`ต้องกำหนด argument ไว้ก่อนอย่างน้อย 1 ตัว`|`list`|
##
## อ้างอิง
#### https://marcuscode.com/lang/ruby/methods 
ใช้ในการอ้างอิงตัวอย่างที่ 1 (Ruby),ใช้เปรียบเทียบความแตกต่างด้วย *args
#### https://www.geeksforgeeks.org/python/variable-length-argument-in-python/
ใช้ในการอ้างอิงตัวอย่างที่ 2 (Python),ใช้เปรียบเทียบความแตกต่างด้วย *args
#### https://www.geeksforgeeks.org/java/variable-arguments-varargs-in-java/
ใช้ในการอ้างอิงตัวอย่างที่ 3 (Java),ใช้เปรียบเทียบความแตกต่างด้วย Varargs, ...(ellipsis)
#### https://www.geeksforgeeks.org/c/variadic-functions-in-c/
ใช้ในการอ้างอิงตัวอย่างที่ 4 (C),ใช้เปรียบเทียบความแตกต่างด้วย variadic function
