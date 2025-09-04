---
description: local variable
---

# Ruby local variable

&#x20;     ruby local variable  ใช้งานได้เฉพาะภายในโครงสร้างของโค้ดที่มันถูกประกาศไว้ได้เท่านั้น เช่น ตัวแปรที่ประกาศไว้ในเมธอดหรือภายในลูป จะไม่สามารถเรียกใช้งานนอกเมธอดหรือลูปได้   ชื่อตัวแปรแบบ local จะต้องขึ้นต้นด้วยขีดล่าง \_ หรืออักษรตัวเล็กเท่านั้น &#x20;

**การตั้งชื่อ**

Ruby   สามารถใช้ได้ ทั้ง lower case/\_  ในการตั้งชื่อ

C       \_ ใช้ได้เเต่ระวังชนกับ compiler

Java    \_ ใช้ได้ เเต่ไม่เเนะนำ ตาม name conventions

Python   \_ใช้ได้ เเต่บางครั้งมักหมายถึง internal

&#x20;        **ตัวอย่าง**

```
def pl
    name = "kanawad"
    _lastname = "choobanna"
    puts "#{name}, #{_lastname}"
end
```

&#x20;**ruby**&#x20;

ประกาศเมธอด pl

name,\_lastname → local variable&#x20;

puts คือคำสั่งพิมพ์ จะได้ว่า kanawad, choobanna

end คือ การจบคำสั่ง

```
def pl():
    _kanawad = 10
    kanawad = 10
    print(_kanawad, kanawad)

​
```

&#x20;**python**&#x20;

def pl(): ประกาศ ฟังก์ชัน

\_kanawad เเละ kanawad เป็น local variable ที่ใช้ได้ภายในฟังก์ชัน

print คือคำสั่งพิมพ์ 10, 10

```
#include <stdio.h>

int main() {
    int kanawad = 100;     
    int _kanawad = 100;       
    printf("%d %d\n", kanawad, _kanawad);
    return 0;
}
```

&#x20;**c**&#x20;

ประกาศ main&#x20;

kanawad เเละ \_kanawad เป็น local variable&#x20;

printf ประกาศพิมพ์ จะได้ว่า 100 , 100

return 0 คือการส่งค่า 0  กลับไป เพื่อบอกว่าทำงานเสร็จเเล้ว ไม่มี error

<pre><code>public class Main {
    public static void main(String[] args) {
    int kanawad = 20;
    int _kanawad = 20;
    System.out.println(kanawad + " " + _kanawad);
<strong>    }
</strong>}
</code></pre>

&#x20;**java**  &#x20;

public static void main(String\[] args) ประกาศ เมธอด

kanawad   เเละ  \_kanawad  → local variable&#x20;

System.out.println() จะได้ว่า 20 20



**ดังนั้น** local variable นั้น คือ ตัวเเปรที่ในฟังก์ชัน หรือเมธอด ไม่สามารถ ใช้ได้นอกฟังก์ชัน หรือเมธอด ที่ประกาศไว้ได้





**การนำเสนอ**



​​**presentation**





​​

**เเหล่งอ้างอิง**

{% embed url="https://www.techotopia.com/index.php/Ruby_Essentials" %}

{% embed url="https://peps.python.org/pep-0008/" %}

{% embed url="https://stackoverflow.com/questions/3136594/naming-convention-underscore-in-c-and-c-sharp-variables" %}

{% embed url="https://www.oracle.com/java/technologies/javase/codeconventions-namingconventions.html" %}

{% embed url="https://www.w3schools.com/c/c_scope.php" %}

{% embed url="https://data-flair.training/blogs/variable-scope-in-c-local-vs-global/" %}
