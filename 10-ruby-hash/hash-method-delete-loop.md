# Hash method, Delete, Loop
Hash ในภาษา Ruby คือโครงสร้างข้อมูลที่เก็บข้อมูลแบบคู่ Key-Value ใช้ Key(กุญแจ) เพื่อเข้าถึง Value(ค่า) คล้ายกับ Array แต่การเข้าถึงต้องใช้จำนวนเต็ม ขณะที่ Key ของ Hash เป็น Object ได้เกือบทุกชนิด

## ลักษณะสำคัญของ Hash 
- แต่ละ Key ต้องไม้ซ้ำกัน <br>
- Value สามารถซ้ำกันได้ <br>
- Hash จะเก็บลำดับตามที่ใส่เข้าไป

# Hash Method 
Method ที่เป็นคลาสของ Hash โดยเฉพาะ ซึ่ง Ruby มี Method เยอะมากที่ไว้ใช้สำหรับการสร้าง/เข้าถึง/แก้ไข/ลบ/แปลงข้อมูลใน Hash

## แหล่งอ้างอิงอื่นๆกล่าวถึง Hash
Hash คือ key-value pairs, ใช้เก็บข้อมูลแบบ associative array, เป็น data structure พิเศษของ Ruby, และเป็น collection แบบ key-value

## Hash Method ใน Ruby เทียบกับ
### ภาษา C 
ภาษา C ไม่มี Hash โดยตรง ต้องใช้ struct + array + hash function หรือใช้ Hash Table library <br>
แต่ในภาษา C++ มี
```c++
unordered_map<Key,Value> "name";
```
และภาษา C# มี 
```c#
Dictionary<TKey,TValue> "name" = new Dictionary<TKey, TValue>();
```
เป็น Hash Table ของทั้งสองภาษา

### ภาษา Java
ภาษา Java มี HashMap และ Hashtable ใน Java Collections เป็น generic type ปลอดภัยและยืดหยุ่นต่อการใช้งานแต่ method จะตรงไปตรงมา จะไม่มี method invert ที่ทำหน้าที่ถ้า value ซ้ำ key เดิมจะถูกแทนที่ เหลือแค่คู่สุดท้าย
```java
HashMap<Key, Value> "name" = new HashMap<>();
```

### ภาษา Python
ภาษา Python มี dict เป็น built-in type ใช้ key-value คล้ายกับ Ruby ที่สุดและใช้ syntax กระชับ แต่ method ไม่เยอะเท่า Ruby
```python
"name" = {Key : Value}
```

# Hash#Delete
Method delete ใช้สำหรับลบคู่ค่า key-value pair ออกจาก Hash โดยระบุ key ที่ต้องการจะลบ
```ruby
hash.delete(key)
hash.delete(key) { |missing_key| ... }
```
### ตัวอย่าง การลบ Key
```ruby
person = {"name" => "Nice", "age" => 20 }
p person.delete("name")
```
>"name" ถูกลบออกแล้วคืนค่า "Nice"

### Print Output
```ruby
{"age"=>20}
```

### ตัวอย่าง การลบ Key ที่ไม่มีอยู่
```ruby
person = {"name" => "Nice", "age" => 20 }
p person.delete("gender")
```
>ไม่มี key "gender" คืนค่า nil และ Hash ไม่มีการเปลี่ยนแปลง
### Output
```ruby
nil
```

### ตัวอย่าง การลบ Key ที่ไม่มีอยู่ (มี block)
```ruby
person = {"name" => "Nice", "age" => 20 }
p person.delete("gender") { |x| "#{x} not found" }
```
>Block จะทำงานเมื่อไม่เจอ key
### Output
```ruby
"gender not found"
```

## การลบค่าในภาษาอื่นๆ
### ภาษา Python
```python
dict.pop(key)
dict.pop(key, default)
```
>คืนค่า value ที่ถูกลบ หากไม่เจอ key จะเกิด KeyError หรือใช้ default เพื่อคืนค่าแทน

### ภาษา Java
```java
Object "name" = map.remove(key);
```
>สามารถเป็น Object ใดก็ได้ จะคืนค่า value ที่ถูกลบ หากไม่เจอ key จะคืนค่า null
### ภาษา C#
```C#
bool "name" = dict.Remove(key);
```
>Remove ไม่คืนค่า value ของ key ต่างจาก Ruby delete หรือ Python pop จะคืนค่า true หากลบสำเร็จ และคืนค่า false หากลบไม่สำเร็จหรือไม่เจอ key


# *Reference*
### Ruby
- ruby-lang.org <br>
  https://docs.ruby-lang.org/en/master/Hash.html
- ruby-doc.org <br>
  https://ruby-doc.org/3.4.1/Hash.html
- rubyapi.org <br>
  https://rubyapi.org/3.4/o/hash
- rubyonrails.org <br>
  https://api.rubyonrails.org/classes/Hash.html
