# Passing Arguments to a Method
**Passing Arguments to a Method** เวลาเราเรียกใช้งาน method ใน Ruby สามารถส่งข้อมูล (arguments) เข้าไปเพื่อให้ method ทำงานกับค่าที่กำหนด โดย Ruby รองรับหลายรูปแบบดังนี้
### 1.Positional Arguments

      def greet(name, age)
          puts "Hello #{name}, you are #{age} years old."
      end
    
      greet("Alice", 25)

ผลลัพธ์

      Hello Alice, you are 25 years old.

### 2.Default Arguments

      def greet(name, age = 18)  
          puts "Hello #{name}, age: #{age}"
      end

      greet("Bob")              
      greet("Bob", 30)          

ผลลัพธ์

      Hello Bob, age: 18
      Hello Bob, age: 30

### 3.ariable-length Arguments

      def print_numbers(*nums) 
         puts nums.inspect        
      end

      print_numbers(1, 2, 3, 4) 

ผลลัพธ์

     [1, 2, 3, 4]    

### 4.Keyword Arguments

      def profile(name:, age:)      
         puts "Name: #{name}, Age: #{age}"
      end

      profile(name: "Sara", age: 22)

ผลลัพธ์

      Name: Sara, Age: 22    

### 5.Double Splat

      def info(**details)
        puts details.inspect
      end

      info(name: "Ann", age: 20, city: "Bangkok")

ผลลัพธ์

      {:name=>"Ann", :age=>20, :city=>"Bangkok"}

### 6.Block Arguments

      def repeat(n, &block)
        n.times { block.call }
      end

      repeat(3) { puts "Hello!" }

ผลลัพธ์

      Hello!
      Hello!
      Hello!

### 7. Argument Forwarding

      def log_call(...)
        puts "Calling method..."
        actual_method(...)
      end

      def actual_method(a, b)
        puts a + b
      end

      log_call(5, 10)

ผลลัพธ์

      Calling method...
      15

# ตัวอย่างโค๊ด
## ตัวอย่างที่ 1: Positional Arguments + Default Value

      def greet(name, age = 18)     
        puts "Hello #{name}, age: #{age}" 
      end

      greet("Alice")                 
      greet("Bob", 25) 

ผลลัพธ์

      Hello Alice, age: 18
      Hello Bob, age: 25

## ตัวอย่างที่ 2: Variable-length Arguments

      def sum_numbers(*nums)         
        total = 0                   
        nums.each { |n| total += n } 
        puts "Sum = #{total}"       
      end

      sum_numbers(1, 2, 3, 4, 5)   

ผลลัพธ์

      Sum = 15

## ตัวอย่างที่ 3: Keyword Arguments

      def profile(name:, age:)      
        puts "Name: #{name}, Age: #{age}"
      end

      profile(name: "Sara", age: 20) 

ผลลัพธ์

      Name: Sara, Age: 20


# เปรียบเทียบ ภาษา C/Java/Python

### 1. ภาษา C

      #include <stdio.h>

      void add(int a, int b) {         
          printf("Sum = %d\n", a + b);  
      }

      int main() {
          int x = 5, y = 10;            
          add(x, y);                  
          return 0;                    
      }

ผลลัพธ์

      Sum = 15

### 2. ภาษา Java

      public class Main {
          static void greet(String name) {               
              System.out.println("Hello, " + name);        
          }

          static void changeValue(int num) {             
              num = 100;                                   
          }

          public static void main(String[] args) {
              greet("Alice");                            

              int x = 50;                                
              changeValue(x);                             
              System.out.println("x = " + x);             
          }
      }

ผลลัพธ์

      Hello, Alice
      x = 50

### 3.ภาษา Python

      def greet(name):                    
          print("Hello,", name)           

      def change_value(num):             
          num = 100                       

      def modify_list(lst):                
          lst.append(99)                  

      greet("Alice")                       

      x = 50
      change_value(x)                      
      print("x =", x)

      numbers = [1, 2, 3]
      modify_list(numbers)                
      print("numbers =", numbers)

ผลลัพธ์

      Hello, Alice
      x = 50
      numbers = [1, 2, 3, 99]

# ตารางเปรียบเทียบ

|ภาษา|วิธีส่งค่า|ตัวแปรธรรมดา|Object/Reference|
|-------|-----|----|------|  
|C|Call by Value|ไม่เปลี่ยนค่าต้นฉบับ|ใช้ pointer ถึงจะเปลี่ยนได้|  
|Java|Pass by Value|ไม่เปลี่ยนค่าต้นฉบับ|เปลี่ยนค่าภายใน object ได้|
|Python|Pass by Object Reference|immutable → ไม่เปลี่ยน|mutable → เปลี่ยนจริง | 

## Reference

# C

GeeksforGeeks. (ไม่มีวันที่). Functions in C. GeeksforGeeks. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.geeksforgeeks.org/functions-in-c/

TutorialsPoint. (ไม่มีวันที่). C – Functions. TutorialsPoint. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.tutorialspoint.com/cprogramming/c_functions.htm

# Java

W3Schools. (ไม่มีวันที่). Java Methods. W3Schools. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.w3schools.com/java/java_methods.asp

GeeksforGeeks. (ไม่มีวันที่). Methods in Java. GeeksforGeeks. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.geeksforgeeks.org/methods-in-java/

# Python

W3Schools. (ไม่มีวันที่). Python Functions. W3Schools. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.w3schools.com/python/python_functions.asp

GeeksforGeeks. (ไม่มีวันที่). Functions in Python. GeeksforGeeks. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.geeksforgeeks.org/functions-in-python/

# Ruby

Techotopia. (ไม่มีวันที่). Ruby Essentials. Techotopia. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.techotopia.com/index.php/Ruby_Essentials

Ruby-lang.org. (ไม่มีวันที่). Ruby master documentation. Ruby-lang. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://docs.ruby-lang.org/en/master/

Github. (ไม่มีวันที่). The best ruby books. GitHub. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://github.com/maniramakumar/the-best-ruby-books/tree/master/books

TutorialsPoint. (ไม่มีวันที่). Ruby tutorial. TutorialsPoint. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.tutorialspoint.com/ruby/index.htm

GeeksforGeeks. (ไม่มีวันที่). Ruby tutorial. GeeksforGeeks. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.geeksforgeeks.org/ruby/ruby-tutorial/

Codecademy. (ไม่มีวันที่). Learn Ruby. Codecademy. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.codecademy.com/enrolled/courses/learn-ruby













    


      

