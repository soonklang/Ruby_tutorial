# Freezing Objects

## การแช่แข็ง Objects
ทุกวัตถุที่ถูกสร้างมาจะสามารถถูกแช่แข็งได้ โดยที่วัตถุที่ถูกแช่แข็งจะไม่สามารถถูกดัดแปลงได้ ไม่สามารถเปลี่ยน Instance variables ได้ และไม่สามารถสร้าง singleton method ได้
สมมติว่า Class ถูกแช่แข็ง จะไม่สามารถเพิ่ม,ลบ หรือ เปลี่ยนแปลง method ได้
> Syntax: ObjectName.freeze

## ตัวอย่าง Ruby
```ruby
# การแช่แข็ง Object ของภาษา Ruby

# สร้างคลาส
class Addition
   # constructor method
   def initialize(x, y)
      @a, @b = x, y
   end

   # methods เข้าถึงค่า
   def getA
      @a
   end
   def getB
      @b
   end

   # methods กำหนดค่า
   def setA=(value)
      @a = value
   end
   def setB=(value)
      @b = value
   end
end

# สร้างวัตถุ
add = Addition.new(10, 20)

# แช่แข็งวัตถุ 
add.freeze
if( add.frozen? )
   puts "Addition object is frozen object"
else
   puts "Addition object is normal object"
end

# ลองใช้ methods กำหนดค่า
add.setA = 30
add.setB = 50

# ลองใช้ accessor การเข้าถึง
add.getA()
add.getB()

puts "A is : #{add.getA()}"
puts "B is : #{add.getB()}"
```

### OUTPUT
```
Addition object is frozen object 
main.rb:20:in `setA=': can't modify frozen Addition (FrozenError) 
from main.rb:39:in `'
```

สังเกตว่าใน Terminal บรรทัดที่ 2 เมื่อมีการพยายามแก้ไข Object จะมีการขึ้นเตือน (FrozenError) และหยุดรันทันที

เราสามารถตรวจสอบได้ว่าวัตถุนี้ถูกแช่แข็งหรือไม่โดยการใช้
### Syntax: ObjectName.frozen?
```ruby
a = []
a.frozen? # => return ค่าเป็น false
a.freeze
a.frozen? # => return ค่าเป็น true
```

## เทียบกับภาษา Java
ภาษาจาวาไม่มีเมธอด freeze แต่การ immutability (การไม่เปลี่ยนรูป) สามารถทำได้ด้วยการใช้คีย์เวิร์ด "final" นำหน้าหรือตัวแปร
###Syntax:
```java
public class FinalTest {
    public static void main(String[] args) {
        final int x = 10; // กำหนดให้ตัวแปรนี้เป็น final
        x = 20;  // Error: ไม่สามารถเปลี่ยนค่าในตัวแปรได้
        System.out.println(x);
    }
}
```
### แต่เมื่อ final ถูกวางไว้หน้าวัตถุตอนที่ถูกสร้าง ตัวแปรภายในวัตถุจะยังคงสามารถเปลี่ยนแปลงค่าได้
```java
class Person {
    String name;
    Person(String name) {
        this.name = name;
    }
}

public class FinalObjectExample {
    public static void main(String[] args) {
        final Person p = new Person("Alice");
        p.name = "Bob"; // สามารถเปลี่ยนค่าภายใน Object ได้
        System.out.println(p.name); // Output เป็น Bob
        p = new Person("Charlie"); // Compile-time error (ไม่สามารถเปลี่ยนให้วัตถุ p ไปสร้าง object ใหม่ได้)
    }
}
```

## REFERENCES
Ruby Documentation's Freezing Method https://docs.ruby-lang.org/en/3.4/Array.html#method-i-freeze

GeeksForGeeks's Freezing Objects | Ruby https://www.geeksforgeeks.org/ruby/freezing-objects-ruby/

Java Documentation's Final Keyword: https://docs.oracle.com/javase/tutorial/essential/concurrency/imstrat.html

GeeksForGeeks's Final Keyword Tutorial https://www.geeksforgeeks.org/java/final-keyword-in-java/
