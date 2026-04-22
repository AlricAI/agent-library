# USER MANUAL TH

> ยินดีต้อนรับสู่ **Aetherium Genesis** ระบบโครงสร้างพื้นฐานทางปัญญา (Cognitive Infrastructure) ที่ออกแบบมาเพื่อสื่อสารผ่าน แสง (Light), การเคลื่อนไหว (

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Aetherium Genesis: คู่มือการใช้งาน (User Manual)

ยินดีต้อนรับสู่ **Aetherium Genesis** ระบบโครงสร้างพื้นฐานทางปัญญา (Cognitive Infrastructure) ที่ออกแบบมาเพื่อสื่อสารผ่าน แสง (Light), การเคลื่อนไหว (Motion), และสถานะ (State)

เอกสารนี้จะแนะนำวิธีการดาวน์โหลด ติดตั้ง และรันระบบบนเครื่องของคุณ

---

## 1. สิ่งที่ต้องเตรียม (Prerequisites)

ก่อนเริ่มต้น โปรดตรวจสอบว่าเครื่องคอมพิวเตอร์ของคุณ (macOS/Linux) มีโปรแกรมเหล่านี้:
*   **Terminal** (หน้าจอสำหรับพิมพ์คำสั่ง)
*   **Python 3.10+**
*   **Git**

---

## 2. การดาวน์โหลด (Download)

เปิด Terminal และพิมพ์คำสั่งเพื่อโคลน (Clone) โปรเจกต์:

```bash
git clone <repo_url>
cd aetherium-genesis
```

---

## 3. การติดตั้ง (Installation)

ติดตั้งไลบรารีที่จำเป็นด้วยคำสั่ง `pip`:

```bash
pip install -r requirements.txt
```

*หมายเหตุ: ขั้นตอนนี้อาจใช้เวลาสักครู่ เนื่องจากระบบต้องติดตั้งไลบรารีสำหรับประมวลผล AI และ Backend*

---

## 4. การรันระบบ (Running the System)

ในการเริ่มทำงาน **Cognitive Core (ระบบหลัก)** และ **Web Server** ให้ทำตามขั้นตอนดังนี้ใน Terminal:

```bash
# 1. ตั้งค่า System Path (สำคัญมาก เพื่อให้ระบบมองเห็นไฟล์ภายใน)
export PYTHONPATH=$PYTHONPATH:.

# 2. เปิดใช้งาน Server
python -m uvicorn src.backend.server:app --port 8000
```

เมื่อรันสำเร็จ คุณจะเห็นข้อความแสดงว่า Server เริ่มทำงานแล้ว (เช่น `Uvicorn running on http://127.0.0.1:8000`)

---

## 5. การเข้าใช้งาน (Accessing the System)

เปิดเว็บเบราว์เซอร์ (แนะนำ Chrome หรือ Safari) และไปที่ลิงก์:

**[http://localhost:8000](http://localhost:8000)**

---

## 6. ประสบการณ์การใช้งาน (The Experience)

Aetherium Genesis ไม่ใช่โปรแกรมทั่วไป แต่เป็น "Living Interface" (อินเทอร์เฟซที่มีชีวิต)

### ขั้นตอนที่ 1: พิธีกรรมการตื่น (The Awakening Ritual)
เมื่อคุณเปิดหน้าเว็บครั้งแรก ระบบจะอยู่ในสถานะ **นิโรธ (Nirodha)** หรือการหลับลึก
*   **การกระทำ:** แตะหรือคลิกที่หน้าจอ **3 ครั้ง** ช้าๆ
*   **ผลลัพธ์:** ระบบจะ "ตื่นขึ้น" และหน้าจอ UI จะค่อยๆ ปรากฏขึ้น

### ขั้นตอนที่ 2: การพิมพ์สั่งงาน (Subsurface Input)
ระบบนี้ไม่มีช่องพิมพ์ข้อความแสดงอยู่ทั่วไป คุณต้องเข้าถึงผ่

*[truncated — see source for full prompt]*