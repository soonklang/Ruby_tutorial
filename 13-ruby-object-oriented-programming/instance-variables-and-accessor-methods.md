# Instance Variables and Accessor Methods
# Instance Variables คืออะไร?
  Instance variables คือ ตัวแปรที่กำหนดไว้ใน class จะใช้งานได้เพียงแค่แต่ละวัตถุของ class นั้นที่ถูกสร้างขึ้นมาเท่านั้น โดยภาษา Ruby จะใช้สัญลักษณ์ @ นำหน้า variables ที่กำหนดไว้เพื่อเข้าถึงตัวแปรภายใน class แต่การที่จะเข้าถึงจากนอก class จะต้องใช้ public method ที่เรียกว่า Accessor Methods (setter และ getter)

# Accessor Methods คืออะไร?
  Accessor Methods คือ Method ใน class ที่สามารถอ่านหรือเขียน Instance variables จากภายนอกคลาสได้ เพราะ Instance variables ไม่สามารถเข้าถึงจากนอก class ได้โดยตรง

# ตัวอย่างของการกำหนด Instance Variables
```ruby
class Student
  def initialize(id,name)
    #กำหนด instance variables
    @id = id
    @name = name
  end
end

student = Student.new(1,"Prayat")
```
จากโค้ด การกำหนด instance Variables จะมีสัญลักษณ์ @ ข้างหน้าตัวแปรที่กำหนดไว้ และ student จะทำการสร้างวัตถุจาก student เพื่อเก็บค่า id และ name เอาไว้

# ตัวอย่างของการกำหนด Accessor Methods
```ruby
class Student
  def initialize(id,name)
    #กำหนด instance variables
    @id = id
    @name = name
  end

  def getId()
    @id
  end

  def getName()
    @name
  end

  def setId(id)
    @id = id
  end

  def setName(name)
    @name = name
  end
end

student = Student.new(1,"Prayat")
puts student.getName() #output Prayat
student.setName("Tony")
puts student.getName() #output Tony
```

 


