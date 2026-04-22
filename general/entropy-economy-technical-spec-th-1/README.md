# ENTROPY ECONOMY TECHNICAL SPEC TH

> - **Project:** AETHERIUM GENESIS (Module: AetherBusExtreme / CSP-X1)
- **Version:** 1.0 Alpha
- **Status:** Confidential Blueprint

## 1) วัตถุประสงค์

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ระบบเศรษฐศาสตร์เอนโทรปี (Entropy Economy Technical Specification)

- **Project:** AETHERIUM GENESIS (Module: AetherBusExtreme / CSP-X1)
- **Version:** 1.0 Alpha
- **Status:** Confidential Blueprint

## 1) วัตถุประสงค์ (Purpose)

ระบบนี้ออกแบบมาเพื่อสร้างมูลค่าจาก "ความไม่แน่นอนของมนุษย์" (Human Entropy) โดยวัดระยะห่างระหว่างสิ่งที่ระบบ CSP-X1 พยากรณ์กับสิ่งที่ผู้ใช้ทำจริง แล้วแปลงเป็นคะแนน **QoU (Quality of Unpredictability)** เพื่อใช้ทั้งในการให้รางวัลเชิงเศรษฐกิจ (เครดิต/โทเค็นภายในระบบ) และสร้างข้อมูลใหม่เพื่อลดความเสี่ยง **Model Collapse**.

## 2) ขอบเขต (Scope)

### In-Scope
- การคำนวณ QoU แบบ real-time.
- โครงสร้างข้อมูล Entropy Packet และ Ledger สำหรับข้อมูล high-entropy.
- อินเทอร์เฟซ API สำหรับรับ packet และคืนผลการประเมิน.
- Anti-gaming logic เพื่อแยก "noise" ออกจาก "novel creativity".

### Out-of-Scope
- การแลกโทเค็นกับเงินจริง (Fiat) ในเฟสแรก.
- การ train LLM ใหม่ทั้งโมเดล (เฟสนี้รองรับ fine-tune / RAG pipeline เท่านั้น).

## 3) องค์ประกอบระบบ (System Components)

### 3.1 CSP-X1 Prediction Engine (The Oracle)
- รัน shadow prediction เพื่อคาดการณ์ action ถัดไป.
- ส่ง confidence score เข้า entropy pipeline.

### 3.2 Entropy Validator (The Judge)
- เปรียบเทียบ `prediction_snapshot.confidence_score` กับ action จริง.
- คำนวณ QoU จากสูตรหลัก และกำหนด state ของ Singularity Meter.
- ทำ anti-gaming และ safety filter.

### 3.3 Akashic Treasury (The Ledger)
- บันทึกธุรกรรม QoU เป็น hash-chain.
- Packet ที่ QoU สูงถูกทำเครื่องหมาย preserve พร้อม artifact reference.

### 3.4 GunUI Feedback Layer (The Sensor)
- ใช้ข้อมูลการประเมินเพื่อแสดงสถานะ visual feedback:
  - Predictable → เทา/ขาว
  - Divergent → ส้ม/ม่วง
  - Chaotic/Genius → ทอง + particle explosion

## 4) Interface Contract

### 4.1 Entropy Submit API

`POST /api/v1/entropy/submit`

**Headers**
- `Content-Type: application/json`
- `Authorization: Bearer <user_token>` (policy-level contract)

**Body (ย่อ)**
```json
{
  "user_id": "uuid-v4",
  "packet": {
    "packet_id": "uuid-v4",
    "timestamp": "2023-10-2

*[truncated — see source for full prompt]*