# Intersection, Union and Difference

เรื่องนี้จะเป็นสิ่งที่ทุกคนคุ้นเคยกันเป็นอย่างดีตั้งแต่โรงเรียนแน่นอน เพราะไม่ว่าจะไปที่ไหนต้องมีหลักการความคิดแบบนี้เป็นทั่วไป นั่นคือเรื่อง Intersection, Union และ Differenceนั่นเอง! ซึ่งเราจะมาดูกันว่าหลักการมันทำงานยังไงในภาษาโปรแกรมอย่าง Ruby นะครับผมซึ่งไม่ต้องห่วงเลย! ผมจะยกตัวอย่างเปรียบเทียบกับภาษาอื่นอย่างแน่นอน เช่น C, Python, Java 

<img width="621" height="232" alt="image" src="https://github.com/user-attachments/assets/60f15568-5ab1-4e6e-bd1e-3676d90c48b4" />

ซึ่งผมขอทบทวนให้ทุกคนที่เข้ามาอ่านเพื่ออย่างน้อยได้รำลึกถึงสมัยวันวานกันหน่อยนะครับ ซึ่งตามภาพเลยคือความหมายของแต่ละแบบซึ่งในตอนผมยังเด็กๆผมก็มีทริคจำความหมายของพวกนี้ง่ายๆคือ Union = เอาหมด, Intersection = เอาซ้ำ, Difference = เอาตัวหลักและไม่เอาตัวซ้ำ อาจจะตลกไปหน่อยแต่นี่คือทริคการจำของผมครับ 

ในเมื่อเราได้ทบทวนคร่าวๆไปบ้างแล้วงั้นผมขอเข้าสู่เนื้อหาเลยแล้วกันนะ

## ตัวอย่างในภาษา Ruby

### 1.) Intersection ( & ) | Ruby
<pre>
a = [1, 2, 3]
b = [3, 4, 5]

puts (a & b)
</pre>

นี่คือโค๊ดตัวอย่างง่ายๆที่ผมยกมาให้ดูกันครับ ซึ่งตามทริคที่ผมบอกไปก่อนหน้านี้เลยคือ Intersection = เอาตัวซ้ำ งั้นจากโค๊ดนี้ผมลลัพธ์ที่จะออกมานั่นก็ง่ายๆเลยครับผมนั่นคือ  
<details> 
  <summary>Output</summary>
  3
</details>




### 2.) Union ( | ) | Ruby
<pre>
a = [1, 2, 3]
b = [3, 4, 5]

puts (a | b)
</pre>

เรามาต่อกันที่ตัวต่อไปกันเลยครับแถมยังเป็นตัวที่ง่ายที่สุดในทุกบรรดาผองเพื่อนของมันเลยด้วยนั่นคือ Union ซึ่งก็กลับมานึกตามทริคการจำของผมอีกเช่นเคยคือ Union = เอาหมด แสดงว่าจากโค๊ดที่ผมให้มานั้นผลลัพธ์ที่ได้นั่นคือ ตัวเลขทั้งหมดทุกตัวในอาเรย์ของ a และ b ครับผมซึ่งมันคือ
<details> 
  <summary>Output</summary>
   1,2,3,4,5 
</details>

### 3.) Difference ( - ) | Ruby
<pre>
a = [1, 2, 3]
b = [3, 4, 5]

puts (a - b)
</pre>

และที่ขาดไปไม่ได้อย่างอันสุดท้ายคือ Difference นั่นเองและอย่างที่ผมบอกเช่นเคยนั่นคือ Difference = เอาตัวหลักและไม่เอาตัวซ้ำ แสดงว่าผลลัพธ์ที่ได้จากโค๊ดตัวอย่างนั่นคือ 
<details> 
  <summary>Output</summary>
   1,2 
</details>


## ตัวอย่างในภาษา C
ผมจะพยายามอธิบายให้เข้าใจง่ายที่สุดของแต่ละตัวอย่างนะครับ งั้นไปเริ่มกันเลย!
### Intersection ( & ) | C
<pre>
#include <stdio.h>

int main() {
    int a[] = {1,2,3};
    int b[] = {3,4,5};
    for (int i = 0; i < 3; i++) {
        for(int j = 0; j<3;j++)
        {
            if(a[i] == b[j])
            {
                printf("%d ", a[i]);
            }
        }
    }
}
</pre>
<details> 
  <summary>Output</summary>
  3
</details>

หลักการของโค้ดอย่างง่ายคือ:

1. เราเอาตัวเลขแต่ละตัวใน a ไปเทียบกับทุกตัวใน b ทีละตัว
2. ถ้าเจอเลขที่เหมือนกัน ก็พิมพ์เลขนั้นออกมา
3. แบบนี้เหมือนเราเอากล่องของ a มาไล่ดูทีละอันว่าใน b มีอันเดียวกันมั้ย
4. เจอปุ๊บ ก็แสดงผลเลย




### Union ( | ) | C
<pre>
  
#include <stdio.h>

int main() {
    
    int a[] = {1, 2, 3}; 
    int b[] = {3, 4, 5};
    int sizeA = sizeof(a) / sizeof(a[0]);
    int sizeB = sizeof(b) / sizeof(b[0]);
    
    int c[10]; 
    int sizeC = 0;
    
    for (int i = 0; i < sizeA; i++) {
        c[sizeC++] = a[i];
    }


    for (int i = 0; i < sizeB; i++) {
        int found = 0;
        for (int j = 0; j < sizeC; j++) {
            if (b[i] == c[j]) {
                found = 1;  
                break;
            }
        }
        if (!found) {
            c[sizeC++] = b[i];
        }
    }
    for (int i = 0; i < sizeC; i++) {
        printf("%d ", c[i]);
    }

    return 0;
}

</pre>
<details> 
  <summary>Output</summary>
  1 2 3 4 5 
</details>

หลักการของโค๊ดอย่างง่ายคือ : 
1. เราเริ่มด้วยเอาทุกตัวใน a ใส่ลงในอาเรย์ใหม่ c เลย
2. จากนั้น เราก็เอาแต่ละตัวใน b มาตรวจสอบว่ามันเคยใส่ใน c หรือยัง
3. ถ้ายังไม่เคยใส่ ก็เอามาเพิ่มลง c ต่อ
4. สุดท้าย c จะมีเลขจาก a ทั้งหมด แล้วก็เลขจาก b ที่ไม่ซ้ำกัน
5. เท่ากับว่าเราได้ชุดเลขทั้งหมดที่อยู่ใน a และ b รวมกัน โดยไม่มีเลขซ้ำ
6. ก็เหมือนเอาของสองกล่องมารวมกันโดยไม่ให้ซ้ำกันนั่นเอง



### Difference ( - ) | C
<pre>
  #include <stdio.h>

int main() {
    int a[] = {1, 2, 3};
    int b[] = {3, 4, 5};
    int sizeA = sizeof(a) / sizeof(a[0]);
    int sizeB = sizeof(b) / sizeof(b[0]);

    int diff[10];
    int sizeDiff = 0;

    for (int i = 0; i < sizeA; i++) {
        int found = 0;
        for (int j = 0; j < sizeB; j++) {
            if (a[i] == b[j]) {
                found = 1;
                break;
            }
        }
        if (!found) {
            diff[sizeDiff++] = a[i];
        }
    }

    printf("a - b: ");
    for (int i = 0; i < sizeDiff; i++) {
        printf("%d ", diff[i]);
    }
    printf("\n");

    return 0;
}


</pre>
<details> 
  <summary>Output</summary>
  1 2 
</details>

หลักการของโค๊ดอย่างง่ายคือ : 
1. เราไล่ดูทีละตัวใน a
2. สำหรับแต่ละตัว เราก็เช็คว่าใน b มีตัวนั้นหรือเปล่า
3. ถ้าไม่มี เราก็เอาตัวนั้นใส่อาเรย์ใหม่ชื่อ diff
4. สุดท้าย เราก็จะได้แค่เลขที่อยู่ใน a เท่านั้น แต่ไม่มีใน b
5.  เหมือนเราหยิบของจากกล่อง a มา แล้วเช็คว่าของชิ้นนั้นอยู่ในกล่อง b มั้ย
6.  ถ้าไม่อยู่ เราก็เก็บไว้ แสดงว่าเป็นของที่ต่างกันนั่นเอง



## ตัวอย่างในภาษา Java

สิ่งที่ต้องรู้ก่อน :
1. Arrays.asList() สร้าง List ขนาดคงที่ เพิ่มหรือลดข้อมูลไม่ได้
2. เราต้องการ List ที่สามารถเพิ่มข้อมูลได้ (dynamic size) เพื่อเก็บผลลัพธ์ทีละตัว
3. เลยสร้าง ArrayList ใหม่ที่รับค่าจาก a หรือว่าง ๆ แล้วค่อยเพิ่มข้อมูลเข้าไป

### Intersection ( & ) | JAVA
<pre>
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> a = Arrays.asList(1, 2, 3);
        List<Integer> b = Arrays.asList(3, 4, 5);

        List<Integer> intersection = new ArrayList<>();

        for (int i : a) {
            if (b.contains(i)) {
                intersection.add(i);
            }
        }

    }
}

</pre>
<details> 
  <summary>Output</summary>
  3
</details>

หลักการของโค๊ดอย่างง่ายคือ : 
1. เราเริ่มจากลิสต์ a แล้วเอาทีละตัวมาเช็คใน b
2. ถ้าตัวนั้นอยู่ใน b เราก็เก็บมันไว้ใน intersection
3. นี่คือการหาค่าส่วนที่เหมือนกันใน a และ b

ทำไมสร้าง intersection เป็น new ArrayList<>() ? 

1. เราต้องการเพิ่มข้อมูลใหม่เรื่อย ๆ ใน intersection เลยต้องสร้าง ArrayList ใหม่ที่ขยายขนาดได้
2. ทำให้เราสามารถเพิ่มข้อมูลตอนรันโปรแกรมได้อย่างอิสระ

### Union ( | ) | JAVA
<pre>
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> a = Arrays.asList(1, 2, 3);
        List<Integer> b = Arrays.asList(3, 4, 5);

        List<Integer> union = new ArrayList<>(a);
        for (int i : b) {
            if (!union.contains(i)) {
                union.add(i);
            }
        }

        
    }
}
</pre>
<details> 
  <summary>Output</summary>
  1,2,3,4,5
</details>

หลักการของโค๊ดอย่างง่ายคือ : 
1. ไล่ดูทุกตัวใน a
2. ถ้าตัวนั้น ไม่เจอใน b เราก็เก็บไว้ใน difference
3. คือการหาค่าที่มีเฉพาะใน a เท่านั้น

ทำไมสร้าง union เป็น new ArrayList<>(a) ?
1. เพราะอยากเริ่มต้น union ด้วยข้อมูลทั้งหมดของ a ทันที
2. แล้วค่อยเพิ่มค่าจาก b เข้าไปทีหลัง
3. ใช้วิธีนี้จะได้ไม่ต้องเขียนลูปเพิ่มเพื่อใส่ a ทีหลังอีก


### Differnce ( - ) | JAVA
<pre>
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> a = Arrays.asList(1, 2, 3);
        List<Integer> b = Arrays.asList(3, 4, 5);

        List<Integer> difference = new ArrayList<>();

        for (int i : a) {
            if (!b.contains(i)) {
                difference.add(i);
            }
        }
    }
}

</pre>
<details> 
  <summary>Output</summary>
  1,2
</details>

หลักการของโค๊ดอย่างง่ายคือ : 
1. เริ่มจากเอาทุกตัวใน a ใส่ลงใน union เลย
2. แล้วลูปแต่ละตัวใน b
3. ถ้าตัวใน b ยังไม่มีใน union ก็เพิ่มเข้าไป
4. แบบนี้เราจะได้ค่าทั้งหมดจาก a และ b รวมกัน แต่ไม่มีตัวซ้ำ

ทำไมสร้าง difference เป็น new ArrayList<>() ?
1. เหมือนข้อแรก เพราะเราต้องเก็บค่าที่เจอทีละตัว เพิ่มเติมเรื่อย ๆ
2. Arrays.asList() ไม่สามารถเพิ่มข้อมูลได้ ทำให้ต้องใช้ ArrayList ใหม่ที่เพิ่มได้

## ตัวอย่างในภาษา Python

สิ่งที่ต้องรู้ก่อน ทำไมถึงใช้ set? : 
1. เพราะ set เป็นโครงสร้างข้อมูลที่เก็บข้อมูล ไม่ซ้ำกัน
2. ใช้งานง่ายและเร็วสำหรับการทำ Intersection, Union, Difference
3. โค้ดสั้น อ่านง่าย ไม่ต้องเขียนลูปตรวจสอบเองทีละตัว

### Intersection ( & ) | Python
<pre>
a = [1, 2, 3]
b = [3, 4, 5]

intersection = list(set(a) & set(b))

</pre>
<details> 
  <summary>Output</summary>
  3
</details>

หลักการของโค๊ดอย่างง่ายคือ : 
1. set(a) กับ set(b) แปลงลิสต์เป็นชุดข้อมูล (set) ซึ่งข้อมูลจะไม่ซ้ำกัน
2. เครื่องหมาย & หมายถึงเอาส่วนที่ เหมือนกัน (intersection) ของสองชุด
3. สุดท้ายแปลงกลับเป็นลิสต์ด้วย list() เพื่อใช้งานตามปกติ

### Union ( | ) | Python
<pre>
a = [1, 2, 3]
b = [3, 4, 5]

union = list(set(a) | set(b))

</pre>
<details> 
  <summary>Output</summary>
  1,2,3,4,5
</details>

หลักการของโค๊ดอย่างง่ายคือ : 
1. set(a) | set(b) คือการรวมสมาชิกของทั้งสอง set โดยเอาทุกตัว แต่ไม่ซ้ำกัน (union)
2. แปลงกลับเป็นลิสต์เหมือนเดิม



### Differnce ( - ) | Python
<pre>
a = [1, 2, 3]
b = [3, 4, 5]

difference = list(set(a) - set(b))

</pre>
<details> 
  <summary>Output</summary>
  1,2
</details>

หลักการของโค๊ดอย่างง่ายคือ : 
1. set(a) - set(b) คือเอาตัวที่อยู่ใน a แต่ ไม่มี ใน b (difference)
2. แปลงกลับเป็นลิสต์เช่นกัน


---

# Reference
- stackoverflow : https://stackoverflow.com/questions/5678108/how-can-i-get-the-intersection-union-and-subset-of-arrays-in-ruby
- Ruby-lang : https://www.ruby-lang.org/en/ 
- geeksforgeeks : https://www.geeksforgeeks.org/ruby/ruby-set-operations/
- Github (lifeparticle) : https://github.com/lifeparticle/Ruby-Cheatsheet?tab=readme-ov-file
- Github (ga-wdi-boston) : https://github.com/ga-wdi-boston/ruby-array-methods
- Programming Ruby (Book) : https://jmvidal.cse.sc.edu/library/thomas05a.pdf
- Ruby Cookbook by Lucas Carlson & Leonard Richardson : https://books.google.lk/books?id=oRqkBwAAQBAJ&printsec=copyright#v=onepage&q&f=false
