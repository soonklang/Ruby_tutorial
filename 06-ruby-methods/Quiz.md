# Quiz ประจำบท 


## 1) สร้างเมธอดชื่อ factorial ที่รับค่าจำนวนเต็ม n และ return ค่าแฟกทอเรียล (n!) 
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


## Passing a Variable Number of Argument 


## Passing Argument to a Method


## Return a Value from a Function


## Method Aliases
