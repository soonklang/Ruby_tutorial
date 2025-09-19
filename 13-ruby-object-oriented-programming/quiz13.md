# แบบฝึกหัด

## 5. Instance Variables and Accessor Methods
### Q : จงเขียนโปรแกรมภาษา Ruby ที่มีการสร้างคลาส Animals โดยสัตว์แต่ละตัว รหัสประจำตัว ชนิด ชื่อ อายุ ของสัตว์กำกับไว้ พร้อมแสดงข้อความ
<details>
<summary> เฉลยข้อที่ 5. </summary>
  
```ruby

class Animals
  attr_accessor :animal_id
  attr_accessor :species
  attr_accessor :name
  attr_accessor :age

   def initialize(animal_id, species, name, age)
    @animal_id = animal_id   # รหัสสัตว์
    @species   = species     # ชนิด เช่น ช้าง, สิงโต
    @name      = name        # ชื่อ
    @age       = age         # อายุ
  end
end

animal_1 = Animals.new(1,"elephant","Khan Kluay",5)
animal_2 = Animals.new(2,"lion","Simba",7)

puts "ID: #{animal_1.animal_id}, species: #{animal_1.species}, name: #{animal_1.name}, age: #{animal_1.age} years old"
puts "ID: #{animal_2.animal_id}, species: #{animal_2.species}, name: #{animal_2.name}, age: #{animal_2.age} years old"

```

</details>

## 6. Operator Overloading in Ruby
### Q : จงเขียนคำสั่งในภาษา Ruby ที่เปลี่ยนแปลงการทำงานของ operator `/` เป็นการเชื่อมระหว่าง String และ String โดยมีข้อความ `" and "` คั่นแต่ละ String ที่ทำการ `/` พร้อมแสดงผลข้อความ

```ruby

class OverloadExample

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
