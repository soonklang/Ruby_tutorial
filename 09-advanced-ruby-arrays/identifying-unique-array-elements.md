# Identifying Unique Array Elements
Method Unique หรือ .uniq คือ Method ในภาษา Ruby ที่ใช้ลบค่าที่ซั้ากันในอาเรย์ 

อธิบายง่ายๆ คือ สมมติในอาเรย์ม [1,2,2,3,3] พอใช้คำสั่ง .uniq ก็จะตัดตัวซั้ากันออกจะเหลือ [1,2,3] แต่ในภาษาอื่นอาจจะแตกต่างกันในการใช้

ต่อไปจะเป็นตัวอย่างพร้อมกับเปรียบเทียบกับภาษา C, Java, Python

## ใช้กับอาเรย์แบบ Integer, String
>Ruby Example 1

    arr = [1, 2, 2, 3, 4, 4, 5]
    arr_unique = arr.uniq
    puts "Array Elements: #{arr.inspect}"
    puts "Array after Removing Duplicates: #{arr_unique.inspect}"

    Output: 
    Array Elements: [1, 2, 2, 3, 4, 4, 5]
    Array after Removing Duplicates: [1, 2, 3, 4, 5]

>Ruby Example 2

    linux_systems = ["RHEL", "SuSE", "PCLinuxOS", "Ubuntu", "Fedora", "RHEL", "SuSE"]

    linux_systems.uniq
    => ["RHEL", "SuSE", "PCLinuxOS", "Ubuntu", "Fedora"]

## ใช้กับ Loop
>Ruby Example 3

    arr = [1, 3, 2, 4, 4, 5]
    arr_unique = []
    arr.each { |element| arr_unique << element unless arr_unique.include?(element) }
    puts "Array Elements: #{arr.inspect}"
    puts "Array after Removing Duplicates: #{arr_unique.inspect}"

    Output:
    Array Elements: [1, 3, 2, 4, 4, 5]
    Array after Removing Duplicates: [1, 3, 2, 4, 5]
สังเกตุว่าแบบนี้จะไม่ใช้ .uniq แต่จะใช้ Loop แทนแล้วตรวจหาตัวซั้าถ้าซั้าจะไม่ push เข้าไปในอาเรย์

* หลายๆภาษาเช่น C, java, python ใช้การเขียนแบบนี้ แต่รูปแบบอาจจะไม่คล้ายกัน

## ใช้กับ | (Union)
>Ruby Example 4

    arr = [1, 2, 2, 3, 4, 4, 5]
    arr_unique = arr | []
    puts "Array Elements: #{arr.inspect}"
    puts "Array after Removing Duplicates: #{arr_unique.inspect}"

    Output:
    Array Elements: [1, 2, 2, 3, 4, 4, 5]
    Array after Removing Duplicates: [1, 2, 3, 4, 5]
วิธีนี้คือการใช้คู่กับเครื่องหมายทางคณิตศาสตร์ คือ เครื่องหมาย Union จากในโค๊ดคือการเอาอาเรย์ไปยูเนี่ยนกับอาเรย์ว่าง ซึ่ง ยูเนี่ยนจะตัดตัวซํ้ากันออกให้เองเลย หลักการคล้ายๆกับ Ruby Example 3

# ตัวอย่าง Unique ในภาษา C
>C Example 1

    #include <stdio.h>
    
    int removeDup(int arr[], int n) {
        if (n == 0) return 0;

        int j = 0;
        for (int i = 1; i < n - 1; i++) {
            if (arr[i] != arr[j])
                arr[++j] = arr[i];
        }
        return j + 1;
    }
    
    int main() {
        int arr[] = {1, 1, 2, 2, 3, 4, 4, 5}; 
        int n = sizeof(arr) / sizeof(arr[0]);
        n = removeDup(arr, n);
        for (int i = 0; i < n; i++)
            printf("%d ", arr[i]);
        return 0;
    }

    Output : 1, 2, 3, 4, 5
*โค๊ดนี้สังเกตุได้ว่า เป็นชุดตัวเลขในอาเรย์ที่เรียงมาแล้ว เลยทำให้ใน Function removeDup ไม่ซับซ้อน หลักการทำงานก็คือ ใช้ตัวล่าสุดเป็นตัวเช็คว่าซํ้ากันหรือไม่ซั้า

ในโค๊ดคือ ให้ j เป็นตัวเช็คตัวล่าสุด และนำไปเช็คกับตัวที่ j + 1(i + 1) 


ต่อไปเป็นโค๊ดที่ใช้กับชุดข้อมูลตัวเลขที่ไม่เรียงลำดับมา
>C Example 2

    #include <stdio.h>
    #include <stdlib.h>
    
    int main(){
        int a[50], i, j, k, number;
        
        printf("Enter size of the array: ");
        scanf("%d", &number);
        
        printf("Enter Elements of the array:\n");
        for (i = 0; i < number; i++) {
            scanf("%d", &a[i]);
        }
    
        for (i = 0; i < number; i++) {
            for (j = i + 1; j < number; j++) {
                if (a[i] == a[j]) {
                    for (k = j; k < number; k++) {
                        a[k] = a[k + 1];
                    }
                    j--;
                    number--;
                }
            }
        }
    
        printf("After deleting the duplicate elements, the Array is:\n");
        for (i = 0; i < number; i++) {
            printf("%d ", a[i]);
        }
    
        return 0;
    }
    
    Input : 7
            1 2 2 3 3 4 5
    Output : After deleting the duplicate elements, the Array 1 2 3 4 5
    
วิธีนี้จะค่อนข้างสับซ้อนเพราะมี for loop ถึง 3 ลูป โค๊ดทำงานยังไง?

  number ใช้เป็นตัวแปรเก็บขนาดอาเรย์
  
  a คือชุดข้อมูลทั้งหมดในอาเรย์
  
  หลักการทำงานก็คือ i เป็นตัวที่ 0 ส่วน j เป็นตัวที่ 1 ถ้า ตัวที่ 0 และตัวที่ 1 เหมือนกัน จะใช้ ลูป k ที่มีค่าเท่ากับตัว j มาทับค่าที่ซั้ากัน ที่นี้พอลบไปแล้ว ขนาดอาเรย์จะลดลง(--number) j ก็ต้องลบด้วยเพื่อไม่ให้เคลื่อนเกินไป 1 ค่่า
  
# ตัวอย่าง unique ภาษา Java
>Example Java 1

    import java.util.*;

    public class RemoveDuplicatesWithSet {
        public static void main(String[] args) {
            List<String> list = Arrays.asList("apple", "banana", "apple", "orange");
            List<String> result = new ArrayList<>(new HashSet<>(list));
            System.out.println(result);
        }
    }

    Output : apple banana orange
ภาษา Java จะใช้ ArrayList เพื่อให้ยืดหยุ่นต่อการเก็บข้อมูล จะใช้เป็น Integer, String หรืออะไรก็ได้

ใน Java Set จะไม่เก็บค่าซํ้าเหมือนจากในโค๊ดที่ แปลงจาก ArrayList ไปเป็น Set เป็นวิธีที่ง่าย

>code

    List<String> result = new ArrayList<>(new HashSet<>(list));

ในตัวอย่างแรกใช้ HashSet ซึ่งจะไม่รักษาลำดับ การรัน 1 ครั้ง อาจจะสุ่มตำแหน่งของข้อมูล แต้ถ้าอยากให้ รักษาตำแหน่งของข้อมูล แนะนำให้ใช้ LinkedHashSet<> จะรักษาลำดับของข้อมูลทุกครั้ง 

>code

    List<String> result = new ArrayList<>(new LinkedHashSet<>(list));

>Example Java 2

    import java.util.*;
    import java.util.stream.*;
    
    public class RemoveDuplicatesWithStream {
        public static void main(String[] args) {
            List<Integer> list = Arrays.asList(1, 2, 2, 3, 4, 4, 5);
            List<Integer> uniqueList = list.stream()
                                           .distinct()
                                           .collect(Collectors.toList());
            System.out.println(uniqueList);
        }
    }

    Output : 1 2 3 4 5
วิธีนี้ค่อนข้างสะดวก และมีความคล้าย Ruby ตรงที่ว่า .uniq จะตัดตัวซํ้าและรักษาลำดับของข้อมูล เหมือนกับตัวอย่างนี้ที่ใช้ .distinct() จะทำหน้าที่ตัดข้อมูลที่ซั้ากันและ รักษาลำดับเดิมไว้ ทำให้มีความคล้ายกับ Ruby มากๆ 

ต่อไปเป็นภาษา Python
# ภาษา Python
>Example Python 1

    data = [1, 2, 2, 3, 4, 4, 5]
    unique_data = list(set(data))
    
    print(unique_data)
    
    Output : 1 2 3 4 5

วิธีนี้คล้ายๆกับ Java Example 1 ตรงที่ว่า เปลี่ยนจาก List ไปเป็น Set และเหมือนกันตรงที่ตัดตัวซั้าออก และไม่รักษาตำแหน้งของข้อมูล

>Example Python 2

    import numpy as np

    data = np.array([1, 2, 2, 3, 4, 4, 5])
    unique_data = np.unique(data)
    print(unique_data)

    Output : 1 2 3 4 5

ใช้numpy

วิธีนี้แทยจะเหมือน Ruby 100% แต่ว่าจะไม่รักษาตำแหน่ง แค่ตัดตัวซั้าออก ที่คล้ายเพราะว่าคำสั่ง ใช้คำว่า Unique เหมือนกัน

>Example Python 3

    import pandas as pd

    data = [1, 2, 2, 3, 4, 4, 5]
    unique_data = pd.Series(data).drop_duplicates().tolist()
    print(unique_data)

    Output : 1 2 3 4 5

วิธีนี้ใช้ pandas .drop_duplicates() ชื่อคำสั่งตรงตัว คือตัดตัวซํ้า และรักษาตำแหน่งของข้อมูลด้วย

>Example Python 4

    data = [1, 2, 2, 3, 4, 4, 5]
    unique_data = list(dict.fromkeys(data))
    print(unique_data)

    Output : 1 2 3 4 5
วิธีนี้เป็นวิธีที่ง่ายอีกเหมือนกันใช้ dict.fromkeys() แปลงจาก list เป็น dict โดยใช้ ตำแหน่งของ list เป็น key ทำให้วิธีนี้รักษาตำแหน่งของข้อมูลด้วย
