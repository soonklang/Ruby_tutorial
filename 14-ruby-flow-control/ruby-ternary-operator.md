# Ruby Ternary Operator
Ternary operator คือ ตัวดำเนินการที่ใช้เขียนเงื่อนไขแบบย่อ ในบรรทัดเดียว แทนการใช้ if  else แบบเต็ม
# flow chart
<img width="752" height="881" alt="image" src="https://github.com/user-attachments/assets/46b62340-9305-4706-a66b-739462a7469a" />



อ้างอิงจาก<br><br>
https://www.geeksforgeeks.org/java/java-ternary-operator/
# ตัวอย่างการเขียน if else ใน Ruby
```ruby
wight = 75
if wight >= 75
    body = "fat"
else 
    body = "thin"
end
puts body

```
```
fat
```

# ตัวอย่าง Ternary Oparator ใน Ruby
```ruby
wight = 75
body = wight >= 75 ? "fat" : "thin"
puts body
```


จะเห็นได้ว่า การเขียนแบบ Ternary Operator ทำให้โค้ด if else มีความกระชับ ลดบรรทัดในการเขียน <br><br>
อ้างอิงจาก<br><br>
https://www.ruby-lang.org/en/documentation/faq/11/<br><br>
https://www.w3resource.com/ruby/ruby-ternary-operator.php
<br><br>
แต่มีข้อควรระวังคือ เหมาะกับ if else ที่มีเงื่อนไขไม่ซับซ้อน หากมีเงือนไขที่ซับซ้อมเกินไป ควรใช้ if else ปกติ
# รูปแบบการเขียน Ruby ternary operator
condition ? value if true : value if false
# ส่วนประกอบของ Ruby ternary operator
ประกอบด้วย 3 ส่วน คือ <br><br>
เงื่อนไข ? condition เงื่อนไขที่จะทำให้ผลลัพธ์เป็นจริง
<br><br>
ค่าที่ได้เมื่อเงื่อนไขเป็นจริง : value if true ค่าที่จะได้รับถ้าเงื่อนไขเป็นจริง
<br><br>
ค่าที่ได้เมื่อเงื่อนไขเป็นเท็จ value if false ค่าที่จะได้รับถ้าเงื่อนไขเป็นเท็จ

# ปกติ ternary operator ถูกออกแบบมาให้ใช้กับแค่ 2 เงื่อนไข แต่ถ้าต้องการเขียนแบบ 3 เงื่อนไขก็สามารถเขียนได้
รูปแบบ if else ปกติ 
```ruby
wight = 75
if wight >= 75
    body = "fat"
elsif wight < 60
    body = "proportionate"
else 
    body = "thin"
end
puts body

```
เพิ่มเงื่อนไขขึ้นมาอีก 1 เงื่อนไข คือ weight < 75 
<br><br>
รูปแบบ ternary operator 
```ruby
wight = 75
body = wight >= 75 ? "fat" : (wight < 60 ? "proportionate" : "thin")
puts body

```
ในส่วนของ ternary operator เราจะทำการเพิ่มเงื่อนไข เข้าไปในเงื่อนไขอีกที
<br><br>
การทำงานก็คือ ถ้า wiegh >= 75 = fat (if)
<br><br>
ถ้าไม่ใช่ ให้เข้าไปดูเงื่อนไขที่ 2 ที่เป็นเท็จ ซึ่ง เป็นการถามเงื่อนไขอีกครั้ง
<br><br>
การทำงานก็คือ ถ้า wiegh < 60 = proportionate (elsif)
<br><br>
เงื่อนไขสุดท้ายคือ else = thin (else)<br><br>
อ้างอิงจาก
<br><br>
https://stackoverflow.com/questions/15478357/ruby-ternary-operator-and-elsif
# การเขียน ternary operator กับภาษาอื่นๆ เพื่อเปรียบเทียบ 
# python ternary operator
```python
wight = 75
if wight >= 75:
    body = "fat"
else:
    body = "thin"
print(body)
```
```python
body = "fat" if wight >= 75 else "thin"
print(body)
```
value if true if condition 1 else (value if true if condition 2 else value if false)
<br><br>
ในภาษา Python syntax จะค่อนข้างแตกต่างกับ Ruby
<br><br>
อ้างอิงจาก <br><br>
https://www.geeksforgeeks.org/python/ternary-operator-in-python/
# javascript ternary operator
```javascript
let wight = 75;
let body;
if (wight >= 75) {
    body = "fat";
} else {
    body = "thin";
}
console.log(body);
```
```javascript
body = wight >= 75 ? "fat" : "thin";
console.log(body);
```
ในภาษา javascript syntax จะใกล้เคียง ruby เลยแต่ Ruby ไม่จำเป็นต้องประกาสตัวแปล body <br><br>
อ้างอิงจาก<br><br>
https://dev.to/nicm42/ternary-operators-in-javascript-go5
# java ternary operator
```java
int wight = 75;
String body;
if (wight >= 75) {
    body = "fat";
} else {
    body = "thin";
}
    System.out.println(body);
```
```java
body = (wight >= 75) ? "fat" : "thin");
System.out.println(body);
```
ในภาษา java syntax จะใกล้เคียง ruby และ javascript เลยแต่ Ruby ไม่จำเป็นต้องประกาสตัวแปล body<br><br>
อ้างอิงจาก<br><br>
https://www.w3schools.com/java/java_conditions_shorthand.asp
# สิ่งที่พิเศษ สำหรับ ternary operator คือ สามารถใช้คู่กับการแสดงผลบน terminal เช่น print console log และอื่นๆ
```ruby
puts wight >= 75 ? "fat" : "thin"
```
อ้างอิงจาก <br><br>
https://launchschool.com/books/ruby/read/flow_control
```python
print("fat" if wight >= 75 else "thin")
```
อ้างอิงจาก <br><br>
https://www.geeksforgeeks.org/python/ternary-operator-in-python/
```javascript
console.log((wight >= 75) ? "fat" : "thin");
```
อ้างอิงจาก <br><br>
https://www.youtube.com/watch?v=s4sB1hm73tw
```java
System.out.println((wight >= 75) ? "fat" :  "thin");
```
อ้างอิงจาก <br><br>
https://www.geeksforgeeks.org/java/java-ternary-operator-puzzle/br><br>
เป็นการเขียนเพื่อลดบรรทัด แต่ต้องระวัง เพราะว่าการทำแบบนี้ จะเป็นการทำงานครั้งเดียว ไม่มีการเก็บค่าใดๆ<

# และอีก 1 อย่างที่ใช้กับ ternary operator ได้ คือ การ return จาก method
```ruby
def body_type(wight)
  wight >= 75 ? "fat" : (wight < 60 ? "proportionate" : "thin")
end

puts body_type(50)
```
```
thin
```
อ้างอิงจาก <br><br>
https://medium.com/@dru_edmondson/the-ternary-operator-in-ruby-1e87b57f2fc9
```python
def body_type(wight):
    return "fat" if wight >= 75 else ("proportionate" if wight < 60 else "thin")

print(body_type(75))
```
```
fat
```
อ้างอิงจาก <br><br>
https://www.scaler.com/topics/python/ternary-operator-in-python/
```javascript
function bodyType(wight) {
    return wight >= 75 ? "fat" : (wight < 60 ? "proportionate" : "thin");
}
console.log(bodyType(50));
```
```
proportionate
```
อ้างอิงจาก <br><br>
https://www.geeksforgeeks.org/javascript/javascript-ternary-operator/
```java
static String bodyType(int wight) {
        return (wight >= 75) ? "fat" : (wight < 60 ? "proportionate" : "thin");
    }

    public static void main(String[] args) {
        System.out.println(bodyType(75));
}
```
```
fat
```
จะเห็นว่า ทุกภาษาใช้ ternary return ได้เลย เพราะ ternary เป็น expression ไม่ใช่ statement
# สรุป
1.ternary operator นั้น เป็นการลดตัวโค้ดให้มีความกระชับแต่ไม่เหมาะกับเงื่อนไขที่มีความซับซ้อน เช่น if elsif else 
<br><br>
2.ternary operator สามารถ assignment ค่าให้ตัวแปรได้ตรงๆ
<br><br>
3.ternary operator สามารถ return ออกมาจาก method ได้
<br><br>
4.ternary operator สามารถ print ออกมาได้เลยตรงๆ ไม่ต้องเก็บค่าไว้ที่ไหน
# Presentation
https://drive.google.com/file/d/1iaQ0NBLzU8IJtSvf6xD2uud0erfAg0pq/view?usp=sharing
# Video
https://youtu.be/RLw1SiV3ysU
