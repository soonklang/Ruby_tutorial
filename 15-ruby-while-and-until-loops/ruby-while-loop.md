# Ruby While Loop

**ความหมาย และหลักการทำงาน**

> While Loop เป็นcontrol expression ที่ควบคุมการทำซ้ำ โดยจะตรวจสอบเงื่อนไขทุกครั้งก่อนทำคำสั่งในบล็อก while loop ถ้าเงื่อนไขเป็นจริงจะทำคำสั่งลูป แต่ถ้าเป็นเท็จจะออกจากลูป

**Flow Chart**

![Image](https://github.com/user-attachments/assets/d1cd0950-c875-4667-bc9e-2a00c5aa98c1)

**Syntax**
``` ruby
while conditional_expression[do]
 # code to be executed
end
```

>* while ต้องมี end ปิดเสมอ
>* conditional expression(เงื่อนไข) : มีค่าเป็นจริง(true) หรือเท็จ(false)
>
>   ตัวอย่างค่า conditional expression เช่น true, false , 1<2 , nil(ในการเช็คเงื่อนไขจะถูกพิจารณาเป็นfalse) เป็นต้น
>* do จะเขียนหรือไม่เขียนก็ได้

nil คือค่าในหลายภาษาโปรแกรมที่ใช้แสดงว่า “ไม่มีค่า” หรือ “ไม่ได้กำหนดค่า” เช่นเดียวกับ null ใน java ,NULL ใน C,C++,nil ใน Go

ใน Ruby nil เป็นอ็อบเจ็กต์หนึ่งของคลาส NilClass และใช้สื่อถึงความว่างเปล่าหรือไม่มีข้อมูลในตัวแปรนั้น

```ruby
puts nil == false     # false   (nil ไม่เท่ากับ false)
```
>ดังนั้น nil ไม่ได้มีค่าเป็น false แค่ถูกพิจารณาให้เป็น false ตอนเช็คเงื่อนไข

**ข้อดี:เหมาะกับงานทำซ้ำที่ไม่ทราบจำนวนรอบที่แน่นอน**

**ข้อควรระวัง:การเกิดลูปไม่รู้จบ(infinite loop)**

**วิธีแก้**
* เพิ่มตัวแปรนับรอบลูป
``` ruby
i = 0 
while i < 10
  puts i
  i += 1  # i=i+1 
end
``` 
* ใช้คำสั่ง break
``` ruby
while true
  puts "Enter number (0 to stop):"
  input = gets.to_i
  break if input == 0
end
``` 
> gets ใช้รับ input จากคีย์บอร์ด , to_i ใช้แปลง string เป็น integer 

### การเปรียบเทียบแต่ละภาษา(Ruby,Python,Java,C)

**Ruby**
``` Ruby
i = 1
while i <= 5
  puts "The number is: #{i}"
  i += 1
end 
puts "Loop finished."
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>The number is: 1
The number is: 2
The number is: 3
The number is: 4
The number is: 5
Loop finished.</code></pre>
</details>

**Python**
``` Python
i = 1
while i <= 5:
    print(f"The number is: {i}")
    i += 1
print("Loop finished.")
```
> สิ่งที่ต่างจากRubyคือ
>* การใช้เครื่องหมาย : ต่อท้ายเงื่อนไขของ while

**Java**
``` Java
public class WhileLoopExample {
    public static void main(String[] args) {
        int i = 1;
        while (i <= 5) {
            System.out.println("The number is: " + i);
            i++;
        }
        System.out.println("Loop finished.");
    }
}
```
> สิ่งที่ต่างจากRubyคือ
>* ต้องประกาศชนิดข้อมูลของตัวแปร (Static Typing) เช่น int i;
>* เงื่อนไขของต้องอยู่ในวงเล็บ ()
>* ใช้ {} เพื่อกำหนดขอบเขตของ loop
>* ทุกคำสั่งต้องลงท้ายด้วย ;

**C**
``` C
#include <stdio.h>
int main() {
    int i = 1;
    while (i <= 5) {
        printf("The number is: %d\n", i);
        i++;
    }
    printf("Loop finished.\n");
    return 0; //คือการบอก Operating System ว่าโปรแกรมทำงานเสร็จสิ้นโดยไม่มีข้อผิดพลาด ซึ่งเป็นมาตรฐานของภาษา C
}
```
> สิ่งที่ต่างจากRubyคือ
>* ต้องประกาศชนิดข้อมูลของตัวแปร (Static Typing) เช่น int i;
>* เงื่อนไขของต้องอยู่ในวงเล็บ ()
>* ใช้ {} เพื่อกำหนดขอบเขตของ loop
>* ทุกคำสั่งต้องลงท้ายด้วย ;
>  
> ***เนื่องจากJavaได้รับอิทธิพลจากCทำให้syntaxมีความคล้ายคลึงกันมาก ดังนั้นสิ่งที่ต่างจากRubyจึงเหมือนกับJava***

### References

### Presentation

### Video

### Quiz
