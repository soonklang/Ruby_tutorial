# Using Range Methods

#### **Range Methods** คือฟังก์ชั้นต่างๆ ที่เราสามารถเรียกใช้กับช่วงค่าพวกนี้ได้ เช่นการหาค่าต่ำสุด สูงสุด การวนลูปผ่านค่าทุกตัวในช่วง ฯลฯ

การสร้าง Range สามารถทำได้ 2 แบบคือ

### <kbd>**#1 Range Literal**</kbd>

<kbd>Range</kbd> ที่ใช้ <kbd>'..'</kbd> จะเป็นการสร้างที่รวมค่าสุดท้ายของช่วงนั้นเข้าไปด้วย แต่ถ้าหากใช้ <kbd>'...'</kbd> ช่วงสุดท้ายจะไม่ถูกรวมเข้าไป

<pre><code><strong>
</strong>(1..4)      Output => [1, 2, 3, 4]
('a'..'d')  Output => ["a", "b", "c", "d"]

(1...4)     Output => [1, 2, 3]
('a'...'d') Output => ["a", "b", "c"]
</code></pre>

### <kbd>**#2 Range.new**</kbd>

คือการสร้างช่วงใหม่โดยอิงตามวัตถุที่ถูกกำหนดไว้ได้แก่ <kbd>begin</kbd>, <kbd>end</kbd> ตามลำดับและมีตัว <kbd>exclude\_end</kbd> เพื่อกำหนดว่าเราจะรวมวัตถุตัวสุดท้ายกับช่วงนั้นไหม

```
Range.new(2, 5)            Output => [2, 3, 4, 5]
Range.new(2, 5, true)      Output => [2, 3, 4]
Range.new('a', 'd')        Output => ["a", "b", "c", "d"]
Range.new('a', 'd', true)  Output => ["a", "b", "c"]
```

### <kbd>**.to\_a**</kbd>

<kbd>to\_a</kbd> เป็นเมธอดที่แปลงวัตถุ <kbd>Range</kbd> ให้เป็น <kbd>Array</kbd> โดยสมาชิกทั้งหมดจะมีอยู่ในช่วงที่กำหนดไว้

```
(1..4).to_a                 Output => [1, 2, 3, 4]
Range.new(2, 5).to_a        Output => [2, 3, 4, 5]
```

### <kbd>**.begin**</kbd>

ใช้สำหรับคืนค่าเริ่มต้นของช่วงนั้นๆ

```
(1..4).begin        Output => 1
```

### <kbd>**.end**</kbd>&#x20;

ใช้สำหรับคืนค่าสุดท้ายของช่วงนั้นๆ

```
(1..4).end         Output => 4
```

### <kbd>**.count**</kbd>

ใช้สำหรับคืนค่าจำนวนสมาชิกทั้งหมดในช่วงนั้น

```
(1..4).count          Output => 4
('a'..'d').count      Output => 4
```

### <kbd>**.exclude\_end?**</kbd>

เมธอดนี้จะคืนค่าเป็น <kbd>true</kbd> กับ <kbd>false</kbd> โดยจะเช็คว่าช่วงนั้นๆรวมค่าสุดท้ายหรือไม่

```
Range.new(2, 5).exclude_end?       Output => false
Range.new(2, 5, true).exclude_end? Output => true
(2..5).exclude_end?                Output => false
(2...5).exclude_end?               Output => true
```

### <kbd>**.first**</kbd>

<kbd>first</kbd> อาจจะมีความคล้ายกันกับ [<kbd>begin</kbd>](using-range-methods.md#begin) แต่ทำงานไม่เหมือนกันโดย [<kbd>begin</kbd> ](using-range-methods.md#begin)จะดึงสมาชิกตัวแรกออกมา แต่ first สามารถดึงออกมาได้หลายตัวในเวลาเดียวกันหรือไม่เอาอะไรออกมาเลยก็ได้

```
(1..4).first     Output => 1
('a'..'d').first Output => "a"

(1..10).first(3) Output => [1, 2, 3]
(1..10).first(0) Output => []
```

### <kbd>**.last**</kbd>&#x20;

ทำหน้าที่คล้ายกับ [<kbd>end</kbd>](using-range-methods.md#end) และมีความสามารถที่เหมือนกับ [<kbd>first</kbd>](using-range-methods.md#first) ในการดึงสมาชิกออกมาได้มากกว่า 1

```
(1..4).last     Output => 4
('a'..'d').last Output => "d"

(1..10).last(3) Output => [8, 9, 10]
(1..10).last(0) Output => []
```

