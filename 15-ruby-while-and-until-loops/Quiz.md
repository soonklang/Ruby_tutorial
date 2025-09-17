# While Loop
**1.What is the output of the following code?**

Ruby
``` ruby
n=0
while 0
  puts "basic syntax #{n}"
  i = 0 
  begin
    puts "begin-end while #{i}"
    puts "modifier form #{i += 1}" while i%2==0
    i+=1
  end while i<4
  n+=1
  break if n==3
end
```
<details open>
  <summary><strong>Answer</strong></summary>
  <pre><code>basic syntax 0
begin-end while 0
modifier form syntax 1
begin-end while 2
modifier form syntax 3
basic syntax 1
begin-end while 0
modifier form syntax 1
begin-end while 2
modifier form syntax 3
basic syntax 2
begin-end while 0
modifier form syntax 1
begin-end while 2
modifier form syntax 3
</code></pre>

</details>
<details open>
  <summary><strong>Describe</strong></summary>
  <pre>
</pre>
</details>

Python
``` python
n = 0
while 1:  # while 0 means false isn't infinite loop like Ruby
    print(f"basic syntax {n}")
    i = 0
    while i < 4:
        print(f"begin-end while {i}")
        while i % 2 == 0:
            i += 1
            print(f"modifier form syntax {i}")
        i += 1
    n += 1
    if n == 3:
        break
```
C
``` c
#include <stdio.h>

int main() {
    int n = 0;
    while (1) { //while 0 means false
        printf("basic syntax %d\n", n);
        int i = 0;
        do {
            printf("begin-end while %d\n", i);
            while (i % 2 == 0) {
                i++;
                printf("modifier form syntax %d\n", i);
            }
            i++;
        } while (i < 4);
        n++;
        if (n == 3) {
            break;
        }
    }
    return 0;
}
```

Java
``` java
public class Main {
    public static void main(String[] args) {
        int n = 0;
        while (true) { //condition of while loop must be boolean(true/false) only
            System.out.println("basic syntax " + n);
            int i = 0;
            do {
                System.out.println("begin-end while " + i);
                while (i % 2 == 0) {
                    i++;
                    System.out.println("modifier form syntax " + i);
                }
                i++;
            } while (i < 4);
            n++;
            if (n == 3) {
                break;
            }
        }
    }
}
```

**2.What is the output of the following code?**

Ruby
``` ruby
count = 0
while true do
  result = while false
    break "greeting"
  end
  puts "hello" while result
  i=0
  while i<2
    puts "sawasdee"
    while (result.class).equal?(nil.class)&&i%2!=0
      puts "aloha"
      break "Hawaii"
    end
    i+=1
  end  
  break if count==3
  count+=1
end
``` 
<details open>
  <summary><strong>Answer</strong></summary>
  <pre><code>sawasdee
sawasdee
aloha
sawasdee
sawasdee
aloha
sawasdee
sawasdee
aloha
sawasdee
sawasdee
aloha
</code></pre>
</details>

</details>
<details open>
  <summary><strong>Describe</strong></summary>
  <pre> 
</pre>
</details>

Python
``` python
count = 0
while True:
    #while cannot be used as an expression
    # nil in Ruby so in Python is None
    result = None
    #break with value exists only in Ruby
    while result:
        print("hello")
    i = 0
    while i < 2:
        print("sawasdee")
        while type(result) == type(None) and i%2 != 0:
            print("aloha")
            break
        i += 1
    if count == 3:
        break
    count += 1
```
C
``` c
#include <stdio.h>

int main() {
    int count = 0;
    while (1) {
        //while cannot be used as an expression
        // nil => NULL in C
        void* result = NULL;
        while(result) printf("hello\n"); // NULL is falsey, this never executes.
        //break with value exists only in Ruby
        int i = 0;
        while (i < 2) {
            printf("sawasdee\n");
            while ((result==NULL) && i%2!=0){
                printf("aloha\n");
                break;
            }
            i++; 
        }
        if (count == 3)
            break;
        count++;
    }
    return 0;
}
```

Java
``` java
public class Main {
    public static void main(String[] args) {
        int count = 0;
        while (true) {
            //while cannot be used as an expression like Ruby
            Object result = null;
            while (result != null) System.out.println("hello"); // never executed
            //break with value exists only in Ruby
            int i = 0;
            while (i < 2) {
                System.out.println("sawasdee");
                //null is not instance of any class
                while ((result == null) && (i % 2 != 0)) {
                    System.out.println("aloha");
                    break;
                }
                i++;
            }
            if (count == 3)
                break;
            count++;
        }
    }
}
```
