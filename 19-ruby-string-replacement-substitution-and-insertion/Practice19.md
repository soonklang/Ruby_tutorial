# เเบบฝึกหัด เรี่อง Ruby String Replacement Substitution and Insertion
### 1
```ruby

```
### 2
```ruby

```
### 3
```ruby

```
### 4
```ruby

```
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
