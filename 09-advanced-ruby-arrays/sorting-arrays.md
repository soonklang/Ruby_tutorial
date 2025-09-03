# Sorting Arrays (การเรียงข้อมูลใน Array)

Sorting Arrays คือการเรียงข้อมูลใน Array โดยสามารถเรียงข้อมูลให้เป็นไปตามที่เรากำหนดได้ว่าอยากให้เรียงข้อมูล array ให้เรียงในรูปแบบที่ต้องการ

โดย Ruby จะมีการ Sorting ทั้งหมด 4 รูปแบบแบบชัดเจนได้ดังนี้ :

1. sort (ที่จะไม่ทำการเปลี่ยนแปลงค่าเดิมใน Array)
2. sort! (ที่จะทำการเปลี่ยนแปลงค่าเดิมใน Array)
3. sort_by (ที่จะไม่ทำการเปลี่ยนแปลงค่าเดิมใน Array โดยจะใช้ Block ในการเปลี่ยนแปลงค่า)
4. sort_by! (ที่จะทำการเปลี่ยนแปลงค่าเดิมใน Array โดยจะใช้ Block ในการเปลี่ยนแปลงค่า)

ก่อนจะเริ่มการเปรียบเทียบกับภาษาอื่นเนื่องจากภาษา C ไม่มีฟังก์ชันที่สนับสนุนกับการใช้ Sorting Array มากเท่าที่ควร เนื่องจากภาษา C เป็นภาษาระดับสูง (High-Level)เป็นสาเหตุที่ทำให้ต้องเน้นในเรื่องของประสิทธิภาพและการควบคุมหน่วยความจำที่ต้องจัดการด้านการเขียนภาษาเอง โดยทำให้มีแค่ฟังก์ชันแค่ qsort ทำให้ต้องมีการสร้าง ฟังก์ชันเปรียบเทียบเพื่อให้สามารถนำภาษา C มาเปรียบเทียบกับภาษา Ruby ได้โดยตัวของ Code สำหรับการใช้งานสำหรับมาเปรียบเทียบจะมีรายละเอียดดังนี้

**ฟังก์ชั่นการเปรียบเทียบที่ไว้ใช้สำหรับภาษา C**

```c
#include <stdio.h>    /* ใช้สำหรับ I/O เช่น printf */
#include <stdlib.h>   /* ใช้สำหรับ qsort, malloc, free */
#include <string.h>   /* ใช้สำหรับ strcmp, strlen, memcpy */

int compareStrings(const void *a, const void *b) {
    const char **str_a = (const char **)a; /*แปลง (cast) พอยน์เตอร์ void *a ให้กลายเป็นพอยน์เตอร์ไปยัง char */
    const char **str_b = (const char **)b; /*แปลง (cast) พอยน์เตอร์ void *b ให้กลายเป็นพอยน์เตอร์ไปยัง char */
    return strcmp(*str_a, *str_b);
} /* ฟังก์ชันเปรียบเทียบ String ตามลำดับตัวอักษร ซึ่งหลักการทำงานจะคล้ายกับตัว Sort ของ Ruby */

int compareByLength(const void *a, const void *b) {
    const char **str_a = (const char **)a;
    const char **str_b = (const char **)b;
    int len_a = strlen(*str_a);/* เปลี่ยน pointer ให้เป็น string โดย str_a จะชี้ไปยัง string ตัวที่ 1*/
    int len_b = strlen(*str_b);/* เปลี่ยน pointer ให้เป็น string โดย str_b จะชี้ไปยัง string ตัวที่ 2*/
    return (len_a > len_b) - (len_a < len_b); /* เทคนิคการคืนค่า -1, 0, หรือ 1 */
} /* ฟังก์ชันเปรียบเทียบ String ตามความยาวตัวอักษร ซึ่งหลักการทำงานจะคล้ายกับตัว sort_by ของ Ruby */

void printArray(const char *arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%s ", arr[i]);
    }
    printf("\n");
} /* ตัวสำหรับการพิมพ์ Array ให้เข้าใจง่ายๆ */
```

---

## 1. sort (ที่จะไม่ทำการเปลี่ยนแปลงค่าเดิมใน Array)

โดยการทำแบบนี้จะเป็นการเรียงลำดับค่าใน Array โดยจะต้องมี Array อีกตัวหนึ่งในการเก็บค่า Array อีกตัวที่ได้ทำการเรียงข้อมูลผ่านการ sort ไว้แล้ว
โดยวิธีการใช้งานสามารถทำได้ดังนี้ :

**Ruby**

```ruby
numbers = [3, 1, 5, 2, 4]
sorted_numbers = numbers.sort #จะทำการเรียงข้อมูลจะน้อยไปหามาก
puts sorted_numbers  #ผลลัพธ์ที่ได้ => [1, 2, 3, 4, 5]
```

**C**

```c
const char *original1[] = {"kiwi", "apple", "fig", "banana"};
int n = sizeof(original1) / sizeof(original1[0]); /*หาว่า Array มีสมาชิกกี่ตัว โดยไม่ต้องนับเอง*/
const char **sorted_copy = malloc(n * sizeof(const char *)); /* จะเป็นการสร้าง Array เพื่อมาเตรียมพร้อมสำหรับการใส่ค่าที่เรียงไว้ */
memcpy(sorted_copy, original1, n * sizeof(const char *)); /* ทำการคัดลอกข้อมูลจาก original1 มาใส่ยังตัว sorted_copy */
qsort(sorted_copy, n, sizeof(const char *), compareStrings); /* เรียงลำดับภายใน Array ใหม่ แล้วทำมาใส่ตัวของ sorted_copy โดยใช้คำสั่ง qsort */
printArray(sorted_copy,n); /* ผลลัพธ์ที่ได้ => apple banana fig kiwi */
free(sorted_copy); /* เพื่อคืนหน่วยความจำจากการสร้างมาเพื่อลดการทำงานที่มากเกินไป */
```

**Java**

```java
import java.util.Arrays; //ใช้สำหรับ Array
import java.util.List; //ใช้สำหรับ สร้างตัวแปร List
import java.util.stream.Collectors; //ใช้สำหรับทำงานกับ Stream API

List<String> words = Arrays.asList("kiwi", "apple", "fig", "banana");
List<String> sortedWords = words.stream().sorted().collect(Collectors.toList()); // ส่วนที่เหมือนกับ sort โดย สร้าง List ใหม่ชื่อ sortedWords จากการเรียงลำดับ
System.out.println(sortedWords); // ผลลัพธ์ที่ได้ => [apple, banana, fig, kiwi]
```

**Python**

```python
words = ["kiwi", "apple", "fig", "banana"]
new_words = sorted(words) # สร้างตัวเก็บ Array มาใหม่โดยที่ไม่มีการเปลี่ยนแปลงค่าใน Array ของตัว words โดยหลังจากนั้นจะทำการเรียงข้อมูลเพื่อมาเก็บใน Array ของ new_words
print(f"New sorted list: {new_words}") # ผลลัพธ์ที่ได้ => ['apple', 'banana', 'fig', 'kiwi']
```

---

## 2. sort! (ที่จะทำการเปลี่ยนแปลงค่าเดิมใน Array)

โดยการทำแบบนี้จะเป็นการเรียงค่าใน Array โดยสามารถเรียงค่าผ่านทาง Array ได้โดยตรง ผ่านการใช้ sort! ได้เลย ซึ่งจะแตกต่างจาก sort ตรงที่จะต้องมีตัว Array อีกตัวที่คอยมารับค่า
โดยวิธีการใช้งานสามารถทำได้ดังนี้ :

**Ruby**

```ruby
numbers = [3, 1, 5, 2, 4]
numbers.sort!
puts numbers  #ผลลัพธ์ที่ได้ => [1, 2, 3, 4, 5]
```

**C**

```c
const char *words1[] = {"kiwi", "apple", "fig", "banana"};
int n = sizeof(words1) / sizeof(words1[0]);/*หาว่า Array มีสมาชิกกี่ตัว โดยไม่ต้องนับเอง*/
qsort(words1, n, sizeof(const char *), compareStrings); /* เรียงลำดับภายใน Array ใหม่ แล้วทำมาใส่ตัวของ word1 เข้าไปตรงๆ โดยใช้คำสั่ง qsort */
printArray("Sorted (in-place)", words1, n); /* ผลลัพธ์ที่ได้ => apple banana fig kiwi */
```

**Java**

```java
import java.util.Arrays; //ใช้สำหรับ Array

String[] words = {"kiwi", "apple", "fig", "banana"};
Arrays.sort(words); // ส่วนที่เหมือนกับ sort! โดยมีการเรียงลำดับภายใน Array ของ  words โดยตรง
System.out.println(Arrays.toString(words)); // ผลลัพธ์ที่ได้ => [apple, banana, fig, kiwi]
```

**Python**

```python
words = ["kiwi", "apple", "fig", "banana"]
words.sort() # ทำการเรียงค่าใน Array ของ words โดยตรง
print(f"After sort():  {words_to_modify}") # ผลลัพธ์ที่ได้ => ['apple', 'banana', 'fig', 'kiwi']
```

---

## 3. sort_by (ที่จะไม่ทำการเปลี่ยนแปลงค่าเดิมใน Array โดยจะใช้ Block ในการเปลี่ยนแปลงค่า)

โดยการทำแบบนี้จะเป็นการเรียงค่าใน Array โดยใช้ Block หรือเรียกอีกอย่างว่าเงื่อนไข ในการเรียงค่า โดยจะต้องมี Array อีกตัวที่คอยรับค่าที่ผ่านการเรียงข้อมูลด้วย sort_by ไว้แล้ว
โดยวิธีการใช้งานสามารถทำได้ดังนี้ :

**Ruby**

```ruby
words = ["ruby", "is", "awesome"]
sorted_words = words.sort_by { |words| word.length }#ทำการเรียงค่าภายใน Array แล้วบันทึกค่าลงไปใน Array ของ sorted_words โดยเรียงด้วยการใช้ข้อมูลจาก words ในการเรียงข้อมูลที่มาจาก words
puts sorted_words #ผลลัพธ์ที่ได้ => ["is", "ruby", "awesome"]
```

**C**

```c
const char *original4[] = {"kiwi", "apple", "fig", "banana"};
int n = sizeof(original4) / sizeof(original4[0]);/*หาว่า Array มีสมาชิกกี่ตัว โดยไม่ต้องนับเอง*/
const char **sorted_by_copy = malloc(n * sizeof(const char *)); /* สร้าง array เพื่อเก็บ string จำนวน n ตัว */
memcpy(sorted_by_copy, original4, n * sizeof(const char *));/* คัดลอกข้อมูลจาก array ของ original4 ไปยัง array ของ sorted_by_copy */
qsort(sorted_by_copy, n, sizeof(const char *), compareByLength); /* เรียงลำดับ Array ใหม่โดยใช้เงื่อนไข compareByLength ที่เรียงผ่านการใช้ความยาวเป็นเกณฑ์ โดยจะเก็บเข้าไปใน sorted_by_copy */
printArray(sorted_by_copy, n); /* ผลลัพธ์ที่ได้ => fig kiwi apple banana */
free(sorted_by_copy); /* เพื่อคืนหน่วยความจำจากการสร้างมา */
```

**Java**

```java
import java.util.Arrays; //ใช้สำหรับ Array
import java.util.List; //ใช้สำหรับ สร้างตัวแปร List
import java.util.Comparator; //ใช้สำหรับ Comparator เพื่อการเปรียบเทียบ
import java.util.stream.Collectors; //ใช้สำหรับทำงานกับ Stream API

List<String> words = Arrays.asList("kiwi", "apple", "fig", "banana");
List<String>sortedWords=words.stream().sorted(Comparator.comparingInt(String::length)).collect(Collectors.toList()); //ส่วนที่เหมือนกับ sort_by โดยมีการเรียงลำดับและจะมีการจัดเก็บไว้ในตัวของ sortedWords โดยตรงร่วมกับการใช้เงื่อนไขความยาวของ String
```

**Python**

```python
people = [
    {'name': 'somsak', 'age': 35},
    {'name': 'malee', 'age': 28},
    {'name': 'piti', 'age': 42}
]
new_people_sorted_by_age = sorted(people, key=lambda person: person['age']) # สร้างตัวเก็บ Array มาใหม่โดยที่ไม่มีการเปลี่ยนแปลงค่าใน Array ของตัว people โดยหลังจากนั้นจะทำการเรียงข้อมูลเพื่อมาเก็บใน Array ของ new_people_sorted_by_age โดยทำการเรียงโดยใช้ age เป็นเกณฑ์
print("{new_people_sorted_by_age}") # ผลลัพธ์ที่ได้ => [{'name': 'malee', 'age': 28}, {'name': 'somsak', 'age': 35}, {'name': 'piti', 'age': 42}]
```

---

## 4. sort_by! (ที่จะทำการเปลี่ยนแปลงค่าเดิมใน Array โดยจะใช้ Block ในการเปลี่ยนแปลงค่า)

โดยการทำแบบนี้จะเป็นการเรียงค่าใน Array โดยใช้ block หรือเรียกอีกอย่างว่าเงื่อนไข โดยสามารถเรียงค่าผ่านทาง Array ได้โดยตรงผ่านการใช้ sort_by! ได้เลย ซึ่งจะแตกต่างจาก sort_by ตรงที่จะต้องมีตัว Array อีกตัวที่คอยมารับค่า
โดยวิธีการใช้งานสามารถทำได้ดังนี้ :

**Ruby**

```ruby
words = ["ruby", "is", "awesome"]
words.sort_by! { |words| words.length } #ทำการเรียงค่าภายใน Array แล้วบันทึกค่าลงไปใน Array ได้เลยโดยตรง โดยเรียงด้วยการใช้ข้อมูลจาก words ในการเรียงข้อมูล
puts words #ผลลัพธ์ที่ได้ => ["is", "ruby", "awesome"]
```

**C**

```c
const char *words1[] = {"kiwi", "apple", "fig", "banana"};
int n = sizeof(words1) / sizeof(words1[0]);/*หาว่า Array มีสมาชิกกี่ตัว โดยไม่ต้องนับเอง*/
qsort(words1, n, sizeof(const char *), compareByLength); /* เรียงลำดับ Array ใหม่โดยใช้เงื่อนไข compareByLength ที่เรียงผ่านการใช้ความยาวเป็นเกณฑ์ และเก็บเข้าไปยัง word1 โดยตรง */

printArray(words1, n);
printf("\n");
```

**Java**

```java
import java.util.Arrays; //ใช้สำหรับ Array
import java.util.Comparator; //ใช้สำหรับ Comparator เพื่อการเปรียบเทียบ

String[] words = {"kiwi", "apple", "fig", "banana"};
Arrays.sort(words, Comparator.comparingInt(String::length)); // ส่วนที่เหมือนกับ sort_by! โดยมีการเรียงลำดับภายใน Array ของ words โดยตรงร่วมกับการใช้เงื่อนไขความยาวของ String
System.out.println(Arrays.toString(words)); //ผลลัพธ์ที่ได้ => [fig, kiwi, apple, banana]
```

**Python**

```python
people = [
    {'name': 'somsak', 'age': 35},
    {'name': 'malee', 'age': 28},
    {'name': 'piti', 'age': 42}
]
people.sort(key=lambda person: person['age']) # ทำการเรียงค่าใน Array ของ people โดยตรงร่วมกับการใช้เงื่อนไขการเรียง Array โดยใช้ age เรียงค่าข้อมูล
print("{people}")  # ผลลัพธ์ที่ได้ => [{'name': 'malee', 'age': 28}, {'name': 'somsak', 'age': 35}, {'name': 'piti', 'age': 42}]
```

---

โดยจะสรุปความแตกต่างแบบเป็นตารางเพื่อให้เข้าใจได้ง่ายแบบสรุปได้ดังนี้

| ภาษา       | วิธีที่ไม่เปลี่ยนแปลงค่า (non‑mutating)                                       | วิธีที่เปลี่ยนแปลงค่า (in‑place)                        | การใช้เงื่อนไข/คอมพาเรเตอร์                                             | หมายเหตุ (จากเนื้อหา)                                                          |
| ---------- | ----------------------------------------------------------------------------- | ------------------------------------------------------- | ----------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **Ruby**   | `sort`, `sort_by` (คืน Array ใหม่)                                            | `sort!`, `sort_by!` (แก้ไข Array ตรงๆ)                  | `sort_by` / `sort_by!` ใช้ block เพื่อกำหนดเงื่อนไขการเรียง             | แยกชัดเจนระหว่างเมธอดที่เปลี่ยนค่าและไม่เปลี่ยนค่า                             |
| **C**      | คัดลอก Array อันเดิม `qsort` กับคัดลอกข้อมูล (ตัวอย่างใช้ `memcpy` + `qsort`) | ใช้ `qsort` บน array เดิม (in‑place)                    | ต้องเขียนฟังก์ชันเปรียบเทียบ (เช่น `compareStrings`, `compareByLength`) | ภาษา High‑level ต้องจัดการหน่วยความจำเอง (malloc/free) และสร้าง comparator เอง |
| **Java**   | `stream().sorted()` สร้าง List ใหม่ (non‑mutating)                            | `Arrays.sort(Array)` เรียงภายใน Array โดยตรง (in‑place) | `Comparator` (เช่น `Comparator.comparingInt(String::length)`)           | มี API ทั้งแบบ stream และแบบ in‑place ผ่าน Arrays                              |
| **Python** | `sorted()` คืน list ใหม่ (non‑mutating)                                       | `list.sort()` เรียงใน list เดิม (in‑place)              | `key=` (เช่น `key=lambda x: x['age']`)                                  | เหมือนแนวคิดของ Ruby แต่ใช้ `key` แทน block ที่คืนค่าหลังจัดลำดับ              |

---

---

## ตารางเปรียบเทียบ

| วิธีการ      | Ruby                                                  | C                                                                    | Java                                               | Python                                                              | ข้อดี                                                               | ข้อเสีย                                                                |
| ------------ | ----------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------- | -------------------------------------------------------------------- |
| **sort**     | `numbers.sort` คืนค่า array ใหม่ โดยไม่เปลี่ยนค่าเดิม | ใช้ `qsort` กับ array ที่คัดลอกมาจากของเดิม (ผ่าน `malloc + memcpy`) | ใช้ `stream().sorted()` สร้าง List ใหม่            | ใช้ `sorted(list)` คืนค่า list ใหม่                                 | - ไม่กระทบข้อมูลเดิม<br>- ปลอดภัย                                   | - ต้องมี array/list ใหม่เพิ่มขึ้นมา<br>- กินหน่วยความจำมากกว่าเล็กน้อย |
| **sort!**    | `numbers.sort!` เรียงใน array เดิม                    | ใช้ `qsort` กับ array เดิมโดยตรง                                     | ใช้ `Arrays.sort()` เรียงใน array เดิม             | ใช้ `list.sort()` เรียงใน list เดิม                                 | - ประหยัดหน่วยความจำ<br>- ไม่ต้องสร้าง array ใหม่                   | - ทำให้ข้อมูลเดิมหายไป<br>- อาจผิดพลาดถ้าเผลอแก้ไขข้อมูลต้นฉบับ        |
| **sort_by**  | `words.sort_by {                                      | w                                                                    | w.length }` คืนค่า array ใหม่ โดยไม่เปลี่ยนค่าเดิม | ใช้ `qsort` กับ array ที่คัดลอกมา แล้วใช้ฟังก์ชัน `compareByLength` | ใช้ `stream().sorted(Comparator.comparingInt(...))` สร้าง List ใหม่ | ใช้ `sorted(list, key=...)` คืนค่า list ใหม่                           | - เลือกเงื่อนไขการเรียงได้ยืดหยุ่น<br>- ข้อมูลเดิมไม่ถูกแก้ไข | - ต้องมี array/list ใหม่<br>- กินหน่วยความจำเพิ่ม                    |
| **sort_by!** | `words.sort_by! {                                     | w                                                                    | w.length }` เรียงใน array เดิม                     | ใช้ `qsort` โดยตรงกับ array เดิม และกำหนด comparator เอง            | ใช้ `Arrays.sort(array, Comparator.comparingInt(...))`              | ใช้ `list.sort(key=...)` เรียงใน list เดิม                             | - ยืดหยุ่น (กำหนดเงื่อนไขได้)<br>- ไม่ต้องสร้าง array ใหม่    | - ข้อมูลเดิมถูกเปลี่ยน<br>- อาจเสี่ยงหากต้องการเก็บค่าต้นฉบับไว้ด้วย |

---

# แหล่งอ้างอิง

**Ruby**

- เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ array = [https://docs.ruby-lang.org/en/master/Array.html](https://docs.ruby-lang.org/en/master/Array.html) ไม่พบวันที่เขียนหน้าเว็บไซต์ สืบค้นเมื่อวันที่ 31 สิงหาคม พ.ศ. 2568
- เว็บไซต์ทางการสำหรับการค้นหาในเรี่องของ sorting array = [https://docs.ruby-lang.org/en/master/Array.html#method-i-sort](https://docs.ruby-lang.org/en/master/Array.html#method-i-sort) ไม่พบวันที่เขียนหน้าเว็บไซต์ สืบค้นเมื่อวันที่ 31 สิงหาคม พ.ศ. 2568
- หนังสือสำหรับการค้นหาในเรี่องของ sorting array

  1. Programming Ruby 1.9 & 2.0 – The Pragmatic Programmers' Guide หน้า 437 = [https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Programming%20Ruby%201.9%20%26%202.0%20-%20The%20Pragmatic%20Programmers'%20Guide%20-%20Fourth%20Edition.pdf](https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Programming%20Ruby%201.9%20%26%202.0%20-%20The%20Pragmatic%20Programmers'%20Guide%20-%20Fourth%20Edition.pdf) เขียน ณ วันที่ 15 มิถุนายน พ.ศ. 2556 สืบค้นเมื่อวันที่ 31 สิงหาคม พ.ศ. 2568
  2. The Ruby Programming Language หน้า 338 = [https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/The%20Ruby%20Programming%20Language.pdf](https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/The%20Ruby%20Programming%20Language.pdf) เขียน ณ วันที่ 24 กุมภาพันธ์ 2536 สืบค้นเมื่อวันที่ 31 สิงหาคม พ.ศ. 2568
  3. Ruby Recipes – A Problem-Solution Approach หน้า 84 = [https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Ruby%20Recipes%20-%20A%20Problem-Solution%20Approach.pdf](https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Ruby%20Recipes%20-%20A%20Problem-Solution%20Approach.pdf) เขียน ณ วันที่ 8 ธันวาคม พ.ศ. 2559 สืบค้นเมื่อวันที่ 31 สิงหาคม พ.ศ. 2568

**Java**

- เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ array = [https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html) ไม่พบวันที่เขียนหน้าเว็บไซต์ สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568
- เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ sort = [https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Arrays.html#sort(java.lang.Object%5B%5D)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Arrays.html#sort%28java.lang.Object%5B%5D%29)
- เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ sorted = [https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/stream/Stream.html#sorted()](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/stream/Stream.html#sorted%28%29)
- เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ Stream = [https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/stream/Stream.html#sorted(java.util.Comparator)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/stream/Stream.html#sorted%28java.util.Comparator%29)

**C**

- เว็บไซต์ของ geeksforgeeks สำหรับการค้นหาการใช้งาน qsort = [https://www.geeksforgeeks.org/c/c-program-to-sort-an-array-in-ascending-order/](https://www.geeksforgeeks.org/c/c-program-to-sort-an-array-in-ascending-order/) ถูกแก้ไขล่าสุด ณ วันที่ 12 กรกฎาคม พ.ศ.2568 สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568
- เว็บไซต์ของ cppreference สำหรับการค้นหาการใช้งาน strcmp สำหรับการทำฟังก์ชันการเปรียบเทียบของ sort = [https://en.cppreference.com/w/c/string/byte/strcmp](https://en.cppreference.com/w/c/string/byte/strcmp) ไม่พบวันที่เขียนหน้าเว็บไซต์ สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568
- เว็บไซต์ของ cppreference การใช้งาน strlen สำหรับการทำฟังก์ชันการเปรียบเทียบของ sort_by = [https://en.cppreference.com/w/c/string/byte/strlen](https://en.cppreference.com/w/c/string/byte/strlen) ไม่พบวันที่เขียนหน้าเว็บไซต์ สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568

**Python**

- เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ sorting array = [https://docs.python.org/3/howto/sorting.html](https://docs.python.org/3/howto/sorting.html) ถูกแก้ไขล่าสุด ณ วันที่ 2 กันยายน พ.ศ.2568 สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568
- เว็บไซต์ทางการสำหรับการค้นหาในเรื่องของ sorted = [https://docs.python.org/3/library/functions.html#sorted](https://docs.python.org/3/library/functions.html#sorted) ถูกแก้ไขล่าสุด ณ วันที่ 2 กันยายน พ.ศ.2568 สืบค้นเมื่อวันที่ 2 กันยายน พ.ศ. 2568

---
