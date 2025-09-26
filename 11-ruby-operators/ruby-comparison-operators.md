# Ruby Comparison Operators

Ruby Comparison Operators ถ้าให้เข้าใจง่าย ๆ มันก็คือ เครื่องหมาย (หรือตัวดำเนินการ) ที่เอาไว้ใช้เปรียบเทียบค่านึงกับอีกค่านึง เมื่อเปรียบเทียบเสร็จจะคืนค่าตรรกะ (หรือค่าความจริง/เท็จ) กลับมา เพื่อให้เราเอาไปใช้เป็นทางเลือกให้กับโปรแกรมเรา อย่างเช่น ถ้าเปรียบเทียบว่าปีนี้เท่ากับ 2569 แล้วเป็นจริงจะให้พิมพ์ "สวัสดีปีใหม่" ออกมา แต่ถ้าไม่จริง จะให้พิมพ์ "รอก่อน" ออกมา จะทำให้โปรแกรมของเราไม่ส่งแต่ผลลัพธ์เดิมออกมา แต่มันจะขึ้นอยู่กับปีปัจจุบันว่าเป็นปี 2569 หรือไม่แทน

ตัวดำเนินการเปรียบเทียบที่จริงเป็นสิ่งที่เราเห็นผ่านตาอยู่ในชีวิตประจำวันอยู่แล้ว ในม.3 เราก็คงเคยผ่านเรื่องอสมการกันมาบ้าง อย่างเช่น x > 9 แปลว่า x สามารถเป็นได้ตั้งแต่มากกว่า 9 เป็นต้นไป (9, +inf) ดังนั้นในภาษา Ruby มีความหมายว่าถ้า x เป็นค่าใด ๆ ที่มากกว่า 9 อย่างเช่น x = 9.01, x = 10 หรือ x = 11 หลังเปรียบเทียบค่าเสร็จแล้วค่าตรรกะจะเป็นจริง หรือถ้าจะเป็นเรื่องของสมการในป.6 อย่างเช่น y = 25 ในสมการคณิตศาสตร์ ในภาษา Ruby จะมีความหมายประมาณว่าเปรียบเทียบค่าของ y กับค่า 25 (ซึ่งในภาษา Ruby ไม่ได้ใช้เป็นเครื่องหมายเท่ากับ แต่จะขอละไว้ก่อนแล้วค่อยอธิบายในหัวข้อถัด ๆ ไป) เมื่อเปรียบเทียบเสร็จจะคืนค่าตรรกะออกมา ถ้า y เป็น -1 จะคืนค่าตรรกะเป็นเท็จออกมา แต่ถ้า y เป็น 25 จะคืนค่าตรรกะเป็นจริงออกจริงออกมาแทน

## ตารางตัวดำเนินการเปรียบเทียบตัวต่าง ๆ

<table><thead><tr><th width="100">ตัวดำเนินการ</th><th>ลักษณะการทำงาน</th></tr></thead><tbody><tr><td>==</td><td>เปรียบเทียบความเท่ากัน ถ้าเท่ากันจะคืนค่าตรรกะค่าจริง ถ้าไม่เท่ากันจะคืนค่าตรรกะเท็จ</td></tr><tr><td>!=</td><td>เปรียบเทียบความเท่ากัน ถ้าเท่ากันจะคืนค่าตรรกะค่าเท็จ ถ้าไม่เท่ากันจะคืนค่าตรรกะจริง</td></tr><tr><td>&#x3C;</td><td>เปรียบเทียบค่าด้านซ้ายน้อยกว่าค่าด้านขวาหรือไม่ ถ้าใช่คืนค่าตรรกะจริง ถ้าไม่ใช้จะคืนค่าเท็จ</td></tr><tr><td>&#x3C;=</td><td>เปรียบเทียบค่าด้านซ้ายน้อยกว่าหรือเท่ากับค่าด้านขวาหรือไม่ ถ้าใช่คืนค่าตรรกะจริง ถ้าไม่ใช้จะคืนค่าเท็จ</td></tr><tr><td>></td><td>เปรียบเทียบค่าด้านซ้ายมากกว่าค่าด้านขวาหรือไม่ ถ้าใช่คืนค่าตรรกะจริง ถ้าไม่ใช้จะคืนค่าเท็จ</td></tr><tr><td>>=</td><td>เปรียบเทียบค่าด้านซ้ายมากกว่าหรือเท่ากับค่าด้านขวาหรือไม่ ถ้าใช่คืนค่าตรรกะจริง ถ้าไม่ใช้จะคืนค่าเท็จ</td></tr><tr><td>&#x3C;=></td><td>เปรียบเทียบค่าด้านซ้ายกับด้านขวา ถ้าค่าด้านซ้ายน้อยกว่าด้านขวา จะคืนค่า -1 ถ้าทั้งสองค่าเท่ากัน จะคืนค่า 0 ถ้าค่าด้านซ้ายมากกว่าดด้านขวา จะคืนค่า 1</td></tr><tr><td>===</td><td>ตรวจสอบว่าค่าด้านขวา เป็นส่วนหนึ่งของค่าด้านซ้ายหรือไม่ ถ้าใช่คืนค่าตรรกะจริง ถ้าไม่ใช่คืนค่าตรรกะเท็จ</td></tr><tr><td>=~</td><td>ตรวจสอบว่าลักษณะรูปแบบของข้อความขวา (string) ว่าตรงกับหรือเป็นส่วนหนึ่งของข้อความซ้ายหรือไม่ โดยถ้าเจอจะคืนค่า <code>index</code> เริ่มต้นของรูปแบบที่เจอของข้อความซ้ายมาให้ ถ้าไม่เจอจะคืน nil</td></tr><tr><td>!~</td><td>ตัวดำเนินการตัวนี้ทำงานเป็นนิเสธของตัวดำเนินการ <code>=~</code> ทำงานโดยตรวจสอบว่าลักษณะรูปแบบของข้อความขวา (string) ว่าต้องไม่ตรงหรือไม่เป็นส่วนหนึ่งของข้อความซ้าย ถ้าดำเนินการเปรียบเทียบแล้วว่าข้อความขวาไม่เป็นส่วนหนึ่งของข้อความซ้ายจะคืนค่าตรรกะจริงออกมา และคืนค่าเท็จออกมาในเชิงตรงกันข้าม ก็คือพบว่าข้อความขวาเป็นส่วนหนึ่งของข้อความซ้าย</td></tr></tbody></table>

## ตัวดำเนินการ ==

### 1. ใช้ตรวจสอบว่าเป็น Object เดียวกันหรือไม่

#### วิธีการใช้งาน

```ruby
obj = Object.new()
puts obj == obj
puts obj == Object.new()
```

จะแสดงผลออกมาเป็น

```
true
false
```

ที่ผลลัพธ์บรรทัด 1 แสดงผลออกมาเป็น `true` เพราะว่าเปรียบเทียบ `obj` กับ `obj` ซึ่ง `obj` นั้นคือตัวเดียวกัน ทำให้มีตำแหน่งในหน่วยความจำที่นำมาเปรียบเทียบเป็นตำแหน่งเดียวกันจึงมีผลลัพธ์เป็น true

ที่ผลลัพธ์บรรทัดที่ 2 แสดงผลออกมาเป็น `false` เนื่องจาก `obj` กับ `Object.new()` ในบรรทัดที่ 3 คือคนละตัวกัน

มีบาง class อย่างเช่น `String` ที่กำหนดการทำงานของ `==` ขึ้นใหม่ ทำให้ไม่สามารถตรวจตอบว่าเป็น `Object` เดียวกันด้วยวิธีนี้ได้ โดย `==` ของ String จะเป็นการตรวจสอบว่าเป็นข้อความเดียวกันไหมแทน

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C ไม่ได้เป็นภาษาเชิงวัตถุ จึงไม่มีวัตถุให้มาตรวจสอบ

> Python

ในภาษา Python สามารถเปรียบเทียบได้โดยใช้ `is` ตัวอย่างบรรทัดที่ 9

```python
data1 = []
data2 = []
data3=data1

if (data1 == data2):
    print("True")
else:
    print("False")
if (data1 is data2):
    print("True")
else:
    print("False")
if (data1 is data3):
    print("True")
else:
    print("False")
```

จะแสดงผลลัพธ์เป็น

```
This is true.
This is false.
This is true.
```

ที่ผลลัพธ์บรรทัดที่ 1 เป็น `true` เพราะ ค่าใน `data1` เท่ากับค่าของ `data2`

ที่ผลลัพธ์บรรทัดที่ 2 เป็น `false` เพราะ `data1` ไม่ใช่ตัวเดียวกันกับ `data2`

ที่ผลลัพธ์บรรทัดที่ 3 เป็น `true` เพราะ `data1` เป็นตัวเดียวกันกับ `data2`

> Java

ภาษา Java สามารถใช้ตัวดำเนินการ == แบบภาษา Ruby ได้เลย

```java
class main {
	public static void main(String[] args) {
		Object x = new Object();
		Object y = new Object();
		System.out.println(x == y);
	}
}
```

จะแสดงผลลัพธ์เป็น `false` เนื่องจากเป็นคนละ `Object`

### 2. ใช้เปรียบเทียบค่า

```ruby
puts 10 == 10                   # เช็ก number
puts 5 == 9 / 2.0
puts "hello" == "hello"         # เช็ก String
puts [1, "a", true] == [1, "a", true] # เช๊ก array
h1 = { name: "Alice", role: "admin" }
h2 = { role: "admin", name: "Alice" }
puts h1 == h2                   # เช็ก hash
puts :hello == :world           # เช็ก symbol
puts true == true               # เช็ก boolean
puts nil == nil                 # เช็กค่า nil ซึ่งมีค่าใน boolean เท่ากับ false 
```

จงแสดงผลลัพธ์เป็น

```
true
false
true
true
true
false
true
true
```

ที่แสดงผลลัพธ์เป็น `true` เพราะว่าทั้งสองค่ามีค่าเท่าทัน

ที่ผลลัพธ์บรรทัดที่ 2 มีผลลัพธ์เป็น `false` เพราะว่าใน 5 ไม่เท่ากับ 4.5

และที่ผลลัพธ์บรรทัดที่ 6 มีผลลัพธ์เป็น `false` เพราะว่า `symbol` มีซื่อ `symbol` ที่ไม่เหมือนกัน

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C เราสามารถใช้ตัวดำเนินการ `==` ได้เลย

```c
#include <stdio.h>
#include <string.h>

int is_equal(int *array1, int *array2) {
	int arr1_size = sizeof(array1) / sizeof(array1[0]);
	int arr2_size = sizeof(array2) / sizeof(array2[0]);
  
	if (arr1_size != arr2_size) {
		return -1;
	}

	for (int i = 0; i < arr1_size; i++) {
		if (array1[i] != array2[i]) {
			return -1;
                }
	}
	return 1;
}

int main() {
	int x[] = {1, 2, 3, 4};
        int y[] = {5, 6, 7, 8};
	
	printf("%d\n", 10 == 10);
	printf("%d\n", 5 == 9 / 2.0);
	printf("%d\n", strcmp("hello", "hello") == 0);
        printf("%d\n", is_equal(x, x));
	printf("%d\n", is_equal(x, y));
	printf("%d\n", 1 == 1);
	printf("%d\n", NULL == NULL);
	return 0;
}
```

จะได้ผลลัพธ์เป็น

```
1
0
1
1
-1
1
1
```

ที่ได้ผลลัพธ์เป็น 1 กับ 0 ในภาษา C เพราะว่าภาษา C ไม่มี `boolean` แต่จะถือว่า 0 เป็นค่าตรรกะเท็จ และค่าอื่น ๆ ที่ไม่ใช่ 0 จะเป็นจริงทั้งหมด

> Python

ภาษา Python เราสามารถใช้ตัวดำเนินการ `==` ได้เลย

```python
print(10 == 10)
print(5 == 9 / 2.0)
print("hello" == "hello")
print([1, "a", True] == [1, "a", True])
h1 = {"name": "Alice", "role": "admin"}
h2 = {"role": "admin", "name": "Alice"}
print(h1 == h2)
print("hello" == "world")
print(True == True)
print(None == None)
```

จะได้ผลลัพธ์เป็น

```
True
False
True
True
True
False
True
True
```

> Java

ภาษา Java เราสามารถใช้ตัวดำเนินการ `==` ได้เลย

```java
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class main {
    public static void main(String[] args) {
        System.out.println(10 == 10);
        System.out.println(5 == 9 / 2.0);
        System.out.println("hello".equals("hello"));
        List<Object> list1 = Arrays.asList(1, "a", true);
        List<Object> list2 = Arrays.asList(1, "a", true);
        System.out.println(list1.equals(list2));
        Map<String, String> h1 = new HashMap<>();
        h1.put("name", "Alice");
        h1.put("role", "admin");
        Map<String, String> h2 = new HashMap<>();
        h2.put("role", "admin");
        h2.put("name", "Alice");
        System.out.println(h1.equals(h2));
        System.out.println("hello".equals("world"));
        System.out.println(true == true);
        System.out.println(null == null);
    }
}
```

จะได้ผลลัพธ์เป็น

```
true
false
true
true
true
false
true
true
```

ทั้ง Python และ Java ต่างก็มี `boolean` เป็นของตัวเอง ทำให้ผลลัพธ์ไม่ต่างจาก Ruby มากนัก

## ตัวดำเนินการ !=

### 1. ใช้ตรวจสอบว่าไม่เป็น Object เดียวกัน

#### วิธีใช้งาน

```ruby
obj = Object.new()
puts obj != obj
puts obj != Object.new()
```

จะได้ผลลัพธ์เป็น

```
false
true
```

ผลลัพธ์ที่ได้จะเป็นการเช็กว่าวัตถุหนึ่งไม่ใช่วัตถุเดียวกันกับอีกวัตถุหนึ่ง หรือพูดได้ว่า `!=` นั้นเป็นนิเสธของ `==` นั่นเอง

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C ไม่ได้เป็นภาษาเชิงวัตถุ จึงไม่มีวัตถุให้มาตรวจสอบ

> Python

ภาษา Python เราสามารถ `is not` ทดแทนได้

```python
data1 = []
data2 = []
data3=data1

if (data1 is not data3):
    print("True")
else:
    print("False")
```

จะได้ผลลัพธ์เป็น `False`

> Java

ภาษา Java เราสามารถใช้ตัวดำเนินการ !`=` ได้เลย

```java
class main {
	public static void main(String[] args) {
		Object x = new Object();
		Object y = new Object();
		System.out.println(x != y);
	}
}
```

จะได้ผลลัพธ์เป็น `true`

### 2. ใช้เปรียบเทียบค่า

```ruby
puts 10 != 10                   # เช็ก number
puts 5 != 9 / 2.0
puts "hello" != "hello"         # เช็ก String
puts [1, "a", true] != [1, "a", true] # เช๊ก array
h1 = { name: "Alice", role: "admin" }
h2 = { role: "admin", name: "Alice" }
puts h1 != h2                   # เช็ก hash
puts :hello != :world           # เช็ก symbol
puts true != true               # เช็ก boolean
puts nil != nil                 # เช็กค่า nil ซึ่งมีค่าใน boolean เท่ากับ false 
```

จะได้ผลลัพธ์เป็น

```
false
true
false
false
false
true
false
false
```

จะเห็นว่า Ruby จะคืนค่า `false` ถ้าค่าทั้งสองเท่ากัน และคืนค่า `true` ถ้าค่าทั้งสองไม่เท่ากัน

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C เราสามารถใช้ตัวดำเนินการ !`=` ได้เลย

```c
#include <stdio.h>
#include <string.h>

int main() {
	printf("%d\n", 10 != 10);
	printf("%d\n", 5 != 9 / 2.0);
	printf("%d\n", strcmp("hello", "hello") != 0);
	printf("%d\n", strcmp("hello", "world") != 0);
	printf("%d\n", 1 != 1);
	printf("%d\n", NULL != NULL);
	return 0;
}

```

จะได้ผลลัพธ์เป็น

```
0
1
0
1
0
0
```

> Python

ภาษา Python เราสามารถใช้ตัวดำเนินการ !`=` ได้เลย

```python
print(10 != 10)
print(5 != 9 / 2.0)
print("hello" != "hello")
print([1, "a", True] != [1, "a", True])
h1 = {"name": "Alice", "role": "admin"}
h2 = {"role": "admin", "name": "Alice"}
print(h1 != h2)
print("hello" != "world")
print(True != True)
print(None != None)
```

จะได้ผลลัพธ์เป็น

```
False
True
False
False
False
True
False
False
```

> Java

ภาษา Java เราสามารถใช้ตัวดำเนินการ !`=` ได้เลย

```java
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class EqualityChecks {
	public static void main(String[] args) {
		System.out.println(10 != 10);
		System.out.println(5 != 9 / 2.0);
		System.out.println(!"hello".equals("hello"));
		List<Object> list1 = Arrays.asList(1, "a", true);
		List<Object> list2 = Arrays.asList(1, "a", true);
		System.out.println(!list1.equals(list2));
		Map<String, String> h1 = new HashMap<>();
		h1.put("name", "Alice");
		h1.put("role", "admin");
		Map<String, String> h2 = new HashMap<>();
		h2.put("role", "admin");
		h2.put("name", "Alice");
		System.out.println(!h1.equals(h2));
		System.out.println(!"hello".equals("world"));
		System.out.println(true != true);
		System.out.println(null != null);
	}
}
```

จะได้ผลลัพธ์เป็น

```
false
true
false
false
false
true
false
false
```

## ตัวดำเนินการ >, >=, <, <=

### 1. ใช้ตรวจสอบว่า `class` นั้นได้สืบทอดมาจาก `class` อื่นหรือไม่

สำหรับตัวดำเนินการ `>` จะคืนค่าค่าตรรกะจริงถ้า `class` ด้านซ้ายเป็น `class` แม่ของ `class` ทางด้านขวา และคืนค่าตรรกะเท็จถ้า `class` ด้านซ้ายเป็น `class` ลูกของ `class` ทางด้านขวาหรือ `class` ทั้งสองเป็น `class` เดียวกัน หรือก็คือเราสามารถบอกได้ว่ามันจะคืนค่าตรรกะเท็จเมื่อเป็นกรณีอื่น

ตัวดำเนินการ `<` นั้นจะคืนค่าตรรกะจริงถ้า `class` ด้านซ้ายเป็น `class` ลูกของ `class` ทางด้านขวา และคืนค่าตรรกะเท็จเมื่อเป็นกรณีอื่น

ตัวดำเนินการ `>=` นั้น จะคืนค่าตรรกะจริงถ้า `class` ด้านซ้ายเป็น `class` แม่ของ `class` ทางด้านขวาหรือ `class` ทั้งสองเป็น c`lass` เดียวกัน และคืนค่าตรรกะเท็จถ้าเป็นกรณีอื่น

ตัวดำเนินการ <`=` นั้น จะคืนค่าตรรกะจริงถ้า `class` ด้านซ้ายเป็น `class` ลูกของ `class` ทางด้านขวาหรือ `class` ทั้งสองเป็น `class` เดียวกัน และคืนค่าตรรกะเท็จถ้าเป็นกรณีอื่น

```ruby
class B                         # ประกาศ class B
end

class A < B                     # ประกาศ class A โดนเป็นลูกของ class B
end

puts A > B
puts A >= B
puts A < B
puts A <= B
puts String >= String
```

จะได้ผลลัพธ์เป็น

```
false
false
true
true
true
```

ที่ผลลัพธ์บรรทัดที่ 1 และ 2 ได้ค่าเป็น `false` เพราะ A ไม่ใช่ `class` แม่ของ B หรือเป็น `class` เดียวกันกับ B

ที่ผลลัพธ์บรรทัดที่ 3 และ 4 ได้ค่าเป็น `true` เพราะ B เป็น `class` แม่ของ A

ที่ผลลัพธ์บรรทัดที่ 5 ได้ค่าเป็น `true` เพราะเป็น class เดียวกัน

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C ไม่ได้เป็นภาษาเชิงวัตถุ จึงไม่มีคลาสให้มาตรวจสอบ

> Python

ภาษา Python เราสามารถใช้ `method` `issubclass(A, B)` ได้

```python
class B:                        # ประกาศ class B
    def do_thing():
        print("It in B class")

class A(B):                     # ประกาศ class A โดยเป็น class ลูกของ B
    def new_thing():
        print("Hello")

print(issubclass(A, B))
print(issubclass(B, A))
```

จะได้ผลลัพธ์เป็น

```
True
False
```

ที่ได้ค่าเป็น `True` ก็เพราะว่า `class` A เป็น `class` ลูก (subclass) ของ B และบรรทัดที่ได้ `False` เพราะ B ไม่ใช่ `class` ลูกของ A แต่เป็น `class` แม่

> Java

ภาษา Java เราสามารถใช้ `method` `isAssignableFrom(class)` ได้ โดยจำเป็นต้องใช้ `A.class`, `B.class` เพื่อให้ได้ตัวแทนของ `class` ออกมาเพื่อที่จะไปเทียบได้

```java
class main {
	public static void main(String[] args) {
		System.out.println(A.class.isAssignableFrom(B.class));
		System.out.println(B.class.isAssignableFrom(A.class));
		System.out.println(A.class.isAssignableFrom(A.class));
	}
}

class B {			// ประกาศ class B
}

class A extends B {		// ประกาศ class A โดยเป็น class ลูกของ B
}
```

จะได้ผลลัพธ์เป็น

```
false
true
true
```

### 2. ใช้เปรียบเทียบค่า

ในภาษา Ruby ตัวดำเนินการเหล่านี้สามารถเปรียบเทียบได้ทั้งตัวเลขต่าง ๆ (`Numberic`,`Integer`, `Float`, `Rational`) ว่าค่าใดมากกว่าหรือน้อยกว่า

เทียบกับข้อความ ว่าข้อความใดมีตัวอักษรที่เริ่มต้นก่อน

เทียบกับเวลา (`Time`, `Date`, `DateTime`) ว่าเวลาใดเริ่มต้นก่อนหรือหลัง

เทียบกับ `Symbol` ว่า `Symbol` ใดมีตัวอักษรที่เริ่มต้นก่อนกัน

```ruby
require 'date'
require 'time'

# เปรียบเทียบค่าที่เป็นตัวเลข
puts 5 < 10
puts 3.14 < 3.141
puts 100 < 99

# เปรียบเทียบค่าที่เป็นตัวอักษร
puts "apple" < "banana"
puts "ruby" < "rubies"
puts "Zebra" < "apple"

# เปรียบเทียบเวลา
t1 = Time.new(2025, 9, 3, 10, 00, 0, "+07:00")
t2 = t1 + 3600                  # เพิ่มไป 1 ชม.
puts t1 < t2

d1 = Date.new(2025, 1, 1)
d2 = Date.new(2024, 1, 1)
puts d1 < d2

# เปรียบเทียบ Symbol
puts :alpha < :beta
puts :zulu < :yankee
```

จะได้ผลลัพธ์เป็น

```
true
true
false
true
false
true
true
false
true
false
```

ในผลลัพธ์บรรทัดที่ 1-3 เป็นผลลัพธ์จากการเปรียบเทียบว่าค่าใดมากกว่า

ในผลลัพธ์บรรทัดที่ 4-6 เป็นผลลัพธ์จากการเปรียบเทียบลำดับ ASCII ของตัวอักษรแต่ละตัว โดยเริ่มที่ตัวแรกแล้วไปเรื่อย ๆ จนกว่าจะเจอตัวอักษรตัวที่แตกต่าง จึงจะคืนค่าตรรกะแล้วหยุดทำงาน

ในผลลัพธ์บรรทัดที่ 7-8 เป็นผลลัพธ์จากการเปรียบเทียบวัน เวลา

ในผลลัพธ์บรรทัดที่ 9-10 เป็นผลลัพธ์จากการเปรียบเทียบจากการเปรียบเทียบลำดับ ASCII ของตัวอักษรใน Symbol แต่ละตัว โดยหลักการทำงานคล้ายกับการเปรียบเทียบข้อความ

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C เราสามารถใช้ตัวดำเนินการเปรียบเทียบได้เลย แต่ในการเทียบข้อความ จำเป็นต้องใช้ `strcmp(char *string)` และในการเทียบเวลา จำเป็นต้องใช้ `difftime(x, y)`

```c
#include <stdio.h>
#include <string.h>
#include <time.h>

int main() {
	printf("%d\n", 5 < 10);
	printf("%d\n", 3.14 < 3.141);
	printf("%d\n", 100 < 99);

	printf("%d\n", strcmp("apple", "banana") < 0);
	printf("%d\n", strcmp("ruby", "rubies") < 0);
	printf("%d\n", strcmp("Zebra", "apple") < 0);
    
	struct tm time_info_1 = {0};
	time_info_1.tm_year = 2025 - 1900;
	time_info_1.tm_mon = 9 - 1;
	time_info_1.tm_mday = 3;
	time_info_1.tm_hour = 10;
	time_t t1 = mktime(&time_info_1);
	time_t t2 = t1 + 3600;
	printf("%d\n", difftime(t1, t2) < 0);

	struct tm date_info_1 = {0};
	date_info_1.tm_year = 2025 - 1900;
	date_info_1.tm_mon = 1 - 1;
	date_info_1.tm_mday = 1;
	time_t d1 = mktime(&date_info_1);
    
	struct tm date_info_2 = {0};
	date_info_2.tm_year = 2024 - 1900;
	date_info_2.tm_mon = 1 - 1;
	date_info_2.tm_mday = 1;
	time_t d2 = mktime(&date_info_2);
	printf("%d\n", difftime(d1, d2) < 0);

	printf("%d\n", strcmp("alpha", "beta") < 0);
	printf("%d\n", strcmp("zulu", "yankee") < 0);

	return 0;
}
```

จะได้ผลลัพธ์เป็น

```
1
1
0
1
0
1
1
0
1
0
```

> Python

ภาษา Python เราสามารถใช้ตัวดำเนินการเปรียบเทียบได้แบบภาษา Ruby ได้เลย

```python
import datetime

print(5 < 10)
print(3.14 < 3.141)
print(100 < 99)

print("apple" < "banana")
print("ruby" < "rubies")
print("Zebra" < "apple")

tz = datetime.timezone(datetime.timedelta(hours=7))
t1 = datetime.datetime(2025, 9, 3, 10, 0, 0, tzinfo=tz)
t2 = t1 + datetime.timedelta(hours=1)
print(t1 < t2)

d1 = datetime.date(2025, 1, 1)
d2 = datetime.date(2024, 1, 1)
print(d1 < d2)

print("alpha" < "beta")
print("zulu" < "yankee")
```

จะได้ผลลัพธ์เป็น

```
True
True
False
True
False
True
True
False
True
False
```

> Java

ภาษา Java เราสามารถใช้ตัวดำเนินการเทียบได้เลย แต่ในการเทียบข้อความ จำเป็นต้องใช้ `method` `compareTo` และในการเทียบเวลา จำเป็นต้องใช้ `method` `isBefore`

```java
import java.time.LocalDate;
import java.time.ZoneId;
import java.time.ZonedDateTime;

public class EqualityChecks {
	public static void main(String[] args) {
		System.out.println(5 < 10);
		System.out.println(3.14 < 3.141);
		System.out.println(100 < 99);

		System.out.println("apple".compareTo("banana") < 0);
		System.out.println("ruby".compareTo("rubies") < 0);
		System.out.println("Zebra".compareTo("apple") < 0);

		ZoneId bangkokZone = ZoneId.of("Asia/Bangkok");
		ZonedDateTime t1 = ZonedDateTime.of(2025, 9, 3, 10, 0, 0, 0, bangkokZone);
		ZonedDateTime t2 = t1.plusHours(1);
		System.out.println(t1.isBefore(t2));

		LocalDate d1 = LocalDate.of(2025, 1, 1);
		LocalDate d2 = LocalDate.of(2024, 1, 1);
		System.out.println(d1.isBefore(d2));

		System.out.println("alpha".compareTo("beta") < 0);
		System.out.println("zulu".compareTo("yankee") < 0);
	}
}

```

จะได้ผลลัพธ์เป็น

```
true
true
false
true
false
true
true
false
true
false
```

## ตัวดำเนินการ <=>

ตัวดำเนินการเป็นตัวดำเนินการพิเศษที่ไม่มีอยู่ในภาษาอื่น หลักการการทำงานคล้าย ๆ กับ `>`,`>=`,`<`,`<=`,`==` เลย โดยที่จะคืนค่า `-1` ถ้าค่าด้านซ้ายน้อยกว่าค่าด้านขวา คืนค่า `0` ถ้าค่าทั้งสองข้างเท่ากัน คืนค่า `1` ถ้าค่าด้านซ้ายมากกว่าค่าด้านขวา

```ruby
require 'date'
require 'time'

# เปรียบเทียบค่าที่เป็นตัวเลข
puts 5 <=> 10
puts 3.14 <=> 3.141
puts 100 <=> 99
puts 10 <=> 10

# เปรียบเทียบค่าที่เป็นตัวอักษร
puts "apple" <=> "banana"
puts "ruby" <=> "rubies"
puts "Zebra" <=> "apple"

# เปรียบเทียบเวลา
t1 = Time.new(2025, 9, 3, 10, 0, 0, "+07:00")
t2 = t1 + 3600                  # เพิ่มไป 1 ชม.
puts t1 <=> t2

d1 = Date.new(2025, 1, 1)
d2 = Date.new(2024, 1, 1)
puts d1 <=> d2

# เปรียบเทียบ Symbol
puts :alpha <=> :beta
puts :zulu <=> :yankee
```

จะได้ผลลัพธ์เป็น

```
-1
-1
1
0
-1
1
-1
-1
1
-1
1
```

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C ไม่มี `spaceship operator` แต่เราสามารถ `function` ทำขึ้นมาให้คืนค่าให้มีคุณสมบัติคล้าย ๆ กับ `spaceship operator` ได้ หรือจะใช้ตัวดำเนินการขึ้นทดแทน อย่างเช่น  >,== ได้

```c
#include <stdio.h>
#include <string.h>
#include <time.h>

int normalize_comparison(int result) {
	if (result < 0) return -1;
	if (result > 0) return 1;
	return 0;
}

int compare_double(double a, double b) {
	if (a < b) return -1;
	if (a > b) return 1;
	return 0;
}

int main() {
	printf("%d\n", compare_double(5, 10));
	printf("%d\n", compare_double(3.14, 3.141));
	printf("%d\n", compare_double(100, 99));
	printf("%d\n", compare_double(10, 10));
    
	printf("%d\n", normalize_comparison(strcmp("apple", "banana")));
	printf("%d\n", normalize_comparison(strcmp("ruby", "rubies")));
	printf("%d\n", normalize_comparison(strcmp("Zebra", "apple")));
    
	struct tm time_info_1 = {0};
	time_info_1.tm_year = 2025 - 1900;
	time_info_1.tm_mon = 8;
	time_info_1.tm_mday = 3;
	time_info_1.tm_hour = 10;
	time_t t1 = mktime(&time_info_1);
	time_t t2 = t1 + 3600;
	printf("%d\n", compare_double(difftime(t1, t2), 0.0));

	struct tm date_info_1 = {0};
	date_info_1.tm_year = 2025 - 1900;
	time_t d1 = mktime(&date_info_1);
    
	struct tm date_info_2 = {0};
	date_info_2.tm_year = 2024 - 1900;
	time_t d2 = mktime(&date_info_2);
	printf("%d\n", compare_double(difftime(d1, d2), 0.0));

	printf("%d\n", normalize_comparison(strcmp("alpha", "beta")));
	printf("%d\n", normalize_comparison(strcmp("zulu", "yankee")));

	return 0;
}
```

จะได้ผลลัพธ์เป็น

```
-1
-1
1
0
-1
1
-1
-1
1
-1
1
```

> Python

ภาษา Python ไม่มี `spaceship operator` แต่เราสามารถ `function` ทำขึ้นมาให้คืนค่าให้มีคุณสมบัติคล้าย ๆ กับ `spaceship operator` ได้ หรือจะใช้ตัวดำเนินการขึ้นทดแทน อย่างเช่น  >,== ได้

```python
import datetime

def spaceship_compare(a, b):
    if a < b:
        return -1
    elif a > b:
        return 1
    else:
        return 0

print(spaceship_compare(5, 10))
print(spaceship_compare(3.14, 3.141))
print(spaceship_compare(100, 99))
print(spaceship_compare(10, 10))

print(spaceship_compare("apple", "banana"))
print(spaceship_compare("ruby", "rubies"))
print(spaceship_compare("Zebra", "apple"))

tz = datetime.timezone(datetime.timedelta(hours=7))
t1 = datetime.datetime(2025, 9, 3, 10, 0, 0, tzinfo=tz)
t2 = t1 + datetime.timedelta(hours=1)
print(spaceship_compare(t1, t2))

d1 = datetime.date(2025, 1, 1)
d2 = datetime.date(2024, 1, 1)
print(spaceship_compare(d1, d2))

print(spaceship_compare("alpha", "beta"))
print(spaceship_compare("zulu", "yankee"))
```

จะได้ผลลัพธ์เป็น

```
-1
-1
1
0
-1
1
-1
-1
1
-1
1
```

> Java

ภาษา Java ไม่มี `spaceship operator` แต่มี `method` `compare` ที่มีคุณสมบัติคล้าย ๆ กัน

```java
import java.time.LocalDate;
import java.time.ZoneId;
import java.time.ZonedDateTime;

public class ComparisonChecks {
	public static void main(String[] args) {
		System.out.println(Integer.compare(5, 10));
		System.out.println(Double.compare(3.14, 3.141));
		System.out.println(Integer.compare(100, 99));
		System.out.println(Integer.compare(10, 10));

		System.out.println("apple".compareTo("banana"));
		System.out.println("ruby".compareTo("rubies"));
		System.out.println("Zebra".compareTo("apple"));

		ZoneId bangkokZone = ZoneId.of("Asia/Bangkok");
		ZonedDateTime t1 = ZonedDateTime.of(2025, 9, 3, 10, 0, 0, 0, bangkokZone);
		ZonedDateTime t2 = t1.plusHours(1);
		System.out.println(t1.compareTo(t2));

		LocalDate d1 = LocalDate.of(2025, 1, 1);
		LocalDate d2 = LocalDate.of(2024, 1, 1);
		System.out.println(d1.compareTo(d2));

		System.out.println("alpha".compareTo("beta"));
		System.out.println("zulu".compareTo("yankee"));
	}
}
```

จะได้ผลลัพธ์เป็น

```
-1
-1
1
0
-1
16
-7
-1
1
-1
1
```

## ตัวดำเนินการ ===

### 1. ตรวจสอบว่า มีค่าใน `Range` หรือไม่

```ruby
puts (1..10) === 5
puts (1..10) === 15
puts ('a'..'f') === 'c'
```

จะได้ผลลัพธ์เป็น

```
true
false
true
```

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C ไม่สามารถทำแบบนี้ได้ จำเป็นต้องแปลงให้เงื่อนไขมากกว่า น้อยกว่า และเชื่อมเงื่อนไขทั้งสองด้วย "และ (`&&`)" เอา

```c
#include <stdio.h>

int main() {
	printf("%d\n", 5 >= 1 && 5 <= 10);
	printf("%d\n", 15 >= 1 && 15 <= 10);
	printf("%d\n", 'c' >= 'a' && 'c' <= 'f');
	return 0;
}
```

จะได้ผลลัพธ์เป็น

```
1
0
1
```

> Python

ภาษา Python สามารถใช้โดยให้ค่าที่เอาจะตรวจสอบ อยู่ระหว่างกลางช่วงค่าที่จะตรวจสอบ ซึ่งระหว่างค่าที่จะตรวจสอบและช่วงค่าที่จะตรวจสอบ จำเป็นต้องเชื่อมด้วยเงื่อนไข

```python
print(1 <= 5 <= 10)
print(1 <= 15 <= 10)
print('a' <= 'c' <= 'f')
```

จะได้ผลลัพธ์เป็น

```
True
False
True
```

> Java

ภาษา Java ไม่สามารถทำแบบนี้ได้ จำเป็นต้องแปลงให้เงื่อนไขมากกว่า น้อยกว่า และเชื่อมเงื่อนไขทั้งสองด้วย "และ (`&&`)" เอา

```java
public class ComparisonChecks {
	public static void main(String[] args) {
		System.out.println(5 >= 1 && 5 <= 10);
		System.out.println(15 >= 1 && 15 <= 10);
		System.out.println('c' >= 'a' && 'c' <= 'f');
	}
}
```

จะได้ผลลัพธ์เป็น

```
true
false
true
```

### 2. ตรวจสอบว่า `Object` นั้นเป็นของ `class` นั้นหรือไม่

<pre class="language-ruby"><code class="lang-ruby"><strong>puts String === "hello"
</strong>puts Numeric === 123.45
puts Integer === 123.45
</code></pre>

จะได้ผลลัพธ์เป็น

```
true
true
false
```

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C ไม่ได้เป็นภาษาเชิงวัตถุ จึงไม่มีวัตถุให้มาตรวจสอบ

> Python

ภาษา Python สามารถตรวจสอบโดยใช้ `function`/`method` `isinstance` ได้

```python
import numbers

print(isinstance("hello", str))
print(isinstance(123.45, numbers.Number))
print(isinstance(123.45, int))
```

จะได้ผลลัพธ์เป็น

```
True
True
False
```

> Java

ภาษา Java ไม่สามารถใช้ `instanceof` โดยตรงได้ถ้า `Object` ที่เอามาตรวจสอบไม่ใช่ลูกของ `Class` นั้นเพราะจะทำให้เกิด `Exception` ดังนั้นจึงตรวจสอบโดยเอา `Class` มาเปรียบเทียบกันแทน

```java
public class ComparisonChecks {
	public static void main(String[] args) {
		System.out.println("hello" instanceof String);
		System.out.println(Double.valueOf(123.45).getClass().equals(Double.class));
		System.out.println(Double.valueOf(123.45).getClass().equals(Float.class));
	}
}
```

จะได้ผลลัพธ์เป็น

```
true
true
false
```

### 3. ใช้กับการตรวจสอบค่า Regexp

```ruby
puts /hello/ === "hello world"
puts /^\d+$/ === "12345"
puts /^\d+$/ === "user123"
```

จะได้ผลลัพธ์เป็น

```
true
true
false
```

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C ไม่มีตัวดำเนินการของ `regex` โดยเฉพาะ จึงต้องนำเข้า `library` `regex` มาใช้งานแทน

```c
#include <stdio.h>
#include <regex.h>

int check_match(const char *pattern, const char *str) {
	regex_t regex;
	int result;

	if (regcomp(&regex, pattern, REG_EXTENDED) != 0) {
		return 0; 
	}

	result = regexec(&regex, str, 0, NULL, 0);
	regfree(&regex);

	return result == 0;
}

int main() {
	printf("%d\n", check_match("hello", "hello world"));
	printf("%d\n", check_match("^[0-9]+$", "12345"));
	printf("%d\n", check_match("^[0-9]+$", "user123"));
	return 0;
}
```

จะได้ผลลัพธ์เป็น

```
1
1
0
```

> Python

ภาษา Python ไม่มีตัวดำเนินการของ `regex` โดยเฉพาะ จึงต้องนำเข้า `re` มาเพื่อใช้งานแทน

```python
import re

print(bool(re.search(r"hello", "hello world")))
print(bool(re.match(r"^\d+$", "12345")))
print(bool(re.match(r"^\d+$", "user123")))
```

จะได้ผลลัพธ์เป็น

```
True
True
False
```

> Java

ภาษา Java ไม่มีตัวดำเนินการของ `regex` โดยเฉพาะ จึงต้องนำเข้า `Class` `Pattern` ของ `regex` มาเพื่อใช้งานแทน

```java
import java.util.regex.Pattern;

public class RegexChecks {
	public static void main(String[] args) {
		System.out.println(Pattern.compile("hello").matcher("hello world").find());
		System.out.println("12345".matches("^\\d+$"));
		System.out.println("user123".matches("^\\d+$"));
	}
}
```

จะได้ผลลัพธ์เป็น

```
true
true
false
```

### 4. เปรียบเทียบค่าปกติ

ในกรณีอื่น ๆ ที่ไม่ใช่ 3 ข้อข้างต้น `===` จะทำหน้าที่เหมือน `==`

```ruby
puts 42 === 42
puts "abc" === "abc"
```

จะได้ผลลัพธ์เป็น

```
true
true
```

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C สามารถทดแทนด้วยการใช้ `==` กับ `strcmp`

```c
#include <stdio.h>
#include <string.h>

int main() {
	printf("%d\n", 42 == 42);
	printf("%d\n", strcmp("abc", "abc") == 0);
	return 0;
}
```

จะได้ผลลัพธ์เป็น

```
1
1
```

> Python

ภาษา Python สามารถทดแทนด้วยการใช้ `==`

```python
print(42 == 42)
print("abc" == "abc")
```

จะได้ผลลัพธ์เป็น

```
True
True
```

> Java

ภาษา Java สามารถทดแทนด้วยการใช้ `==` กับ  `method` `equals`

```java
public class ComparisonChecks {
	public static void main(String[] args) {
		System.out.println(42 == 42);
		System.out.println("abc".equals("abc"));
	}
}
```

จะได้ผลลัพธ์เป็น

```
true
true
```

## ตัวดำเนินการ =\~, !\~

```ruby
puts /hay/ =~ 'haystack'
puts 'haystack' =~ /hay/
puts /hay/ !~ 'haystack'
puts 'haystack' !~ /hay/
```

จะได้ผลลัพธ์เป็น

```
0
0
false
false
```

#### เทียบกับภาษาอื่น ๆ&#x20;

> C

ภาษา C ไม่มีตัวดำเนินการของ `regex` โดยเฉพาะ จึงต้องนำเข้า `library` `regex` มาใช้งานแทน

```c
#include <stdio.h>
#include <regex.h>

int regex_index(const char* text, const char* pattern) {
	regex_t regex;
        regmatch_t pmatch;
	if (regcomp(&regex, pattern, 0)) {
		fprintf(stderr, "Could not compile regex\n");
		return -1;
	}

	// ทำ regex
        int status = regexec(&regex, text, 1, &pmatch, 0);

        if (status == 0) {
		regfree(&regex);
		return pmatch.rm_so;
        } else if (status == REG_NOMATCH) {
		regfree(&regex);
		return -1;
	} else {
		char msgbuf[100];
		regerror(status, &regex, msgbuf, sizeof(msgbuf));
		fprintf(stderr, "Regex match failed: %s\n", msgbuf);
		regfree(&regex);
	}
}

int regex_find(const char* text, const char* pattern) {
	regex_t regex;
	int reti;

	reti = regcomp(&regex, pattern, 0);
	if (reti) {
		fprintf(stderr, "Could not compile regex\n");
		return -1;
	}

        reti = regexec(&regex, text, 0, NULL, 0);

        regfree(&regex);
	
	if (reti == REG_NOMATCH) {
		return 0;
	} else {
		return 1;
	}
}


int main() {
	const char* text = "haystack";
	const char* pattern = "hay";
        int found_idx = regex_index(text, pattern);
        int is_found = regex_find(text, pattern);
        printf("%d\n", found_idx);
	printf("%d\n", is_found);
	return 0;
}
```

จะได้ผลลัพธ์เป็น

```
0
1
```

> Python

ภาษา Python ไม่มีตัวดำเนินการของ `regex` โดยเฉพาะ จึงต้องนำเข้า `re` มาเพื่อใช้งานแทน

```python
import re

text = 'haystack'
pattern = 'hay'

match = re.search(pattern, text)
if match:
    print(match.start())
else:
    print(None)

print(re.search(pattern, text) is None)
```

จะได้ผลลัพธ์เป็น

```
0
False
```

> Java

ภาษา Java ไม่มีตัวดำเนินการของ `regex` โดยเฉพาะ จึงต้องนำเข้า `Class` `Pattern` ของ `regex` มาเพื่อใช้งานแทน

```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class RegexMatch {
	public static void main(String[] args) {
		String text = "haystack";
		String regex = "hay";
		Pattern pattern = Pattern.compile(regex);
		Matcher matcher = pattern.matcher(text);

		matcher.reset();
		if (matcher.find()) {
			System.out.println(matcher.start());
		} else {
			System.out.println("-1");
		}
		
		matcher.reset();
		System.out.println(!matcher.find());
	}
}
```

จะได้ผลลัพธ์เป็น

```
0
false
```
## Slice

https://silpakorn-my.sharepoint.com/:p:/g/personal/saree_w_su_ac_th/ESzi6TJr1txMoLshdGb_j3IBRGFOsTfFsD_tGc36Ex1O8g?e=21RHtj

https://silpakorn-my.sharepoint.com/:b:/g/personal/saree_w_su_ac_th/EUROGGwAwdBLhqbw5zrFKjgB7ukC1pm8heOtvr6I-1jYBA?e=XKSo0g

## Video

https://youtu.be/P8zcpdT9MmI

## &#x20;แหล่งอ้างอิง

### &#x20;Ruby

#### ตัวดำเนินการแบบต่าง ๆ, การใช้ตัวดำเนินการ

Techotopia. (2016, October 27). _Ruby Operators._ [https://www.techotopia.com/index.php/Ruby\_Operators](https://www.techotopia.com/index.php/Ruby_Operators)

Flanagan, D., & Matsumoto, Y. (2008). _The Ruby programming language_. O'Reilly Media.

GeeksforGeeks. (2024, April 23). _Ruby | Operators_. [https://www.geeksforgeeks.org/ruby/ruby-operators/](https://www.geeksforgeeks.org/ruby/ruby-operators/)

#### การเปรียบเทียบวัตถุ

Castello, J. (2017, March). _How Ruby equality works_. RubyGuides. [https://www.rubyguides.com/2017/03/ruby-equality/](https://www.rubyguides.com/2017/03/ruby-equality/)

#### class ลูกของ Numeric

Ruby Association. _Numeric_. (n.d.). [https://ruby-doc.org/core-2.5.2/Numeric.html](https://ruby-doc.org/core-2.5.2/Numeric.html)

#### การเปรียบเทียบ String โดยใช้ >,>=,<,<=

Andrew. (2014, February 7). _Comparing two strings using > (greater than sign) in Ruby?_ \[Online forum post]. Stack Overflow. [https://stackoverflow.com/questions/21618216/comparing-two-strings-using-greater-than-sign-in-ruby](https://stackoverflow.com/questions/21618216/comparing-two-strings-using-greater-than-sign-in-ruby)

#### Regexp, การใช้ =\~, !\~

Ruby Association. _Regexp._ (n.d.). [https://ruby-doc.org/core-2.5.7/Regexp.html](https://ruby-doc.org/core-2.5.7/Regexp.html)

### C

#### ลักษณะค่าตรรกะ

Bell, J. (n.d.). _Decisions_. University of Illinois Chicago, Department of Computer Science. [https://www.cs.uic.edu/\~jbell/CourseNotes/C\_Programming/Decisions.html](https://www.cs.uic.edu/~jbell/CourseNotes/C_Programming/Decisions.html)

#### Regexp

GeeksforGeeks. (2025, July 12). _Regular expressions in C._ [https://www.geeksforgeeks.org/c/regular-expressions-in-c/](https://www.geeksforgeeks.org/c/regular-expressions-in-c/)

The Open Group. (1997). _regex.h - regular-expression-matching types_. [https://pubs.opengroup.org/onlinepubs/7908799/xsh/regex.h.html](https://pubs.opengroup.org/onlinepubs/7908799/xsh/regex.h.html)

### Python

**การเปรียบเทียบวัตถุ**

McCullum, N. (2020, August 6). _How to compare objects in Python_. [https://www.nickmccullum.com/how-to-compare-objects-python/](https://www.nickmccullum.com/how-to-compare-objects-python/)

#### การเปรียบเทียบ class, การใช้ is, is not

Langen, J. de. (n.d.). _Python != is not is not: Comparing objects in Python_. Real Python. [https://realpython.com/python-is-identity-vs-equality/](https://realpython.com/python-is-identity-vs-equality/)

#### subclass

Python Software Foundation. (n.d.). _Classes_. [https://docs.python.org/3/tutorial/classes.html](https://docs.python.org/3/tutorial/classes.html)

### Java

#### วิธีการใช้ method isAssignableFrom

Oracle. (n.d.). _Class._ [https://docs.oracle.com/javase/8/docs/api/java/lang/Class.html](https://docs.oracle.com/javase/8/docs/api/java/lang/Class.html)

#### การตรวจตอบว่า Object เป็นของ Class ไหน โดยไม่ใช้ instanceof

Addev. (2013, May 22). _Check if an object is an instance of a class (but not an instance of its subclass)_. \[Online forum post]. Stack Overflow. [https://stackoverflow.com/questions/16688655/check-if-an-object-is-an-instance-of-a-class-but-not-an-instance-of-its-subclas](https://stackoverflow.com/questions/16688655/check-if-an-object-is-an-instance-of-a-class-but-not-an-instance-of-its-subclas)

