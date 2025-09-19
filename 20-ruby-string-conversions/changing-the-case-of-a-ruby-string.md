# Changing the Case of a Ruby String
คือ การเปลี่ยนตัวอักษร string ให้เป็นตัวพิมเล็กหรือตัวพิมพ์ใหญ่ซึ่งสามารถทำได้ด้วยการเรียกใช้ method 
ซึ่งการเรียกใช้ method ที่เกี่ยวกับการเปลี่ยนตัวพิมพ์ ก็จะมี 2 รูปแบบคือสร้าง String ใหม่ขึ้นมาเเล้วคืนค่าเป็น String ใหม่ (Non-destructive) และแบบที่แก้ไข String เดิมโดยตรง (Destructive) ซึ่งมักจะลงท้ายด้วยเครื่องหมาย (!) เรียกว่า bang

#### ข้อควรระวัง: ถ้า string ถูก freeze ("str".freeze) การใช้ upcase! จะเกิด FrozenError

## การใช้งานพื้นฐาน

###  Capitalize
เมธอดนี้จะเปลี่ยน String ตัวแรกเป็นตัวพิมพ์ใหญ่และแปลงส่วนที่เหลือเป็นตัวพิมพ์เล็ก
```ruby
"hello world".capitalize
=> "Hello world"
"hello world".capitalize!  # ใช้เครื่องหมาย bang 
=> "Hello world"
```

###  Downcase
เมธอดนี้จะเปลี่ยน String ทุกตัวเป็นตัวพิมพ์เล็ก
```ruby
"HELLO WORLD".downcase
=> "hello world"
"HELLO WORLD".downcase!  # ใช้เครื่องหมาย bang
=> "hello world"
```

###  Upcase
เมธอดนี้จะเปลี่ยน String ทุกตัวเป็นตัวพิมพ์ใหญ่
```ruby
"hello world".upcase
=> "HELLO WORLD"
"hello world".upcase!  # ใช้เครื่องหมาย bang
=> "HELLO WORLD"
```

###  Swapcase
เมธอดนี้จะสลับ String ทุกตัว ซึ่งตัวพิมพ์เล็กจะเป็นใหญ่ และใหญ่จะเป็นเล็ก
```ruby
"HeLLo WoRld".swapcase
=> "hEllO wOrLD"
"HeLLo WoRld".swapcase!  # ใช้เครื่องหมาย bang
=> "hEllO wOrLD"
```
## ตัวอย่างการใช้งานเพิ่มเติม
ในบางภาษา เช่น ตุรกี (Turkish) มีกฎการใช้ตัวพิมพ์เล็ก-ใหญ่ที่ไม่เหมือนปกติ เราสามารถระบุภาษาเพื่อให้ Ruby แปลงได้อย่างถูกต้อง
```ruby
# ภาษาตุรกี ตัว I พิมพ์ใหญ่ จะกลายเป็น i ไม่มีจุด (ı) เวลาเป็นพิมพ์เล็ก
"İstanbul".downcase             # => "i̇stanbul" (ผลลัพธ์อาจไม่ถูกต้องขึ้นอยู่กับระบบ)
"İstanbul".downcase(:turkish)  # => "istanbul" (ถูกต้องตามหลักภาษาตุรกี)
```
<br>

การเรียกเมธอดต่อกันเราสามารถเรียกใช้หลายๆ เมธอดต่อกันเพื่อจัดการข้อความที่ซับซ้อนได้
```ruby
# ตัดช่องว่าง -> ทำให้เป็นตัวเล็ก -> ทำให้ตัวแรกเป็นตัวใหญ่
"  MIXED case STRING  ".strip.downcase.capitalize
# => "Mixed case string"
```
<br>

สร้างรูปแบบการแปลงของตัวเอง
เราสามารถเขียนฟังก์ชันของเราเองโดยผสมผสานเมธอดเหล่านี้เพื่อสร้างรูปแบบที่ต้องการได้
```ruby
# เปลี่ยนข้อความแบบ snake_case (เช่น first_name) เป็น Title Case (First Name)
def snake_to_title(str)
  str.split('_').map(&:capitalize).join(' ')
end

snake_to_title("first_name_field")  # => "First Name Field"
```
<br>

ใช้ร่วมกับ Regular Expressions (RegEx)
เราสามารถใช้ RegEx เพื่อเลือกเปลี่ยนตัวพิมพ์เฉพาะส่วนที่ตรงกับเงื่อนไขที่เรากำหนดได้
```ruby
# ทำให้ตัวอักษรที่ตามหลัง "." เป็นตัวพิมพ์ใหญ่
text = "hello. world! how are you?"
text.gsub(/(?<=\.\s)[a-z]/) { |match| match.upcase }
# => "hello. World! How are you?"
```
<br>

# การเปรียบเทียบกับภาษาอื่นๆ
## java

### Capitalize
Java ไม่มีเมธอด capitalize ในตัว แต่เราสามารถสร้างขึ้นเองได้ง่ายๆ โดยการผสมผสานเมธอดอื่น หรือใช้ ไลบรารีภายนอกอย่าง Apache Commons Lang
```java
String text = "hello world";
String capitalized = text.substring(0, 1).toUpperCase() + text.substring(1).toLowerCase();
// => "Hello world"

// ต้อง import org.apache.commons.lang3.StringUtils;
StringUtils.capitalize("hello world");
// => "Hello world"
```
### Downcase
ใช้เมธอด toLowerCase() เพื่อแปลงทุกตัวอักษรเป็นตัวพิมพ์เล็ก
```java
"HELLO WORLD".toLowerCase();
// => "hello world"
```

### Upcase
ใช้เมธอด toUpperCase() เพื่อแปลงทุกตัวอักษรเป็นตัวพิมพ์ใหญ่
```java
"hello world".toUpperCase();
// => "HELLO WORLD"
```

### Swapcase
Java ไม่มีเมธอด swapcase มาให้โดยตรง แต่สามารถใช้ไลบรารีภายนอกอย่าง Apache Commons Lang ได้
```java
// ต้อง import org.apache.commons.lang3.StringUtils;
StringUtils.swapCase("HeLLo WoRld");
// => "hEllO wOrLD"
```
<br>

## Python
### Capitalize
ใช้เมธอด .capitalize() ซึ่งจะเปลี่ยนตัวอักษรแรกเป็นตัวพิมพ์ใหญ่และที่เหลือเป็นตัวพิมพ์เล็ก
```Python
"hello world".capitalize()
# => "Hello world"
```

### Downcase
ใช้เมธอด .lower() เพื่อแปลงทุกตัวอักษรเป็นตัวพิมพ์เล็ก
```Python
"HELLO WORLD".lower()
# => "hello world"
```

### Upcase
ใช้เมธอด .upper() เพื่อแปลงทุกตัวอักษรเป็นตัวพิมพ์ใหญ่
```Python
"hello world".upper()
# => "HELLO WORLD"
```

### Swapcase
ใช้เมธอด .swapcase() เพื่อสลับระหว่างตัวพิมพ์เล็กและใหญ่
```Python
"HeLLo WoRld".swapcase()
# => "hEllO wOrLD"
```
<br>

## C
ใน C เราต้องวนลูปเพื่อเปลี่ยนตัวอักษรทีละตัว

### Downcase
ใช้ฟังก์ชัน tolower() กับอักขระแต่ละตัว
```C
#include <stdio.h>
#include <ctype.h>

char str[] = "HELLO WORLD";
for (int i = 0; str[i]; i++) {
    str[i] = tolower(str[i]);
}
// str จะกลายเป็น "hello world"
```

### Upcase
ใช้ฟังก์ชัน toupper() กับอักขระแต่ละตัว
```C
#include <stdio.h>
#include <ctype.h>

char str[] = "hello world";
for (int i = 0; str[i]; i++) {
    str[i] = toupper(str[i]);
}
// str จะกลายเป็น "HELLO WORLD"
```

### Capitalize และ Swapcase
ภาษา C ไม่มีฟังก์ชันมาตรฐานสำหรับ capitalize และ swapcase แต่สามารถเขียนขึ้นเองได้โดยใช้ toupper(), tolower(), และ islower() เเละ isupper() เพื่อตรวจสอบตัวอักษรแต่ละตัวในลูป

<br>

# Video Presentation
# Slide Presentation

#### ruby
- GeeksforGeeks. (23 Jul, 2025). How to Convert a String to Lower or Upper Case in Ruby? Retrieved August 30, 2025 From
  https://www.geeksforgeeks.org/ruby/how-to-convert-a-string-to-lower-or-upper-case-in-ruby/
- techotopia. (27 October 2016). Ruby String Conversions. Retrieved August 30, 2025 From
  https://www.techotopia.com/index.php/Ruby_String_Conversions
- CrackedRuby. (n.d.). String Case Conversion. Retrieved August 30, 2025 From
  https://crackedruby.com/learn-ruby/string-case-conversion
#### java
- w3schools. (n.d.). Java String toLowerCase() Method. Retrieved August 30, 2025 From
  https://www.w3schools.com/java/ref_string_tolowercase.asp
- w3schools. (n.d.). Java String toUpperCase() Method. Retrieved August 30, 2025 From
  https://www.w3schools.com/java/ref_string_touppercase.asp
- baeldung. (June 6, 2024). Capitalize the First Letter of a String in Java. Retrieved August 30, 2025 From
  https://www.baeldung.com/java-string-uppercase-first-letter
- how.dev. (n.d.). What is StringUtils.swapCase in Java?. Retrieved August 30, 2025 From
  https://how.dev/answers/what-is-stringutilsswapcase-in-java
#### Python
- analyticsvidhya(27 May, 2025). Case Conversion in Python: Upper(), Lower() & Swapcase(). Retrieved August 30, 2025 From
  https://www.analyticsvidhya.com/blog/2024/01/case-conversion-in-python-upper-lower-swapcase/
#### C
- tutorialgateway(n.d.). C program to Convert String to Lowercase. Retrieved August 30, 2025 From
  https://www.tutorialgateway.org/c-program-to-convert-string-to-lowercase/
- tutorialgateway(n.d.). C Program to Convert Character to Uppercase. Retrieved August 30, 2025 From
  https://www.tutorialgateway.org/c-program-to-convert-character-to-uppercase/
