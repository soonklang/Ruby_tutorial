# Quoting Ruby Strings
สตริง (String) ในภาษา Ruby สามารถกำหนดขอบเขตได้ด้วยเครื่องหมาย ' (Single quote) หรือเครื่องหมาย " (Double quote) 

```ruby
word_1 = 'a'
word_2 = "a"

str_1 = 'This is Ruby Language'
str_2 = "This is Ruby Language"
```

โดยทั้งสองเครื่องหมายจะทำการครอบข้อความให้เป็นสตริงเหมือนกันแต่มีวัตถุประสงค์แตกต่างกัน

## Double Quote (")
เครื่องหมาย double quote จะอนุญาตให้เราใช้ escape sequences ได้ ตัวอักษรที่ตามหลัง \ (Backslash) จะถูก Ruby ตีความว่าเป็นตัวอักษรตัวนั้น

```ruby
puts "Hello in Ruby\."
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>Hello in Ruby.</code></pre>
</details>

>จากตัวอย่างด้านบนเราจะเห็นได้ว่า \\. จะแสดงผลเป็น . อย่างเดียว

```ruby
puts "This line already taken\nAlright I'll go to the new line"
```
<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>This line already taken
Alright I'll go to the new line</code></pre>
</details>

>ขึ้นบรรทัดใหม่เนื่องจากภายในสตริงมี \\n อยู่

นอกจากนี้แล้วการใช้เครื่องหมาย double quote ยังสามารถทำให้เราแทรกค่าจากตัวแปรหรือค่าอื่นๆเข้ามาในสตริงได้ด้วย

```ruby
name = "Yukihiro Matsumoto"
puts "The creator of Ruby language is #{name}."
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>The creator of Ruby language is Yukihiro Matsumoto.</code></pre>
</details>

```ruby
puts "2 plus 2 is #{4}"
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>2 plus 2 is 4</code></pre>
</details>

```ruby
puts "Ten minus five equal five : #{10-5}"
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>Ten minus five equal five : 5</code></pre>
</details>

## Single Quote (')
ในส่วนของเครื่องหมาย single quote นั้นเราจะไม่สามารถแทรกค่าหรือใช้ escape sequences ได้
> ยกเว้น \\' และ \\\ ที่สามารถใช้ได้

```ruby
name = "Yukihiro Matsumoto"
puts 'The creator of Ruby language is #{name}.'
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>The creator of Ruby language is #{name}.</code></pre>
</details>

>จากตัวอย่างด้านบนจะเห็นว่า Ruby แสดงผลตรงส่วนของ #{name} ออกมาแบบนั้นเลยไม่ได้ไปดึงค่าจากตัวแปร name มา

```ruby
puts 'one plus one is equal #{1+1}.'
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>one plus one is equal #{1+1}.</code></pre>
</details>

ตัวอย่างกรณียกเว้นของ \\' และ \\\ 

- กรณี \\'

```ruby
puts '\'First example of exception\''
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>'First example of exception'</code></pre>
</details>

- กรณี \\\

```ruby
puts 'This is backslash \\'
```

<details open>
  <summary><strong>Output</strong></summary>
  <pre><code>This is backslash \</code></pre>
</details>

## *Reference*
- https://blog.appsignal.com/2016/12/21/ruby-magic-escaping-in-ruby.html
