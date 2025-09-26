# Case Insensitive String Comparisons
**Case Insensitive String Comparisons** คือการเปรียบเทียบข้อความ (String) โดยไม่สนใจตัวอักษรพิมพ์เล็กหรือพิมพ์ใหญ่ ในภาษา Ruby สามารถทำได้ดังนี้ 
> ใช้ casecmp()

casecmp() เป็นเมธอดที่ใช้เปรียบเทียบข้อความเหมือนกับ <=> โดยการเช็คอักขระของข้อความทางด้านซ้ายและข้อความทางด้านขวาว่าเหมือนกันทุกตัวหรือไม่ จะคืนค่าเป็น 
- -1 ถ้าข้อความทางซ้าย น้อยกว่า ข้อความทางขวา 
- 0 ถ้าข้อความทางซ้าย เท่ากับ ข้อความทางขวา 
- 1 ถ้าข้อความทางซ้าย มากกว่า ข้อความทางขวา 
- nil ถ้าไม่สามารถเปรียบเทียบกันได้ เนื่องจากมีข้อความใดข้อความหนึ่งหรือทั้งสองข้อความไม่ใช่ String
  
**Example**
```
str1 = "Silpakorn"
str2 = "SILPAKORN"
puts str1.casecmp(str2)
```
output => 0 casecmp() จะเช็คอักขระทีละตัวโดยไม่คำนึงถึงตัวพิมพ์เล็ก-พิมพ์ใหญ่
```
str1 = “Silpakorn”
str2 = “Silpakorn University”
puts str1.casecmp(str2)
```
output => -1 เพราะว่า str1 น้อยกว่า str2
```
str1 = “Jar”
str2 = “Car”
puts str1.casecmp(str2) 
```
output => 1 เพราะ ‘J’ มีค่ามากกว่า ‘C’ 

> ใช้ casecmp?()

casecmp?() เป็นการเปรียบเทียบว่าข้อความเหมือนกันหรือไม่ โดยไม่สนว่าเป็นตัวพิมพ์เล็กหรือพิมพ์ใหญ่ จะคืนค่าเป็น 

- true ถ้าข้อความที่เปรียบเทียบเหมือนกันทุกตัวอักษร 

- false ถ้าข้อความที่เปรียบเทียบไม่เหมือนกัน หรือมีจุดที่ต่างกัน 

- nil ถ้าข้อความไม่สามารถเปรียบเทียบกันได้ หรือมีข้อความข้อใดข้อความหนึ่ง หรือทั้งสองข้อความไม่ใช่ String
  
**Example**
```
str1 = “SILPAKORN”
str2 = “silpakorn”
puts str1.casecmp?(str2) 
```
output => true เพราะ str1 และ str2 เหมือนกันทุกตัวอักษร 
```
str1 = “comment”
str2 = “comments”
puts str1.casecmp?(str2) 
```
output => false เพราะ str1 และ str2 มีจุดที่ต่างกัน 
```
str1 = “comment”
str2 = 123
puts str1.casecmp?(str2) 
```
output => nil เพราะ str2 ไม่เป็น String 

## Case Insensitive String Comparisions ใน ภาษา Python, Java และ C 

### Python

ในภาษา Python นิยมใช้ lower() หรือ upper() กับข้อความก่อนแล้วจึงใช้ == เปรียบเทียบข้อความ 
และ casefold() ที่จะแปลงข้อความให้เป็นตัวพิมพ์เล็กก่อนแล้วจึงใช้ == เปรียบเทียบข้อความ มีประโยชน์สำหรับการเปรียบเทียบสตริงที่มีอักขระพิเศษหรือ Unicode 

>ใช้ lower()/upper() 

**Example**
```
str1 = “PYTHON”
str2 = “Python”
if str1.lower() == str2.lower():
  print(“equal”)
else:
  print(“not equal”) 
```
output => equal 

>ใช้ casefold() 

**Example**
```
str1 = "straße"
str2 = "STRASSE"
if str1.casefold() == str2.casefold():
  print(“equal”)
else:
  print(“not equal”) 
```
output => equal เนื่องจาก ẞ ในภาษาเยอรมันมีความหมายเดียวกันกับ ss ในภาษาอังกฤษ 

### Java 

ในภาษา Java จะใช้ equalsIgnoreCase( ) 
จะคืนค่าเป็น 
- true หากข้อความมีความยาวเท่ากันและเหมือนกันทุกตัวอักษร
- false หากข้อความมีความยาวไม่เท่ากันและไม่เหมือนกันทุกตัวอักษร

**Example**
```
public class Main {
  public static void main(String[] args) {
    String str1 = "Silpakorn";
    String str2 = "silpakorn";
    String str3 = "Silpakorn University";
    System.out.print(str1.equalsIgnoreCase(str2)+" ");
    System.out.println(str2.equalsIgnoreCase(str3)); 
  }
}
```
output => true false 

### C 

> ใช้ strcasecmp()

- โดยจะต้อง include **<strings.h>** 
- ถ้า strcasecmp() มีค่าเท่ากับ 0 หมายความว่าข้อความทั้งสองเหมือนกัน


**Example**
```
#include <stdio.h>
#include <strings.h>
int main() {
  char *a = "Silpakorn";
  char *b = "SilPakorn";
  if (strcasecmp(a, b) == 0) {
      printf("equal");
  } else {
      printf("not equal");
  }
      return 0;
}
```
output => equal 

# Presentation
[slide](https://docs.google.com/presentation/d/1bs3tXOc9rWy8w49l-Y00uwyh0OB6S_lqHPzg9z5e6E0/edit?usp=sharing)
# Video
[video](https://youtu.be/h5GTLeyOMm8)
### Reference 

>Ruby
  
APIdock. (ม.ป.ป). casecmp. สืบค้นเมื่อ 2 กันยายน 2568, จาก https://apidock.com/ruby/v2_6_3/String/casecmp 

Ruby Language Documentation. (ม.ป.ป). Symbol#casecmp. สืบค้นเมื่อ 2 กันยายน 2568, จาก https://docs.ruby-lang.org/en/master/Symbol.html#method-i-casecmp 

Ruby Language Documentation. (ม.ป.ป). Symbol#casecmp?. สืบค้นเมื่อ 2 กันยายน 2568, จาก https://docs.ruby-lang.org/en/master/Symbol.html#method-i-casecmp-3F 

Techotopia. (2559). Ruby string concatenation and comparison. สืบค้นเมื่อ 2 กันยายน 2568, จาก https://www.techotopia.com/index.php/Ruby_String_Concatenation_and_Comparison

>Python
   
Geeksforgeeks. (15 กรกฎาคม 2568). Case-insensitive string comparison in Python. สืบค้นเมื่อ 2 กันยายน 2568, จาก https://www.geeksforgeeks.org/python/case-insensitive-string-comparison-in-python/ 

Ioflood. (12 สิงหาคม 2567). Case-Insensitive String Comparisons. สืบค้นเมื่อ 2 กันยายน 2568, จาก https://ioflood.com/blog/using-python-to-compare-strings-methods-and-tips 

>Java
  
Oracle. (ม.ป.ป). equalsIgnoreCase. สืบค้นเมื่อ 2 กันยายน 2568, จาก https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#equalsIgnoreCase-java.lang.String- 

W3schools. (ม.ป.ป). Java String equalsIgnoreCase() Method. สืบค้นเมื่อ 2 กันยายน 2568, จาก https://www.w3schools.com/java/ref_string_equalsignorecase.asp 

>C
  
IBM. (12 เมษายน 2564)). strcasecmp() Case-insensitive string comparison. สืบค้นเมื่อ 3 กันยายน 2568, จาก https://www.ibm.com/docs/en/zos/2.4.0?topic=functions-strcasecmp-case-insensitive-string-comparison  

Studyplan. (ม.ป.ป). Case-Insensitive C-String Comparison. สืบค้นเมื่อ 3 กันยายน 2568, จาก https://www.studyplan.dev/pro-cpp/c-strings/q/case-insensitive-c-string-comparison 
