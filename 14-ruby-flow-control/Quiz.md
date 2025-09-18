# Quiz ประจำบท

##  1.จงเขียน case Statement ของ Ruby เเละ Switch case ของ C,Java เเละ Match ของ Python

กำหนดให้ int day = 6 ให้เขียนโค้ดรับวัน เเละเเสดงผลเป็น "Today is Saturday." ตามลำดับวันให้ครบทุกวันในสัปดาห์ โดยเริ่มที่วันจันทร์ เเละหากเลขที่รับมาไม่ใช่เลขที่ถูกต้องให้พิมพ์ "I think you might have remembered the number wrong."

#### Ruby

```ruby
day = 6
# using case statement

case day 
when 1  
  puts "Today is Monday."

when 2  
  puts "Today is Tuesday."

when 3  
  puts "Today is Wednesday."

when 4  
  puts "Today is Thursday."

when 5
  puts "Today is Friday."

when 6
  puts "Today is Saturday."

when 7  
  puts "Today is Sunday."
else  
  puts "I think you might have remembered the number wrong."

end

```

#### C

```c

```

#### Java

```java
```

#### Python

```python

day = 6
# using match

match day:
    case 1:
        print("Today is Monday.")

    case 2:
        print("Today is Tuesday.")

    case 3:
        print("Today is Wednesday.")

    case 4:
        print("Today is Thursday.")

    case 5:
        print("Today is Friday.")

    case 6:
        print("Today is Saturday.")

    case 7:
        print("Today is Sunday.")

    case _:
        print("I think you might have remembered the number wrong.")

```
