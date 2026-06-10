# 🛠️ PROGRESS / HANDOFF — RO Tactical Board

> ไฟล์นี้สรุปว่าทำอะไรไปแล้ว + ต่ออะไร เผื่อเปิดงานต่อคนละเครื่อง (บริษัท/บ้าน) หรือ Claude session ใหม่
> อัปเดตล่าสุด: 2026-06-10

## ไฟล์ในโปรเจค
- `ro-tactical-board.html` — **ไฟล์หลัก** (HTML + inline JS, เปิดดับเบิลคลิกได้เลย)
- `styles.css` — **CSS แยกออกมาแล้ว** (ลิงก์ผ่าน `<link>`) ต้องวางคู่กับ html เสมอ
- `11.png` — รูปแผนที่เริ่มต้น (Vale of Clash)
- `README.md` — requirement (ภาษาไทย, มีคอมเมนต์สั่งงานฝังอยู่)
- `features.md` — รายการฟีเจอร์เดิม

## Stack / กติกา
- **Vanilla ล้วน — ไม่ใช้ Next.js** (ผู้ใช้ยืนยัน) เปิดออฟไลน์ได้; CSS แยกเป็น `styles.css` แล้ว (2026-06-10)
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
10. **ใบไม้ใหม่ (2026-06-10)** — เลิกร่วงสุ่มทั่วแมพ → spawn ที่ตำแหน่งเมาส์ **เฉพาะตอนชี้พื้นที่สีเขียว** เท่านั้น; throttle ลดความถี่ (≤~4/วิ + สุ่มข้าม 45%); emoji 🍃🍂🍁
    - กลไก: เพิ่ม `window.__mapSampleLoad(url)` (โหลดรูปลง offscreen canvas) + `window.__isGreenAt(x,y)` (แปลงพิกัดเมาส์→พิกเซลรูป ชดเชย `background-size:cover`+center แล้วเช็คสีเขียว) — `setMap` เรียก `__mapSampleLoad` อยู่แล้ว (hook เดิมที่ค้าง ตอนนี้ define จริงแล้ว)
11. **แยก CSS (2026-06-10)** — ดึง `<style>` ออกเป็น `styles.css` (251 บรรทัด) ลิงก์ผ่าน `<link>`

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
- title ใน `<head>` มี mojibake (`RO Guild War โ€" Tactical Board`) ยังไม่แก้

## ✅ emote sprites จริงในเกม (2026-06-10)
- โหลด gif emote จริง 22 ตัวจาก nn.ai4rei.net/dev/emolist (referer-protected — โหลดผ่าน curl ใส่ Referer) เก็บใน `emotes/{id}.gif`
- `roEmoteNode(cls)` คืน `<img src=emotes/..>` + fallback เป็น emoji (`RO_EMOTE_FB`) ถ้าโหลดไม่ขึ้น
- ใช้ทั้ง 3 จุด: token บนแมพ (.tok-emote), party thumbnail (.pmob-emote), header mob คลิก (.hdr-part)
- CSS `img.ro-emote` คุมขนาดต่อ context

## ✅ party thumbnail mobs เดินเล่น (2026-06-10)
- `initPartyMobs()` (rAF เดียว เก็บ id `window.__pmobRAF` cancel ก่อน re-init) — มอนสเตอร์ในแบดจ์ pace ±4px + bob + flip + สุ่ม emote; เรียกท้าย renderSidebar ทุกครั้ง

## ⚖️ หมายเหตุ IP (สำคัญถ้าจะขาย)
- sprite มอนสเตอร์ (divine-pride) + emote (nn.ai4rei) + แมพ = asset ของ Gravity มีลิขสิทธิ์ ใช้ในงานขายจริงเสี่ยงละเมิด — ก่อนขายควรเปลี่ยนเป็น asset ที่สร้างเอง/มีสิทธิ์ หรือขอ license
