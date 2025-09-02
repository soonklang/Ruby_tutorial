# Instance Variables and Accessor Methods
## Instance Variables คืออะไร?
  ในภาษา Ruby Instance Variables คือ ชื่อตัวแปรที่มีสัญลักษณ์ @ นำหน้า และค่าที่อยู่ด้านในจะจำกัดเฉพาะของแต่ละวัตถุที่ถูกสร้างขึ้นเท่านั้น ถึงวัตถุที่สร้างมาจากคลาสเดียวกันแต่ก็สามารถมีค่าของตัวแปรที่แตกต่างกันได้
  โดยลักษณะเฉพาะของ Instance Variables ในภาษา Ruby ได้แก่
  - Instance Variables จะเป็นค่า "nil" ก่อนที่ถูกกำหนด
  - Instance Variables จะเป็น private โดยอัตโนมัติ
  - การที่จะเข้าถึง Instance Variables จากภายนอกคลาสได้ ต้องใช้ method ภายในวัตถุนั้นเท่านั้น (getter และ setter)
  - ในภาษา Ruby Instance Variables ไม่จำเป็นต้องประกาศไว้ล่วงหน้า ทำให้มีความยืดหยุ่น เพราะจะถูกเพิ่มเข้าไปในวัตถุแบบไดนามิกเมื่อมันถูกอ้างอิงเป็นครั้งแรก
  - Instance Variables เป็นของวัตถุนั้นๆ เพราะแต่ละวัตถุจะมี Instance Variables เป็นของตัวเองในคลาสนั้นๆ

## Accessor Methods คืออะไร?
  Accessor Methods คือ Method ในคลาสที่สามารถอ่านหรือเขียน Instance variables จากภายนอกคลาสได้ เพราะ Instance Variables ไม่สามารถเข้าถึงจากนอกคลาสได้โดยตรง

### ตัวอย่างที่ 1
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
จากโค้ดด้านบน Instance Variables ในคลาส Student คือ id และ name แต่เนื่องจากตอนนี้ยังไม่สามารถเข้าถึง Instance Variables ได้จึงต้องดูตัวอย่างต่อไป

### ตัวอย่างที่ 2
```ruby
class Student
  def initialize(id,name)
    #กำหนด instance variables
    @id = id
    @name = name
  end

  def getId()  #Accessor Methods (getter) ของ @id
    @id
  end

  def getName() #Accessor Methods (getter) ของ @name
    @name
  end

  def setId(id) #Accessor Methods (setter) ของ @id
    @id = id
  end

  def setName(name) #Accessor Methods (setter) ของ @name
    @name = name
  end
end

student = Student.new(1,"Prayat")
puts student.getName() #output Prayat
student.setName("Tony")
puts student.getName() #output Tony
```

จากโค้ด เมื่อมี methods getter และ setter ก็จะสามารถเข้าถึง instance Variables นอกคลาสได้แล้วผ่านการเรียกใช้ method แต่เนื่องจากถ้าในอนาคตมีการเพิ่ม Instance Variables มากขึ้นจะเกิดอะไรขึ้น

### ตัวอย่างที่ 3
```ruby
class Student
  def initialize(id,firstName,lastName,age)
    #กำหนด instance variables
    @id = id
    @firstName = firstName
	@lastName = lastName
	@age = age
  end

  def getId()  #Accessor Methods (getter) ของ @id
    @id
  end

  def getFirstName() #Accessor Methods (getter) ของ @firstName
    @firstName
  end

  def getLastName()  #Accessor Methods (getter) ของ @lastName
    @lastName
  end

  def getAge() #Accessor Methods (getter) ของ @age
    @age
  end

  def setId(id) #Accessor Methods (setter) ของ @id
    @id = id
  end

  def setFirstName(name) #Accessor Methods (setter) ของ @firstName
    @firstName = firstName
  end

  def setLastName(id) #Accessor Methods (setter) ของ @lastName
    @lastName = lastName
  end

  def setAge(name) #Accessor Methods (setter) ของ @age
    @age = age
  end
end

student = Student.new(1,"Prayat","Jutha",15)
puts student.getName() #output Prayat
```

### เมื่อเทียบกับ Java
```java
public class Student{
	// Instance variables (non-static)
    private int id;
    private String name;
	
     // Constructor
    public Student(int id, String name) {
        this.id = id;
        this.name = name;
    }
    
     // getters method
    public String getName() { 
    	return name; 
    }
    
    public float getId() { 
    	return id;
    }

    // setters method
    public void setName(String name) { 
    	this.name = name; 
    }
    
    public void setId(int id) { 
    	this.id = id;
    }
}
```




### เมื่อเทียบกับ Python
```python

```




## Reference (Temporary)

### Ruby








### Java
https://www.geeksforgeeks.org/java/object-oriented-programming-oops-concept-in-java/

https://www.w3schools.com/java/java_encapsulation.asp

https://www.tutorialspoint.com/java/java_object_classes.htm

### Python
https://www.geeksforgeeks.org/python/python-oops-concepts/

https://www.geeksforgeeks.org/python/python-classes-and-objects/

https://docs.python.org/3/tutorial/classes.html#class-and-instance-variables

https://www.geeksforgeeks.org/python/accessing-attributes-methods-python/

https://www.squash.io/how-to-use-class-and-instance-variables-in-python/

### C
https://www.w3schools.com/c/c_structs.php

https://www.w3schools.com/c/c_structs_pointers.php

https://www.tutorialspoint.com/cprogramming/c_structures.htm

