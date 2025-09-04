# Inserting Text Into a Ruby String
การแทรกข้อความเพิ่มลงใน string ในภาษา Ruby

**ในภาษา Ruby สามารถแทรกข้อความเพิ่มได้โดยการใช้ method ที่ชื่อว่า "insert"**

method insert เป็น method ของคลาส String ในภาษา Ruby ซึ่งใช้สำหรับแทรกข้อความใหม่ลงใน string ตรงตำแหน่งที่ต้องการ

## Syntax

```ruby
str.insert(index, other_str) 
```

<kbd>str</kbd> คือ string เดิม&#x20;

<kbd>index</kbd>  คือ ตำแหน่งที่ต้องการจะแทรก&#x20;

&#x20;      แบ่งออกเป็น 2 กรณี&#x20;

&#x20;            \- <kbd>index</kbd> เป็น **จำนวนเต็มบวก** จะเริ่มแทรกจากด้านหน้าของ string&#x20;

&#x20;            \- <kbd>index</kbd> เป็น **จำนวนเต็มลบ** จะนับตำแหน่งถอยหลังจากด้านท้ายของ string&#x20;

<kbd>other\_str</kbd> คือ ข้อความที่ต้องการจะแทรกเข้าไป&#x20;

## Example

**Example 1 :** กรณี index เป็น**จำนวนเต็มบวก**&#x20;

```ruby
str = "Helloworld" 
str.insert(5, "my") 
```

**Output :**&#x20;

```ruby
Hellomyworld 
```

**Example 2 :** กรณี index เป็น**จำนวนเต็มลบ**

```ruby
str = "Helloworld" 
str.insert(-2, "my") 
```

**Output :**&#x20;

```ruby
Hellowormyld  
```

***

## เปรียบเทียบกับภาษา C / Java / Python

## ภาษา C

เนื่องจากภาษา C ไม่มี method insert() โดยตรงจึงต้องสร้าง method ในการแทรกข้อความขึ้นเอง

**Example :**

```c
#include <stdio.h>
#include <string.h>

void insertString(char *str, const char *insert, int index) {
    int lenStr = strlen(str);
    int lenInsert = strlen(insert);
    
    memmove(str + index + lenInsert, str + index, lenStr - index + 1);

    memcpy(str + index, insert, lenInsert);
}

int main() {
    char str[50] = "Helloworld";
    char insert[] = "my";
    int index = 5;

    insertString(str, insert, index);
    printf("%s\n", str);

    return 0;
}

```

**Output :**&#x20;

```c
Hellomyworld
```

## ภาษา Java

เนื่องจาก String ในภาษา Java **ไม่สามารถเปลี่ยนค่าได้โดยตรง** จึงต้องใช้method insert() ของ class <kbd>StringBuffer</kbd>  ใน Java ซึ่งเป็นคลาสที่ใช้จัดการกับ String ที่สามารถแก้ไขได้โดยไม่จำเป็นต้องสร้าง object ใหม่ทุกครั้ง

**Syntax**

```java
StringBuffer.insert(int Position, String str)
```

&#x20;**Example:**

```java
public class Main {
    public static void main(String[] args) {
        StringBuffer str = new StringBuffer("Helloworld");
        str.insert(5, "my");
        System.out.println(str);
    }
}
```

**Output :**&#x20;

```java
Hellomyworld 
```

## ภาษา Python

เนื่องจาก String ในภาษา  Python **ไม่สามารถเปลี่ยนค่าได้โดยตรง ไม่มี method insert() เหมือนกับ Ruby** แต่สามารถทำได้โดยการตัด string แล้วต่อกลับเข้าด้วยกัน

**Syntax**

```java
new_str = str[:index] + insert_text + str[index:]
```

<kbd>str\[:index]</kbd> คือ การตัด string **ตั้งแต่ตัวแรก ถึง ตำแหน่งก่อนหน้า index** (\* ไม่รวมตำแหน่ง index)\
<kbd>insert\_text</kbd> คือ ข้อความที่ต้องการแทรกเข้าไปใน string

<kbd>str\[index:]</kbd> คือ การตัดstring **ตั้งแต่ตำแหน่ง index ถึง ตัวสุดท้าย**

**Example:**

```python
str = "Helloworld"
index = 5
insert_text = "my"

new_str = str[:index] + insert_text + str[index:]
print(new_str) 
```

**Output :**&#x20;

```python
Hellomyworld 
```

***

## References

**Ruby**

Techotopia. (n.d.). _Ruby String Replacement, Substitution and Insertion: Inserting Text into a Ruby String_. Techotopia. สืบค้นเมื่อ 1 กันยายน 2025, จาก [https://www.techotopia.com/index.php/Ruby\_String\_Replacement,\_Substitution\_and\_Insertion#Inserting\_Text\_into\_a\_Ruby\_String](https://www.techotopia.com/index.php/Ruby_String_Replacement,_Substitution_and_Insertion?utm_source=chatgpt.com#Inserting_Text_into_a_Ruby_String)

GeeksforGeeks. (n.d.). _Ruby String insert method_. GeeksforGeeks. สืบค้นเมื่อ 1 กันยายน 2025, จาก [https://www.geeksforgeeks.org/ruby/ruby-string-insert-method/](https://www.geeksforgeeks.org/ruby/ruby-string-insert-method/?utm_source=chatgpt.com)

Ruby Documentation. (2025). _String#insert (Ruby 3.3.6)_. สืบค้นเมื่อ 1 กันยายน 2025, จาก [https://ruby-doc.org/3.3.6/String.html#method-i-insert](https://ruby-doc.org/3.3.6/String.html?utm_source=chatgpt.com#method-i-insert)

**Others**

GeeksforGeeks. (2025, July 12). _How to append a character to a string in C?_ GeeksforGeeks. สืบค้นเมื่อ 1 กันยายน 2025, จาก [https://www.geeksforgeeks.org/c/how-to-append-a-character-to-a-string-in-c/](https://www.geeksforgeeks.org/c/how-to-append-a-character-to-a-string-in-c/?utm_source=chatgpt.com)

FromDev. (2025, December). _Using memmove for string manipulation_. FromDev. สืบค้นเมื่อ 1 กันยายน 2025, จาก [https://www.fromdev.com/2025/12/using-memmove-for-string-manipulation.html](https://www.fromdev.com/2025/12/using-memmove-for-string-manipulation.html?utm_source=chatgpt.com)

GeeksforGeeks. (2025, July 23). _Java program to add characters to a string_. GeeksforGeeks. สืบค้นเมื่อ 1 กันยายน 2025, จาก [https://www.geeksforgeeks.org/java/java-program-to-add-characters-to-a-string/](https://www.geeksforgeeks.org/java/java-program-to-add-characters-to-a-string/?utm_source=chatgpt.com)

GeeksforGeeks. (2025, July 23). _Insert a variable into a string - Python_. GeeksforGeeks. สืบค้นเมื่อ 1 กันยายน 2025, จาก [https://www.geeksforgeeks.org/python/insert-a-variable-into-a-string-python/](https://www.geeksforgeeks.org/python/insert-a-variable-into-a-string-python/?utm_source=chatgpt.com)

***

## Slides
