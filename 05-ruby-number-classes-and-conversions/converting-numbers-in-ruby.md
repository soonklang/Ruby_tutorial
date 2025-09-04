# Converting Numbers in Ruby

การแปลงชนิดของข้อมูลของภาษา Ruby จากชนิดหนึ่งไปอีกชนิดได้ จะต้องวใช้ Method และ รับค่าที่จะแปลงเข้าไป
ตัวอย่างต่อไปนี้เราจะมีการเปรียบเทียบกับ Java C Python

โดยการแปลงค่าของแต่ละภาษามีความแตกต่างกันอยู่นิดหน่อย คือ 
ภาษา C กับ Java จะเรียกว่า Type Casting
ภาษา Ruby จะเป็น 

# Convert Floating Point -> Integer
ในภาษาของ Ruby
```
#ruby
Integer(11.111)
 จะได้ค่าเป็น 11

#Java
(int)11.111;
 จะได้คือเป็น 11

#C
(int)11.111
 จะได้ค่าเป็น 11

#Python
int(10.898)
 จะได้ค่าเป็น 11
```

#Reference

Built-in Functions https://docs.python.org/3/library/functions.html
Kernel Method https://ruby-doc.org/3.4.1/Kernel.html#module-Kernel-label-Converting
