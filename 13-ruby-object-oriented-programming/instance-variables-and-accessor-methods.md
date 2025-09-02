# Instance Variables and Accessor Methods
## Instance Variables คืออะไร?
  ในภาษา Ruby Instance variables คือ ชื่อตัวแปรที่มีสัญลักษณ์ @ นำหน้า และค่าที่อยู่ด้านในจะจำกัดเฉพาะของแต่ละวัตถุที่ถูกสร้างขึ้นเท่านั้น ถึงวัตถุที่สร้างมาจากคลาสเดียวกันแต่ก็สามารถมีค่าของตัวแปรที่แตกต่างกันได้
  โดยลักษณะเฉพาะของ Instance variables ในภาษา Ruby ได้แก่
  - instance variable จะเป็นค่า "nil" ก่อนที่ถูกกำหนด
  - instance variable จะเป็น private โดยอัตโนมัติ
  - การที่จะเข้าถึง instance variable จากภายนอกคลาสได้ ต้องใช้ method ภายในวัตถุนั้นเท่านั้น
  - ในภาษา Ruby instance variable ไม่จำเป็นต้องประกาศไว้ล่วงหน้า ทำให้มีความยืดหยุ่น เพราะจะถูกเพิ่มเข้าไปในวัตถุแบบไดนามิกเมื่อมันถูกอ้างอิงเป็นครั้งแรก
  - instance variable เป็นของวัตถุนั้นๆ เพราะแต่ละวัตถุจะมี instance variable เป็นของตัวเองในคลาสนั้นๆ

## Accessor Methods คืออะไร?
  Accessor Methods คือ Method ในคลาสที่สามารถอ่านหรือเขียน Instance variables จากภายนอกคลาสได้ เพราะ Instance variables ไม่สามารถเข้าถึงจากนอกคลาสได้โดยตรง

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




### ตัวอย่างของการกำหนด Accessor Methods
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

จากโค้ด เมื่อมี methods getter และ setter จะสามารถเข้าถึง instance Variables นอกคลาสได้ผ่านการเรียก method ของ student

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

