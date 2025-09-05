# Ruby Assignment Operators

## Ruby Assignment Operators คืออะไร ?

**Ruby Assignment Operators** คือชุดของสัญลักษณ์ที่ใช้สำหรับ กำหนดค่า ให้กับตัวแปรครับ โดยมีจุดประสงค์หลักคือทำให้การเขียนโค้ดสั้นลง เข้าใจง่ายขึ้น และมีประสิทธิภาพมากขึ้น

**เครื่องหมายการกำหนดค่าพื้นฐาน (`=`)** ซึ่งใช้เพื่อกำหนดค่าของนิพจน์ (expression) ให้กับตัวแปร เช่น `y = 10` ซึ่งหมายถึงการกำหนดค่า 10 ให้กับตัวแปร y&#x20;

อย่างไรก็ตาม เครื่องหมาย `=` จะไม่ได้ทำการเปลี่ยนแปลงค่าใดๆ ก่อนที่จะกำหนดให้ตัวแปร แต่ยังมีเครื่องหมายกำหนดค่าอีกหลายชนิดที่ทำหน้าที่ "**รวมการคำนวณทางคณิตศาสตร์และการกำหนดค่าเข้าไว้ด้วยกัน"** ทำให้สามารถคำนวณและกำหนดค่าใหม่ให้กับตัวแปรได้ในคำสั่งเดียว

เครื่องหมายเหล่านี้มักเรียกว่า **"เครื่องหมายการกำหนดค่าเชิงผสม" (combined arithmetic and assignment operators)** ซึ่งช่วยให้การเขียนโค้ดสั้นและมีประสิทธิภาพมากขึ้น

### ตัวดำเนินการเหล่านี้แบ่งออกเป็น 2 กลุ่มหลักๆ ได้แก่ :&#x20;

1. **Basic Assignment Operator (`=`):** ตัวดำเนินการพื้นฐานที่สุด ทำหน้าที่กำหนดค่าทางฝั่งขวาให้กับตัวแปรทางฝั่งซ้ายโดยตรง
2. **Compound Assignment Operators:** ตัวดำเนินการที่รวมการคำนวณทางคณิตศาสตร์เข้ากับการกำหนดค่า ช่วยให้ไม่ต้องเขียนโค้ดซ้ำซ้อน

#### \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### 1. Basic Assignment Operator (`=`)

นี่คือตัวดำเนินการที่เราคุ้นเคยกันดีที่สุด ทำหน้าที่กำหนดค่าที่อยู่ในนิพจน์ (expression) หรือค่าคงที่ (literal value) ให้กับตัวแปรที่อยู่ทางซ้ายมือ ในภาษา Ruby, การกำหนดค่าใช้เครื่องหมาย `=` (เครื่องหมายเท่ากับ) การกำหนดค่าจะสร้างตัวแปรโลคัลขึ้นมา หากตัวแปรนั้นไม่เคยถูกอ้างถึงมาก่อน และผลลัพธ์ของนิพจน์การกำหนดค่า (assignment expression) จะเป็นค่าที่ถูกกำหนดให้นั้นเสมอ

### **ตัวอย่าง:**

#### Ruby และ Python (Dynamic Typing)

ในภาษา Ruby และ Python ไม่จำเป็นต้องระบุชนิดของตัวแปร (เช่น `int`, `String`) อย่างชัดเจนตอนที่ประกาศตัวแปรครั้งแรก ภาษาจะอนุมานชนิดของข้อมูลให้เองโดยอัตโนมัติจากค่าที่ถูกกำหนดให้

<pre class="language-ruby" data-title="Ruby" data-overflow="wrap" data-line-numbers><code class="lang-ruby"><strong># Basic Assignmen
</strong><strong>name = "Ruby"
</strong><strong>age = 30
</strong><strong>price = 15.50
</strong></code></pre>

{% code title="Python" overflow="wrap" lineNumbers="true" %}
```python
# Basic Assignmen
name = "Python"
age = 35
price = 22.50
```
{% endcode %}

#### Java และ C (Static Typing)

ในภาษา Java และ C ต้อง ระบุชนิดของตัวแปรอย่างชัดเจน ก่อนที่จะใช้งานเสมอ และชนิดของตัวแปรจะไม่สามารถเปลี่ยนแปลงได้หลังจากที่ถูกกำหนดไปแล้ว

<pre class="language-c" data-title="C" data-overflow="wrap" data-line-numbers><code class="lang-c">#include &#x3C;stdio.h>
int main() {
<strong>    // Basic Assignment
</strong><strong>    char* name = "C Language";
</strong><strong>    int age = 40;
</strong><strong>    float price = 8.99;
</strong><strong>    return 0;
</strong><strong>}
</strong></code></pre>

{% code title="JAVA" overflow="wrap" lineNumbers="true" %}
```java
public class Main {
    public static void main(String[] args) {
        // Basic Assignment
        String name = "Java";
        int age = 25;
        double price = 12.75;
    }
}
```
{% endcode %}

ในตัวอย่างนี้, `name`, `age`, และ `price` คือตัวแปรที่ถูกกำหนดค่าด้วยเครื่องหมาย `=`

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### 2. Compound Assignment Operators

Compound Assignment Operators คือตัวดำเนินการที่ใช้สำหรับ ย่อโค้ด ให้สั้นลงและเข้าใจง่ายขึ้น โดยจะทำการคำนวณและกำหนดค่าใหม่ให้กับตัวแปรในขั้นตอนเดียวครับ ตัวดำเนินการเหล่านี้เป็นการรวมกันระหว่าง Arithmetic Operator (เช่น `+`, `-`, `*`) และ Assignment Operator (`=`)

ในภาษา Ruby มีตัวดำเนินการหลายประเภท แต่ในนี้ จะเน้นไปที่ Arithmetic Operators (ตัวดำเนินการทางคณิตศาสตร์) ซึ่งใช้สำหรับการคำนวณทางคณิตศาสตร์ครับ

#### Arithmetic Operators (ตัวดำเนินการทางคณิตศาสตร์)

* **`Simple Assignment (=)`:** เป็นตัวดำเนินการกำหนดค่าที่ง่ายที่สุด ใช้กำหนดค่าทางด้านขวาให้กับตัวแปรทางด้านซ้าย
* **`Add AND Assignment (+=)`:** ใช้สำหรับบวกตัวถูกดำเนินการทางซ้ายมือกับตัวถูกดำเนินการทางขวามือ แล้วกำหนดค่าให้กับตัวแปรทางซ้ายมือ
* **`Subtract AND Assignment (-=)`:** ใช้สำหรับลบตัวถูกดำเนินการทางขวามือออกจากตัวถูกดำเนินการทางซ้ายมือ แล้วกำหนดค่าให้กับตัวแปรทางซ้ายมือ
* **`Multiply AND Assignment (*=)`:** ใช้สำหรับคูณตัวถูกดำเนินการทางซ้ายมือกับตัวถูกดำเนินการทางขวามือ แล้วกำหนดค่าให้กับตัวแปรทางซ้ายมือ
* **`Divide AND Assignment (/=)`:** ใช้สำหรับหารตัวถูกดำเนินการทางซ้ายมือด้วยตัวถูกดำเนินการทางขวามือ แล้วกำหนดค่าให้กับตัวแปรทางซ้ายมือ
* **`Modulus AND Assignment (%=)`:** ใช้สำหรับหาค่าโมดูลัส (เศษจากการหาร) ของตัวถูกดำเนินการทางซ้ายมือด้วยตัวถูกดำเนินการทางขวามือ แล้วกำหนดค่าให้กับตัวแปรทางซ้ายมือ
* **`Exponent AND Assignment (**=)`:** ใช้สำหรับยกกำลังตัวถูกดำเนินการทางซ้ายมือด้วยตัวถูกดำเนินการทางขวามือ แล้วกำหนดค่าให้กับตัวแปรทางซ้ายมือ

#### ตัวอย่างในภาษา Ruby:

**`Simple Assignment (=)`:**

{% code title="Ruby" overflow="wrap" %}
```ruby
puts "Simple assignment operator" # แสดงข้อความบ่งบอกการทำงาน
a = 20                           # ใช้ Simple Assignment (=) กำหนดค่า 20 ให้กับตัวแปร a
puts a                           # แสดงค่าของ a ซึ่งก็คือ 20
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
Simple assignment operator
20
```
{% endcode %}

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**`Add AND Assignment (+=)`:**

{% code title="Ruby" overflow="wrap" %}
```ruby
puts "Add AND assignment operator" # แสดงข้อความ
a = 20
a += 10                          # ใช้ += เพื่อบวกค่า 10 เข้าไปใน a (a = a + 10)
                                 # ตอนนี้ a มีค่าเป็น 20 + 10 = 30
puts a                           # แสดงค่าของ a ซึ่งก็คือ 30
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
Add AND assignment operator
30
```
{% endcode %}

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**`Subtract AND Assignment (-=)`:**

{% code title="Ruby" overflow="wrap" %}
```ruby
puts "Subtract AND assignment operator" # แสดงข้อความ
a = 20
a -= 5                           # ใช้ -= เพื่อลบค่า 5 ออกจาก a (a = a - 5)
                                 # ตอนนี้ a มีค่าเป็น 20 - 5 = 15
puts a                           # แสดงค่าของ a ซึ่งก็คือ 15
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
Subtract AND assignment operator
15
```
{% endcode %}

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**`Multiply AND Assignment (*=)`:**

{% code title="Ruby" overflow="wrap" %}
```ruby
puts "Multiply AND assignment operator" # แสดงข้อความ
a = 25
a *= 10                          # ใช้ *= เพื่อคูณ a ด้วย 10 (a = a * 10)
                                 # ตอนนี้ a มีค่าเป็น 25 * 10 = 250
puts a                           # แสดงค่าของ a ซึ่งก็คือ 250
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
Multiply AND assignment operator
250
```
{% endcode %}

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**`Divide AND Assignment (/=)`:**

{% code title="Ruby" overflow="wrap" %}
```ruby
puts "Divide AND assignment operator" # แสดงข้อความ
a = 250
a /= 4    # ใช้ /= เพื่อหาร a ด้วย 4 (a = a / 4)
# ตอนนี้ a มีค่าเป็น 250 / 4 = 62.5 แต่เนื่องจาก a เป็นจำนวนเต็ม Ruby จะปัดทศนิยมทิ้งเหลือ 62
puts a    # แสดงค่าของ a ซึ่งก็คือ 62
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
Divide AND assignment operator
62
```
{% endcode %}

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**`Modulus AND Assignment (%=)`:**

{% code title="Ruby" overflow="wrap" %}
```ruby
puts "Modulus AND assignment operator" # แสดงข้อความ
a = 62
a %= 3   # ใช้ %= เพื่อหาเศษจากการหาร a ด้วย 3 (a = a % 3) 
# ตอนนี้ a มีค่าเป็น 62 % 3 = 2 (เพราะ 62 หาร 3 เหลือเศษ 2)
puts a  # แสดงค่าของ a ซึ่งก็คือ 2
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
Modulus AND assignment operator
2
```
{% endcode %}

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**`Exponent AND Assignment (**=)`:**

{% code title="Ruby" overflow="wrap" %}
```ruby
puts "Exponent AND assignment operator" # แสดงข้อความ
a = 2
a **= 3                          # ใช้ **= เพื่อยกกำลัง a ด้วย 3 (a = a ** 3)
                                 # ตอนนี้ a มีค่าเป็น 2 ** 3 = 8
puts a                           # แสดงค่าของ a ซึ่งก็คือ 8
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
Exponent AND assignment operator
8
```
{% endcode %}

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### 2.1 เปรียบเทียบ Compound Assignment Operators ของภาษา (Ruby & Python)

***

#### Ruby

Ruby ใช้ Compound Assignment Operators เพื่อย่อโค้ดที่ต้องมีการอัปเดตค่าของตัวแปร โดยจะทำการคำนวณและกำหนดค่าใหม่ในขั้นตอนเดียว

ตัวอย่าง:

{% code title="Ruby" overflow="wrap" %}
```ruby
x = 10
x += 5  # x = x + 5
puts x  # ผลลัพธ์: 15
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
15
```
{% endcode %}

ใน Ruby, ตัวดำเนินการเหล่านี้สามารถใช้ได้กับทั้งตัวเลขและสตริง ตัวอย่างเช่น `+=` ใช้สำหรับเชื่อมต่อสตริง

{% code title="Ruby" overflow="wrap" %}
```ruby
greeting = "Hello"
greeting += ", World!"
puts greeting # ผลลัพธ์: "Hello, World!"
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
Hello, World!
```
{% endcode %}

***

#### Python

Python มีการใช้ Compound Assignment Operators ในลักษณะเดียวกับ Ruby คือเพื่อลดความซ้ำซ้อนในการเขียนโค้ดและทำให้อ่านง่ายขึ้น

ตัวอย่าง:

{% code title="Python" overflow="wrap" %}
```python
x = 10
x += 5  # x = x + 5
print(x)  # ผลลัพธ์: 15
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
15
```
{% endcode %}

เช่นเดียวกับ Ruby, Python ก็ใช้ `+=` สำหรับการเชื่อมต่อสตริงเช่นกัน

{% code title="Python" overflow="wrap" %}
```python
greeting = "Hello"
greeting += ", World!"
print(greeting) # ผลลัพธ์: "Hello, World!"
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
Hello, World!
```
{% endcode %}

***

#### ข้อสรุปและความแตกต่าง

โดยรวมแล้ว การทำงานของ Compound Assignment Operators ใน Ruby และ Python แทบจะเหมือนกันทุกประการ ทั้งในเรื่องของไวยากรณ์ (syntax) และความสามารถในการทำงานกับชนิดข้อมูล (data types) ต่างๆ เช่น ตัวเลขและสตริง ความแตกต่างหลักจะอยู่ที่การจัดการประเภทข้อมูล (type system) และการใช้เครื่องหมายบางตัว

* Ruby: เป็นภาษาที่มีความยืดหยุ่นสูง โดย Operator บางตัวเป็นเพียงเมธอดที่สามารถ Overload ได้ ทำให้มีความสามารถในการปรับแต่งได้มากกว่า
* Python: มีการทำงานที่ชัดเจนและตรงไปตรงมา โดยตัวดำเนินการจะทำงานตามกฎที่กำหนดไว้สำหรับชนิดข้อมูลนั้นๆ

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### 2.2 เปรียบเทียบ Compound Assignment Operators ของภาษา (Ruby & C)

#### Ruby (Dynamic Typing)

Ruby เป็นภาษาแบบ Dynamic Typing ที่ยืดหยุ่นสูงมาก คุณไม่ต้องประกาศชนิดของตัวแปร (เช่น `int`, `float`) ล่วงหน้า เพราะ Ruby จะอนุมานชนิดข้อมูลให้เองโดยอัตโนมัติจากค่าที่ถูกกำหนดให้ นี่ทำให้การเขียนโค้ดสั้นและรวดเร็ว

{% code title="Ruby" overflow="wrap" %}
```ruby
# Ruby code
puts "--- Ruby Example ---"
# ไม่ต้องประกาศชนิดของตัวแปร
a = 10 

# ใช้ Compound Operator เพื่อคำนวณกับตัวเลข
a += 5  # a = a + 5 -> a มีค่าเป็น 15
puts "a += 5  : #{a}"

# สามารถใช้ Compound Operator กับ String ได้
text = "Hello"
text += " World" # ใช้ += เพื่อต่อสตริง
puts "text += ' World' : #{text}"
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
--- Ruby Example ---
a += 5  : 15
text += ' World' : Hello World
```
{% endcode %}

#### C (Static Typing)

C เป็นภาษาแบบ Static Typing ที่เข้มงวดกว่ามาก ต้องประกาศชนิดของตัวแปรอย่างชัดเจน ก่อนที่จะใช้งาน และชนิดของข้อมูลจะไม่สามารถเปลี่ยนแปลงได้หลังจากที่ถูกกำหนดไปแล้ว นี่ช่วยเพิ่มประสิทธิภาพและความปลอดภัยของโปรแกรม

{% code title="C" overflow="wrap" %}
```c
// C code
#include <stdio.h>

int main() {
    printf("--- C Example ---\n");
    // ต้องประกาศชนิดของตัวแปร
    int a = 10; 

    // ใช้ Compound Operator กับตัวเลข
    a += 5;  // a = a + 5 -> a มีค่าเป็น 15
    printf("a += 5  : %d\n", a);

    // C ไม่สามารถใช้ Compound Operator กับสตริงแบบนี้ได้
    // คุณต้องใช้ฟังก์ชันเฉพาะเช่น strcat() ในไลบรารี string.h
    // char text[50] = "Hello";
    // strcat(text, " World");
    
    return 0;
}
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
--- C Example ---
a += 5  : 15
```
{% endcode %}

#### ข้อสรุปและความแตกต่าง

โดยรวมแล้ว การทำงานของ Compound Assignment Operators ใน Ruby และ C มีแนวคิดหลักเหมือนกันคือการคำนวณและกำหนดค่าในคำสั่งเดียว แต่ความแตกต่างที่สำคัญที่สุดอยู่ที่ ระบบการจัดการประเภทข้อมูล (type system) ของแต่ละภาษา

* Ruby ใช้ระบบ Dynamic Typing ที่ยืดหยุ่นสูง ทำให้คุณไม่ต้องระบุชนิดตัวแปรและสามารถใช้ตัวดำเนินการอย่าง `+=` เพื่อคำนวณหรือต่อสตริงได้อย่างเป็นธรรมชาติ
* C ใช้ระบบ Static Typing ที่เข้มงวดกว่า ทำให้ต้องประกาศชนิดตัวแปรอย่างชัดเจน ซึ่งช่วยเพิ่มประสิทธิภาพและความปลอดภัยของโค้ด แต่ทำให้การใช้ `+=` เพื่อต่อสตริงทำได้ยาก ต้องใช้ฟังก์ชันจากไลบรารีเข้ามาช่วยแทน

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### 2.3 เปรียบเทียบ Compound Assignment Operators ของภาษา (Ruby & Java)

Ruby

Ruby เป็นภาษาแบบ Dynamic Typing ที่มีความยืดหยุ่นสูงมาก ทำให้คุณไม่ต้องระบุชนิดของตัวแปรอย่างชัดเจน โค้ดจึงสั้นและรวดเร็วในการพัฒนา นอกจากนี้ Ruby ยังอนุญาตให้มีการ Overload หรือนิยามการทำงานของ Operator ได้เอง ทำให้การใช้งานกับข้อมูลประเภทต่างๆ เช่น การใช้ `+=` เพื่อต่อสตริง ทำได้ง่ายดายและเป็นธรรมชาติ

#### Ruby(Dynamic Typing)

{% code title="Ruby" overflow="wrap" %}
```ruby
# Ruby code
puts "--- Ruby Example ---"
# ไม่ต้องประกาศชนิดของตัวแปร
a = 10 

# ใช้ Compound Operator เพื่อคำนวณกับตัวเลข
a += 5  # a = a + 5 -> a มีค่าเป็น 15
puts "a += 5  : #{a}"

# สามารถใช้ Compound Operator กับ String ได้
text = "Hello"
text += " World" # ใช้ += เพื่อต่อสตริง
puts "text += ' World' : #{text}"
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
--- Ruby Example ---
a += 5  : 15
text += ' World' : Hello World
```
{% endcode %}

#### Java(Static Typing)

Java เป็นภาษาแบบ Static Typing ที่เข้มงวด ต้องประกาศชนิดของตัวแปรทุกครั้งก่อนใช้งาน และชนิดข้อมูลจะไม่สามารถเปลี่ยนได้ โค้ดจึงมีความปลอดภัยสูงและมีประสิทธิภาพในการทำงานมากกว่า อย่างไรก็ตาม ความเข้มงวดนี้ทำให้การใช้งาน Operator กับชนิดข้อมูลที่ไม่เข้ากันทำได้ยาก เช่น การใช้ `+=` เพื่อต่อสตริง จะต้องใช้กับ `String` Class ที่รองรับการทำงานนี้อยู่แล้ว และจะทำงานแตกต่างจากการบวกตัวเลขทั่วไป

{% code title="Java" overflow="wrap" %}
```java
public class Main {
    public static void main(String[] args) {
      // ตัวอย่างใน Java
      
      System.out.println("--- Java Example ---");
      
      int x = 10;
      x += 5; // x = 15
      System.out.println("a += 5  : " + x);
        
      String text = "Hello";
      text += " World"; // ใช้ได้เพราะ String Class รองรับ
      System.out.println("text += ' World' : " + text);
    }
}
```
{% endcode %}

{% code title="Output" overflow="wrap" %}
```
--- Java Example ---
a += 5  : 15
text += ' World' : Hello World
```
{% endcode %}

#### ข้อสรุปและความแตกต่าง

แม้ว่าทั้งสองภาษาจะใช้ Compound Assignment Operators ในไวยากรณ์ที่คล้ายกัน แต่ความแตกต่างหลักคือ Ruby ใช้ระบบแบบ Dynamic Typing ที่ยืดหยุ่นและอนุญาตให้ Overload ได้ ทำให้ตัวดำเนินการทำงานกับชนิดข้อมูลที่หลากหลายได้อย่างเป็นธรรมชาติ ในขณะที่ Java ใช้ระบบแบบ Static Typing ที่เข้มงวด ซึ่งต้องระบุชนิดข้อมูลที่ชัดเจน และการทำงานของ Operator จะขึ้นอยู่กับข้อกำหนดของแต่ละคลาสครับ

* Ruby ใช้ Dynamic Typing ที่ยืดหยุ่นกว่า คุณจึงไม่ต้องระบุชนิดตัวแปรและสามารถใช้ตัวดำเนินการอย่าง `+=` เพื่อคำนวณหรือต่อสตริงได้อย่างเป็นธรรมชาติ
* Java ใช้ Static Typing ที่เข้มงวดกว่า ทำให้ต้องประกาศชนิดข้อมูลอย่างชัดเจน ซึ่งแม้จะช่วยเพิ่มความปลอดภัยและประสิทธิภาพ แต่การทำงานของ `+=` กับข้อมูลแต่ละชนิดจะขึ้นอยู่กับข้อกำหนดเฉพาะของคลาสนั้น ๆ

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### **แหล่งอ้างอิง :**

**หนังสือ**

* Matsumoto, Y., & Flanagan, D. (2008). The Ruby Programming Language. O'Reilly Media.

***

**เว็บไซต์ทางการและเอกสารอ้างอิงของภาษา**

* Mozilla. (ม.ป.ป.). Static typing. จาก [https://developer.mozilla.org/en-US/docs/Glossary/Static\_typing](https://developer.mozilla.org/en-US/docs/Glossary/Static_typing)
* Microsoft. (ม.ป.ป.). C Assignment Operators. จาก [https://learn.microsoft.com/en-us/cpp/c-language/c-assignment-operators?view=msvc-170](https://learn.microsoft.com/en-us/cpp/c-language/c-assignment-operators?view=msvc-170)
* Oracle. (ม.ป.ป.). The Java™ Tutorials. จาก [https://docs.oracle.com/javase/tutorial/](https://docs.oracle.com/javase/tutorial/)
* Python Software Foundation. (ม.ป.ป.). The Python Language Reference. จาก [https://docs.python.org/3/reference/index.html](https://docs.python.org/3/reference/index.html)
* Ruby Language. (ม.ป.ป.). Operators and Expressions. จาก [https://docs.ruby-lang.org/en/master/syntax/assignment\_rdoc.html](https://docs.ruby-lang.org/en/master/syntax/assignment_rdoc.html)
* cplusplus.com. (ม.ป.ป.). `<cstring>`. จาก [https://cplusplus.com/reference/cstring](https://cplusplus.com/reference/cstring)

***

**เว็บไซต์บทความและบทเรียน**

* GeeksforGeeks. (ม.ป.ป.). Assignment Operators. จาก [https://www.geeksforgeeks.org/ruby/ruby-operators](https://www.geeksforgeeks.org/ruby/ruby-operators)
* GeeksforGeeks. (ม.ป.ป.). Assignment Operators in Python. จาก [https://www.geeksforgeeks.org/python/assignment-operators-in-python](https://www.geeksforgeeks.org/python/assignment-operators-in-python)
* Techotopia. (2024). Ruby Assignment Operators. จาก [https://www.techotopia.com/index.php/Ruby\_Operators](https://www.techotopia.com/index.php/Ruby_Operators)
