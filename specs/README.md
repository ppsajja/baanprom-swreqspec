# ดัชนี specs

| โฟลเดอร์ | Use case | ฟีเจอร์ | สถานะ | ผู้รับผิดชอบ |
|---|---|---|---|---|
| 000-shared | ทุก use case | Constraint กลางที่ใช้กับทุก feature (constraints.md) ไม่ใช่ feature | รุ่น 1.0 (B2, CR-04) | RE lead กลุ่ม X |
| 002-booking | UC-07 | จองงานบริการซ่อมบำรุง (ทำครบรอบ clarify, plan, tasks, implement, test และรอบเปลี่ยนแปลง CR-03, CR-04) | spec 1.4 (B2 = B1 + CR-01, CR-03, CR-04) | กลุ่ม X |
| 003-job-status | UC-09 | ช่างอัปเดตสถานะงาน | Draft ยังไม่เข้า Baseline ยังไม่ได้ /plan | กลุ่ม X |

001-booking (ตัวอย่างจองคิวตรวจสุขภาพของรายวิชาปริญญาตรี ที่มากับ template) ถูกลบออกหลังใช้ซ้อมใน Studio ช่วงที่ 1

กติกา
- 1 โฟลเดอร์ = 1 ฟีเจอร์ระดับ use case ชื่อโฟลเดอร์ขึ้นต้นด้วยเลข 3 หลัก ตามด้วยชื่อฟีเจอร์ภาษาอังกฤษตัวเล็ก
- เลข 000 สงวนไว้ให้ของที่ใช้ร่วมกันทุก feature
- spec.md ของทุก feature อ้าง Constraint กลางด้วยบรรทัดเดียวในส่วน 8 ไม่คัดลอกข้อความ (ดู docs/shared-constraints-guide.md)
