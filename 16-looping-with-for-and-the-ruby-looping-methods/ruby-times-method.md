# Ruby times Method 
เมธอด times เป็นวิธีที่ใช้แทนการเขียน for loop เมธอดนี้ถูกกำหนดไว้ในคลาส Integer 
และเราสามารถทำงานซ้ำได้ตามจำนวนครั้งที่กำหนดโดยจะคืนค่าตัวเลขตั้งแต่ 0 จนถึง (จำนวนที่กำหนด - 1) 
แต่ถ้าใช้ .times กับเลขติดลบหรือ0 จะไม่วน loop และ return ค่าตัวเลขนั้นๆ

## Syntax พื้นฐาน
```ruby
integer.times do |variable|
  # คำสั่งที่ต้องการให้ทำซ้ำ
end
```
- **integer** : จำนวนครั้งที่จะวนซ้ำ (ต้องเป็น Integer เท่านั้น)
- **variable** : ตัวแปรตัวนับ (optional)
- **block { ... } หรือ do ... end** : คำสั่งที่จะทำซ้ำ

## ตัวอย่างการใช้ times method ในภาษา ruby
- **แบบใส่ตัวเลขเลย**
```ruby
5.times do |i|
  puts "รอบที่ #{i}"
end
```

- **แบบใส่ตัวแปร**
```ruby
n = 5
n.times do |i|
  puts "รอบที่ #{i}"
end
```

- **แบบ Single line block**
```ruby
5.times { |i| puts "รอบที่ #{i}" }
```

## Output
```ruby
รอบที่ 0
รอบที่ 1
รอบที่ 2
รอบที่ 3
รอบที่ 4
```

## ตัวอย่างของการใช้รอบติดลบใน times method
```ruby
-2.times do |i|
  puts "รอบที่ #{i}"
end
```

## Output
จะไม่มีอะไรถูกพิมออกมา​ แต่ค่าที่return จะเป็น -2 ถ้าอยากให้ค่า -2 ขึ้นต้องใส่ pนำหน้า ดังนี้
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>p(-2.times do |i|
  puts "รอบที่ #{i}"
end)
</code></pre>
</details>

## การเปรียบเทียบโค้ดนี้กับภาษาต่างๆ
- **Ruby (times method)**
```ruby
  5.times do |i|
  puts "รอบที่ #{i}"
end
```

- **C (for loop)**
```c
#include <stdio.h>

int main() {
    int n = 5;
    for (int i = 0; i < n; i++) {
        printf("รอบที่ %d\n", i);
    }
    return 0;
}
```
      เนื่องจากภาษา C ไม่มี .times method ต้องใช้ for loop หรือ while loop เพื่อวนรอบตามที่กำหนด

- **Java (for loop)**
```java
public class Main {
    public static void main(String[] args) {
        int n = 5;
        for (int i = 0; i < n; i++) {
            System.out.println("รอบที่ " + i);
        }
    }
}
```

    เนื่องจากภาษา Java ไม่มี .times method ต้องใช้ for loop หรือ while loop เพื่อวนรอบตามที่กำหนด

- **Python (for loop)**
```python
n = 5
for i in range(n):
    print(f"รอบที่ {i}")
```
    เนื่องจากภาษา Python ไม่มี .times method ต้องใช้ for loop หรือ while loop เพื่อวนรอบตามที่กำหนด



## แหล่งอ้างอิง
- **Smyth, N. (2016, October 27). Looping with for and the Ruby Looping Methods. Techotopia. Retrieved August 30, 2025, from
https://www.techotopia.com/index.php/Looping_with_for_and_the_Ruby_Looping_Methods**
- **GeeksforGeeks. (2025, July 12). Ruby Integer times function with example. GeeksforGeeks. Retrieved August 30, 2025, from https://www.geeksforgeeks.org/ruby/ruby-integer-times-function-with-example/**
- **Ruby Monstas. (n.d.). Alternative block syntaxes. In Ruby for Beginners. Retrieved September 1, 2025, from https://ruby-for-beginners.rubymonstas.org/blocks/syntax.html**
- **Ruby Core Team. (n.d.). Integer#times. In Ruby 3.2 Documentation. Retrieved September 1, 2025, from https://docs.ruby-lang.org/en/3.2/Integer.html**
- **Flanagan, D., & Matsumoto, Y. (2008). The Ruby Programming Language. O’Reilly Media. Retrieved September 1, 2025, from https://theswissbay.ch/pdf/Gentoomen%20Library/Programming/Ruby/The%20Ruby%20Programming%20Language%20-%20Oreilly.pdf**
- **Goalkicker. (n.d.). Ruby Notes for Professionals. Retrieved September 1, 2025, from https://goalkicker.com/RubyBook/RubyNotesForProfessionals.pdf**

## Slides

## Video
