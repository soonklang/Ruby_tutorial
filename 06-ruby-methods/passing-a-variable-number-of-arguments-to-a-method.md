# Passing a Variable Number of Arguments to a Method
เป็นวิธีที่ Ruby ใช้ในการแก้ปัญหาในตอนที่เราไม่รู้ว่าจะรับ argument เข้ามาทั้งหมดกี่ตัว ด้วยการใช้ * นำหน้าชื่อ argument ในตอนที่เราสร้าง method จะทำให้ method ที่ถูกประกาศสามารถรับค่า argument ได้แบบไม่จำกัดจำนวน และ argument ที่รับเข้ามาจะถูกเก็บไวใน array เพื่อเข้าถึงและใช้งานต่อไปใน method นั้นๆ
### ตัวอย่าง 1 (Ruby)

    def method(*arguments)
    p arguments
    end
    
    method(1)
    method(1, 2, 3)
    method(true, false, 5, 1.23)
    method("PHP", "Ruby", "Python", "Java")
    
### ผลลัพธ์

    [1]
    [1, 2, 3]
    [true, false, 5, 1.23]
    ["PHP", "Ruby", "Python", "Java"]

### คำอธิบาย
จากตัวอย่างที่ 1 จะเห็นว่าในภาษา Ruby เมื่อใส่ * ไปที่หน้าชื่อ argument ใน method ที่ประกาศไว้จะสามารถทำให้รับค่า argument ที่ส่งมาได้จำนวนกี่ค่าก็ได้แล้วนำจำนวนเหล่านั้นไปเก็บไว้ในรูปแบบของ array แล้วไล่แสดงผลข้อมูลใน array ที่ละช่อง

### ตัวอย่าง 2 (Python)

     def sum_all(*args):
         result = 0
         for num in args:
             result += num
             return result
    print(sum_all(1, 2, 3, 4, 5))

### ผลลัพธ์

    15

### คำอธิบาย
จากตัวอย่างที่ 2 จะเห็นได้ว่าใน Python มีการใช้ * นำหน้าชื่อ argument เหมือนกันกับ Ruby จึงทำให้ function sum_all สามารถรับค่า argument กี่จำนวนก็ได้เช่นเดียวกัน แต่ในภาษา Python จะนำ argument ที่รับมาไปเก็บในรูปแบบ tuple แล้วบวกค่า argument ทุกตัวที่อยู่ใน tuple แล้วนำค่าที่ได้ไปเก็บที่ result แล้วนำมาแสดงผล

### ตัวอย่าง 3 (๋Java)

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

### ผลลัพธ์

    geek1 geek2 
    geek1 geek2 geek3

### คำอธิบาย
จากตัวอย่างที่ 3 จะเห็นว่าใน Java จะใช้เครื่องหมาย ... (ellipsis)ต่อท้ายชนิดข้อมูลใน method Names และทำให้ Method Names สามารถรับค่า argument หรือ parameter ได้ไม่จำกัดเหมือนกันและนำไปเก็บในรุปแบบของ array แล้วค่อยๆนำผลลัพธ์ออกมาแสดงที่ละช่องๆ

### ตัวอย่าง 4 (๋C)

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

### ผลลัพธ์

    1 2 3 
    1 2 3 4 5

### คำอธิบาย
จากตัวอย่างที่ 4 ในภาษา C จะใช้ Variadic function ซึ่งจะช่วยทำให้ function สามารถรับ argrument ได้ไม่จำกัด แต่ในภาษา C จะมีข้อแต่งต่างจากภาษา Ruby Python และ Java ตรงที่ใน function จะต้องกำหนด argument ไว้อย่างน้อย 1 ตัวและหลังจากนั้นจะส่ง argument มาเพิ่มกี่ตัวก็ได้แล้วก็นำมาเก็บใน list จากนั้นก็จะวนลูปนำข้อมูลในลิสต์ออกมาแสดงทีละตัว

## สรุปข้อแต่งต่าง

1 ภาษา Ruby ใช้ * นำหน้าชื่อ argument เหมือนกัน ต่างกันตรงที่นำไปใช้ใน method กับ function และในส่วนของการเก็บ argument Ruby จะเอาไปเก็บใน array ส่วน Python เอาไปเก็บใน tuple แล้วค่อยเข้าถึงค่าที่อยู่ด้านในแล้วนำออกมาใช้
2.ภาษา Java ต่างกับ ภาษา Ruby ตรงที่ Java ใช้ ...(ellipsis) Ruby ใช้ *args ที่เหลือจะเหมือนกันทั้งหมด
3.ภาษา C จะมีความแตกต่างกับทุกภาษาเลยทั้ง Ruby Python และ Java เพราะมีการใช้ทั้ง variadic function การเก็บ argument ในรูปแบบ list และการการที่ต้องกำหนดค่าในฟังก์ชันไว้อย่างน้อย 1 ตัวเพื่อที่จะสามารถรับ argument อื่นๆเพิ่มได้


## อ้างอิง
#### https://marcuscode.com/lang/ruby/methods 
ใช้ในการอ้างอิงตัวอย่างที่ 1 (Ruby),ใช้เปรียบเทียบความแตกต่างด้วย *args
#### https://www.geeksforgeeks.org/python/variable-length-argument-in-python/
ใช้ในการอ้างอิงตัวอย่างที่ 2 (Python),ใช้เปรียบเทียบความแตกต่างด้วย *args
#### https://www.geeksforgeeks.org/java/variable-arguments-varargs-in-java/
ใช้ในการอ้างอิงตัวอย่างที่ 3 (Java),ใช้เปรียบเทียบความแตกต่างด้วย Varargs, ...(ellipsis)
#### https://www.geeksforgeeks.org/c/variadic-functions-in-c/
ใช้ในการอ้างอิงตัวอย่างที่ 4 (C),ใช้เปรียบเทียบความแตกต่างด้วย variadic function
