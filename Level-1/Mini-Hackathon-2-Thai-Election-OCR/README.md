# Mini Hackathon 2 : Thai Election OCR

Extract structured voting data from scanned Thai election result documents (Form สส.6/1) from the 2026 Thai general election.

Given PNG scans of official election documents, your task is to:

1. Locate the correct row for each party in the voting tables
2. Extract the corresponding vote count
3. Convert all numbers to Arabic digits (0-9)

Party names are pre-filled in the submission template — you only need to predict the vote counts.

ภารกิจคือการดึงจำนวนคะแนนเสียงจากเอกสารผลการเลือกตั้งไทยที่สแกนไว้

สำหรับแต่ละแถวในการส่งผลงาน ให้ทำนายค่า vote count ของ id ที่กำหนด public reference template มี metadata ของเอกสารเพื่อช่วยในการจัดแนวผล OCR แต่คีย์ที่ใช้สำหรับการส่งผลงานอย่างเป็นทางการคือ id

ข้อมูล:
- 300 documents
- 846 PNG page images
- 10,053 submission rows
- public reference files ประกอบด้วย <b>*submission_template_v3.csv*</b>

หมายเหตุ:
- มีเอกสารแบบบัญชีรายชื่อบางส่วนใน public template เดิมที่มีชื่อพรรคแบบ placeholder หรือไม่สมบูรณ์
- template ฉบับปรับปรุงได้ทำ normalization ของ placeholder เหล่านี้สำหรับการใช้งานสาธารณะแล้ว
- ค่า submission id ไม่มีการเปลี่ยนแปลง
รูปแบบการส่ง
ให้ส่งไฟล์ CSV ที่มีคอลัมน์ดังนี้เท่านั้น:
```
id,votes
```
กติกา:
- ห้ามแก้ไข id
- ต้องส่งให้ครบทุกแถว
- votes ต้องเป็นเลขอารบิกเท่านั้น
- party_name ไม่ใช่ส่วนหนึ่งของรูปแบบ submission

การให้คะแนน:
ระบบให้คะแนนอย่างเป็นทางการต้องใช้เพียง:
- id
- votes

Metric:
- คำนวณ Levenshtein distance ระหว่าง votes ที่ทำนายกับ votes จริงในแต่ละแถว
- คะแนนสุดท้าย = mean Levenshtein distance เฉลี่ยทุกแถว
- ค่ายิ่งต่ำยิ่งดี