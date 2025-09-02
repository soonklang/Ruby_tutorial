# Ruby Class Inheritance
---
## Class Inheritance คืออะไร?

Inheritance(การสืบทอด) คือ การที่เราสามารถสร้าง class ใหม่ขึ้นมาโดยใช้ class ที่มีอยู่แล้วเป็นต้นแบบ(superclass) โดยยังมี variable และ method ของของ class นั้นๆอยู่ เพื่อนำมาสร้าง class ที่มีความคล้ายกันแต่สามารถเพิ่ม variable และ method ใหม่ๆได้(subclass)

### ประเภทของ Inheritance
- **Single inheritance(การสืบทอดเดี่ยว)** คือ class หนึ่งสืบทอดมาจาก class เพียง class เดียว
- **Multiple inheritance(การสืบทอดหลายรายการ)** คือ class หนึ่งสามารถสืบทอดมาจาก หลายๆ class พร้อมกันได้
- **Multilevel inheritance(การสืบทอดหลายระดับ)** คือ class หนึ่งสืบทอดมาจากอีก class ที่สืบทอด class อื่นมาอีกที
- **Hierarchical inheritance(การสืบทอดแบบลำดับชั้น)** คือ มีหลาย class สืบทอดมาจาก class เพียง class เดียว 
- **Hybrid inheritance(การสืบทอดแบบผสม)** คือ การรวมกันระหว่างประเภทของ Inheritance ตั้งแต่ 2 ขึ้นไป
 
โดยภาษา Ruby นั้นไม่รองรับ **Multiple inheritance** แต่ว่าสามารถใช้ **Mixins** (via Modules) แทนได้

---

## การใช้งาน Class Inheritance ใน Ruby

- การสืบทอดใน Ruby สามารถทำได้โดยใช้เครื่องหมาย `<`
### Syntax ตัวอย่าง
```ruby
class subclass_name < superclass_name 
```
