# Intersection, Union and Difference

เรื่องนี้จะเป็นสิ่งที่ทุกคนคุ้นเคยกันเป็นอย่างดีตั้งแต่โรงเรียนแน่นอน เพราะไม่ว่าจะไปที่ไหนต้องมีหลักการความคิดแบบนี้เป็นทั่วไป นั่นคือเรื่อง Intersection, Union และ Differenceนั่นเอง! ซึ่งเราจะมาดูกันว่าหลักการมันทำงานยังไงในภาษาโปรแกรมอย่าง Ruby นะครับผมซึ่งไม่ต้องห่วงเลย! ผมจะยกตัวอย่างเปรียบเทียบกับภาษาอื่นอย่างแน่นอน เช่น C, Python, Java 

<img width="621" height="232" alt="image" src="https://github.com/user-attachments/assets/60f15568-5ab1-4e6e-bd1e-3676d90c48b4" />

ซึ่งผมขอทบทวนให้ทุกคนที่เข้ามาอ่านเพื่ออย่างน้อยได้รำลึกถึงสมัยวันวานกันหน่อยนะครับ ซึ่งตามภาพเลยคือความหมายของแต่ละแบบซึ่งในตอนผมยังเด็กๆผมก็มีทริคจำความหมายของพวกนี้ง่ายๆคือ Union = เอาหมด, Intersection = เอาซ้ำ, Difference = เอาตัวหลักและไม่เอาตัวซ้ำ อาจจะตลกไปหน่อยแต่นี่คือทริคการจำของผมครับ 

### ในเมื่อเราได้ทบทวนคร่าวๆไปบ้างแล้วงั้นผมขอเข้าสู่เนื้อหาเลยแล้วกันนะ


## 1.) Intersection ( & )
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




## 2.) Union ( | )
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

## 3.) Difference ( - )
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


## ตัวอย่างในภาษา C, Java, Python

## Intersection ( & ) | C
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


---

# Reference
- stackoverflow : https://stackoverflow.com/questions/5678108/how-can-i-get-the-intersection-union-and-subset-of-arrays-in-ruby
- Ruby-lang : https://www.ruby-lang.org/en/ 
- geeksforgeeks : https://www.geeksforgeeks.org/ruby/ruby-set-operations/
- Github (lifeparticle) : https://github.com/lifeparticle/Ruby-Cheatsheet?tab=readme-ov-file
- Github (ga-wdi-boston) : https://github.com/ga-wdi-boston/ruby-array-methods
- Programming Ruby (Book) : https://jmvidal.cse.sc.edu/library/thomas05a.pdf
- Ruby Cookbook by Lucas Carlson & Leonard Richardson : https://books.google.lk/books?id=oRqkBwAAQBAJ&printsec=copyright#v=onepage&q&f=false
