# Operator Overloading in Ruby

**Operator Overloading** คือ การกำหนดลักษณะการทำงานของ operator เช่น + , - , * , / , == เพื่อให้เหมาะสมกับการทำงานของแต่ละ object ที่ใช้งาน

# Operator Overloading ในภาษาต่างๆ
  * Ruby -> support การใช้ operator overloading
  * Python -> support การใช้ operator overloading
  * C++ -> support การใช้ operator overloading
  * C -> ไม่ support การใช้ operator overloading
  * Java -> ไม่ support การใช้ **user defined** operator overloading

# Ruby
ใน Ruby Operator Overloading สามารถกำหนดโดยสร้าง def ในแต่ละ class เพื่อใช้งานกับ operator ต่างๆได้โดย
> def \<operator_symbol>(\<input>) { \<code> }

```ruby

class OverloadingTest                 # สร้าง class ใหม่
  attr_accessor :text

  def initialize(text)
    @text = text
  end

  def *(t)                            # Operator Overloading *
    a = ""
    t.times{                          # เติม String "Very " ตามจำนวน input
      a = a + "Very "
    }
    OverloadingTest.new(a + @text)
  end

end

good = OverloadingTest.new("Good")
bad = OverloadingTest.new("Bad")

good10_fake = "Good" * 10            # ทดลองใช้ operator แบบ default
bad3_fake = "Bad" * 3
good10 = good * 10                   # ทดลองใช้ operator ที่ overload แล้ว
bad3 = bad * 3

puts good10_fake
puts bad3_fake
puts good10.text
puts bad3.text

```

Output:<br>
> GoodGoodGoodGoodGoodGoodGoodGoodGoodGood<br>
> BadBadBad<br>
> Very Very Very Very Very Very Very Very Very Very Good<br>
> Very Very Very Bad<br>

จะสังเกตได้ว่า เมื่อมีการทำ operator overloading ตัว operator `*` จะเพิ่มจำนวนรอบของคำว่า `"Very "` ไปตามจำนวนของ Integer
ที่ `*` กับ object ของ `class OverloadingTest` 

# Python
ใน Python operator overloading สามารถกำหนดโดยสร้าง `def` ในแต่ละ class โดย operator แต่ละตัวจะ define ต่างกัน เช่น
  * `__add__`    *(a + b)*
  * `__sub__`    *(a - b)*
  * `__mul__`    *(a * b)*
  * `__truediv__`*(a / b)*
  * `__mod__`    *(a % b)*

> def \<operator_name>(\<input>) :
> > \<code>

```python

class OverloadingTest:                       # สร้าง class ใหม่
  def __init__(self, text):
    self.text = text
    
  def __mul__(self, t):                      # Operator Overloading *
    a = ""
    for k in range(t):                       # เติม String "Very " ตามจำนวน input
      a = a + "Very "
    return OverloadingTest(a + self.text)

good = OverloadingTest("Good")
bad = OverloadingTest("Bad")

good10_fake = "Good" * 10                    # ทดลองใช้ operator แบบ default
bad3_fake = "Bad" * 3
good10 = good * 10                           # ทดลองใช้ operator ที่ overload แล้ว
bad3 = bad * 3

print(good10_fake)
print(bad3_fake)
print(getattr(good10, 'text'))
print(getattr(bad3, 'text'))

```

Output:<br>
> GoodGoodGoodGoodGoodGoodGoodGoodGoodGood<br>
> BadBadBad<br>
> Very Very Very Very Very Very Very Very Very Very Good<br>
> Very Very Very Bad<br>

จะสังเกตได้ว่า เมื่อมีการทำ operator overloading ตัว operator `*` จะเพิ่มจำนวนรอบของคำว่า `"Very "` ไปตามจำนวนของ Integer
ที่ `*` กับ object ของ `class OverloadingTest`

# C++
ในภาษา C++ สามารถ operator overloading โดยสร้าง `class` ใหม่
แล้วจึง overload ด้วย
> \<class_name> operator\<operator_symbol>(\<input>) { \<code> }

```c++

#include <iostream>
#include <string>
using namespace std;

class OverloadingTest{                          // สร้าง class ใหม่
  private:
    string text = "";
  
  public:
    OverloadingTest(string text){
      this->text = text;
    }
    
    OverloadingTest operator*(int t){            // Operator Overloading *
        string a = "";
        for(int i=0 ; i<t ; i++){                // เติม String "Very " ตามจำนวน input
          a = a + "Very ";
        }
        return OverloadingTest(a + text);
    }
    
    string getText(){
      return this->text;
    }
    
};

int main() 
{
    OverloadingTest good = OverloadingTest("Good");
    OverloadingTest bad = OverloadingTest("Bad");
    
    // OverloadingTest good10_fake = "Good"*10;  // ทดลองใช้ operator แบบ default แล้วเกิด error
    // OverloadingTest bad3_fake = "Bad"*10;
    OverloadingTest good10 = good*10;            // ทดลองใช้ operator ที่ overload แล้ว
    OverloadingTest bad3 = bad*3;
    
    // cout << good10_fake;
    // cout << bad3_fake;
    cout << good10.getText();
    cout << "\n";
    cout << bad3.getText();
    
    return 0;
}

```

Output:<br>
> Very Very Very Very Very Very Very Very Very Very Good<br>
> Very Very Very Bad<br>

สาเหตุที่เกิด error เพราะว่าภาษา C++ ไม่มี default ของการ `*` `string` ด้วย `int`

# Java
ภาษา Java ไม่ support การใช้ **user defined** operator overloading แต่ยังมีการใช้ operator overloading แบบ built-in อยู่ เช่น

```java
public class Main {
    public static void main(String[] args) {
      int a = 5;
      int b = 5;
      String c = "5";
      
      System.out.println(a + b);
      
      System.out.println(a + c);
      System.out.println((a + c).getClass().getName());
  }
}
```

Output:<br>
> 10<br>
> 55<br>
> java.lang.String<br>

ในการ + ครั้งแรกเป็น `int` + `int` = `int` แต่ครั้งที่สองเป็น `int` + `String` = `String` สังเกตได้ว่า Java มีการ built-in operator overloading `+` อย่างชัดเจน

# Video
* https://www.youtube.com/watch?v=SfBqTh8XqNw

# Slide


# References
* cppreference.com. (n.p.). operator overloading. https://en.cppreference.com/w/cpp/language/operators.html/.
* Deivinson. (n.d.). How to define operator overloading in Ruby?. CloudDevs. https://clouddevs.com/ruby/operator-overloading/.
* GeeksforGeeks. (2022). Operator Overloading in Ruby. https://www.geeksforgeeks.org/ruby/operator-overloading-in-ruby/.
* GeeksforGeeks. (2025). Operator Overloading in C++. https://www.geeksforgeeks.org/cpp/operator-overloading-cpp/
* Jerry Coffin. (2010). C does not support operator overloading. Stack Overflow. https://stackoverflow.com/questions/3417413/operator-overloading-in-c/.
* Jon Skeet. (2009). Operator overloading in Java. Stack Overflow. https://stackoverflow.com/questions/1686699/operator-overloading-in-java/.
* Michael Granger. (n.d.). Operators. RUBY-DOC.ORG.  https://ruby-doc.org/3.4.1/syntax/operators_rdoc.html/.
* Programiz. (n.p.). Python Operator Overloading. https://www.programiz.com/python-programming/operator-overloading/.
* Python Software Foundation. (2025). operator — Standard operators as functions. Python.org. https://docs.python.org/3/library/operator.html/.
* Soraya S.. (2022). การเขียนบรรณานุกรม รูปแบบ APA 7th. สำนักพิมพ์มหาวิทยาลัยนเรศวร. https://www.nupress.grad.nu.ac.th/การเขียนบรรณานุกรม/.
