# Declaring and Calling a Ruby Method
## บทนำ
***Method*** : เป็นชุดคำสั่งที่ทำงานฌฉพาะเจาะจง และคืนค่าผลลัพธ์ (result)กลับมา Method นั้นจะช่วยประหยัดเวลาและช่วยให้สามารถนำ Code ของผู้ใช้กลับมาใช้ซ้ำได้โดยไม่ต้องพิมพ์ Code ใหม่อีก
## การเรียกใช้ Method
- ในภาษา Ruby จะใช้คำว่า **def** ตามด้วยชื่อ Method และจบด้วยคำว่า **end** 

- Method นั้นต้องถูกกำหนดก่อนที่จะเรียกใช้งาน และชื่อของ Method ควรเขียนด้วย***ตัวพิมพ์เล็ก*** 

- การเรียกใช้เพียงแค่เขียนชื่อของ Method ก็สามารถเรียกใช้งานได้แล้ว

### syntax
```ruby
def name( arg1, arg2, arg3, ... )
   .. ruby code ..
   return value
end
```
def - ใช้เริ้มต้นในการประกาศ Method

name - ชื่อของ Method ที่ต้องการสร้าง

arg - parameters (ตัวแปร) ที่ Method รับเข้ามา ***(ถ้าไม่ใส่หมายถึง Method นี้จะไม่มีการรับค่าเข้ามา)**

return - ส่งค่ากลับออกมาจาก Method ***(ถ้าไม่ใส่ Ruby จะส่งค่าของบบรทัดสุดท้ายออกมา)**

### ตัวอย่างที่ 1
```ruby
def hello
  puts "Hello World"
end
```

### ผลลัพธ์
```ruby
 Hello World
```

### ตัวอย่างที่2
```ruby
 def add_two(number)
  number + 2
end

puts add_two(8)
```
### ผลลัพธ์
```ruby
 10
```
# Declaring and Calling a Java Method
***Method*** ใน Java ทำหน้าที่แสดงพฤติกรรมของ Object ออกมา โดยจะต้องอยู่ภายใน Class และ สามารถเรียกใช้งานได้จากที่อื่นๆ ขึ้นอยู่กับขอบเขตและระดับการเข้าถึงที่ได้กำหนดขึ้น

```java
access_modifier type name(parameter1, parameter2, ...) {
    statements
}
```

access_modifier - เป็นการกำหนดระดับการเข้าถึงของเมธอด ซึ่งจะอยู่ในเรื่องของออบเจ็ค โดยมี 4 ระดับคือ private protected public และ default (ไม่ต้องกำหนด)

type - เป็นประเภทของเมธอดที่จะสร้างขึ้น โดยสามารถเป็นได้ทั้ง primitive datatype หรือ reference types ได้ และถ้าหากเมธอดไม่มีการส่งค่ากลับจะใช้คำสั่ง void

name - เป็นชื่อของเมธอดหรือ identifier ซึ่งมีกฏในการตั้งชื่อเช่นเดียวกันกับตัวแปร

parameters - เป็นลิสต์ของตัวแปรที่จะส่งเข้าไปใช้ในเมธอด โดยสามารถมีตั้งแต่ 1 ขึ้นไปหรือไม่มีก็ได้

### ตัวอย่าง private

เป็นการเข้าถึงได้เฉพาะภายใน class เดียวกัน
```java
class Example {
    private void greet() {
        System.out.println("Hello");
    }
}
```

### ตัวอย่าง protected

เป็นการเข้าถึงภายใน class เดียวกัน package เดียวกัน หรือถ้าเป็นแบบ subclass ใน package อื่นก็สามารถเข้าถึงได้
```java
class Example {
    protected void greet() {
        System.out.println("Hello");
    }
}
```

### ตัวอย่าง public

เป็นการเข้าถึงได้ทุก class, method, variable จากทุกที่
```java
class Example {
    public void greet() {
        System.out.println("Hello");
    }
}
```

### ตัวอย่าง default

เป็นการเข้าถึงได้เฉพาะ class ใน package เดียวกัน
```java
class Example {
    void greet() {
        System.out.println("Hello");
    }
}
```

## การเรียกใช้ Method

เป็นการส่งการควบคุมไปยัง Method ที่ทำการเรียกเพื่อให้ทำงานตามตรรกะที่กำหนด มีการเรียก Method 4 แบบ

### 1.เรียกโดยที่ผู้ใช้กำหนดเอง

เป็นการเขียนเองโดยโปรแกรมเมอร์ เพื่อใช้เรียก Method 

ถ้าเป็น Method ที่ไม่ใช่ static จะต้องสร้าง object ของ class ก่อนแล้วจึงเรียกใช้ Method

### ตัวอย่าง
```java
class Geeks {
    void hello() {
        System.out.println("This is a user-defined method.");
    }

    public static void main(String[] args) {
        Geeks obj = new Geeks(); // Create object
        obj.hello();             // Call method
    }
}
```

### ผลลัพธ์
```java
This is a user-defined method.
```

### 2.เรียกโดยใช้ Abstract

ไม่มีตัวโค้ดภายในจำเป็นต้อง5^d override ใน subclass
การเรียกใช้นั้น จะต้องทำผ่าน object ของ subclass ที่ override แล้ว

### ตัวอย่าง
```java
abstract class GeeksHelp {
    abstract void check(String name); // Abstract method
}

public class Geeks extends GeeksHelp {
    @Override
    void check(String name) {
        System.out.println(name);
    }

    public static void main(String[] args) {
        Geeks obj = new Geeks(); // Subclass object
        obj.check("GeeksforGeeks");
    }
}
```

### ผลลัพธ์
```java
GeeksforGeeks
```
### 3.เรียกโดยใช้ Method ที่มีอยู่แล้ว

ใน java มี method สำเร็จรูปจำนวนมากใน Java Standard Library เช่น hashCode() สามารถใช้งานได้โดยตรงผ่าน object
### ตัวอย่าง
```java
public class Geeks {
    public static void main(String[] args) {
        Geeks obj = new Geeks();
        System.out.println(obj.hashCode()); // Predefined method
    }
}
```

### ผลลัพธ์
```java
1510467688
```

### 4.เรียกโดยใช้ Method แบบ static

method แบบ static เป็นของ class ไม่ใช่ object เพราะฉนั้นเราสามารถเรียกใช้งานได้ดดยตรงดดยไม่ต้องผ่าน object

### ตัวอย่าง
```java
class Test {
    static void hello() {
        System.out.println("Hello");
    }
}
public class Geeks {
    public static void main(String[] args) {
        Test.hello(); // Call static method directly
    }
}
```

### ผลลัพธ์
```java
Hello
```

# Declaring and Calling a Python Method

***Method*** ใน Python นั้นถ้าอยู่นอก class จะถูกเรียกว่า function แต่เมื่ออยู่ใน class จะถูกเรียกว่า method (ซึ่ง method นั้นจะต้องถูกเรียกผ่าน object)

 ### syntax function

 ```python
  def function_name(parameters):
    # function body
```

def - ใช้เริ้มต้นในการประกาศ function

function_name - ชื่อของ function ที่ต้องการสร้าง

parameters - ค่าที่ส่งเข้าไปยังใน function (อาจจะใส่หรื่อไม่ใส่ก็ได้)

### ตัวอย่างที่ 1
```python
  def my_function():
    print("Hello from a function")
```

### ตัวอย่างที่ 2
```python
 def my_function(fname):
    print(fname + " Refsnes")

my_function("Emil")
```
## การเรียกใช้ function
หลังจากการสร้าง function เราสามารถเรียกใช้ได้โดยการเขียนชื่อของ function ตามด้วยวงเล็บ () ภายในวงเล็บสามาารถใส่ parameters ที่ function ต้องการได้

### ตัวอย่างที่ 1
```python
def evenOdd(x):
    if (x % 2 == 0):
        return "Even"
    else:
        return "Odd"

print(evenOdd(16))
print(evenOdd(7))
```

### ผลลัพธ์
```python
Even
Odd
```

### ตัวอย่างที่2
```python
def myFun(x, y=50):
    print("x: ", x)
    print("y: ", y)

myFun(10)
```

### ผลลัพธ์
```python
x:  10
y:  50
```

### syntax ของ function ที่อยู่ใน class (Method)
มีการสร้าง object เหมือน java เพื่อเรียกใช้ function ใน class
```python
class ClassName:
    def method_name(self, parameter1, parameter2, ...):
        # Method body - code goes here


# Creating an object of the class

object_name = ClassName()


# Calling a method on the object

object_name.method_name(argument1, argument2, ...)

```

### ตัวอย่างที่ 1
```python
class Calculator:
    def add(self, num1, num2):
        return num1 + num2

# Creating an object of Calculator
calculator_object = Calculator()

# Calling the add method with parameters
result = calculator_object.add(5, 7)
print(&quot;Result of addition:&quot;, result)
```
### ผลลัพธ์
```python
Result of addition: 12
```

### ตัวอย่างที่ 2

```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    @classmethod
    def calculate_age(cls, name, birth_year):
        # calculate age an set it as a age
        # return new object
        return cls(name, date.today().year - birth_year)

    def show(self):
        print(self.name + "'s age is: " + str(self.age))

jessa = Student('Jessa', 20)
jessa.show()

# create new object using the factory method
joy = Student.calculate_age("Joy", 1995)
joy.show()
```
### ผลลัพธ์
```python
Jessa's age is: 20
Joy's age is: 30
```

# Declaring and Calling a C Method



# Reference

### Ruby
**-Defining & Calling the method in Ruby**

geeksforgeeks.(ไม่มีวันที่). Ruby | Methods. geeksforgeeks. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://www.geeksforgeeks.org/ruby/ruby-methods/


rubymonstas.(ไม่มีวันที่). Defining a method. rubymonstas. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://ruby-for-beginners.rubymonstas.org/writing_methods/definition.html#


techotopia.(ไม่มีวันที่). Ruby | Methods. techotopia. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://www.techotopia.com/index.php/Ruby_Methods

### Java
**-Defining & Calling the method in Java**


geeksforgeeks.(ไม่มีวันที่). Java Methods. geeksforgeeks. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://www.geeksforgeeks.org/java/methods-in-java/


marcuscode.(2016). เมธอด. marcuscode. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://marcuscode.com/lang/java/methods


**-Access Modifiers Java**


geeksforgeeks.(ไม่มีวันที่). Access Modifiers in Java. geeksforgeeks. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://www.geeksforgeeks.org/java/access-modifiers-java/


### Python
**-Defining & Calling the method in Python**


geeksforgeeks.(ไม่มีวันที่). Python Functionss. geeksforgeekse. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://www.geeksforgeeks.org/python/python-functions/


geeksforgeeks.(ไม่มีวันที่). Define and Call Methods in a Python Class. geeksforgeekse. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://www.geeksforgeeks.org/python/define-and-call-methods-in-a-python-class/


w3schools.(ไม่มีวันที่). Python Classes and Objects. w3schools. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://www.w3schools.com/python/python_classes.asp


w3schools.(ไม่มีวันที่). Python Functions. w3schools. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://www.w3schools.com/python/python_functions.asp


simplilearn.(ไม่มีวันที่). Functions in Python | Definition, Types and Examples. simplilearn. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://www.simplilearn.com/tutorials/python-tutorial/python-functions


pynative.(ไม่มีวันที่). Python Class Method Explained With Examples, Types and Examples. pynative. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://pynative.com/python-class-method/


w3schools.(ไม่มีวันที่). Python Functions. w3schools. สือค้นเมื่อวันที่ 3 กันยายน 2025, จาก https://www.w3schools.com/python/python_functions.asp






