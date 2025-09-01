# Ruby for loop
## นิยามของ for loop

 for loop คือคำสั่งควบคุมการทำงานของโปรแกรมที่ช่วยให้สามารถทำงานซ้ำ ๆ ได้ภายใต้เงื่อนไขที่ผู้เขียนโปรแกรมกำหนด ประโยชน์ที่เราได้จากการใช้ for loop คือ  การทำงานซ้ำตามจำนวนที่แน่นอน เช่น พิมพ์ข้อความ 10 ครั้ง ลดความซ้ำซ้อนของโค้ด ไม่ต้องเขียนคำสั่งเดิม ๆ หลายบรรทัด, แก้ไขหรืออัปเดตเงื่อนไขได้เพียงจุดเดียว ทำให้โค้ดอ่านง่าย 

## for loop ในภาษา Ruby

for loop ของ Ruby มักถูกใช้งานเมื่อต้องการให้ชุดคำสั่งทำงานซ้ำ โดยสามารถวนผ่านคอลเลกชันของข้อมูล เช่น อาเรย์ (Array) หรือ เรนจ์ (Range) ได้โดยตรงโดย
ในการวนซ้ำ จะมี ตัววน (iterator) ทำหน้าที่เข้าถึงค่าทีละตัว เพื่อนำค่าไปใช้ในการคำนวณ การนับ การอัปเดตค่า หรือการประมวลผลอื่น ๆ ตามที่กำหนด

## Basic Syntax
``` ruby
for variable_name in expression 

   # code to be executed

end
```
>
>+ for :คือคีย์เวิร์ดที่ใช้เพื่อเริ่มต้นการทำงานของลูป
>
>+ variable_name :คือตัวแปรที่ทำหน้าที่เป็น ตัววน (iterator) โดยเป็นตัวแปรที่ทำหน้าที่ในการเข้าถึงข้อมูลแต่ละตัว
>
>+ in :คือคีย์เวิร์ดที่บอกว่าเราจะวนซ้ำแบบไหนเช่น ช่วง(Range)  หรือ อาเรย์(Array)  เป็นต้น
>
>+ expression :คือนิพจน์ที่จะกำหนดชนิดข้อมูลที่เราจะนำมาวน เช่น 1..5 หรือ [10, 20, 30] 
>
>+ end: ใช้เพื่อปิดบล็อกคำสั่งที่อยู่ภายในลูป
>

``` ruby
for i in 1..5
    puts i
end
```
<details>
<summary>Output</summary>
<pre>
1<br>2<br>3<br>4<br>5
</pre>
</details>


>ซึ่งการใช้ Range นั้นจะมีการใช้งาน 2 แบบคือ
>
>1. การที่ใช้ 2 จุดคือ 1..5 => เราจะได้ตัวเลขออกมา 5 ตัวคือ 1 2 3 4 5 
>
>2. การที่ใช้ 3 จุดคือ 1...5 => จะได้ตัวเลขมาออกมา  4 คือ 1 2 3 4

# ตัวอย่างการใช้งาน  for loop

## Range

 ``` ruby
for i in 1...10
    print "#{i} "
end

```
<details>
<summary>Output</summary>
<pre>
1 2 3 4 5 6 7 8 9
</pre>
</details>

## Array
 ``` ruby
languages = ["Ruby","Python", "Java", "C"]
for i in languages 
    puts i
end
```
<details>
<summary>Output</summary>
<pre>
Ruby<br>Python<br>Java<br>C
</pre>
</details>


## Hash
 ``` ruby
movies = {"Star Wars": 1, "Avatar": 2, "Harry Potter": 3}
for k, v in movies
    puts "#{k} => #{v}"
end
```
<details>
<summary>Output</summary>
<pre>
Star Wars => 1<br>Avatar => 2<br>Harry Potter => 3
</pre>
</details>


# การเปรียบเทียบ Ruby กับภาษาชนิดอื่น








