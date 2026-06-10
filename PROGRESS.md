# 🛠️ PROGRESS / HANDOFF — RO Tactical Board

> ไฟล์นี้สรุปว่าทำอะไรไปแล้ว + ต่ออะไร เผื่อเปิดงานต่อคนละเครื่อง (บริษัท/บ้าน) หรือ Claude session ใหม่
> อัปเดตล่าสุด: 2026-06-10

## ไฟล์ในโปรเจค
- `ro-tactical-board.html` — **ไฟล์หลักไฟล์เดียว** (vanilla HTML/CSS/JS, เปิดดับเบิลคลิกได้เลย ~480KB)
- `11.png` — รูปแผนที่เริ่มต้น (Vale of Clash)
- `README.md` — requirement (ภาษาไทย, มีคอมเมนต์สั่งงานฝังอยู่)
- `features.md` — รายการฟีเจอร์เดิม

## Stack / กติกา
- **Vanilla ล้วน ไฟล์เดียว — ไม่ใช้ Next.js** (ผู้ใช้ยืนยัน) เปิดออฟไลน์ได้
- Firebase Realtime DB (CDN v9.23) sync เรียลไทม์ + localStorage (key `ro_gw10`) เป็น fallback
- สไปรท์มอนสเตอร์จาก divine-pride.net, ฟอนต์ Cinzel (Google Fonts) — ต้องต่อเน็ต ถ้าออฟไลน์ fallback เป็น emoji/ฟอนต์ระบบ
- Login: admin / admin123 (hardcode ใน `tryLogin`). Admin แก้ได้ / Viewer อ่านอย่างเดียว

## ✅ ทำเสร็จแล้ว (ทดสอบ syntax ผ่านหมด)
1. **Token = มอนสเตอร์ RO จริง** — array `JOBS` (mob id: Poring1002, Wolf1013, Ghostring1120, Lunatic1063, Fabre1007, Spore1014, Chonchon1011, Angeling1096), มี emoji สำรองผ่าน `mobNode()`. เลขปาร์ตี้ขยายใหญ่ขึ้น
2. **Drawing tools** — pen/erase/arrow/label/clear/undo/export; ลูกศรมีจุดวิ่งไหล; label มีปุ่ม ✕ ลบ; toolbar ปิด/เปิด (🛠 Tools) ได้
3. **Saved Plans (Formations)** — admin save/ลบ, viewer ดูได้; **Play/Replay** (`startReplay`) เดินไล่ทุกแผนอัตโนมัติ; ปุ่ม `btnSpeed` ปรับความเร็ว 1/1.5/2/0.5×
4. **Token เดินโยกตัว** ตอนสลับแผน (`animateFormation`)
5. **Polish ระดับขาย** — toast, Cinzel, scrollbar ทอง, ambient glow + grid + vignette, entrance/hover animation, modal เด้งสปริง
6. **Header มอนสเตอร์เดินเล่น** (`initHeaderMobs`) — วิ่งหนีเมาส์, hover เห็นชื่อ, คลิกเด้ง+particle
7. **Ambient juice** — `#fxCanvas` หมอกอนุภาคเขียว (55 ตัว), token emote สุ่ม, click ripple, **ใบไม้ร่วง 🍃** (ทุก 680ms)
8. **Map Switcher** (`setMap`/`renderMapList`) — ดรอปดาวน์ `mapSelect` + อัปโหลด `mapUpload` (DataURL); state `maps[]`+`curMap` sync เป็น `mp`/`cm`; แต่ละแผนจำแมพ (`f.map`)
9. **แก้บั๊ก** — Party notes พิมพ์ไม่ได้ตอน login admin (แก้ `.pnotes` ใน applyMode); style ช่อง fmName หาย

## ❌ ลบออกตามคำสั่งผู้ใช้
- GvG Timer และ Objective Markers (Throne/Emperium/Flag/Portal) — ลบหมดแล้ว ไม่มีค้าง

## 🔜 ต่อไป (ผู้ใช้สนใจ — เพื่อขาย)
- **Guild branding / White-label** — ตั้งชื่อกิลด์ + โลโก้ + สีธีม + ลายน้ำตอน export (อธิบายผู้ใช้แล้ว ยังไม่ทำ) ← น่าทำต่ออันนี้
- ไอเดียอื่น: โซน AoE (วงกลม/สี่เหลี่ยม), วัดระยะ, export PDF ทุก Phase, login จริงต่อกิลด์, แมพ preset หลายอัน

## ⚠️ หมายเหตุการแก้โค้ด (สำคัญ)
- inline `<script>` เริ่มที่ `var MI=`
- เช็ค syntax: ดึง JS ระหว่าง `var MI=` ถึง `</script>` แล้ว `node --check`
- ไฟล์เดิมมี **mojibake บางตัว** (เช่นอักขระเสียในโค้ดเก่า) ที่ Edit match ไม่ติด — ให้ override ด้วยการ assign ใหม่ อย่าพยายาม match ตัวที่เสีย
- เลขบรรทัดขยับบ่อย — ใช้ Grep หาตำแหน่งล่าสุดก่อนแก้เสมอ


 เเก้ส่วนใบไม้ ให้เเสดง ขึ้น ต่อเมื่อเอาเมาส์ไปชี้ บริเวณสีเขียวภายในเเมพ  ลดการใบไม้ร่วงหน่อย  emoji ที่เอามาขอสมจริงกว่านี้หน่อย




 อีโมจิที่เเสดงอาการ ให้อิงจาก emoji ภายในเกม ragnarok gravity pc ก็ได้ 


 ตอนนี้โทนเคนหมดถึงตรงนี้

  เเก้ส่วนใบไม้ ให้เเสดง ขึ้น ต่อเมื่อเอาเมาส์ไปชี้ บริเวณสีเขียวภายในเเมพ  ลดการใบไม้ร่วงหน่อย  emoji ที่เอามาขอสมจริงกว่านี้หน่อย

เข้าใจครับ — ใบไม้จะโผล่เฉพาะตอนเอาเมาส์ชี้พื้นที่สีเขียวบนแมพ, ลดความถี่, และใช้ emoji สมจริงขึ้น (🍃🍂🍁)

1) CSS ใบไม้ (เอา top บังคับออก):

● Update(vs\ro-tactical-board.html)
Added 3 lines, removed 3 lines
/* ── AMBIENT FX: particle fog ── */
#fxCanvas{position:absolute;inset:0;z-index:4;pointer-events:none;}

/* ── FALLING LEAVES (forest vibe) ── */
@keyframes leafFall{0%{opacity:0;transform:translate(0,-14px) rotate(0deg);}8%{opacity:.95;}100%{opaci
ty:0;transform:translate(var(--lx,30px),var(--lh,520px)) rotate(var(--lr,400deg));}}
.leaf{position:absolute;top:-14px;pointer-events:none;z-index:4;will-change:transform;filter:drop-shad
ow(0 1px 2px rgba(0,0,0,0.35));}
/* ── LEAVES (spawn at cursor over green areas) ── */
@keyframes leafFall{0%{opacity:0;transform:translate(0,0) rotate(0deg);}15%{opacity:.95;}100%{opacity:
0;transform:translate(var(--lx,30px),var(--lh,110px)) rotate(var(--lr,260deg));}}
.leaf{position:absolute;pointer-evege:transform;filter:drop-shadow(0 1px
