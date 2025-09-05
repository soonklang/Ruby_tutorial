
# Ruby String Substitution
ใช้ในปรับแต่ง string เช่น การสร้างข้อความอัตโนมัติ และ การแก้ไขข้อมูลที่ซ้ำ

## การใช้ gsub
ใช้ในการแทนที่คำหรือข้อความย่อยใน string ซึ่งเหมาะกับเวลาที่ต้องการเปลี่ยนค่าใน string

gsub(pattern, replacement) คืนค่าเป็น string ใหม่ โดยไม่เปลี่ยนค่า string เดิม


- **pattern** คือ ค่าเดิมที่ต้องการเปลี่ยน
- **replacement** คือ ค่าใหม่ที่ต้องการใส่ลงใน string
## ตัวอย่างการใช้ gsub
```ruby
myString = "Welcome to Thailand!"
=> "Welcome to Thailand!"

myString.gsub("Thailand", "Vietnam")
=> "Welcome to Vietnam!"

```
## การใช้ replace
ใช้ในการเปลี่ยน string ทั้ง string

## ตัวอย่างการใช้ replace
```ruby
myString = "Welcome to Thailand!"
=> "Welcome to Thailand!"

myString.replace "Goodbye to Vietnam!"
=> "Goodbye to Vietnam!"
```

## เปรียบเทียบกับ java / c / python
- **java**
Java ใช้เมธอด replace จากคลาส String
```
 public class Main {
    public static void main(String[] args) {
        String myString = "Welcome to Thailand!";

        // แทนที่ substring
        String newString = myString.replace("Thailand", "Vietnam");
        System.out.println(newString);
        // => "Welcome to Vietnam!"
    }
}

```

- **C**
ภาษา C ไม่มีเมธอดสำเร็จรูปสำหรับ string replacement 

เพราะ string ใน C เป็นเพียง array ของ char จึงต้องเขียนฟังก์ชันเอง
```
#include <stdio.h>
#include <string.h>

void replaceWord(char *str, const char *oldWord, const char *newWord) {
    static char buffer[100];
    char *pos;
    int oldLen = strlen(oldWord);

    if ((pos = strstr(str, oldWord)) != NULL) {
        int lenBefore = pos - str;
        strcpy(buffer, str);
        buffer[lenBefore] = '\0';

        strcat(buffer, newWord);
        strcat(buffer, pos + oldLen);

        strcpy(str, buffer);
    }
}

int main() {
    char str[100] = "Welcome to Thailand!";
    replaceWord(str, "PHP", "C");
    printf("%s\n", str);
    // => "Welcome to Vietnam!"
    return 0;
}
```

- **python**
Python ใช้เมธอด replace 
```
my_string = "Welcome to Thailand!"

new_string = my_string.replace("Thailand", "Vietnam")
print(new_string)  
=> "Welcome to Vietnam!"

print(my_string)  
=> "Welcome to Thailand!"
```

## แหล่งอ้างอิง
- **https://www.techotopia.com/index.php/Ruby_String_Replacement,_Substitution_and_Insertion#Ruby_String_Substitution**
- **https://www.geeksforgeeks.org/c/c-program-replace-word-text-another-given-word/?utm_source=chatgpt.com** 
- **https://www.w3schools.com/java/ref_string_replaceall.asp?utm_source=chatgpt.com**
- **https://www.w3schools.com/python/ref_string_replace.asp?utm_source=chatgpt.com**
