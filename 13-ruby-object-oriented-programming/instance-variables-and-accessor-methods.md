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
#### Ruby
```ruby
class Student
  # Constructor
  def initialize(id,name)
    # กำหนด instance variables
    @id = id
    @name = name
  end
end
```
จากโค้ดด้านบน Instance Variables ในคลาส Student คือ id และ name ที่ประกาศไว้ใน methods initialize ที่รับค่าจากภายนอกคลาสแล้วนำมาเก็บไว้ ทีนี้เรามาลองเทียบกับภาษาอื่นบ้าง

#### Java
```java
public class Student{
	# กำหนด instance variables
    int id;
    String firstName;
    String lastName;
    int age;
	
     // Constructor
    public Student(int id, String firstName, String lastName, int age) {
        this.id = id;
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
}
```
จากโค้ดด้านบน Instance Variables ของ Java จำเป็นต้องประกาศนอก Constructor ด้วยและตัว Instance Variables ไม่จำเป็นต้องมีสัญลักษณ์ @ เหมือนภาษา Ruby แต่จะมีการกำหนด Datatypes ของตัวแปรและมีการกำหนด access specifier ว่าจะเป็นแบบไหน เช่น ถ้าไม่กำหนด java จะกำหนดให้เป็น default โดยอัตโนมัติและทำให้ภายนอกคลาสจะเข้าถึงตัวแปรนั้นได้ แต่ถ้าไม่ต้องการก็ต้องกำหนดให้เป็น private ส่วนภายใน Constructor Instance Variables จะต้องใช้ this. เพื่อบ่งบอกถึงตัวแปรภายในคลาสไม่ใช่ parameter ที่รับเข้ามา


#### Python
```python
class Student:
    # Constructor
    def __init__(self, firstName, lastName, age, id):
        # กำหนด Instance variables
        self.firstName = firstName
        self.lastName = lastName
        self.age = age
        self.id = id
```
จากโค้ดด้านบน Instance Variables ของ Python จะประกาศข้างใน Constructor เหมือน Ruby แต่จะใช้ self. แทน @ หน้าชื่อตัวแปร

#### C
เนื่องจากภาษา C ไม่มีหลักการ OOP หรือการสร้างวัตถุจาก Class แต่มีแนวคิดที่คล้ายกันคือ struct
```c
struct Students {   
	int id;
	char firstName[50];
	char lastName[50];
	int age;       
};
```
จากโค้ดด้านบน เนื่องจาก C ไม่มี class แต่ก็มี struct ที่มีหลักการคล้ายกัน โดยหลักการคือจะจัดกลุ่มตัวแปรที่เกี่ยวข้องไว้ในที่เดียวกัน แต่ละตัวแปรจะถูกเรียกว่า member ของ struct อาจจะจำลองเป็น instance variable ได้

### ตัวอย่างที่ 2
เนื่องจากตัวอย่างที่ 1 เรายังไม่สามารถเข้าถึง Instance Variables ใน Ruby ได้ ดังนั้นเราต้องเพิ่ม Accessor Methods (getter , setter) เข้าไปในคลาสให้สามารถเข้าถึงได้เพื่อที่จะสามารถอ่านและแก้ไขได้จากนอกคลาส
#### Ruby
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
puts "id #{student.getId()} #{student.getFirstName()} #{student.getLastName()} age #{student.getAge()}" #output id 1 Prayat Jutha age 15
```

จากโค้ด เมื่อมี methods getter และ setter ก็จะสามารถเข้าถึง Instance Variables นอกคลาสได้แล้วผ่านการเรียกใช้ Accessor Methods ทีนี้เราลองเปรียบเทียบกับภาษาอื่นกัน

#### Java
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
        System.out.println("Id " + student.id);
		System.out.println(student.getFirstName() + " " + student.getLastName() + " age " + student.getAge() );
		//output id 1 Prayat Jutha age 15
    }
}
```
จากโค้ดด้านบน เมื่อตัวแปรกำหนด access specifier เป็น private จึงทำให้ไม่สามารถเข้าถึงค่าของตัวแปรได้โดยตรงดังนั้นจึงใช้ methods getter และ setter เหมือนภาษา Ruby แต่ตัว methods จะมี access specifier แล้วถูกกำหนดให้เป็น public เพื่อที่ภายนอกคลาสสามารถใช้ได้ และต้องกำหนด return types เพื่อกำหนดว่า methods นี้จะต้อง return ค่าอะไรออกมาแต่ปกติจะถูกตั้งให้เป็น void ส่วนตัว methods setter จะต้องกำหนด dataypes ของค่าที่รับเข้ามา ส่วนการกำหนดและคืนค่ามี syntax ที่คล้ายกับ Ruby ยกเว้นแต่ตัว getter ที่ต้องมี return นำหน้า instance variables

#### Python
```python
class Student:
    def __init__(self, firstName, lastName, age, id):
        # กำหนด Instance variables
        self.__firstName = firstName
        self.__lastName = lastName
        self.__age = age
        self.__id = id

    # getter
    @property
    def firstname(self):
        return self.__firstName

    @property
    def lastname(self):
        return self.__lastName

    @property
    def age(self):
        return self.__age

    @property
    def id(self):
        return self.__id

    # setter
    @firstname.setter
    def firstname(self, value):
        self.__firstName = value

    @lastname.setter
    def lastname(self, value):
        self.__lastName = value

    @age.setter
    def age(self, value):
        self.__age = value

    @id.setter
    def id(self, value):
        self.__id = value

student1 = Student("Prayat", "Jutha", 15, 1)
student1.__firstName = "Adison"
print("ID", student1.id, student1.firstname, student1.lastname,"age" ,student1.age) #output ID 1 Prayat Jutha age 15
```
จากโค้ดด้านบน เนื่องจากภาษา Python อนุญาติให้ภายนอกคลาสเข้าถึงตัวแปรได้โดยตรง ไม่เหมือนกับภาษา Ruby แต่ถึงอย่างนั้น Python ก็มีวิธีที่ทำให้คล้ายกันนั้นก็คือ การเพิ่ม "_" 2 ตัว นำหน้า instance variable เป็นตัวแปรแบบ private เพื่อไม่ให้ภายนอกคลาสสามารถอ้างอิงถึงตัวแปรได้ เมื่อลองเปรียบเทียบกับ Ruby จะเห็นว่า
- ตัว getter จะมี @property decorator ก่อนที่จะสร้าง methods โดยตัว methods ต้องรับ self เข้ามา และต้องมี return นำหน้า instance variables ถึงจะสามารถส่งค่าออกไปได้ ไม่เหมือนภาษา Ruby ที่สามารถจะ return ค่าออกไปได้เลยเพียงแค่ประกาศ instance variables
- ตัว setter จะมี @ชื่อตัวแปร.setter decorator ก่อนที่จะสร้าง methods โดยตัว methods ต้องรับ self และ value แต่ของ Ruby สามารถรับแค่ value อย่างเดียวได้ ส่วนการกำหนดค่าใหม่นั้นมีการเขียน syntax ที่คล้ายกัน

จากโค้ดที่เราเปรียบเทียบในหลายๆภาษาจะเห็นได้ชัดว่าถ้ามี Instance Variables เพิ่มก็ต้องมี Accessor Methods เพิ่มขึ้นด้วย ทำให้โค้ดมีขนาดที่ใหญ่มากขึ้น แต่ถึงอย่างนั้นในภาษา Ruby ยังมีวิธีการเขียน method เหล่านี้ (getter และ setter) ให้มีความรวดเร็วมากขึ้นซึ่งมีการทำงานที่คล้ายกันนั้นก็คือ
- attr_reader ทำหน้าที่เป็น methods getter โดยอัตโนมัติ
- attr_writer ทำหน้าที่เป็น methods setter โดยอัตโนมัติ
- attr_accessor ทำหน้าที่เป็นทั้ง methods setter และ getter โดยอัตโนมัติ

### ตัวอย่างที่ 3
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
จากโค้ดจะเห็นได้ชัดว่า โค้ดมีขนาดที่ลดลงแต่ก็มีการทำงานไม่ต่างจากเดิม และเนื่องจากภาษาอื่นไม่มีวิธีการเช่นเดียวกันเช่นนี้เหมือนกับ Ruby ทำให้ Ruby มีความยืดหยุ่นของภาษาและสามารถช่วยทำให้เขียนได้ง่ายขึ้นอีกด้วย

## Slide
- https://docs.google.com/presentation/d/1ug50czP39ZfiT167Tc_1DQn-nT3YmMkA/edit?usp=sharing&ouid=104190213375917016614&rtpof=true&sd=true
## Video
- https://drive.google.com/file/d/1yuPMAefQafL4d9RP251MlhXdiJJcInlc/view?usp=drive_link
## Reference

- GeeksforGeeks. (17 ธันวาคม 2019). Instance Variables in Ruby. เข้าค้นเมื่อ 31 สิงหาคม 2025 จาก https://www.geeksforgeeks.org/ruby/instance-variables-in-ruby/

- GeeksforGeeks. (11 ตุลาคม 2019).  Ruby getters and setters Method. เข้าค้นเมื่อ 31 สิงหาคม 2025 จาก https://www.geeksforgeeks.org/ruby/ruby-getters-and-setters-method/

- tutorailspoint. (ม.ป.ป). Ruby - Object Oriented. เข้าค้นเมื่อ 31 สิงหาคม 2025 จาก https://www.tutorialspoint.com/ruby/ruby_object_oriented.htm

- Bunlong. (ม.ป.ป). The Ruby Programming Language. เข้าค้นเมื่อ 1 กันยายน 2025 จาก https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/The%20Ruby%20Programming%20Language.pdf

- Ruby Programming Language. (ม.ป.ป). Classes and modules. เข้าค้นเมื่อ 2 กันยายน 2025 จาก https://www.ruby-lang.org/en/documentation/faq/8/


  
#### ภาษาอื่นๆนอกเหนือ Ruby

- Rohollah Afzali. (24 มิถุนายน 2025). Python Accessor (Getter) Methods: Mastering @property for Safer Attribute Access. เข้าค้นเมื่อ 1 กันยายน 2025 จาก https://medium.com/@rohollah2afzali/python-accessor-getter-methods-mastering-property-for-safer-attribute-access-9244380cf3c0

- GeeksforGeeks. (14 สิงหาคม 2025). Python Classes and Objects. เข้าค้นเมื่อ 1 กันยายน 2025 จาก https://www.geeksforgeeks.org/python/python-classes-and-objects/

- tutorailspoint (13 เมษายน 2023). Accessor and Mutator Methods in Python เข้าค้นเมื่อ 2 กันยายน 2023 จาก https://www.tutorialspoint.com/accessor-and-mutator-methods-in-python

- GeeksforGeeks. (29 กรกฎาคม 2025). C Structures. เข้าค้นเมื่อ 1 กันยายน 2025 จาก https://www.geeksforgeeks.org/c/structures-c/






