# Creating an Object from a Class
## Creating an Object from a Class คืออะไร
ในภาษา Ruby Creating an Object from a Class คือ การสร้างอ็อบเจกต์ (Object) จากคลาส (Class) เรียกว่าการสร้างอินสแตนซ์(Instantiation) ซึ่งทำได้โดยใช้เมธอด new ที่เป็นเมธอดของคลาส ที่กำหนดโครงสร้างข้อมูล (instance variables) และพฤติกรรม (methods) ของอ็อบเจกต์นั้น ๆ  

เมื่อเรียก ClassName.new(...), Ruby จะ:  
1.สร้างอ็อบเจกต์เปล่า  
2.เรียกเมธอด initialize โดยอัตโนมัติเพื่อกำหนดค่าตัวแปรภายในอ็อบเจกต์
## ตัวอย่าง Ruby
```ruby
account = BankAccount.new()
```
## ตัวอย่าง Ruby
```ruby
class BankAccount
  def initialize(name, balance)
    @name = name
    @balance = balance
  end

  def test_method
    puts "Hello from #{@name}'s account!"
  end
end

account = BankAccount.new("Alice", 1000)
account.test_method
```
## คำอธิบาย
Ruby มีลักษณะไดนามิกและเป็นภาษาแบบ interpreted เช่น Python ใช้ initialize เป็น constructor และใช้ @ นำหน้าตัวแปร instance variable โค้ดดูง่ายและกระชับกว่า Java และ C++
## ตัวอย่าง Java
```Java
class BankAccount {
    String name;
    double balance;

    BankAccount(String name, double balance) {
        this.name = name;
        this.balance = balance;
    }

    void testMethod() {
        System.out.println("Hello from " + name + "'s account!");
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount("Alice", 1000.0);
        account.testMethod();
    }
}
```
## ตัวอย่าง Python
```Python
class BankAccount:
    def __init__(self, name, balance):
        self.name = name
        self.balance = balance

    def test_method(self):
        print(f"Hello from {self.name}'s account!")

account = BankAccount("Alice", 1000.0)
account.test_method()
```
## ตัวอย่าง C++
```C++
#include <iostream>
#include <string>
using namespace std;

class BankAccount {
public:
    string name;
    double balance;

    BankAccount(string n, double b) {
        name = n;
        balance = b;
    }

    void testMethod() {
        cout << "Hello from " << name << "'s account!" << endl;
    }
};

int main() {
    BankAccount account("Alice", 1000.0);
    account.testMethod();
    return 0;
}
```
## คำอธิบาย
C++ เป็นภาษาแบบคอมไพล์และมีการจัดการหน่วยความจำโดยตรง การสร้างอ็อบเจกต์คล้าย Java แต่ใช้คำสั่ง public เพื่อกำหนดความสามารถในการเข้าถึง และต้องจัดการรายละเอียดมากกว่า
## References
- Thomas, D., Fowler, C., & Hunt, A. (2004). Programming Ruby: The Pragmatic Programmers' Guide (1st ed.). Pragmatic Bookshelf. Retrieved September 3, 2025, from https://ruby-doc.org
- Flanagan, D., & Matsumoto, Y. (2008). The Ruby Programming Language. O'Reilly Media. Retrieved September 3, 2025, from https://www.oreilly.com/library/view/the-ruby-programming/9780596516178/
- RubyMonstas. (n.d.). Ruby for Beginners. Retrieved September 3, 2025, from https://ruby-for-beginners.rubymonstas.org
- Riptutorial. (n.d.). Ruby new, allocate and initialize. Retrieved September 3, 2025, from https://riptutorial.com/ruby/example/13315/new--allocate--and-initialize
- Oracle. (n.d.). Classes and Objects. Oracle Java Tutorials. Retrieved September 3, 2025, from https://docs.oracle.com/javase/tutorial/java/javaOO/classes.html  
- Python Software Foundation. (n.d.). 9. Classes. Python Documentation. Retrieved September 3, 2025, from https://docs.python.org/3/tutorial/classes.html  
- cplusplus.com. (n.d.). C++ Classes and Objects. Retrieved September 3, 2025, from http://www.cplusplus.com/doc/tutorial/classes/
