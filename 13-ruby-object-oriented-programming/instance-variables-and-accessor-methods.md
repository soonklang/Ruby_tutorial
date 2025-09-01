# Instance Variables and Accessor Methods
# Instance Variables คืออะไร?
  Instance variables คือ ตัวแปรที่กำหนดไว้ใน class จะใช้งานได้เพียงแค่แต่ละวัตถุของ class นั้นที่ถูกสร้างขึ้นมาเท่านั้น โดยภาษา Ruby จะใช้สัญลักษณ์ @ นำหน้า variables ที่กำหนดไว้เพื่อเข้าถึงตัวแปรภายใน class แต่การที่จะเข้าถึงจากนอก class จะต้องใช้ public method ที่เรียกว่า Accessor Methods (setter และ getter)

# Accessor Methods คืออะไร?
  Accessor Methods คือ Method ใน class ที่สามารถอ่านหรือเขียน Instance variables ภานในคลาสได้ เพราะใน ruby Instance Variables ไม่สามารถเข้าถึงตัวแปรได้จากภายนอก class ได้โดยตรง จึงต้องใช้ accessor methods เพื่อให้สามารถเข้าถึงได้

# ตัวอย่างของการกำหนด Instance Variables ภายใน Method
class Student
  def initialize(id,name)
    #กำหนด instance variables
    @id = id
    @name = name
  end
 end 

# ตัวอย่างของการกำหนด Accessor Methods
class Student
  def initialize(id,name)
    #กำหนด instance variables
    @id = id
    @name = name
  end

  def setId(id)
    @id = id
  end

  def setName(name)
    @name = name
  end
  
  def getId()
    @id
  end

  def getName()
    @name
  end
 end 

student = Student.new(1,"Prayat")
puts student.getId() # output 1
puts student.getName() # output Prayat

 


