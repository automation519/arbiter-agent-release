# ARBITER Competition Monitor Agent — ไฟล์แจกทีม

**LEJP-2026.10004 โปรแกรมควบคุมระบบภายใน** · Jinpao Praksa Automation Contest 2026

ที่นี่คือแหล่งดาวน์โหลดทางการของโปรแกรม Audit Agent สำหรับทีมผู้แข่งขัน (RULES-TECH ข้อ 5.1.1a)
ไฟล์ทั้งหมดอยู่ในหน้า **[Releases](../../releases)** — repo นี้มีเฉพาะไฟล์แจก ไม่มี source code

## ดาวน์โหลด — เวอร์ชันแข่ง 1.0.0

ใช้ Release **[v1.0.0](../../releases/tag/v1.0.0)** เท่านั้นในวันแข่ง · เลือกตามเครื่องประมวลผลหลักของหุ่น:

| เครื่อง | ไฟล์ |
|---|---|
| Windows 10/11 (64-bit) | `arbiter-agent-1.0.0-windows.zip` |
| Linux x86_64 — PC / NUC (Ubuntu 20.04 ขึ้นไป) | `arbiter-agent-1.0.0-linux-x86_64.tar.gz` |
| Raspberry Pi 5 / ARM64 (Ubuntu 24.04 ขึ้นไป) | `arbiter-agent-1.0.0-linux-aarch64.tar.gz` |
| Jetson (JetPack) | ยังไม่รองรับ — แจ้งผู้จัดล่วงหน้า |

วิธีติดตั้งและคำสั่งปิดเครือข่าย: `README-INSTALL-TH.txt` (มีอยู่ในไฟล์ zip / tar.gz ด้วย)

> **ห้ามเปลี่ยนชื่อไฟล์โปรแกรม** และห้ามแยก `organizer.pub` ออกจากโฟลเดอร์
> รุ่น DEMO (Release `demo-2026-10-16`) ใช้แข่งไม่ได้ — ลบทิ้งได้

## ตรวจว่าไฟล์เป็นของผู้จัดและไม่ถูกแก้

**1) ไฟล์ที่ดาวน์โหลดไม่เสีย/ไม่ถูกเปลี่ยน** — เทียบกับ `SHA256SUMS.txt` ในหน้า Release เดียวกัน

```
# Linux
sha256sum -c SHA256SUMS.txt --ignore-missing

# Windows (PowerShell)
Get-FileHash .\arbiter-agent-1.0.0-windows.zip -Algorithm SHA256
```

**2) ตัวโปรแกรมเป็นของผู้จัด** — `manifest-windows.json` / `manifest-linux-x86_64.json` / `manifest-linux-aarch64.json`
คือรายการ hash ของตัวโปรแกรมที่ผู้จัด **เซ็นด้วยกุญแจ Ed25519** (กุญแจตรวจลายเซ็น: `organizer.verify.pub`)
ชุดตรวจของกรรมการ (1-PRE-ARM / 2-COLLECT) ใช้ manifest นี้ตรวจโปรแกรมบนเครื่องของทีมก่อนและหลังแข่งทุกแมตช์ —
โปรแกรมที่ถูกแก้แม้ 1 byte จะ hash ไม่ตรง และไม่มีใครสร้าง manifest ปลอมได้โดยไม่มีกุญแจเซ็นของผู้จัด

> ห้ามแก้ไข ดัดแปลง หรือรัน Agent จาก source ในสนาม (RULES-TECH ข้อ 5.1.1a, 5.1.3)

## รายงานปัญหา

แจ้งผู้จัดพร้อม: รุ่นเครื่อง/บอร์ด · ระบบปฏิบัติการและเวอร์ชัน · รูปหน้าจอ · ไฟล์ `agent.log` ในโฟลเดอร์โปรแกรม

---

Organized by Jinpao · พัฒนาโดย Automation Engineer
