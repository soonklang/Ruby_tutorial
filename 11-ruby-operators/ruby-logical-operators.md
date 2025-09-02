# Ruby Logical Operators

>เป็นการเปรียบเทียบข้อมูลค่าความจริงเช่น true , false ไปใช้ในการทำงานของโปรแกรมในคำสั่ง if,while เป็นต้น

***Ruby Logical Operators***
 | Operator | Description | Example |
|----------|-------------|---------|
| `&&`     |  AND – คืนค่า `true` ก็ต่อเมื่อทั้งสองเงื่อนไขเป็นจริง | `(5 > 3) && (10 > 5)` → `true` |
| `||`     | OR – คืนค่า `true` ถ้าอย่างน้อยหนึ่งเงื่อนไขเป็นจริง | `(5 > 3) || (5 > 10)` → `true` |
| `!`      | NOT – สลับผลลัพธ์ | `!(5 > 3)` → `false` |
| `and`    |  AND แบบตัวอักษร (priority ต่ำกว่า `&&`) | `true and false` → `false` |
| `or`     |  OR แบบตัวอักษร (priority ต่ำกว่า `||`) | `false or true` → `true` |
| `not`    | NOT แบบตัวอักษร (priority ต่ำกว่า `!`) | `not true` → `false` |

***Java , C Logical Operators***

| Operator | Description | Example |
|----------|-------------|---------|
| `&&`     | AND – คืนค่า true ก็ต่อเมื่อทั้งสองเงื่อนไขเป็นจริง | `(5 > 3) && (10 > 5)` → `true` |
| `||`     | OR – คืนค่า true ถ้าอย่างน้อยหนึ่งเงื่อนไขเป็นจริง | `(5 > 3) || (5 > 10)` → `true` |
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


