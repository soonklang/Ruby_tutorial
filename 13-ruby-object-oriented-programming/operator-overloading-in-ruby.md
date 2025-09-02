# Operator Overloading in Ruby

### Operator Overloading คืออะไร

Operator Overloading คือ การกำหนดลักษณะการทำงานของ operator เช่น + , - , * , / , == เพื่อให้เหมาะสมกับการทำงานของแต่ละ object ที่ใช้งาน

ใน Ruby Operator Overloading สามารถกำหนดโดยสร้าง def ในแต่ละ class เพื่อใช้งานกับ operator ต่างๆได้


```ruby

class OverloadingTest
  attr_accessor :text

  def initialize(text)
    @text = text
  end

  def *(t)
    a = ""
    t.times{
      a = a + "Very "
    }
    OverloadingTest.new(a + @text)
  end

end

good = OverloadingTest.new("Good")
bad = OverloadingTest.new("Bad")

good10_fake = "Good" * 10
bad3_fake = "Bad" * 3
good10 = good * 10
bad3 = bad * 3

puts good10_fake
puts bad3_fake
puts good10.text
puts bad3.text

```

Output:
Very Very Very Very Very Very Very Very Very Very Good
Very Very Very Bad

จะสังเกตได้ว่า เมื่อมีการ Overloading operator "*" จะเพิ่มจำนวนรอบของคำว่า "Very " ไปตามจำนวนของ Integer
ที่ * กับ object ที่กำหนดขึ้นเอง

# Ref (WIP)

## Ruby
https://www.geeksforgeeks.org/ruby/operator-overloading-in-ruby/
https://clouddevs.com/ruby/operator-overloading/
## Compiler
https://onecompiler.com/ruby

## C++
https://en.cppreference.com/w/cpp/language/operators.html
https://www.geeksforgeeks.org/cpp/operator-overloading-cpp/
