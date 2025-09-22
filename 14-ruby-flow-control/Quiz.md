# Quiz ประจำบท

##  1.จงเขียน case Statement ของ Ruby เเละ Switch case ของ C,Java เเละ Match ของ Python

กำหนดให้ int day = 6 ให้เขียนโค้ดรับวัน เเละเเสดงผลเป็น "Today is Saturday." ตามลำดับวันให้ครบทุกวันในสัปดาห์ โดยเริ่มที่วันจันทร์ เเละหากเลขที่รับมาไม่ใช่เลขที่ถูกต้องให้พิมพ์ "I think you might have remembered the number wrong."

## เฉลย

#### Ruby

```ruby
day = 6

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
#include <stdio.h>
int main() {
  int day = 6;

  switch (day)
    {
      case 1:
            printf("Today is Monday.");
            break;
      case 2:
            printf("Today is Tuesday.");
            break;
      case 3:
            printf("Today is Wednesday.");
            break;
      case 4:
            printf("Today is Thursday.");
            break;
      case 5:
            printf("Today is Friday.");
            break;
      case 6:
            printf("Today is Saturday.");
            break;
      case 7:
            printf("Today is Sunday.");
            break;
      default:
            printf("I think you might have remembered the number wrong.");
    }
}

```

#### Java

```java
class Main
{
    public static void main(String[] args) {
        int day = 6; 

        switch (day) {
            case 1:
                System.out.println("Today is Monday.");
                break;
            case 2:
                System.out.println("Today is Tuesday.");
                break;
            case 3:
                System.out.println("Today is Wednesday.");
                break;
            case 4:
                System.out.println("Today is Thursday.");
                break;
            case 5:
                System.out.println("Today is Friday.");
                break;
            case 6:
                System.out.println("Today is Saturday.");
                break;
            case 7:
                System.out.println("Today is Sunday.");
                break;
            default:
                System.out.println("I think you might have remembered the number wrong.");
        }
    }
}

```

#### Python

```python

day = 6

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
##  2.จงแปลง if else ต่อไปนี้เป็น ternary operator โดยใช้ภาษา java javascript python
```ruby
if wight >= 75
    body = "fat"
else 
    body = "thin"
end
puts body
```
##เฉลย

#### python
```python
print("fat" if wight >= 75 else "thin")
```
#### Javascript
```javascript
console.log((wight >= 75) ? "fat" : "thin");
```
#### Java
```java
System.out.println((wight >= 75) ? "fat" :  "thin");
```
## 3.พิจารณาโค้ด Ruby ต่อไปนี้

```Ruby
puts "Welcome!" if true
puts "Bye!" if false
```

##### จะแสดง output ออกมาเป็น?
A. Welcome! Bye!

B. Welcome!

C. Bye!

D. ไม่มี output

#### เฉลย
คำตอบ: B
