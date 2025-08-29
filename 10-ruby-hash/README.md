# Top, Add, Swap Key and Value, Merge

## <mark style="color:$primary;">ทำความรู้จัก Methods ที่เป็นพื้นฐานที่สุดของ hash ใน Ruby</mark>

หลังจากเรารู้วิธีการสร้าง hash แบบเริ่มต้นแล้ว เราก็ต้องรู้ความสามารถพื้นฐานที่สุดด้วย โดยเราจะใช้ข้อมูล hash ตามด้านล่างนี้

```ruby
people = {jordan:32,tiffany:27,tromas:10,micheal:29}
```

<mark style="color:$info;">ผลลัพธ์</mark>

```ruby
puts people
```

{jordan: 32, tiffany: 27, tromas: 10, micheal: 29,}

***

## <mark style="color:$primary;">Add</mark>

เริ่มต้นด้วยคำสั่ง เพิ่มค่าเข้าไปใน hash โดยข้อมูลที่เพิ่มเข้าไป จะถูกนำเข้าไปเพิ่มต่อหลัง hash ท้ายสุด โดยอาศัยเพียงการใส่ key และ value ลงไปเท่านั้น

```
people[:leaon] = 42
```

<mark style="color:$info;">ผลลัพธ์</mark>

```ruby
puts people
```

{jordan: 32, tiffany: 27, tromas: 10, micheal: 29, leaon: 42}

***

## <mark style="color:$primary;">Swap Key and Value</mark>

ต่อมาเป็น คำสั่งสำหรับ สลับ key กับ value ด้วยคำสั่ง .invert โดยเราจะยกตัวอย่างในการเก็บค่าไว้ใน people\_2

```
people_2 = people.invert
```

<mark style="color:$info;">ผลลัพธ์</mark>

{32 => :jordan, 27 => :tiffany, 10 => :tromas, 29 => :micheal, 42 => :leaon}

***

## <mark style="color:$primary;">Merge</mark>

คำสั่งสุดท้ายเป็น คำสั่งสำหรับ รวม hash 2 ก้อนเข้าด้วยกัน ด้วยคำสั่ง .merge โดยเราจะยกตัวอย่างในการเก็บค่าไว้ใน people\_3

```
people_3 = people.merge(people_2)
```

<mark style="color:$info;">ผลลัพธ์</mark>

{jordan: 32, tiffany: 27, tromas: 10, micheal: 29, leaon: 42, 32 => :jordan, 27 => :tiffany, 10 => :tromas, 29 => :micheal, 42 => :leaon}

## <mark style="color:$primary;">เทียบกับภาษาอื่น</mark>&#x20;

การใช้คำสั่งต่างๆใน Ruby เทียบกับ Java

```ruby
person = { "name" => "Alice", "age" => 25 }

person["city"] = "Bangkok"

# Add key
puts person
# {"name"=>"Alice", "age"=>25, "city"=>"Bangkok"}

# Swap key กับ value
swapped = person.invert
puts swapped
# {"Alice"=>"name", 25=>"age", "Bangkok"=>"city"}

# merge hash
merged = person.merge(swapped)
puts merged
# {"name"=>"Alice", "age"=>30, "city"=>"Bangkok","Alice"=>"name", 25=>"age", "Bangkok"=>"city"}
```

```
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        HashMap<String, Object> person = new HashMap<>();
        person.put("name", "Alice");
        person.put("age", 25);

        // Add key
        person.put("city", "Bangkok");

        System.out.println(person);
        // {name=Alice, age=25, city=Bangkok}
        
        
        // Swap key กับ value
        HashMap<Object, String> swapped = new HashMap<>();
        for (Map.Entry<String, Object> entry : person.entrySet()) {
            swapped.put(entry.getValue(), entry.getKey());
        }

        System.out.println(swapped);
        // {Alice=name, 25=age, Bangkok=city}
        
        
        // Merge hash
        HashMap<String, Object> merged = new HashMap<>(person);
        merged.putAll(extra);

        System.out.println(merged);
        // {"name"=>"Alice", "age"=>30, "city"=>"Bangkok","Alice"=>"name", 25=>"age", "Bangkok"=>"city"}
    }
}

```

## <mark style="color:$primary;">Reference</mark>

Ruby knowledge :&#x20;

[https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Comprehensive%20Ruby%20Programming.pdf](https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Comprehensive%20Ruby%20Programming.pdf)

Java knowledge :&#x20;

[https://www.w3schools.com/java/java\_hashmap.asp](https://www.w3schools.com/java/java_hashmap.asp)
