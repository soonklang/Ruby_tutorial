# Ruby Class Inheritance
---
## Class Inheritance คืออะไร?

Inheritance(การสืบทอด) คือ การที่เราสามารถสร้าง class ใหม่ขึ้นมาโดยใช้ class ที่มีอยู่แล้วเป็นต้นแบบ โดยยังมี variable และ method ของของ class นั้นๆอยู่ เพื่อนำมาสร้าง class ที่มีความคล้ายกันแต่สามารถเพิ่ม variable และ method ใหม่ๆได้

### ประเภทของ Inheritance
- **Single inheritance(การสืบทอดเดี่ยว)** คือ class หนึ่งสืบทอดมาจาก class เพียง class เดียว
- **Multiple inheritance(การสืบทอดหลายรายการ)** คือ class หนึ่งสามารถสืบทอดมาจาก หลายๆ class พร้อมกันได้
- **Multilevel inheritance(การสืบทอดหลายระดับ)** คือ class หนึ่งสืบทอดมาจากอีก class ที่สืบทอด class อื่นมาอีกที
- **Hierarchical inheritance(การสืบทอดแบบลำดับชั้น)** คือ มีหลาย class สืบทอดมาจาก class เพียง class เดียว 
- **Hybrid inheritance(การสืบทอดแบบผสม)** คือ การรวมกันระหว่างประเภทของ Inheritance ตั้งแต่ 2 ขึ้นไป
 
โดยภาษา Ruby นั้นไม่รองรับ **Multiple inheritance** แต่ว่าสามารถใช้ **Mixins** (via Modules) แทนได้

### Keywords
- **Super Class** คือ class ที่ถูกสืบทอด method หรือ/และ variable ไปโดยเรียกได้หลายแบบ เช่น classแม่, classพ่อ ,Parent Class, Super Class
- **Sub Class** คือ class ที่สืบทอด method และ/หรือ variable มาจาก Super Class และสามารถเพิ่มvariable และ method ใหม่ๆได้ โดยเรียกได้หลายแบบ เช่น classลูก, Sub Class

---

## การใช้งาน Class Inheritance ในภาษา Ruby

- การสืบทอดใน Ruby สามารถทำได้โดยใช้เครื่องหมาย `<`
### Syntax ตัวอย่าง
```ruby
class subclass_name < superclass_name 
```

### ตัวอย่าง Code การใช้งาน Class Inheritance ในภาษา Ruby
```ruby
# Superclass 
class ThisIsSuperClass 

    # constructor of superclass
    def initialize 
        
        puts "Creating class"
    end
    
    # method of the Superclass
    def super_method
        
        puts "Method of Superclass"
    end
end

# Subclass
class ThisIsSubClass < ThisIsSuperClass 

end

# creating object from superclass
ThisIsSuperClass.new

# creating object from subclass
test_obj = ThisIsSubClass.new

# calling the method of superclass from subclass
test_obj.super_method
```

<details>

<summary>Output</summary>

> Creating class\
> Creating class\
> Method of Superclass

</details>
จากตัวอย่าง Code การใช้งาน Class Inheritance จะเห็นว่า ThisIsSubClass สืบทอดมาจาก ThisIsSuperClass ทำให้ test_obj ที่สร้างมาจาก ThisIsSubClass สามารถใช้ method initialize และ super_method ได้แม้ใน ThisIsSubClass ไม่ได้เขียนขึ้นมาใหม่



### การใช้งาน Class Inheritance ในภาษาอื่นๆ
- ### Java
  การสืบทอดใน Java สามารถทำได้โดยใช้ keyword `extend`
  
  **ตัวอย่าง**
  ```Java
  // Superclass
  public class ThisIsSuperClass {
    // Constructor (เหมือน initialize ใน Ruby)
    public ThisIsSuperClass() {
        System.out.println("Creating class");
    }

    public void superMethod() {
        System.out.println("Method of Superclass");
    }
  }

  // Subclass
  public class ThisIsSubClass extends ThisIsSuperClass {
    
  }
  
  public class Main {
    public static void main(String[] args) {
        // creating object from superclass
        new ThisIsSuperClass();

        // creating object from subclass
        ThisIsSubClass testObj = new ThisIsSubClass();

        // calling the method of superclass from subclass
        testObj.superMethod();
    }
  }

  
  ```

  <details>

  <summary>Output</summary>

  > Creating class\
  > Creating class\
  > Method of Superclass

  </details>
  
  
- ### Python
  การสืบทอดใน Python สามารถทำได้โดยใช้ `class SubClass(SuperClass)`
  
  **ตัวอย่าง**
  ```Python
  # Superclass
  class ThisIsSuperClass:
    def __init__(self):
        print("Creating class")

    def super_method(self):
        print("Method of Superclass")

  # Subclass
  class ThisIsSubClass(ThisIsSuperClass):
    pass  

  # Execution
  if __name__ == "__main__":
    # Create object from superclass
    ThisIsSuperClass()

    # Create object from subclass
    test_obj = ThisIsSubClass()

    # calling the method of superclass from subclass
    test_obj.super_method()


  
  ```

  <details>

  <summary>Output</summary>

  > Creating class\
  > Creating class\
  > Method of Superclass

  </details>
  
- ### C++
  การสืบทอดใน C++ สามารถทำได้โดยใช้ `class SubClass : access_specifier SuperClass`

  **ตัวอย่าง**
  ```C++

  #include <iostream>
  using namespace std;
  
  // Superclass
  class ThisIsSuperClass {
  public:
      // Constructor
      ThisIsSuperClass() {
          cout << "Creating class" << endl;
      }
  
      void super_method() {
          cout << "Method of Superclass" << endl;
      }
  };
  
  // Subclass
  class ThisIsSubClass : public ThisIsSuperClass {
      
  };
  
  int main() {
  
      ThisIsSuperClass obj1;
  
      ThisIsSubClass test_obj;
  
      test_obj.super_method();
  
      return 0;
  }

  ```


  <details>

  <summary>Output</summary>

  > Creating class\
  > Creating class\
  > Method of Superclass

  </details>
  
---

## Method Overriding
 Method Overriding คือ การที่เราสามารถเขียนทับ method ใน subclass ที่สืบทอดมาจาก superclass ได้โดยชื่อ method ยังคงเดิมแต่การดำเนินการใน method นั้นเปลี่ยนไปจาก superclass 
 ### ตัวอย่าง Code การใช้งาน Method Overriding ในภาษา Ruby
```ruby
class Lion
  
  def roar
    print "ROAR!"
  end
end

class Cat < Lion
  
  def roar #Overriding
    print "meow!"
  end
end

c = Cat.new
c.roar
```
<details>

<summary>Output</summary>

> meow!


</details>
จากตัวอย่าง Code การใช้งาน Method Overriding จะเห็นว่า แม้ว่า object c สร้างมาจาก class Cat ที่สืบทอดมาจาก class Lion มี method roar เหมือนกันแต่ class Cat ได้ Overriding method roar ไปแล้วทำให้ผลลัพธ์จากที่ควรจะเป็น ROAR! กลายเป็น meow! แทน

### การใช้งาน Method Overriding ในภาษาอื่นๆ
- ### Java
  **ตัวอย่างการใช้งาน Method Overriding ในภาษา Java**

  ```Java

    // Superclass
  public class Lion {
      public void roar() {
          System.out.print("ROAR!");
      }
  }
  
  // Subclass
  public class Cat extends Lion {
      @Override
      public void roar() {
          System.out.print("meow!");
      }
  }
  
  // Main
  public class Main {
      public static void main(String[] args) {
          Cat c = new Cat();
          c.roar();  
      }
  }

  
  ```
  <details>

  <summary>Output</summary>

  > meow!


  </details>
  
- ### Python
  **ตัวอย่างการใช้งาน Method Overriding ในภาษา Python**
  ```Python

  class Lion:
      def roar(self):
          print("ROAR!", end="")
  
  class Cat(Lion):
      def roar(self):  # Overriding
          print("meow!", end="")
  
  if __name__ == "__main__":
      c = Cat()
      c.roar() 
  
  
  ```
  <details>

  <summary>Output</summary>

  > meow!

  </details>
- ### C++
  **ตัวอย่างการใช้งาน Method Overriding ในภาษา C++**
  
  ```C++

  #include <iostream>
  using namespace std;
  
  // Superclass
  class Lion {
  public:
      virtual void roar() {
          cout << "ROAR!";
      }
  };
  
  // Subclass
  class Cat : public Lion {
  public:
      void roar() override { // Overriding
          cout << "meow!";
      }
  };
  
  int main() {
      Cat c;
      c.roar();
  
      return 0;
  }

  ```

  <details>

  <summary>Output</summary>

  > meow!

  </details>
  
---

## Super method
Super method ใช้ใน Sub Class เพื่อเรียก method ของ Super Class มาใช้ โดยมีการส่ง parameter ที่ใช้สำหรับ Super method นั้นๆในลักษณะที่แตกต่างกันไป สามารถดูตัวอย่างข้างล่างเพื่อง่ายต่อความเข้าใจได้
### ตัวอย่าง Code การใช้งาน Super method ในภาษา Ruby
```ruby
class Super_Original
  
    def display a = 0, b = 0
        puts "Parent class, 1st Parameter: #{a}, 2nd Parameter: #{b}"
    end
end

class Super_Copy < Super_Original
  
    def display a, b
        
        super
        
        super a
        
        super a, b
        
        super()
        
        puts "This is subclass method"
    end
end

obj = Super_Copy.new
obj.display "ONE", "TWO"
```
<details>

<summary>Output</summary>

>Parent class, 1st Parameter: ONE, 2nd Parameter: TWO\
>Parent class, 1st Parameter: ONE, 2nd Parameter: 0\
>Parent class, 1st Parameter: ONE, 2nd Parameter: TWO\
>Parent class, 1st Parameter: 0, 2nd Parameter: 0\
>This is subclass method

</details>
จากตัวอย่าง Code การใช้งาน Super method obj ได้ส่ง parameter "ONE" และ "TWO" ไปใน display ของ Super_Copy เพราะ obj สร้างมาจาก class Super_Copy จะเห็นได้ว่า ผลลัพธ์ของแต่ละ super จะออกมาไม่เหมือนกัน โดยมีลักษณะดังนี้

- **super** จะส่ง parameter ที่ได้มาจาก obj.display ก็คือ "ONE" และ "TWO" ไปใน display ของ Super Class **โดยอัตโนมัติ**
- **super a** จะส่งไปแค่ parameter "ONE" ทำให้ค่า parameter ของ b=0 ตามที่ display ของ Super Class กำหนดไว้
- **super a, b** จะส่ง parameter ที่ได้มาจาก obj.display ก็คือ "ONE" และ "TWO" ไปใน display ของ Super Class
- **super()** จะไม่ส่งอะไรไปเลย แค่เรียกใช้ method display ของ Super Class ทำให้ค่า parameter ของ a = 0 และ b=0 ตามที่ display ของ Super Class กำหนดไว้

### การใช้งาน Super method ในภาษาอื่นๆ
- ### Java
  **ตัวอย่างการใช้งาน Super method  ในภาษา Java**

  ```Java

  class SuperOriginal {
    void display(String a, String b) { //ใน java ไม่สามารถกำหนดค่า Default ของพารามิเตอร์ใน method ได้
        System.out.println("Parent class, 1st Parameter: " + a + ", 2nd Parameter: " + b);
    }
  }

  class SuperCopy extends SuperOriginal {
    void display(String a, String b) { 
        super.display(a, b);     //ต้องกำหนดตัวแปรเอง ไม่สามารถ super.display() แล้ว auto ได้เหมือน ruby
        super.display(a, null);  // ต้องกำหนดตัวแปรให้ครบ ไม่สามารถ super.display(a)
        super.display(a, b);     
        super.display(null, null); // ต้องกำหนดตัวแปรเอง ไม่สามารถ super.display() แล้ว auto ได้เหมือน ruby
        System.out.println("This is subclass method");
    }
  }

  public class Main {
    public static void main(String[] args) {
        SuperCopy obj = new SuperCopy();
        obj.display("ONE", "TWO");
    }
  }

  
  ```
  <details>

  <summary>Output</summary>

  > Parent class, 1st Parameter: ONE, 2nd Parameter: TWO\
  > Parent class, 1st Parameter: ONE, 2nd Parameter: null\
  > Parent class, 1st Parameter: ONE, 2nd Parameter: TWO\
  > Parent class, 1st Parameter: null, 2nd Parameter: null\
  > This is subclass method


  </details>
  
- ### Python
  **ตัวอย่างการใช้งาน Super method  ในภาษา Python**

  ```Python
  class SuperOriginal:
    def display(self, a=0, b=0):
        print(f"Parent class, 1st Parameter: {a}, 2nd Parameter: {b}")

  class SuperCopy(SuperOriginal):
    def display(self, a, b):
        super().display(a, b)     # ทำ auto ไม่ได้แบบ ruby
        super().display(a)     
        super().display(a, b)
        super().display()         # super().display() ก็ตรงตัวดีโดยไม่ส่งอะไรไปก็ไปใช้ ค่า Default ใน method display ของ super
        print("This is subclass method")

  if __name__ == "__main__":
    obj = SuperCopy()
    obj.display("ONE", "TWO")

  
  ```
  <details>

  <summary>Output</summary>

   > Parent class, 1st Parameter: ONE, 2nd Parameter: TWO\
   > Parent class, 1st Parameter: ONE, 2nd Parameter: 0\
   > Parent class, 1st Parameter: ONE, 2nd Parameter: TWO\
   > Parent class, 1st Parameter: 0, 2nd Parameter: 0\
   > This is subclass method



  </details>
  
- ### C++
  **ตัวอย่างการใช้งาน Super method  ในภาษา C++**

  ในภาษา C++ ไม่มี keyword super เพราะว่า C++ รองรับ multiple inheritance ทำให้เกิดความกำกวมเวลลาเรียกใช้ super ว่าหมายถึง class ที่สืบทอดมา class ไหนกันแน่
  โดยเราสามารถเรียก method จาก super class ได้โดย `SuperClass::superMethod();`
  ```C++
  #include <iostream>
  #include <string>
  using namespace std;
  
  class Super_Original {
  public:
       void display(const string &a = "", const string &b = "") {
          cout << "Parent class, 1st Parameter: " << a
               << ", 2nd Parameter: " << b << endl;
      }
  };
  
  class Super_Copy : public Super_Original {
  public:
      void display(const string &a, const string &b)  {
          // super               
          Super_Original::display();  
          
          // super a             
          Super_Original::display(a);
          
          // super a, b          
          Super_Original::display(a, b);
          
          // super()              
          Super_Original::display();
          
          cout << "This is subclass method" << endl;
      }
  };
  
  int main() {
      Super_Copy obj;
      obj.display("ONE", "TWO");
      return 0;
  }

  ```
  
  <details>

  <summary>Output</summary>

   > Parent class, 1st Parameter: ONE, 2nd Parameter: TWO\
   > Parent class, 1st Parameter: ONE, 2nd Parameter: (null)\
   > Parent class, 1st Parameter: ONE, 2nd Parameter: TWO\
   > Parent class, 1st Parameter: (null), 2nd Parameter: (null)\
   > This is subclass method



  </details>
  
---

## Class Inheritance across different files ในภาษา Ruby
ในตัวอย่าง code ต่างๆที่ได้แสดงให้ดูไปเป็นการสืบทอดที่สามารถทำได้หากเราประกาศ class ไว้ไฟล์เดียวกัน แต่เราก็สามารถที่จะสืบทอด class จาก class ที่ประกาศไว้ในไฟล์อื่นๆได้เหมือนกัน โดย

- **require_relative** ใช้เมื่อไฟล์ของ class ที่อยากจะสืบทอด(Super Class)อยู่ใน Folder เดียวกันกับ Sub Class
- **require** ใช้เมื่อไฟล์ของ class ที่อยากจะสืบทอด(Super Class)อยู่ใน Folder คนละ Folder กับ Sub Class

### ตัวอย่าง
ต้องการที่จะ สร้าง class Cat ในไฟล์ cat.rb โดยสืบทอดมาจาก class Lion ในไฟล์ lion.rb ที่อยู่ใน Drive D ใน folder ชื่อ ruby

- อยู่ใน Folder เดียวกัน
 
  ```ruby
  # in cat.rb
  require_relative 'lion' 

  class Cat < Lion
  
  end
  ```
- อยู่คนละ Folder กัน
 
  ```ruby
  # in cat.rb
  require 'D:/folder/ruby/lion'

  class Cat < Lion
  
  end
  ```
---

## References

- Codecademy Team. (2023, November 7). What is Inheritance in Object‑Oriented Programming? Retrieved September 4, 2025, from https://www.codecademy.com/resources/blog/what-is-inheritance

- Ruby User’s Guide. (n.d.). Inheritance. In Ruby User’s Guide. Retrieved September 4, 2025, from https://ruby-doc.org/docs/ruby-doc-bundle/UsersGuide/rg/inheritance.html
  
- GeeksforGeeks. (2021, August 5). Ruby | Inheritance. Retrieved September 4, 2025, from https://www.geeksforgeeks.org/ruby/ruby-inheritance/
  
- W3Schools. (n.d.). Java Inheritance (Subclass and Superclass). Retrieved September 4, 2025, from https://www.w3schools.com/java/java_inheritance.asp
  
- W3Schools. (n.d.). Python Inheritance. Retrieved September 4, 2025, from https://www.w3schools.com/python/python_inheritance.asp

- Kurian, A. (2009, August 6). How can Inheritance be modelled using C? Retrieved September 4, 2025, from Stack Overflow: https://stackoverflow.com/questions/1237266/how-can-inheritance-be-modelled-using-c
    
- Lieblang, M. (n.d.). How to implement inheritance and polymorphism in C. In Modern C Programming. Retrieved September 4, 2025, from https://moderncprogramming.com/how-to-implement-inheritance-and-polymorphism-in-c/

- GeeksforGeeks. (2024, May 29). Function overriding in programming. Retrieved September 4, 2025, from https://www.geeksforgeeks.org/dsa/function-overriding-in-programming/

- Ruby Core Documentation. (n.d.). require_relative. Retrieved September 4, 2025, from https://ruby-doc.org/core/Kernel.html#method-i-require_relative
  
- Ruby Core Documentation. (n.d.). require. Retrieved September 4, 2025, from https://ruby-doc.org/core/Kernel.html#method-i-require

---

## Presentation
- [Link video](https://www.youtube.com/watch?v=-LGrIUsAZHo)
- [Slide](https://docs.google.com/presentation/d/12AQXTwxs6nZAg_m5MjcnqZ0vEBm_6qxs1V23kI7xu74/edit?usp=sharing)



---
