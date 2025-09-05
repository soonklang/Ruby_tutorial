# Instance Methods
## Instance Methods คืออะไร
ในภาษา Ruby, Instance Method คือเมธอดที่ถูกประกาศไว้ในคลาส และสามารถเรียกใช้งานได้ก็ต่อเมื่อมีการสร้างอ็อบเจกต์ (instance object) จากคลาสนั้น ๆ ก่อน 

การสร้าง instance method จะเริ่มใช้คำสั่ง __def__ ตามด้วย ชื่อของ instance method ซึ่งชื่อควรเป็นพิมพ์เล็กทั้งหมดถ้ามีเว้นวรรคให้ใส่ __"_"__ จากนั้นหากมี พารามิเตอร์ที่ต้องการ ให้ใส่ __(พารามิเตอร์1,พารามิเตอร์2,...)__ ตามหลังชื่อของ instance method และใช้ __end__ เพื่อจบเมธอด

instance Methods มักจะใช้เพื่อเข้าถึงหรือปรับเปลี่ยนค่าของตัวแปรอินสแตนซ์ (instance variables) ที่ขึ้นต้นด้วย @ ในอ็อบเจกต์ (instance object) เดียวกัน

## ตัวอย่าง Ruby
```ruby
class BankAccount
  attr_accessor :balance , rate

  def initialize(balance)
    @balance = balance
    @rate = 0.7
  end

  def calc_interest  # instance method
    interest = @balance * @rate
    puts "Interest on balance #{@balance} at rate #{@rate} is #{interest}"
  end
end

account = BankAccount.new(1000)
account.calc_interest
```
## Output
```
Interest on balance 1000 at rate 0.7 is 700.0
```
ต่อมาจะเป็นการเปรียบเทียบ instance methods ของภาษา Ruby กับภาษาอื่นๆ โดยจะเริ่มจากภาษา Java
## ตัวอย่าง Java
```Java
class BankAccount {
    private double balance;
    private double rate;

    public BankAccount(double balance) {
        this.balance = balance;
        this.rate = 0.7;
    }

    // instance method
    public void calcInterest() {
        double interest = balance * rate;
        System.out.println("Interest on balance " + balance + " at rate " + rate + " is " + interest);
    }

    public static void main(String[] args) {
        BankAccount account = new BankAccount(1000);
        account.calcInterest();
    }
}
```
## Output
```
Interest on balance 1000 at rate 0.7 is 700.0
```
จากโค้ดตัวอย่างเมื่อเปรียบเทียบจะเห็นว่า ทางภาษา Java สามารถเข้าถึงตัวแปรอินสแตนซ์ (instance variables) ได้เลย, จะต้องระบุ type ของพารามิเตอร์กับ return type ให้ชัดเจน และเวลาเรียก method ผ่าน object ด้วยวงเล็บเสมอ ส่วนทางภาษา Ruby สามารถเข้าถึงตัวแปรอินสแตนซ์ (instance variables) ได้โดยที่ขึ้นต้นด้วย @ , ไม่ต้องระบุ type และเวลาเรียก method ผ่าน object วงเล็บสามารถใส่หรือไม่ก็ได้

## ตัวอย่าง python
```
class BankAccount:  
    def __init__(self, balance):  
        self.balance = balance  
        self.rate = 0.7  
  
    def calc_interest(self):  
        interest = self.balance * self.rate  
        print(f"Interest on balance {self.balance} at rate {self.rate} is {interest}")  
  
account = BankAccount(1000)  
account.calc_interest()
```
Output
```
Interest on balance 1000 at rate 0.7 is 700.0
```

จากโค้ดตัวอย่างเมื่อเปรียบเทียบจะเห็นว่า ทางภาษา python และ ภาษา Ruby ไม่ต้องระบุ type ของพารามิเตอร์กับ return type แต่ ภาษา python ต้องใส่ self เป็นพารามิเตอร์แรกเสมอ เพื่อเข้าถึง ตัวแปรอินสแตนซ์ (instance variables) และเวลาเรียก method ผ่าน object ด้วยวงเล็บเสมอ ส่วนทางภาษา Ruby สามารถเข้าถึงตัวแปรอินสแตนซ์ (instance variables) ได้โดยที่ขึ้นต้นด้วย @ และเวลาเรียก method ผ่าน object วงเล็บสามารถใส่หรือไม่ก็ได้

## Slide
-
## Video
-
## Reference
