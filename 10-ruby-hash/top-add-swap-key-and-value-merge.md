# Top, Add, Swap Key and Value, Merge

### <mark style="color:$primary;">ทำความรู้จัก Methods ที่เป็นพื้นฐานที่สุดของ hash ใน Ruby</mark>

หลังจากเรารู้วิธีการสร้าง hash แบบเริ่มต้นแล้ว เราก็ต้องรู้ความสามารถพื้นฐานที่สุดด้วย โดยเราจะใช้ข้อมูล hash ตามด้านล่างนี้

```ruby
people = {jordan:32,tiffany:27,tromas:10,micheal:29}
```

ผลลัพธ์

```ruby
puts people
```

{jordan: 32, tiffany: 27, tromas: 10, micheal: 29,}

***

## <mark style="color:$success;">Add</mark>

เริ่มต้นด้วยคำสั่ง เพิ่มค่าเข้าไปใน hash โดยข้อมูลที่เพิ่มเข้าไป จะถูกนำเข้าไปเพิ่มต่อหลัง hash ท้ายสุด โดยอาศัยเพียงการใส่ key และ value ลงไปเท่านั้น

```ruby
people[:leaon] = 42
```

<mark style="color:$info;">ผลลัพธ์</mark>

```ruby
puts people
```

{jordan: 32, tiffany: 27, tromas: 10, micheal: 29, leaon: 42}

***

## <mark style="color:$success;">**Swap Key and Value**</mark>

ต่อมาเป็น คำสั่งสำหรับ สลับ key กับ value ด้วยคำสั่ง .invert โดยเราจะยกตัวอย่างในการเก็บค่าไว้ใน people\_2

```ruby
people_2 = people.invert
```

<mark style="color:$info;">ผลลัพธ์</mark>

{32 => :jordan, 27 => :tiffany, 10 => :tromas, 29 => :micheal, 42 => :leaon}

***

## <mark style="color:$success;">**Merge**</mark>

คำสั่งสุดท้ายเป็น คำสั่งสำหรับ รวม hash 2 ก้อนเข้าด้วยกัน ด้วยคำสั่ง .merge โดยเราจะยกตัวอย่างในการเก็บค่าไว้ใน people\_3

```
people_3 = people.merge(people_2)
```

ผลลัพธ์

{jordan: 32, tiffany: 27, tromas: 10, micheal: 29, leaon: 42, 32 => :jordan, 27 => :tiffany, 10 => :tromas, 29 => :micheal, 42 => :leaon}

***

## <mark style="color:$primary;">**เทียบกับภาษาอื่น**</mark>

การใช้คำสั่งต่างๆใน Ruby เทียบกับ Java

#### Ruby

```ruby
person = { "name" => "Alice", "age" => 25 }

# Add key
person["city"] = "Bangkok"
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

#### **JAVA**

```java
import java.util.HashMap;
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        // Create a HashMap
        HashMap<String, Object> person = new HashMap<>();
        person.put("name", "Alice");
        person.put("age", 25);
        // Add key
        person.put("city", "Bangkok");

        System.out.println(person);
        // Output: {name=Alice, age=25, city=Bangkok}

        // Swap key and value
        HashMap<Object, String> swapped = new HashMap<>();
        for (Map.Entry<String, Object> entry : person.entrySet()) {
            swapped.put(entry.getValue(), entry.getKey());
        }

        System.out.println(swapped);
        // Output: {Alice=name, 25=age, Bangkok=city}

        // Merge hash
        // Assuming 'extra' is defined somewhere. For example:
        HashMap<String, Object> extra = new HashMap<>();
        extra.put("age", 30); // overriding age
        extra.put("Alice", "name");
        extra.put("25", "age");
        extra.put("Bangkok", "city");

        HashMap<String, Object> merged = new HashMap<>(person);
        merged.putAll(extra);

        System.out.println(merged);
        // Output: {name=Alice, age=30, city=Bangkok, Alice=name, 25=age, Bangkok=city}
    }
}

```

#### C <a href="#c" id="c"></a>

```c
#include <stdio.h>
#include <string.h>

#define MAX 10
#define KEY_SIZE 50
#define VALUE_SIZE 50

typedef struct {
    char key[KEY_SIZE];
    char value[VALUE_SIZE];
} Pair;

typedef struct {
    Pair data[MAX];
    int size;
} Hash;

// Print hash
void printHash(Hash *h) {
    printf("{ ");
    for (int i = 0; i < h->size; i++) {
        printf("\"%s\" => \"%s\"", h->data[i].key, h->data[i].value);
        if (i < h->size - 1) printf(", ");
    }
    printf(" }\n");
}

// Add key and value
void add(Hash *h, const char *key, const char *value) {
    if (h->size < MAX) {
        strcpy(h->data[h->size].key, key);
        strcpy(h->data[h->size].value, value);
        h->size++;
    }
}

// Swap key and value
Hash invert(Hash *h) {
    Hash swapped;
    swapped.size = 0;
    for (int i = 0; i < h->size; i++) {
        add(&swapped, h->data[i].value, h->data[i].key);
    }
    return swapped;
}

// Merge two hashes
Hash merge(Hash *h1, Hash *h2) {
    Hash merged;
    merged.size = 0;

    // Copy h1
    for (int i = 0; i < h1->size; i++) {
        add(&merged, h1->data[i].key, h1->data[i].value);
    }

    // Copy h2
    for (int i = 0; i < h2->size; i++) {
        add(&merged, h2->data[i].key, h2->data[i].value);
    }

    return merged;
}

int main() {
    Hash person;
    person.size = 0;

    add(&person, "name", "Alice");
    add(&person, "age", "25");
    add(&person, "city", "Bangkok");

    printf("Original: ");
    printHash(&person);

    Hash swapped = invert(&person);
    printf("Swapped: ");
    printHash(&swapped);

    Hash merged = merge(&person, &swapped);
    printf("Merged: ");
    printHash(&merged);

    return 0;
}

```

#### Python <a href="#python" id="python"></a>

```python
# Python มันไม่ได้เรียกว่า Hash จะเรียกว่า dictionary (dict)
person = {"name": "Alice", "age": 25} 

​# Add key and value
person["city"] = "Bangkok"
print(person)
# {'name': 'Alice', 'age': 25, 'city': 'Bangkok'}​

# Swap key and value
swapped = {v: k for k, v in person.items()}
print(swapped)
# {'Alice': 'name', 25: 'age', 'Bangkok': 'city'}​

# Merge dict
merged = {**person, **swapped} 
print(merged)
#( {'name': 'Alice', 'age': 25, 'city': 'Bangkok', 'Alice': 'name', 25: 'age', 'Bangkok': 'city'}​
```

***

## <mark style="color:$primary;">Presentation</mark> <a href="#presentation" id="presentation"></a>

Link video:

slice: https://www.canva.com/design/DAGzJ91qkj0/otylluOC4OdD6ha53WbkfA/view?utm_content=DAGzJ91qkj0&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=h3b9baf33c5

## <mark style="color:$primary;">**Reference**</mark> <a href="#reference" id="reference"></a>

Ruby knowledge :

[https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Comprehensive Ruby Programming.pdf](https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Comprehensive%20Ruby%20Programming.pdf)

[https://docs.ruby-lang.org/en/master/Hash.html#class-Hash-label-Common+Uses](https://docs.ruby-lang.org/en/master/Hash.html#class-Hash-label-Common+Uses)

C knowledge

[https://www.geeksforgeeks.org/dsa/implementation-of-hash-table-in-c-using-separate-chaining/](https://www.geeksforgeeks.org/dsa/implementation-of-hash-table-in-c-using-separate-chaining/)

Python knowledge

[https://www.w3schools.com/python/python\_dictionaries.asp](https://www.w3schools.com/python/python_dictionaries.asp)

Java knowledge

[https://www.w3schools.com/java/java\_hashmap.asp](https://www.w3schools.com/java/java_hashmap.asp)
