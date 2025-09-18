# Quiz ประจำบท

##  1.จงเขียนโปรแกรมพิมชื่อตัวเอง (ใช้ String.new , ใช้ String(), และใช้ literal " " หรือ ' ' ) 



#### Ruby

```ruby
# ใช้ String.new
s1 = String.new("Steve Jobs")

# ใช้ String()
s2 = String("Steve Jobs")

# ใช้ literal
s3 = "Steve Jobs"
s4 = 'Steve Jobs'

puts s1
puts s2
puts s3
puts s4

```


#### Python

```python
# ใช้ str() 
s1 = str("Steve Jobs")

# ใช้ literal
s2 = "Steve Jobs"
s3 = 'Steve Jobs'

print(s1)
print(s2)
print(s3)

```


#### Java

```java
public class StringExample {
    public static void main(String[] args) {
        // ใช้ new String()
        String s1 = new String("Steve Jobs");

        // ใช้ literal
        String s2 = "Steve Jobs";

        // ใช้ String.valueOf()
        String s3 = String.valueOf("Steve Jobs");

        System.out.println(s1);
        System.out.println(s2);
        System.out.println(s3);
    }
}

```


#### C

```c
#include <stdio.h>

int main() {
    // แบบ literal
    char s1[] = "Steve Jobs";

    // แบบกำหนดเอง (array of char + null)
    char s2[] = {'S','t','e','v','e',' ','J','o','b','s','\0'};

    printf("%s\n", s1);
    printf("%s\n", s2);

    return 0;
}

```


