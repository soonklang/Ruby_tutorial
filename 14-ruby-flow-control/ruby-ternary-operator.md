# Ruby Ternary Operator
Ternary operator คือ ตัวดำเนินการที่ใช้เขียนเงื่อนไขแบบย่อ ในบรรทัดเดียว แทนการใช้ if  else แบบเต็ม
# ตัวอย่างการเขียน if else ใน Ruby
<img width="377" height="213" alt="image" src="https://github.com/user-attachments/assets/d28dc935-1951-49f8-832e-7082f3b7f7bb" />


# ตัวอย่าง Ternary Oparator ใน Ruby
<img width="447" height="101" alt="image" src="https://github.com/user-attachments/assets/81125430-b010-44b1-928c-3a6555e5e1b9" />


จะเห็นได้ว่า การเขียนแบบ Ternary Operator ทำให้โค้ด if else มีความกระชับ ลดบรรทัดในการเขียน
แต่มีข้อควรระวังคือ เหมาะกับ if else ที่มีเงื่อนไขไม่ซับซ้อน หากมีเงือนไขที่ซับซ้อมเกินไป ควรใช้ if else ปกติ


# ส่วนประกอบของ Ruby ternary operator
ประกอบด้วย 3 ส่วน คือ เงื่อนไข ? ค่าที่ได้เมื่อเงื่อนไขเป็นจริง : ค่าที่ได้เมื่อเงื่อนไขเป็นเท็จ

# ปกติ ternary operator ถูกออกแบบมาให้ใช้กับแค่ 2 เงื่อนไข แต่ถ้าต้องการเขียนแบบ 3 เงื่อนไขก็สามารถเขียนได้
รูปแบบ if else ปกติ 


<img width="477" height="272" alt="image" src="https://github.com/user-attachments/assets/76a62418-f523-48cd-9aa8-bcd06be7791a" />


รูปแบบ ternary operator 


<img width="1026" height="92" alt="image" src="https://github.com/user-attachments/assets/f895dfd3-09cf-4a95-9ef8-53b2f300f82d" />


เป็นการเอาเงื่อนไข เอาเข้าไปใส่ในเงื่อนไขอีกที แต่ไม่แนะนำ เพราะจะยิ่งทำให้โค้ดอ่านยาก 
