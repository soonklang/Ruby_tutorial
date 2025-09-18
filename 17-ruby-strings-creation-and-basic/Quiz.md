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
---
##  2.จงเขียนโปรแกรมให้แสดงคำว่า Albert Einstein said "I have no special talent. I am only passionately curious."โดยข้อความผลลัพธ์ต้องแสดงตัว " " ด้วย และกำหนดให้ใช้ภาษาRubyโดยใช้วิธี general delimited stringในการทำ พร้อมทั้งโปรแกรมที่แสดงผลแบบเดียวกันด้วยภาษา Python,Java & C (ไม่จำกัดวิธีในกรณี Python,Java & C)

<details close>
   <summary><b>เฉลยภาษา Ruby</b></summary>
    
```ruby
    msg = %{Albert Einstein said "I have no special talent. I am only passionately curious."}
    puts msg
 ```
        
</details>

<details close>
   <summary><b>เฉลยภาษา Python</b></summary>
    
```python
    msg = 'Albert Einstein said "I have no special talent. I am only passionately curious."'
    print(msg)
 ```
        
</details>

<details close>
   <summary><b>เฉลยภาษา Java</b></summary>
    
```java
    public class Quote {
        public static void main(String[] args) {
            String msg = "Albert Einstein said \"I have no special talent. I am only passionately curious.\"";
            System.out.println(msg);
        }
    }
 ```
        
</details>

<details close>
   <summary><b>เฉลยภาษา C</b></summary>
    
```c
    #include <stdio.h>
    void main() {
        printf("Albert Einstein said \"I have no special talent. I am only passionately curious.\"\n");
    }
 ```
        
</details>

---
## 3. ให้เขียนโปรแกรมเพื่อรับข้อมูล **ชื่อ อายุ สาขาวิชา** จากผู้ใช้ แล้วแสดงข้อความแนะนำตัว (อย่างน้อย 3 บรรทัด) โดยใช้การสร้างข้อความหลายบรรทัดในแต่ละภาษา (Ruby: Heredoc, Java: Text Block, C: เชื่อม string, Python: triple quotes)  
**หมายเหตุ:**  
- ใช้ฟีเจอร์รับข้อมูล input ตามรูปแบบแต่ละภาษา  
- ข้อความแสดงผลต้องมีข้อมูลที่รับมาแทรกอยู่

---

<details>
  <summary>คลิกเพื่อดูเฉลย</summary>

  ### Ruby
  ```ruby
  print "กรุณากรอกชื่อ: "
  name = gets.chomp
  print "กรุณากรอกอายุ: "
  age = gets.chomp
  print "กรุณากรอกสาขาวิชา: "
  major = gets.chomp

  str = <<TEXT
  สวัสดีค่ะ ฉันชื่อ #{name}
  อายุ #{age} ปี
  สาขาวิชา: #{major}
  TEXT

  puts str
  ```

  ---

  ### Java (Text Block, Java 15+)
  ```java
  import java.util.Scanner;
  public class Main {
      public static void main(String[] args) {
          Scanner sc = new Scanner(System.in);
          System.out.print("กรุณากรอกชื่อ: ");
          String name = sc.nextLine();
          System.out.print("กรุณากรอกอายุ: ");
          String age = sc.nextLine();
          System.out.print("กรุณากรอกสาขาวิชา: ");
          String major = sc.nextLine();

          String str = """
              สวัสดีค่ะ ฉันชื่อ %s
              อายุ %s ปี
              สาขาวิชา: %s
              """.formatted(name, age, major);

          System.out.println(str);
      }
  }
  ```

  ---

  ### C
  ```c
  #include <stdio.h>
  int main() {
      char name[100], age[10], major[100];
      printf("กรุณากรอกชื่อ: ");
      fgets(name, sizeof(name), stdin);
      printf("กรุณากรอกอายุ: ");
      fgets(age, sizeof(age), stdin);
      printf("กรุณากรอกสาขาวิชา: ");
      fgets(major, sizeof(major), stdin);

      printf("สวัสดีค่ะ ฉันชื่อ %s", name);
      printf("อายุ %s", age);
      printf("สาขาวิชา: %s", major);
      return 0;
  }
  ```

  ---

  ### Python
  ```python
  name = input("กรุณากรอกชื่อ: ")
  age = input("กรุณากรอกอายุ: ")
  major = input("กรุณากรอกสาขาวิชา: ")

  str = f"""สวัสดีค่ะ ฉันชื่อ {name}
  อายุ {age} ปี
  สาขาวิชา: {major}
  """
  print(str)
  ```

</details>

##  4. ผลลัพธ์ที่ได้จากโค้ดดังต่อไปนี้คืออะไร

```ruby
    puts "This is the first question and it\'s a \"Ruby\" language\."
 ```

<details>
<summary><strong>เฉลย</strong></summary>
    
```
This is the first question and it's a "Ruby" language.
```

</details>

```python
    number = 2
    print(f' And this is the {number}nd question\n take your time.')
 ```

<details>
<summary><strong>เฉลย</strong></summary>
    
```
And this is the 2nd question
take your time.
```

</details>

```c
    #include <stdio.h>
    void main() {
        printf("This one \\ is\neasy.");
    }
 ```

<details>
<summary><strong>เฉลย</strong></summary>
    
```
This one \ is
easy.
```

</details>

```java
    public class question {
        public static void main(String[] args) {
            String str = "What\'s favourite ";
            String str2 = "Programming language?";
            System.out.println("Last question " + str + str2);
        }
    }
 ```

<details>
<summary><strong>เฉลย</strong></summary>
    
```
Last question What's favourite Programming language?
```

</details>
