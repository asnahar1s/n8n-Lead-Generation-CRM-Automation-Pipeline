# 🎯 Lead Generation & CRM Automation Workflow
> **Automatically capture leads, store them in Airtable, and send personalized welcome emails — zero manual effort.**

---

## 📌 Project Overview

Small businesses lose leads every day due to slow manual follow-ups and disorganized tracking. This workflow solves that by automatically capturing form submissions, saving them to an Airtable CRM, and instantly sending a personalized welcome email — all within seconds of a lead submitting the form. No code required on the client side, fully automated end to end.

---

## ✨ Features

- 📋 **Custom Lead Form** — Branded web form with Name, Email, and Message fields built directly in n8n
- 🗃️ **Airtable CRM Integration** — Every submission is auto-saved as a record with name, email, message, source, and timestamp
- 📧 **Instant Welcome Email** — Personalized Gmail email sent automatically to every lead within seconds
- ⚡ **Real-time Execution** — Average workflow completion in under 2 seconds
- 🔁 **Always On** — Workflow runs 24/7 once activated, no manual triggering needed

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **n8n** | Workflow automation engine |
| **n8n Form Trigger** | Lead capture form |
| **Airtable API** | CRM database for storing leads |
| **Gmail / SMTP** | Sending personalized welcome emails |

---

## 📸 Screenshots

### Workflow Canvas
> *Form Trigger → Airtable → Gmail (all nodes green ✅)*

<img width="1913" height="702" alt="Screenshot 2026-04-24 130840" src="https://github.com/user-attachments/assets/295d67a7-7092-4390-bef8-190fdfb8b78d" />


### Lead Capture Form
> *What the lead sees when they visit the form URL*

<img width="1902" height="909" alt="Screenshot 2026-04-24 131152" src="https://github.com/user-attachments/assets/30ac825b-3056-4092-a72b-6a22575afc3b" />


### Airtable CRM — Leads Table
> *All submitted leads automatically saved with timestamp*

<img width="1903" height="910" alt="Screenshot 2026-04-24 131615" src="https://github.com/user-attachments/assets/be5dd1a4-5212-4369-ae0a-1a3e99f6291a" />


### Welcome Email in Inbox
> *Personalized email received by the lead instantly*

<img width="1905" height="910" alt="Screenshot 2026-04-24 131353" src="https://github.com/user-attachments/assets/eb57ea6b-4b14-4ebe-93d8-b4d3d5a7c2d1" />


---

## 🚀 Installation & Setup

### Prerequisites
- n8n account → [cloud.n8n.io](https://cloud.n8n.io)
- Airtable account → [airtable.com](https://airtable.com)
- Gmail account with App Password enabled

### Step 1 — Import the Workflow
```bash
# 1. Clone this repository
git clone https://github.com/asnahar1s/n8n-workflows.git

# 2. Open your n8n dashboard
# Go to cloud.n8n.io

# 3. Click "Add workflow" → "..." menu → "Import from file"
# Select: Lead-Gen-Workflow.json
```

### Step 2 — Set Up Airtable
1. Create a base called **Leads CRM**
2. Create a table called **Leads** with these columns:
```
Name (Single line text)
Email (Email)
Message (Long text)
Source (Single line text)
Date (Created time)
```
3. Go to `airtable.com/create/tokens` → create a token with scopes:
   - `data.records:write`
   - `data.records:read`
   - `schema.bases:read`

### Step 3 — Set Up Gmail
1. Go to `myaccount.google.com/apppasswords`
2. Create an App Password for **Mail**
3. Use these SMTP credentials in n8n:
```
Host: smtp.gmail.com
Port: 465
User: your Gmail address
Password: your 16-character app password
SSL: ON
```

### Step 4 — Activate
- Click **Publish** in n8n → your workflow is now live 24/7!

---

## 📋 Usage

1. Share your n8n form URL with potential leads
2. Lead fills in Name, Email, and Message → hits Submit
3. Within 2 seconds:
   - ✅ Lead is saved to Airtable CRM
   - ✅ Welcome email arrives in lead's inbox
4. Check Airtable anytime to view all captured leads

---

## 📂 Project Structure

```
n8n-workflows/
│
├── Lead-Gen-Workflow.json          # Import this into n8n
│
├── screenshots/
│   ├── lead-gen-canvas.png         # n8n workflow canvas
│   ├── lead-gen-form.png           # Lead capture form
│   ├── lead-gen-airtable.png       # Airtable CRM with data
│   └── lead-gen-email.png          # Welcome email received
│
└── Lead-Gen-Workflow-README.md     # This file
```

---

## 📊 Results & Performance

| Metric | Value |
|--------|-------|
| Avg. execution time | ~1.5 seconds |
| Nodes in workflow | 3 |
| Fields captured | 5 (Name, Email, Message, Source, Date) |
| Email delivery time | Under 5 seconds |
| Uptime | 24/7 when activated |

---

## 💡 Challenges & Learnings

- **Airtable token scopes** — Discovered that n8n requires `schema.bases:read` in addition to write permissions to detect the base and table
- **Gmail OAuth vs SMTP** — OAuth kept failing due to permission restrictions; switched to Gmail App Password via SMTP for reliable delivery
- **n8n expressions** — Learned to use `{{ $json.fieldName }}` to pass form data dynamically between nodes
- **Date formatting** — Airtable's date field required switching to "Created time" type instead of passing `$now` from n8n

---

## 🔮 Future Improvements

- [ ] Add a **follow-up email node** — automatically email leads again after 24 hours if no reply
- [ ] Connect to **WhatsApp via Twilio** to also notify the business owner instantly
- [ ] Add **lead scoring** using AI to tag hot vs cold leads automatically
- [ ] Build an **Airtable dashboard** to visualize lead pipeline metrics
- [ ] Add a **duplicate detection** step to avoid saving the same lead twice

---

## 👩‍💻 Author

**Asna** — BSc Computer Science @ University of West London (RAK Campus, UAE)
Specializing in Cloud Security, AI Automation & API Integrations

-  [GitHub](https://github.com/asnahar1s)
-  [LinkedIn](https://www.linkedin.com/in/asna-haris-684058319/)
-  asnaharis06@gmail.com
