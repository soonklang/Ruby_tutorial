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



## Lambdas
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
people = [("Alice", 19), ("Bob", 21), ("Charlie", 23)]
adults = list(map(lambda p: p[0], filter(lambda p: p[1] > 20, people)))
print(adults)
```


## Passing a Variable Number of Argument 


## Passing Argument to a Method


## Return a Value from a Function


## Method Aliases
