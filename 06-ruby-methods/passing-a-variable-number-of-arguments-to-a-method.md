# Passing a Variable Number of Arguments to a Method
เป็นวิธีที่ Ruby ใช้ในการแก้ปัญหาในตอนที่เราไม่รู้ว่าจะรับ argument เข้ามาทั้งหมดกี่ตัว ด้วยการใช้ * นำหน้าชื่อ argument ในตอนที่เราสร้าง method จะทำให้ method ที่ถูกประกาศสามารถรับค่า argument ได้แบบไม่จำกัดจำนวน และ argument ที่รับเข้ามาจะถูกเก็บไวใน array เพื่อเข้าถึงและใช้งานต่อไปใน method นั้นๆ
### การรับค่า argument แบบทั่วไป
### ตัวอย่างที่ 1 Ruby

    def multiply(val1, val2 )
        result = val1 * val2
        puts result
    end
    
    multiply( 2, 10 )
    multiply( 4, 20 )
    multiply( 10, 40 )
    multiply( 6, 7, 5)
    
### ผลลัพธ์
    `multiply': wrong number of arguments (given 3, expected 2) (ArgumentError)
### คำอธิบาย
จากตัวอย่างที่ 1 จะเห็นว่าจำนวน argument ที่ส่งเข้าไปใน method นั้น มีจำนวนเท่ากันกับ argument ที่กำหนดไว้ใน method
### ตัวอย่างที่ 2 (Python)

    def sum(a,b):
    print(a+b)
  
    sum(1,2,5)
    
### ผลลัพธ์
    TypeError: sum() takes 2 positional arguments but 3 were given

### คำอธิบาย
จากตัวอย่างที่ 2 จะเห็นว่าเมื่อเรียกใช้ function sum มี argument ที่ส่งค่าไปที่ method 3 ค่า แต่จำนวน argument ใน method ที่รับได้มีแค่ 2 ค่าจึงทำให้เกิด error ขึ้น

## การรับค่าโดยใช้ * นำหน้าชื่อ argument
### ตัวอย่าง 1 (Ruby)

    def method(*arguments)
    p arguments
    end
    
    method(1)
    method(1, 2, 3)
    method(true, false, 5, 1.23)
    method("PHP", "Ruby", "Python", "Java")
    
### ผลลัพธ์

    [1]
    [1, 2, 3]
    [true, false, 5, 1.23]
    ["PHP", "Ruby", "Python", "Java"]

### คำอธิบาย
จากตัวอย่างที่ 1 จะเห็นว่าการใส่ * ไปที่หน้าชื่อ argument ใน method ที่ประกาศจะสามารถทำให้รับค่า argument ที่ส่งมาได้จำนวนกี่ค่าก็ได้แล้วนำจำนวนเหล่านั้นไปเก็บไว้ในรูปแบบของ array 

### ตัวอย่าง 2 (Python)

     def sum_all(*args):
         result = 0
         for num in args:
             result += num
             return result
    print(sum_all(1, 2, 3, 4, 5))

### ผลลัพธ์

    15

### คำอธิบาย
จากตัวอย่างที่ 2 จะเห็นได้ว่าเมื่อมีการใช้ * นำหน้า argument จะทำให้สามารถรับค่ากีจำนวนก็ได้เช่นเดียวกับตัวอย่างที่ 1 แต่ในภาษา Python จะนำ argument ที่รับมาไปเก็บในรูปแบบ tuple แล้วบวกค่า argument ทุกตัวที่อยู่ใน tuple แล้วนำค่าที่ได้ไปเก็บที่ result แล้วนำมาแสดงผล










## อ้างอิง
https://marcuscode.com/lang/ruby/methods ใช้ในการอ้างอิงตัวอย่างที่ 1การรับค่า argument แบบไม่จำกัดจำนวนใน method,อ้างอิงตัวอย่างที่ 2 การรับค่า argument แบบทั่วไป
https://www.techotopia.com/index.php/Ruby_Methods#Passing_a_Variable_Number_of_Arguments_to_a_Method ใช้อ้างอิง อ้างอิงตัวอย่างที่ 1 การรับค่า argument แบบทั่วไป
https://www.geeksforgeeks.org/python/variable-length-argument-in-python/ ใช้เปรียบเทียบและอ้างอิงการรับค่า argument กับภาษา Ruby 
