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












# Reference (Temporary)

# Ruby
https://www.techotopia.com/index.php/Ruby_Object_Oriented_Programming

https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/The%20Ruby%20Programming%20Language.pdf

https://www.geeksforgeeks.org/ruby/object-oriented-programming-in-ruby-set-1/

https://www.tutorialspoint.com/ruby/ruby_object_oriented.htm

# Java
https://www.geeksforgeeks.org/java/object-oriented-programming-oops-concept-in-java/

https://www.w3schools.com/java/java_encapsulation.asp

https://www.tutorialspoint.com/java/java_object_classes.htm

# Python
https://www.geeksforgeeks.org/python/python-oops-concepts/

https://www.geeksforgeeks.org/python/python-classes-and-objects/

https://docs.python.org/3/tutorial/classes.html#class-and-instance-variables

https://www.geeksforgeeks.org/python/accessing-attributes-methods-python/

https://www.squash.io/how-to-use-class-and-instance-variables-in-python/

# C
https://www.w3schools.com/c/c_structs.php

https://www.w3schools.com/c/c_structs_pointers.php

https://www.tutorialspoint.com/cprogramming/c_structures.htm

