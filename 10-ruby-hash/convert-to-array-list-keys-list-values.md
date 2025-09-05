# Convert to Array, List Keys, List Values

## Convert to array

Convert to array คือ การแปลงข้อมูลเป็นอาเรย์ ไม่ว่าจะเป็นข้อมูลรูปแบบไหนเช่น String , Range , Hash เป็นต้น
\
เพื่อที่จะจัดการกับข้อมูลได้ง่ายและมีปีะสิทธิภาพมากยิ่งขึ้น มาดูการ Convert to array ของข้อมูลรูปแบบต่างๆกันดีกว่า

## String

String คือ Text หรือ ข้อมความใน " " เช่น " String "
\
การแปลง String สามารถทำได้โดยการใช้เมธอด .spilt(delimiter) ลองดูตัวอย่างด้านล่าง

```ruby
text = "Ruby,Python,JavaScript" # แบ่งตาม , ที่คั่นคำต่างๆ
result = text.split(",")
p result
```

Out put

```ruby
["Ruby", "Python", "JavaScript"]
```

ตัวอย่างเปรียบเทียบการ Convert ของ String ในภาษา C&#x20;

```c
#include <stdio.h>
#include <string.h>

int main() {
    char text[] = "Ruby,Python,JavaScript";
    char *result[10];  // array สำหรับเก็บคำที่แยกได้
    int i = 0;

    // ใช้ strtok เพื่อแยก string ตาม ","
    char *token = strtok(text, ",");
    while (token != NULL) {
        result[i++] = token;
        token = strtok(NULL, ",");
    }

    // แสดงผลลัพธ์
    for (int j = 0; j < i; j++) {
        printf("result[%d] = %s\n", j, result[j]);
    }

    return 0;
}
```

Out put

```c
result[0] = Ruby
result[1] = Python
result[2] = JavaScript
```

<sub>ฟังก์ชัน</sub> <sub></sub><sub>`strtok()`</sub> <sub></sub><sub>ในภาษา C คือเครื่องมือสำหรับ</sub> <sub></sub><sub>**แยก string ออกเป็นส่วน ๆ (tokens)**</sub> <sub></sub><sub>โดยใช้ตัวคั่นที่กำหนด เช่น</sub> <sub></sub><sub>`,`</sub> <sub></sub><sub>หรือช่องว่าง</sub> <sub></sub><sub>`" "`</sub>

## Range & Hash

Range คือ ค่าที่อยู่ในช่วงที่มีจุดเริ่มต้นและจุดจบโดยจะเป็นตัวเลขหรือตัวอักษร เช่น Box = \[ 1 , 2 , 3]
\
Hash คือ โครงสร้างข้อมูลแบบ Key-Values
\
การแปลง Range & Hash สามารถทำได้โดยการใช้เมธอด (Data).to\_a ลองดูตัวอย่างด้านล่าง

```ruby
Range
  range = (10..15).to_a
  p range
```

Out put

```ruby
[10, 11, 12, 13, 14, 15]
```

```ruby
Hash
  data = {a: 1, b: 2}
  result = data.to_a
  p result.inspect
```

Out put

```ruby
"[[:a, 1], [:b, 2]]"
```

ตัวอย่างเปรียบเทียบการ Convert ของ Range & Hash ในภาษา Java

Range

```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<Integer> range = new ArrayList<>();

        for (int i = 10; i <= 15; i++) {
            range.add(i);
        }

        System.out.println(range);
    }
}
```

Out put

```java
[10, 11, 12, 13, 14, 15]
```

`ใช้ ArrayList แทน array แบบ dynamic ใน Java`

`ใช้ for loop เพื่อเพิ่มตัวเลขตั้งแต่ 10 ถึง 15 เข้าไปใน list`

`System.out.println(range) จะพิมพ์ list ออกมาในรูปแบบคล้าย Ruby`

Hash

```java
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Map<String, Integer> data = new HashMap<>();
        data.put("a", 1);
        data.put("b", 2);

        List<Map.Entry<String, Integer>> result = new ArrayList<>(data.entrySet());

        // แสดงผลแบบ inspect
        for (Map.Entry<String, Integer> entry : result) {
            System.out.println("[" + entry.getKey() + ", " + entry.getValue() + "]");
        }
    }
}
```

Out put

```java
[a, 1]  
[b, 2]
```

`HashMap ใช้แทน Hash ใน Ruby`

`entrySet() คืนค่าเป็นชุดของ key-value pairs`

`ArrayList<>(...) ใช้แปลงเป็น list ที่สามารถวนลูปได้`

`การ println แบบ ["key", value] เพื่อ print ค่าออกมาแบบเว้นบรรทัด`

## Nile & Single Object

Nile คือ ค่าที่ไม่ได้แสดงข้อมูลหรือยังไม่ได้กำหนดค่า
\
Single Object คือ ข้อมูลที่ไม่ใช่อาเรย์เช่น ตัวเลข ตัวอักษร nil
\
การแปลง Nile & Single Object สามารถทำได้โดยการใช้เมธอด array(Data) ลองดูตัวอย่างด้านล่าง

```ruby
Nile 
 data = nil
 result = Array(data)
 p result
```

Out put

```ruby
[] #จะถูกแปลงเป็นอาเรย์ว่าง [] เพราะไม่มีข้อมูลให้เก็บ (nil) 
```

```ruby
Single Object
 data = "Ruby"
 result = Array(data)
 p result
```

Out put

```ruby
["Ruby"]
```

ตัวอย่างเปรียบเทียบการ Convert ของ Nil & Single Object ในภาษา Python

Nile

```python
data = None
result = [] if data is None else list(data)
print(result)
```

Out put

```python
[]
```

`None ใน Python คือการไม่มีค่า เหมือน nil ใน Ruby`

`list(data) จะทำงานได้ก็ต่อเมื่อ data เป็น iterable เช่น list, tuple, string`

Single Object

```python
data = "Python"
result = [data]
print(result)
```

Out put

```python
['Python']
```

`ใน Python ถ้าใช้ list("Ruby") จะได้ ['R', 'u', 'b', 'y'] เพราะมันแยกตัวอักษร`

`แต่ถ้าอยากให้ "Ruby" เป็นสมาชิกเดียวใน list ต้องใช้ [data] แบบนี้`

## List Key - Values

List คือ array ที่เก็บค่าข้อมูลที่เรียงลำดับโดยเริ่มนับจาก 0 ไปถึง n โดยสามารถเก็บข้อมูลได้หลายประเภทเช่น  String , ตัวเลข เป็นต้น สามารถสร้างได้โดยใช้ \[ ]
\
และสามารถเข้าถึงข้อมูลโดยใช้ Box\[Number] ลองดูตัวอย่างด้านล่าง

```ruby
Box = [ "apple" , 25 , "mango"]
puts Box[0]
puts Box[1]
puts Box[2]
```

Out put

```ruby
apple
25
mango
```

## List Key

Key คือ ชื่อ หรือ ตัวระบุ ที่ใช้ในการเข้าถึงข้อมูลใน List และสามารถตั้งชื่อ Key ได้หลายรูปแบบ ตัวเลข String โดยมีกฎว่า ห้ามมีชื่อซ้ำกันใน List เดียวกัน
\
และ Key สามารถสร้างได้โดย Box = { Key : } หรือดูตามตัวอย่างด้านล่าง

```ruby
person = {
  name: "Ame",   # ใช้ symbol เป็น key
  age: 120,
  mood: "Cozy"
}

puts person[:name]
puts person[:mood]
```

Out put

```ruby
Ame
Cozy
```

ถ้าเราใช้ symbol ตอนประกาศ key ต้องใช้ symbol ตอนเรียกด้วย
\
หรือใช้ string ตอนประกาศ key ต้องใช้ string ตอนเรียกด้วย สามารถเทียบได้ตามตาราง

| รูปแบบ Key | ตัวอย่าง         | วิธีเรียกใช้    |
| ---------- | ---------------- | --------------- |
| Symbol     | {name: "Ame"}    | person\[:name]  |
| String     | {"name" ⇒ "Ame"} | person\["name"] |

ตัวอย่างเปรียบเทียบการสร้าง List-Key ของภาษา C&#x20;

C

```c
#include <stdio.h>

int main() {
    char name[] = "Ame";
    char mood[] = "Cozy";

    printf("%s\n", name);
    printf("%s\n", mood);

    return 0;
}
```

Out put

```c
Ame
Cozy
```

`ใช้ char[] สำหรับเก็บ string แบบง่าย ๆ`

`ใช้ printf เพื่อแสดงผลเหมือน puts ใน Ruby`

## List Value

Value คือข้อมูลที่ถูกเก็บไว้ภายไต้ Key ที่สร้างขึ้นมา และ Values สามารถสร้างซ้ำกันได้ใน List เดียวกัน โดยสามารถเก็บข้อมูลได้หลายประเภทแบบตัวอื่นๆ
\
และ Value สามารถสร้างได้โดย Box = { Key : Value } หรือดูตามตัวอย่างด้านล่าง

```ruby
person = {
  name : "Ame" , # "Ame" คือ Values สังเกตุได้โดยมันจะอยู่หลัง : 
  age : 75 ,
  city : "Cathedral of the Sacred Blood"
}  

puts "Name: #{person[:name]}"  
puts "Age: #{person[:age]}"     
puts "City: #{person[:city]}"   
```

Out put

```ruby
Name: Ame  # "Ame" คือ Value
Age: 75  # 75 คือ Value
City: Cathedral of the Sacred Blood # "Cathedral of the Sacred Blood" คือ Value
```

ตัวอย่างเปรียบเทียบการสร้าง List-Value ของภาษา C&#x20;

```c
#include <stdio.h>

struct Person {
    char name[50];
    int age;
    char city[100];
};

int main() {
    // ประกาศและกำหนดค่าให้กับตัวแปร person
    struct Person person = {
        "Ame",
        75,
        "Cathedral of the Sacred Blood"
    };

    // แสดงผลข้อมูล
    printf("Name: %s\n", person.name);
    printf("Age: %d\n", person.age);
    printf("City: %s\n", person.city);

    return 0;
}
```

```c
Name: Ame  
Age: 75  
City: Cathedral of the Sacred Blood
```

`ในภาษา C เราใช้ struct เพื่อรวมข้อมูลหลายประเภทไว้ในตัวเดียวกัน`

`char name[50] คือการกำหนดให้ชื่อเป็นข้อความที่มีความยาวไม่เกิน 49 อักษร`

`char city[100] ก็เช่นกันแต่ยาวไม่เกิน 100 อักษร`

`printf ใช้ %s สำหรับ string และ %d สำหรับตัวเลขจำนวนเต็ม`

ตัวอย่างในภาษา Java&#x20;

```java
import java.util.*;

class Player {
    String name;
    int level;
    String location;

    Player(String name, int level, String location) {
        this.name = name;
        this.level = level;
        this.location = location;
    }
}

public class Game {
    public static void main(String[] args) {
        List<Player> players = new ArrayList<>();
        players.add(new Player("Ame", 75, "Cathedral of the Sacred Blood"));
        players.add(new Player("Yuki", 82, "Frozen Abyss"));
        players.add(new Player("Kai", 68, "Ashen Ruins"));

        for (Player p : players) {
            System.out.println(p.name + " is level " + p.level + " and located in " + p.location);
        }
    }
}
```

Out put

```java
Ame is level 75 and located in Cathedral of the Sacred Blood  
Yuki is level 82 and located in Frozen Abyss  
Kai is level 68 and located in Ashen Ruins
```

`ใช้ class เพื่อสร้าง key-value แบบมีโครงสร้าง`

ตัวอย่างในภาษา Python

```python
from dataclasses import dataclass

@dataclass
class Player:
    name: str
    level: int
    location: str

players = [
    Player("Ame", 75, "Cathedral of the Sacred Blood"),
    Player("Yuki", 82, "Frozen Abyss"),
    Player("Kai", 68, "Ashen Ruins")
]

for p in players:
    print(f"{p.name} is level {p.level} and located in {p.location}")
```

Out put

```python
Ame is level 75 and located in Cathedral of the Sacred Blood  
Yuki is level 82 and located in Frozen Abyss  
Kai is level 68 and located in Ashen Ruins
```

`ใช้ @Dataclass เพื่อสร้าง class ที่มี key-value`
\
`ข้อมูลอยู่ใน list ของ object ที่อ่านง่ายและกระชับ`

ตารางเปรียบเทียบ : Key-Value

| ภาษา   | โครงสร้าง               | การเข้าถึงข้อมูล            |
| ------ | ----------------------- | --------------------------- |
| C      | struct + array          | player\[i].key              |
| Java   | class + List            | object.key                  |
| Python | dataclass + list        | object.key                  |
| Ruby   | class หรือ Hash + Array | object.key หรือ hash\[:key] |

## Presentation <a href="#presentation" id="presentation"></a>

Slid : [https://www.canva.com/design/DAGxwUh2aCw/1a7AEiWc0X7H5oc7evfaNQ/view?utm\_content=DAGxwUh2aCw\&utm\_campaign=designshare\&utm\_medium=link2\&utm\_source=uniquelinks\&utlId=hbe515c0544](https://www.canva.com/design/DAGxwUh2aCw/1a7AEiWc0X7H5oc7evfaNQ/view?utm_content=DAGxwUh2aCw\&utm_campaign=designshare\&utm_medium=link2\&utm_source=uniquelinks\&utlId=hbe515c0544)

{% embed url="https://www.canva.com/design/DAGxwUh2aCw/1a7AEiWc0X7H5oc7evfaNQ/view?utm_content=DAGxwUh2aCw&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=hbe515c0544" %}

Video :&#x20;

## **Reference** <a href="#reference" id="reference"></a>

Convert to array ( สืบค้นเมื่อวันที่ 02/09/2568 ) :&#x20;

{% embed url="https://stackoverflow.com/questions/18358717/ruby-elegantly-convert-variable-to-an-array-if-not-an-array-already" %}

{% embed url="https://www.sourcecodeexamples.net/2023/11/ruby-convert-string-to-array.html" %}

{% embed url="https://ruby-doc.org/core-2.7.0/Array.html" %}

List Key-Value ( สืบค้นเมื่อวันที่ 02/09/2568 ) :&#x20;

{% embed url="https://coderscratchpad.com/exploring-ruby-hashes-key-value-pairs-and-methods/" %}

{% embed url="https://www.programiz.com/ruby/hash" %}
