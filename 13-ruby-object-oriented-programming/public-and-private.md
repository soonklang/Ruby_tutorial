# Public and Private

ในส่วนนี้เราจะมาศึกษาเรื่องของ Access Control ในภาษา Ruby อย่างเช่น public, private และรวมไปถึง protected ด้วย ว่าตัวกำหนดการเข้าถึงเป็นอย่างไรผ่านตัวอย่างที่จะทำให้เข้าใจได้ง่ายขึ้น ก่อนที่เราจะลงรายละเอียดของตัวเหล่านี้ เราขอให้คุณมีพื้นฐานที่เกี่ยวข้องกับ Access Control ใน Ruby จะเป็นประโยชน์หากคุณเข้าใจพื้นฐานเกี่ยวกลับคลาสและเมธอดในภาษาโปรแกรมต่างๆ ถ้าคุณยังไม่มีความรู้ด้านนี้ คุณสามารถศึกษาในแหล่งข้อมูลเพิ่มเติมก่อนที่จะดำเนินการเรียนรู้ได้

## Public and Private ในภาษา Ruby 
ก่อนอื่นเรามาทำความรู้จักกับ Access Control กันก่อน
Method Access Control **เป็นคำสั่งควบคุมที่กำหนดการเข้าถึงของโปรแกรมในระดับของเมธอดที่อยู่ในคลาส** โดยทั่วไปจะเรียกว่า Access Modifiers 

Access Control เป็นส่วนที่สำคัญมากๆสำหรับการเขียนโปรแกรมแบบ OOP
หลักสำคัญจะประกอบด้วย
- class variable	และ instance variable ใน Ruby visibility เป็น private เสมอ
- การควบคุมการเข้าถึงใช้ได้กับเมธอดเท่านั้น
- ไม่สามารถกำหนด access control ให้กับ instance variable และ class variable
- เมธอดแบบ private สามารถูกสืบทอดได้เหมือนเมธอดอื่นๆ

โดย Access Control จะมีหน้าที่กำหนดการเข้าถึงของเมธอดในคลาส เช่น public, private และ protected

#### `ตัวอย่างที่ 1` การใช้ public and private ใน Ruby

```ruby
# Ruby program of Public and Private method
class Vehicle
    def initialize(vehicle_name, vehicle_color)
        @vehicle_name = vehicle_name
        @vehicle_color = vehicle_color
    end
  
  # Using public method
    public
    def display
        greeting
        puts 'Your car details are: '
        puts @vehicle_name
        puts @vehicle_color
    end
  
   # Using Private method
    private
    def greeting
        puts 'Hello, user'
    end
end

# Creating object
object = Vehicle.new('Nissan', 'white')

# Calling object
object.display
```

<details>
<summary><strong>Java</strong></summary>
<pre>
<code>Sparky</code>
</pre>
</details>

จากตัวอย่าง มีการทำให้เมธอด display เป็น public และเมธอด greeting เป็น private

## วิธีการใช้

เขียน public, protected หรือ private โดยไว้ด้านบนของเมธอดหรือตัวแปรบนสุด

#### `ตัวอย่างที่ 2` เขียน public ไว้บนสุดของเมธอด
```ruby
public
def display
  greeting
  puts 'Your car details are: '
  puts @vehicle_name
  puts @vehicle_color
end
```

#### `ตัวอย่างที่ 3` เขียน private ไว้บนสุดของเมธอด
```ruby
private
def greeting
  puts 'Hello, user'
end
```

#### `ตัวอย่างที่ 4` ต้องการเมธอดที่เป็น private ถึง 3 เมธอด ต้องเขียนไว้ที่เมธอดบนสุดตำแน่งเดียว
```ruby
private
def greeting1
  puts 'Hello, user1'
end

def greeting2
  puts 'Hello, user2'
end


def greeting3
  puts 'Hello, user3'
end
```
> note : เราจะเห็นว่าเราเขียน private ที่เมธอด greeting1 อันเดียวแต่ greeting2 และ greeting3 ก็เป็น private ด้วยเช่นกัน

## Statements

1. public method สามารถเข้าถึงได้จากทุกที่ โดยสามารถใช้งานได้ภายนอกคลาส
#### `ตัวอย่างที่ 5` สร้างคลาส GoodDog แล้วมีเมธอด dog_name ที่เป็น public แล้วสร้าง object ชื่อ sparky

```ruby
class GoodDog
  DOG_YEARS = 7

  attr_accessor :name, :age

  def initialize(n, a)
    self.name = n
    self.age = a
  end

  public
  def dog_name
    puts name
  end
end

sparky = GoodDog.new("Sparky", 4)
sparky.dog_name
```

<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>Sparky</code>
</pre>
</details>

> จากผลลัพท์เราสังเกตได้ว่าเราสามารถเข้าถึงเมธอดนี้ได้ทุกที่

2. private method ไม่สามารถถูกเรียกภายนอกคลาสได้
   
#### `ตัวอย่างที่ 6` เพิ่มเมธอด human_year ที่เป็น private แล้วเรียกเมธอดนี้จาก sparky

```ruby
class GoodDog
  DOG_YEARS = 7

  attr_accessor :name, :age

  def initialize(n, a)
    self.name = n
    self.age = a
  end

  public
  def dog_name
    puts name
  end

  private
  def human_years
    DOG_YEARS * age
  end
end

sparky = GoodDog.new("Sparky", 4)
sparky.human_years
```

<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>NoMethodError</code>
</pre>
</details>

> จากผลลัพท์เราจะสังเกตว่าเราไม่สามารถเข้าถึงเมธอดที่เป็น private ได้ ดังนั้นจะเกิดข้อผิดพลาด

3. private method ของคลาสที่ประกาศจะถูกใช้ได้แค่ในคลาสของตัวเองเท่านั้น

#### `ตัวอย่างที่ 7` เราสร้างเมธอด get_human_year ที่เป็น public แล้วเรียก human_year ภายใน

```ruby
class GoodDog
  DOG_YEARS = 7

  attr_accessor :name, :age

  def initialize(n, a)
    self.name = n
    self.age = a
  end

  public
  def dog_name
    puts name
  end

  private
  def human_years
    DOG_YEARS * age
  end

  public
  def get_human_years
    puts human_years
  end
end

sparky = GoodDog.new("Sparky", 4)
sparky.get_human_years
```
<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>28</code>
</pre>
</details>

> จากผลลัพท์เราจะเห็นว่าเราจะได้ผลลัพท์ของเมธอดที่เป็น private ออกมาได้

4. ถ้าไม่ได้ประกาศว่าเป็น modifier ตัวไหน ค่า default จะเป็น public

#### `ตัวอย่างที่ 8` เราสร้างเมธอด get_human_year ที่เป็น public แล้วเรียก human_year ภายใน

```ruby
class GoodDog
  DOG_YEARS = 7

  attr_accessor :name, :age

  def initialize(n, a)
    self.name = n
    self.age = a
  end

  def human_years
    DOG_YEARS * age
  end
end

sparky = GoodDog.new("Sparky", 4)
puts sparky.get_human_years
```

> จากผลลัพท์เราจะเห็นว่าเมธอดจะเป็น public เองอัตโนมัติโดยที่เราไม่ต้องกำหนดเอง

แล้วสมมติว่าเราอยากเรียกใช้เมธอดที่เป็น private เราสามารถเรียกใช้โดยใช้เมธอดที่เป็น public ออกมาแทน
โดยเราจะเอาโค้ดจากตัวอย่างที่ 1 มาใช้อธิบาย

```ruby
# Ruby program of Public and Private method
class Vehicle
    def initialize(vehicle_name, vehicle_color)
        @vehicle_name = vehicle_name
        @vehicle_color = vehicle_color
    end
  
  # Using public method
    public
    def display
        greeting
        puts 'Your car details are: '
        puts @vehicle_name
        puts @vehicle_color
    end
  
   # Using Private method
    private
    def greeting
        puts 'Hello, user'
    end
end
```

โดยเราจะเห็นการเมธอด greeting ที่เป็น private ในเมธอด display ที่เป็น public 

ดังนั้นเริ่มต้นที่สร้าง Object สำหรับ Vehicle

```ruby
# Creating object
object = Vehicle.new('Nissan', 'white')

# Calling object
object.display
```

เมื่อเรียกเมธอด display แล้วได้ผลลัพท์ดังนี้ 
<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>Hello, user
Your car details are:
Nissan
white</code>
</pre>
</details>

โดยจากผลลัพท์บรรทัดแรก จะมาจากเมธอด greeting ที่เป็น private โดยเรียกใช้จาก display ที่เป็นpublic 

เราเริ่มต้นกันมาในระดับหนึ่ง ดังนั้นเรามาดูโค้ดที่ละเอียดขึ้นกันเพื่อความเข้าใจในรายละเอียดที่เยอะขึ้น

#### `ตัวอย่างที่ 9` สร้างคลาส Region ที่ภายในมีเมธอดต่างๆ

```ruby
class Region
 attr_accessor :name

 def initialize(name, population, area_size, continent)
   self.name = name
   self.population = population
   self.area_size = area_size
   self.continent = continent
 end

 def greeting
   puts name_info + population_info
 end

 def more_densely_populated?(other_region)
   result = population_density > other_region.population_density ? 'more' : 'less'
   puts "#{name} is #{result} densely populated than #{other_region.name}."
 end

 def the_same_continent?(other_region)
   if continent.eql?(other_region.continent)
     puts "#{name} and #{other_region.name} lie in the same continent."
   else
     puts "#{name} and #{other_region.name} lie in the different continents."
   end
 end

 def can_be_crowdy?
   if self.consider_as_densely_populated?
     puts "#{name} can be crowdy."
   else
     "There is enough space in the #{name}."
   end
 end

 protected

 attr_accessor :continent

 def name_info
   "Hello, I'm #{name}!"
 end

 private

 attr_accessor :population, :area_size

 def population_info
   " #{population} people live here."
 end

 def population_density
   population / area_size
 end

 def consider_as_densely_populated?
   population_density > self.class::HIGH_POPULATION_DENSITY
 end
end

class Country < Region
 HIGH_POPULATION_DENSITY = 300

 def own_greeting
   puts "The country name: #{name}." + population_info
 end
end

class City < Region

 HIGH_POPULATION_DENSITY = 3000

 def own_greeting
   puts name_info + " The population: #{population} people."
 end
end
```
Region เป็นคลาสแม่ที่มีเมธอดแบบ public, protected และ private ทั้ง 3 แบบ โดยที่จะมีคลาสลูกอยู่ทั้งหมด 2 ตัว คือ Country และ City โดยสืบทอดมาจาก Region 

จากตัวอย่าง ในคลาสของ Region มีเมธอดที่เป็น public อยู่คือ greeting, more_populated?, the_same_continent? และ can_be_crowdy? มีเมธอด protected คือ name_info และ เมธอด private คือ population_info, population_density และ consider_as_densely_populated? 

ในคลาสของ Country และ City จะมีเมธอด own_greeting เพิ่มขึ้นมา 

หลังจากนั้นเราจะสร้าง Object มา 3 อัน 

```
# initialization
wroclaw = City.new('Wroclaw', 638_000, 293, 'Europe')
san_francisco = City.new('San Francisco', 884_000, 121, 'Northern America')
poland = Country.new('Poland', 38_000_000, 312_000, 'Europe')
```

โดยสร้างวัตถุ wroclaw และ san_francisco จาก city และ poland จาก country

#### Section I เข้าถึง public เมธอดของคลาสแม่

```ruby
# I section
wroclaw.greeting
poland.greeting
```

<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>Hello, I'm Wroclaw! 638000 people live here.
Hello, I'm Poland! 38000000 people live here.</code>
</pre>
</details>

> เราจะเห็นว่าเมธอดที่เป็น public จะไม่มีเขียนกำกับไว้ด้านบนสุดของเมธอด เพราะ ถ้าเราไม่กำกับการเข้าถึง ค่า default จะเป็น public เสมอ

#### Section 2

```ruby
# II section
wroclaw.name_info
wroclaw.population_info
```

<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>NoMethodError
NoMethodError</code>
</pre>
</details>

> จากโค้ดตัวอย่าง เราจะเห็นว่า name_info เป็นเมธอด protected และ population_info เป็นเมธอด private โดยเมื่อเรารันจะทำให้เกิด NoMethodError เพราะเราไม่สามารถเข้าถึงเมธอดที่เป็น protected และ private จากภายนอกคลาสได้

#### Section 3 เข้าถึง protected และ private จากภายในคลาส

```ruby
# III section
wroclaw.own_greeting
poland.own_greeting
```

<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>Hello, I'm Wroclaw! The population: 638000 people.
The country name: Poland. 38000000 people live here.</code>
</pre>
</details>

> จากโค้ดตัวอย่าง เราจะเห็นว่าเมธอด own_greeting มีการเรียกใช้เมธอดที่เป็น protected และ private ในตัวของมันเอง โดยที่ตัวมันเองเป็น public 

> โดยเมธอด own_greeting ของ wroclaw จะใช้ name_info ที่เป็น protected และตัวแปร population ที่เป็น private 

> และเมธอด own_greeting ของ poland จะใช้ population_info ที่เป็น private 

> และสังเกตผลลัพท์ว่าโค้ดสามารถรันและออกผลลัพท์มาได้

#### Secition 4 ความแตกต่างระหว่าง protected และ private

```ruby
# IV section
wroclaw.more_densely_populated?(san_francisco)
wroclaw.the_same_continent?(san_francisco)
san_francisco.can_be_crowdy?
```
> ตั้งแต่บรรทัด 1-3 เป็นเมธอดแบบ public โดยภายในจะมีการใช้เมธอดแบบ protected และ private 

เริ่มต้นที่บรรทัดที 1 คลาสลูกใช้เมธอดที่เป็น public ที่ข้างในมีเมธอด private 
<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>wroclaw.more_densely_populated?(san_francisco)
=> NoMethodError</code>
</pre>
</details>

> ผลลัพท์จะได้เป็น NoMethodError เพราะ wroclaw เป็น Object ของคลาสลูกอย่าง City แต่ภายในของเมธอด more_densely_populated? มีการใช้เมธอด population_density ที่เป็น private ในคลาส Region อยู่ด้วย แล้วเนื่องจากเมธอด private สามารถใช้ได้แค่ในคลาส Region เท่านั้น ทำให้คลาส City ไม่สามารถใช้ได้

บรรทัดที่ 2 คลาสลูกใช้เมธอดที่เป็น public ที่ข้างในมีเมธอด protected 
<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>wroclaw.the_same_continent?(san_francisco)
=> Wroclaw and San Francisco lie in the different continents.</code>
</pre>
</details>

> สามารถรันได้ตามปกติเพราะ wroclaw เป็น Object ของคลาสลูกอย่าง City แล้วภายในเมธอด the_same_continent? มีการใช้ตัวแปร continent ที่เป็นแบบ protected ในคลาส Region ซึ่งเป็นคลาสแม่ แล้วคุณสมบัติของ protected สามารถใช้ได้ในคลาสลูกเช่นเดียวกับคลาสแม่

บรรทัดที่ 3 คลาสลูกใช้เมธอดที่เป็น public ที่ข้างในมีเมธอด private
<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>san_francisco.can_be_crowdy?
=> NoMethodError</code>
</pre>
</details>

> ผลลัพท์จะได้เป็น NoMethodError เช่นเดียวกับบรรทัดที่1 เพราะ san_francisco เป็น Object ของคลาสลูกอย่าง City แต่ภายในของเมธอด can_be_crowdy?  มีการใช้เมธอด consider_as_densely_populated? ที่เป็น private ในคลาส Region อยู่ด้วย แล้วเนื่องจากเมธอด private สามารถใช้ได้แค่ในคลาส Region เท่านั้น ทำให้คลาส City ที่เป็นคลาสลูกใช้ไม่ได้

แต่เราสังเกตเห็นว่า   Section3 และ Section4 ภายในมีการใช้เมธอด private เหมือนกันในเมธอดที่เรียกออกมาใช้งาน 

โดยทั้งหมดจะเกี่ยวกับ reciever 

## Reciever
Reciever คือ Object ที่เมธอดถูกเรียกใช้จากมัน
ตัวอย่าง
 - other_region.population_density --> reciever คือ other_region
 - other_region.continent -->  reciever คือ other_region
 - self.consider_as_densely_populated? --> reciever คือ self

โดยสิ่งสำคัญคือ เมธอดที่เป็น private ไม่สามารถถูกเรียกด้วย explicit receiver ได้ 

Explicit receiver คือการเรียกเมธอดที่ระบุชื่อ Object นำหน้า เช่น object.some_method 

โดยการเรียกเมธอดที่เป็น private ต้องเรียกแบบนี้ some_method เพราะ Ruby จะใช้ implicit receiver เสมอ นั่นก็คือ self 

> note : ถึงจะเขียน self.some_method แบบนี้ก็ไม่ได้ เพราะนี่ก็คือ explicit receiver อยู่ดี

 โดยเรากลับไปดูที่เมธอดที่เราเขียน 

- other_region.population_density เป็น explicit receiver บวกกับเมธอดเป็น private ดังนั้นจะเกิด NoMethodError 

- other_region.continent เป็น explicit receiver และ attribute เป็น protected ดังนั้นสามารถใช้ได้ 

- self.consider_as_densely_populated? เป็น explicit receiver บวกกับเมธอดเป็น private ดังนั้นจะเกิด NoMethodError

แล้ว Implicit Reciever หน้าตาเป็นอย่างไร ?
เราเรียกเมธอดแบบสั้นๆได้เลย อย่างเราดูในเมธอด greeting เราจะเห็นการใช้ name_info และ population.info

โดยทำเป็น explicit reciever ได้อย่างการเรียก object.name_info

และสิ่งนี้ทำให้ private และ protected แตกต่างกัน
โดย private ไม่สามารถเรียกผ่าน explicit reciever ได้ แต่ไม่ใช่กับ protected

## Conclusion

โดยสรุปแล้วจะมี Modifier 3 รูปแบบ เช่น public, protected และ private โดยการเข้าถึงของแต่ละ Modifier จะแตกต่างกันโดย public สามารถเข้าถึงนอกคลาสได้ protected ไม่สามารถเข้าถึงได้จากนอกคลาส แต่สามารถเข้าถึงได้ด้วยคลาสลูก และ private สามารถเข้าถึงได้ในคลาสตัวมันเองเท่านั้น โดยการณีที่เป็น subclass เมธอดไหนใช้ได้ต้องไปดูในโค้ดว่า Reciever ว่าเป็น explicit หรือ implicit

โดยสามารถใช้ลิงค์นี้เพื่อให้ความเข้าใจคร่าวๆได้
[Public Protected Private](https://www.linkedin.com/pulse/access-modifiers-public-protected-private-oop-manoj-shrestha-tyxtc)
## Video Clip

## Presentation

## แหล่งอ้างอิง

Geeksforgeeks (2025, July 25). Object Oriented Programming in Ruby | Set-2. [https://www.geeksforgeeks.org/ruby/object-oriented-programming-in-ruby-set-2/](https://www.geeksforgeeks.org/ruby/object-oriented-programming-in-ruby-set-2/)
เนื้อหาที่นำมาใช้ : ใช้อธิบายตัวอย่างที่1 ถึงตัวอย่างที่4 เพื่ออธิบายพื้นฐานของ public private โดยเน้นไปดูวิธีการใช้งาน

Naturaily (2019, March 18). Do You Really Know Public Private And Protected In Ruby
[https://naturaily.com/blog/private-protected-public-ruby](https://naturaily.com/blog/private-protected-public-ruby)
เนื้อหาที่นำมาใช้งาน : ใช้อธิบายในตัวอย่างที่9 โดยอธิบายเพื่อให้เข้าใจได้ง่ายมากขึ้น รวมถึงว่า modifier ตัวไหนสามารถใช้งานได้

LanunchSchool (n.d).
[https://launchschool.com/books/oo_ruby/read/inheritance#privateprotectedandpublic](https://launchschool.com/books/oo_ruby/read/inheritance#privateprotectedandpublic)
เนื้อหาที่นำมาใช้ : ใช้อธิบายตัวอย่าง5 ถึงตัวอย่างที่8 โดยที่จะใช้โค้ดเดิมแล้วเพิ่มอธิบายพร้อมกฏต่างๆของ Access Control

stackoverflow (2016, May 25). What are the differences between "private", "public", and "protected methods"?
[https://stackoverflow.com/questions/9882754/what-are-the-differences-between-private-public-and-protected-methods/9882795#9882795](https://stackoverflow.com/questions/9882754/what-are-the-differences-between-private-public-and-protected-methods/9882795#9882795)
เนื้อหาที่นำมาใช้ : ใช้บอกความต่างของ public protected private

Geeksforgeeks (2018, Sep 4). Ruby | Access Control [https://www.geeksforgeeks.org/ruby/ruby-access-control/](https://www.geeksforgeeks.org/ruby/ruby-access-control/)
เนื้อหาที่นำมาใช้ : นำมาอธิบายความหมายของ Access Control

CloudBees (n.d) What's the Difference Between Implicit vs. Explicit Programming? (https://www.cloudbees.com/blog/what-is-the-difference-between-implicit-vs-explicit-programming)[https://www.cloudbees.com/blog/what-is-the-difference-between-implicit-vs-explicit-programming]
เนื้อหาที่นำมาใช้ : อธิบายความแตกต่างระหว่าง Explicit และ Implicit
