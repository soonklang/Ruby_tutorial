# Ruby case Statement
# Ruby case Statement คืออะไร?
มันคือการที่เราต้องการตรวจสอบค่า ให้ตรงตามเงื่อนไขที่มีหลายเงื่อนไขเเละหลายผลลัพธ์ตามที่เราต้องการหรือวางเอาไว้ โดยไม่มีความซับซ้อน ทำให้เกิดผลลัพธ์ได้หลากหลายเเบบตามเงื่อนไข ซึ่งทำหน้าที่เหมือนกับ switch ในภาษา C,Java

**Flow Chart**

![Local Image](picture-660710587/ruby-case-diagram.jpg)

**Basic Syntax**
``` ruby
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
>โดยจะมีส่วนที่สำคัญอยู่ 3 ส่วนคือ 
 >1. case คือ ค่าที่เรากำหนดเพื่อนำเข้าไปในเงื่อนไขเพื่อหาผลลัพธ์ตามค่า โดยอาจเกิด output(ผลลัพธ์) หรือไม่เกิดก็ได้
 >2. when คือ ตัวเงื่อนไขที่จะนำค่า case มาพิจารณาตามเงื่อนไข หากค่า case ตรงตามเงื่อนไขก็จะได้ output ตามที่ตั้งไว้ในเงื่อนไขนั้น 
 >3. else คือ เป็นเงื่อนไขสุดท้าย ที่หากค่า case ถูกตรวจเข้าทุกเงื่อนไขเเล้ว เเต่ไม่ตรงตามเงื่อนไขที่มีเลย ก็ยังจะทำให้ค่า case นั้นยังสามารถเกิด output ได้

**ตัวอย่างที่เป็น String**

โดยในตัวอย่างนี้ case จะรับค่า str ที่เป็น String นำไปตรวจสอบกับ when เมื่อเจอเงื่อนไขที่ตรงกันก็จะได้ output ตามเงื่อนไข เเล้วจบการทำงาน เเต่หากตรวจครบทุกเงื่อนไข when เเล้ว ก็จะเข้าสู่เงื่อนไข else เเละได้ output เป็น Default! เเล้วค่อยจบการทำงาน

``` ruby
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

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>
  Input from one, two, three, four: Input is 2
</code></pre>
</details>

**ตัวอย่างที่เป็นตัวเลข**

โดยตัวอย่างนี้ ในตัวเงื่อนไขจะเรียกว่า number range หรือ เลขในช่วง ซึ่งค่าที่ case รับมาเป็น Integer เเล้วนำมาตรวจสอบกับเงื่อนไข when ที่เป็น number range โดยการดูว่าเลขที่รับมานั้น อยู่ในช่วงของเลขในเงื่อนไขหรือไม่ เช่น หากเลข case เป็นค่า 30 เมื่อตรวจสอบกับเงื่อนไข when ที่มี number range เป็น 0..32 ( 0 ถึง 32 โดยรวมค่าสุดท้ายด้วย) ก็จะได้ output ออกมาเป็น You fail! เเล้วจบการทำงาน เเต่ถ้าหากเป็น case เป็นค่า 70 เมื่อตรวจสอบกับทุกเงื่อนไข when พบว่าไม่เข้าเงื่อนไขใดเลย จึงเข้าสู่เงื่อนไขสุดท้าย หรือ else ได้ output เป็น You got A grade! เเล้วจบการทำงาน

``` ruby
marks = 70

case marks
# using range operators ..
when 0..32
  puts "You fail!"

when 33..40
  puts "You got C grade!"

when 41..60
  puts "You got B grade!"

else
 puts  "You got A grade!"
 
end
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>
  You got A grade!
</code></pre>
</details>

**ตัวอย่างอีกเเบบ** 

ที่เงื่อนไข when เป็นรูปแบบ ค่า,ค่า ที่ความหมายเหมือนกับคำว่า 'หรือ' เช่น case เป็นค่า "1" เมื่อนำไปตรวจกับเงื่อนไขพบว่าตรง กับเงื่อน ไข "1","2" เพราะ case ที่เป็น "1" ตรงกับค่าในเงื่อนไขที่เป็น "1" เช่นกัน ทำให้ output เป็น You order Espresso! เเต่หาก case ไม่ตรงกับเงื่อนไขใดเลย ก็จะได้ output ตาม เงื่อนไข else คือ No Order!

``` ruby
choice = "5"

# using 'case' statement
case choice
    
    # the two values
    when "1","2"
        puts "You order Espresso!"
    
    when "3","4"
        puts "You order Short Macchiato!"
    
    when "5","6"
        puts "You order Ristretto!"
    
    when "7","8"
        puts "You order Cappuccino!"
    
else
    "No Order!"
end
``` 
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>
  You order Ristretto!
</code></pre>
</details>

### การเปรียบกับภาษาอื่น (C,Java,Python)

**ภาษา Ruby**

``` ruby
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
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>
  B
</code></pre>
</details>

**ภาษา C**


``` c
int day = 4;

switch (day) {
  case 1:
    printf("Monday");
    break;
  case 2:
    printf("Tuesday");
    break;
  case 3:
    printf("Wednesday");
    break;
  case 4:
    printf("Thursday");
    break;
  case 5:
    printf("Friday");
    break;
  case 6:
    printf("Saturday");
    break;
  case 7:
    printf("Sunday");
    break;
}
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>
  Thursday
</code></pre>
</details>

**ภาษา Java**

``` java
int day = 4;
switch (day) {
  case 1:
    System.out.println("Monday");
    break;
  case 2:
    System.out.println("Tuesday");
    break;
  case 3:
    System.out.println("Wednesday");
    break;
  case 4:
    System.out.println("Thursday");
    break;
  case 5:
    System.out.println("Friday");
    break;
  case 6:
    System.out.println("Saturday");
    break;
  case 7:
    System.out.println("Sunday");
    break;
}
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>
  Thursday
</code></pre>
</details>

**ภาษา Python**

Python ไม่มี switch case เเต่มีสิ่งที่ใช้เเทนได้คือ if-else(elif) 

```python
bike = 'Yamaha'

if bike == 'Hero':
    print("bike is Hero")

elif bike == "Suzuki":
    print("bike is Suzuki")

elif bike == "Yamaha":
    print("bike is Yamaha")

else:
    print("Please choose correct answer")
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>
  bike is Yamaha
</code></pre>
</details>

หรือถ้าหากเป็น Python 3.10 หรือเวอชันหลังจากนี้ จะสามารถใช้ match ที่มีความคล้ายกับ switch ได้
```python
day = "Monday"

# Match the day to predefined patterns
match day:
    case "Saturday" | "Sunday":
        print(f"{day} is a weekend.")  # Match weekends
    case "Monday" | "Tuesday" | "Wednesday" | "Thursday" | "Friday":
        print(f"{day} is a weekday.")  # Match weekdays
    case _:
        print("That's not a valid day of the week.")  # Default case

# Monday is a weekday.
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>
  Monday is a weekday.
</code></pre>
</details>



### Reference
* [https://www.geeksforgeeks.org/ruby/ruby-case-statement/] ตัวอย่างของ Ruby
* [https://www.techotopia.com/index.php/Ruby_Ranges] สำหรับศึกษา number range
* [https://www.scaler.com/topics/ruby-switch-statement/] สำหรับการยกตัวอย่างของ Ruby
* [https://www.w3schools.com/c/c_switch.php] สำหรับการยกตัวอย่างของ C
* [https://www.w3schools.com/java/java_switch.asp] สำหรับการยกตัวอย่างของ Java
* [https://www.geeksforgeeks.org/python/switch-case-in-python-replacement/] สำหรับการยกตัวอย่างของ Python เเบบ elif
* [https://www.datacamp.com/tutorial/python-switch-case] สำหรับการยกตัวอย่างของ Python เเบบ match
