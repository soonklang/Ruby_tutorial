# Quiz
จงเขียนโปรแกรมการหาค่าของ sin cos tan จาก Input ของผู้ใช้ช่วงค่า [0,1) คูณกับค่าพายในภาษา Ruby C Java Python

# เฉลย

Ruby
```Ruby
puts "Input in [0,1): "
n = Float(gets.chomp)
if(n>=0 && n<1)
  angle = n * Math::PI
  puts "Angle: #{angle} radians"
  puts Math.sin(angle)
  puts Math.cos(angle)
  puts Math.tan(angle)
else
  puts "Input not in [0,1)"
end
```

C
```C
#include <stdio.h>
#define _USE_MATH_DEFINES
#include <math.h>

int main() {
    double n, angle, sin_val, cos_val, tan_val;
    
    printf("Input in [0,1): \n");
    if (scanf("%lf", &n) != 1) {
        printf("\n*** ERROR: Invalid input. Enter a number. ***\n");
        return 1;
    }

    if (n>=0 && n<1) {
        angle = n * M_PI;
        printf("Angle: %f radians\n", angle);
        printf("%f\n",sin(angle));
        printf("%f\n",cos(angle));
        printf("%f\n",tan(angle));
    }else{
        printf("Input not in [0,1)");
    }
    return 0;
}
```

Java
```Java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Input in [0,1): ");
        double n = sc.nextDouble();
        if(n>=0 && n<1){
          double angle = n * Math.PI;
  
          System.out.printf("Angle: %f radians\n",angle);
          System.out.println(Math.sin(angle));
          System.out.println(Math.cos(angle));
          System.out.println(Math.tan(angle));
        }else{
          System.out.println("Input not in [0,1)");
        }
    }
}
```

Python
```Python
import math

n = float(input("Input in [0,1): "))
if(n>=0 and n<1):
  angle = n * math.pi
          
  print(f"\nAngle: {angle} radians")
  print(math.sin(angle))
  print(math.cos(angle))
  print(math.tan(angle))
else:
  print(f"\nInput not in [0,1)")
```
