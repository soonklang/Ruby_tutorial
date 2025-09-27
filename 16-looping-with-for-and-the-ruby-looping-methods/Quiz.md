# แบบฝึกหัด
##  Ruby for-loop

### จงคำนวณโดยให้เลขเริ่มต้น มีค่าเท่ากับ 100 เลขสิ้นสุดมีค่าเท่ากับ 1500 จงหาผลรวมของเลขคู่ ผลรวมเลขคี่ ผลรวมของเลขคู่บวกกับผลรวมเลขคี่ว่ามีค่าเท่าไรโดยจะต้องใช้ for loop และเขียนเป็นภาษา Ruby Python Java และ C

### เฉลย
<details close>
   <summary><b> Ruby</b></summary>
    
```ruby
start = 100
end_num = 1500
sum_even = 0
sum_odd = 0

for i in start..end_num
  if i % 2 == 0
    sum_even += i
  else
    sum_odd += i
  end
end

total = sum_even + sum_odd

puts "Sum of even = #{sum_even}"
puts "Sum of odd  = #{sum_odd}"
puts "Total sum   = #{total}"
 ```
        
</details>

<details close>
   <summary><b> Python</b></summary>
    
```python
start, end = 100, 1500
sum_even = 0
sum_odd = 0

for i in range(start, end+1):
    if i % 2 == 0:
        sum_even += i
    else:
        sum_odd += i

total = sum_even + sum_odd

print("Sum of even =", sum_even)
print("Sum of odd  =", sum_odd)
print("Total sum   =", total)
 ```
        
</details>

<details close>
   <summary><b> Java</b></summary>
    
```java
public class SumEvenOddTotal {
    public static void main(String[] args) {
        int start = 100;
        int end = 1500;

        int sumEven = 0, sumOdd = 0;
        for (int i = start; i <= end; i++) {
            if (i % 2 == 0) {
                sumEven += i;
            } else {
                sumOdd += i;
            }
        }
        int total = sumEven + sumOdd;

        System.out.println("Sum of even = " + sumEven);
        System.out.println("Sum of odd  = " + sumOdd);
        System.out.println("Total sum   = " + total);
    }
}
 ```
        
</details>

<details close>
   <summary><b> C</b></summary>
    
```c
#include <stdio.h>
int main() {
    int start = 100, end = 1500;
    int sumEven = 0, sumOdd = 0;

    for (int i = start; i <= end; i++) {
        if (i % 2 == 0) {
            sumEven += i;
        } else {
            sumOdd += i;
        }
    }

    int total = sumEven + sumOdd;

    printf("Sum of even = %d\n", sumEven);
    printf("Sum of odd  = %d\n", sumOdd);
    printf("Total sum   = %d\n", total);

    return 0;
}
 ```
</details> 


## Ruby Times Method

### จงใช้ times เพื่อพิมพ์เลขคู่ตั้งแต่ 2 ถึง 20 ทีละบรรทัด เป็นภาษา Ruby

### เฉลย
<details close>
   <summary><b> Ruby</b></summary>
    
```ruby
   10.times do |i|
     puts (i + 1) * 2
   enก
 ```
        
</details>

##  Ruby upto-and-downto-method
### เมธอด downto ใน ruby ไม่สามารถใช้งานได้บนคลาสใด
1. Integer
2. Date
3. String
4. ใช้งานได้หมดทุกคลาส
### เฉลย
<details close>
   <summary><b>เฉลย</b></summary>
 <pre>3. เพราะเมธอด downto สามารถใช้งานได้บนคลาส Integer และ Date แต่ไม่สามารถใช้กับ String ได้
 </pre>
</details>

