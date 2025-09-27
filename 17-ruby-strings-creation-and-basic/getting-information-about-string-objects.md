---
description: นฤดม ศรีปัญญา 660710604
icon: function
cover: >-
  https://images.unsplash.com/photo-1551122089-4e3e72477432?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwzfHxydWJ5fGVufDB8fHx8MTc1NjQ2OTQ3Nnww&ixlib=rb-4.1.0&q=85
coverY: -269.2090773809524
---

# Getting Information About String Objects

## String Objects Information

> (เกือบ) ทุกอย่างใน Ruby เป็น Object ซึ่งหนึ่งในนั้นก็คือ String แล้วใน Object ของ String จะมี Method มากมายที่เก็บข้อมูล (Information) เกี่ยวกับ String ที่เราสามารถเรียกใช้เมธอดนั้นเพื่อนำข้อมูลออกมาใช้ได้

{% hint style="success" %}
ในบทความนี้ เราจะยกตัวอย่าง Methods ที่นิยมใช้กันส่วนใหญ่และบางตัวอย่างเท่านั้น ซึ่งอาจไม่ครอบคลุมตัวอย่างทั้งหมดใน Ruby ท่านสามารถศึกษาเพิ่มเติมได้ที่ [Reference](getting-information-about-string-objects.md#reference) ด้านล่างได้เลย
{% endhint %}

***

## <mark style="color:$danger;">ตัวอย่าง</mark> Method

### .length หรือ .size

String ทั้ง 2 เมธอดนี้ จะคืนค่า<mark style="color:yellow;">จำนวนตัวอักษรในข้อความ</mark>นั้นออกมาเหมือนกัน ไม่มีความแตกต่างใดๆ

{% tabs %}
{% tab title="Ruby" %}
<pre class="language-ruby"><code class="lang-ruby"><strong>puts "こんにちは".length 
</strong># Output: 5
</code></pre>
{% endtab %}

{% tab title="Java" %}
```java
System.out.println("こんにちは".length());
// Output: 5
```
{% endtab %}

{% tab title="Python" %}
```python
print(len("こんにちは"))
# Output: 5
```
{% endtab %}

{% tab title="C" %}
```c
#include <string.h>
printf("%zu",strlen("こんにちは"));
// Output: 5
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
ในภาษา Python หรือ C นั้น จะไม่มี Method ที่่ทำงานเหมือน _.length_ ใน String Object ดังนั้นจึงต้องเรียกใช้ฟังก์ชัน\
จากข้างนอกที่เตรียมไว้แล้วหรือ Import library เข้ามาเอง
{% endhint %}

#### เปรียบเทียบ <mark style="color:$danger;">Ruby</mark> กับภาษาโปรแกรมอื่นๆ

| Ruby                                                                                                      | Java                                                      | Python                                                                  | C                                                                                                         |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- | ----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| ใช้ Method _<mark style="color:$danger;">.length</mark>_ หรือ _<mark style="color:$danger;">.size</mark>_ | ใช้ Method _<mark style="color:purple;">.length()</mark>_ | ใช้ Built-in Function แทนคือ _<mark style="color:yellow;">len()</mark>_ | ใช้ Function ชื่อ _<mark style="color:blue;">strlen()</mark>_ ที่ ถูก import จาก library ชื่อ \<string.h> |

### .empty?

เพื่อเช็คว่าในข้อความนั้น<mark style="color:yellow;">มีจำนวนตัวอักษรหรือไม่</mark>และจะคืนค่ากลับมาเป็น <mark style="color:yellow;">Boolean</mark> ถ้าไม่มีตัวอักษรใดเลย จะคืนค่าเป็น <mark style="color:$success;">True</mark> ถ้ามีอย่างน้อยหนึ่งตัว จะคืนค่าเป็น <mark style="color:$danger;">False</mark>

{% tabs %}
{% tab title="Ruby" %}
<pre class="language-ruby"><code class="lang-ruby"><strong>puts "こんにちは".empty?
</strong># Output: false
</code></pre>
{% endtab %}

{% tab title="Java" %}
```java
System.out.println("こんにちは".isEmpty());
// Output: false
```
{% endtab %}

{% tab title="Python" %}
```python
print(len("こんにちは") == 0)
# Output: False
```
{% endtab %}

{% tab title="C" %}
```c
#include <string.h>
printf("%d", strlen("こんにちは") == 0);
// Output: 0
// Which means false
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
ในภาษา Python และ C นั้นจะไม่มี Method ให้เรียกใช้ได้โดยตรงกับ Object หรือก็คือเราจะต้องเรียกใช้ Method \
จากภายนอก หรือเราสามารถประยุกต์จาก Method อื่นๆ ขึ้นมาเองก็ได้เช่นกัน
{% endhint %}

#### เปรียบเทียบ <mark style="color:$danger;">Ruby</mark> กับภาษาโปรแกรมอื่นๆ

| Ruby                                                      | Java                                                       | Python                                                                                                                                                                                                       | C                                                                                                  |
| --------------------------------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- |
| ใช้ Method  _<mark style="color:$danger;">.empty?</mark>_ | ใช้ Method _<mark style="color:purple;">.isEmpty()</mark>_ | <mark style="color:yellow;">ไม่มีทั้ง</mark> Method ให้เรียกใช้โดยตรงและ Built-in Method เราสามารถประยุกต์ใช้ _<mark style="color:yellow;">len()</mark>_ <mark style="color:yellow;">== 0</mark> หรือไม่ ได้ | เหมือนกับ Python เราสามารถประยุกต์ใช้ _<mark style="color:blue;">strlen() == 0</mark>_ หรือไม่ ได้ |

### .index(\<substring | regexp> \*, offset = 0)

สำหรับ<mark style="color:yellow;">ค้นหาค่าตำแหน่ง</mark> (ค่าดัชนี) ของข้อความที่ต้องการหาและจะคืนค่ากลับมาเป็นค่าของตำแหน่งนั้น

{% include "../.gitbook/includes/code.md" %}

{% tabs %}
{% tab title="Ruby" %}
<pre class="language-ruby"><code class="lang-ruby"><strong>puts "こんにちは".index('ん')
</strong># Output: 1
</code></pre>
{% endtab %}

{% tab title="Java" %}
```java
System.out.println("こんにちは".indexOf("ん"));
// Output: 1
```
{% endtab %}

{% tab title="Python" %}
```python
print("こんにちは".find('ん'))
# Output: 1
```
{% endtab %}

{% tab title="C" %}
```c
#include <stdio.h>
#include <string.h>

int main() {
  char str[] = "hello";
  char *ptr = strchr(str, 'e');

  if (ptr != NULL)
    printf("%d", ptr-str);
  
  return 1;
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
ในภาษา C นั้น จะยุ่งยากเล็กน้อยคือ ไม่มี Method ที่ทำงานเหมือนกับ .Index ของ Ruby แต่ก็พอมีฟังก์ชันให้เรียกใช้\
ได้เหมือนกันโดยจะต้องทำงาน #include \<string.h> เข้ามา ซึ่งฟังก์ชันที่จะนำมาประยุกต์ใช้ ได้แก่ strchr(), strstr() \
ทั้งสองฟังก์ชันต่างกันที่ parameters คือจะรับเป็น char หรือ string (array of char) ทั้งสองฟังก์ชันจะคืนค่าเป็น \
pointer ที่ชี้ไปยังตำแหน่งแรกของตัวที่เราต้องการจะค้นหา ทำให้เราต้องนำข้อความที่เริ่มตั้งแต่ตัวอักษรที่ pointer ชี้อยู่\
ไปลบ ข้อความเดิม เพื่อให้ได้ค่าดัชนีของตัวอักษรนั้น&#x20;
{% endhint %}

#### เปรียบเทียบ <mark style="color:$danger;">Ruby</mark> กับภาษาโปรแกรมอื่นๆ

| Ruby                                                      | Java                                                        | Python                                                  | C                                                                                                                                      |
| --------------------------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| ใช้ Method _<mark style="color:$danger;">.index()</mark>_ | ใช้ Method _<mark style="color:purple;">.indexOf()</mark>_  | ใช้ Method _<mark style="color:yellow;">.find()</mark>_ | <mark style="color:blue;">ไม่มี</mark> เราอาจต้อง #include \<string.h> แล้วเรียกใช้ _strchr()_ หรือ _strstr()_ ตาม Argument ที่ใส่ลงไป |

***

## Presentation

[Slide](https://drive.google.com/file/d/1qkIIPchUuOCMlktPdvk2_42YsDEhYVFa/view?usp=sharing)
[Video](https://drive.google.com/file/d/1BOv75qHRS-OppdT0SgJVi_69Xhrih8k9/view?classId=9b29eaeb-1c1f-4e8b-b901-572b4811be7f&assignmentId=99f8e016-2dff-4668-a3a8-10ee39590798&submissionId=48375fd9-185e-6b62-af24-ad95e70579cb)
***

## Reference

{% embed url="https://www.techotopia.com/index.php/Ruby_Strings_-_Creation_and_Basics" %}

{% embed url="https://www.freecodecamp.org/news/ruby-string-methods-explained-length-empty-and-other-built-in-methods/" %}

{% embed url="https://ruby-doc.org/3.4.1/String.html#class-String-label-What-27s+Here" %}

{% embed url="https://docs.python.org/3/library/functions.html#len" fullWidth="false" %}

{% embed url="https://docs.oracle.com/javase/8/docs/api/java/lang/String.html" %}

{% embed url="https://sourceware.org/glibc/manual/2.42/html_mono/libc.html#String-Length" %}

