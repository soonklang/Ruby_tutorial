# Operator Overloading in Ruby

### Operator Overloading คืออะไร

Operator Overloading คือ การกำหนดลักษณะการทำงานของ operator เช่น + , - , * , / , == เพื่อให้เหมาะสมกับการทำงานของแต่ละ object ที่ใช้งาน

# Ruby
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
GoodGoodGoodGoodGoodGoodGoodGoodGoodGood
BadBadBad
Very Very Very Very Very Very Very Very Very Very Good
Very Very Very Bad

จะสังเกตได้ว่า เมื่อมีการ Overloading operator "*" จะเพิ่มจำนวนรอบของคำว่า "Very " ไปตามจำนวนของ Integer
ที่ * กับ object ที่กำหนดขึ้นเอง

# Python

```python

class OverloadingTest:
  def __init__(self, text):
    self.text = text
    
  def __mul__(self, t):
    a = ""
    for k in range(t):
      a = a + "Very "
    return OverloadingTest(a + self.text)

good = OverloadingTest("Good")
bad = OverloadingTest("Bad")

good10_fake = "Good" * 10
bad3_fake = "Bad" * 3
good10 = good * 10
bad3 = bad * 3

print(good10_fake)
print(bad3_fake)
print(getattr(good10, 'text'))
print(getattr(bad3, 'text'))

```

Output:
GoodGoodGoodGoodGoodGoodGoodGoodGoodGood
BadBadBad
Very Very Very Very Very Very Very Very Very Very Good
Very Very Very Bad

# Ref (WIP)

## Ruby
https://www.geeksforgeeks.org/ruby/operator-overloading-in-ruby/
https://clouddevs.com/ruby/operator-overloading/

## Python
https://www.programiz.com/python-programming/operator-overloading

## Compiler
https://onecompiler.com/

## C++
https://en.cppreference.com/w/cpp/language/operators.html
https://www.geeksforgeeks.org/cpp/operator-overloading-cpp/
