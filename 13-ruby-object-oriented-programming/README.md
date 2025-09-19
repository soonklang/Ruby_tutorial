# Ruby Object Oriented Programming
ในส่วนนี้คุณจะได้เรียนรู้เกี่ยวกับพื้นฐานของการเขียนโปรแกรมแบบเชิงวัตถุด้วยภาษาโปรแกรม Ruby เพื่อให้คุณสามารถสร้างสรรค์ผลงานที่น่าทึ่งของตนเองได้ โดยคุณจะได้เรียนรู้หัวข้อที่เป็นพื้นฐานสำคัญดังต่อไปนี้:

- [Create an Object From Class](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/creating-an-object-from-a-class.md)
- [Defien Ruby Class](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/define-ruby-class.md)
- [Freezing Object](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/define-ruby-class.md)
- [Instance Method](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/instance-methods.md)
- [Instance Variables and Accessor Methods](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/instance-variables-and-accessor-methods.md)
- [Operator Overloading in Ruby](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/operator-overloading-in-ruby.md)
- [Passing Parameter to New Method](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/passing-parameters-to-new-method.md)
- [Private Classes in Ruby](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/private-classes-in-ruby.md)
- [Public and Private](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/public-and-private.md)
- [Ruby Class Inheritance](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/ruby-class-inheritance.md)
- [Ruby Class Variables](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/ruby-class-variables.md)
- [Static Members](https://github.com/soonklang/Ruby_tutorial/blob/main/13-ruby-object-oriented-programming/static-members.md)

  # แบบฝึกหัด
  
## 6. Operator Overloading in Ruby
### Q : จงเขียนคำสั่งในภาษา Ruby ที่เปลี่ยนแปลงการทำงานของ operator `/` เป็นการเชื่อมระหว่าง String และ String โดยมีข้อความ `" and "` คั่นแต่ละ String ที่ทำการ `/` พร้อมแสดงผลข้อความ

```ruby

Class OverloadExample

  attr_accessor :text

  def ____
    ____
  end

  def ____
    ____
  end

end

```

<details>
<summary> เฉลยข้อที่ 6. </summary>
  
```ruby
class OverloadExample

  attr_accessor :text

  def initialize(text)
    @text = text
  end

  def /(other)
    OverloadExample.new(@text + " and " + other.text)
  end

end

good = OverloadExample.new("good")
bad = OverloadExample.new("bad")

a = good / bad
puts a.text
```

</details>

















