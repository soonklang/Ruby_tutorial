# Ruby String Conversion

## String Conversion คืออะไรใน Ruby

String Conversion คือการเปลี่ยนค่าข้อมูลจากชนิด `String` ไปเป็นชนิดข้อมูลอื่น เช่น `Integer`, `Float`, `Symbol` หรือแปลงกลับจากข้อมูลชนิดอื่นกลับมาเป็น `String` อีกครั้ง สิ่งนี้มีประโยชน์ในการคำนวณ, การจัดการ input/output และการทำงานร่วมกับ library ต่างๆ





## การแปลง String เป็น Integer

การแปลงค่าชนิดข้อมูลจาก String เป็น Integer จะทำการแปลงค่าตัวเลขใน String จนกว่าจะครบหรือพบตัวอักษรก็จำหยุดทำงาน หรือถ้า String ตัวแรกไม่ใช้ตัวแรกก็จะคืนค่า 0

**ตัวอย่างการทำงาน**

```
puts "123".to_i
#Output >>> 123
```


**ตัวอย่างการทำงานเมื่อตรวจพบตัวอักษร**
```
puts "321-cba".to_i
#Output >>> 321
```
**ตัวอย่างการทำงานเมื่อพบตัวอักษรตัวแรก**
```
puts "banana".to_i
#Output >>> 0
```



## การแปลง String เป็น Float
การแปลงค่าชนิดข้อมูลจาก String เป็น Float จะมีลักษณะการทำงานเหมือนกับ Integer โดยจะแปลงจากซ้ายไปขวาจนกว่าจะครบ String หรือ เจอตัวอักษร และจะคืนค่า 0 เมื่อ String เริ่มต้นด้วยตัวอักษร

**ตัวอย่างการทำงาน**

```
puts "123.45".to_f
#Output >>> 123.45
```

**ตัวอย่างการทำงานเมื่อตรวจพบตัวอักษร**
```
puts "123-abc".to_f
#Output >>> 123.0
```
**ตัวอย่างการทำงานเมื่อพบตัวอักษรตัวแรก**
```
puts "hello man".to_f
#Output >>> 0.0
```


## การแปลงข้อมูลชนิดอื่นๆเป็น String
เป็นการนำข้อมูลชนิดอื่นๆมาแปลงข้อมูลให้อยู่ในรูปแบบ String ทำให้สามารถนำไปต่อกับข้อความได้ง่าย และ สามารถใช้ได้กับทุก object ใน Ruby

**ตัวอย่างการทำงาน**


```
puts 888.to_s
#Output >>> "888"

puts 1.4.to_s
#Output >>> "1.4"


puts :hello.to_s
#Output >>> "hello"
```



## การแปลง String เป็น Symbol
ใช้ในการแปลง String เป็น Symbol เหมาะกับการใช้งานเป็น key ของ hash

**ตัวอย่างการทำงาน**

```
puts "ruby".to_sym
#Output >>> :ruby
```



## การแปลงเลขฐาน

Ruby สามารถแปลงเลขฐานจากคำสั่งก่อนหน้าได้คือ  `to_i(base)` และ `to_s(base)`


`to_i(base)` ใช้แปลงข้อมูลชนิด String เป็น Integer โดยแปลง String ที่เป็นเลขฐาน n ให้เป็นจำนวนเต็ม โดยต้องกำหนดว่า String เป็นเลขฐานอะไรในวงเล็บ
```
puts "1000".to_i(2)  
#Output >>> 8   
```
`to_s(base)` ใช้แปลงข้อมูลชนิด Integer เป็น String โดยแปลงจำนวนเต็มให้เป็น String ในเลขฐาน n โดยกำหนดเลขฐานที่ต้องการแปลงในวงเล็บ
```
puts 10.to_s(2)
#Output >>> "1010" 
```



# เปรียบเทียบกับภาษาอื่น


ในภาษาที่นำมาเปรียบเทียบจำมีหลักการทำงานคล้ายภาษา Ruby แต่จะไม่มี method ในการแปลง Symbol แบบ Ruby

## C Language

หลักการทำงานคล้ายกับ Ruby คือทำงานจากซ้ายไปขวาและจะหยุดทำงานเมื่อทำจนหมดหรือเจอตัวอักษร และจำคืนค่า 0 เมื่อแปลง String ที่เริ่มต้นด้วยตัวอักษรแทนตัวเลข

**ตัวอย่างการแปลง Integer , Float , การแปลงข้อมูลชนิดอื่นๆเป็น String และการแปลงเลขฐาน**

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    printf("%d\n", atoi("123abc"));  // String -> Integer

    printf("%f\n", atof("456.7xyz"));  // String -> Float

    char A[20];
    sprintf(A, "%d", 789);  // Integer → String
    printf("%s\n", A);      

    return 0;
}

```

```
#Output >>> 123
            456.700000
            "789"

```



## JAVA

หลักการทำงานคือ ถ้าแปลง String -> Integer ใน String ต้องเป็นตัวเลขเท่านั้นถ้ามีตัวอักษรจะ error ทันที

**ตัวอย่างการแปลง Integer , Float , การแปลงข้อมูลชนิดอื่นๆเป็น String และการแปลงเลขฐาน**

```
public class Main {
    public static void main(String[] args) {
        
        System.out.println(Integer.parseInt("444"));   // String → Integer
        

        System.out.println(Float.parseFloat("555"));    // String → Float
        

        System.out.println(Integer.toString("666"));    // toString
        

    }
}

```

```
#Output >>> 444
            555.0
            "666"

```

## Python

การแปลง String เป็นตัวเลขใน String ต้องเป็นตัวเลขล้วนถ้ามีตัวอักษรจะ error (สามารถมี + - ข้างหน้าตัวเลขได้)

**ตัวอย่างการแปลง Integer , Float , การแปลงข้อมูลชนิดอื่นๆเป็น String และการแปลงเลขฐาน**

```
print(int("8087"))     # String → Integer


print(float("7074.555"))   # String → Float      


print(str(6958.777))     # Float → String

```

```
#Output >>> 8087
            7074.555
            "6958.777"

```

## Video Presentation
[Video Presentation](https://youtu.be/sNGsL6AeTmI)


## Slide

[Slide Presentation](https://drive.google.com/file/d/1q4-v0lnMrz15712QdQOJa0TuWY8ixM82/view?usp=sharing)





## Reference

### RUBY

GeeksforGeeks. (2025, July 12). *Ruby Integer to_s(base) function with example*. Retrieved from https://www.geeksforgeeks.org/ruby/ruby-integer-to_s-function-with-example/  

APIdock. (n.d.). *Ruby String to_i(base)*. APIdock release: IRON STEVE (1.4), copyright 2008–2025. Retrieved from https://apidock.com/ruby/String/to_i  


Centron. (n.d.). *How to convert data types in Ruby*. Retrieved from https://www.centron.de/en/tutorial/how-to-convert-data-types-in-ruby/  

Techotopia. (n.d.). *Ruby string conversions*. Retrieved from https://www.techotopia.com/index.php/Ruby_String_Conversions  

Bansal, V. (2023, August 1). Ruby to_s Function. Scaler Topics. Retrieved from https://www.scaler.com/topics/ruby-to_s/

Bansal, V. (2023, November 6). Ruby to_i Method. Scaler Topics. Retrieved from https://www.scaler.com/topics/ruby-to-i/ 

APIdock. (n.d.). to_f (String). In APIdock – Ruby v2.5.5 documentation. Retrieved from https://apidock.com/ruby/v2_5_5/String/to_f

### C Language

GeeksforGeeks. (n.d.). How to convert an integer to a string in C? GeeksforGeeks. Retrieved September 2, 2025, from https://www.geeksforgeeks.org/c/how-to-convert-an-integer-to-a-string-in-c/

Sanfoundry. (n.d.). Different string conversion functions in C standard library. Sanfoundry. Retrieved September 2, 2025, from https://www.sanfoundry.com/c-tutorials-different-string-conversion-functions-standard-library/

### JAVA

Alexander, A. (n.d.). Java FAQ: Convert String to integer, float. Alvinalexander.com. Retrieved September 2, 2025, from https://alvinalexander.com/blog/post/java/java-faq-convert-string-integer-float/#:~:text=Short%20answer:%20You%20want%20to%20use%20the%20Integer.parseInt(),String%20s%20=%20%225%22;%20int%20i%20=%20Integer.parseInt(s)
;

GeeksforGeeks. (n.d.). Different ways for integer to string conversions in Java. GeeksforGeeks. Retrieved September 2, 2025, from https://www.geeksforgeeks.org/java/different-ways-for-integer-to-string-conversions-in-java/

Codementor. (n.d.). Java String: A beginner-friendly tutorial. Codementor. Retrieved September 2, 2025, from https://www.codementor.io/blog/java-string-cj3j4tddhj#:~:text=In%20this%20beginner-friendly%20tutorial,%20we%E2%80%99ll%20walk%20through%20some,char%20to%20String,%20and%20Java%20array%20to%20String.\


### Python

Nkmk. (2018, October 3). Convert between string and number in Python. Note.nkmk.me. Retrieved September 2, 2025, from https://note.nkmk.me/en/python-str-num-conversion/





