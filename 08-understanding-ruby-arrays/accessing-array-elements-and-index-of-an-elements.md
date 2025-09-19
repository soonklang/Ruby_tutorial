# Accessing Array Elements and Finding Index of an Elements

# Accessing  Array Element

### การเข้าถึง Array

การเข้าถึงองค์ประกอบ(Element)ของ array นั้น สามารถเข้าถึงผ่าน index ของ arrayนั้นได้โดยวิธีต่างๆดังนี้

1.การเข้าถึงเเบบปกติ หรือใช้ \[]

การเข้าถึงอาเรย์โดยวิธีนี้สามารถเข้าถึง Element ใน index ได้โดยใช้ \[] เเละใส่ค่า index เข้าไปข้างในดังนี้

### ตัวอย่าง array&#x20;

```
odd = [1,3,5,7,9]
even = [2,4,6,8,10]
```

### ตัวอย่างภาษา Ruby

```
puts odd[0]
# ค่าที่ได้คคือ 1
puts even[1]
# ค่าที่ได้คือ 4
```

### ตัวอย่างภาษา Python

```
print(odd[0])
# ค่าที่ได้คคือ 1
print(even[1])
# ค่าที่ได้คือ 4
```

### ตัวอย่างภาษา Java

```
System.out.println(odd[0]);
# ค่าที่ได้คคือ 1
System.out.println(even[1]);
# ค่าที่ได้คือ 4
```

### ตัวอย่างภาษา C

```
#include<stdio.h>
int main(){
    printf("%d\n",odd[0]);
    # ค่าที่ได้คคือ 1
    printf("%d\n",even[1]);
    # ค่าที่ได้คือ 4
return 0;
}
```

#### 2.การใช้ .at()

การใช้ .at() นั้นจะใส่ค่า index ลงใน () เพื่อที่จะหา Element ในตำเเหน่งที่ส่งค้าเข้าไปดังนี้

### ตัวอย่างภาษา Ruby

```
puts odd.at(1)
# ค่าที่ได้ออกมาคือ 3
puts even.at(2)
# ค่าที่ได้ออกมาคือ 6
```

เเต่ในภาษา Python Java เเละ C ไม่มีคำสั่งนี้จึงใช้วิธีเเรก

#### 3. การใช้ .fetch()

การใช้ .fetch จะมีการส่งค่า parameter เข้าไปสองตัวโดยที่ค่าเเรกเป็นค่า index เเละ ค่าที่สองคือข้อความหากเกิดกรณีค่า index เกินขอบเขตของ array เช่น

### ตัวอย่าง

```
puts odd.fetch(100,"Error Index out of bound")
#ค่าที่ได้ออกมาคือ Error Index out of bound
```

#### 4. การใช้ .first() เเละ .last()

การใช้ .first() คือการหาค่า Element เเรกใน array เเละ .last() คือการหาค่าตำเเหน่งสุดท้ายใน array

### ตัวอย่างภาษา Ruby

```
puts odd.first()
# ค่าที่ได้ออกมาคือ 1
puts even.last()
# ค่าที่ได้ออกมาคือ 10
```

### ตัวอย่างภาษา Python

```
print(odd[0])
# ค่าที่ได้ออกมาคือ 1
print(even[-1])
# ค่าที่ได้ออกมาคือ 10
```

### ตัวอย่างภาษา Java

```
System.out.println(odd[0]);
# ค่าที่ได้ออกมาคือ 1
System.out.println(even[even.length-1]);
# ค่าที่ได้ออกมาคือ 10
```

### ตัวอย่างภาษา C

```
#include <stdio.h>
int main(){
    printf("%d\n",odd[0]);
    # ค่าที่ได้ออกมาคือ 1
    int size = sizeof(even) / sizeof(even[0]);
    printf("%d\n",even[size-1]);
    # ค่าที่ได้ออกมาคือ 10
return 0;
}
```

5.การใช้ .take() เเละ .drop()

การใช้ .take() จะทำงานโดยการใส่ค่า index ลงใน () เพื่อทำการเข้าถึงค่าตั้งเเต่ค่าเเรกใน array จนถึง ค่าตัวที่ใส่เข้าไปใน array\
การใช้ .drop() จะทำงานโดยการใส่ค่า index ลงใน() เเละทำการกระโดดข้ามค่าตั้งเเต่ค่าเเรกใน array จนถึงตัวที่ใส่เข้าไปใน array ดังนี้

### ตัวอย่างภาษา Ruby

```
puts odd.take(3).join(",")
# ค่าที่ได้คือ 1,3,5
puts even.drop(3).join(",")
# ค่าที่ได้คือ 8,10
```

### ตัวอย่างภาษา Python

```
print(odd[:3])
# ค่าที่ได้คือ [1,3,5]
print(even[3:])
# ค่าที่ได้คือ [8,10]
```

### ตัวอย่างภาษา Java

```
for(int i=0;i<3;i++){
    System.out.print(odd[i]);
    if (i < 2) {
        System.out.print(",");
    }
}
System.out.println();
# ค่าที่ได้คือ 1,3,5
for(int i=3;i<even.length;i++){
    System.out.print(even[i]);
    if (i<even.length-1){
        System.out.print(",");
    }
}
# ค่าที่ได้คือ 8,10
```

### ตัวอย่างภาษา C

```
#include <stdio.h>
int main(){
    for(int i=0;i&#x3C;3;i++){
       printf("%d",odd[i]);
        if (i &#x3C; 2) {
            printf(",");
        }
    }
    # ค่าที่ได้คือ 1,3,5
    printf("\n");
    int e_size = sizeof(even) / sizeof(even[0]);
    for(int i=3;i&#x3C;e_size;i++){
            printf("%d",even[i]);
        if (i&#x3C;e_size-1){
            printf(",");
        }
    }
    # ค่าที่ได้ 8,10
}
```
## Reference

Ruby Documentation - Accessing Elements สืบค้นเมื่อ 3/9/2568 จาก [https://docs.ruby-lang.org/en/master/Array.html#class-Array-label-Accessing+Elements](https://docs.ruby-lang.org/en/master/Array.html#class-Array-label-Accessing+Elements)\
geeksforgeeks - How to access array Elements in Ruby สืบค้นเมื่อ 3/9/2568 จาก [https://www.geeksforgeeks.org/ruby/how-to-access-array-elements-in-ruby/](https://www.geeksforgeeks.org/ruby/how-to-access-array-elements-in-ruby/
)\
W3schools - Python Arrays สืบค้นเมื่อ 3/9/2568 จาก [https://www.w3schools.com/python/python\_arrays.asp](https://www.w3schools.com/python/python_arrays.asp)\
W3schools - C Arrays สืบค้นเมื่อ 3/9/2568 จาก [https://www.w3schools.com/c/c\_arrays.php](https://www.w3schools.com/c/c_arrays.php) \
W3schools - Java Arrays สืบค้นเมื่อ 3/9/2568 จาก [https://www.w3schools.com/java/java\_arrays.asp](https://www.w3schools.com/java/java_arrays.asp)


# Finding the Index of an Element

การหาค่า Index ใน Element ของ array นั้นบ่อยครั้งที่เราต้องการหาตำเเหน่ง index ของ array เพื่อนำไปใช้งานต่อโดยเราสามารถหาตำเเหน่ง index ได้โดยคำสั่งต่อไปนี้

#### 1.)  การใช้ .index()

#### การใช้ .index()  นั้นเป็นการหาค่า index ใน array  ของ element ตัวเเรกที่เจอโดยการใส่ค่า element ลงไปใน () เพื่อตรวจสอบค่าใน array เเละทำการ return ออกมา

### ตัวอย่าง Array

```
month = ["Jan","Feb","Mar","April","May","May","June"]
```

หากเราต้องการหาค่า index ใน array สามารถทำได้ดังนี้

### ตัวอย่างภาษา Ruby

```
puts month.index("May")
# ค่าที่ได้ออกมาคือ 4
```

### ตัวอย่างภาษา Python

```
print(month.index("May"))
# ค่าที่ได้ออกมาคือ 4
```

### ตัวอย่างภาษา Java

```
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        String[] month = {"Jan", "Feb", "Mar", "April", "May", "May", "June"};
        List<String> monthList = Arrays.asList(month);

        System.out.print(monthList.indexOf("May"));
    }
}
# ค่าที่ได้ออกมาคือ 4
```

### ตัวอย่างภาษา C

```
#include <stdio.h>
int main(){
    int size = sizeof(month) / sizeof(month[0]);

    for (int i = 0; i < size; i++) {
        if (strcmp(month[i], "May")==0) {
            printf("%d" , i);
            break;
      }
    }
    return 0;
}
# ค่าที่ได้ออกมาคือ 4
```

2.) การใช้ .rindex()

การใช้ .rindex() เป็นการหาค่า index ของelement ตัวสุดท้ายที่เจอใน array โดยทำการใส่ค่าลงใน () เเละทำการ return ออกมา

### ตัวอย่างภาษา Ruby

```
puts month.rindex("May")
# ค่าที่ได้ออกมาคือ 5
```

### ตัวอย่างภาษา Python

<pre><code>last_index = -1
for i in range(len(month)-1, -1, -1):
    if month[i] == "May":
        last_index = i
        print(last_index)
        break
        
# ค่าที่ได้ออกมาคือ 5    
</code></pre>

### ตัวอย่างภาษา Java

```
for(int i=month.length-1;i>-1;i--){
    if(month[i].equals("May")){
        System.out.print(i);
        break;
    }
}

# ค่าที่ได้ออกมาคือ 5
```

### ตัวอย่างภาษา C

```
#include <stdio.h>
int main(){
int size = sizeof(month) / sizeof(month[0]);

for(int i=size-1;i>-1;i--){
    if(strcmp(month[i],"May")==0){
        printf("%d",i);
        break;
    }
}
return 0;
}

# ค่าที่ได้ออกมาคือ 5
```

## Reference

Techtopia - Understanding Ruby Arrays สืบค้นเมื่อ 4/9/2568 จาก [https://www.techotopia.com/index.php/Understanding\_Ruby\_Arrays](https://www.techotopia.com/index.php/Understanding_Ruby_Arrays)\
geeksforgeeks - Ruby | Array index() function สืบค้นเมื่อ 4/9/2568 จาก [https://www.geeksforgeeks.org/ruby/ruby-array-class-index-function/](https://www.geeksforgeeks.org/ruby/ruby-array-class-index-function/)\
geekforgeeks - Ruby | Array rindex() function สืบค้นเมื่อ 4/9/2568 จาก [https://www.geeksforgeeks.org/ruby/ruby-array-rindex-function/](https://www.geeksforgeeks.org/ruby/ruby-array-rindex-function/)\
W3schools - Python Arrays สืบค้นเมื่อ 4/9/2568 จาก [https://www.w3schools.com/python/python\_arrays.asp](https://www.w3schools.com/python/python_arrays.asp)\
W3schools - C Arrays สืบค้นเมื่อ 4/9/2568 จาก [https://www.w3schools.com/c/c\_arrays\_size.php](https://www.w3schools.com/c/c_arrays_size.php)\
W3schools - Java Arrays สืบค้นเมื่อ 4/9/2568 จาก [https://www.w3schools.com/java/java\_arrays.asp](https://www.w3schools.com/java/java_arrays.asp)

[^1]: 
