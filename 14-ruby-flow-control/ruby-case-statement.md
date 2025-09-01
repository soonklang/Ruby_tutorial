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
 >1. case คือ ค่าคงที่ที่เรากำหนดเพื่อนำเข้าไปในเงื่อนไขเพื่อหาผลลัพธ์ตามค่า โดยอาจเกิด output(ผลลัพธ์) หรือไม่เกิดก็ได้
 >2. when คือ ตัวเงื่อนไขที่จะนำค่า case มาพิจารณาตามเงื่อนไข หากค่า case ตรงตามเงื่อนไขก็จะได้ output ตามที่ตั้งไว้ในเงื่อนไขนั้น 
 >3. else คือ เป็นเงื่อนไขสุดท้าย ที่หากค่า case ถูกตรวจเข้าทุกเงื่อนไขเเล้ว เเต่ไม่ตรงตามเงื่อนไขที่มีเลย ก็ยังจะทำให้ค่า case นั้นยังสามารถเกิด output ได้

**ตัวอย่าง**

``` ruby
# concept of case statement

print "Input from one, two, three, four: "  

# str = gets.chomp

str = "two"

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

<details>
  <summary>Output</summary>
``` ruby
  Input from one, two, three, four: Input is 2
``` 
</details>
