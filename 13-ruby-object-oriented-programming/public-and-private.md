# Public and Private

ในส่วนนี้เราจะมาศึกษาเรื่่องของ Access Control ในภาษา Ruby อย่างเช่น public, private และรวมไปถึง protected ด้วย ว่าตัวกำหนดการเข้าถึงเป็นอย่างไรผ่านตัวอย่างที่จะทำให้เข้าใจได้ง่ายขึ้น ก่อนที่เราจะลงรายละเอียดของตัวเหล่านี้ เราขอให้คุณมีพื้นฐานที่เกี่ยวข้องกับ Access Control ใน Ruby จะเป็นประโยชน์หากคุณเข้าใจพื้นฐานเกี่ยวกลับคลาสและเมธอดในภาษาโปรแกรมต่างๆ ถ้าคุณยังไม่มีความรู้ด้านนี้ คุณสามารถศึกษาในแหล่งข้อมูลเพิ่มเติมก่อนที่จะดำเนินการเรียนรู้ได้

## Public and Private ในภาษา Ruby 
ก่อนอื่นเรามาทำความรู้จักกับ Access Control กันก่อน
Method Access Control **เป็นคำสั่งควบคุมที่กำหนดการเข้าถึงของโปรแกรมในระดับของเมธอดที่อยู่ในคลาส** โดยทั่วไปจะเรียกว่า Access Modifiers 

Access Control เป็นส่วนที่สำคัญมากๆสำหรับการเขียนโปรแกรมแบบ OOP
หลักสำคัญจะประกอบด้วย
- class variable	และ instance variable ใน Ruby visibility เป็น private เสมอ
- การควบคุมการเข้าถึงใช้ได้กับเมธอดเท่านั้น
- ไม่สามารถกำหนด access control ให้กับ instance variable และ  class variable
- เมธอดแบบ private สามารถูกสูทอดได้เหมือนเมธอดอื่นๆ

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
