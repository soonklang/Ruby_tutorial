# Variable scope
# What is Variable Scope?

 คือขอบเขต ที่ ตัวแปรสามารถเข้าถึงและใช้งานได้ในโปรแกรม ตัวแปรแต่ละประเภทจะถูกประกาศโดยใช้อักขระพิเศษที่ด้านหน้าของชื่อตัวแปร
 
 Ruby แบ่งเป็น 4 ประเภทหลัก  ได้แก่ :

- *Local Variable* ([a-z] or _)

   ตัวแปรที่ประกาศภายในเมธอด บล็อก หรือคลาส และสามารถเข้าถึงได้เฉพาะภายในขอบเขตนั้นๆ

  ## ตัวอย่าง
  Ruby :
      
       x = 10            // x เป็น Local Varible        
       puts x
 

  
- *Global Variable*

  เริ่มต้นด้วย $ สามารถเข้าถึงได้จากทุกที่ในโปรแกรม แต่ไม่แนะนำให้ใช้บ่อย เนื่องจากอาจทำให้โปรแกรมซับซ้อนและเข้าใจยาก

   ## ตัวอย่าง
  Ruby :
 
        $global = 100      // $ เป็น Global Variable
        puts $global

- *Instance Variable*

  เริ่มต้นด้วย @ เช่น @name ใช้เก็บข้อมูลที่เกี่ยวข้องกับอินสแตนซ์ของคลาสนั้นๆ และสามารถเข้าถึงได้ภายในเมธอดของคลาสเดียวกัน

   ## ตัวอย่าง
  Ruby :

       @name = "phonchanok"    // @ เป็น Instance Variable
       puts @name

  
- *Class Variable*

  เริ่มต้นด้วย @@  ใช้เก็บข้อมูลที่ใช้ร่วมกันระหว่างคลาสและซับคลาสของมัน

    ## ตัวอย่าง
  Ruby :

       class Test
           @@count = 0        // @@ เป็น Class Variable
       end       



นอกจากนี้ Ruby ยังมีชนิดค่าคงที่อีกหนึ่งชนิด คือ
- *Constant*
  
    เริ่มต้นด้วยตัวอักษรพิมพ์ใหญ่  ใช้เก็บค่าที่ไม่ควรเปลี่ยนแปลง แต่ Ruby อนุญาตให้เปลี่ยนค่าได้ หากเปลี่ยนจะมีการแจ้งเตือน

    ## ตัวอย่าง
  Ruby :
  
       PI = 3.14    // PI เป็น Constant

---
## เปรียบเทียบวิธีการใช้ Scope ขอภาษา C,Java,Python

- *Local Variable*
  
  C และ Java ต้องกำหนดชนิดข้อมูล (int, String) ใช้ได้เฉพาะฟังก์ชันหรือเมธอด

   เช่น

         int x = 10;     # ต้องกำหนดชนิดข้อมูล ในตัวอย่างคือ int
 
  Python  ประกาศง่าย ไม่ต้องกำหนดชนิดข้อมูล ใช้ได้เฉพาะบล็อกหรือฟังก์ชันหรือเมธอด

   เช่น

         x = 10    # ไม่ต้องกำหนดชนิดข้อมูล ซึ่งเหมือน Ruby


- *Global Variable*

  C จะประกาศนอกฟังก์ชัน ใช้ได้ทุกที่ในไฟล์

   เช่น

        int global = 100;  #ประกาศนอกฟังก์ชัน
        int main() {
        printf("%d", global);
       }

  Java ต้องใช้ static ในคลาส
  
   เช่น

       static int global = 100;
       System.out.println(global);

  Python ประกาศนอกฟังก์ชัน ถ้าต้องการแก้ค่าจากในฟังก์ชัน ต้องใช้ global

    เช่น

       global = 100   
       def show():
          print(global)
       show()

 - *Instance Variable*

 C  ต้องใช้ struct จำลอง

  เช่น

        struct Person { char* name; };

  Java และ Python  มี การเก็บค่าแยกตาม object ไม่แชร์ค่า

   เช่น
       
         String name = "Phonchanok";   #ใช้ field ของ object แต่ละตัว แยกค่าเหมือน Ruby
         System.out.println(name);    //Java


  - *Class Variable*
  
  C  ไม่มี class variable ต้องใช้ global + struct


  Java จะใช้ static ในคลาส

   เช่น  

        class Test {
        static int count = 0;
       }

  Python จะ ประกาศในคลาสโดยตรง

   เช่น

         class Test:
         count = 0

  - *Constant*

  C จะใช้ #define หรือ const

   เช่น

       const float PI = 3.14;

  Java จะใช้ final

   เช่น

        class Circle {
            static final double PI = 3.14;
       }
  Python จะใช้ชื่อพิมพ์ใหญ่

   เช่น
       
          PI = 3.14  # convention ใช้ชื่อพิมพ์ใหญ่

---
# Detecting the Scope of a Ruby Variable
คือ การตรวจสอบ ว่าตัวแปรนั้นอยู่ในขอบเขต (scope) แบบใด

 ใน Ruby สามารถ ตรวจสอบ scope ของตัวแปรได้ด้วย defined?

   เช่น
            
       x = 10
       puts defined?(x)      # => "local-variable"

       @name = "Alice"
       puts defined?(@name)  # => "instance-variable"

       $global = 5
       puts defined?($global) # => "global-variable"

       puts defined?(y)      # => nil (ไม่ได้กำหนด)

       // ถ้า defined? คืนค่าเป็น "local-variable", "instance-variable", "global-variable"  หมายถึงตัวแปรนั้นมีอยู่และ scope ตามที่แจ้ง
       // ถ้า defined? คืนค่า nil หมายถึง ตัวแปรยังไม่ถูกประกาศใน scope 

## เปรียบเทียบ การตรวจจับ scope ของตัวแปร ระหว่าง ภาษาC,Java,Python

  C

   -  ตัวแปรมี local (ในฟังก์ชัน), global (นอกฟังก์ชัน)

   -  ตรวจสอบ runtime ไม่ได้ ต้องดูจากโค้ด
   
  Java

   -  ตัวแปรมี local, instance, class(static)

   -  ตรวจสอบ runtime สำหรับ local ไม่ได้ ต้องใช้ Reflection สำหรับ object/class fields

  Python

   -  ตัวแปรมี local, instance, global

   -  ตรวจสอบได้ด้วย locals(), globals(), hasattr(obj, "attr")


  ---
  ## คลิปนำเสนอ
Link video: https://www.youtube.com/watch?v=TQt67tODIHE

  ---
  ## Presentation 
Slide : https://www.canva.com/design/DAGyulWy8wY/A91tlL0g8gkbpjGUcDpeJA/edit?utm_content=DAGyulWy8wY&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton


  ---
  ## Reference
   - Smyth, N. (2016, October 27). Ruby Variable Scope. Techotopia. https://www.techotopia.com/index.php/Ruby_Variable_Scope
   - GeeksforGeeks. (2024, May 7). Scope of a variable. https://www.geeksforgeeks.org/dsa/scope-of-a-variable
   - GeeksforGeeks. (2025, July 23). Variable scope in Java. https://www.geeksforgeeks.org/java/variable-scope-in-java
   - GeeksforGeeks. (2025, July 12). Python Scope of Variables. https://www.geeksforgeeks.org/python/python-scope-of-variables/

