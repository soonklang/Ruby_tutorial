# เเบบฝึกหัด เรี่อง Ruby String Conversions
### 1
```ruby

```
### 2
```ruby

```
### 3. กำหนดตัวแปร String width = "12.5" และ String height = "3.2" ให้เขียนโปรแกรมแปลงค่าเป็น Float แล้วคำนวณพื้นที่ จากนั้นพิมพ์ผลลัพธ์
<details close>
   <summary><b>ภาษา Ruby</b></summary>
    
```ruby
width = "12.5"
height = "3.2"

puts "Area = #{width.to_f * height.to_f}"

 ```
Output
```ruby

Area = 40.0

 ```
        
</details>

<details close>
   <summary><b>ภาษา Java</b></summary>
    
```java
    public class Main {
    public static void main(String[] args) {
        String width = "12.5";
        String height = "3.2";

        System.out.println("Area = " + (Double.parseDouble(width) * Double.parseDouble(height)));
    }
}

 ```
Output
```java

Area = 40.0

 ```
        
</details>

<details close>
   <summary><b>ภาษา C</b></summary>
    
```C
   #include <stdio.h>
#include <stdlib.h>

int main() {
    char width[] = "12.5";
    char height[] = "3.2";

    printf("Area = %.1f\n", atof(width) * atof(height));
    return 0;
}

 ```
Output
```C

Area = 40.0

 ```
        
</details>

<details close>
   <summary><b>ภาษา Python</b></summary>
    
```python
width = "12.5"
height = "3.2"

print("Area =", float(width) * float(height))

 ```
Output
```python

Area = 40.0

 ```
        
</details>


