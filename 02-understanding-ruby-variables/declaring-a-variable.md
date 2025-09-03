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
ตัวแปรใน Java มีหลายประเภท จึงต้องเลือกประเภทตัวแปรก่อนตั้งชื่อแล้วถึงจะกำหนดค่าตัวแปรได้
### Example :
     class Geeks {
        public static void main(String[] args) {
        int age = 25;      
        String name = "GeeksforGeeks"; 
        double salary = 50000.50;     

       
        System.out.println("Age: " + age);          
        System.out.println("Name: " + name);        
        System.out.println("Salary: " + salary);
        }
     }

### Output :
     Age: 25
     Name: GeeksforGeeks
     Salary: 50000.5

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
และสามารถทำการลบตัวแปรด้วยคำสั่ง del
### Example :
     counter = 100
     print (counter)
     
     del counter
     print (counter)
### Output :
     100
     
     Traceback (most recent call last):
     File "main.py", line 7, in <module>
     print (counter)
     NameError: name 'counter' is not defined

# คลิปนำเสนอ
...
# Presentation (slides)
...
# Reference from : 

https://www.theodinproject.com/lessons/ruby-variables

https://marcuscode.com/lang/ruby/variables-basic

https://www.geeksforgeeks.org/java/variables-in-java/

https://www.w3schools.com/c/c_variables.php

https://www.tutorialspoint.com/python/python_variables.htm
