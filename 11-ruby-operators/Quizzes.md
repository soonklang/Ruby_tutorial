# Operator Quizzes
## Comparison Operator
ให้รับตัวเลขมาหนึ่งตัว แล้วตรวจสอบว่าตัวเลขที่รับมานั้นมากกว่า 100 หรือไม่ ถ้ามากกว่า 100 ให้พิมพ์ "This number is so big!" ถ้าไม่ใช่ให้พิมพ์ "This number is smaller or equal 100"

### เฉลย

> Ruby

```ruby
number = gets.chomp.to_i

if number > 100
  puts "This number is so big!"
else
  puts "This number is smaller or equal 100"
end
```

> C

```c
#include <stdio.h>

int main() {
	int number;
        scanf("%d", &number);

        if (number > 100) {
		printf("This number is so big!");
	} else {
		printf("This number is smaller or equal 100");
        }
	
	return 0;
}
```

> Python

```python
number = int(input("input: "))

if number > 100:
    print("This number is so big!")
else:
    print("This number is smaller or equal 100")
```

> Java

```java
import java.util.Scanner;

public class main {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		
		int number = scanner.nextInt();

		if (number > 100) {
			System.out.println("This number is so big!");
		} else {
			System.out.println("This number is smaller or equal 100");
		}

		scanner.close();
	}
}
```

## Parallel Assignment
1.ในJavaสามารถประกาศให้lvalueตัวสุดท้ายมี "*" ค่าrvalueหลังจากนั้นเป็นarrayเหมือนRubyได้ไหม

	->ไม่สามารถทำได้ เพราะในJavaไม่มี splat operatorเหมือนในRuby

2.ถ้ามีlvalue 1 = rvalueหลายตัว ในC,Java,Python สามารถประกาศแบบนี้ได้เหมือนRubyไหม

	->ในภาษาC และJava ไม่สามารถทำได้ แต่ในPythonสามารถทำได้
>python
```python
a = 1,2,3,4
print(a) # a = [1,2,3,4]
```

## Assignment Operators
1. การดำเนินการกับตัวเลข (Numeric Operations)
โจทย์:
เขียนโปรแกรม Ruby เพื่อคำนวณและแสดงผลลัพธ์:
1.กำหนดค่าตัวแปร score ให้เท่ากับ 100
2.เพิ่มค่า score ขึ้นอีก 50 โดยใช้ Compound Assignment Operator
3.แสดงผลค่าสุดท้ายของ score

2. การดำเนินการกับสตริง (String Operations)
โจทย์:
เขียนโปรแกรม Ruby เพื่อต่อสตริงโดยใช้ Compound Assignment Operator:
1.กำหนดค่าตัวแปร message ให้มีค่าเริ่มต้นเป็น "Hello"
2.ต่อสตริง " World" เข้ากับ message
3.แสดงผลค่าสุดท้ายของ message

### เฉลย:

> Ruby

```ruby
score = 100
score += 50
puts "คะแนนสุดท้ายคือ: #{score}"
```

> Ruby

```ruby
message = "Hello"
message += " World"
puts message
```
