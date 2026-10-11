# baanprom-swreqspec

repo ตัวอย่างของรายวิชา 517 511 Requirements Engineering (AI-Native RE)
ภาควิชาคอมพิวเตอร์ คณะวิทยาศาสตร์ มหาวิทยาลัยศิลปากร | ภาคต้น 1/2569

เคส: บ้านพร้อม (แพลตฟอร์มจองช่างซ่อมบ้าน) feature ที่ทำครบรอบคือ UC-07 จองงานบริการซ่อมบำรุง
ข้อมูลทั้งหมดในเคสนี้เป็นข้อมูลสมมติเพื่อการสอน

repo นี้คือสภาพงานของกลุ่มตัวอย่าง (กลุ่ม X) หลังจบ 2 บทเรียน
- รอบแรก บทเรียน "ให้ AI สร้างจากสเปก" (4 ต.ค. 2569): clarify, plan, tasks, implement, test จนได้ Baseline B1 + CR-01
- รอบเปลี่ยนแปลง บทเรียน "Verification, Traceability และ Change" (11 ต.ค. 2569): ตามรอยด้วย rtm.md เอาหน้าจอ (mockup) เข้าสเปกด้วย CR-03 ย้าย Constraint ที่ใช้ทุก feature ไปไฟล์กลางด้วย CR-04 แล้วรัน test ทั้งชุดซ้ำ จนได้ Baseline B2

ทุกไฟล์ที่ AI สร้างถูกเก็บไว้ตามที่สร้างจริง รวมถึงจุดที่ AI ทำผิดกติกาและทีมสั่งแก้ (ดู gaps.md และ prompt-log.md)

## ทีม

- ชื่อทีม: กลุ่ม X (ตัวอย่างของรายวิชา)
- สมาชิก: สมาชิก A, สมาชิก B, สมาชิก C, สมาชิก D
- เครื่องมือ AI ที่ใช้: Copilot Chat โหมด Agent ใน GitHub Codespaces (ผู้สอนเดโมด้วย Claude Code)

## โครงของ repo

```
README.md                      ไฟล์นี้
AGENTS.md                      กติกาที่ AI ต้องทำตาม 10 ข้อ (agent-pack รุ่น 2 เพิ่มข้อ 9 Constraint กลาง และข้อ 10 mockup)
CLAUDE.md                      ชี้ไป AGENTS.md (สำหรับ Claude Code)
prompt-log.md                  บันทึกทุกคำสั่ง คำถาม คำตอบ และสิ่งที่ AI เดา (เพิ่มต่อท้ายเท่านั้น)
docs/srs/                      ต้นฉบับจากบทเรียนก่อนหน้า: catalogue, UC-07, glossary, baseline (B1 และ B2)
docs/agent-pack-README.md      วิธีใช้ชุดคำสั่ง รุ่น 2
docs/shared-constraints-guide.md  วิธีใช้ Constraint กลาง
docs/mockup-guide.md           วิธีเอา mockup เข้าสเปก และรายการตรวจหน้าจอ 6 ข้อ
docs/cr-template.md, rtm-template.md, mockup-template.html, constraints-template.md   แบบของ CR ตารางตามรอย mockup และไฟล์ Constraint กลาง
specs/README.md                ดัชนี feature
specs/000-shared/constraints.md   Constraint กลาง ใช้กับทุก feature เขียนที่เดียว (CR-04)
specs/002-booking/             feature ที่ทำครบรอบ (ดูตารางด้านล่าง)
specs/003-job-status/          feature ที่สอง ยังเป็นร่าง มีไว้ให้เห็นว่า spec ใหม่อ้าง Constraint กลางอย่างไร
backend/                       Python FastAPI + SQLAlchemy (test ใช้ SQLite ในหน่วยความจำ)
frontend/                      React (Vite) + Tailwind CSS + Vitest
.github/prompts/               คำสั่ง /clarify /plan /tasks /implement สำหรับ Copilot
.claude/commands/              คำสั่งชุดเดียวกัน สำหรับ Claude Code
.cursor/commands/              คำสั่งชุดเดียวกัน สำหรับ Cursor
```

## ไฟล์ใน specs/002-booking/ และใครสร้าง

| ไฟล์ | ใครสร้าง | เกิดในขั้นไหน |
|---|---|---|
| spec.md | กลุ่มเขียน v1, AI แก้เป็น v2 หลัง /clarify, กลุ่มแก้ v3 ผ่าน CR-01, กลุ่มแก้ 1.3 ผ่าน CR-03 และ 1.4 ผ่าน CR-04 | บทเรียน Living Specification, /clarify และรอบเปลี่ยนแปลง |
| booking.feature | กลุ่ม (จากบทเรียน Acceptance Criteria) | ก่อน /clarify |
| rules.md, models.md | กลุ่ม (สรุปจาก docs/srs) | ก่อน /clarify |
| plan.md | AI (/plan) ทีมตรวจแล้ว รอบเปลี่ยนแปลงสั่ง AI แก้เฉพาะหัวข้อที่ CR กระทบ | /plan และรอบเปลี่ยนแปลง |
| plan-compare.md | กลุ่ม | เทียบ plan ของ AI กับที่กลุ่มเขียนเอง |
| tasks.md | AI (/tasks) ทีมสั่งแก้ 1 รอบ รอบเปลี่ยนแปลงเพิ่ม T-12 ถึง T-16 ต่อท้าย | /tasks และรอบเปลี่ยนแปลง |
| tasks-compare.md | กลุ่ม | เทียบ tasks ของ AI กับที่กลุ่มเขียนเอง |
| test-run.txt | pytest และ vitest (ผลรันจริง รอบล่าสุด) | รัน test ทั้งชุด |
| test-run-round3.txt | vitest (ผลรันจริงรอบที่ไม่ผ่าน 2 ตัว) | รันซ้ำทั้งชุดครั้งแรกหลังการเปลี่ยนแปลง |
| ac-results.md | กลุ่ม | กรอกจาก test-run.txt |
| gaps.md | กลุ่ม | ทุกครั้งที่พบจุดพลาด |
| changes/CR-01.md, CR-02.md | กลุ่ม | เมื่อต้องแก้สิ่งที่อยู่ใน Baseline B1 |
| rtm.md | AI ร่าง กลุ่มตรวจทุกแถวและเขียนช่อง "ทีมตัดสิน" | รอบเปลี่ยนแปลง ขั้นตามรอย |
| mockups/ (3 หน้า .html และ .png) | กลุ่มวาดกับเจ้าของ AI แปลงเป็น HTML | รอบเปลี่ยนแปลง ก่อน /clarify |
| changes/CR-03.md | AI ร่างจาก /clarify กลุ่มเติมผลกระทบ SH-01 อนุมัติ | เอาหน้าจอเข้าสเปก |
| changes/CR-04.md | กลุ่ม | ย้าย Constraint ไปไฟล์กลาง |
| ui-review/ | กลุ่ม (ภาพหน้าจอจริงและผลตรวจ 6 ข้อ) | หลัง /implement หน้าจอ |
| quality-requirements.md | กลุ่ม | บทเรียนข้อกำหนดคุณภาพ |

## วิธีรัน

หลังบ้าน

```
cd backend
pip install -r requirements.txt
pytest -v -k "AC_" 2>&1 | tee ../specs/002-booking/test-run.txt
uvicorn app.main:app --reload --port 8000
```

หน้าจอ

```
cd frontend
npm install
npm test
npm run dev
```

(ถ้าเปิดด้วย GitHub Codespaces คำสั่ง pip install และ npm install ถูกรันให้แล้วตอนสร้างเครื่อง)

## อ่านรอบเปลี่ยนแปลงตามลำดับนี้

| ลำดับ | เปิดไฟล์ | ดูอะไร |
|---|---|---|
| 1 | specs/002-booking/rtm.md | สายตามรอยที่ขาด 8 ข้อ ทั้งที่ test รอบก่อนผ่านเกือบหมด |
| 2 | specs/002-booking/mockups/ | แบบหน้าจอ 3 หน้า กล่องเส้นประคือเรื่องที่ยังเป็นคำถาม |
| 3 | specs/002-booking/changes/CR-03.md | ตาราง "เดิม และ ใหม่" กับตารางผลกระทบ และแถวที่ถูกเพิ่มทีหลัง |
| 4 | specs/000-shared/constraints.md และ changes/CR-04.md | Constraint กลาง และเหตุผลที่ต้องมี |
| 5 | specs/002-booking/spec.md ส่วน 8 และ 12 | บรรทัดอ้างบรรทัดเดียว และรายการ "ต้องตรง" ของหน้าจอ |
| 6 | specs/002-booking/tasks.md T-12 ถึง T-16 | task ที่เพิ่มต่อท้าย ไม่ได้รัน /tasks ใหม่ |
| 7 | specs/002-booking/ac-results.md รอบที่ 3 และ 4 | ของเดิมที่พังเพราะการเปลี่ยนแปลง และวิธีแก้ |
| 8 | specs/002-booking/ui-review/ui-review.md | ตรวจหน้าจอจริงเทียบ mockup ด้วยคน |
| 9 | docs/srs/baseline.md | Baseline B2 ต่างจาก B1 อย่างไร |

## ถ้าจะทำของกลุ่มเอง

อย่า fork repo นี้ ให้ไปที่ template ของรายวิชา github.com/ppsajja/reqeng-template กด Use this template
แล้วเอาไฟล์ของกลุ่มใส่ตาม README ของ template repo นี้มีไว้เปิดดูเทียบทีละขั้นเท่านั้น

## สิ่งที่รู้อยู่แล้วว่ายังไม่ใช่ของจริง

- ทุก endpoint รับ `now=...` ใน query เพื่อให้ test กำหนดเวลาได้ (backend/app/clock.py) ก่อนขึ้นระบบจริงต้องปิดช่องนี้
- FakeGateway ใช้แทน Payment Gateway จริง (IF-01) และคิวแจ้งเตือนอยู่ในหน่วยความจำ (IF-02)
- ระยะทาง BR-03 ใช้สูตรคำนวณจากพิกัดแทนบริการแผนที่ (IF-03)
- AC-07-08 ผ่านแบบย่อส่วน 20 คำขอเท่านั้น ผลตรวจรับจริงต้องวัดบนเครื่องทดสอบ (รอ CR-02)
- ตอน test คำขอที่ใช้ SQLite เข้าฐานข้อมูลทีละคำขอ (backend/app/db/session.py, GAP-15) ระบบจริงใช้ PostgreSQL ไม่ผ่านเงื่อนไขนี้
- หน้าจอยังไม่แสดงราคาประเมิน ไม่มีปุ่มเข้าคิวรอ และไม่ให้เลือกที่อยู่ เพราะยังเป็น Q-26, Q-28, Q-29
- ลูกค้าและที่อยู่บนหน้าจอเป็นค่าคงที่ (ลูกค้า 1 ที่อยู่ 1) เพราะการเข้าสู่ระบบเป็นของอีก use case
- `backend/seed_demo.py` ใส่ข้อมูลสมมติไว้เปิดดูหน้าจอ ไม่ใช่ส่วนของระบบ

## Reflection ของกลุ่ม X (5 บรรทัด)

1. คำถามของ AI ที่ไม่คาดคิด: ถามว่า "ใกล้เคียง" ใน AC-07-04 หมายถึงกี่ชั่วโมง ทั้งทีมไม่เคยสงสัยเลยจนกระทั่งต้องเขียน assert
2. คำถามของเพื่อนที่ AI ไม่ถาม: กลุ่มข้างเคียงถามว่าถ้าลูกค้าปิดเบราว์เซอร์ระหว่างล็อกช่วงเวลา ใครปลดล็อก (AI ถือว่าหมดอายุเองโดยไม่ถาม)
3. กฎที่ AI ละเมิดและจับได้: /implement T-01 แตะ router.py ซึ่งเป็นไฟล์ของ T-04 (กติกา "แตะเฉพาะไฟล์ในช่องไฟล์ที่แตะ") และ /tasks ตั้ง T-06 เป็นพร้อมทำทั้งที่ R3 รอ Q-14
4. สิ่งที่สเปกของกลุ่มคุมได้: ทุก endpoint อ้าง REQ ได้ ไม่มีฟีเจอร์เกิน ไม่มีคอลัมน์เบอร์โทรใน log และช่างไม่เห็นเบอร์ก่อน 2 ชั่วโมง
5. สิ่งที่หลุด: ค่า timeout ของ gateway ที่สเปกกับ Interface Contract บอกไม่ตรงกัน (GAP-07) และ "ระบบต้องเร็ว" ที่ยังวัดไม่ได้จนต้องเปิด CR-02

## Reflection ของกลุ่ม X รอบเปลี่ยนแปลง (5 บรรทัด)

1. สิ่งที่ตารางตามรอยเจอแต่ test ไม่เจอ: REQ-BR-002 ไม่มี AC เลย ยอดมัดจำถูกตัดจากตารางที่ไม่มีอะไรตรวจ และ test ทั้งชุดผ่านมาตลอด
2. สิ่งที่ mockup พาเข้ามาโดยไม่มีใครขอ: คะแนนรีวิวของช่าง (อยู่ใน Non-goals) ราคาประเมิน และปุ่มเข้าคิวรอ /clarify จับได้ก่อนถึงมือ AI ที่เขียนโค้ด
3. ผลกระทบที่วิเคราะห์พลาด: CR-03 ไล่จาก REQ ถึง task แต่ไม่ถึง test หน้าจอเดิม จึงรู้ตอน AC-07-04.test.jsx ไม่ผ่านในรอบที่ 3
4. สิ่งที่ไฟล์กลางช่วยได้จริง: สเปกของ feature ที่สองไม่ต้องคัดลอก Constraint 3 ข้อ และเทคโนโลยีที่ทีมเลือกมีที่จดที่ทุก feature มองเห็น (ยังไม่ได้รัน /plan ของ feature ที่สองซ้ำเพื่อยืนยันว่า AI เลิกถามเรื่องนี้)
5. สิ่งที่ยังไม่ปิด: Q-26 ถึง Q-29 และข้อค้นพบ F-05 ถึง F-08 เราเลือกปล่อยไว้เป็นคำถามที่มีเจ้าของ ดีกว่าให้ AI หรือเราเดาคำตอบ
