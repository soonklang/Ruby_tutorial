# General Delimited Strings

## ความหมาย :  
   เป็นการอนุญาตให้คุณสามารถเลือกตัวคั่น ของข้อความนั้นๆ ได้ เพื่อที่จะหลีกเลี่ยงการซ้อนทับของอักขระพิเศษภายในข้อความกับตัวคั่นตามปกติของ ภาษา Ruby
ตามปกติในภาษา Ruby เวลาที่เราจะสร้าง String จะมี pattern ดังนี้ 
### Example 1 :  
      myString = "This is a string"
      puts myString
<details close>
   <summary><b>output</b></summary>
 <pre>
   This is a string
 </pre>
</details>

  ซึ่ง Ruby อนุญาตให้เราใช้เครื่องหมาย % ตามด้วยตัวคั่นอะไรก็ได้ที่คุณเลือกได้ เช่น ( ), [ ], { }, ! ! , | | , etc. (Techotopia, n.d.).

  ### Example 2 :
      myString = %{"This is a string"}
      puts myString
<details close>
   <summary><b>output</b></summary>
 <pre>
   This is a string
 </pre>
</details> 

และ Ruby ยังมี ตัวคั่นพิเศษบางประเภทที่ใช้คั่นด้วยความหมายที่แตกต่างกันด้วย เช่น
### Example 3 %Q:
      myString = %Q{"This is a string #{1+2}"}
      puts myString
<details close>
   <summary><b>output</b></summary>
 <pre>
   This is a string 3
 </pre>
</details> 

### Example 4 %q:
      myString = %q{"This is a string #{1+2}"}
      puts myString
<details close>
   <summary><b>output</b></summary>
 <pre>
   This is a string #{1+2}
 </pre>
</details> 
แต่ ถ้าเราไม่ต้องการใช้วิธีการ General delimited String ก็ สามารถใช้ Backslash คู่กับตัว " หรือ ' ด้วย ซึ่งเราจะใช้ Backslash เพื่อ "escape" ก็ต่อเมื่อ เครื่องหมายคำพูดข้างใน เป็นชนิดเดียวกับเครื่องหมายที่ใช้ล้อมกรอบ

### Example 5 \" \":
      myString = "This is \"my\" String"
      puts myString
<details close>
   <summary><b>output</b></summary>
 <pre>
   This is "my" String
 </pre>
</details> 

### Example 6 \' \':
      myString = 'This is \'my\' String'
      puts myString
<details close>
   <summary><b>output</b></summary>
 <pre>
   This is 'my' String
 </pre>
</details> 

แต่ถ้าเครื่องหมายที่ใช้ล้อมกรอบคนละชนิดกับเครื่องหมายภายใน เราก็สามารถใช้มันได้โดยที่ไม่ต้อง escape

### Example 7 ' ':
      myString = "This is 'my' String"
      puts myString
<details close>
   <summary><b>output</b></summary>
 <pre>
   This is 'my' String
 </pre>
</details> 

### Example 8 " ":
      myString = 'This is "my" String'
      puts myString
<details close>
   <summary><b>output</b></summary>
 <pre>
   This is "my" String
 </pre>
</details> 
ซึ่งตัวคั่นนั้นก็สามารถใช้กับข้อมูลประเภทอื่นๆได้เช่นกัน เช่น %w[apple banana cherry] ทำให้ สร้าง Array ของ String โดยไม่ต้องพิมพ์ " หรือ , และยังมีตัวคั่นอื่นๆอีก ซึ่งสามารถ ศึกษาต่อที่หัวข้อ General Delimited Input (Thomas et al., 2013).

# เปรียบเทียบกับภาษาอื่นๆ
## C Language      
ในภาษา C นั้น ไม่มี ตัวแทนการทำ General Delimited String เหมือนในภาษา Ruby (%) แต่มีการใช้เทคนิค อย่างอื่นแทน นั่นก็คือ escape sequence เพื่อให้อักขระพิเศษบางอย่างสามารถปรากฎบน String ได้ เช่น \n ที่ถ้าใช้เปล่าๆ จะหมายถึงการขึ้นบรรทัดใหม่
   ### Example C language :
         #include <stdio.h>
            int main() {
                printf("He said, \"It's a 'tricky' string!\"");
             return 0;
            }
<details close>
    <summary><b>output</b></summary>
   <pre>
       He said, "It's a 'tricky' string!"
   </pre>
 </details>

   ## Java Language
   ในทำนองเดียวกัน ภาษา Java ก็ใช้การescape sequence เช่นเดียวกับ ภาษา C แต่ในกรณีที่ตัวข้อความมีขนาดยาว เราจะใช้เทคนิคที่เรียกว่า Text Blocks (java 15 ขึ้นไปเท่านั้นที่สามารถใช้ได้) เพื่อทำให้การเขียน string นั้นสะดวกมากยิ่งขึ้น (Oracle, n.d.).
   ### Example Java language (กรณีใช้ Escape Sequence) :
         public class Main {
             public static void main(String[] args) {
                 // เช่นเดียวกับ C, Java ต้องใช้ \ เพื่อ escape "
                 String trickyString = "He said, \"It's a 'tricky' string!\"";
                 System.out.println(trickyString);
             }
         }
   <details close>
   <summary><b>output</b></summary>
       <pre>
         He said, "It's a 'tricky' string!"
       </pre>
   </details>
   
   แต่ถ้าตัว string มีการต่อกันมากๆเพื่อให้การเชียนง่ายขึ้นเราจะใช้ """ """ดังตัวอย่างต่อไปนี้
   ### Example Java language (กรณีใช้ Text Blocks) :
         public class test {
             public static void main(String[] args) {
                 // ORIGINAL
                 String message = "'The time has come,' the Walrus said,\n" +
                         "'To talk of many things:\n" +
                         "Of shoes -- and ships -- and sealing-wax --\n" +
                         "Of cabbages -- and kings --\n" +
                         "And why the sea is boiling hot --\n" +
                         "And whether pigs have wings.'\n";
                 System.out.println(message);
             }
         }
   <details close>
         <summary><b>output</b></summary>
               <pre>
                  'The time has come,' the Walrus said,
                        'To talk of many things:
                        Of shoes -- and ships -- and sealing-wax --
                        Of cabbages -- and kings --
                        And why the sea is boiling hot --
                        And whether pigs have wings.'
               </pre>
   </details>
         
   ### Example Java language (กรณีใช้ Text Blocks) :      
         public class test {
          public static void main(String[] args) {
              // TextBlocks version
              String messageTextBlocks = """
                      'The time has come,' the Walrus said,
                      'To talk of many things:
                      Of shoes -- and ships -- and sealing-wax --
                      Of cabbages -- and kings --
                      And why the sea is boiling hot --
                      And whether pigs have wings.'
                      """;
              System.out.println(messageTextBlocks);
          }
      }
   <details close>
            <summary><b>output</b></summary>
                <pre>
                  'The time has come,' the Walrus said,
                        'To talk of many things:
                        Of shoes -- and ships -- and sealing-wax --
                        Of cabbages -- and kings --
                        And why the sea is boiling hot --
                        And whether pigs have wings.'
                </pre>
   </details>
   
   ## Python Language
   และเช่นกัน! python ก็ไม่มี General Delimited String เหมือนกับ C และ Java โดยPythonจะมีวิธีการอยู่ 2 แบบ (Python Software Foundation, n.d.-a).
   ### Example 1. Triple-Quoted Strings  (ใช้ ''' ''' หรือ """ """ ประกบข้อความ)    
      message = """
      'The time has come,' the Walrus said,
      'To talk of many things:
      Of shoes -- and ships -- and sealing-wax --
      Of cabbages -- and kings --'
      """
      print(message)
   <details close>
            <summary><b>output</b></summary>
                <pre>
                  'The time has come,' the Walrus said,
                  'To talk of many things:
                  Of shoes -- and ships -- and sealing-wax --
                  Of cabbages -- and kings --'
                </pre>
   </details>
   หมายเหตุ ในภาษา Python เรายังสามารถใช้ """ สิ่งที่ต้องการcomment """  เพื่อเป็นการ comment หลายบรรทัด แต่ถ้าจะ comment บรรทัดเดียวใช้ # ตามด้วยสิ่งที่อยากcomment
   
   ### Example 2.การสลับใช้เครื่องหมายคำพูด (ใช้ ' ' หรือ " " )
      # ถ้าในสตริงมี ' เช่นตรงจุด It's  ต้อง \' เพื่อ escape ' 
      message1 = ' He said, "It\'s a beautiful day!" ' 
      print(message1)
      # ถ้าในสตริงมี " ตรงข้อความ "It's a beautiful day!" ต้อง \" เพื่อ escape "
      message2 = " He said, \"It's a beautiful day!\" " 
      print(message2)
   <details close>
            <summary><b>output</b></summary>
                <pre>
                  ผลลัพธ์ทั้งสองข้อความได้แบบเดียวกันคือ He said, "It's a beautiful day!"
                </pre>
   </details>
      
   ##  เอกสารอ้างอิง (References) :
   
   cppreference.com. (n.d.). Escape sequences. Retrieved October 26, 2023, from https://en.cppreference.com/w/c/language/escape.html

   GeeksforGeeks. (2023, September 26). Escape sequences in Java. https://www.geeksforgeeks.org/java/escape-sequences-in-java/

   GeeksforGeeks. (2023, October 23). How to split a string by a delimiter in C? https://www.geeksforgeeks.org/c/how-to-split-a-string-by-a-delimiter-in-c/

   Oracle. (n.d.). Text blocks. Oracle Help Center. Retrieved October 26, 2023, from https://docs.oracle.com/en/java/javase/15/text-blocks/index.html

   Python Software Foundation. (n.d.-a). An informal introduction to Python. Python 3.12.0 documentation. Retrieved October 26, 2023, from https://docs.python.org/3/tutorial/introduction.html#text

   Python Software Foundation. (n.d.-b). Text sequence type — str. Python 3.12.0 documentation. Retrieved October 26, 2023, from https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str

   Techotopia. (n.d.). Ruby strings - Creation and basics. Retrieved October 26, 2023, from https://www.techotopia.com/index.php/Ruby_Strings_-_Creation_and_Basics

   Thomas, D., Fowler, C., & Hunt, A. (2013). Programming Ruby 1.9 & 2.0: The pragmatic programmers' guide (4th ed.). The Pragmatic Programmers.


