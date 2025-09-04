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
<summary><strong>ตัวอย่างที่ 1 ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
class Vehicle {
    private String vehicle_name;
    private String vehicle_color;

    Vehicle(String vehicle_name, String vehicle_color) {
        this.vehicle_name = vehicle_name;
        this.vehicle_color = vehicle_color;
    }

    public void display(){
        greeting();
        System.out.println("Your car details are:");
        System.out.println(vehicle_name);
        System.out.println(vehicle_color);
    }

    private void greeting(){
        System.out.println("Hello, user");
    }
}

public class Ruby1 {
    public static void main(String[] args) {
        Vehicle object = new Vehicle("Nissan","white");
        object.display();
    }
}
```
> คำอธิบายโค้ด : java มี public private เช่นเดียวกับ Ruby
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 1 ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
class Vehicle :
    def __init__(self, vehicle_name, vehicle_color):
        self.vehicle_name = vehicle_name
        self.vehicle_color = vehicle_color

    def display(self) :
        self.__greeting()
        print('Your car details are: ')
        print(self.vehicle_name)
        print(self.vehicle_color)

    def __greeting(self):
        print('Hello, user')

object = Vehicle('Nissan', 'white')

object.display()
```
> คำอธิบายโค้ด : python ก็มีเช่นกันแต่ เราจะเห็นว่ารูปแบบจะต่างกันชัดเจน
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 1 ในรูปแบบภาษา C</strong></summary>
<pre>

```c
#include <stdio.h>
#include <string.h>

// no class in c use struct
typedef struct {
    char vehicle_name[50];
    char vehicle_color[50];
} Vehicle; // define class Vehicle

Vehicle create_vehicle(const char* name, const char* color) {
    Vehicle v;
    strcpy(v.vehicle_name, name);
    strcpy(v.vehicle_color, color);
    return v;
}

void greeting() {
    printf("Hello, user\n");
}

void display(Vehicle* v) {
    greeting();  // Call private method
    printf("Your car details are: \n");
    printf("%s\n", v->vehicle_name);
    printf("%s\n", v->vehicle_color);
}

int main() {
    Vehicle object = create_vehicle("Nissan", "white");
    display(&object);
    
    return 0;
}
```
> คำอธิบายโค้ด : c ไม่มี public private ให้ใช้รวมถึง class จึงจำเป็นต้องใช้ struct เนื่องจาก c เป็นภาษาเชิงกระบวนการ (Procedural Language)
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

<details>
<summary><strong>ตัวอย่างที่ 2 ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
public void display(){
        greeting();
        System.out.println("Your car details are:");
        System.out.println(vehicle_name);
        System.out.println(vehicle_color);
    }
```
> คำอธิบายโค้ด : java จะประกาศไว้หน้าเมธอด
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 2 ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
def display(self) :
    self.__greeting()
    print('Your car details are: ')
    print(self.vehicle_name)
     print(self.vehicle_color)
```
> คำอธิบายโค้ด : python จะไม่มีการประกาศถ้าต้องการให้เป็น public
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 2 ในรูปแบบภาษา C</strong></summary>
<pre>\
    
```c
void display(Vehicle* v) {
    greeting();  // Call private method
    printf("Your car details are: \n");
    printf("%s\n", v->vehicle_name);
    printf("%s\n", v->vehicle_color);
}
```
> คำอธิบายโค้ด : c ไม่มีการประกาศเพราะไม่มีให้ใช้
</pre>
</details>

#### `ตัวอย่างที่ 3` เขียน private ไว้บนสุดของเมธอด
```ruby
private
def greeting
  puts 'Hello, user'
end
```

<details>
<summary><strong>ตัวอย่างที่ 3 ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
private void greeting(){
        System.out.println("Hello, user");
    }
```
> คำอธิบายโค้ด : java จะประกาศไว้หน้าเมธอด
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 3 ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
def __greeting(self):
        print('Hello, user')
```
> คำอธิบายโค้ด : python จะใช้ __ วางไว้หน้าเมธอด
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 3 ในรูปแบบภาษา C</strong></summary>
<pre>

```c
void greeting() {
    printf("Hello, user\n");
}
```
> คำอธิบายโค้ด : c ไม่มี private ทำให้ทุกเมธอดสามารถเข้าถึงได้
</pre>
</details>

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
<details>
<summary><strong>ตัวอย่างที่ 4 ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
private void greeting1(){
System.out.println("Hi user");
}

private void greeting2(){
    System.out.println("Hello, user");
}

private void greeting3(){
    System.out.println("Hello, user");
}
```
> คำอธิบายโค้ด : java จะประกาศไว้หน้าเมธอดทุกตัวเพื่อที่จะเป็นแบบ private ทำให้ต่างจาก ruby
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 4 ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
    def __greeting1(self):
        print('Hello, user1')

    def __greeting2(self):
        print('Hello, user2')

    def __greeting3(self):
        print('Hello, user3')    
```
> คำอธิบายโค้ด : python จะใช้ __ วางไว้หน้าเมธอดทุกตัว concept จะคล้ายๆกับ java
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 4 ในรูปแบบภาษา C</strong></summary>
<pre>

```c
void greeting1() {
    printf("Hello, user1\n");
}

void greeting1() {
    printf("Hello, user1\n");
}

void greeting1() {
    printf("Hello, user1\n");
}
```
> คำอธิบายโค้ด : c ไม่มี private ทำให้ทุกเมธอดสามารถเข้าถึงได้
</pre>
</details>

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

<details>
<summary><strong>ตัวอย่างที่ 5 ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
class GoodDog{
    private String name;
    private int age;
    private final int DOG_YEARS = 7;
    GoodDog(String name, int age){
        this.name = name;
        this.age = age;
    }

    public void dog_name(){
        System.out.println(name);
    }
}

class Ruby3 {
    public static void main(String[] args) {
        GoodDog sparky = new GoodDog("Sparky", 4);
        sparky.dog_name();
    }
}
```
> คำอธิบายโค้ด : โค้ดนี้จะได้ผลลัพท์เดียวกัน โดยรายละเอียดจะเหมือนกันกับ ruby
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 5 ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def dog_name(self):
        print(self.name)

sparky = GoodDog('Sparky', 4)
sparky.dog_name()  
```
> คำอธิบายโค้ด : python จะใช้ public คล้ายกันกับ ruby โดยรวมจะเหมือนกันแต่จะไม่มีการประกาศ public
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 5 ในรูปแบบภาษา C</strong></summary>
<pre>

```c
#include <stdio.h>
#include <string.h>

typedef struct {
    char name[50];
    int age;
} GoodDog;

#define DOG_YEARS 7

GoodDog create_good_dog(const char* name, int age) {
    GoodDog dog;
    strcpy(dog.name, name);
    dog.age = age;
    return dog;
}

void dog_name(GoodDog* dog) {
    printf("%s\n", dog->name);
}

int main() {
    GoodDog sparky = create_good_dog("Sparky", 4);
    dog_name(&sparky);
    return 0;
}
```
> คำอธิบายโค้ด : c สามารถทำให้ผลลัพท์เป็นแบบ ruby ได้ แต่จะไม่มีการใช้ public เพราะไม่มี
</pre>
</details>

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

<details>
<summary><strong>ตัวอย่างที่ 6 ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
class GoodDog{
    private String name;
    private int age;
    private final int DOG_YEARS = 7;
    GoodDog(String name, int age){
        this.name = name;
        this.age = age;
    }

    public void dog_name(){
        System.out.println(name);
    }

    private int human_years(){
        return age * DOG_YEARS;
    }
}

class Ruby4 {
    public static void main(String[] args) {
        GoodDog sparky = new GoodDog("Sparky", 4);
        sparky.human_years();
    }
}
```
> คำอธิบายโค้ด : java จะไม่สามารถรันได้เลยเพราะมี error และ compiler จะมีการประมวลผลก่อนแสดงผลลัพท์
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 6 ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
    class GoodDog:
    DOG_YEARS = 7
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def dog_name(self):
        print(self.name)

    def __human_years(self):
        return self.age * self.DOG_YEARS

sparky = GoodDog('Sparky', 4)
sparky.__human_years() # This will raise an AttributeError 
```
> คำอธิบายโค้ด : python รันแล้วจะเกิด error เช่นเดียวกันกับ ruby
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 6 ในรูปแบบภาษา C</strong></summary>
<pre>

```c
#include <stdio.h>
#include <string.h>

#define DOG_YEARS 7

typedef struct {
    char name[50];      
    int age;            
} GoodDog;

GoodDog create_good_dog(const char* name, int age) {
    GoodDog dog;
    strcpy(dog.name, name);
    dog.age = age;
    return dog;
}

void dog_name(GoodDog* dog) {
    printf("%s\n", dog->name);
}

int human_years(GoodDog* dog) {
    return dog->age * DOG_YEARS;
}


int main() {
    GoodDog sparky = create_good_dog("Sparky", 4);
    int years = human_years(&sparky);
    printf("%d\n", years);
    
    return 0;
}
```
> คำอธิบายโค้ด : c สามารถทำให้ผลลัพท์เป็น 24 เพราะไม่มีการกำหนดการเข้าถึง ทำให้สามารถเข้าถึงได้
</pre>
</details>

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

<details>
<summary><strong>ตัวอย่างที่ 7 ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
class GoodDog{
    private String name;
    private int age;
    private final int DOG_YEARS = 7;
    GoodDog(String name, int age){
        this.name = name;
        this.age = age;
    }

    public void dog_name(){
        System.out.println(name);
    }

    private int human_years(){
        return age * DOG_YEARS;
    }

    public void get_human_years(){
        System.out.println(human_years());
    }
}

class Ruby5 {
    public static void main(String[] args) {
        GoodDog sparky = new GoodDog("Sparky", 4);
        sparky.get_human_years();
    }
}

```
> คำอธิบายโค้ด : ผลลัพท์จะออกมาเช่นเดียวกันกับ ruby
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 7 ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
    class GoodDog:
    DOG_YEARS = 7
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def dog_name(self):
        print(self.name)

    def __human_years(self):
        return self.age * self.DOG_YEARS
    
    def get_human_years(self):
        print(self.__human_years())

sparky = GoodDog('Sparky', 4)
sparky.get_human_years() # This will raise an AttributeError
```
> คำอธิบายโค้ด : python ก็สามารถรันได้ผลลัพท์เช่นเดียวกันกับ java และ ruby
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 7 ในรูปแบบภาษา C</strong></summary>
<pre>

```c
#include <stdio.h>
#include <string.h>

#define DOG_YEARS 7

typedef struct {
    char name[50];      
    int age;            
} GoodDog;

GoodDog create_good_dog(const char* name, int age) {
    GoodDog dog;
    strcpy(dog.name, name);
    dog.age = age;
    return dog;
}

void dog_name(GoodDog* dog) {
    printf("%s\n", dog->name);
}

int human_years(GoodDog* dog) {
    return dog->age * DOG_YEARS;
}


int main() {
    GoodDog sparky = create_good_dog("Sparky", 4);
    int years = human_years(&sparky);
    printf("%d\n", years);
    
    return 0;
}
```
> คำอธิบายโค้ด : c สามารถทำให้ผลลัพท์เป็น 24 ได้เช่นกัน แต่เราใช้โค้ดเดิมกับตัวอย่างที่แล้ว เพราะไม่มี public private ทำให้สามารถใช้ได้เลย
</pre>
</details>

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

<details>
<summary><strong>ตัวอย่างที่ 8 ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
class GoodDog{
    private String name;
    private int age;
    private final int DOG_YEARS = 7;
    GoodDog(String name, int age){
        this.name = name;
        this.age = age;
    }

    public void dog_name(){
        System.out.println(name);
    }
}

class Ruby3 {
    public static void main(String[] args) {
        GoodDog sparky = new GoodDog("Sparky", 4);
        sparky.dog_name();
    }
}
```
> คำอธิบายโค้ด : java จำเป็นต้องระบุเพราะถ้าไม่ระบุจะทำให้เมธอดเป็น default โดยที่การเข้าถึงไม่เท่ากับ public
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 8 ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def dog_name(self):
        print(self.name)

sparky = GoodDog('Sparky', 4)
sparky.dog_name()  
```
> คำอธิบายโค้ด : python จะไม่มีการประกาศ public ทำให้เป็น public โดยอัตโนมัติ
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 8 ในรูปแบบภาษา C</strong></summary>
<pre>

```c
#include <stdio.h>
#include <string.h>

typedef struct {
    char name[50];
    int age;
} GoodDog;

#define DOG_YEARS 7

GoodDog create_good_dog(const char* name, int age) {
    GoodDog dog;
    strcpy(dog.name, name);
    dog.age = age;
    return dog;
}

void dog_name(GoodDog* dog) {
    printf("%s\n", dog->name);
}

int main() {
    GoodDog sparky = create_good_dog("Sparky", 4);
    dog_name(&sparky);
    return 0;
}
```
> คำอธิบายโค้ด : c ไม่มี public private ทำให้ทุกเมธอดเป็น public
</pre>
</details>

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

<details>
<summary><strong>ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
class Vehicle {
    private String vehicle_name;
    private String vehicle_color;

    Vehicle(String vehicle_name, String vehicle_color) {
        this.vehicle_name = vehicle_name;
        this.vehicle_color = vehicle_color;
    }

    public void display(){
        greeting();
        System.out.println("Your car details are:");
        System.out.println(vehicle_name);
        System.out.println(vehicle_color);
    }

    private void greeting(){
        System.out.println("Hello, user");
    }
}

public class Ruby1 {
    public static void main(String[] args) {
        Vehicle object = new Vehicle("Nissan","white");
        object.display();
    }
}
```
> คำอธิบายโค้ด : java ใช้คลาส private โดยผ่านคลาส public
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
class Vehicle :
    def __init__(self, vehicle_name, vehicle_color):
        self.vehicle_name = vehicle_name
        self.vehicle_color = vehicle_color

    def display(self) :
        self.__greeting()
        print('Your car details are: ')
        print(self.vehicle_name)
        print(self.vehicle_color)

    def __greeting(self):
        print('Hello, user')

object = Vehicle('Nissan', 'white')

object.display()
```
> คำอธิบายโค้ด : python ใช้คลาส private โดยผ่านคลาส public
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา C</strong></summary>
<pre>

```c
#include <stdio.h>
#include <string.h>

// no class in c use struct
typedef struct {
    char vehicle_name[50];
    char vehicle_color[50];
} Vehicle; // define class Vehicle

Vehicle create_vehicle(const char* name, const char* color) {
    Vehicle v;
    strcpy(v.vehicle_name, name);
    strcpy(v.vehicle_color, color);
    return v;
}

void greeting() {
    printf("Hello, user\n");
}

void display(Vehicle* v) {
    greeting();  // Call private method
    printf("Your car details are: \n");
    printf("%s\n", v->vehicle_name);
    printf("%s\n", v->vehicle_color);
}

int main() {
    Vehicle object = create_vehicle("Nissan", "white");
    display(&object);
    
    return 0;
}
```
> คำอธิบายโค้ด : c ไม่มีคลาส private ทำให้สามารถเข้าถึงได้ทุกกเมธอด
</pre>
</details>

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

<details>
<summary><strong>ตัวอย่างที่ 9 ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
class Region{
    public String name;
    private int population; // cant call in subclass directly i will change to protected
    private int area_size;
    protected String continent;
    private int HIGH_POPULATION_DENSITY = 0;
    Region(String name, int population, int area_size, String continent){
        this.name = name;
        this.population = population;
        this.area_size = area_size;
        this.continent = continent;
    }

    public void greeting(){
        System.out.println(name_info() + population_info());
    }

    public void more_densely_populated(Region other_region){
        String result;
        if(population_density() > other_region.population_density()){
            result = "more";
        } else {
            result = "less";
        } 
        System.out.println(name + " is " + result + " densely populated than " + other_region.name + ".");
    }

    public void the_same_continent(Region other_region){
        if (continent.equals(other_region.continent)){
            System.out.println(name + " and " + other_region.name + " are in the same continent.");
        } else {
            System.out.println(name + " and " + other_region.name + " are not in the same continent.");
        }
    }

    public void can_be_crowdy(){
        if(consider_as_densily_populated()){
            System.out.println(name + "can be crowdy.");
        }else{
            System.out.println(name + "can not be crowdy.");
        }
    }

    protected String name_info(){
        return "Hello, I'm " + name;
    }

    private String population_info(){ // cant call in subclass directly i will change to protected
        return " "+ population + " people live here.";
    }

    private int population_density(){
        return population / area_size;
    }

    private boolean consider_as_densily_populated(){
        return population_density() > HIGH_POPULATION_DENSITY;
    }
}

class Country extends Region{
    // Override
    public final int HIGH_POPULATION_DENSITY = 300;
    Country (String name, int population, int area_size, String continent){
        super(name, population, area_size, continent);
    }

    public void own_greeting(){
        System.out.println("The country name: " + this.name + ". " + population_info());
    }
}

class City extends Region{
    public final int HIGH_POPULATION_DENSITY = 1000;
    City (String name, int population, int area_size, String continent){
        super(name, population, area_size, continent);
    }

    public void own_greeting(){
        System.out.println(name_info() + " The population: " + this.population + " people.");
    }
}


public class Ruby6 {
    public static void main(String[] args) {
        City wroclaw = new City("Wroclaw", 638000, 293, "Europe");
        City san_francisco = new City("San Francisco", 884000, 121, "Northern America");
        Country poland = new Country("Poland", 38000000, 312000, "Europe");

        // I section
        wroclaw.greeting();
        poland.greeting();

        // II section Always error because name_info() and population_info() are protected 
        //note: population_info if protected it error too
        wroclaw.name_info();
        wroclaw.population_info();

        // III section if you want to call own_greeting population and population_info() should be protected
        wroclaw.own_greeting();
        poland.own_greeting();

        // IV section above 3 methods can running if population is protected or private
        wroclaw.more_densely_populated(san_francisco);
        wroclaw.the_same_continent(san_francisco);
        san_francisco.can_be_crowdy();
    }
}

```
> คำอธิบายโค้ด : java ถ้าเราเขียนตาม ruby จะเกิด error ขึ้นมา ถ้าไม่อยากกให้เกกิด error ต้องเปลี่ยน modifer ของ population และ population_info() ให้เป็น protected
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 9 ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
class Region:
    HIGH_POPULATION_DENSITY = 0 #set in subclass
    def __init__(self, name, population, area_size, continent):
        self.name = name
        self.__population = population
        self.__area_size = area_size
        self._continent = continent
    
    def greeting(self):
        print(self._name_info() + self.___population_info())

    def more_densely_populated(self, other_region):
        result = "more" if self.__population_density() > other_region.__population_density() else "less"
        print(self.name + " is " + result + " densely populated than " + other_region.name)
    
    def the_same_continent(self, other_region):
        if self._continent == other_region._continent:
            print(self.name + " and " + other_region.name + " lie in the same continent.")
        else:
            print(self.name + " and " + other_region.name + " lie in different continents.")

    def can_be_crowdy(self):
        if self.consider_as_densely_populated():
            print(self.name + " can be crowdy.")
        else:
            print(self.name + " can't be crowdy.")

    def _name_info(self):
        return "Hello, I'm " + self.name
    
    def ___population_info(self):
        return " " + str(self.__population) + " people live here."
    
    def __population_density(self):
        return self.__population / self.__area_size
    
    def consider_as_densely_populated(self):
        return self.__population > self.HIGH_POPULATION_DENSITY
    
class Country(Region):
    HIGH_POPULATION_DENSITY = 300
    def __init__(self, name, population, area_size, continent):
        super().__init__(name, population, area_size, continent)

    def own_greeting(self):
        print("the country name: " + self.name + " " + self._Region___population_info())

class City(Region):
    HIGH_POPULATION_DENSITY = 3000
    def __init__(self, name, population, area_size, continent):
        super().__init__(name, population, area_size, continent)

    def own_greeting(self):
        print(self._name_info() + " the population: " + str(self._Region__population) + " people.") # self._Region__population call private variable from parent class

# Innitializations for testing
wroclaw = City('Wroclaw', 638000, 293, 'Europe')
san_francisco = City('San Francisco', 884000, 121, 'Northern America')
poland = Country('Poland', 38000000, 312000, 'Europe')

# section 1
wroclaw.greeting()
poland.greeting()

# section 2 Errors
# wroclaw._name_info()
# wroclaw.___population_info()

# section 3
wroclaw.own_greeting()
poland.own_greeting()

# section 4
wroclaw.more_densely_populated(san_francisco)
wroclaw.the_same_continent(san_francisco)
san_francisco.can_be_crowdy()
```
> คำอธิบายโค้ด : python สามารถรันได้ปกติ
</pre>
</details>

<details>
<summary><strong>ตัวอย่างที่ 9 ในรูปแบบภาษา C</strong></summary>
<pre>

```c
#include <stdio.h>
#include <string.h>


typedef struct {
    char name[50];
    int population;
    double area;
    char continent[50];
} Region;

typedef struct {
    Region base; 
} Country;

typedef struct {
    Region base;
} City;

// Constants
#define COUNTRY_HIGH_DENSITY 300
#define CITY_HIGH_DENSITY 3000

double density(Region* r) {
    return r->population / r->area;
}

// Region methods
void greeting(Region* r) {
    printf("Hello, I'm %s! %d people live here.\n", r->name, r->population);
}

void name_info(Region* r) {
    printf("Hello, I'm %s!", r->name);
}

void population_info(Region* r) {
    printf(" %d people live here.", r->population);
}

void more_densely_populated(Region* r1, Region* r2) {
    char* result = (density(r1) > density(r2)) ? "more" : "less";
    printf("%s is %s densely populated than %s.\n", r1->name, result, r2->name);
}

void the_same_continent(Region* r1, Region* r2) {
    if (strcmp(r1->continent, r2->continent) == 0) {
        printf("%s and %s lie in the same continent.\n", r1->name, r2->name);
    } else {
        printf("%s and %s lie in the different continents.\n", r1->name, r2->name);
    }
}

void can_be_crowdy_region(Region* r, int high_density) {
    if (density(r) > high_density) {
        printf("%s can be crowdy.\n", r->name);
    } else {
        printf("There is enough space in the %s.\n", r->name);
    }
}

// Country constructor
Country create_country(char* name, int population, double area, char* continent) {
    Country c;
    strcpy(c.base.name, name);
    c.base.population = population;
    c.base.area = area;
    strcpy(c.base.continent, continent);
    return c;
}

// City constructor
City create_city(char* name, int population, double area, char* continent) {
    City c;
    strcpy(c.base.name, name);
    c.base.population = population;
    c.base.area = area;
    strcpy(c.base.continent, continent);
    return c;
}

// Country methods
void country_own_greeting(Country* c) {
    printf("The country name: %s.", c->base.name);
    population_info(&c->base);
    printf("\n");
}

void country_can_be_crowdy(Country* c) {
    can_be_crowdy_region(&c->base, COUNTRY_HIGH_DENSITY);
}

// City methods
void city_own_greeting(City* c) {
    name_info(&c->base);
    printf(" The population: %d people.\n", c->base.population);
}

void city_can_be_crowdy(City* c) {
    can_be_crowdy_region(&c->base, CITY_HIGH_DENSITY);
}

int main() {
    // Initialization
    City wroclaw = create_city("Wroclaw", 638000, 293, "Europe");
    City san_francisco = create_city("San Francisco", 884000, 121, "Northern America");
    Country poland = create_country("Poland", 38000000, 312000, "Europe");

    // section I
    greeting(&wroclaw.base);
    greeting(&poland.base);

    // section II
    name_info(&wroclaw.base);
    printf("\n");
    population_info(&wroclaw.base);
    printf("\n");

    // section III
    city_own_greeting(&wroclaw);
    country_own_greeting(&poland);

    // section IV
    more_densely_populated(&wroclaw.base, &san_francisco.base);
    the_same_continent(&wroclaw.base, &san_francisco.base);
    city_can_be_crowdy(&san_francisco);

    return 0;
}
```
> คำอธิบายโค้ด : c ไม่มี public private ทำให้สามารถใช้ได้ทุกเมธอด
</pre>
</details>

Region เป็นคลาสแม่ที่มีเมธอดแบบ public, protected และ private ทั้ง 3 แบบ โดยที่จะมีคลาสลูกอยู่ทั้งหมด 2 ตัว คือ Country และ City โดยสืบทอดมาจาก Region 

จากตัวอย่าง ในคลาสของ Region มีเมธอดที่เป็น public อยู่คือ greeting, more_populated?, the_same_continent? และ can_be_crowdy? มีเมธอด protected คือ name_info และ เมธอด private คือ population_info, population_density และ consider_as_densely_populated? 

ในคลาสของ Country และ City จะมีเมธอด own_greeting เพิ่มขึ้นมา 

หลังจากนั้นเราจะสร้าง Object มา 3 อัน 

```ruby
# initialization
wroclaw = City.new('Wroclaw', 638_000, 293, 'Europe')
san_francisco = City.new('San Francisco', 884_000, 121, 'Northern America')
poland = Country.new('Poland', 38_000_000, 312_000, 'Europe')
```

<details>
<summary><strong>ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
public class Ruby6 {
    public static void main(String[] args) {
        City wroclaw = new City("Wroclaw", 638000, 293, "Europe");
        City san_francisco = new City("San Francisco", 884000, 121, "Northern America");
        Country poland = new Country("Poland", 38000000, 312000, "Europe");
    }
}

```
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
# Innitializations for testing
wroclaw = City('Wroclaw', 638000, 293, 'Europe')
san_francisco = City('San Francisco', 884000, 121, 'Northern America')
poland = Country('Poland', 38000000, 312000, 'Europe')
```
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา C</strong></summary>
<pre>

```c
int main() {
    // Initialization
    City wroclaw = create_city("Wroclaw", 638000, 293, "Europe");
    City san_francisco = create_city("San Francisco", 884000, 121, "Northern America");
    Country poland = create_country("Poland", 38000000, 312000, "Europe");

    return 0;
}
```
</pre>
</details>

โดยสร้างวัตถุ wroclaw และ san_francisco จาก city และ poland จาก country

#### Section I เข้าถึง public เมธอดของคลาสแม่

```ruby
# I section
wroclaw.greeting
poland.greeting
```

<details>
<summary><strong>ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
// I section
wroclaw.greeting();
poland.greeting();
```
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
# section 1
wroclaw.greeting()
poland.greeting()
```
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา C</strong></summary>
<pre>

```c
// section I
greeting(&wroclaw.base);
greeting(&poland.base);
```
</pre>
</details>

<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>Hello, I'm Wroclaw! 638000 people live here.
Hello, I'm Poland! 38000000 people live here.</code>
</pre>
</details>

> เราจะเห็นว่าเมธอดที่เป็น public จะไม่มีเขียนกำกับไว้ด้านบนสุดของเมธอด เพราะ ถ้าเราไม่กำกับการเข้าถึง ค่า default จะเป็น public เสมอ
> โดยทั้ง 3 ภาษาที่เรานำมาเปรียบเทียบก็ได้ผลลัพท์เช่นนี้

#### Section 2

```ruby
# II section
wroclaw.name_info
wroclaw.population_info
```
<details>
<summary><strong>ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
// II section
wroclaw.name_info();
poland.population_info();
```
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
# section 2
wroclaw.name_info()
poland.population_info()
```
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา C</strong></summary>
<pre>

```c
// section II
name_info(&wroclaw.base);
population_info(&poland.base);
```
</pre>
</details>

<details>
<summary><strong>แสดงผลลัพธ์</strong></summary>
<pre>
<code>NoMethodError
NoMethodError</code>
</pre>
</details>

> จากโค้ดตัวอย่าง เราจะเห็นว่า name_info เป็นเมธอด protected และ population_info เป็นเมธอด private โดยเมื่อเรารันจะทำให้เกิด NoMethodError เพราะเราไม่สามารถเข้าถึงเมธอดที่เป็น protected และ private จากภายนอกคลาสได้
> java และ python จะได้ผลลัพท์เช่นนี้ แต่ c จะได้ผลลัพท์ออกมาโดยที่ไม่ error

#### Section 3 เข้าถึง protected และ private จากภายในคลาส

```ruby
# III section
wroclaw.own_greeting
poland.own_greeting
```

<details>
<summary><strong>ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
// III section
wroclaw.own_greeting();
poland.own_greeting();
```
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
# section 3
wroclaw.own_greeting()
poland.own_greeting()
```
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา C</strong></summary>
<pre>

```c
// section III
own_greeting(&wroclaw.base);
own_greeting(&poland.base);
```
</pre>
</details>

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
> python และ c จะได้ผลลัพท์ออกมาโดย python จะทำงานเหมือนกันกับ ruby และ c จะสามารถรันได้อยู่แล้วเพราะเป็น public อยู่แล้ว ส่วน java ไม่สามารถรันได้ หากไม่เปลี่ยน population และ population_info() เป็น protected 

#### Secition 4 ความแตกต่างระหว่าง protected และ private

```ruby
# IV section
wroclaw.more_densely_populated?(san_francisco)
wroclaw.the_same_continent?(san_francisco)
san_francisco.can_be_crowdy?
```
<details>
<summary><strong>ในรูปแบบภาษา Java</strong></summary>
<pre>

```java
// IV section above 3 methods can running if population is protected or private
wroclaw.more_densely_populated(san_francisco);
wroclaw.the_same_continent(san_francisco);
san_francisco.can_be_crowdy();
```
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา Python</strong></summary>
<pre>

```python
# section 4
wroclaw.more_densely_populated(san_francisco)
wroclaw.the_same_continent(san_francisco)
san_francisco.can_be_crowdy()
```
</pre>
</details>

<details>
<summary><strong>ในรูปแบบภาษา C</strong></summary>
<pre>

```c
// section IV
more_densely_populated(&wroclaw.base, &san_francisco.base);
the_same_continent(&wroclaw.base, &san_francisco.base);
city_can_be_crowdy(&san_francisco);
```
</pre>
</details>

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

> โดยเรามาสรุป section IV โดย java จะไม่สามารถรันได้หากไม่เปลี่ยน population และ population_info() เป็น protected แต่ถ้าเปลี่ยนจะมีผลลัพท์ออกมาทุกบรรทัด แล้ว python และ c สามารถรันได้ทุกบรรทัดมีผลลัพท์ออกมาทุกบรรทัด

แต่เราสังเกตเห็นว่า Section3 และ Section4 ของ Ruby ภายในมีการใช้เมธอด private เหมือนกันในเมธอดที่เรียกออกมาใช้งาน 

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
