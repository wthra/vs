# ⚔️ RO Guild War — Tactical Board

เครื่องมือวางแผนสงครามกิลด์สำหรับเกม **Ragnarok Origin** โดยเฉพาะโหมด **Vale of Clash (Guild War)**

---

## 🎮 เกี่ยวกับโปรเจค

Ragnarok Origin คือเกม MMORPG มือถือและ PC จาก Gravity ที่นำโลกของ Ragnarok Online มาทำใหม่ในกราฟิก 3D  
โหมด **Guild War / Vale of Clash** คือการสู้แบบกิลด์ต่อกิลด์ โดยแต่ละฝ่ายส่งสมาชิกสูงสุด 40 คน (8 Party × 5 คน) เข้าแย่งชิงพื้นที่และ Throne

Tactical Board นี้ช่วยให้ **Guild Leader และ War Commander** วางแผนการจัดทัพก่อนสงครามได้อย่างชัดเจน

---

## ✨ ฟีเจอร์หลัก

### 🗺️ แผนที่และ Token
- แสดง Token ของแต่ละ Party (P1–P8) บนแผนที่ Vale of Clash
- ลาก-วาง Token เพื่อกำหนดตำแหน่งจัดทัพ
- Token มี animation glow และ floating effect ตามธีมเกม

### ✏️ Drawing Tools (Admin Only)
| Tool | ฟังก์ชั่น |
|------|-----------|
| ✦ Move | เลื่อน Party token บนแผนที่ |
| ✎ Pen | วาดเส้นบนแผนที่อิสระ |
| ⌫ Erase | ลบเส้นที่วาด |
| ➔ Arrow | วาดลูกศรแสดงทิศทางการเคลื่อนที่ |
| T Label | ใส่ข้อความ label บนแผนที่ (ลบได้ด้วยปุ่ม ✕ หรือดับเบิลคลิก) |
| 🗑 Clear | ลบทุกเส้นที่วาด |
| ↩ Undo | ย้อนการกระทำ |
| 📷 Export | บันทึกแผนที่เป็นรูปภาพ |
| ✕ Close | ปิดหน้าต่าง toolbar (กด 🛠 Tools เพื่อเปิดใหม่) |

> ✅ **ลบ Label ได้แล้ว** — โฮเวอร์ที่กล่องข้อความจะมีปุ่ม ✕ มุมขวาบน
> ✅ **ปิด/เปิดหน้าต่าง Drawing Tools ได้แล้ว** — ปุ่ม ✕ บน toolbar / ปุ่ม 🛠 Tools เพื่อเปิดกลับ
> ✅ **บันทึกแผนการเล่น (Saved Plans)** — Admin บันทึกได้, Viewer เปิดดูแผนที่บันทึกไว้ได้

### 👥 จัดการ Party
- ตั้งชื่อ Party และชื่อสมาชิกแต่ละคน (5 คน/Party)
- บันทึกข้อมูลไว้ใน localStorage อัตโนมัติ
- รองรับ 8 Party สีต่างกันชัดเจน

### 🐉 Token เป็นมอนสเตอร์ RO จริง
แต่ละ Party ใช้สไปรท์มอนสเตอร์จริงจาก **divine-pride.net** (มี emoji สำรองถ้าโหลดรูปไม่ขึ้น):

| Party | มอนสเตอร์ | mob id |
|-------|-----------|:------:|
| P1 | Poring 🫠 | 1002 |
| P2 | Wolf 🐺 | 1013 |
| P3 | Ghostring 👻 | 1120 |
| P4 | Lunatic 🐰 | 1063 |
| P5 | Fabre 🐛 | 1007 |
| P6 | Spore 🍄 | 1014 |
| P7 | Chonchon 🦗 | 1011 |
| P8 | Angeling 😇 | 1096 |

> เปลี่ยนมอนสเตอร์ได้ที่ตัวแปร `JOBS` (ใส่ `mob` = id จาก divine-pride)

### ✨ Animation & UX (ดูโปร พร้อมขาย)
- **Token เดินโยกตัว** ตอนสลับ Phase/แผน (glide + walk-bob)
- **ลูกศรมีจุดวิ่งไหล** ตามทิศทางการเคลื่อนที่
- **Toast notifications** ตอน Save / Export / Login / Reset
- Ambient glow + tactical grid + vignette บนแผนที่
- Panel/card entrance animation, micro-interactions, ฟอนต์เกม Cinzel
- Custom scrollbar ธีมทอง, modal login เด้งเข้าแบบ spring

### 📋 Formation System (Saved Plans)
- บันทึกแผนที่ใช้บ่อยไว้โหลดกลับมาได้ — Admin บันทึก/ลบได้, Viewer เปิดดูได้
- รองรับหลาย Phase การรบ พร้อม animation เดินเปลี่ยนตำแหน่ง

### 📝 Battle Notes
- พื้นที่จดบันทึกคำสั่ง/แผนการรบ
- มองเห็นได้ทั้ง Admin และ Viewer

### 🔐 Admin / Viewer Mode
- **Admin**: วางแผน แก้ไข วาด จัดตำแหน่งได้ทุกอย่าง
- **Viewer**: ดูแผนที่แบบ read-only สำหรับสมาชิกในกิลด์

---

## 🚀 วิธีใช้งาน

1. เปิดไฟล์ `ro-tactical-board.html` ในเว็บบราวเซอร์
2. กด **🔑 Admin** เพื่อ login
   - Username: `admin`
   - Password: `admin123`
3. ลาก Token ไปวางตำแหน่งบนแผนที่
4. ใช้ Toolbar วาดลูกศรและ Pen อธิบายเส้นทาง
5. กด **📷 Export** เพื่อแชร์แผนให้สมาชิกกิลด์

---

## 🛠️ Tech Stack

- **Vanilla HTML / CSS / JavaScript** — ไม่มี dependency ภายนอก
- **SVG** — สำหรับ render ลูกศรและ drawing layer
- **Canvas API** — สำหรับ Pen และ Erase tool
- **localStorage** — บันทึกข้อมูลในเครื่อง
- **Glassmorphism UI** — ธีมมืด + ทอง ตามสไตล์เกม RO

---

## 📁 ไฟล์ในโปรเจค

```
vs/
├── ro-tactical-board.html   # ไฟล์หลัก (เปิดในเว็บได้เลย)
└── README.md                # เอกสารนี้
```

---

> **Made for Ragnarok Origin Guild War commanders** ⚔️  
> Vale of Clash · Guild Battle Planning Tool
