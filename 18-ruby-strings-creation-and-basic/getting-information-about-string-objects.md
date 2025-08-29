---
description: นฤดม ศรีปัญญา 660710604
icon: memo-circle-info
cover: >-
  https://images.unsplash.com/photo-1551122089-4e3e72477432?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwzfHxydWJ5fGVufDB8fHx8MTc1NjQ2OTQ3Nnww&ixlib=rb-4.1.0&q=85
coverY: -172.19158075601376
layout:
  width: default
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Getting Information About String Objects

เมื่อเราสร้างตัวแปร Variable ที่มีค่าเป็น String นั้น Variable ในภาษา Ruby ถือว่าเป็น Object อย่างหนึ่ง ซื่งเมื่อตัวแปรนั้นเก็บค่า String แล้ว Object นั้นจะมี Method หลากหลายที่เก็บข้อมูลเกี่ยวกับ String ที่เราสามารถเรียกใช้ได้

***

## <mark style="color:$danger;">ตัวอย่าง</mark> Method

### .length หรือ .size

สองเมธอดนี้จะทำการคืนค่าความยาวของข้อความของตัวแปรนั้นๆ

```ruby
# สร้างตัวแปรชื่อ text ที่เก็บค่าสตริงคือ "I love Ruby."
text = "I love Ruby."
puts text.length # Output: 12
```

***



