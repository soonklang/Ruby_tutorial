# Hash method, Delete, Loop

## Hash method, Delete, Loop

Hash ในภาษา Ruby คือโครงสร้างข้อมูลที่เก็บข้อมูลแบบคู่ Key-Value ใช้ Key(กุญแจ) เพื่อเข้าถึง Value(ค่า) คล้ายกับ Array แต่การเข้าถึงต้องใช้จำนวนเต็ม ขณะที่ Key ของ Hash เป็น Object ได้เกือบทุกชนิด

### ลักษณะสำคัญของ Hash

* แต่ละ Key ต้องไม้ซ้ำกัน

* Value สามารถซ้ำกันได้

* Hash จะเก็บลำดับตามที่ใส่เข้าไป

## Hash Method

Method ที่เป็นคลาสของ Hash โดยเฉพาะ ซึ่ง Ruby มี Method เยอะมากที่ไว้ใช้สำหรับการสร้าง/เข้าถึง/แก้ไข/ลบ/แปลงข้อมูลใน Hash

### แหล่งอ้างอิงอื่นๆกล่าวถึง Hash

Hash คือ key-value pairs, ใช้เก็บข้อมูลแบบ associative array, เป็น data structure พิเศษของ Ruby, และเป็น collection แบบ key-value

### Hash Method ใน Ruby เทียบกับ

#### ภาษา C

ภาษา C ไม่มี Hash โดยตรง ต้องใช้ struct + array + hash function หรือใช้ Hash Table library\
แต่ในภาษา C++ มี

```c++
unordered_map<Key,Value> "name";
```

และภาษา C# มี

```c#
Dictionary<TKey,TValue> "name" = new Dictionary<TKey, TValue>();
```

เป็น Hash Table ของทั้งสองภาษา

#### ภาษา Java

ภาษา Java มี HashMap และ Hashtable ใน Java Collections เป็น generic type ปลอดภัยและยืดหยุ่นต่อการใช้งานแต่ method จะตรงไปตรงมา จะไม่มี method invert ที่ทำหน้าที่ถ้า value ซ้ำ key เดิมจะถูกแทนที่ เหลือแค่คู่สุดท้าย

```java
HashMap<Key, Value> "name" = new HashMap<>();
```

#### ภาษา Python

ภาษา Python มี dict เป็น built-in type ใช้ key-value คล้ายกับ Ruby ที่สุดและใช้ syntax กระชับ แต่ method ไม่เยอะเท่า Ruby

```python
"name" = {Key : Value}
```

## Hash#Delete

Method delete ใช้สำหรับลบคู่ค่า key-value pair ออกจาก Hash โดยระบุ key ที่ต้องการจะลบ

```ruby
hash.delete(key)
hash.delete(key) { |missing_key| ... }
```

#### ตัวอย่าง การลบ Key

```ruby
person = {"name" => "Nice", "age" => 20 }
p person.delete("name")
```

> "name" ถูกลบออกแล้วคืนค่า "Nice"

#### Print Output

```ruby
{"age"=>20}
```

#### ตัวอย่าง การลบ Key ที่ไม่มีอยู่

```ruby
person = {"name" => "Nice", "age" => 20 }
p person.delete("gender")
```

> ไม่มี key "gender" คืนค่า nil และ Hash ไม่มีการเปลี่ยนแปลง

#### Output

```ruby
nil
```

#### ตัวอย่าง การลบ Key ที่ไม่มีอยู่ (มี block)

```ruby
person = {"name" => "Nice", "age" => 20 }
p person.delete("gender") { |x| "#{x} not found" }
```

> Block จะทำงานเมื่อไม่เจอ key

#### Output

```ruby
"gender not found"
```

### การลบค่าในภาษาอื่นๆ

#### ภาษา Python

```python
dict.pop(key)
dict.pop(key, default)
```

> คืนค่า value ที่ถูกลบ หากไม่เจอ key จะเกิด KeyError หรือใช้ default เพื่อคืนค่าแทน

#### ภาษา Java

```java
Object "name" = map.remove(key);
```

> สามารถเป็น Object ใดก็ได้ จะคืนค่า value ที่ถูกลบ หากไม่เจอ key จะคืนค่า null

#### ภาษา C#

```c#
bool "name" = dict.Remove(key);
```

> Remove ไม่คืนค่า value ของ key ต่างจาก Ruby delete หรือ Python pop จะคืนค่า true หากลบสำเร็จ และคืนค่า false หากลบไม่สำเร็จหรือไม่เจอ key

## Loop การวนลูปกับ Hash

Hash คือโครงสร้างที่เก็บ คู่ key-value เราสามารถวนลูปเพื่อเข้าถึงหรือแก้ไขค่าได้หลายวิธี ช่วยให้เราทำงานกับข้อมูลใน Hash เช่น


* แสดงผลทุก key-value
* กรอง key หรือ value ตามเงื่อนไข
* แปลงค่าใน Hash

### ทุก Method ที่ใช้ในการวนลูป

#### ตัวอย่าง Hash

```ruby
balances = {Jo: 1000, Gon: 2000, Mark: 3000 }
```

#### ตัวอย่าง each ใช้สำหรับการวนทุกคู่

```ruby
balances.each { |name, amount| puts "#{name} has #{amount}" }
```

#### Output

```ruby
Jo has 1000
Gon has 2000
Mark has 3000
```

#### ตัวอย่าง each_key ใช้สำหรับการวนเฉพาะ key

```ruby
balances.each_key { |name| puts name }
```

#### Output

```ruby
Jo
Gon
Mark
```

ยังมี each_value ใช้สำหรับการวนเฉพาะ value และ each_with_index ใช้วน key-value พร้อม index

#### ตัวอย่าง map / collect ใช้สำหรับการแปลงค่าใน Hash

```ruby
new_balances = balances.map { |name, amount| [name, amount + 1000] }.to_h
puts new_balances
```

#### Output

```ruby
{:Jo=>2000, :Gon=>3000, :Mark=>4000}
```

#### ตัวอย่าง select ใช้เลือก key-value ที่ตรงกับเงื่อนไข

```ruby
rich_customers = balances.select { |name, amount| amount >= 2000 }
puts rich_customers
```

#### Output

```ruby
{:Gon=>2000, :Mark=>3000}
```

และมี reject ใช้ตัด key-value ที่ตรงเงื่อนไข ทั้งสองแบบนี้ใช้สำหรับการกรองข้อมูล

### การวนลูปในภาษาอื่นๆ

#### ภาษา Python

คล้ายกับ Ruby ใช้ method และการเขียนที่สั้นและอ่านง่าย

```python
for k, v in balances.items(): print(k,v)
```

> Loop แบบวนทุก key-value

```python
{k:int(v+1000) for k,v in balances.items()}
```

> ตัวอย่างบวกเพิ่ม 1000 ให้ทุก value

```python
{k:v for k,v in balances.items() if v>2000}
```

> ตัวอย่างเลือก value > 2000

#### ภาษา Java

ต้องเขียนโค้ดเยอะกว่า Ruby/Python เพราะ Java ไม่มี syntax ที่ใช้สะดวกเหมือน Ruby

```java
for (Map.Entry<String,Integer> e : balances.entrySet()) { System.out.println(e.getKey()+":"+e.getValue()); }
```

> Loop แบบวนทุก key-value

```java
balances.replaceAll((k,v) -> (int)(v+1000));
```

> ตัวอย่างบวกเพิ่ม 1000 ให้ทุก value

```java
balances.entrySet().stream().filter(e -> e.getValue()>2000).collect(Collectors.toMap(Map.Entry::getKey, Map.Entry::getValue));
```

> ตัวอย่างเลือก value > 2000

#### ภาษา C#

C# มี syntax คล้าย Java ต้องประกาศชนิดตัวแปร แต่สามารถใช้ LINQ ทำให้แปลง Dictionary ได้ง่ายขึ้นเหมือน Ruby และ Python

```c#
foreach(var kv in balances) { Console.WriteLine($"{kv.Key}:{kv.Value}"); }
```

> Loop แบบวนทุก key-value

```c#
var newBalances = balances.ToDictionary(kv => kv.Key, kv => (int)(kv.Value+1000));
```

> ตัวอย่างบวกเพิ่ม 1000 ให้ทุก value

```c#
balances.Where(kv => kv.Value>2000).ToDictionary(kv => kv.Key, kv => kv.Value)
```

> ตัวอย่างเลือก value > 2000

## Summary

* Hash Method เมธอดที่ Ruby เตรียมไว้ให้ใช้งานกับ Object Hash ใช้เพื่อ เข้าถึง/เพิ่ม/แก้ไข/ลบ/รวม/วนลูป/แปลง ข้อมูลใน Hash

* Delete ลบค่า key และ value ออกจาก Hash คืนค่าเป็น value ที่ถูกลบ หรือ nil, block หากไม่เจอ key

* Loop ใช้วนค่าใน Hash เพื่อ อ่าน/สร้าง/กรอง ข้อมูล

## _Reference_

#### Ruby

* ruby-lang.org
  https://docs.ruby-lang.org/en/master/Hash.html
* ruby-doc.org
  https://ruby-doc.org/3.4.1/Hash.html
* rubyapi.org
  https://rubyapi.org/3.4/o/hash
* rubyonrails.org
  https://api.rubyonrails.org/classes/Hash.html
* LaunchSchool
  https://launchschool.com/books/ruby/read/hashes
* The Odin Project
  https://www.theodinproject.com/lessons/javascript-hashmap

#### Python

* Python Official Documentation
  https://docs.python.org/3/library/stdtypes.html#dict
* Python Tutorial – Dictionaries
  https://realpython.com/python-dicts/

#### Java

* Java Official Documentation
  https://docs.oracle.com/en/java/javase/20/docs/api/java.base/java/util/HashMap.html
* Java Tutorials – HashMap
  https://docs.oracle.com/javase/tutorial/collections/interfaces/map.html

#### C\#

* Microsoft Docs – Dictionary\<TKey,TValue>
  https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2

#### C++

* C++ Reference – unordered\_map
  https://en.cppreference.com/w/cpp/container/unordered\_map
* C++ STL Documentation
  https://www.cplusplus.com/reference/unordered\_map/unordered\_map/

## _Presentation_

## _Video_
