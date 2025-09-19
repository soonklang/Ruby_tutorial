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
