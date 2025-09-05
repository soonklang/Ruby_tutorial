# Passing Arguments to a Method
**Passing Arguments to a Method** ใน Ruby เวลาเราสร้าง method ขึ้นมา เราสามารถส่งค่าต่าง ๆ (arguments) เข้าไปเพื่อให้ method ทำงานตามเงื่อนไขหรือข้อมูลที่ต้องการ ซึ่ง Ruby มีรูปแบบการส่ง argument ที่ค่อนข้างยืดหยุ่น โดย Ruby รองรับหลายรูปแบบดังนี้
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

### 3. Variable-length Arguments

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
|C|Call by Value|x=5 → ส่ง copy, ไม่เปลี่ยน|ใช้ pointer ถึงจะเปลี่ยน|  
|Java|Pass by Value|int x=50 → ไม่เปลี่ยน|obj.field=.. → เปลี่ยนได้|
|Python|Pass by Object Reference|x=50 → ไม่เปลี่ยน|list.append() → เปลี่ยนจริง | 

## Reference

# C

GeeksforGeeks. (n.d.). Functions in C. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.geeksforgeeks.org/functions-in-c/

TutorialsPoint. (n.d.). C – Functions. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.tutorialspoint.com/cprogramming/c_functions.htm

# Java

W3Schools. (n.d.). Java Methods. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.w3schools.com/java/java_methods.asp

GeeksforGeeks. (n.d.). Methods in Java. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.geeksforgeeks.org/methods-in-java/

# Python

W3Schools. (n.d.). Python Functions. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.w3schools.com/python/python_functions.asp

GeeksforGeeks. (n.d.). Functions in Python. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.geeksforgeeks.org/functions-in-python/

# Ruby

Ruby-lang.org. (n.d.). Ruby master documentation. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://docs.ruby-lang.org/en/master/

TutorialsPoint. (n.d.). Ruby – Methods. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.tutorialspoint.com/ruby/ruby_methods.htm

GeeksforGeeks. (n.d.). Ruby Methods. สืบค้นเมื่อ 4 กันยายน 2025, จาก https://www.geeksforgeeks.org/ruby-methods/













    


      

