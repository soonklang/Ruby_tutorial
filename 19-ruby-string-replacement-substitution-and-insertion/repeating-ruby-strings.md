# Repeating Ruby Strings

การทำซ้ำของ string หลายๆครั้งจนได้จำนวนที่ต้องการ
### Ruby: 
- ทำได้โดยการใช้ `self * n -> new_string `
  
#### Example:
```ruby
 text = "Ho!"
 puts text * 3
```
#### Output:
```text
  Ho!Ho!Ho!
  ```
> ถ้าเทียบกับภาษาต่างๆ เช่น Java/C/Python
##
  
 ### Java 11+: 
 - ใช้ `repeat(n)` โดย n คือจำนวนที่ต้องการทำซ้ำถ้า n = 0 จะได้ค่า null
  
#### Example:  
  ```java
import java.io.*;

class GFG {
    public static void main (String[] args) {
      
      String string="abc";
      
      int count=3;
      
      System.out.println("String :"+string.repeat(count));

      }
}
  ```
 #### Output: 
 ```text
  abcabcabc
  ```
      
  ##
  ### C: 
  - ไม่มีฟังก์ชั่นให้ใช้แบบ Java และ Ruby แต่ทำได้โดยการใช้ `strcat()` ร่วมกับ loop ในการต่อ string เข้าด้วยกัน 
#### Example:
  ```c 
  #include <stdio.h>
  #include <string.h>

  int main() {
    char text[] = "Hi ";
    int count = 3;
    char result[100] = "";

    for (int i = 0; i < count; i++) {
      strcat(result, text);
    }

    printf("%s\n", result);
    return 0;
  }
  ```
  #### Output: 
  ```text
  Hi Hi Hi
  ```
> ต้องระวังเรื่อง ขนาดของ array ให้ใหญ่พอ ไม่งั้นจะเกิด buffer overflow
##
  ### Python:
  - สามารถใช้ `*` เหมือน Ruby ได้เลย
#### Example:
  ```python
  s = "Hello! "
  r = s * 3  
  print(r)
  ```
#### Output: 
  ```text
  Hello! Hello! Hello! 
  ```
##

### Reference:
  - Ruby-lang.org. (n.d.). String# method documentation*. Ruby-lang.org. https://docs.ruby-lang.org/en/master/String.html#method-i-2A
  - GeeksforGeeks. (2022). String class repeat() method in Java with examples. GeeksforGeeks. https://www.geeksforgeeks.org/java/string-class-repeat-method-in-java-with-examples/
  - GeeksforGeeks. (2022). strcat() in C with examples. GeeksforGeeks. https://www.geeksforgeeks.org/c/strcat-in-c/
  - GeeksforGeeks. (2022). How to repeat a string in Python. GeeksforGeeks. https://www.geeksforgeeks.org/python/how-to-repeat-a-string-in-python/

### Presentation
- Link video: https://youtu.be/8dbPTHl0muI
- PDF: https://www.canva.com/design/DAGzbUsinJs/rc0WarpUD2s8tDT-AVXh_g/edit?utm_content=DAGzbUsinJs&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton
