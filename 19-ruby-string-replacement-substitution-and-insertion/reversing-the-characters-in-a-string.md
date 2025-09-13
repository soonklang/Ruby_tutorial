# Reversing the Characters in a String
คือการย้อนลำดับตัวอักษรที่อยู่ในสตริงให้เรียงจากหลังไปหน้า   
## มี 2 วิธี

### วิธีที่ 1 : การใช้เมธอด .reverse กับตัวแปรประเภทสตริง
```ruby
str = 'Hello, World'
reversed = str.reverse

puts str
puts reversed
```
ผลลัพธ์
```ruby
Hello, World
dlroW ,olleH
```

การใส่เครื่องหมาย ! ทำให้ค่าที่อยู่ในตัวแปรต้นฉบับถูกเปลี่ยนไปด้วย
```ruby
str = 'Hello, World'
reversed = text.reverse!

puts str
puts reversed
```
ผลลัพธ์
```ruby
dlroW ,olleH
dlroW ,olleH
```

### วิธีที่ 2 : การใช้ลูป .each_char และต่อสตริงขึ้นมาใหม่
```ruby
str = 'Hello, World'
reversed = ''
str.each_char { |char| reversed = char+reversed}

puts str
puts reversed
```
ผลลัพธ์
```ruby
Hello, World
dlroW ,olleH
```

## เปรียบเทียบการ reverse ในภาษาอื่นๆ
เนื่องจากทั้ง 3 ภาษานั้นไม่มีเมธอด reverse ติดมากับตัวภาษาเราจึงต้องใช้วิธีสร้างลูปเพื่อต่อสตริงขึ้นมาใหม่

### Java
```java
public class Main {
  public static void main(String[] args) {

    String str = "Hello, World";
    String reversed = "";

    for (int i = 0; i < str.length(); i++) {
      reversed = str.charAt(i) + reversed;
    }
    System.out.println(str);
    System.out.println(reversed);
  }
}
```
 - ใช้เมธอด.length()ร่วมกับเมธอด.charAt() เลือกตัวcharในตำแหน่งนั้นเพื่อใช้ต่อStringขึ้นมาใหม่
 - ไม่มีเมธอด reverse จึงใช้การลูปแทน

### C
```c
#include <stdio.h>
#include <string.h>

void rev(char* src, char* dest) {
    int length = strlen(src);

    for (int i = 0; i < length; i++) {
        printf("%c\n", src[length - i]);
        dest[i] = src[length - i-1];  
    }
    dest[length] = '\0'
}

int main() {
    char str[20] = "Hello, World";
    char reversed[20];   

    rev(str, reversed);

    printf("%s\n", str);
    printf("%s\n", reversed);

    return 0;
}
```
 - เนื่องจากตัวภาษาCนั้นไม่มีตัวแปรStringจึงต้องใช้อาเรย์ของตัวแปรCharแทน   
 - ใช้การเลือกตัวแปรCharในตำแหน่งอาเรย์นั้นมาแทนค่าในอาเรย์ใหม่
 - ไม่มีเมธอด reverse จึงใช้การลูปแทน

### Python
```python
str = "Hello, World"
reversed = str[::-1]
print(str)
print(reversed)
```
- ใช้เมธอด slice notation
- ไม่มีเมธอด reverse สามารถใช้การลูปแทนได้ แต่วิธีนี้เป็นวิธีที่ง่ายที่สุด
- มีความสั้นใกล้เคียง Ruby
- ส่งผลเสียกับ readability ในโด้ด
  
Slice notaion คือการตัดค่าออกมาเป็นส่วนย่อยๆและเรียงค่าใน String หริอ List ให้เป็นในรูปแบบที่ต้องการ
Syntax
```python
sequence[start:stop:step]
```
 - sequence - String หรือ List  
 - start - ตำแหน่งเริ่มต้น (เริ่มตำแหน่งCharตัวแรกคือ 0 )  
 - stop - ตำแหน่งสิ้นสุด (ค่าตำแหน่งCharตัวสุดท้ายที่เลือก + 1)
 - step - จำนวนตัวอักษรที่ข้าม (เมื่อใส่ -1 ตัวอักษรเรียงย้อนกลับ)


---
# Reference 
- https://docs.ruby-lang.org/en/master/
- https://www.techotopia.com/index.php/Ruby_String_Replacement,_Substitution_and_Insertion#Reversing_the_Characters_in_a_String
- https://www.w3schools.com/java/java_howto_reverse_string.asp
- https://www.w3schools.com/Python/python_howto_reverse_string.asp
- https://www.geeksforgeeks.org/c/reverse-string-in-c/
- [Comprehesive Ruby Programming](https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Comprehensive%20Ruby%20Programming.pdf)
- [The Ruby Programming Language](https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/The%20Ruby%20Programming%20Language.pdf)
# Presentation
- [Slide](https://github.com/660710618/PL_Reversing_the_Characters_in_a_String.pptx)
- [Video]()
