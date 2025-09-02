# Sorting Arrays (การเรียงข้อมูลใน Array)

Sorting Arrays คือการเรียงข้อมูลใน array โดยสามารถเรียงข้อมูลให้เป็นไปตามที่เรากำหนดได้ว่าอยากให้เรียงข้อมูล array ให้เรียงในรูปแบบที่ต้องการ

โดย Ruby จะมีการ sorting ทั้งหมด 4 รูปแบบแบบชัดเจนได้ดังนี้ :

1. sort (ที่จะไม่ทำการเปลี่ยนแปลงค่าเดิมใน array)
2. sort! (ที่จะทำการเปลี่ยนแปลงค่าเดิมใน array)
3. sort\_by (ที่จะไม่ทำการเปลี่ยนแปลงค่าเดิมใน array โดยจะใช้  block ในการเปลี่ยนแปลงค่า)
4. sort\_by! (ที่จะทำการเปลี่ยนแปลงค่าเดิมใน array โดยจะใช้  block ในการเปลี่ยนแปลงค่า)

ก่อนจะเริ่มการเปรียบเทียบเนื่องจากภาษา c ไม่มีฟังก์ชันที่สนับสนุนกับการใช้ sorting array มากเท่าที่ควร เนื่องจากภาษา c เป็นภาษาระดับต่ำเป็นสาเหตุที่ทำให้ต้องเน้นในเรื่องของประสิทธิภาพและการควบคุมหน่วยความจำที่ต้องจัดการเอง โดยทำให้มีแค่ฟังก์ชันแค่ qsort ทำให้ต้องมีการสร้าง ฟังก์ชั่นเปรียบเทียบเพื่อให้สามารถนำภาษา c มาเปรียบเทียบกับภาษา ruby ได้โดยตัวของ code สำหรับการใช้งานจะมีดังนี้

**ฟังก์ชั่นการเปรียบเทียบที่ไว้ใช้สำหรับภาษา C**
```c
#include <stdio.h>    /* สำหรับ I/O เช่น printf */
#include <stdlib.h>   /* สำหรับ qsort, malloc, free */
#include <string.h>   /* สำหรับ strcmp, strlen, memcpy */

int compareStrings(const void *a, const void *b) {
    const char **str_a = (const char **)a;
    const char **str_b = (const char **)b;
    return strcmp(*str_a, *str_b);
} /* ฟังก์ชันเปรียบเทียบ String ตามลำดับตัวอักษร ซึ่งหลักการทำงานจะคล้ายกับตัว sort ของ ruby */

int compareByLength(const void *a, const void *b) {
    const char **str_a = (const char **)a;
    const char **str_b = (const char **)b;
    int len_a = strlen(*str_a);
    int len_b = strlen(*str_b);
    return (len_a > len_b) - (len_a < len_b); /* เทคนิคการคืนค่า -1, 0, หรือ 1 */
} /* ฟังก์ชันเปรียบเทียบ String ตามความยาวตัวอักษร ซึ่งหลักการทำงานจะคล้ายกับตัว sort_by ของ ruby */

void printArray(const char *arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%s ", arr[i]);
    }
    printf("\n");
} /* ตัวสำหรับการพิมพ์ Array ให้เข้าใจง่ายๆ */
```

---

## 1. sort (ที่จะไม่ทำการเปลี่ยนแปลงค่าเดิมใน array)

โดยการทำแบบนี้จะเป็นการเรียงค่าใน array โดยจะต้องมี array อีกตัวหนึ่งในการเก็บค่า array ที่ได้ทำการเรียงข้อมูลผ่านการ sort ไว้แล้ว
โดยวิธีการใช้งานสามารถใช้งานได้ดังนี้ :

**Ruby**
```ruby
numbers = [3, 1, 5, 2, 4]
sorted_numbers = numbers.sort
puts sorted_numbers  #ผลลัพธ์ที่ได้ => [1, 2, 3, 4, 5]
```

**C**
```c
const char *original1[] = {"kiwi", "apple", "fig", "banana"};
int n = sizeof(original1) / sizeof(original1[0]);
const char **sorted_copy = malloc(n * sizeof(const char *)); /* จะเป็นการสร้าง array เพื่อมาเตรียมพร้อมสำหรับการใส่ค่าที่เรียงไว้ */
memcpy(sorted_copy, original1, n * sizeof(const char *)); /* ทำการคัดลอกข้อมูลจาก original1 มาใส่ยังตัว  sorted_copy */
qsort(sorted_copy, n, sizeof(const char *), compareStrings); /* เรียงลำดับภายใน  Array ใหม่ แล้วทำมาใส่ตัวของ sorted_copy โดยใช้คำสั่ง qsort */
printArray(sorted_copy,n); /* ผลลัพธ์ที่ได้ => apple banana fig kiwi */
free(sorted_copy); /* เพื่อคืนหน่วยความจำจากการสร้างมา */
```

**Java**
```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

List<String> words = Arrays.asList("kiwi", "apple", "fig", "banana");
List<String> sortedWords = words.stream().sorted().collect(Collectors.toList()); // ส่วนที่เหมือนกับ sort โดย สร้าง List ใหม่ชื่อ sortedWords จากการเรียงลำดับ
System.out.println(sortedWords); // ผลลัพธ์ที่ได้ => [apple, banana, fig, kiwi]
```

**Python**
```python
words = ["kiwi", "apple", "fig", "banana"]
new_words = sorted(words) # สร้างตัวเก็บ array มาใหม่โดยที่ไม่มีการเปลี่ยนแปลงค่าใน array ของตัว words โดยหลังจากนั้นจะทำการเรียงข้อมูลเพื่อมาเก็บใน array ของ new_words
print(f"New sorted list: {new_words}") # ผลลัพธ์ที่ได้ => ['apple', 'banana', 'fig', 'kiwi']
```

---

## 2. sort! (ที่จะทำการเปลี่ยนแปลงค่าเดิมใน array)

โดยการทำแบบนี้จะเป็นการเรียงค่าใน array โดยสามารถเรียงค่าผ่านทาง array ได้โดยตรง ผ่านการใช้ sort! ได้เลย ซึ่งจะแตกต่างจาก sort ตรงที่จะต้องมีตัว array อีกตัวที่คอยมารับค่า
โดยวิธีการใช้งานสามารถใช้งานได้ดังนี้ :

**Ruby**
```ruby
numbers = [3, 1, 5, 2, 4]
numbers.sort!
puts numbers  #ผลลัพธ์ที่ได้ => [1, 2, 3, 4, 5]
```

**C**
```c
const char *words1[] = {"kiwi", "apple", "fig", "banana"};
int n = sizeof(words1) / sizeof(words1[0]);
qsort(words1, n, sizeof(const char *), compareStrings); /* เรียงลำดับภายใน Array ใหม่ แล้วทำมาใส่ตัวของ word1 เข้าไปตรงๆ โดยใช้คำสั่ง qsort */
printArray("Sorted (in-place)", words1, n); /* ผลลัพธ์ที่ได้ => apple banana fig kiwi */
```

**Java**
```java
import java.util.Arrays;

String[] words = {"kiwi", "apple", "fig", "banana"};
Arrays.sort(words); // ส่วนที่เหมือนกับ sort! โดยมีการเรียงลำดับภายใน array ของ  words โดยตรง
System.out.println(Arrays.toString(words)); // ผลลัพธ์ที่ได้ => [apple, banana, fig, kiwi]
```

**Python**
```python
words = ["kiwi", "apple", "fig", "banana"]
words.sort() # ทำการเรียงค่าใน array ของ words โดยตรง
print(f"After sort():  {words_to_modify}") # ผลลัพธ์ที่ได้ => ['apple', 'banana', 'fig', 'kiwi']
```

---

## 3. sort\_by (ที่จะไม่ทำการเปลี่ยนแปลงค่าเดิมใน array โดยจะใช้  block ในการเปลี่ยนแปลงค่า)

โดยการทำแบบนี้จะเป็นการเรียงค่าใน array โดยใช้  block หรือเรียกอีกอย่างว่าเงื่อนไข ในการเรียงค่า โดยจะต้องมี array อีกตัวที่คอยรับค่าที่ผ่านการเรียงข้อมูลด้วย sort\_by ไว้แล้ว
โดยวิธีการใช้งานสามารถใช้งานได้ดังนี้ :

**Ruby**
```ruby
words = ["ruby", "is", "awesome"]
sorted_words = words.sort_by { |word| word.length }
puts sorted_words #ผลลัพธ์ที่ได้ => ["is", "ruby", "awesome"]
```

**C**
```c
const char *original4[] = {"kiwi", "apple", "fig", "banana"};
int n = sizeof(original4) / sizeof(original4[0]);
const char **sorted_by_copy = malloc(n * sizeof(const char *));
memcpy(sorted_by_copy, original4, n * sizeof(const char *));
qsort(sorted_by_copy, n, sizeof(const char *), compareByLength); /* เรียงลำดับ Array ใหม่โดยใช้เงื่อนไข compareByLength ที่เรียงผ่านการใช้ความยาวเป็นเกณฑ์ โดยจะเก็บเข้าไปใน sorted_by_copy */
printArray(sorted_by_copy, n); /* ผลลัพธ์ที่ได้ => fig kiwi apple banana */
free(sorted_by_copy); /* เพื่อคืนหน่วยความจำจากการสร้างมา */
```

**Java**
```java
import java.util.Arrays;
import java.util.List;
import java.util.Comparator;
import java.util.stream.Collectors;

List<String> words = Arrays.asList("kiwi", "apple", "fig", "banana");
List<String>sortedWords=words.stream().sorted(Comparator.comparingInt(String::length)).collect(Collectors.toList());         // ส่วนที่เหมือนกับ sort_by โดยมีการเรียงลำดับและจะมีการจดเก็บไว้ในตัวของ sortedWords โดยตรงร่วมกับการใช้เงื่อนไขความยาวของ String
```

**Python**
```python
people = [
    {'name': 'somsak', 'age': 35},
    {'name': 'malee', 'age': 28},
    {'name': 'piti', 'age': 42}
]
new_people_sorted_by_age = sorted(people, key=lambda person: person['age'])  # สร้างตัวเก็บ array มาใหม่โดยที่ไม่มีการเปลี่ยนแปลงค่าใน array ของตัว people โดยหลังจากนั้นจะทำการเรียงข้อมูลเพื่อมาเก็บใน array ของ new_people_sorted_by_age โดยทำการเรียงโดยใช้ age เป็นเกณฑ์
print("{new_people_sorted_by_age}") # ผลลัพธ์ที่ได้ => [{'name': 'malee', 'age': 28}, {'name': 'somsak', 'age': 35}, {'name': 'piti', 'age': 42}]
```

---

## 4. sort\_by! (ที่จะทำการเปลี่ยนแปลงค่าเดิมใน array โดยจะใช้  block ในการเปลี่ยนแปลงค่า)

โดยการทำแบบนี้จะเป็นการเรียงค่าใน array โดยใช้  block หรือเรียกอีกอย่างว่าเงื่อนไข โดยสามารถเรียงค่าผ่านทาง array ได้โดยตรงผ่านการใช้ sort\_by!  ได้เลย ซึ่งจะแตกต่างจาก sort\_by ตรงที่จะต้องมีตัว array อีกตัวที่คอยมารับค่า
โดยวิธีการใช้งานสามารถใช้งานได้ดังนี้ :

**Ruby**
```ruby
words = ["ruby", "is", "awesome"]
words.sort_by! { |word| word.length }
puts words #ผลลัพธ์ที่ได้ => ["is", "ruby", "awesome"]
```

```c
const char *words1[] = {"kiwi", "apple", "fig", "banana"};
int n = sizeof(words1) / sizeof(words1[0]);
qsort(words1, n, sizeof(const char *), compareByLength); /* เรียงลำดับ Array ใหม่โดยใช้เงื่อนไข compareByLength ที่เรียงผ่านการใช้ความยาวเป็นเกณฑ์ และเก็บเข้าไปยัง word1 โดยตรง */

printArray("Sorted by length", words1, n);
printf("\n");
```

**Java**
```java
import java.util.Arrays;
import java.util.Comparator;

String[] words = {"kiwi", "apple", "fig", "banana"};
Arrays.sort(words, Comparator.comparingInt(String::length)); // ส่วนที่เหมือนกับ sort_by! โดยมีการเรียงลำดับภายใน array ของ  words โดยตรงร่วมกับการใช้เงื่อนไขความยาวของ String
System.out.println(Arrays.toString(words)); // ผลลัพธ์ที่ได้ => [fig, kiwi, apple, banana]
```

**Python**
```python
people = [
    {'name': 'somsak', 'age': 35},
    {'name': 'malee', 'age': 28},
    {'name': 'piti', 'age': 42}
]
people.sort(key=lambda person: person['age']) # ทำการเรียงค่าใน array ของ people โดยตรงร่วมกับการใช้เงื่อนไขการเรียง array โดยใช้ age เรียงค่าข้อมูล
print("{people}")  # ผลลัพธ์ที่ได้ => [{'name': 'malee', 'age': 28}, {'name': 'somsak', 'age': 35}, {'name': 'piti', 'age': 42}]
```

---

โดยจะสรุปความแตกต่างแบบเป็นตารางเพื่อให้เข้าใจได้ง่ายแบบสรุปได้ดังนี้

| ภาษา       | วิธีที่ไม่เปลี่ยนแปลงค่า (non‑mutating)                                 | วิธีที่เปลี่ยนแปลงค่า (in‑place)                        | การใช้เงื่อนไข/คอมพาเรเตอร์                                             | หมายเหตุ (จากเนื้อหา)                                                         |
| ---------- | ----------------------------------------------------------------------- | ------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| **Ruby**   | `sort`, `sort_by` (คืน array ใหม่)                                      | `sort!`, `sort_by!` (แก้ไข array ตรงๆ)                  | `sort_by` / `sort_by!` ใช้ block เพื่อกำหนดเงื่อนไขการเรียง             | แยกชัดเจนระหว่างเมธอดที่เปลี่ยนค่าและไม่เปลี่ยนค่า                            |
| **C**      | คัดลอก array อันเดิม `qsort` กับคัดลอกข้อมูล (ตัวอย่างใช้ `memcpy` + `qsort`) | ใช้ `qsort` บน array เดิม (in‑place)                    | ต้องเขียนฟังก์ชันเปรียบเทียบ (เช่น `compareStrings`, `compareByLength`) | ภาษา low‑level ต้องจัดการหน่วยความจำเอง (malloc/free) และสร้าง comparator เอง |
| **Java**   | `stream().sorted()` สร้าง List ใหม่ (non‑mutating)                      | `Arrays.sort(array)` เรียงภายใน array โดยตรง (in‑place) | `Comparator` (เช่น `Comparator.comparingInt(String::length)`)           | มี API ทั้งแบบ stream และแบบ in‑place ผ่าน Arrays                             |
| **Python** | `sorted()` คืน list ใหม่ (non‑mutating)                                 | `list.sort()` เรียงใน list เดิม (in‑place)              | `key=` (เช่น `key=lambda x: x['age']`)                                  | เหมือนแนวคิดของ Ruby แต่ใช้ `key` แทน block ที่คืนค่าจัดลำดับ                 |

---

# แหล่งอ้างอิง

**Ruby**

* เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ array = [https://docs.ruby-lang.org/en/master/Array.html](https://docs.ruby-lang.org/en/master/Array.html) ไม่พบวันที่เขียนหน้าเว็บไซต์ สืบค้นเมื่อวันที่ 31 สิงหาคม พ.ศ. 2568
* เว็บไซต์ทางการสำหรับการค้นหาในเรี่องของ sorting array = [https://docs.ruby-lang.org/en/master/Array.html#method-i-sort](https://docs.ruby-lang.org/en/master/Array.html#method-i-sort) ไม่พบวันที่เขียนหน้าเว็บไซต์ สืบค้นเมื่อวันที่ 31 สิงหาคม พ.ศ. 2568
* หนังสือสำหรับการค้นหาในเรี่องของ sorting array

  1. Programming Ruby 1.9 & 2.0 – The Pragmatic Programmers' Guide หน้า 437  =  [https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Programming%20Ruby%201.9%20%26%202.0%20-%20The%20Pragmatic%20Programmers'%20Guide%20-%20Fourth%20Edition.pdf](https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Programming%20Ruby%201.9%20%26%202.0%20-%20The%20Pragmatic%20Programmers'%20Guide%20-%20Fourth%20Edition.pdf) เขียน ณ วันที่ 15 มิถุนายน พ.ศ. 2556 สืบค้นเมื่อวันที่ 31 สิงหาคม พ.ศ. 2568
  2. The Ruby Programming Language หน้า 338 = [https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/The%20Ruby%20Programming%20Language.pdf](https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/The%20Ruby%20Programming%20Language.pdf) เขียน ณ วันที่ 24 กุมภาพันธ์ 2536 สืบค้นเมื่อวันที่ 31 สิงหาคม พ.ศ. 2568
  3. Ruby Recipes – A Problem-Solution Approach หน้า 84 = [https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Ruby%20Recipes%20-%20A%20Problem-Solution%20Approach.pdf](https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Ruby%20Recipes%20-%20A%20Problem-Solution%20Approach.pdf) เขียน ณ วันที่ 8 ธันวาคม พ.ศ. 2559 สืบค้นเมื่อวันที่ 31 สิงหาคม พ.ศ. 2568

**Java**

* เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ array = [https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html) ไม่พบวันที่เขียนหน้าเว็บไซต์ สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568
* เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ sort = [https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Arrays.html#sort(java.lang.Object%5B%5D)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Arrays.html#sort%28java.lang.Object%5B%5D%29)
* เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ sorted = [https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/stream/Stream.html#sorted()](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/stream/Stream.html#sorted%28%29)
* เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ Stream = [https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/stream/Stream.html#sorted(java.util.Comparator)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/stream/Stream.html#sorted%28java.util.Comparator%29)

**C**

* เว็บไซต์ของ geeksforgeeks สำหรับการค้นหาการใช้งาน qsort = [https://www.geeksforgeeks.org/c/c-program-to-sort-an-array-in-ascending-order/](https://www.geeksforgeeks.org/c/c-program-to-sort-an-array-in-ascending-order/) ถูกแก้ไขล่าสุด ณ วันที่ 12 กรกฎาคม พ.ศ.2568 สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568
* เว็บไซต์ของ cppreference สำหรับการค้นหาการใช้งาน strcmp สำหรับการทำฟังก์ชันการเปรียบเทียบของ sort = [https://en.cppreference.com/w/c/string/byte/strcmp](https://en.cppreference.com/w/c/string/byte/strcmp) ไม่พบวันที่เขียนหน้าเว็บไซต์ สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568
* เว็บไซต์ของ cppreference การใช้งาน strlen สำหรับการทำฟังก์ชันการเปรียบเทียบของ sort\_by = [https://en.cppreference.com/w/c/string/byte/strlen](https://en.cppreference.com/w/c/string/byte/strlen) ไม่พบวันที่เขียนหน้าเว็บไซต์ สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568

**Python**

* เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ sorting array = [https://docs.python.org/3/howto/sorting.html](https://docs.python.org/3/howto/sorting.html) ถูกแก้ไขล่าสุด ณ วันที่ 2 กันยายน พ.ศ.2568 สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568
* เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ sorted = [https://docs.python.org/3/library/functions.html#sorted](https://docs.python.org/3/library/functions.html#sorted) ถูกแก้ไขล่าสุด ณ วันที่ 2 กันยายน พ.ศ.2568 สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568

---
