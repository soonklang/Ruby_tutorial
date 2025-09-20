# Quiz ประจำบท 


## 1) เขียนเมธอดชื่อ greet ที่รับชื่อ (string) เป็น argument แล้วพิมพ์ข้อความออกมา
#### Ruby
```ruby
def greet(name)
  puts "Hello, #{name}"
end

# เรียกใช้
greet("Dean")
```

#### C
```c
#include <stdio.h>

void greet(char name[]) {
    printf("Hello, %s\n", name);
}

int main() {
    greet("Dean");
    return 0;
}
```

```java
public class Main {
    // เมธอด
    static void greet(String name) {
        System.out.println("Hello, " + name);
    }

    public static void main(String[] args) {
        greet("Dean");
    }
}
```

```python
def greet(name):
    print(f"Hello, {name}")

# เรียกใช้
greet("Dean")
```



## Lambdas


## Passing a Variable Number of Argument 


## Passing Argument to a Method


## Return a Value from a Function


## Method Aliases
