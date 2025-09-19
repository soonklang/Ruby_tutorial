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
จากตัวอย่างที่ 1 จะเห็นได้ว่าในภาษา Python มีการใช้ * นำหน้าชื่อตัวแปร argument ใน method เหมือนกันกับในภาษา Ruby จึงทำให้ function sum_all สามารถรับค่า argument กี่จำนวนก็ได้เช่นเดียวกัน แต่ในภาษา Python จะนำ argument ที่รับมาไปเก็บในรูปแบบ tuple แล้วบวกค่า argument ทุกตัวที่อยู่ใน tuple แล้วนำค่าที่ได้ไปเก็บที่ตัวแปร result แล้วจึงนำมาแสดงผล
##
### ตัวอย่าง 2 (๋Java)
```java
public class Motorcycle {
    private String make;
    private String model;
    private String color;
    private int weight;
    private boolean statusNew;
    private int year;
    private String features = "";

    public Motorcycle(String make, String model, String color, int weight, boolean statusNew, int year) {
        this.make = make;
        this.model = model;
        this.color = color;
        this.weight = weight;
        this.statusNew = statusNew;
        this.year = year;
    }

    public String getFeatures() {
        return features;
    }

    public void setFeatures(String features) {
        this.features = features;
    }

    public void addMotorcycleFeatures(String... features) {
        StringBuilder str = new StringBuilder(this.getFeatures());
        for (String feature : features) {
            if (str.length() != 0) {   // แก้จาก str.isEmpty() -> str.length() != 0
                str.append(", ");
            }
            str.append(feature);
        }
        this.setFeatures(str.toString());
    }

    public static void main(String[] args) {
        Motorcycle motorcycle = new Motorcycle("Ducati", "Monster", "red", 350, true, 2023);

        motorcycle.addMotorcycleFeatures("abs");
        motorcycle.addMotorcycleFeatures("navi", "charger");
        motorcycle.addMotorcycleFeatures("wifi", "phone", "satellite");

        System.out.println(motorcycle.getFeatures());
    }
}
```
### ผลลัพธ์
```java
abs, navi, charger, wifi, phone, satellite
```
### คำอธิบาย
จากตัวอย่างที่ 2 จะเห็นว่าในภาษา Java จะใช้วิธีแบบ Varargs หรือก็คือการใช้ ... ต่อท้ายชนิดข้อมูลใน method และทำให้ method สามารถรับค่า argument ได้ไม่จำกัดเหมือนกัน (วิธีนี้จะสามารถส่งชนิดข้อมูล argument ได้ชนิดเดียวเท่านั้นไม่สามารถส่งข้อมูลหลายๆชนิดได้) จากนั้นจะนำ argument ไปเก็บใน array แล้วจึงนำผลลัพธ์ออกมาแสดงผล
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
จากตัวอย่างที่ 3 ในภาษา C จะใช้วิธีแบบ Variadic ซึ่งจะช่วยทำให้ function สามารถรับ argrument ได้ไม่จำกัด แต่ในภาษา C จะมีข้อแต่งต่างจากภาษา Ruby Python และ Java ตรงที่ใน function จะต้องกำหนดตัวแปร argument ไว้อย่างน้อย 1 ตัวและหลังจากนั้นจะส่ง argument มาเพิ่มกี่ตัวก็ได้แล้วก็นำมาเก็บใน list จากนั้นก็จะวนลูปนำข้อมูลในลิสต์ออกมาแสดงผล
##
## ตารางเปรียบเทียบ
| ภาษา | วิธีส่งค่า argument แบบไม่จำกัดจำนวน |การจำกัดชนิดข้อมูล argument | การกำหนด argument ไว้ก่อน| การเก็บค่า argument ที่รับมา  |
|------|--------------------------------|-----------------------------|-----------------------------|---------------------------|
|Ruby|`ใช้ (*argrument) `|ไม่จำกัดชนิดข้อมูล argument|`ไม่ต้องกำหนด argument`|`array`|
|Python|`ใช้ (*argrument) `|ไม่จำกัดชนิดข้อมูล argument|`ไม่ต้องกำหนด argument`|`tuple`|
|Java|`ใช้ Varargs (String...argument) `|ส่ง argument ได้แค่ชนิดเดียว|`ไม่ต้องกำหนด argument`|`array`|
|C|`ใช้ Variadic (int n, ...)`|ไม่จำกัดชนิดข้อมูล argument|`ต้องกำหนดตัวแปร argument ไว้ก่อนอย่างน้อย 1 ตัว`|`list`|
##
## วิดิโอนำเสนอ
https://drive.google.com/file/d/1VAYlAhozhO-rDPElEoJz97NfPuxgOa7q/view?usp=drive_link
## สไลด์นำเสนอ
https://drive.google.com/file/d/1V8ykFP21DvU299uM4sjdK1VE4lh8fC3g/view?usp=drive_link
##

## อ้างอิง
- MarcusCode. (2025, September 6). Methods in Ruby. MarcusCode. สืบค้นจาก https://marcuscode.com/lang/ruby/methods  
  - ใช้อ้างอิงตัวอย่างที่ 1 (Ruby),ใช้เปรียบเทียบความแตกต่างกับภาษา Python/Java/C
- GeeksforGeeks. (2025, July 23). Python variable-length arguments (variable-length argument in Python). GeeksforGeeks. สืบค้นจาก https://www.geeksforgeeks.org/python/variable-length-argument-in-python/  
  - ใช้อ้างอิงการเปรียบเทียบในตัวอย่าง 1 (Python),ใช้เปรียบเทียบความแตกต่างด้วย *args กับภาษา Ruby และภาษาอื่นๆ
- Cardos, B. (2023, April 27). Java – best practices for many parameters in a method. ใน L. J. Peris (ผู้ตรวจทาน), Baeldung. สืบค้นจาก https://www.baeldung.com/java-best-practices-many-parameters-method  
  - ใช้อ้างอิงการเปรียบเทียบในตัวอย่าง 2 (Java),ใช้เปรียบเทียบความแตกต่างด้วย Varargs หรือ ...(ellipsis)กับภาษา Ruby และภาษาอื่นๆ
- GeeksforGeeks. (2025, March 7). Variadic functions in C. สืบค้นจาก https://www.geeksforgeeks.org/c/variadic-functions-in-c/  
  - ใช้อ้างอิงการเปรียบเทียบในตัวอย่าง 3 (C),ใช้เปรียบเทียบความแตกต่างด้วย variadic กับภาษา Ruby และภาษาอื่นๆ
