# Instance Methods
## Instance Methods คืออะไร
ในภาษา Ruby, Instance Method คือเมธอดที่ถูกประกาศไว้ในคลาส และสามารถเรียกใช้งานได้ก็ต่อเมื่อมีการสร้างอ็อบเจกต์ (instance object) จากคลาสนั้น ๆ ก่อน 

การสร้าง instance method จะเริ่มใช้คำสั่ง def ตามด้วย ชื่อ instance method ซึ่งชื่อควรเป็นพิมพ์เล็กทั้งหมด จากนั้นหากมี พารามิเตอร์ที่ต้องการ ให้ใส่ (พารามิเตอร์1,พารามิเตอร์2,...) ตามหลังชื่อ และใช้ end เพื่อจบเมธอด

instance Methods มักจะใช้เพื่อเข้าถึงหรือปรับเปลี่ยนค่าของตัวแปรอินสแตนซ์ (instance variables) ที่ขึ้นต้นด้วย @ ในอ็อบเจกต์ (instance object) เดียวกัน

## ตัวอย่างการสร้าง instance Methods ในภาษา Ruby
```ruby
class BankAccount
  attr_accessor :balance

  def initialize(balance)
    @balance = balance
  end

  def calc_interest(rate)  # instance method
    interest = @balance * rate
    puts "Interest on balance #{@balance} at rate #{rate} is #{interest}"
  end
end

# create object (instance)
account = BankAccount.new(1000)
account.calc_interest(0.7)
```
## Output
```
Interest on balance 1000 at rate 0.7 is 700.0
```
