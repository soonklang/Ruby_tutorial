# Private Classes in Ruby
โดยปกติแล้วในภาษา Ruby เมื่อเราสร้าง class ขึ้นมา class นั้นจะสามารถถูกเรียกใช้จากที่ไหนก็ได้ภายในโปรแกรมของเรา แต่บางครั้งเราเมื่อเราต้องการสร้างคลาสย่อย(inner-class) ที่เราต้องการให้เรียกใช้ได้ภายในคลาสหลัก(outer-class) เท่านั้น เราก็ต้องสร้าง class ที่เป็น private class ขึ้นมา โดยในภาษา Ruby เราจะสร้าง private class โดยการใช้:  
`private_constant: class_name`  
ยกเว้น outer-class ที่ไม่สามารถสร้างเป็นแบบ private ได้  
**ตัวอย่าง public class ธรรมดา :**  
```ruby
# by default public
class Marvel

  # by default public
  class Guardians
      def Quill
          puts "Legendary outlaw"
        end
      def Groot
          puts "I am Groot"
        end
    end

  # by default public
  class Avengers
      def Tony
        puts "I am Iron-man"
      end
    end
end
Marvel::Avengers.new.Tony
Marvel::Guardians.new.Quill
```
**ผลลัพธ์ :**  
```
I am Iron-man
Legendary Outlaw
```
ในตัวอย่างจะเห็นได้ว่าเราสามารถเรียกใช้งาน method Tony และ Quill ซึ่งเป็น method ของคลาสย่อย(inner class) ภายนอกคลาสหลัก(outer-class) ได้ เนื่องจาก Guardians และ Avengers ประกาศเป็น public class ตาม default ของ Ruby    
**ตัวอย่าง private class :**  
```ruby
# Ruby program of accessing private class
# public
class Marvel

  # Private
  class Guardians
      def Quill
          puts "Legendary outlaw"
        end
      def Groot
          puts "I am Groot"
        end
    end

  # public   
  class Avengers
      def Tony
        puts "I am Iron-man"
      end
    end

# กำหนดให้ Guardians เป็น class แบบ private
private_constant :Guardians
end
 
Marvel::Avengers.new.Tony

# throws an error(NameError)
Marvel::Guardians.new.Quill
```
**ผลลัพธ์ :**  
```
I am Iron-man
main.rb:20:in `': private
constant Marvel::Guardians
referenced (NameError)
```
จากในตัวอย่างนี้เราจะเห็นได้ว่าเราสามารถเรียกใช้ method Tony ภายนอกคลาสหลักได้ปกติ แต่ไม่สามารถเรียก method Quill ได้เนื่องจากเราได้สร้างคลาส Guardians เป็นแบบ private class ไว้ทำให้ไม่สามารถเรียกใช้ method ของคลาสนี้ภายนอก outer-class ได้  
## ต่อมาเราจะมาเปรียบเทียบกับ private class ของภาษาอื่นๆกัน  
### Java  
ในภาษา Java เราจะสร้าง private class โดยการใช้:   
`private class class_name`  
**ตัวอย่าง :**  
```java
class OuterClass {
  int x = 10;
  #สร้าง InnerClass ให้เป็น private class
  private class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);
  }
}
```
**ผลลัพธ์ :**  
```
Main.java:13: error: OuterClass.InnerClass has private access in OuterClass
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
              ^
```
จะเห็นได้ว่าการสร้าง private class ในภาษา java นั้นเป็นการสร้างแบบตรงไปตรงมาโดยการใส่ private ไว้ด้านหน้าเลย ต่างจาก ruby ที่ต้องใช้ private_constant:class เนื้องจากไม่มี private class syntax โดยตรง  
### Python  
ในภาษา python ไม่มี private class โดยตรงแต่จะมีสิ่งที่เรียกว่า Private name mangling ซึ่งใกล้เคียงกับ private class มากที่สุด หลักการทำงานคือใส่ __ ด้านหน้าชื่อของ inner-class จากนั้น python จะทำการแปลงชื่อของ inner-class โดยอัตโนมัติ  
**หลักการทำงาน :**  
สมมุติเราสร้างคลาส __Engine(inner-class) ในคลาส car(outer-class) มันจะถูกแปลงชื่อเป็น _Car__Engine โดยอัตโนมัติ ทำให้การเรียก Car.__Engine จากภายนอกคลาส Car เกิด Error ขึ้น   
**ตัวอย่าง :**  
```python
class Car:
    class __Engine: # ใช้ __ นำหน้าชื่อ
        def start(self):
            print("engine started")

try:
   engine = Car.__Engine()
except AttributeError as e:
    print(f"\nพยายามเรียก __Engine โดยตรง -> เกิดข้อผิดพลาด: {e}")
```

