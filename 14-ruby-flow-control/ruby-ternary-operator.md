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


<img width="935" height="127" alt="image" src="https://github.com/user-attachments/assets/00f92b05-0559-4774-abf3-db1949d1a565" />



เป็นการเอาเงื่อนไข เอาเข้าไปใส่ในเงื่อนไขอีกที แต่ไม่แนะนำ เพราะจะยิ่งทำให้โค้ดอ่านยาก 


# การเขียน ternary operator กับภาษาอื่นๆ เพื่อเปรียบเทียบ 
<img width="523" height="242" alt="image" src="https://github.com/user-attachments/assets/bc002c36-e20e-4a7a-9d94-6448a263c396" />



<img width="1015" height="56" alt="image" src="https://github.com/user-attachments/assets/822286ce-dfb8-4899-8121-ad099a8e4537" />



ในภาษา Python syntax จะค่อนข้างแตกต่างกับ Ruby


<img width="508" height="303" alt="image" src="https://github.com/user-attachments/assets/9ad2fafb-3802-4703-ac01-48b76b715583" />



<img width="997" height="72" alt="image" src="https://github.com/user-attachments/assets/d6f8c5af-4c6f-4c91-aabd-934c7f5f7921" />

ในภาษา javascript syntax จะเหมือน ruby เลยแต่ Ruby ไม่จำเป็นต้องประกาสตัวแปล body


<img width="565" height="307" alt="image" src="https://github.com/user-attachments/assets/f4243fd1-8a30-4ea9-b580-b716dd414cdf" />



<img width="1058" height="57" alt="image" src="https://github.com/user-attachments/assets/3db34aea-7b19-493b-9022-0796902ea4ec" />


ในภาษา java syntax จะเหมือน ruby และ javascript เลยแต่ Ruby ไม่จำเป็นต้องประกาสตัวแปล body
