# 📌 What is Ruby Array
Array เป็นโครงสร้างข้อมูลชนิดหนึ่ง สามารถใช้เก็บหลายตัวแปรได้ ซึ่งข้อมูลข้างในจะเป็นประเภทเดียวกันหรือหลากหลายประเภทก็ได้ 
### Example
```ruby
a = [1,2,"A",true]
print a
```
<details> <summary>Output</summary>
[1, 2, "A", true]
</details>

# 📌 How to Creat a Ruby Array
## วิธีสร้าง Array แบบธรรมดา Ruby
```ruby
a = [1,2,3,"Cat"]
print a
```
<details> <summary>Output</summary>
[1, 2, 3, "Cat"]
</details>

### Example ภาษาอื่นๆ
**ภาษา python**
```python
ar_ray = [1,"hello",3.14,True]
```
<details> <summary>Output</summary>
[1,"hello",3.14,True]
</details>

**ภาษา C**

```C
int myNum[] = {25,50,75,100};
char fruits[2][10] = {"apple","banana"};
printf("myNum: ");
    for (int i = 0; i < 4; i++) {
        printf("%d ", myNum[i]);
    }
    printf("\n");
    printf("fruits: ");
    for (int i = 0; i < 2; i++) {
        printf("%s ", fruits[i]);
    }
```

<details> <summary>Output</summary>
myNum: 25 50 75 100<br>
fruits: apple banana
</details>

**ภาษา Java**

```Java
int[] nums = {1,2,3};
String[] fruits = {"apple","banana"};
for (int i = 0; i < nums.length; i++) {
            System.out.print(nums[i]+" ");
        }
        System.out.println();
        // แสดงผลผลไม้ใน fruits ทีละตัว
        for (int i = 0; i < fruits.length; i++) {
            System.out.print(fruits[i]+" " );
        }
}

```
<details> <summary>Output</summary>
1 2 3<br>
apple banana
    
</details>

## วิธีสร้าง Array แบบว่างเปล่า Ruby
```ruby
my_lovely1 = []
print my_lovely1
```

<details> <summary>Output</summary>
[]
</details>

```ruby
my_lovely2 = Array.new
print my_lovely2
```

<details> <summary>Output</summary>
[]
</details>

```ruby
arr1 = Array.new(3)
print arr1
```

<details> <summary>Output</summary>
[nil,nil,nil]
</details>

```ruby
arr2 = Array.new(3,0)
print arr2
```
<details> <summary>Output</summary>
[0,0,0]
</details>

### Example ภาษาอื่นๆ
**ภาษา python**
```python
arr = []
print(arr)
```

<details> <summary>Output</summary>
[]
</details>

**ภาษา C**

```C
ไม่มีอาเรย์ว่างเปล่าโดยตรงต้องสร้างแบบกำหนดเอา
int c[3]={0, 0, 0};
for (int i = 0; i < 3; i++) {
    printf("%d ", c[i]);
}
```

<details> <summary>Output</summary>
0,0,0
</details>

**ภาษา Java**

```Java
import java.util.Arrays;
class Main {
    public static void main(String[] args) {
        int[] arr =new int[0];
        System.out.println(Arrays.toString(arr));
    }
}
```
<details> <summary>Output</summary>
[]
</details>

# Video
---
# Slide
https://silpakorn-my.sharepoint.com/:p:/g/personal/khumpetch_k3_su_ac_th/EdMgRIPvTTlEnaUeF1RFW6oBuqsYBzoTdBVaddbKbhkqkw?rtime=dqtbArDm3Ug
# Reference
Codecademy – Ruby Arrays. เข้าถึงเมื่อ 30 สิงหาคม 2025 จาก https://www.codecademy.com/learn/learn-ruby/modules/learn-ruby-arrays-and-hashes-u/cheatsheet <br>
Programiz – Ruby Arrays. เข้าถึงเมื่อ 30 สิงหาคม 2025 จาก https://www.programiz.com/ruby/array <br>
W3Schools – C Arrays. เข้าถึงเมื่อ 30 สิงหาคม 2025 จาก https://www.w3schools.com/c/c_arrays.php <br>
W3Schools – Java Arrays. เข้าถึงเมื่อ 30 สิงหาคม 2025 จาก https://www.w3schools.com/java/java_arrays.asp <br>

