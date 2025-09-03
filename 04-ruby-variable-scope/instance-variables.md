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
โค้ด  

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

ผลลัพธ์  

      ชื่อ: นิว, อายุ: 25  
      ชื่อ: ใหม่, อายุ: 30

☞  อันนี้แสดงให้เห็นได้ว่าแต่ละออบเจ็กต์จะมี instance variable เป็นของตัวเองและค่าจะไม่ทับกันแม้ว่าจะใช้คลาสเดียวกัน
### 🌼 ค่าเริ่มต้นเป็น nil  
โค้ด  

      class Box  
            def show  
              @content  
            end
      end  
      b = Box.new  
      p b.show  

ผลลัพธ์    

      nil
☞  หาก instance variable ยังไม่ได้กำหนดค่า จะต้องทำการคืนค่าเป็น nil  

### 🌼 attr_accessor (getter+setter)  
โค้ด  

      class User
            attr_accessor :name, :age
      end

      u = User.new
      u.name = "นิว"
      u.age  = 20

      puts u.name
      puts u.age
      
ผลลัพธ์  

      นิว  
      20
☞  attr_accessor สามารถสร้างได้ทั้ง getter และ setter โดยจะสร้างให้อัตโนมัติ 

### 🌼 attr_reader (getter)  
โค้ด  

      class User
        attr_reader :name

        def initialize(name)
          @name = name
        end
      end

      u = User.new("บีต")
      puts u.name     
      u.name = "ใหม่" 

ผลลัพธ์  

      บีต
      Traceback (most recent call last):
        ...
      NoMethodError: undefined method `name=' for #<User ...>

☞  attr_reader จะใช้เมื่อต้องการที่จะอ่าน "อ่านได้อย่างเดียว"ไมาสามารถแก้ค่าจากภายนอกได้

### 🌼 attr_writer (setter)  
โค้ด  

      class User
        attr_writer :name

        def initialize(name)
          @name = name
        end
      end

      u = User.new("บีต")
      u.name = "ใหม่"   
      puts u.name       

ผลลัพธ์  

      Traceback (most recent call last):
        ...
      NoMethodError: undefined method `name' for #<User ...>

☞  attr_writer จะใช้เมื่อต้องการที่จะแก้ไข "แก้ไขอย่างเดียว"ไม่สามารถอ่านค่าตรงๆได้

### 🌼 ตรวจสอบ instance variable  
โค้ด  

      class Car
            def initialize(brand, year)  
                @brand   = brand
                @year    = year
                @running = false
            end
      end

      c = Car.new("Toyota", 2025)
      p c.instance_variables

ผลลัพธ์  

      [:@brand, :@year, :@running]

☞  instance_variables จะทำการคืน array ของ instance variable กลับมาทั้งหมดในออบเจ็กต์นั้นๆ   

### 🌼 Reflection (set/get/remove)  
โค้ด  

      class Bag; end

      bag = Bag.new
      bag.instance_variable_set(:@items, ["pen", "book"])
      p bag.instance_variable_get(:@items)

      bag.remove_instance_variable(:@items)
      p bag.instance_variables  
      
ผลลัพธ์  

      ["pen", "book"]
      []
☞  methodเหล่านี้สามารถที่จะกำหนดค่า อ่านค่า และ ลบค่าได้แบบdynamic เช่น getค่าออกมา, set ค่าใหม่, remove ทิ้ง  

## 🍅 เปรียบเทียบกับภาษา Java/C/Python  
### 🌸 เปรียบเทียบกับ Java  
|Aspect|Ruby|Java|  
|-------|-----|----|  
|Declaration|@name|private String name;|  
|Type Safety|สร้างแบบ dynamic ได้|Static typing required|
|Access Control|Private|ต้องประกาศ type และ access modifer|  
|Getter/Setter|attr_accessor ในการสร้าง getter/setter|ต้องเขียนขึ้นมาเอง|
|Performance|Interpreted|Compiled|  
|Reflection|Built-in support|ใช้ Reflection API|
 
Ruby 

      class Person
            attr_accessor :name
              def initialize(name)
                @name = name
              end
            end  
      Person.new.instance_variables  

Java  
       
      public class Person {
            private String name;
            private String salutation;

            public void createSalutation() {
                  this.salutation = greeting.greet(name);
            }
      
            public String getSalutation() {
                  return salutation;
            }

            public void setName(String name) {
                  this.name = name;
            }

            public String getName() {
                  return name;
            }
      }
☞  ในภาษา Java คือ "private + public getter/setter”เปิดแบบสาธารณะแต่ต่างจากใน Ruby ที่ต้องทำการสร้าง method เพื่อเข้าถึงด้วย attr_*

### 🌸 เปรียบเทียบกับ Python  
|Aspect|Ruby|Python|  
|-------|-----|----|  
|Syntax|@name|self.name|  
|Privacy|Private|Convention-based (_name, __name)|
|Access|สามารถเข้าถึงได้เฉพาะผ่าน methods|เข้าถึงได้โดยตรงจากภายนอก|    
|Properties|มี attr_accessor helpers|ใช้ property decorators|  
|Inheritance|Single inheritance + mixins|Multiple inheritance|

Ruby  

      class Thermo
        def initialize(c = 0.0) = @c = c
        attr_accessor :c                
        def f        = (@c * 9.0/5.0) + 32
        def f=(v)    = @c = (v - 32) * 5.0/9.0
      end

      t = Thermo.new(25)
      p [t.c, t.f]     # => [25.0, 77.0]

Python  

      class Thermo:
          def __init__(self, c=0.0): self._c = c
    
          def c(self): return self._c
    
          def c(self, v): self._c = v
    
          def f(self): return (self._c * 9.0/5.0) + 32
   
          def f(self, v): self._c = (v - 32) * 5.0/9.0

      t = Thermo(25)
      print(t.c, t.f)   
      print(t._c)       


      class Safe:
          def __init__(self, s): self.__secret = s
      s = Safe("top_secret")

      print(s._Safe__secret)  

### 🌸 เปรียบเทียบกับ C 
|Aspect|Ruby|C|  
|-------|-----|----|  
|Declaration|@member|ใช้ struct เพื่อเก็บข้อมูลสมาชิกและเขียนฟังชันได้แบบอิสระ ไม่มี class|
|Memory Management|สามารถจัดการหน่วยความจำได้อัตโนมัติ Automatic GC|ต้องจัดการหน่วยความจำเอง Manual/Smart pointers|  
|Type System|Dynamic typing|Static typing|  
|Access Control|ควบคุมผ่านเมธอด attr_reader|writer|  
|Compilation|รันบน VM|Compiled ล่วงหน้าเป็นไบนารี่|  
|Performance|ช้ากว่า|เร็วกว่ามาก|

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

      #include <stdio.h>

      typedef struct {
          double width;
          double height;
      } Rectangle;

      double rect_area(const Rectangle *r) {
          return r->width * r->height;
      }

      int main(void) {
          Rectangle r = {3.0, 4.0};
          printf("%.2f\n", rect_area(&r)); /* 12.00 */
          return 0;
      }


## 🍅 ข้อดีและข้อเสียของภาษาRuby(Instance Variables)  
### ข้อดี  
❖ มีการใช้งานที่งานไม่ต้องประกาศล่วงหน้าและสามารถสร้างแบบไดนามิกได้  

❖ มีความปลอดภัยเพราะเป็นแบบ private  

❖ ในภาษาRubyมีการจัดการหน่วยความจำได้อัตโนมัติ
### ข้อเสีย  
❖ ไม่สามารถตรวจสอบชนิดข้อมูลก่อนกำหนดค่าเพราะไม่มี Type Safety  

❖ อาจจะทำงานช้ากว่าภาษาที่คอมไพล์ เนื่องจากเป็น interpreted language  

❖ debug ยากเพราะไม่มีการประก่ศtypeล่วงหน้า  

# presentation  

# Video
 
# Reference  
### Ruby  
- [Instance variables – Ruby User’s Guide (ruby-doc.org)](https://ruby-doc.org/docs/ruby-doc-bundle/UsersGuide/rg/instancevars.html) — นำเนื้อหาคุณสมบัติของ Instance Variables มาใช้<br><sub>ไม่พบวันที่เผยแพร่บนหน้าเว็บ; สืบค้นเมื่อวันที่ 1 กันยายน 2568</sub>

- [Assignment → Instance Variables – Documentation for Ruby 3.3 (docs.ruby-lang.org)](https://docs.ruby-lang.org/en/3.3/syntax/assignment_rdoc.html) — อ้างอิงกฎการตั้งชื่อและข้อเท็จจริงว่าเริ่มต้นเป็น `nil`<br><sub>ไม่พบวันที่เผยแพร่บนหน้าเว็บ; สืบค้นเมื่อวันที่ 1 กันยายน 2568</sub>

- [Accessors – Ruby User’s Guide (ruby-doc.org)](https://ruby-doc.org/docs/ruby-doc-bundle/UsersGuide/rg/accessors.html) — ทางลัด `attr_reader` / `attr_writer` / `attr_accessor`<br><sub>ไม่พบวันที่เผยแพร่บนหน้าเว็บ; สืบค้นเมื่อวันที่ 1 กันยายน 2568</sub>

- [Class: Module – Ruby Core API (ruby-doc.org/core)](https://ruby-doc.org/core/Module.html) — นิยามเมธอด `attr_accessor`, `attr_reader`, `attr_writer`<br><sub>ไม่พบวันที่เผยแพร่บนหน้าเว็บ; สืบค้นเมื่อวันที่ 1 กันยายน 2568</sub>

- [Class: Object – Documentation for Ruby 3.3 (docs.ruby-lang.org)](https://docs.ruby-lang.org/en/3.3/Object.html) — เมธอดสะท้อนข้อมูล: `instance_variables`, `instance_variable_get`, `instance_variable_set`, `remove_instance_variable`<br><sub>ไม่พบวันที่เผยแพร่บนหน้าเว็บ; สืบค้นเมื่อวันที่ 1 กันยายน 2568</sub>

- [Ruby – Variables, Constants and Literals (TutorialsPoint)](https://www.tutorialspoint.com/ruby/ruby_variables.htm) — ใช้ประกอบตัวอย่าง “การกำหนดและใช้งานตัวแปร”<br><sub>ไม่พบวันที่เผยแพร่บนหน้าเว็บ; สืบค้นเมื่อวันที่ 1 กันยายน 2568</sub>

- [Method: Module#attr_accessor – rubydoc.info](https://www.rubydoc.info/stdlib/core/Module%3Aattr_accessor) — ใช้ประกอบ “โค้ดเปรียบเทียบ Ruby” สำหรับสร้าง getter/setter อัตโนมัติ<br><sub>ไม่พบวันที่เผยแพร่บนหน้าเว็บ; สืบค้นเมื่อวันที่ 2 กันยายน 2568</sub>
### Java  
- [Adding Setter and Getter Methods – The Java EE 6 Tutorial (docs.oracle.com)](https://docs.oracle.com/javaee/6/tutorial/doc/gjbbp.html) — ใช้อธิบายแนวคิด getter/setter ฝั่ง Java เพื่อเทียบกับ `attr_*` ของ Ruby<br><sub>ไม่พบวันที่เผยแพร่บนหน้าเว็บ; สืบค้นเมื่อวันที่ 2 กันยายน 2568</sub>

### Python  
- [Built-in Functions – Python 3.x Documentation (docs.python.org)](https://docs.python.org/3/library/functions.html) — ใช้อธิบายแนวคิด `property()`/built-ins ที่เกี่ยวข้อง และแนวปฏิบัติการเข้าถึงแอตทริบิวต์<br><sub>แสดง “Last updated on Sep 03, 2025” บนหน้าเว็บ; สืบค้นเมื่อวันที่ 2 กันยายน 2568</sub>

### C  
- [ISO/IEC 9899:2024 — Programming languages — C (iso.org)](https://www.iso.org/standard/82075.html) — มาตรฐานฉบับปัจจุบันของภาษา C ใช้อ้างอิงนิยามภาษา/การใช้งาน (คอมไพล์, semantics ฯลฯ)<br><sub>เผยแพร่ 31 ตุลาคม 2024 (Edition 5); สืบค้นเมื่อวันที่ 3 กันยายน 2568</sub>
  
- [ISO/IEC 9899:201x Committee Draft N1570 — April 12, 2011 (cs.dal.ca)](https://web.cs.dal.ca/~vlado/pl/C_Standard_2011-n1570.pdf) — เอกสารฉบับร่าง C11 สำหรับรายละเอียดไวยากรณ์/ไลบรารีมาตรฐาน<br><sub>เผยแพร่ 12 เมษายน 2011; สืบค้นเมื่อวันที่ 3 กันยายน 2568</sub>

  
https://ruby-doc.org/docs/ruby-doc-bundle/UsersGuide/rg/instancevars.html นำเนื้อหาคุณสมบัติของ Instance Variables มาใช้ สืบค้นเมื่อวันที่ 1 กันยายน 2568 

https://docs.ruby-lang.org/en/3.3/syntax/assignment_rdoc.html  นำเนื้อหาเรื่องInstance Variablesเรื่องกฎการตั้งชื่อมาใช้ สืบค้นเมื่อวันที่ 1 กันยายน 2568  

นำโค้ดจาก TutorialsPoint – Ruby Variablesมาใช้ในส่วนการกำหนดและใช้งานhttps://www.tutorialspoint.com/ruby/ruby_variables.htm  สืบค้นเมื่อวันที่ 1 กันยายน 2568   
นำโค้ด (จาก Ruby Official Documentation – Syntax: Assignment / Instance Variables)มาใช้ในส่วนค่าเริ้มต้นhttps://docs.ruby-lang.org/en/3.3/syntax/assignment_rdoc.html#label-Instance+Variables  สืบค้นเมื่อวันที่ 1 กันยายน 2568  

นำโค้ด (จาก Ruby Core API – Module)มาใช้ในส่วนattr_accessor, attr_reader, attr_writer https://ruby-doc.org/core/Module.html  สืบค้นเมื่อวันที่ 1 กันยายน 2568    

นำโค้ด (จาก Ruby Official Documentation – Object)มาใช้ในส่วนinstance_variables, instance_variable_set/get/remove https://docs.ruby-lang.org/en/3.3/Object.html  สืบค้นเมื่อวันที่ 1 กันยายน 2568  

Java >>  https://docs.oracle.com/javaee/6/tutorial/doc/gjbbp.html  สืบค้นเมื่อวันที่ 2 กันยายน 2568  

โค้ดเปรียบเทียบRuby https://www.rubydoc.info/stdlib/core/Module%3Aattr_accessor?utm_source=chatgpt.com สืบค้นเมื่อวันที่ 2 กันยายน 2568  

Python >> https://docs.python.org/3/library/functions.html?utm_source=chatgpt.com  สืบค้นเมื่อวันที่ 2 กันยายน 2568  

C >> https://www.iso.org/standard/82075.html?utm_source=chatgpt.com    https://web.cs.dal.ca/~vlado/pl/C_Standard_2011-n1570.pdf?utm_source=chatgpt.com  สืบค้นเมื่อวันที่ 3 กันยายน 2568
