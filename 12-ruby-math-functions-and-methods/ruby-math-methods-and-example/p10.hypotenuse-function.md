# P10.Hypotenuse Function

### <mark style="color:$danger;">Ruby</mark>

เมื่อ include Math แล้วจะสามารถเรียกใช้เมธอดฟังก์ชันทางคณิตศาสตร์ได้โดยตรง

*   <mark style="color:blue;">**hypot(x, y)**</mark> : ส่งคืนค่า .sqrt(x<sup>**2**</sup>**&#x20;+ y**<sup>**2**</sup>) สำหรับค่า x และ y&#x20;

    * <mark style="color:$success;">**Domain**</mark> of x: `(-INFINITY, INFINITY)`
    * <mark style="color:$success;">**Domain**</mark> of y: `(-INFINITY, INFINITY)`
    * <mark style="color:$warning;">**Range**</mark>: `[0, INFINITY)`

    Examples:

    ```ruby
    hypot(0.0, 1.0)       # => 1.0
    hypot(1.0, 1.0)       # => 1.4142135623730951 # sqrt(2.0)
    hypot(3.0, 4.0)       # => 5.0
    hypot(5.0, 12.0)      # => 13.0
    hypot(1.0, sqrt(3.0)) # => 1.9999999999999998 # Near 2.0
    ```

***

### <mark style="color:$danger;">C</mark> <a href="#c" id="c"></a>

เมื่อ #include \<math.h> สามารถใช้ hypot ได้

hypot( double x, double y )

```c
hypot(1,1) // 1.414214
```

***

### <mark style="color:$danger;">Java</mark> <a href="#java" id="java"></a>

การใช้ฟังก์ชันทางคณิตศาสตร์ในภาษาเขียนโปรแกรม **Java** <mark style="color:$info;">ถึงจะไม่</mark> <mark style="color:$info;"></mark><mark style="color:$info;">`import java.lang.Math;`</mark> <mark style="color:$info;"></mark><mark style="color:$info;">ก็สามารถใช้ค่าคงที่ทางคณิตศาสตร์ได้เลย</mark> เพราะ java.lang จะถูก import อัตโนมัติ เหมือนมี `import java.lang.*;` ที่จุดเริ่มต้นของ compiler ทันทีหลังจาก`package`ใดก็ตาม

สามารถใช้ hypot ผ่านคำสั่งด้านล่าง

Math.hypot( double x, double y)

```java
Math.hypot(1, 1) // 1.4142135623730951
```

***

### <mark style="color:$danger;">Python</mark>

เมื่อ include math สามารถใช้ hypot ผ่านคำสั่งด้านล่าง

math.hypot( double x, double y )

```python
math.hypot(1, 1) # 1.4142135623730951
```
