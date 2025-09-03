# Ruby Bitwise Operators
## เนื้อหา

ในภาษา Ruby สามารถจะดำเนินการทางบิตของตัวเลข Integer ได้ โดยมี Operator ดังนี้

```
& (AND)
| (OR)
^ (XOR)
<< (Left Shift)
>> (Right Shift)
~ (One's Complement)
```

และสามารถเขียนรูปย่อได้

```
&= (AND)
|= (OR)
^= (XOR)
<<= (Left Shift)
>>= (Right Shift)
```


- สามารถใช้กับเลขฐาน 10 ได้ โดย Interpreter จะแปลงให้เป็นเลขฐาน 2 ก่อนแล้วค่อยเอามาดำเนินการ  
- int เมื่อแปลงเป็นฐาน 2 จะเป็น signed bit  
- สามารถเขียนเลขฐาน 2 ได้โดย format นี้ `0bxxxx` (x คือ ตัวเลข 0 หรือ 1)  
- การแสดง output ให้เป็นเลขฐาน 2 หลังดำเนินการเสร็จแล้ว ต้องใช้ sprintf method เช่น 
`sprintf('%b', 4)  # 100`

## ตัวอย่าง

```Ruby
x = 0b0101
y = 0b0110


puts sprintf("%08b", x & y)   # 00000100
puts sprintf("%08b", x | y)   # 00000111
puts sprintf("%08b", x ^ y)   # 00000011
puts sprintf("%08b", ~x)  	  # ..111010 
puts sprintf("%08b", x >> 2)  # 00000001
puts sprintf("%08b", y << 2)  # 00011000 
```
`..111010` เป็นการแสดงถึงว่ามีเลข 1 อยู่ข้างหน้าอีกเยอะ แต่ว่าเราสามารถทำ Two’s Complement ปกติได้เลย แล้วจะได้ค่าเลขที่เป็นลบมา

### ตัวอย่างเปรียบเทียบ Ruby / Java / C / Python

```Java
public class Main {
    public static void main(String[] args) {
        int x = 0b0101;
        int y = 0b0110;

        System.out.println(Integer.toBinaryString(x & y));   	// 100
        System.out.println(Integer.toBinaryString(x | y));   	// 111
        System.out.println(Integer.toBinaryString(x ^ y));   	// 11
        System.out.println(Integer.toBinaryString(~x));   		// 11111111111111111111111111111010
        System.out.println(Integer.toBinaryString(y << 2));  	// 1100
        System.out.println(Integer.toBinaryString(x >> 2)); 	// 1

		x = 0b11111111111111111111111111111000; 
		System.out.println(Integer.toBinaryString(x >>> 2)); 	// 111111111111111111111111111110
		System.out.println(Integer.toBinaryString(x >> 2)); 	// 11111111111111111111111111111110
    }
}
```
`Java` มี bitwise operator เพิ่มมา 1 ตัว คือ >>> (Unsigned Right Shift)
เวลาทำงานกับ signed bit จะเติมศูนย์เข้ามาแทน 1

```C
#include <stdio.h>

int main() {
    int x = 0b0101;
    int y = 0b0110; 

    printf("%d\n", x & y);   // 4
    printf("%d\n", x | y);   // 7
    printf("%d\n", x ^ y);   // 3
    printf("%d\n", ~x);   // -6
    printf("%d\n", x >> 2);  // 2
    printf("%d\n", y << 2);  // 12
    return 0;
}
```
`C` มี bitwise operator เหมือนกัน แต่ว่าไม่มี method built-in สำหรับแสดงผลเป็น binary แบบเดียวกันกับภาษาอื่นๆ

```Python
x = 0b0101 
y = 0b0110

print(f"{x & y:08b}")   # 00000100
print(f"{x | y:08b}")   # 00000111
print(f"{x ^ y:08b}")   # 00000011
print(f"{~x:08b}")  	# -0000110
print(f"{x >> 2:08b}")  # 00000001
print(f"{y << 2:08b}")  # 00011000
```
`Python` มี bitwise operator เหมือนกัน

## แหล่งที่มาอ้างอิง
- https://www.techotopia.com/index.php/Ruby_Operators#Ruby_Bitwise_Operators
- https://docs.ruby-lang.org/en/3.4/Integer.html#method-i-26
- https://docs.ruby-lang.org/en/master/format_specifications_rdoc.html#label-Format+Specifications

### แหล่งที่มาอ้างอิงภาษาอื่นๆ

- https://docs.oracle.com/javase/tutorial/java/nutsandbolts/op3.html
- https://learn.microsoft.com/en-us/cpp/c-language/c-bitwise-operators?view=msvc-160
- https://docs.python.org/3/library/stdtypes.html
	
## คลิปนำเสนอที่อัดพร้อมมีหน้าผู้บรรยาย

## presentation (slides)
