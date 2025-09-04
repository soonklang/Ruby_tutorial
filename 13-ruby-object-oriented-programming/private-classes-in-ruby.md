# Private Classes in Ruby
โดยปกติแล้วในภาษา Ruby เมื่อเราสร้าง class ขึ้นมา class นั้นจะสามารถถูกเรียกใช้จากที่ไหนก็ได้ภายในโปรแกรมของเรา แต่บางครั้งเราเมื่อเราต้องการสร้างคลาสย่อยที่เราต้องการให้เรียกใช้ได้ภายในคลาสหลักเท่านั้น เราก็ต้องสร้าง class ที่เป็น private ขึ้นมา โดยในภาษา Ruby เราจะสร้าง private class โดยการใช้ private_constant: "class_name"   
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
Marvel::Guardians.new.Quill```
