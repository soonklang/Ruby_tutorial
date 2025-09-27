# Accessing String Elements
ใน Ruby เราสามารถเข้าถึงสตริง(string) ได้ โดยใช้เมธอด(method) [] ของคลาส(class) String โดยการใช้งานของเมธอด(method) [] มีดังนี้

## 1. string[substring]
ใส่สตริงย่อย(substring) ลงในเมธอด[] เพื่อหาสตริงย่อยในสตริงนั้นๆ และทำการหั่น(slice)🔪สตริงย่อยนั้นออกมา

- พบ ✅ => คืนค่า(return)สตริงย่อยนั้น

- ไม่พบ ❌ => nil

> Example 1. ในภาษา Ruby:

    myString = "Hello World"

    p myString["Hello"]  # "Hello" 

    p myString["Planet"]  # nil

🎉 เราไม่จำเป็นต้องแทนค่า myString = "Hello World" ก็ได้ ใช้ "Hello World" ได้เลย
    
    p "Hello World"["Hello"]  # "Hello" 

    p "Hello World"["Planet"]  # nil
    
ในภาษา C เราสามารถหาสตริงย่อยได้ โดยใช้ฟังก์ชันจาก <string.h> คือ strstr(char * str, char * substring) โดยที่

- char * str -> สตริงที่ถูกค้นหา

- char * substring -> สตริงย่อยที่ต้องการค้นหา

คืนค่าเป็น

- พบ ✅ => คืนค่าเป็นpointer(พอยน์เตอร์) ไปยังตำแหน่งแรกของสตริงย่อยที่ระบุในสตริง

- ไม่พบ ❌ => NULL

> Example 1. ในภาษา C:

    #include <stdio.h>
    #include <string.h>

    int main () {
        char myString[11] = "Hello world";
        char subString1[6] = "Hello"; // [5+1] เพิ่มช่องให้ null terminator
        char subString2[7] = "Planet"; // [6+1] เพิ่มช่องให้ null terminator
        
        if (strstr(myString, subString1) != NULL) {
            printf("%s", subString1);
        }
        else {
            printf("not found");
        }
        // Hello
        
        if (strstr(myString, subString2) != NULL) {
            printf("%s\n", subString2);
        }
        else {
            printf("not found");
        // not found
        }
        return 0;
    }
    
ในภาษา Java เราสามารถหาสตริงย่อยได้ โดยใช้เมธอด boolean String.contains(CharSequence chars) โดยที่ CharSequence chars -> อักขระที่ต้องการหา คืนค่าเป็น

- พบ ✅ => true

- ไม่พบ ❌ => false

> Example 1. ในภาษา Java:

    String myString = "Hello World";

    if (myString.contains("Hello")) {
        System.out.println("Hello");
    } 
    else {
        System.out.println("not found");
    }
    // Hello
        
    if (myString.contains("Planet")) {
        System.out.println("Planet");
    } 
    else {
        System.out.println("not found");
    }
    // not found

ในภาษา Python เราสามารถหาสตริงย่อยได้ โดยใช้คำสั่ง if-else คืนค่าเป็น

- พบ ✅ => true

- ไม่พบ ❌ => false

> Example 1. ในภาษา Python:

    myString = "Hello World"

    if "Hello" in myString:
        print("Hello")
    else:
        print("not found")
    # Hello
    
    if "Planet" in myString:
        print("Planet")
    else:
        print("not found")
    # not found
    
## 2. string[index] 

ใส่ค่าจำนวนเต็ม(integer) ลงในเมธอด[] และทำการหั่นอักขระตำแหน่งนั้นในสตริงออกมา

❗ หากไม่มีค่าใดในตำแหน่งที่ระบุ => nil

> Example 2.1 ในภาษา Ruby:

    myString = "Hello World"
    
    p myString[3]  # "l"
    
    p myString[6]  # :"W"
    
    p myString[20]  # nil
    
ถ้าเราใส่ค่าจำนวนเต็มลบ(negative integer) ลงในเมธอด[] จะเป็นการนับถอยหลังจากอักขระตัวสุดท้ายของสตริง

> Example 2.2 ในภาษา Ruby:

    p myString[-3]  # "r"

    p myString[-7]  #  "o"

    p myString[-20]  # nil

ในภาษา C เราสามารถหั่นอักขระออกมาได้ โดยการใช้ตัวแปร(variable) ที่มีชนิดข้อมูลเป็นอักขระ(character/ char) จากคุณสมบัติของอักขระที่รวมกันเป็นสตริง และสามารถมองอักขระแต่ละตัวเป็นอาเรย์(array) แต่ละช่องได้

> Example 2. ในภาษา C:

    #include <stdio.h>

    void main()  {
        char myString[] = "Hello World";
    
        printf("%c\n", myString[0]); // H

        printf("%c\n", myString[6]); // W
    }

ในภาษา Java เราสามารถหั่นอักขระออกมาได้ โดยการใช้เมธอด charAt(int index) โดยที่ int index -> ตำแหน่งอักขระที่ต้องการ

> Example 2. ในภาษา Java:

    String myString = "Hello World";
    
    System.out.println(myString.charAt(0)); // H

    System.out.println(myString.charAt(6)); // W

ในภาษา Python เราสามารถหั่นอักขระออกมาได้ โดยใช้วิธีเดียวกันกับภาษา C ได้ แต่ไม่ต้องกำหนดชนิดข้อมูลให้กับตัวแปร

> Example 2.1 ในภาษา Python:

    myString = "Hello World"
    
    print(myString[0]) # H
    
    print(myString[6]) # W

❗ แต่ในภาษา Python เราสามารถใส่ค่าจำนวนเต็มลบลงไปได้ โดยจะนับถอยหลังจากอักขระตัวสุดท้ายของสตริง

> Example 2.2 ในภาษา Python

    myString = "Hello World"
    
    print(myString[-11]) # H
    
    print(myString[-5]) # W

## 3. string[start, length]

เราสามารถกำหนดอักขระเริ่มต้น(start) และความยาว(length)📏โดยการใส่ค่าจำนวนเต็ม เพื่อหั่นสตริงย่อยในสตริงนั้นๆออกมา

> Example 3.1 ในภาษา Ruby:

    myString = "Hello World"
    
    p myString[0, 5]  # "Hello"
    
    p myString[6, 5]  # "World"
    
    p myString[2, 0]  # "" => ความยาวเท่ากับ 0 ❗
   
    p myString[6,200]  # "World" => ความยาวที่ต้องการหั่นมากกว่าความยาวของสตริง ❗
    
    p myString[11, 4]  # nil => อักขระเริ่มต้นมากกว่าความยาวของสตริง ❗

 กรณีพิเศษ✨: หากใส่ค่าจำนวนเต็มเริ่มต้นเท่ากับความยาวของสตริง การหั่นจะเป็นการเพิ่มช่องว่างขึ้นมาใหม่

> Example 3.2 ในภาษา Ruby:

    p myString[10, 2]  # ""
    
    p myString[10, 200]  # ""
    
เมื่อเราใส่ค่าจำนวนเต็มลบลงในจุดเริ่มต้น และความยาวไม่เป็นจำนวนเต็มลบ จะเป็นการกำหนดอักขระเริ่มต้นเป็นอักขระตัวสุดท้ายของสตริง และนับต่อไปข้างหน้าตามความยาวที่กำหนด
 
> Example 3.3 ในภาษา Ruby:

    p myString[-5, 5]  # "World"
    
    p myString[-11, 5]  # "Hello"
    
    p myString[-12, 5]  # nil => อักขระเริ่มต้นมากกว่าความยาวของสตริง ❗

❗ แต่ถ้าเราใส่ค่าจำนวนเต็มลบลงในความยาว จะไม่มีการหั่น

> Example 3.4 ในภาษา Ruby:

    p myString[0, -5]  # nil

    p myString[-12, -5]  # nil

ในภาษา C เราสามารถหั่นสตริงย่อยออกมาได้ โดยการใช้ฟังก์ชัน strncpy(dest, src, n) โดยที่ 

- dest -> สตริงย่อยที่ต้องการจะคัดลอก

- src -> สตริงที่ถูกคัดลอก

- n -> จำนวนอักขระที่จะคัดลอกจากสตริง

> Example 3. ในภาษา C:

    #include <stdio.h>
    #include <string.h>
    
    int main() {
       char myString[] = "Hello World";
       
       char subString[10]; 
       
       strncpy(myString, subString , 5); 
    
       printf(%s\n", subString); // Hello
       
       strncpy(myString, subString + 5 , 6);

       printf(%s\n", subString); // World
       
       return 0;
    }

ในภาษา Java เราสามารถหั่นสตริงย่อยออกมาได้ โดยการใช้เมธอด substring(int start, int end) โดยที่

- int start -> ตำแหน่งอักขระเริ่มต้นของสตริงย่อยที่ต้องการหั่น(เริ่มต้นจาก 0)

- int end -> ตำแหน่งอักขระสุดท้ายของสตริงย่อยที่ต้องการหั่น + 1(เริ่มต้นจาก 1)

> Example 3. ในภาษา Java:

    String myString = "Hello World";
    
    System.out.println(myString.substring(0, 5)); # Hello

    System.out.println(myString.substring(6, 11)); # World

ในภาษา Python เราสามารถหั่นสตริงย่อยออกมาได้ โดยการใช้ myString[start:end] หรือการหั่น

-  start -> ตำแหน่งอักขระเริ่มต้นของสตริงย่อยที่ต้องการหั่น หากไม่มีจะเป็นการเริ่มต้นที่อักขระตัวแรกของสตริง(เริ่มต้นจาก 0)

-  end -> ตำแหน่งอักขระตัวสุดท้ายของสตริงย่อยที่ต้องการหั่น หากไม่มีจะเป็นการสิ้นสุดที่อักขระตัวสุดท้ายของสตริง + (เริ่มต้นจาก 1)

❗ หากไม่มีทั้ง start และ end จะเป็นการเริ่มต้นที่อักขระตัวแรก และสิ้นสุดที่อักขระตัวสุดท้ายของสตริง

> Example 4. ในภาษา Python:

    myString = "Hello World"

    print(myString[0:5]) # Hello
    
    print(myString[:5]) # Hello

    print(myString[6:]

    print(myString[6:11]) # World

    print(myString[:11]) # Hello World

    print(myString[:]) # Hello World

❗ start และ end สามารถใส่ค่าจำนวนเต็มลบลงไปได้ โดยจะนับถอยหลังจากอักขระตัวสุดท้ายของสตริง 

    print(myString[-11:-6]) # Hello

    print(myString[-5:11]) # World

    print(myString[-11:11]) # Hello World

## 4. string[range]
เราสามารถกำหนดช่วง เพื่อระบุกลุ่มอักขระระหว่างอักขระเริ่มต้นและอักขระสุดท้าย จากนั้นหั่นกลุ่มอักขระนั้น

> Example 4. ในภาษา Ruby:

    myString = "Hello World"

    p myString[0..4] # "Hello"
    p myString[0, 5] # "Hello"

    p myString[ุ6..9] # "World"
    p myString[6, 5] # "World"

    p myString[ุ10..20] # "World"
    p myString[10, 5] # "World"

🎉 ในภาษา C, Java และ Python เราสามารถหั่นสตริงย่อยในช่วงที่กำหนดได้ โดยใช้วิธีการเดียวกันกับข้อ 3. ที่ได้ยกตัวอย่างไป

## string.index(substring)

หาตำแหน่งของสตริงย่อย คืนค่าเป็นจำนวนเต็ม

> Example ในภาษา Ruby:

    myString = "Hello World"

    p myString.index('H') # 0
    
    p myString.index("Hello") # 0 #นับตำแหน่งแรกที่เจอ ❗

    p myString.index('W') # 6

    p myString.index('W') # 6

    p myString.index("lll") # nil 

ในภาษา C เราสามารถหาตำแหน่งของสตริงย่อย โดยการใช้ฟังก์ชัน strstr(char * str, char * substring)

> Example ในภาษา C:

    #include <stdio.h>
    #include <string.h>
    
    int main() {
        char myString[] = "Hello World";
        char *subString1 = "Hello";
        char *subString2 = "World";
        char *subString3 = "Planet";
        char *found1 = strstr(myString, subString1);
        char *found2 = strstr(myString, subString2);
        char *found3 = strstr(myString, subString3);
        
        if (found1) {
            int index = found1 - myString;
            printf("%d\n", index);
        } else {
            printf("not found");
        }
        // 0

        if (found2) {
            int index = found2 - myString;
            printf("%d\n", index);
        } else {
            printf("not found");
        }
        // 6
        
        if (found3) {
            int index = found3 - myString;
            printf("%d\n", index);
        } else {
            printf("not found");
        }
        // not found
        
        return 0;
    }

ในภาษา Java เราสามารถหาตำแหน่งของสตริงย่อย โดยการใช้เมธอด indexOf(String str) โดยที่ String str -> สตริงย่อยที่ต้องการค้นหา

> Example ในภาษา Java:

    String myString = "Hello World";
    
    System.out.println(myString.indexOf("Hello")); // 0

    System.out.println(myString.indexOf("World")); // 6

    System.out.println(myString.indexOf("Planet")); // -1 => ไม่พบสตริงย่อยที่ต้องการค้นหา ❗

ในภาษา Python เราสามารถหาตำแหน่งของสตริงย่อย โดยการใช้เมธอด find(value) โดยที่ value -> สตริงที่ต้องการค้นหา

> Example ในภาษา Python:

    myString = "Hello World."

    print(myString.find("Hello")) # 0
    
    print(myString.find("World")) # 6

    print(myString.find("Planet")) # -1 => ไม่พบสตริงย่อยที่ต้องการค้นหา ❗

# Presentation
- [Slide](https://drive.google.com/file/d/1AbB4EZ6pwx-zq9nyrjlKmHbxUumg0Lpe/view?usp=drive_link)

- [Video](https://youtu.be/NA81ocQvxh0?feature=shared)

## อ้างอิง

> Ruby

- Techotopia (27 ตุลาคม 2559), Ruby String Concatenation and Comparison, สืบค้นเมื่อ 1 กันยายน 2568, จาก https://www.techotopia.com/index.php/Ruby_String_Concatenation_and_Comparison#Accessing_String_Elements

- Ruby-Doc (ม.ป.ป.) , class String (Ruby ver 3.4.1), สืบค้นเมื่อ 1 กันยายน 2568, จาก https://ruby-doc.org/3.4.1/String.html

- APIdock (ม.ป.ป.) , slice (Ruby ver 2.6.3), สืบค้นเมื่อ 1 กันยายน 2568, จาก https://apidock.com/ruby/v2_6_3/String/slice

> C

- tutorialspoint (ม.ป.ป.), C library - strstr() function, สืบค้นเมื่อ 1 กันยายน 2568, จาก https://www.tutorialspoint.com/c_standard_library/c_function_strstr.htm

- cplusplus (ม.ป.ป.), Character sequences, สืบค้นเมื่อ 1 กันยายน 2568, จาก https://cplusplus.com/doc/tutorial/ntcs/

- tutorialspoint (ม.ป.ป.), C library - strncpy() function, สืบค้นเมื่อ 1 กันยายน 2568, จาก https://www.tutorialspoint.com/c_standard_library/c_function_strncpy.htm

- cppreference (ม.ป.ป.), strstr, สืบค้นเมื่อ 1 กันยายน 2568, จาก https://en.cppreference.com/w/c/string/byte/strstr

> Java

- GeeksForGeeks (11 กรกฎาคม 2568), Java String contains() Method with Example, สืบค้นเมื่อ 1 กันยายน 2568, จาก
https://www.geeksforgeeks.org/java/java-string-contains-method-example/

- W3Schools (ม.ป.ป.), Java String charAt() Method, สืบค้นเมื่อ 1 กันยายน 2568, จาก https://www.w3schools.com/java/ref_string_charat.asp

- W3Schools (ม.ป.ป.), Java String substring() Method, สืบค้นเมื่อ 1 กันยายน 2568, จาก https://www.w3schools.com/java/ref_string_substring.asp

- W3Schools (ม.ป.ป.), Java String indexOf() Method, สืบค้นเมื่อ 1 กันยายน 2568, จาก https://www.w3schools.com/java/ref_string_indexof.asp

> Python

- GeeksForGeeks (20 มิถุนายน 2567), Check if String Contains Substring in Python, สืบค้นเมื่อ 1 กันยายน 2568, จาก
https://www.geeksforgeeks.org/python/check-if-string-contains-substring-in-python/

- Python documentation (31 สิงหาคม 2568), Text Sequence Type — str, สืบค้นเมื่อ 1 กันยายน 2568, จาก https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str

- Python documentation (31 สิงหาคม 2568), Common Sequence Operations, สืบค้นเมื่อ 1 กันยายน 2568, จาก https://docs.python.org/3/library/stdtypes.html#typesseq-common

- W3Schools (ม.ป.ป.), Python String find() Method, สืบค้นเมื่อ 1 กันยายน 2568, จาก https://www.w3schools.com/python/ref_string_find.asp
