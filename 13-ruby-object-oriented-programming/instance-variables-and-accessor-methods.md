# Instance Variables and Accessor Methods
## Instance Variables คืออะไร?
  ในภาษา Ruby Instance Variables คือ ชื่อตัวแปรที่มีสัญลักษณ์ @ นำหน้า และค่าที่อยู่ด้านในจะจำกัดเฉพาะของแต่ละวัตถุที่ถูกสร้างขึ้นเท่านั้น ถึงวัตถุที่สร้างมาจากคลาสเดียวกันแต่ก็สามารถมีค่าของตัวแปรที่แตกต่างกันได้
  โดยลักษณะเฉพาะของ Instance Variables ในภาษา Ruby ได้แก่
  - Instance Variables จะเป็นค่า "nil" ก่อนที่ถูกกำหนดที่ method initialize
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
จากโค้ดด้านบน Instance Variables ในคลาส Student คือ id และ name ที่ประกาศไว้ใน methods initialize ที่รับค่าจากภายนอกคลาสแล้วนำมาเก็บไว้ แต่เนื่องจากตอนนี้ยังไม่สามารถเข้าถึง Instance Variables ได้จึงต้องดูตัวอย่างต่อไป

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

จากโค้ด เมื่อมี methods getter และ setter ก็จะสามารถเข้าถึง Instance Variables นอกคลาสได้แล้วผ่านการเรียกใช้ Accessor Methods แต่เนื่องจากถ้าในอนาคตมีการเพิ่ม Instance Variables มากขึ้นจะเกิดอะไรขึ้นลองดูตัวอย่างถัดไป

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
puts puts "id #{student.getId()} #{student.getFirstName()} #{student.getLastName()} age #{student.getAge()}"
#output id 1 Prayat Jutha age 15
```
จากโค้ดจะเห็นได้ชัดว่าถ้ามี Instance Variables เพิ่มก็ต้องมี Accessor Methods เพิ่มขึ้นด้วย ทำให้โค้ดมีขนาดที่ใหญ่มากขึ้น แต่ถึงอย่างนั้นในภาษา Ruby ยังมีวิธีการเขียน method เหล่านี้ (getter และ setter) ให้มีความรวดเร็วมากขึ้นซึ่งมีการทำงานที่คล้ายกันนั้นก็คือ
- attr_reader ทำหน้าที่เป็น methods getter โดยอัตโนมัติ
- attr_writer ทำหน้าที่เป็น methods setter โดยอัตโนมัติ
- attr_accessor ทำหน้าที่เป็นทั้ง methods setter และ getter โดยอัตโนมัติ

### ตัวอย่างที่ 4
```ruby
class Student
	attr_accessor :id #Accessor Methods (setter และ getter) ของ @id
	attr_accessor :firstName #Accessor Methods (setter และ getter) ของ @firstName
	attr_accessor :lastName #Accessor Methods (setter และ getter) ของ @lastName
	attr_accessor :age #Accessor Methods (setter และ getter) ของ @age
	def initialize(id,firstName,lastName,age)
    	#กำหนด instance variables
    	@id = id
    	@firstName = firstName
		@lastName = lastName
		@age = age
	end
end

student = Student.new(1,"Prayat","Jutha",15)
puts "id #{student.id} #{student.firstName} #{student.lastName} age #{student.age}"
#output id 1 Prayat Jutha age 15

student.firstName = "Taksan"
puts "id #{student.id} #{student.firstName} #{student.lastName} age #{student.age}"
#output id 1 Taksan Jutha age 15
```
จากโค้ดจะเห็นได้ชัดว่า โค้ดมีขนาดที่ลดลงแต่ก็มีการทำงานไม่ต่างจากเดิม หลังจากนี้มาลองเทียบกับภาษาอื่น

### เมื่อเทียบกับ Java
```java
public class Student{
	//กำหนด Instance variables 
    int id; //ภายนอกคลาส สามารถเข้าถึงได้
    private String firstName;
    private String lastName;
    private int age;
	
     // Constructor
    public Student(int id, String firstName, String lastName, int age) {
        this.id = id;
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
    
     // getters 
    public String getFirstName() { 
    	return firstName; 
    }

    public String getLastName() { 
    	return lastName; 
    }
    
    public int getAge() { 
    	return age;
    }

    // setters
    public void setFirstname(String firstName) { 
    	this.firstName = firstName; 
    }
    
    public void setLastName(String lastName) { 
    	this.lastName = lastName; 
    }
    
    public void setAge(int Age) { 
    	this.age = age;
    }

    public static void main(String[] args) {
        Student student = new Student(1, "Prayat", "Jutha",15);
        System.out.println("Id " + student.id); //สามารถเข้าถึง id ได้ เพราะไม่ได้กำหนดให้เป็น private
		System.out.println(student.getFirstName() + " " + student.getLastName() + " age " + student.getAge() );
		//output id 1 Prayat Jutha age 15
    }
}
```
สรุปการเปรียบเทียบ จะเห็นได้ว่า
- Java ต้องมีการกำหนด datatypes ก่อนการประกาศชื่อตัวแปรและไม่มีสัญลักษณ์ @ หรืออย่างอื่นนำหน้า
- Java จะกำหนดหรือไม่กำหนด access specifiers สำหรับ Instance Variables ก็ได้ ถ้าไม่กำหนดจะเป็น default จึงทำให้ภายนอกคลาสสามารถเข้าถึงตัวแปรภายในคลาสได้ แต่ถ้าไม่ต้องจากให้ภายนอกคลาสเข้าถึงได้ก็ต้องกำหนดเป็น private
- Java ไม่มีตัวช่วยในการเขียน methods setter และ getter ให้กระชับเหมือนกับภาษา Ruby จึงจำเป็นต้องสร้างขึ้นมาเอง ทำให้ตัวโค้ดมีขนาดที่ใหญ่กว่า
- ในคลาส Instance Variables จำเป็นต้องกำหนด this. หน้าชื่อตัวแปรที่จะกำหนดค่า เพราะเพื่อบ่งบอกว่าเป็น Instance Variables ในคลาสไม่ใช่พารามิเตอร์ที่รับเข้ามาจากภายนอกคลาส
- การเรียกใช้ method ของ Java นั้นมี syntax ที่เหมือนกับภาษา Ruby
- constructor ของ Java ต้องเหมือนกับชื่อคลาสแต่ของ Ruby ต้องสร้าง methods ชื่อ initialize


### เมื่อเทียบกับ Python

```python

```

### เมื่อเทียบกับ C

```c

```


## Reference (Temporary)

### Ruby


### Java


### Python


### C


