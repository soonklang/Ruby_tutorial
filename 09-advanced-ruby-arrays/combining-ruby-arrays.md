# Combining Ruby Arrays
การรวม Array ในภาษา Ruby ด้วย 3 วิธี 

## 1. การใช้เครื่องหมาย +

ใช้สำหรับสร้าง Array ใหม่ จากการนำสมาชิกของ Array ตั้งแต่สองตัวขึ้นไปมาต่อกัน

**Syntax :**


```ruby
new_array = array1 + array2 + ...
```


#### Key Point :

* การใช้ + จะได้ Array ชุดใหม่เสมอ
* Array ชุดเดิมจะไม่ถูกเปลี่ยนแปลงข้อมูล

**Example :**

<pre data-title="ruby" data-line-numbers>
<code>array1 = [1, 2, 3]
array2 = [4, 5, 6]
array3 = [7, 8, 9]

new_array = array1 + array2 + array3
puts new_array.inspect
</code></pre>

**Output :**
```
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```


## 2. การใช้เมธอด .concat( )
ใช้สำหรับนำสมาชิกจาก Array อื่นตั้งแต่หนึ่งตัวขึ้นไปมาต่อท้าย Array เดิม

**Syntax :**

<pre class="language-ruby" data-title="ruby" data-line-numbers><code class="lang-ruby">target_array.concat(array1,array2,...)
</code></pre>

#### Key Point :
* การใช้ .concat() ไม่มีการสร้าง Array ชุดใหม่
* Array ชุดเดิม(target\_array) จะถูกเปลี่ยนแปลงข้อมูล

#### Example :
```ruby
target_array = [1, 2, 3] 
array1 = [4, 5 , 6]
array2 = [7, 8, 9]

target_array.concat( array1 , array2 )
puts target_array.inspect
```
**Output :**
```
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## 3. การใช้ << (Shovel)
การเพิ่มสมาชิก "**1 ชิ้น**" เข้าไปที่ท้ายสุดของ Array เดิม ( \[1,2,3] แบบนี้ถือว่านับเป็น 1 ชิ้น )

**Syntax :**
```ruby
target_array << element
```

#### Key Point :
* สมาชิกที่ต้องการเพิ่มเข้าไปจะถูกมองว่าเป็นสมาชิก "**ชิ้นเดียว**" เสมอ

#### Example :
```ruby
target_array = [1,2,3]
array1 = [4,5,6]

target_array << array1
puts target_array.inspect

target_array << "seven"
puts target_array.inspect
```
**Output :**
```
[1, 2, 3, [4, 5, 6]]
[1, 2, 3, [4, 5, 6], "seven"]
```

## ตารางสรุป 

<table><thead><tr><th width="100.20001220703125" align="center">วิธีการ</th><th width="190.39996337890625" align="center">การทำงาน</th><th width="156.60003662109375" align="center">ผลกระทบต่อ Array เดิม</th><th>Syntax</th></tr></thead><tbody><tr><td align="center"><strong>+</strong></td><td align="center">นำสมาชิกมาต่อท้ายกัน เพื่อสร้าง Array ใหม่
</td><td align="center">ไม่แก้ไข</td><td>new_array = array1+array2+...</td></tr><tr><td align="center"><strong>.concat( )</strong></td><td align="center">นำสมาชิกมาต่อท้าย Array เดิม **เพิ่มได้เฉพาะ Array 
</td><td align="center">แก้ไขโดยตรง</td><td>target_array.concat(array1,array2,...)</td></tr><tr><td align="center"><strong>&#x3C;&#x3C;</strong></td><td align="center">เพิ่มสมาชิก 1 ชิ้น เข้าไปท้าย Array เดิม</td><td align="center">แก้ไขโดยตรง</td><td>target_array &#x3C;&#x3C; element</td></tr></tbody></table>



***



## เปรียบเทียบกับภาษา Java / C / Python
จริง ๆ แล้วแต่ละภาษามีหลากหลายวิธีที่แตกต่างกันไป ที่นี่เราจะหยิบแค่บางวิธีมาให้ดู

### 1. การต่อกันเพื่อสร้าง Array / List ใหม่

<table><thead><tr><th width="108.99995422363281" align="center">ภาษา</th><th width="731.7999877929688">Syntax หรือ ตัวอย่าง </th></tr></thead><tbody><tr><td align="center"><strong>Ruby</strong></td><td><pre class="language-ruby" data-title="ruby" data-line-numbers><code class="lang-ruby">new_array = array1 + array2 + … 
</code></pre><hr><p>ใช้เครื่องหมาย + ได้เป็น Array ใหม่ </p></td></tr><tr><td align="center"><strong>Python</strong></td><td><pre class="language-python" data-title="python" data-line-numbers><code class="lang-python">new_list = list1 + list2
</code></pre><hr><p>เหมือนกับ Ruby ใช้เครื่องหมาย + เพื่อสร้าง List ใหม่ขึ้นมา</p></td></tr><tr><td align="center"><strong>Java</strong></td><td><pre class="language-java" data-title="java" data-line-numbers><code class="lang-java">int[] array1 = {1, 2};
int[] array2 = {3, 4};
int[] allGroups = new int[(array1.length)+(array2.length)]; // Array ใหม่
System.arraycopy(array1,0,allGroups,0,array1.length); //Copy array1
System.arraycopy(array2,0,allGroups,array1.length,array2.length); //Copy array2
</code></pre><hr><p>ต้องสร้าง Array ใหม่ที่มีขนาดใหญ่กว่าหรือพอดี สำหรับรองรับสมาชิกจากทั้งสอง Array  และใช้ System.arraycopy ( ) ในการคัดลอกสมาชิกจาก Array เดิมไปไว้ใน Array ใหม่ หรือ จะใช้การวนลูปก็ได้เช่นกัน</p></td></tr><tr><td align="center"><strong>C</strong></td><td><pre class="language-c" data-title="C" data-line-numbers>
<code  class="lang-c">
int array1[] = {2, 4, 6}; 
int size1 = 3;
int array2[] = {8, 10, 12, 14}; 
int size2 = 4;

int merged[200]; // Array ใหม่
int mergedSize = size1 + size2;

for (int i = 0; i &#x3C; size1; i++) { //Copy array1
    merged[i] = array1[i];
}

for (int i = 0; i &#x3C; size2; i++) { //Copy array2
    merged[size1 + i] = array2[i];
}
</code></pre><hr><p>ต้องสร้าง Array ใหม่ที่มีขนาดใหญ่กว่าหรือพอดี สำหรับรองรับสมาชิกจากทั้งสอง Array </p><p>และใช้ลูปในการคัดลอกสมาชิกจาก Array เดิมไปไว้ใน Array ใหม่ทีละตัว</p></td></tr></tbody></table>

### 2. การนำสมาชิกมาต่อท้าย Array/List เดิม

<table><thead><tr><th width="112.39999389648438" align="center">ภาษา</th><th>Syntax และตัวอย่าง</th></tr></thead><tbody><tr><td align="center"><strong>Ruby</strong></td><td><pre class="language-ruby" data-title="ruby" data-line-numbers><code class="lang-ruby">array1.concat(array2)
</code></pre><hr><p>ใช้เมธอด .concat() สำหรับนำสมาชิกมาต่อท้าย Array เดิม</p></td></tr><tr><td align="center"><strong>Python</strong></td><td><pre class="language-c" data-title="python" data-line-numbers><code class="lang-c">list1.extend(list2) 
list1 += list2
</code></pre><hr><p>ใช้เมธอด .extend() ซึ่งทำงานเหมือน .concat() ใน Ruby</p></td></tr><tr><td align="center"><strong>Java</strong></td><td><pre class="language-java" data-title="java" data-line-numbers><code class="lang-java">myArrayList1.addAll(myArrayList2);
</code></pre><hr><p>ใช้เมธอด .addAll() ซึ่งจะเพิ่มสมาชิกทั้งหมดจาก Arraylist2 เข้าไปใน Arraylist1</p><p>( ArrayList จะมีความยืดหยุ่น มากกว่า Array ธรรมดา )</p></td></tr><tr><td align="center"><strong>C</strong></td><td><pre class="language-c" data-title="C" data-line-numbers><code class="lang-c">int array1[100] = {2, 4, 6}; 
int size1 = 3;

int arr2[100] = {8, 10, 12, 14}; 
int size2 = 4;

for (int i = 0; i &#x3C; size2; i++) {
    array1[size1] = array2[i];
    size1++;
}
</code></pre><hr><p>ใช้การสร้าง Array ให้มีขนาดใหญ่เพียงพอ สำหรับการเพิ่มสมาชิกในอนาคต และวนลูปเพื่อคัดลอกสมาชิกจาก array2 ไปต่อท้าย array1 </p></td></tr></tbody></table>

### 3. การเพิ่มสมาชิก 1 ตัวท้าย Array/List  เดิม

<table><thead><tr><th width="111.60000610351562" align="center">ภาษา</th><th>Syntax และตัวอย่าง</th></tr></thead><tbody><tr><td align="center"><strong>Ruby</strong></td><td><pre class="language-ruby" data-title="ruby" data-line-numbers><code class="lang-ruby">array &#x3C;&#x3C; element
</code></pre><hr><p>ใช้ <code>&#x3C;&#x3C;</code> สำหรับเพิ่มสมาชิก 1 ชิ้น เข้าไปท้าย Array เดิม</p></td></tr><tr><td align="center"><strong>Python</strong></td><td><pre class="language-python" data-title="python" data-line-numbers><code class="lang-python">my_list.append(element)
</code></pre><hr><p>ใช้เมธอด .append() </p></td></tr><tr><td align="center"><strong>Java</strong></td><td><pre class="language-java" data-title="java" data-line-numbers><code class="lang-java">myArrayList.add(element);
</code></pre><hr><p>ใช้เมธอด .add() ของ ArrayList หรือ List อื่นๆ </p><p>( ArrayList จะมีความยืดหยุ่น มากกว่า Array ธรรมดา )</p></td></tr><tr><td align="center"><strong>C</strong></td><td><pre class="language-c" data-title="C" data-line-numbers><code class="lang-c">int arr1[100] = {2, 4, 6}; 
int size1 = 3;

size1++;
arr1[size1++] = 8;
size1++;
arr1[size1++] = 10;
size1++;
arr1[size1++] = 12;
</code></pre><hr><p>ใช้การเพิ่มสมาชิกทีละตัว แต่ข้อจำกัดคือไม่สามารถเพิ่ม Array ทั้งชุดเข้าไปเป็นสมาชิก "<strong>ชิ้นเดียว</strong>" ได้เหมือนกับการใช้  <strong><code>&#x3C;&#x3C;</code></strong> ในภาษา Ruby</p></td></tr></tbody></table>



## Reference

***

### Ruby

* Techotopia. (n.d.). Advanced Ruby Arrays. Retrieved September 1, 2025, from <br>
  [https://www.techotopia.com/index.php/Advanced\_Ruby\_Arrays]

* Ruby-doc.org. (n.d.). Methods for Comparing. Retrieved September 1, 2025, from <br>
  [https://ruby-doc.org/core-3.1.2/Array.html#class-Array-label-Methods+for+Comparing]

* how.dev. (n.d.). What is Array#concat in Ruby?. Retrieved September 1, 2025, from <br>
  [https://how.dev/answers/what-is-array-concat-in-ruby]


### Python

* Python Software Foundation. (n.d.). More on Lists. Retrieved September 3, 2025, from <br>
  [https://docs.python.org/3/tutorial/datastructures.html#more-on-lists]

* GeeksforGeeks. (n.d.). Python | Ways to Concatenate Two Lists. Retrieved September 3, 2025, from <br>
  [https://www.geeksforgeeks.org/python/python-ways-to-concatenate-two-lists/]

### Java

* GeeksforGeeks. (n.d.). Java | Program to Merge Two Arrays. Retrieved September 3, 2025, from <br>
  [https://www.geeksforgeeks.org/java/java-program-to-merge-two-arrays/]

* W3Schools. (n.d.). Java ArrayList class. Retrieved September 3, 2025, from <br>
  [https://www.w3schools.com/java/java\_ref\_arraylist.asp]

### C

* Wscubetech. (n.d.). Merge Two Arrays. Retrieved September 3, 2025, from <br>
  [https://www.wscubetech.com/resources/c-programming/programs/merge-two-arrays]

* CodeChef. (n.d.). DSAC26. Retrieved September 3, 2025, from<br>
  [https://www.codechef.com/learn/course/college-data-structures-c/CPDSC01/problems/DSAC26?tab=statement]

