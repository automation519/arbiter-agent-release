# ARBITER Competition Monitor Agent — ไฟล์แจกทีม

**LEJP-2026.10004 โปรแกรมควบคุมระบบภายใน** · Jinpao Praksa Automation Contest 2026

ที่นี่คือแหล่งดาวน์โหลดทางการของโปรแกรม Audit Agent สำหรับทีมผู้แข่งขัน (RULES-TECH ข้อ 5.1.1a)
ไฟล์ทั้งหมดอยู่ในหน้า **[Releases](../../releases)** — repo นี้มีเฉพาะไฟล์แจก ไม่มี source code

## ดาวน์โหลด

เลือกตามเครื่องประมวลผลหลักของหุ่น:

| เครื่อง | ไฟล์ |
|---|---|
| Windows 10/11 (64-bit) | `arbiter-agent-DEMO-windows.zip` |
| Linux x86_64 (Ubuntu 20.04 ขึ้นไป) | `arbiter-agent-DEMO-linux-x86_64.tar.gz` |
| Jetson / Raspberry Pi (ARM) | ยังไม่รองรับ — แจ้งผู้จัดล่วงหน้า (RULES-TECH ข้อ 5.1.7) |

คู่มือ: `ARBITER-Agent-DEMO-Manual-TH.pdf` · วิธีติดตั้งย่อ: `README-INSTALL-TH.txt`

> **รุ่น DEMO ใช้แข่งไม่ได้** — สำหรับทดสอบบนเครื่องที่จะใช้แข่งและรายงานปัญหาก่อนวันแข่ง
> ผู้จัดจะประกาศรุ่นแข่งจริงเป็น Release แยกในหน้านี้

## ตรวจว่าไฟล์เป็นของผู้จัดและไม่ถูกแก้

**1) ไฟล์ที่ดาวน์โหลดไม่เสีย/ไม่ถูกเปลี่ยน** — เทียบกับ `SHA256SUMS.txt` ในหน้า Release เดียวกัน

```
# Linux
sha256sum -c SHA256SUMS.txt --ignore-missing

# Windows (PowerShell)
Get-FileHash .\arbiter-agent-DEMO-windows.zip -Algorithm SHA256
```

**2) ตัวโปรแกรมเป็นของผู้จัด** — `manifest-DEMO-windows.json` / `manifest-DEMO-linux.json` คือรายการ hash ของตัวโปรแกรม
ที่ผู้จัด **เซ็นด้วยกุญแจ Ed25519** (กุญแจตรวจลายเซ็น: `organizer-DEMO.verify.pub`)
ชุดตรวจของกรรมการ (1-PRE-ARM / 2-COLLECT) ใช้ manifest นี้ตรวจโปรแกรมบนเครื่องของทีมก่อนและหลังแข่งทุกแมตช์ —
โปรแกรมที่ถูกแก้แม้ 1 byte จะ hash ไม่ตรง และไม่มีใครสร้าง manifest ปลอมได้โดยไม่มีกุญแจเซ็นของผู้จัด

> รุ่น DEMO เซ็นด้วยกุญแจ DEMO ซึ่งแยกจากกุญแจรุ่นแข่ง — ชุดตรวจของสนามจริงจะไม่ยอมรับรุ่น DEMO
> ห้ามแก้ไข ดัดแปลง หรือรัน Agent จาก source ในสนาม (RULES-TECH ข้อ 5.1.1a, 5.1.3)

## รายงานปัญหา

แจ้งผู้จัดพร้อม: รุ่นเครื่อง/บอร์ด · ระบบปฏิบัติการและเวอร์ชัน · ไฟล์ zip ที่โปรแกรมสร้างหลังซ้อม (มี `agent.log` อยู่ข้างใน)

---

Organized by Jinpao · พัฒนาโดย Automation Engineer
