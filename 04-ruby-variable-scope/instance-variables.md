# Instance Variables
**Instance Variables** ในภาษา Ruby คือตัวแปรที่เป็นสมาชิกของ Object แต่ละตัว โดยที่ Instance Varibles ต้องขึ้นต้นด้วยเครื่องหมาย @ ชื่อของInstance Variables จะเป็นไปตามกฏ local และเนื่องจาก Instance Variables ขึ้นต้นด้วยเครื่องหมาย @ อักขระตัวที่สองอาจจะเป็นตัวพิมพ์ใหญ่ได้

## 🍅 คุณสมบัติหลักของ Instance Variables มีดังนี้

⚙︎ การประกาศ Instance Variables ในภาษา Ruby ไม่จำเป็นจะต้องประกาศล่วงหน้า เราสามารถสร้างขึ้นแบบ dynamic ได้เมื่อมีการเรียกใช้งานเป็นครั้งแรก  
⚙︎ การเข้าถึง Instance Variables จะเป็นแบบ private ไม่สามารถเข้าถึงจากภายนอก class ได้โดยตรงจะต้องผ่าน methods หรือใช้ attr_reader ,attr_writer ,attr_accessor  
⚙︎ ก่อนที่จะมีการกำหนดค่า Instance Variables จะต้องมีค่าเป็น nill  
⚙︎ Object แต่ละตัวจะมี Instance Variables ที่แตกต่างกันแม้ว่าจะอยู่ใน classเดียวกัน  
⚙︎ ในการตรวจสอบ/แก้ไข สามารถทำได้ด้วย instance_variables ,instance_variable_get ,instance_variable_set ,remove_instance_variable  
## 🍅 ตัวอย่างโค้ด  
### 🌼 การกำหนดและใช้งาน  
📌 โค้ด  

      class Person
            def initialize(name, age)
              @name = name
              @age = age
            end

            def info
              "ชื่อ: #{@name}, อายุ: #{@age}"
            end
          end
    
      a = Person.new("นิว", 25)
      b = Person.new("ใหม่", 30)

      puts a.info
      puts b.info  

📌 ผลลัพธ์  

      ชื่อ: นิว, อายุ: 25  
      ชื่อ: ใหม่, อายุ: 30

☞  อันนี้แสดงให้เห็นได้ว่าแต่ละออบเจ็กต์จะมี instance variable เป็นของตัวเอง[4]  
### 🌼 ค่าเริ่มต้นเป็น nil  
📌 โค้ด  

      class Box  
            def show  
              @content  
            end
      end  
      b = Box.new  
      p b.show  

📌 ผลลัพธ์    

      nil
☞  หาก instance variable ยังไม่ได้กำหนดค่า จะต้องทำการคืนค่าเป็น nil[1]  

### 🌼 attr_accessor (getter+setter)  
📌 โค้ด  

      class User
            attr_accessor :name, :age
      end

      u = User.new
      u.name = "นิว"
      u.age  = 20

      puts u.name
      puts u.age
      
📌 ผลลัพธ์  

      นิว  
      20
☞  attr_accessor สามารถสร้างได้ทั้ง getter และ setter โดยจะสร้างให้อัตโนมัติ[2] 

### 🌼 attr_reader (get)  
📌 โค้ด  
📌 ผลลัพธ์  
☞  attr_reader จะใช้เมื่อต้องการที่จะอ่าน "อ่านได้อย่างเดียว"[2]  

### 🌼 attr_writer (set)  
📌 โค้ด  
📌 ผลลัพธ์  
☞  attr_writer จะใช้เมื่อต้องการที่จะแก้ไข "แก้ไขอย่างเดียว"[2]  
### 🌼 ตรวจสอบ instance variable  
📌 โค้ด  

      class Car
            def initialize(brand, year)  
                @brand   = brand
                @year    = year
                @running = false
            end
      end

      c = Car.new("Toyota", 2025)
      p c.instance_variables

📌 ผลลัพธ์  

      [:@brand, :@year, :@running]

☞  instance_variables จะทำการคืน array ของ instance variable กลับมาทั้งหมด [3]  

### 🌼 Reflection (set/get/remove)  
📌 โค้ด  

      class Bag; end

      bag = Bag.new
      bag.instance_variable_set(:@items, ["pen", "book"])
      p bag.instance_variable_get(:@items)

      bag.remove_instance_variable(:@items)
      p bag.instance_variables  
      
📌 ผลลัพธ์  

      ["pen", "book"]
      []
☞  สามารถที่จะกำหนดค่า อ่านค่า และลบค่าได้แบบdynamic  
## 🍅 เปรียบเทียบกับภาษา Java/C/Python  
### 🌸 เปรียบเทียบกับ Java  
|Ruby|Java|  
|-----|----|  
|@name|private String name;|
|ไม่ต้องประกาศล่วงหน้า|ต้องประกาศ type และ access modifer|  
|สร้างแบบ dynamic ได้|ต้องทำการประกศใน class definition|  
|ใช้ attr_accessor ในการสร้าง getter/setter|ต้องเขียน getter/setter methods ขึ้นเอง|  

📌 โค้ด  
Ruby  

      class Person
            attr_accessor :name
              def initialize(name)
                @name = name
              end
            end  
Java  

      public class Person {
            private String name;
            public Person(String name) {
                  this.name = name;
            }
            public String getName() {
                  return name;
            }
            public void setName(String name) {
                  this.name = name;
            }
      }

### 🌸 เปรียบเทียบกับ Python  
|Ruby|Python|  
|-----|----|  
|@name|self.name|
|สามารถเข้าถึงได้เฉพาะผ่าน methods|เข้าถึงได้โดยตรงจากภายนอก|  
|ใช้ @ prefix|ใช้ self. prefix|  
|มี attr_accessor helpers|ใช้ property decorators|  

Ruby  

      class Person
        def initialize(name)
          @name = name  # private โดยธรรมชาติ
        end
        def name
          @name
        end
      end  
Python  

      class Person:
          def __init__(self, name):
              self.name = name  # สามารถเข้าถึงจากภายนอกได้
              self._name = name  # convention สำหรับ private
    
      @property
      def name(self):
            return self._name

### 🌸 เปรียบเทียบกับ C  
|Ruby|C|  
|-----|----|  
|@member|private: int member;|
|สามารถจัดการหน่วยความจำได้อัตโนมัติ|ต้องจัดการหน่วยความจำเอง|  
|Dynamic typing|Static typing|  
|ไม่ต้องประกาศ type|ต้องระบุชนิดข้อมูล|  

Ruby  

      class Rectangle
            def initialize(width, height)
                  @width = width
                  @height = height
            end
            def area
                  @width * @height
            end
      end  
C  

      class Rectangle {
      private:
          double width;
          double height;
    
      public:
          Rectangle(double w, double h) : width(w), height(h) {}
    
          double getArea() {
              return width * height;
          }
    
          double getWidth() { return width; }
          void setWidth(double w) { width = w; }
      };

## 🍅 ข้อดีและข้อเสียของภาษาRuby(Instance Variables)  
### ข้อดี  
❖ มีการใช้งานที่งานไม่ต้องประกาศล่วงหน้าและสามารถสร้างแบบไดนามิกได้  
❖ มีความปลอดภัยเพราะเป็นแบบ private  
❖ ในภาษาRubyมีการจัดการหน่วยความจำได้อัตโนมัติ
### ข้อเสีย  
❖ ไม่สามารถตรวจสอบชนิดข้อมูลก่อนกำหนดค่าเพราะไม่มี Type Safety  
❖ อาจจะทำงานช้ากว่าภาษาที่คอมไพล์ เนื่องจากเป็น interpreted language  
❖ debug ยากเพราะไม่มีการประก่ศtypeล่วงหน้า
 
# Reference 
https://ruby-doc.org/docs/ruby-doc-bundle/UsersGuide/rg/instancevars.html นำเนื้อหาคุณสมบัติของ Instance Variables มาใช้ สืบค้นเมื่อวันที่ 1 กันยายน 2568 

https://docs.ruby-lang.org/en/3.3/syntax/assignment_rdoc.html  นำเนื้อหาเรื่องInstance Variablesเรื่องกฎการตั้งชื่อมาใช้ สืบค้นเมื่อวันที่ 1 กันยายน 2568  

https://ruby-doc.org/core/Module.html?utm_source=chatgpt.com Ruby Core API – Module#attr_reader, Module#attr_writer, Module#attr_accessor.  

https://ruby-doc.org/3.4.1/Object.html?utm_source=chatgpt.com Ruby Core API – Object#instance_variables, #instance_variable_get, #instance_variable_set, #remove_instance_variable.  

[4]https://www.tutorialspoint.com/ruby/ruby_variables.htm?utm_source=chatgpt.com  TutorialsPoint – Ruby Variables.  

[2] Ruby Core API – Module#attr_reader, Module#attr_writer, Module#attr_accessor. https://ruby-doc.org/core/Module.html

[1]https://docs.ruby-lang.org/en/master/syntax/assignment_rdoc.html#label-Instance+Variables  Ruby Official Documentation – Syntax: Assignment / Instance Variables.



