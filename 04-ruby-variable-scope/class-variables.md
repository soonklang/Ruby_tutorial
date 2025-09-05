# Class Variables



## ตัวแปลระดับคลาส ในภาษา Ruby

ตัวแปลระดับคลาสในภาษา Ruby คือตัวแปลที่ถูกใช้งานร่วมกัน ซึ่งจะมีระหว่างคลาสและคลาสลูก (subclasses) โดย ถูกเขียนด้วยเครื่องหมาย @ 2ตัว เป็น (@@) โดยจะถูกเขียนไว้ข้างหน้าชื่อตัวแปล เช่น @@count

เนื่องจากเป็นการแชร์ค่าเดียวกันหรือก็คือค่าจะถูกแชร์เหมือนกันทั้งหมดทุกอินสแตนซ์ของคลาสนั้นๆ ถ้าอินสแตนซ์หนึ่งถูกเปลี่ยนค่าตัวแปรนี้ อินสแตนซ์อื่นก็จะเห็นค่าที่เปลี่ยนไปด้วย
		 
##		 

###  ตัวอย่างการใช้งาน:

```ruby
class User
  @@count = 0 # class variable
  
  def initialize(name)
    @name = name
    @@count += 1
  end

  def self.count
    @@count
  end
end

class Admin < User
end

user1 = User.new("Alice")
user2 = User.new("Bob")
admin1 = Admin.new("Charlie")

puts User.count
puts Admin.count
```
##
### Output:
3

3
##

ในตัวอย่างการใช้งานตัวแปร @@count ถูกแชร์ร่วมกันระหว่างคลาส User และคลาสลูก Admin ทุกครั้งที่มีการสร้าง
ออบเจกต์ใหม่จาก User หรือ Admin ค่า @@count จะถูกเพิ่มขึ้น ดังนั้นทั้ง User.count และ Admin.count จึงคืนค่าเดียวกัน

##

## การเปรียบเทียบกับภาษาอื่น

### Python

  ในภาษา Python การประกาศตัวแปรไว้ใน class ตรงๆ ตัวแปรนั้นจะเป็น class variable และแชร์กับ subclass เช่นเดียวกัน 
       
```python
    class User:
        count = 0  # class variable
    
        def __init__(self, name):
            self.name = name
            User.count += 1
    
        @classmethod
        def get_count(cls):
            return cls.count
    
    class Admin(User):
        pass
    
    u1 = User("Alice")
    u2 = User("Bob")
    a1 = Admin("Charlie")
    
    print(User.get_count())
    print(Admin.get_count())
```
##
### Output:
3

3
##

### Java
Class variables ในภาษา Java หรือเรียกว่า static variables จะถูกประกาศด้วยคีย์เวิร์ด static ภายในคลาส 
แต่ต้องอยู่นอกเมธอดตัวสร้าง (constructor) หรือบล็อกต่างๆ โดยตัวแปรระดับคลาสจะมีเพียงหนึ่งชุดต่อหนึ่งคลาสเท่านั้น 
ไม่ว่าจะสร้างออบเจกต์จากคลาสนั้นกี่ออบเจกต์ก็ตาม

```java
    class User {
    static int count = 0;
    String name;

    User(String name) {
        this.name = name;
        count++;
    }

    static int getCount() {
        return count;
    }
}

class Admin extends User {
    Admin(String name) {
        super(name);
    }
}

public class Main {
    public static void main(String[] args) {
        User u1 = new User("Alice");
        User u2 = new User("Bob");
        Admin a1 = new Admin("Charlie");

        System.out.println(User.getCount());
        System.out.println(Admin.getCount());
    }
}
```
##
### Output:
3

3
##

### C++

Class variables ในภาษา C++ คือการประกาศตัวแปรภายในคลาสโดยใช้คีย์เวิร์ด static ตัวแปรชนิดนี้จะมีเพียงชุดเดียว
สำหรับคลาสทั้งหมด ไม่ได้ขึ้นอยู่กับการสร้างออบเจกต์ในแต่ละครั้ง โดย static member variable ทำงานคล้ายกับภาษา Java

```c++
#include <iostream>
using namespace std;

class User {
public:
    static int count;   //class variable (static member variable)
    string name;

    User(string n) {
        name = n;
        count++;
    }

    static int getCount() {
        return count;
    }
};

int User::count = 0;

class Admin : public User { 
public:
    Admin(string n) : User(n) {}
};

int main() {
    User u1("Alice");
    User u2("Bob");
    Admin a1("Charlie");

    cout << User::getCount() << endl;  
    cout << Admin::getCount() << endl;  
}
```
##
### Output:
3

3
##

## ตารางสรุปการเปรียบเทียบ


| ภาษา | เปลี่ยนค่า constant | การประกาศ constant | การเข้าถึงใน method/class | การเข้าถึงจากข้างนอก |
|------|-------------------|-------------------|--------------------------|---------------------|
| **Ruby** | `ได้ (ค่าแชร์กันหมด)` | `ใช้ @@ เช่น @@count = 0` | `เรียกตรง ๆ @@count หรือผ่าน self.method` | `User.count` |
| **Python** | `ได้ (ค่าแชร์กันหมด)`| `ประกาศใน class โดยตรง เช่น count = 0` | `เรียกผ่าน cls.count`  | `User.count` |
| **Java** | `ได้ (ค่าแชร์กันหมด)` | `ใช้ static เช่น static int count;` | `เรียกตรง ๆ เช่น count หรือ ClassName.count` | `User.count`
| **C** | `ได้ (ค่าแชร์กันหมด)` | `ใช้ static เช่น static int count; และกำหนดค่า int User::count = 0; นอกคลาส` | `เรียกตรง ๆ เช่น count หรือ ClassName::count` | `User.count` |

##

## Reference

- Ruby-lang.org. (n.d.). _Classes and modules — Are there class variables?_ Ruby Programming Language FAQ. สืบค้นจาก [https://www.ruby-lang.org/en/documentation/faq/8/
- Mintbit, LLC. (2024, June 5). _Ruby Variable Scope: Class Variables vs. Instance Variables_. 
สืบค้นจาก https://www.mintbit.com/blog/ruby-variable-scope-class-variables-vs-instance-variables/
- Tutorialspoint. (2023, September 13). _What are class variables, instance variables and local variables in Java?_  สืบค้นจาก https://www.tutorialspoint.com/what-are-class-variables-instance-variables-and-local-variables-in-java
- GeeksforGeeks. (2025, July 23). _Difference between instance variable and class variable_. GeeksforGeeks.    
สืบค้นจาก https://www.geeksforgeeks.org/dsa/difference-between-instance-variable-and-class-variable/
- Tagliaferri, L. (2021, August 20). _Understanding class and instance variables in Python 3_.
สืบค้นจาก  https://www.digitalocean.com/community/tutorials/understanding-class-and-instance-variables-in-python-3 

##

