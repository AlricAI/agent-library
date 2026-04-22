# AGENT BASED PLAN

> ## 🎯 Inleiding

Dit plan beschrijft hoe je de **8 bestaande agents** in VorstersNV kunt gebruiken om Fase 3-5 in te vullen. Elk agent wordt gebruikt 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📋 AGENT-GEBASEERD PLAN – VorstersNV Fase 3-5 Uitvoering

## 🎯 Inleiding

Dit plan beschrijft hoe je de **8 bestaande agents** in VorstersNV kunt gebruiken om Fase 3-5 in te vullen. Elk agent wordt gebruikt in specifieke workflows en use cases.

---

## 🤖 Agent Overzicht

### Jouw 8 Agents

| Agent | Model | Focus | Sub-Agents |
|-------|-------|-------|-----------|
| **1. Klantenservice Agent** | llama3 | Klantenvragen & support | Retour, Email, Fraude |
| **2. Order Verwerking Agent** | llama3 | Orderflow automation | Fraude, Email, Voorraad |
| **3. Product Beschrijving Agent** | mistral | SEO & product texts | Geen |
| **4. SEO Agent** | mistral | SEO optimalisatie | Product Beschrijving |
| **5. Fraude Detectie Agent** | llama3 | Verdachte patronen | Klantenservice |
| **6. Retour Verwerking Agent** | llama3 | Retouraanvragen | Email, Voorraad |
| **7. Email Template Agent** | mistral | Email generatie | Geen |
| **8. Voorraad Advies Agent** | llama3 | Inventory management | Geen |

---

## 🔄 Fase 3 – Agent Workflows

### **USE CASE 1: Nieuwe Klant Plaatst Order**

```
Customer buys product
    │
    ▼ (POST /api/orders)
Order Verwerking Agent
    │
    ├─► Fraude Detectie Agent
    │   └─ Analyze risk score
    │
    ├─► Email Template Agent  
    │   └─ Generate order confirmation
    │
    └─► Voorraad Advies Agent
        └─ Check stock levels
            │
            ▼ (Update DB)
        Inventory updated
            │
            ▼ (Send email)
        Customer notified
            │
            ▼ (Webhook)
        Warehouse receives pickup task
```

**Agent Execution Order:**
1. Order Verwerking Agent (validatie)
2. Fraude Detectie Agent (parallel)
3. Email Template Agent (confirmation)
4. Voorraad Advies Agent (stock)

**Expected Outcomes:**
- ✅ Order status: "confirmed" or "flagged"
- ✅ Email sent to customer
- ✅ Stock updated
- ✅ Warehouse notified

---

### **USE CASE 2: Klant Vraagt about Product**

```
Customer sends question
    │
    ▼ (Ch

*[truncated — see source for full prompt]*