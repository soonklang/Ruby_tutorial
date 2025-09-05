# Freezing Objects

## การแช่แข็ง Objects
ทุกวัตถุที่ถูกสร้างมาจะสามารถถูกแช่แข็งได้ โดยที่วัตถุที่ถูกแช่แข็งจะไม่สามารถถูกดัดแปลงได้ ไม่สามารถเปลี่ยน Instance variables ได้ และไม่สามารถสร้าง singleton method ได้
สมมุคิถ้า Class ถูกแช่แข็ง จะไม่สามารถเพิ่ม,ลบ หรือ เปลี่ยนแปลง method ได้

### Syntax: ObjectName.freeze

## ตัวอย่าง Ruby
```ruby
# การแช่แข็ง Object ของภาษา Ruby

# สร้างคลาส
class Addition
   # constructor method
   def initialize(x, y)
      @a, @b = x, y
   end

   # methods การเขาถึง
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

## OUTPUT
```
Addition object is frozen object 
main.rb:20:in `setA=': can't modify frozen Addition (RuntimeError) 
from main.rb:39:in `'
```

สังเกตว่าใน Terminal บรรทัดที่ 2 เมื่อมีการพยายามแก้ไข Object จะมีการขึ้นเตือน (RuntimeError) และหยุดรันทันที

เราสามารถตรวจสอบได้ว่าวัตถุนี้ถูกแช่แข็งหรือไม่โดยการใช้

### Syntax: ObjectName.frozen?
```
a = []
a.frozen? # => return ค่าเป็น false
a.freeze
a.frozen? # => return ค่าเป็น true
```

