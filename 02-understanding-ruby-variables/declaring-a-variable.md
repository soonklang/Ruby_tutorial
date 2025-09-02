# Declaring_variables_in_Ruby
## Ruby >>
การประกาศตัวแปรใน ภาษา Ruby นั้น ชื่อของตัวแปรจะต้องประกอบไปด้วย ตัวอักษร ตัวเลขและเครื่องหมาย _ (Underscore) 
และไม่สามารถขึ้นต้นด้วยตัวเลขได้ เพื่อให้สามารถแยกแยะระหว่างตัวแปรและรหัสอื่นๆในโค้ดได้
### Example :
     name = "Ruby"     # ตัวแปรชนิด String
     age = 25          # ตัวแปรชนิด Integer
     price = 99.99     # ตัวแปรชนิด Float
     is_active = true  # ตัวแปรชนิด Boolean
     
     puts "His name is " + name
### Output :
     His name is Ruby
โดยตัวแปรจะทำหน้าที่ "การอ้างอิง" (reference) หรือ "ตัวชี้" (pointer) ไปยังตำแหน่งในหน่วยความจำนั้น
### Example :
     desired_location = "Barcelona"
     johns_location = desired_location
     
     puts desired_location  #output >>> "Barcelona"
     puts johns_location    #output >>> "Barcelona"

     

# เปรียบเทียบกับภาษา C , Java และ Python
## C >>
ในการประการตัวแปรของภาษา C ต้องมีการกำหนดประเภทตัวแปรที่ต้องการสร้างแล้วจึงสามารถกำหนดค่าได้
### ตัวอย่างประเภทตัวแปร
    int #ตัวเลขจำนวนเต็มบวกและลบ
    float #ทศนิยม
    char #อักขระ โดยล้อมด้วย '..'
### Example :
     int main() {
         int x = 5;
         int y = 6;
         int sum = x + y;
         printf("%d", sum);
         return 0;
     }
### Output :
     11
     
## Java >>
ตัวแปรใน Java มีหลายประเภท จึงต้องเลือกประเภทตัวแปรก่อนตั้งชื่อ แล้วถึงจะกำหนดค่าตัวแปรได้
### Example :
     string name = "Ruby";
     int age = 15;
     boolean human = true;
     
     System.out.println(name);
     System.out.println(age);
     System.out.println(human);
### Output :
     Ruby
     15
     true 

## Python >>
การประกาศตัวแปรในภาษา Python จะไม่มีการกำหนดประเภทตัวแปร จะสามารถกำหนดค่าตัวแปรได้เลย คล้ายๆ Ruby
### Example :
     x = 5
     a = 7
     A = 'Ruby'
     print(x)
     print(a)
     print(A)
### Output :
     5
     7
     Ruby
แต่หากต้องการระบุชนิดข้อมูลทำได้โดยการ Casting
### Example :
     x = 5
     a = 7
     A = 'Ruby'
     
     x = str('B')
     a = int(3)
     A = float(3)
     print(x)
     print(a)
     print(A)
### Output :
     B
     3
     3.0

# Reference from : 

https://www.theodinproject.com/lessons/ruby-variables

https://www.w3schools.com/java/java_variables.asp

https://www.w3schools.com/c/c_variables.php

https://www.w3schools.com/python/python_variables.asp
