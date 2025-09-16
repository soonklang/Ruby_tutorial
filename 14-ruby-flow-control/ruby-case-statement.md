# Ruby case Statement
## Ruby case Statement คืออะไร?

การนำค่าหรือตัวแปรที่กำหนด ไปตรวจกับเงื่อนไข ที่มีหลายเงื่อนไข โดยแต่ละเงื่อนไขมีผลลัพธ์ที่แตกต่างตามที่วางเอาไว้ ซึ่งทำหน้าที่เหมือนกับ switch ในภาษา C,Java หรือ match ในภาษา Python

**Flow Chart**

![Local Image](../.gitbook/assets/ruby-case-diagram.jpg)

**Basic Syntax**

```ruby
result = case value
   when match1 then result1
   when match2 then result2
   when match3 then result3
   when match4 then result4
   when match5 then result5
   when match6 then result6
   else result7
end
```

หรือเเบบนี้ก็ได้เช่นกัน

```ruby
case expression

when expression 1
  # your code

when expression 2
  # your code
.
.

else
  # your code
end
```

> โดยจะมีส่วนที่สำคัญอยู่ 3 ส่วนคือ
>
> 1. case คือ เป็นตัวที่รับค่าหรือตัวแปรที่เรากำหนด เเล้วนำไปตรวจกับตัวเงื่อนไขเพื่อหาผลลัพธ์(Output)
> 2. when คือ ตัวเงื่อนไขที่จะนำค่า case มาพิจารณาตามเงื่อนไข หากค่า case ตรงตามเงื่อนไขก็จะได้ output ตามที่ตั้งไว้ในเงื่อนไขนั้น
> 3. else คือ เป็นเงื่อนไขสุดท้าย ที่หากค่า case ถูกตรวจเข้าทุกเงื่อนไขเเล้ว เเต่ไม่ตรงตามเงื่อนไขที่มีเลย ก็ยังจะทำให้ค่า case นั้นยังสามารถเกิด output ได้

**ตัวอย่างที่เป็น String**

โดยที่ case รับค่าเป็น "Patriot" เเล้วนำค่าไปเช็คในเงื่อนไข when

```ruby
car = "Patriot"

manufacturer = case car
   when "Focus" then "Ford"
   when "Navigator" then "Lincoln"
   when "Camry" then "Toyota"
   when "Civic" then "Honda"
   when "Patriot" then "Jeep"
   when "Jetta" then "VW"
   when "Ceyene" then "Porsche"
   when "Outback" then "Subaru"
   when "520i" then "BMW"
   when "Tundra" then "Nissan"
   else "Unknown"
end

puts "The " + car  + " is made by "  + manufacturer
```

เมื่อ case เจอกับเงื่อนไขที่ตรงกันก็จะได้ output ออกมาเเล้วจบการทำงาน

<details>

<summary><strong>Output</strong></summary>

```

  The Patriot is made by Jeep
```

</details>

เเต่หาก case ไม่ตรงกับเงื่อนไขไหนเลย จะได้ output ของเงื่อนไข else เเทนเเล้วจบการทำงาน

<details>

<summary><strong>Output</strong></summary>

```

  The Prius is made by Unknown
```

</details>

**หรือจะเขียนโดยการใช้ put(หรือจะใช้ print ก็ได้เพราะเหมือนกัน)**

โดยในตัวอย่างนี้ case จะรับค่า str ที่เป็น String นำไปตรวจสอบกับ when

```ruby
print "Input from one, two, three, four: "  

str = "two"
# using case statement
case str 
when "one"  
  puts 'Input is 1'

when "two"  
  puts 'Input is 2'

when "three"  
  puts 'Input is 3'

 when "four"  
  puts 'Input is 4'

else  
  puts "Default!"

end  
```

เมื่อเจอเงื่อนไขที่ตรงกันก็จะได้ output ตามเงื่อนไข เเล้วจบการทำงาน

<details>

<summary><strong>Output</strong></summary>

```

  Input from one, two, three, four: Input is 2
```

</details>

เเต่หากตรวจครบทุกเงื่อนไข when เเล้ว ก็จะเข้าสู่เงื่อนไข else เเละได้ output เป็น Default! เเล้วค่อยจบการทำงาน

<details>

<summary><strong>Output</strong></summary>

```

  Input from one, two, three, four: Default!
```

</details>

**ตัวอย่างที่เป็น Number range**

โดยตัวอย่างนี้ ในตัวเงื่อนไขจะเรียกว่า number range หรือ เลขในช่วง ซึ่งค่าที่ case รับมาเป็น Integer เเล้วนำมาตรวจสอบกับเงื่อนไข when ที่เป็น number range โดยการดูว่าเลขที่รับมานั้น อยู่ในช่วงของเลขในเงื่อนไขหรือไม่

```ruby
score = 70

result = case score
   when 0..40 then "Fail"
   when 41..60 then "Pass"
   when 61..70 then "Pass with Merit"
   when 71..100 then "Pass with Distinction"
   else "Invalid Score"
end

puts result
```

case เป็นค่า 70 เมื่อตรวจสอบกับทุกเงื่อนไข when พบว่าเข้ากับเงื่อนไขที่ 3 คือ 61 .. 70(เลขตั้งเเต่ 61-70 รวมเลขท้ายด้วย) จึงได้ output เป็น Pass with Merit เเล้วจบการทำงาน

<details>

<summary><strong>Output</strong></summary>

```

  Pass with Merit
```

</details>

หากเลข case เป็นค่าที่ไม่ตรงกับเงื่อนไขใดเลย ก็จะได้ output ออกมาเป็น adult เเล้วจบการทำงาน

<details>

<summary><strong>Output</strong></summary>

```

  Invalid Score
```

</details>

**ตัวอย่างอีกเเบบที่ใช้ put(หรือจะใช้ print ก็ได้เพราะเหมือนกัน) เเทน then**

```ruby
$age =  5
case $age
when 0 .. 2
   puts "baby"
when 3 .. 6
   puts "little child"
when 7 .. 12
   puts "child"
when 13 .. 18
   puts "youth"
else
   puts "adult"
end
```

case เป็นค่า 5 เมื่อนำไปตรวจสอบพบว่าตรงกับเงื่อนไขที่ 2 คือ 3..6 ซึ่งได้ output เป็น little child

<details>

<summary><strong>Output</strong></summary>

```

  little child
```

</details>

หากเลข case เป็นค่าที่ไม่ตรงกับเงื่อนไขใดเลย ก็จะได้ output ออกมาเป็น adult เเล้วจบการทำงาน

<details>

<summary><strong>Output</strong></summary>

```

  adult
```

</details>

#### การเปรียบกับภาษาอื่น (C,Java,Python)

**ภาษา Ruby**

```ruby
grade = 85

case grade
when 90..100
  puts "A"
when 80..89
  puts "B"
when 70..79
  puts "C"
else
  puts "F"
end
```

<details>

<summary><strong>Output</strong></summary>

```

  B
```

</details>

**ภาษา C**

```c
#include <stdio.h>
int main() {
  int var = 10;
  switch (var)
    {
      case 5:
          printf("Case 1 executed.");
          break;
      case 10:
          printf("Case 2 executed. ");
          break;
      case 15:
          printf("Case 3 executed. ");
          break;
      case 20:
          printf("Case 4 executed. ");
          break;
      default:
          printf("Default case executed. ");
    }
}
```

<details>

<summary><strong>Output</strong></summary>

```
Case 2 executed.
  
```

</details>

ข้อเเตกต่างกับ Ruby :

```
            1. ตัวเงื่อนไขใช้ case เเทน when

            2. ต้องใช้ break ช่วยในการหยุดการทำงานซึ่ง Ruby ไม่ต้องใช้
               
            3. การเเสดงผลใช้ printf เเทน puts,print

            4. ตัวเงื่อนไขใช้ : เพื่อเเยกระหว่างเงื่อนไขกับส่วนของ output ในการเขียนโค้ด

            5. ที่เงื่อนไขสุดท้ายนั้นเขียนเป็น default: เเต่ของ Ruby ใช้เป็น else

               
```

**ภาษา Java**

```java
class Main
{
    public static void main(String[] args) {
        int size = 2; 

        switch (size) {
            case 1:
                System.out.println("Extra Small");
                break;
            case 2:
                System.out.println("Small");
                break;
            case 3:
                System.out.println("Medium");
                break;
            case 4:
                System.out.println("Large");
                break;
            case 5:
                System.out.println("Extra Large");
                break;
            default:
                System.out.println("Invalid size number");
        }
    }
}

```

<details>

<summary><strong>Output</strong></summary>

```

  Small
```

</details>

ข้อเเตกต่างกับ Ruby :

```
            1. ตัวเงื่อนไขใช้ case เเทน when
               
            2. ต้องใช้ break ช่วยในการหยุดการทำงานซึ่ง Ruby ไม่ต้องใช้
               
            3. การเเสดงผลใช้ System.out.println เเทน puts,print

            4. ตัวเงื่อนไขใช้ : เพื่อเเยกระหว่างเงื่อนไขกับส่วนของ output ในการเขียนโค้ด

            5. ที่เงื่อนไขสุดท้ายนั้นเขียนเป็น default: เเต่ของ Ruby ใช้เป็น else
               
```

**ภาษา Python**

Python 3.10 หรือเวอร์ชั่นหลังจากนี้ จะสามารถใช้ match ที่มีความคล้ายกับ switch ได้

```python
animal = "Eagle"
match animal:
    case "Eagle" | "Parrot":
        print("Bird")
    case "Lion" | "Tiger":
        print("Mammal")
    case "Python" | "Crocodile":
        print("Reptile")
    case _:
        print("Unknown Class")

# Bird
```

<details>

<summary><strong>Output</strong></summary>

```

  Bird
```

</details>

ข้อเเตกต่างกับ Ruby :

```
               1. ตัวเงื่อนไขใช้ case เเทน when

               2. การเเสดงผลใช้ print ในขณะที่ Ruby ใช้ได้ทั้ง puts,print

               3. ตัวเงื่อนไขใช้ : เพื่อเเยกระหว่างเงื่อนไขกับส่วนของ output ในการเขียนโค้ด

               4. ที่เงื่อนไขสุดท้ายนั้นเขียนเป็น case_: เเต่ของ Ruby ใช้เป็น else
              
```

#### Reference

* [https://www.techotopia.com/index.php/The\_Ruby\_case\_Statement](https://www.techotopia.com/index.php/The_Ruby_case_Statement) ตัวอย่างของ Ruby เเละศึกษา syntax
* [https://www.tutorialspoint.com/ruby/ruby\_if\_else.htm](https://www.tutorialspoint.com/ruby/ruby_if_else.htm) ตัวอย่างของ Ruby ของ Range
* https://www.geeksforgeeks.org/ruby/ruby-case-statement/ ตัวอย่างของ Ruby เเละศึกษา syntax
* [https://www.techotopia.com/index.php/Ruby\_Ranges](https://www.techotopia.com/index.php/Ruby_Ranges) สำหรับศึกษา number range
* [https://www.tutorialspoint.com/ruby/ruby\_ranges.htm](https://www.tutorialspoint.com/ruby/ruby_ranges.htm) สำหรับศึกษา number range
* https://www.scaler.com/topics/ruby-switch-statement/ สำหรับการยกตัวอย่างของ Ruby เพื่อเปรียบเทียบ
* https://how.dev/answers/how-to-use-the-switch-statement-in-c สำหรับการยกตัวอย่างของ C เพื่อเปรียบเทียบ
* https://www.geeksforgeeks.org/java/switch-statement-in-java/ สำหรับการยกตัวอย่างของ Java เพื่อเปรียบเทียบ
* https://www.datacamp.com/tutorial/python-switch-case สำหรับการยกตัวอย่างของ Python เเบบ match เพื่อเปรียบเทียบ

#### Presentation
[Ruby case Statement](https://github.com/user-attachments/files/22311603/660710587-casestatement.pdf.pdf)


#### Video
