###

# Changing a Section of a String
 >  เป็นการใช้เมธอดแก้ไขค่าในสตริง โดยที่ไม่ได้เกิดจากการสร้างสตริงใหม่ เนื่องจาก String ในภาษา Ruby มีคุณสมบัติ mutable คือ อนุญาตให้แก้ไขค่าในสตริงได้โดยตรง
  #### โดยมีวิธีการพื้นฐาน ดังนี้ 
   
## สารบัญ Table of Contents

  - [String Slices](#string-slices)
  - [Substitution Methods](#substitution-methods)
    - [String#sub](#stringsub)
    - [String#sub!](#stringgsub)
    - [String#gsub](#stringgsub) 
    - [String#gsub!](#stringgsub)
 - [เทียบกับภาษาอื่นๆ](#%E0%B9%80%E0%B8%97%E0%B8%B5%E0%B8%A2%E0%B8%9A%E0%B8%81%E0%B8%B1%E0%B8%9A%E0%B8%A0%E0%B8%B2%E0%B8%A9%E0%B8%B2%E0%B8%AD%E0%B8%B7%E0%B9%88%E0%B8%99%E0%B9%86)

## วิธีการ Changing a Section of a String 
## String Slices 
   >เป็นวิธีการที่ใช้ในการแก้ไขค่าในสตริง โดยใช้สัญลักษณ์[] เพื่อระบุช่วงของตัวอักษรที่ต้องการจะแก้ไข
#### ตัวอย่าง
   ```ruby
myString = "Silpakorn University"
puts 'myString'[0] 
 # เริ่มนับจากตัวอักษรแรก เป็นตำแหน่งที่ 0
```
<details>
   <summary>Output</summary>

 > S

</details>

  > หากไม่มี เครื่องหมาย(=) จะยังไม่ใช่การแก้ไขค่า แต่เป็นการเลือกแสดงผลค่าออกมา
#### ตัวอย่าง
  > แก้ไขค่าในสตริงโดยการกำหนดคำที่ต้องการจะแก้ไข
```ruby
myString = "Silpakorn University"
myString["University"] = "Educator"
puts myString

```
<details>
   <summary>Output</summary>

 > Silpakorn Educator

</details>
 
#### ตัวอย่าง
>แก้ไขโดยอิงจากค่าตำแหน่งของตัวอักษรในสตริง

   ```ruby
myString = "Silpakorn University"
myString[9] = " is " 
puts myString

```
<details>
   <summary>Output</summary>

  > Silpakorn is University

</details>
   

 

#### ตัวอย่าง
> แก้ไขโดยอิงจากค่าตำแหน่งของตัวอักษรในสตริง

```ruby
myString = "Silpakorn University"
myString[9...20] = " is The Best "
puts myString
#นับตั้งแต่ตัวอักษรตัวที่ 9 ถึง ตัวที่ 20 
```
<details>
   <summary>Output</summary>
   
   > Silpakorn is The Best 

</details>



## Substitution Methods
   > เป็นเมธอดสำหรับแทนที่ค่าบางส่วนในสตริงตามเงื่อนไขที่เรากำหนด
   
   ### แบ่งออกเป็น 4 วิธี ได้แก่
   - String#sub 
   - String#sub!
   - String#gsub
   - String#gsub!
## String#sub 
>เมธอดสำหรับแทนที่ตำแหน่งแรกที่เจอ หากไม่เจอจะไม่แทนที่เลย และจะคืนค่าเป็นสตริงใหม่(สตริงเดิมจะไม่ถูกแก้ไข)

ตัวอย่าง

```ruby
myString = "I like to walk around my house"
puts myString.sub(/[l]/, '*') #ถ้าเจอ 'l' ตัวแรกจะแทนค่าเป็น '*'
puts myString.sub('like','love') #ถ้าเจอ 'like'จะแทนค่าเป็น 'love'
puts myString.sub('eat','love')
puts myString
```
<details>
   <summary>Output</summary>
   
>I *ike to walk around my house </br>
>I love to walk around my house </br>
>I like to walk around my house     #ไม่เจอคำว่า 'eat' สตริงจึงไม่เปลี่ยนแปลง </br>
>I like to walk around my house     #ไม่มีการเปลี่ยนแปลงสตริงเดิม </br>

</details>


## String#sub!
>เมธอดสำหรับแทนที่ตำแหน่งแรกที่เจอ หากไม่เจอจะไม่แทนที่เลยและคืนค่าเป็น nil แต่ถ้าแทนที่ได้จะคืนค่าเป็นสตริงที่ถูกแก้ไข 

 ตัวอย่าง
 ```ruby
myString = "I like to walk around my house" 
puts myString.sub!(/[l]/, '*') 
puts myString.sub!('like','love')
puts myString.sub!('eat','love')
puts myString
```
<details>
   <summary>Output</summary>
   
>I *ike to walk around my house  </br>
>(                                                  ) #คืนค่าเป็น nil   </br>
>(                                                  ) #คืนค่าเป็น nil   </br>
>I *ike to walk around my house #สตริงเดิมที่ถูกเปลี่ยนแปลง </br>

</details>
    
      
## String#gsub
>เมธอดสำหรับแทนที่ทุกตำแหน่งที่เจอ หากไม่เจอจะไม่แทนที่เลย และจะคืนค่าเป็นสตริงใหม่(สตริงเดิมจะไม่ถูกแก้ไข)

ตัวอย่าง
 ```ruby
myString = "I like to walk around my house"
puts myString.gsub(/[il]/, '*') #ถ้าเจอ 'il' ทุกตัวจะแทนค่าเป็น '*'
puts myString.gsub('like','love')
puts myString.gsub('eat','love')
puts myString
```
<details>
   <summary>Output</summary>
   
>I **ke to wa *k around my house </br>
>I love to walk around my house </br>
>I like to walk around my house </br>
>I like to walk around my house </br>

</details>
    
## String#gsub!
>เมธอดสำหรับแทนที่ทุกตำแหน่งที่เจอ หากไม่เจอจะไม่แทนที่เลยและคืนค่าเป็น nil แต่ถ้าแทนที่ได้จะคืนค่าเป็นสตริงที่ถูกแก้ไข 

ตัวอย่าง

```ruby
myString = "I like to walk around my house"
puts myString.gsub!(/[il]/, '*') #ถ้าเจอ 'il' ทุกตัวจะแทนค่าเป็น '*'
puts myString.gsub!('like','love')
puts myString.gsub!('eat','love')
puts myString
```
<details>
   <summary>Output</summary>

>I **ke to wa * k around my house </br>
>(                                                  ) #คืนค่าเป็น nil   </br>
>(                                                  ) #คืนค่าเป็น nil   </br>
>I **ke to wa*k around my house #สตริงเดิมถูกเปลี่ยนแปลง </br>

</details>
      

## เทียบกับภาษาอื่นๆ
## C
> สตริงในภาษาซีมีคุณสมบัติเป็น mutable เช่นเดียวกัน แต่เมธอดสำเร็จรูป ต้องใช้การเขียน loop หรือ ฟังก์ชัน แทน

ตัวอย่าง

```c
#include <stdio.h>
#include <string.h>

int main() {
    char mystring[] = "Silpakorn University";

    // Slice
    mystring[1] = 'a';
    printf("%s\n", mystring);
    
    // Substitution (replace 'i' with '*')
    for (int i = 0; i < strlen(mystring); i++) {
        if (mystring[i] == 'i') mystring[i] = '*';
    }
    printf("%s\n", mystring); 
}
```
<details>
   <summary>Output</summary>

>Salpakorn University </br>
>Salpakorn Un* vers* ty </br>


</details>


## Python
> สตริงในภาษาไพธอนมีคุณสมบัติเป็น 'immutable' คือ ไม่อนุญาตให้มีการแก้ไขโดยตรง ต้องสร้างสตริงใหม่เสมอ

ตัวอย่าง

```python
mystring1 = "Silpakorn University";

# ทำ Slice ไม่ได้
# mystring1[1] = 'a'; จะ error
# ทำได้โดยสร้างสตริงใหม่
mystring2 = mystring1[:1] + "a" + mystring1[2:]
print(mystring2)  

# Substitution ไพธอนมีเมธอด replace()
print(mystring1.replace("i", "*"))

```
<details>
   <summary>Output</summary>

>Salpakorn University </br>
>S * lpakorn Un*vers*ty </br>

</details>





## Java
>สตริงในภาษาจาวามีคุณสมบัติเป็น 'immutable' เช่นเดียวกัน จะต้องอาศัยการสร้างสตริงใหม่
>
ตัวอย่าง


```java
public class Main {
    public static void main(String[] args) {
        String mystring1 = "Silpakorn University";

        // ทำ Slice ไม่ได้  #
        // mystring1[1] = 'a'; จะ error
        // สร้างใหม่แทน
        String mystring2 = mystring1.substring(0,1) + "a"+mystring1.substring(2);
        System.out.println(mystring2); 
        
        // Substitution ใช้เมธอด replace()
        System.out.println(mystring1.replace("i", "*"));  }}
```
<details>
   <summary>Output</summary>

>Salpakorn University </br>
>S* lpakorn Un* vers* ty </br>
 
</details>

คลิปวิดีโอการนำเสนอ : [watch on youtube](https://youtu.be/WYVeaN4HimU?si=sYP7kc0u34clKxp0)

ไฟล์การนำเสนอ : [Canva](https://www.canva.com/design/DAGywD4Tvq0/8TKjKMbw5d-cRDdepQNW-Q/edit?utm_content=DAGywD4Tvq0&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)
               [OneDrive](https://silpakorn-my.sharepoint.com/:b:/g/personal/pulkasem_p_su_ac_th/Ef2bvCUDnHNCpWZ_0K1g48oBK5Tep-r0FmwehxiQ5yCJxQ?e=auUAvg)

## Reference 
String. (n.d.). In Ruby-Doc.org. สืบค้นเมื่อ 29 สิงหาคม 2025, จาก Ruby Reference , จาก https://ruby-doc.org/3.4.1/String.html </br>
Mandal, M. (2010). Ruby recipes: A problem-solution approach. Apress. https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Ruby%20Recipes%20-%20A%20Problem-Solution%20Approach.pdf </br>
Cooper, P. (2016). Beginning Ruby: From novice to professional (3rd ed.). Apress.https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Beginning%20Ruby%20-%20From%20Novice%20to%20Professional%20-%20Third%20Edition.pdf </br>
Thomas, D., Fowler, C., & Hunt, A. (2013). Programming Ruby 1.9 & 2.0: The pragmatic programmers’ guide (4th ed.). Pragmatic Bookshelf.https://github.com/maniramakumar/the-best-ruby-books/blob/master/books/Programming%20Ruby%201.9%20%26%202.0%20-%20The%20Pragmatic%20Programmers'%20Guide%20-%20Fourth%20Edition.pdf </br>


