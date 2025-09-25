# Ruby Logical Operators
>เป็นการเปรียบเทียบข้อมูลค่าความจริงเช่น true , false ไปใช้ในการทำงานของโปรแกรมในคำสั่ง if,while เป็นต้น

***Ruby Logical Operators***
 | Operator | Description | Example |
|----------|-------------|---------|
| `&&`     |  AND – คืนค่า `true` ก็ต่อเมื่อทั้งสองเงื่อนไขเป็นจริง | `(5 > 3) && (10 > 5)` → `true` |
| `\|\|`     | OR – คืนค่า `true` ถ้าอย่างน้อยหนึ่งเงื่อนไขเป็นจริง | `(5 > 3) \|\| (5 > 10)` → `true` |
| `!`      | NOT – สลับผลลัพธ์ | `!(5 > 3)` → `false` |
| `and`    |  AND แบบตัวอักษร (priority ต่ำกว่า `&&`) | `true and false` → `false` |
| `or`     |  OR แบบตัวอักษร (priority ต่ำกว่า `\|\|`) | `false or true` → `true` |
| `not`    | NOT แบบตัวอักษร (priority ต่ำกว่า `!`) | `not true` → `false` |

***Java , C Logical Operators***

| Operator | Description | Example |
|----------|-------------|---------|
| `&&`     | AND – คืนค่า true ก็ต่อเมื่อทั้งสองเงื่อนไขเป็นจริง | `(5 > 3) && (10 > 5)` → `true` |
| `\|\|`    | OR – คืนค่า true ถ้าอย่างน้อยหนึ่งเงื่อนไขเป็นจริง | `(5 > 3) \|\| (5 > 10)` → `true` |
| `!`      | NOT – สลับผลลัพธ์ | `!(5 > 3)` → `false` |

 ***Python Logical Operators***

| Operator | Description | Example |
|----------|-------------|---------|
| `and`    | AND – คืนค่า True ก็ต่อเมื่อทั้งสองเงื่อนไขเป็นจริง | `(5 > 3) and (10 > 5)` → `True` |
| `or`     | OR – คืนค่า True ถ้าอย่างน้อยหนึ่งเงื่อนไขเป็นจริง | `(5 > 3) or (5 > 10)` → `True` |
| `not`    | NOT – สลับผลลัพธ์ | `not (5 > 3)` → `False` |

## ตัวอย่างการใช้งาน AND 
	
***ภาษา Ruby***

	var1 = 20 
	var2 = 60 
	var1 < 25 and var2 > 45  
	=> true

***ภาษา Java***

	public class Main {
    public static void main(String[] args) {
        int var1 = 20;
        int var2 = 60;

        boolean result = (var1 < 25) && (var2 > 45);
        System.out.println(result); // true
   		 }
	}


***ภาษา C***

	#include <stdio.h>
	#include <stdbool.h>

	int main() {
	    int var1 = 20;
	    int var2 = 60;

	    bool result = (var1 < 25) && (var2 > 45);
	    printf("%s\n", result ? "true" : "false"); // true

	    return 0;
	}
 
***ภาษา Python***

	var1 = 20
	var2 = 60
	result = (var1 < 25) and (var2 > 45)
	print(result)  # True


## ตัวอย่างการใช้งาน OR
***ภาษา Ruby***

	var1 = 20  
	var2 = 60
	var1 < 25 or var2 > 45  
	=> true

***ภาษา Java***

	
	public class Main {
	    public static void main(String[] args) {
	        int var1 = 20;
	        int var2 = 60;

	        boolean result = (var1 < 25) || (var2 > 45);
	        System.out.println(result); // true
	    }
	}


***ภาษา C***

	#include <stdio.h>
	#include <stdbool.h>

	int main() {
	    int var1 = 20;
	    int var2 = 60;

	    bool result = (var1 < 25) || (var2 > 45);
	    printf("%s\n", result ? "true" : "false"); // true

	    return 0;
	}
***ภาษา Python***
	
	var1 = 20
	var2 = 60

	result = (var1 < 25) or (var2 > 45)
	print(result)  # True

## ตัวอย่างการใช้งาน NOT

***ภาษา Ruby***

	var1 = 20  
	var2 = 60
	!(var1 < 25 and var2 > 45)  
	=> false

***ภาษา Java***

	public class Main {
	    public static void main(String[] args) {
	        int var1 = 20;
	        int var2 = 60;

	        boolean result = !((var1 < 25) && (var2 > 45));
	        System.out.println(result); // false
	    }
	}

***ภาษา C***

	#include <stdio.h>
	#include <stdbool.h>

	int main() {
	    int var1 = 20;
	    int var2 = 60;

	    bool result = !((var1 < 25) && (var2 > 45));
	    printf("%s\n", result ? "true" : "false"); // false

	    return 0;
	}

***ภาษา Python***

	var1 = 20
	var2 = 60

	result = not (var1 < 25 and var2 > 45)
	print(result)  # False




# Truthiness (Ruby / Python / Java / C)

| ภาษา       | ค่าที่ถือว่า **False** | ค่าที่ถือว่า **True** |
|------------|--------------------------|-------------------------|
| **Ruby**  | `false`, `nil` | ค่าอื่นทั้งหมด เช่น `0`, `""` สตริง, `[]` อาเรย์, อ็อบเจกต์ต่าง ๆ |
| **Python**| `False`, `None`, `0`, `0.0`, `0j`, `Decimal(0)`, `Fraction(0)`, `""` (สตริงว่าง), `[]`, `{}`, `set()`, `range(0)` | ค่าอื่นทั้งหมด |
| **Java**  |  `false` ต้องเป็นชนิด `boolean` เท่านั้น  | `true` ต้องเป็นชนิด `boolean` เท่านั้น<br> ถ้าเป็นตัวเลขหรืออ็อบเจกต์ ใช้ตรง ๆ ไม่ได้ ต้องเปรียบเทียบ เช่น `x != 0` |
| **C**     | `0` | ทุกค่าที่ไม่ใช่ศูนย์  |

# Short-circuit behavior

>ทุกภาษาในตารางนี้รองรับ short-circuit evaluation คือถ้ารู้ผลจาก operand แรกแล้วไม่ต้องสนใจ operand ที่เหลือ
เช่น `
A && B` ถ้า `A` เป็น **false** ก็ไม่ต้องเช็ค `B` เพราะผลรวมจะเป็น false แน่นอน  
หรือ `A || B` ถ้า `A` เป็น **true** ก็ไม่ต้องเช็ค `B`

# Logical Expressions return (Ruby / Python / Java / C)
>แต่ละภาษามีค่า return  ไม่เหมือนกัน ขึ้นกับ **แนวคิดของภาษา**

| ภาษา   | Expression               | ผลลัพธ์ที่คืนกลับ | คำอธิบาย |
|--------|--------------------------|-----------------|--------------------------------------------------------|
| Ruby   | `true && "Hello"`        | `"Hello"`       | คืน operand สุดท้ายที่เป็น truthy |
| Ruby   | `false || "Hi"`          | `"Hi"`          | short-circuit แล้วคืนค่า operand ที่ truthy |
| Python | `True and "Hello"`       | `"Hello"`       | คืน operand สุดท้าย (truthy) |
| Python | `False or "Hi"`          | `"Hi"`          | short-circuit แล้วคืนค่า truthy |
| Java   | `true && false`          | `false`         | คืน boolean เสมอ ไม่มีการคืนค่า operand |
| Java   | `true || false`          | `true`          | คืน boolean |
| C      | `1 && 0`                 | `0`             | คืนค่าเป็น int (`0` = false, non-zero = true) |
| C      | `0 || 42`                | `1`             | non-zero  นับเป็น true → คืน 1 |

### สรุป
 **เปรียบเทียบระหว่าง 4 ภาษานี้**
 >จะเห็นได้ว่า  Ruby ออกแบบ Logical operator มาให้ใช้ได้ทั้งแบบ symbolic และ keyword ซึ่งทำให้มีความหลากหลายในการเลือกใช้
>จะแตกต่างจาก Java/C ที่ภาษาออกแบบมาให้ใช้ได้แค่ symbolic เพื่อเน้นให้ สั้น กระชับ และเช่นเดียวกับกันกับ Python ที่ออกแบบมาให้ใช้แค่ keyword เพื่อความสะดวกในการอ่าน


อ้างอิง
>https://www.techotopia.com/index.php/Understanding_Ruby_Logical_Operators
>
>https://www.geeksforgeeks.org/java/java-logical-operators-with-examples/
>
>https://www.geeksforgeeks.org/c/logical-operators-in-c/
>
>https://www.w3schools.com/python/gloss_python_logical_operators.asp
>
>https://andycroll.com/ruby/truthiness-in-conditionals/
>
>https://stackoverflow.com/questions/23068834/what-evaluates-to-false-in-ruby
