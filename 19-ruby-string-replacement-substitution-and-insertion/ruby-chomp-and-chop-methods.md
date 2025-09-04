# Ruby chomp and chop Methods

## Chomp และ Chop Methods คืออะไร?
Chomp และ Chop Methods ใน Ruby คือเมธอดที่ใช้ในการตัดอักขระตัวสุดท้ายใน 'String' ออก

แต่!! Methods ทั้งสองตัว __ทำงานไม่เหมือนกัน!!!__

### Chomp Method

Chomp method คือเมธอดที่ตัดอักขระตัวสุดท้ายออกเมื่อตัวนั้นคือตัวคั่นบรรทัด ซึ่งจะคืนค่าเป็น 'String' ตัวใหม่ที่คัดลอกมาจากตัวมันเองโดยตัดอักขระตัวสุดท้ายออก

**Syntax**
```Ruby
str.chomp(separator = $/)
```

วิธีการใช้

**แบบที่ 1 เมื่อไม่ได้ระบุ separator**

หากไม่ได้ระบุ separator Default ของ Chomp จะกำหนด separator = $/ และจะตัดอักขระคั่นบรรทัด (New line) หรือ Carriage return ออก เช่น "\n", "\r" หรือ "\r\n" 2 ตัวคู่กัน

```Ruby
"Umiri".chomp        # => "Umiri"
"Umiri\r".chomp      # => "Umiri"
"Umiri\n".chomp      # => "Umiri"
"Umiri\r\n".chomp    # => "Umiri"      # \r\n ถูกตัดออก
"Umiri\n\r".chomp    # => "Umiri\n\r"  # \n\r ไม่ถูกตัดออก
"Umiri\t".chomp      # => "Umiri\t"    # \t ไม่ถูกตัดออก
```

**แบบที่ 2 เมื่อ separator = '' (empty string)**

หากระบุ separator เป็น empty string Chomp จะตัดอักขระคั่นบรรทัดออก (New line) เช่น "\n" หรือ "\r\n" (แต่ไม่ตัด "\r" ออก)

```Ruby
"Taki\n".chomp('')               # => "Taki"
"Taki\n\n\n\n".chomp('')         # => "Taki"
"Taki\r\n\r\n\r\n".chomp('')     # => "Taki"
"Taki\r".chomp('')               # => "Taki\r"
"Taki\r\r\r".chomp('')           # => "Taki\r\r\r"
"Taki\n\r\n\r\n\r".chomp('')     # => "Taki\n\r\n\r\n\r"
```

**แบบที่ 3 เมื่อกำหนด separator เอง**

```Ruby
"Mortis".chomp('tis')        # => "Mor"
"Mortistis.chomp('tis')      # => "Mortis"
"Mortis".chomp('Mor')        # => "Mortis"
"Mortis".chomp('Mut')        # => "Mortis"
"Mortis\t".chomp("\t")        # => "Mortis"      # ว้าวว ลบ "\t" ด้วยวิธีนี้ได้!
"Mortis\r".chomp("\r")       # => "Mortis"      # ลบ "\r" ด้วยวิธีนี้ก็ได้เหมือนกัน แต่ทำไปทำไม ใช้แบบที่ 1 ดีกว่า...
```

**Example 1**

```Ruby
name = "Umiri\n"

puts name.chomp
puts "----------"
puts name + ". Dumb dork"
```

**Output**
```Ruby
Umiri
----------
Umiri
. Dumb dork    # name ไม่เปลี่ยนแปลง ยังมีการคั่นบรรทัดเช่นเดิม
```

**Example 2**

```Ruby
puts "What is your name?"

name = gets    # สมมติว่ารับเป็น Taki

puts name + ". You're the only one who found me."
puts "---------------------------------------"

puts name.chomp + ". You're the only one who found me."
```

**Output**
```Ruby
What is your name?
Taki
Taki
. You're the only one who found me.      # name ไม่เปลี่ยนแปลง ยังมีการคั่นบรรทัดเช่นเดิม
---------------------------------------
Taki. You're the only one who found me.  # ไม่มีการคั่นบรรทัดแล้ว
```

และเมธอด Chomp ก็มีอีกรูปแบบ ซึ่งนั่นก็คือ...

#### Chomp!

Chomp! คือเมธอดที่ตัดอักขระตัวสุดท้ายออกเมื่อตัวนั้นคือตัวคั่นบรรทัดเช่นกัน ทำงานเหมือน chomp แต่! **เป็นการแก้ไข String ตัวเดิม**
* Return ตัวมันเองเมื่อมีอักขระที่ถูกนำออก </br>
* Return nil (nothing) เมื่อไม่มีอะไรให้ลบ </br>

**Example**

```Ruby
name = "Umiri\n"
name2 = "Mutsumi"

name.chomp!
name2.chomp!

puts name
puts name2
```

**Output**
```Ruby
Umiri    # แก้ไขค่าใน name โดยตรง
         # return nil (ว่างเปล่า)
```

### Chop Method

Chop method คือเมธอดที่ตัดอักขระตัวสุดท้ายของ String ออกไปและจะคืนค่าเป็น 'String' ตัวใหม่ที่คัดลอกมาจากตัวมันเองโดยตัดอักขระตัวสุดท้ายออก
* ลบ "\r\n" ออก เมื่อ 2 ตัวนี้อยู่คู่กัน

**Syntax**
```Ruby
str.chop
```
**Example 1**
```Ruby
"Umiri".chop      # => "Umir"
"Umiri\n".chop    # => "Umiri"
"Umiri\r".chop    # => "Umiri"
"Umiri\r\n".chop  # => "Umiri"
```

**Example 2**

```Ruby
name = "Umiri\n"
puts name + "Dork."
puts "---------------------------------------"
puts name.chop
```

**Output**
```Ruby
Umiri
Dork.
---------------------------------------
Umiri
```

และ Chop ก็มีอีกรูปแบบเช่นกัน!

#### Chop!

ทำงานเหมือน Chop ทุกประการ **แต่!**
* ลบอักขระตัวสุดท้ายออกจาก String ตัวเดิมโดยตรง
* Return ตัวมันเองถ้ามีอักขระที่ถูกนำออก
* Return nil (nothing) ถ้าไม่มีอักขระใดถูกนำออก

**Example**

```Ruby
name = "Umiri\n"
name2 = ''

puts name.chop!
puts name2.chop!

puts name
puts name2
```

**Output**
```Ruby
Umiri
         # return nil (ว่างเปล่า)
Umiri    # แก้ไขค่าใน name โดยตรง
         # return nil (ว่างเปล่า)
```


**_ถ้าต้องการแค่ลบอักขระคั่นบรรทัดตัวสุดท้ายของ String เท่านั้น เมธอด Chomp เป็นทางเลือกที่ดีกว่า..._**


## เปรียบเทียบ Chomp and Chop Methods กับภาษาอื่น ๆ

### ภาษา C

น่าเสียดายที่ในภาษา C ไม่มี built-in method แบบ Chomp หรือ Chop เลยสำหรับการตัดอักขระตัวสุดท้าย เพราะ String ในภาษา C เป็น array ของ char แต่เราสามารถประยุกต์ใช้ Function ที่ภาษา C มี ในการทำ Chomp หรือ Chop ได้

#### การ Chomp และ Chomp! ในภาษา C

สามารถทำได้โดย... **ใช้ Function strcspn() !!!**

**strcspn()**

> strcspn() คือ ฟังก์ชันการหาจำนวนตัวอักษรที่ถูกพบก่อนตัวอักษรที่กำหนด อยู่ในไลบารี <string.h>

**Syntax**
```C
strcspn(const char *str1, const char *str2)
```
* str1: String ที่ต้องการค้นหา
* str2: อักขระที่ต้องการหาตำแหน่งใน str1

**Example**

```C
char Name[50] = "Timoris\n";
printf(Name);
// แก้ไข Name โดยตรง ตรงกับเมธอด Chomp!
Name[strcspn(Name, "\n")] = 0;         // ใส่ค่า 0 ('\0') ที่ตำแหน่งของ "\n"
printf("%s. I do not fear being afraid", Name);
// แต่ถ้าอยากทำ Chomp อาจจะต้องสร้าง buffer มาเก็บ Name ก่อน แล้วค่อยทำการลบอักขระ
```

**Output**
```C
Timoris
Timoris. I do not fear being afraid         # เย้ ไม่มีการคั่นบรรทัดแล้ว!
```
> [!TIP]
> ถ้าต้องการตัด "\r" ออกไปด้วย สามารถทำได้โดย
> ```C
> Name[strcspn(Name, "\r\n")] = 0;
> //หรือ
> Name[strcspn(Name, "\r")] = 0;


#### การ Chop ในภาษา C

น่าเสียดายที่ภาษา C ไม่มีอะไรที่เข้าเค้าเมธอด Chop ใน Ruby เลย ดังนั้นเราจึงต้องทำเองแบบ manual...

**Example**

```C
char Name[50] = "Timoris";
size_t len = strlen(Name);
if(len > 0) {
    Name[len-1] = '\0';
}
printf("%s", Name);
```
**Output**
```C
Timori         # ตัดอักขระสุดท้ายออกไปด้วยวิธีแสนยุ่งยาก
```

### ภาษา Java

ใน Java string เป็น immutable (แก้ไขค่าเดิมไม่ได้) จึงไม่สามารถทำ Chomp! และ Chop! ได้ แต่โชคดีที่ใน Java มีเมธอด Chomp และ Chop อยู่ด้วย ถึงแม้เมธอดจะไม่ใช่เมธอดมาตรฐานที่มีอยู่ทั่วไปใน Class หลักภาษา Java เพราะเป็นเมธอดที่พบได้ในไลบารีนอก นั่นก็คือ Apache Commons Lang ใน StringUtils class แต่ก็สามารถใช้ได้เพราะมีหน้าที่ลบอักขระขึ้นวรรคใหม่ที่อยู่ท้ายสุดของ String เหมือนกัน 

#### เมธอด Chomp ในภาษา Java

เมธอดนี้จะลบอักขระขึ้นวรรคใหม่ที่อยู่ตำแหน่งท้ายสุดของ String ได้แก่ "\n", "\r" หรือ "\r\n" สามารถศึกษาเพิ่มเติมได้ที่เอกสารนี้ [Apache Commons Lang](https://commons.apache.org/proper/commons-lang/apidocs/org/apache/commons/lang3/StringUtils.html#chomp(java.lang.String,java.lang.String))

**Syntax**
```Java
> แบบที่ 1
> chomp(String str)
> แบบที่ 2
> chomp(String str, String separator)
```

> [!Warning]
> **ย้ำอีกครั้ง!!** StringUtils อยู่ใน Apache Commons Lang3 ไม่ใช่ Java มาตรฐาน
ดังนั้นก่อนจะใช้งาน ต้องดาวน์โหลดและเพิ่ม library เข้า classpath ก่อน

**แบบที่ 1 chomp(String str) เมื่อไม่ได้ระบุ separator**
หากไม่ได้ระบุ separator Default ของ Chomp จะกำหนด separator = $/ และจะตัดอักขระคั่นบรรทัด (New line) หรือ Carriage return ออก เช่น "\n", "\r" หรือ "\r\n" 2 ตัวคู่กัน

```Java
 StringUtils.chomp(null)                   // => null
 StringUtils.chomp("")                     // => ""
 StringUtils.chomp("Umiri \r")             // => "Umiri "
 StringUtils.chomp("Umiri\n")              // => "Umiri"
 StringUtils.chomp("Umiri\r\n")            // => "Umiri"
 StringUtils.chomp("Umiri\r\n\r\n")        // => "Umiri\r\n"
 StringUtils.chomp("Umiri\n\r")            // => "Umiri\n"
 StringUtils.chomp("Umiri\n\rTaki")        // => "Umiri\n\rTaki"
 StringUtils.chomp("\r")                   // => ""
 StringUtils.chomp("\n")                   // => ""
 StringUtils.chomp("\r\n")                 // => ""
```

**แบบที่ 2 chomp(String str, String separator) เมื่อระบุ separator**
หากระบุ separator Chomp จะตัดอักขระนั้นออก หากอยู่ตำแหน่งสุดท้ายของ String
```Java
 StringUtils.chomp(null, *)                                // => null
 StringUtils.chomp("", *)                                  // => ""
 StringUtils.chomp("trustworthy", "worthy")                // => "trust"
 StringUtils.chomp("trustworthy", "no")                    // => "trustworthy"
 StringUtils.chomp("trustworthy", "trustworthy")           // => ""
 StringUtils.chomp("trustworthy ", "trustworthy")          // =>= "trustworthy "
 StringUtils.chomp(" trustworthy", "trustworthy")          // => " "
 StringUtils.chomp("trustworthy", "trustworthyyyy")        // => "trustworthy"
 StringUtils.chomp("trustworthy", "")                      // => "trustworthy"
 StringUtils.chomp("trustworthy", null)                    // => "trustworthy"
```

**Example**

```Java
// import library ก่อน
import org.apache.commons.lang3.StringUtils;

// main
String name = "Umiri\n";
String chompped = StringUtils.chomp(name);
System.out.println(chopped + ". You're not trustworthy");
```
**Output**
```Java
Umiri. You're not trustworthy
```


#### เมธอด Chop ในภาษา Java

เมธอด Chop จะนำอักขระตัวสุดท้ายของ String ออก
Syntax

```Java
> แบบที่ 1
> chop(String str)
> แบบที่ 2
> chop(String str, String separator)
```

**Example**

```Java
 StringUtils.chop(null)          // => null
 StringUtils.chop("")            // => ""
 StringUtils.chop("abc \r")      // => "abc "
 StringUtils.chop("abc\n")       // => "abc"
 StringUtils.chop("abc\r\n")     // => "abc"
 StringUtils.chop("abc")         // => "ab"
 StringUtils.chop("abc\nabc")    // => "abc\nab"
 StringUtils.chop("a")           // => ""
 StringUtils.chop("\r")          // => ""
 StringUtils.chop("\n")          // => ""
 StringUtils.chop("\r\n")        // => ""
```

แต่จริง ๆ แล้ว... Java มีวิธีที่ง่ายกว่านั้นโดยไม่ต้องดาวน์โหลดไลบารีเพิ่มเติมในการทำหน้าที่เหมือนเมธอด Chomp หรือ Chop ซึ่งใช้เมธอดที่ Java มีอยู่แล้ว

 **การ Chomp ใน Java**
```Java
String name = "Soyo\n";

// ทำงานเหมือน chomp
name = name.replaceAll("[\r\n]+$", "");

System.out.println(name + "rin");
```
 **Output**
```Java
Soyorin
```

 **การ Chop ใน Java**
```Java
String name = "Soyo\n";

// ทำงานเหมือน chomp
name = name.substring(0, name.length() - 1); // ใส่ค่า 0 ('\0') ที่ตำแหน่งสุดท้ายของ String

System.out.println(name + "rin");
```
 **Output**
```Java
Soyorin
```

เมธอดเหล่านี้ก็สามารถประยุกต์ใช้ให้ทำหน้าที่คล้ายกับเมธอด Chomp และ Chop ของ Ruby ได้!


### ภาษา Python

ใน Python ไม่มีเมธอด Chomp หรือ Chop โดยตรง แต่ก็มีวิธีการทำงานที่ใกล้เคียงโดยใช้เมธอดใน Python

#### การ Chomp ใน Python

วิธีที่ใกล้เคียงที่สุดคือการใช้ rstrip() ซึ่งเมธอดนี้จะทำหน้าที่ลบอักขระหรือช่องว่างด้านท้ายทั้งหมดของ String โดย default คือช่องว่าง

Syntax
```Python
str.rstrip(characters)
> characters คือชุดอักขระที่ต้องการลบ (ไม่ระบุก็ได้) ค่าเริ่มต้นคือช่องว่าง
```

**Example**

```Python
name = "UmiriInwza\n"
chompped = name.rstrip()
chompped2 = name.rstrip('Iwnaz\n')
print("Name: " + name)
print("Chomp1: " + chompped + ", handsome and cool")
print("Chomp2: " + chompped2 + ", handsome and cool")
```

**Output**
```Python
Name: UmiriInwza

Chomp1: UmiriInwza, handsome and cool
Chomp2: Umiri, handsome and cool
```

#### การ Chop ใน Python


วิธีที่ใกล้เคียงที่สุดคือการใช้ slicing (แต่ถ้ามี "\r\n" วิธีการนี้จะไม่สามารถลบทั้งคู่ได้ทันที ต้องเพิ่ม condition)

**Example**


```Python
name = "Yahata\n"
print(name[:-1])
```

**Output**
```Python
Yahata        # ลบอักขระท้ายสุดออก
```

ส่วนเมธอด Chomp! และ Chop! ใน Python นั้นไม่มี เพราะใน Python string เป็น immutable (แก้ไขค่าไม่ได้) ทุกเมธอดที่เปลี่ยนค่า String จะคืนค่าใหม่เสมอ


# Video Presentation


# Slide Presentation


# Reference
#### Ruby
- Ruby Documentation. (n.d.). String class documentation. https://docs.ruby-lang.org/en/master/String.html
- Udemy Blog. (n.d.). Ruby chomp. https://blog.udemy.com/ruby-chomp/
- Techotopia. (n.d.). Ruby string replacement, substitution and insertion: Ruby chomp and chop methods. https://www.techotopia.com/index.php/Ruby_String_Replacement,_Substitution_and_Insertion#Ruby_chomp_and_chop_Methods

#### C
- Stack Overflow. (n.d.). Removing trailing newline character from fgets input. https://stackoverflow.com/questions/2693776/removing-trailing-newline-character-from-fgets-input
- GeeksforGeeks. (n.d.). strcspn() in C. https://www.geeksforgeeks.org/c/strcspn-in-c/

#### Java
- Apache Commons. (n.d.). StringUtils (Apache Commons Lang3 API). https://commons.apache.org/proper/commons-lang/apidocs/org/apache/commons/lang3/StringUtils.html
- How.dev. (n.d.). What is StringUtils.chomp in Java? https://how.dev/answers/what-is-stringutilschomp-in-java
- GeeksforGeeks. (n.d.). substring() in Java. https://www.geeksforgeeks.org/java/substring-in-java/
#### Python
- DCRub. (n.d.). Python string rstrip() method. https://www.dcrub.com/python-string-rstrip-method
