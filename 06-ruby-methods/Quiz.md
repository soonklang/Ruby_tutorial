# Quiz ประจำบท 


## 1) สร้างเมธอดชื่อ factorial ที่รับค่าจำนวนเต็ม n และ return ค่าแฟกทอเรียล (n!) 
#### เฉลย
#### Ruby
```ruby
# Declaring
def factorial(n)
  return 1 if n == 0
  result = 1
  (1..n).each { |i| result *= i }
  result
end

# Calling
puts factorial(5)
```

#### C
```c
#include <stdio.h>

// Declaring
long factorial(int n) {
    if (n == 0) return 1;
    long result = 1;
    for (int i = 1; i <= n; i++) {
        result *= i;
    }
    return result;
}

int main() {
    // Calling
    printf("%ld\n", factorial(5));
    return 0;
}
```

#### Java
```java
public class Main {
    // Declaring
    static long factorial(int n) {
        if (n == 0) return 1;
        long result = 1;
        for (int i = 1; i <= n; i++) {
            result *= i;
        }
        return result;
    }

    public static void main(String[] args) {
        // Calling
        System.out.println(factorial(5));
    }
}
```

#### Python
```python
# Declaring
def factorial(n):
    if n == 0:
        return 1
    result = 1
    for i in range(1, n+1):
        result *= i
    return result

# Calling
print(factorial(5))
```



## 2) ให้เขียนโปรแกรมใช้ Lambda (หรือ Anonymous Function) เพื่อคัดกรอง รายชื่อคนที่อายุมากกว่า 20 ปี จากลิสต์ที่เก็บเป็น (ชื่อ, อายุ) แล้วคืนผลลัพธ์เฉพาะชื่อคนที่ผ่านเงื่อนไข
#### เฉลย
#### Ruby
``` ruby
people = [["Alice", 19], ["Bob", 21], ["Charlie", 23]]
adults = people.select { |p| p[1] > 20 }.map(&:first)
puts adults.inspect
```

#### C
``` c
#include <stdio.h>

int main() {
    char *names[] = {"Alice", "Bob", "Charlie"};
    int ages[] = {19, 21, 23};
    for(int i=0; i<3; i++) {
        if(ages[i] > 20) printf("%s ", names[i]);
    }
    return 0;
}
```

#### Java
``` java
import java.util.*;
import java.util.stream.*;

public class Main {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice","Bob","Charlie");
        List<Integer> ages = Arrays.asList(19,21,23);

        List<String> adults = IntStream.range(0, names.size())
            .filter(i -> ages.get(i) > 20)
            .mapToObj(names::get)
            .toList();

        System.out.println(adults);
    }
}
```

#### Python
``` python
people = [("Alice",19), ("Bob",21), ("Charlie",23)]
adults = list(filter(lambda p: p[1] > 20, people))
print([name for name,age in adults])
```



## 3) ให้เขียนฟังก์ชัน statistics(*numbers) ที่รับจำนวนอาร์กิวเมนต์ไม่จำกัด และคืนค่าเป็น
#### เฉลย
#### Ruby
``` ruby
def statistics(*nums)
  sum = nums.sum
  avg = sum.to_f / nums.size
  return sum, avg, nums.max, nums.min
end

puts statistics(3,7,2,9)
```

#### C
``` c
#include <stdio.h>
#include <stdarg.h>

void statistics(int count, ...) {
    va_list args;
    va_start(args,count);
    int sum=0, max=-9999, min=9999;
    for(int i=0;i<count;i++){
        int x = va_arg(args,int);
        sum+=x;
        if(x>max) max=x;
        if(x<min) min=x;
    }
    va_end(args);
    printf("sum=%d avg=%.2f max=%d min=%d\n", sum, (double)sum/count, max, min);
}

int main() {
    statistics(4,3,7,2,9);
}
}
```

#### Java
``` java
public class Main {
    static void statistics(int... nums) {
        int sum=0, max=nums[0], min=nums[0];
        for(int n:nums){
            sum+=n;
            if(n>max) max=n;
            if(n<min) min=n;
        }
        double avg=(double)sum/nums.length;
        System.out.printf("sum=%d avg=%.2f max=%d min=%d\n", sum, avg, max, min);
    }

    public static void main(String[] args) {
        statistics(3,7,2,9);
    }
}
```

#### Python
``` python
def statistics(*nums):
    return sum(nums), sum(nums)/len(nums), max(nums), min(nums)

print(statistics(3,7,2,9))
```


## 4) เขียนฟังก์ชัน matrix_multiply(A, B) ที่รับเมทริกซ์ 2 ตัว (ในรูปแบบ 2D array/list) แล้วคืนค่าเป็นผลคูณของเมทริกซ์ (Matrix Multiplication) *ถ้าไม่สามารถคูณกันได้ ให้ return ค่าว่างหรือ error*
#### เฉลย
#### Ruby
``` ruby
def matrix_multiply(a,b)
  rows, cols = a.size, b[0].size
  result = Array.new(rows) { Array.new(cols,0) }
  rows.times do |i|
    cols.times do |j|
      b.size.times do |k|
        result[i][j] += a[i][k]*b[k][j]
      end
    end
  end
  result
end

A=[[1,2,3],[4,5,6]]
B=[[7,8],[9,10],[11,12]]
puts matrix_multiply(A,B).inspect
```

#### C
``` c
#include <stdio.h>

int main() {
    int A[2][3]={{1,2,3},{4,5,6}};
    int B[3][2]={{7,8},{9,10},{11,12}};
    int C[2][2]={{0,0},{0,0}};

    for(int i=0;i<2;i++){
        for(int j=0;j<2;j++){
            for(int k=0;k<3;k++){
                C[i][j]+=A[i][k]*B[k][j];
            }
        }
    }
    for(int i=0;i<2;i++){
        for(int j=0;j<2;j++) printf("%d ",C[i][j]);
        printf("\n");
    }
}
```

#### Java
``` java
public class Main {
    static int[][] multiply(int[][] A,int[][] B){
        int[][] C=new int[A.length][B[0].length];
        for(int i=0;i<A.length;i++){
            for(int j=0;j<B[0].length;j++){
                for(int k=0;k<B.length;k++){
                    C[i][j]+=A[i][k]*B[k][j];
                }
            }
        }
        return C;
    }

    public static void main(String[] args){
        int[][] A={{1,2,3},{4,5,6}};
        int[][] B={{7,8},{9,10},{11,12}};
        int[][] C=multiply(A,B);
        for(int[] row:C){
            for(int x:row) System.out.print(x+" ");
            System.out.println();
        }
    }
}
```

#### Python
``` python
def matrix_multiply(A,B):
    result=[[0]*len(B[0]) for _ in range(len(A))]
    for i in range(len(A)):
        for j in range(len(B[0])):
            for k in range(len(B)):
                result[i][j]+=A[i][k]*B[k][j]
    return result

A=[[1,2,3],[4,5,6]]
B=[[7,8],[9,10],[11,12]]
print(matrix_multiply(A,B))
```


## 5) เขียนฟังก์ชัน fibonacci(n) ที่ return ลำดับ Fibonacci ลำดับที่ n โดยใช้การเขียนแบบ recursive และทำให้โปรแกรมรองรับค่า n ที่มาก (เช่น n=40+) ได้ด้วย (แนะนำให้ใช้ memoization / dynamic programming)
#### เฉลย
#### Ruby
``` ruby
def fib(n)
  return n if n<2
  fib(n-1)+fib(n-2)
end

puts fib(10)
```

#### C
``` c
#include <stdio.h>

int fib(int n){
    if(n<2) return n;
    return fib(n-1)+fib(n-2);
}

int main(){
    printf("%d\n", fib(10));
}
```

#### Java
``` java
public class Main {
    static int fib(int n){
        if(n<2) return n;
        return fib(n-1)+fib(n-2);
    }
    public static void main(String[] args){
        System.out.println(fib(10));
    }
}
```

#### Python
``` python
def fib(n):
    if n<2: return n
    return fib(n-1)+fib(n-2)

print(fib(10))
```


## 6) ใน Ruby ให้สร้างเมธอด factorial(n) ที่หาค่าแฟกทอเรียลของ n แล้วสร้าง alias ชื่อ fact เพื่อให้เรียกแทนกันได้
จากนั้นเขียนโปรแกรมทดสอบว่า
	•	ใช้ factorial หาค่า 5!
	•	ใช้ fact หาค่า 7!
 #### เฉลย
#### Ruby
``` ruby
def factorial(n)
  return 1 if n<=1
  n*factorial(n-1)
end

alias fact factorial

puts factorial(5)
puts fact(7)
```

#### C
``` c
#include <stdio.h>

int factorial(int n){
    return (n<=1)?1:n*factorial(n-1);
}

#define fact factorial

int main(){
    printf("%d\n", factorial(5));
    printf("%d\n", fact(7));
}
```

#### Java
``` java
public class Main {
    static int factorial(int n){
        return (n<=1)?1:n*factorial(n-1);
    }
    static int fact(int n){ return factorial(n); }

    public static void main(String[] args){
        System.out.println(factorial(5));
        System.out.println(fact(7));
    }
}
```

#### Python
``` python
def factorial(n):
    return 1 if n<=1 else n*factorial(n-1)

fact=factorial

print(factorial(5))
print(fact(7))
```
