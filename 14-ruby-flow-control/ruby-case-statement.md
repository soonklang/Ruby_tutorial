# Ruby case Statement
# Ruby case Statement คืออะไร?
มันคือการที่เราต้องการตรวจสอบค่า ให้ตรงตามเงื่อนไขที่เราต้องการหรือวางเอาไว้ โดยไม่มีความซับซ้อน ทำให้เกิดผลลัพธ์ได้หลากหลายเเบบตามเงื่อนไข ซึ่งทำหน้าที่เหมือนกับ switch ในภาษา C,Java

**Flow Chart**

![Local Image]()

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

โดยในตัวอย่างนี้ case จะรับค่า str ที่เป็น String นำไปตรวจสอบกับ when เมื่อเจอเงื่อนไขที่ตรงกันก็จะได้ output ตามเงื่อนไข เเล้วจบการทำงาน เเต่หากตรวจครบทุก when เเล้ว ก็จะเข้าสู่เงื่อนไข else เเละได้ output เป็น Default! เเล้วค่อยจบการทำงาน

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

โดยตัวอย่างนี้ ในตัวเงื่อนไขจะเรียกว่า number range หรือ เลขในช่วง ซึ่งค่าที่ case รับมาเป็น Integer เเล้วนำมาตรวจสอบกับเงื่อนไข when ที่เป็น number range โดยการดูว่าเลขที่รับมานั้น อยู่ในช่วงของเลขในเงื่อนไขหรือไม่ เช่น หากเลข case เป็นค่า 30 เมื่อตรวจสอบกับเงื่อนไข when ที่มี number range เป็น 0..32 ( 0 ถึง 32 โดยรวมค่าสุดท้ายด้วย) ก็จะได้ output ออกมาเป็น You fail! เเต่ถ้าหากเป็น case เป็นค่า 70 เมื่อตรวจสอบกับทุกเงื่อนไข when พบว่าไม่เข้าเงื่อนไขใดเลย จึงเข้าสู่เงื่อนไขสุดท้าย หรือ else ได้ output เป็น You got A grade!

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

หรือตัวอย่างอีกเเบบ

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







### Reference
* [https://www.techotopia.com/index.php/Ruby_While_and_Until_Loops](https://www.geeksforgeeks.org/ruby/ruby-case-statement/)
