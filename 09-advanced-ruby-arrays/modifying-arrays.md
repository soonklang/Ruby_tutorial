# Modifying array 
การเปลี่ยนค่าใน array ของ ruby
## 1. Method .insert(index,value)
### input
```
a = [1,2,3,4]
a.insert(1,6)
puts a
```
### output
```
[1,6,2,3,4]
```
### C
ในภาษา C ปกติไม่มี method .insert() ที่ใช้กับ array เราจึงต้อง shift ค่าออกไปทางขวาแล้วใส่ค่าเพิ่มลงไป
<details>
  
  ```
  
#include <stdio.h>

void insert(int arr[], int *n, int pos, int val) {
  
    // Shift elements to the right
    for (int i = *n; i > pos; i--)
        arr[i] = arr[i - 1];

    // Insert val at the specified position
    arr[pos] = val;

    // Increase the current size
    (*n)++;
}

int main() {
    int arr[7] = {10, 20, 30, 40, 50};
    int n = 5;
    int pos = 3;
    int val = 25;

    // Insert the value at the specified position
    insert(arr, &n, pos, val);

    for (int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    return 0;
}
```

</details>

### output
<details>
  
```
10 20 30 25 40 50
```

</details>

### Java
  การสร้าง method insert ในภาษา Java
  <details>
    
```
import java.io.*;
import java.lang.*;
import java.util.*;

class GFG {

    // Function to insert x in arr at position pos
    public static int[] insertX(int n, int arr[],
                                int x, int pos)
    {
        int i;

        // create a new array of size n+1
        int newarr[] = new int[n + 1];

        // insert the elements from
        // the old array into the new array
        // insert all elements till pos
        // then insert x at pos
        // then insert rest of the elements
        for (i = 0; i < n + 1; i++) {
            if (i < pos - 1)
                newarr[i] = arr[i];
            else if (i == pos - 1)
                newarr[i] = x;
            else
                newarr[i] = arr[i - 1];
        }
        return newarr;
    }

    // Driver code
    public static void main(String[] args)
    {

        int n = 10;
        int i;

        // initial array of size 10
        int arr[]
            = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

        // print the original array
        System.out.println("Initial Array:\n"
                           + Arrays.toString(arr));

        // element to be inserted
        int x = 50;

        // position at which element
        // is to be inserted
        int pos = 5;

        // call the method to insert x
        // in arr at position pos
        arr = insertX(n, arr, x, pos);

        // print the updated array
        System.out.println("\nArray with " + x
                           + " inserted at position "
                           + pos + ":\n"
                           + Arrays.toString(arr));
    }
}
```

</details>

### output
<details>
  
```
Initial Array:
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

Array with 50 inserted at position 5:
[1, 2, 3, 4, 50, 5, 6, 7, 8, 9, 10]
```

</details>

## 2. array[index] = value
### input
```
a = [1,2,3,4]
a[3] = 5
puts a
```
### output
```
[1,2,3,5]
```
### C
<details>
  
```
void main(){
  int arr[] = {1,2,3,4,5};
  arr[1] = 3;
  for(int i = 0 ; i < 5 ; ++i){
    printf("%d ",arr[i]);
  }
}
```

</details>

### output
<details>
  
```
1 3 3 4 5
```
  
</details>

### Java

<details>
  
```
class Arr{
  public static void main(String[] args) {
    int[] myNum = {10, 20, 30, 40};
    myNum[2] = 50;
    for(int i : myNum)
      System.out.print(i + " ");    
  }
}
```
</details>

### output
<details>
  
```
10 20 50 40
```

</details>

## 3. [..] range
### input
```
a = [1,2,3,4]
a[0..2] = [4..6]
puts a
```
### output
```
[4,5,6,4]
```
### C
ในภาษา C ไม่มีการเปลี่ยนค่าแบบ range ใน array ทำได้แค่ลูปเปลี่ยนค่าเท่านั้น
<details>
  
```
#include <stdio.h>

int main() {
    int arr[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}; // Example array
    int start_index = 2; // Inclusive start index
    int end_index = 6;   // Inclusive end index
    int new_value = 99;  // Value to assign

    printf("Original array: ");
    for (int i = 0; i < 10; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    // Change values within the specified range
    for (int i = start_index; i <= end_index; i++) {
        if (i >= 0 && i < 10) { // Boundary check to prevent out-of-bounds access
            arr[i] = new_value;
        }
    }

    printf("Array after changing values in range [%d, %d]: ", start_index, end_index);
    for (int i = 0; i < 10; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}
```

</details>

### output
<details>
  
```
Original array: 1 2 3 4 5 6 7 8 9 10 
Array after changing values in range [2, 6]: 1 2 99 99 99 99 99 8 9 10 
```

</details>

### Java
  ในภาษา Java สามารถใช้ method ใน class Arrays เพื่อแกค่าเป็น range ได้ หรือ ใช้ลูปแบบ C ก็ได้
<details>
  
```
import java.util.Arrays;

public class ArrayFillRange {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50, 60, 70, 80};

        // Define the range and the value to fill
        int startIndex = 2;
        int endIndex = 5;
        int fillValue = 99;

        System.out.println("Array before fill:");
        for (int num : numbers) {
            System.out.print(num + " ");
        }
        System.out.println();

        // Fill the range with the specified value
        Arrays.fill(numbers, startIndex, endIndex, fillValue);

        System.out.println("Array after fill:");
        for (int num : numbers) {
            System.out.print(num + " ");
        }
    }
}
```

</details>

### output
<details>
  
```
Array before fill:
10 20 30 40 50 60 70 80 
Array after fill:       
10 20 99 99 99 60 70 80
```

</details>

# Reference
## Ruby
- www.techotopia.com/index.php/Advanced_Ruby_Arrays
## C
- www.geeksforgeeks.org/c/c-program-to-insert-an-element-in-an-array/
## Java
- www.w3schools.com/java/java_arrays.asp
- www.geeksforgeeks.org/java/how-to-insert-an-element-at-a-specific-position-in-an-array-in-java/
- https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html
