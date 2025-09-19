# เเบบฝึกหัด เรี่อง Ruby String Replacement Substitution and Insertion
### 1 เมธอด sub! และ  gsub! เหมือนหรือแตกต่างกันอย่างไร

<details>
   <summary>เฉลย</summary>

>เหมือนกัน : มีการแก้ไข้สตริงต้นฉบับจริงๆถ้าหาเจอ และจะคืนค่ากลับมาเป็นสตริงที่ถูกแก้ไขแล้ว แต่หากหาไม่เจอจะคืนค่าเป็น nil
แตกต่างกัน :  gsub! จะแทนที่ทุกตำแหน่งที่เจอ ส่วน sub! จะแทนที่แค่ตำแหน่งแรกที่เจอ
</details>

### 2
```ruby

```
### 3
```ruby

```
### 4.จงเขียนโปรแกรมภาษา Ruby เพื่อแทรกเครื่องหมาย “-” ระหว่างตัวอักษรทุกตัวใน String ที่ผู้ใช้ได้ทำการป้อนเข้ามา โดยใช้เมธอด .insert()
กำหนดให้

* รับอินพุต 1 บรรทัดเป็น String แทรก “-” ระหว่างตัวอักษรในสตริง เช่น "Ruby" -> "R-u-b-y"
* หากความยาวของ String เท่ากับ 0 หรือ 1 ให้แสดงผลตามเดิม

<details close>
   <summary><b>Solution Ruby</b></summary>
    
```ruby
input = gets.chomp

if input.length <= 1
  puts input
else
  i = input.length - 1
  while i > 0
    input.insert(i, "-")
    i -= 1
  end
  puts input
end
```
Input :
```ruby

Hellomyworld 

 ```
Output
```ruby

H-e-l-l-o-m-y-w-o-r-l-d

 ```        
</details>


<details close>
   <summary><b>Solution C</b></summary>
    
```c
#include <stdio.h>
#include <string.h>

void insertString(char *str, const char *insert, int index) {
    int lenStr = strlen(str);
    int lenInsert = strlen(insert);
    
    memmove(str + index + lenInsert, str + index, lenStr - index + 1);
    memcpy(str + index, insert, lenInsert);
}

int main() {
    char str[200];
    char insert[] = "-";

    scanf("%s", str);

    int len = strlen(str);
    if (len <= 1) {
        printf("%s\n", str);
        return 0;
    }

    for (int i = len - 1; i > 0; i--) {
        insertString(str, insert, i);
    }

    printf("%s\n", str);
    return 0;
}
```
Input :
```c

Hellomyworld 

 ```
Output
```c

H-e-l-l-o-m-y-w-o-r-l-d

 ```        
</details>

<details close>
   <summary><b>Solution Java</b></summary>
    
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine();
        scanner.close();

        StringBuffer str = new StringBuffer(input);

        if (str.length() > 1) {
            for (int i = str.length() - 1; i > 0; i--) {
                str.insert(i, "-");
            }
        }

        System.out.println(str.toString());
    }
}

```
Input :
```java

Hellomyworld 

 ```
Output
```java

H-e-l-l-o-m-y-w-o-r-l-d

 ```        
</details>

<details close>
   <summary><b>Solution Python</b></summary>
    
```python
s = input("Enter a string: ")

if len(s) <= 1:
    print(s)
else:
    for i in range(len(s)-1, 0, -1):
        s = s[:i] + "-" + s[i:]
    print(s)

```
Input :
```python

Hellomyworld 

 ```
Output
```python

H-e-l-l-o-m-y-w-o-r-l-d

 ```        
</details>


### 5
```ruby

```
### 6 เขียนโปรแกรมภาษา Ruby เพื่อตรวจสอบว่าสตริงที่ผู้ใช้ป้อนเข้ามาเป็น Palindrome หรือไม่ โดยใช้เมธอด .reverse()
- Ruby
```ruby
def palindrome?(str)
  str == str.reverse
end

print "Enter a word: "
word = gets.chomp

if palindrome?(word)
  puts "#{word} is a palindrome."
else
  puts "#{word} is not a palindrome."
end
```
- Java
```java
import java.util.Scanner;

public class PalindromeChecker {
    public static boolean isPalindrome(String str) {
        int left = 0;
        int right = str.length() - 1;

        while (left < right) {
            if (str.charAt(left) != str.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a word: ");
        String word = sc.nextLine();

        if (isPalindrome(word)) {
            System.out.println(word + " is a palindrome.");
        } else {
            System.out.println(word + " is not a palindrome.");
        }
    }
}
```
