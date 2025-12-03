# **📄 ATS Resume Scoring Automation using n8n + Telegram + Google Gemini**

This project is an **end-to-end automated ATS Resume Scoring System** built using **n8n**, **Telegram Bot**, **Google Gemini AI**, and **Google Sheets**.
It allows users to **upload a PDF or ZIP file of multiple resumes** via Telegram, automatically extracts text, evaluates each resume using Gemini, assigns an **ATS Score (0–100)**, and finally logs the results in Google Sheets as **Accepted or Rejected** based on score thresholds.


## **Features**

### ✅ **1. Telegram Bot Integration**

* Users can send **PDF** or **ZIP files** directly to the bot.
* Bot supports:

  * `hi`, `hello`, `hey` → Sends greeting and instructions
  * Single resume PDF
  * ZIP files containing multiple resumes

### 📦 **2. Resume Extraction**

* PDF resumes are parsed using `Extract from File` node.
* ZIP files are decompressed and processed resume-by-resume.

### 🤖 **3. AI-Powered ATS Scoring (Google Gemini)**

Each resume is analyzed based on:

* Keyword Match
* Formatting Quality
* Experience Relevance
* Skills Coverage
* Achievements & Metrics
* Grammar & Readability
* ATS Compatibility Issues

**Gemini returns output strictly in JSON format:**

```json
{
  "name": "",
  "email": "",
  "mobile no": 0,
  "ats_score": 0
}
```

### 📊 **4. Automatic Shortlisting (Google Sheets)**

Based on ATS score:

* **Score > 75 → Saved to “Accepted” Sheet**
* **Score ≤ 75 → Saved to “Rejected” Sheet**

This allows recruiters/trainers to maintain structured records of evaluated resumes.

### 🔁 **5. Multi-Resume Processing**

* ZIP files are split into individual PDFs
* Each PDF is evaluated in a loop
* All results are merged and recorded

### ✉️ **6. Status Updates to User**

* Bot replies with **“Done”** after evaluating all resumes.
* Clean, conversational Telegram-based workflow.

## 📂 **Workflow Overview**

The n8n workflow includes the following key components:

| Node                                    | Purpose                           |
| --------------------------------------- | --------------------------------- |
| **Telegram Trigger**                    | Receive messages/files from users |
| **IF Node**                             | Detect greetings (hi/hello/hey)   |
| **Switch Node**                         | Route PDF vs ZIP                  |
| **Extract From File**                   | Extract PDF text                  |
| **Compression / SplitOut / Loop**       | Handle ZIP multiple PDFs          |
| **AI Agent + Google Gemini Chat Model** | ATS analysis                      |
| **Python Code Node**                    | Clean JSON output                 |
| **Google Sheets (Accepted/Rejected)**   | Store results                     |
| **Wait + Merge**                        | Sync multi-resume processing      |
| **Telegram (Done message)**             | Notify completion                 |


## 🧠 **Tech Stack**

* **n8n Automation Platform**
* **Telegram Bot API**
* **Google Gemini AI**
* **Google Sheets API**
* **Python Native Code (inside n8n)**

## 📸 **Workflow Screenshot**

<img width="1819" height="722" alt="Screenshot 2025-12-03 135906" src="https://github.com/user-attachments/assets/9b55a23b-c295-4617-bd61-8a2709ec3177" />


## 🛠️ Setup Instructions

### **1. Create Telegram Bot**

Use **@BotFather**:

* `/newbot`
* Get the **bot token**
* Add it in n8n credentials (Telegram API)

### **2. Configure Google Gemini API**

* Get an API key from Google AI Studio
* Add credentials in n8n under **Google Palm/Gemini**

### **3. Connect Google Sheets**

Create a Google Sheet with:

* `Accepted` sheet
* `Rejected` sheet

Add OAuth2 credentials in n8n.

### **4. Import Workflow**

* Upload the provided `.json` file
* Connect all credentials
* Activate workflow

### **5. Start Using the Bot**

Send:

* **hi / hello / hey** → instructions
* **PDF resume** → AI scoring
* **ZIP with multiple resumes** → batch scoring


## ⭐ Why This Project?

This automation solves real problems:

* Saves hours of manual screening
* Ensures unbiased evaluation
* Provides structured ATS-style scoring
* Works for bulk resumes with zero human effort

Perfect for:

* Training institutes
* HR departments
* Recruiters
* Ed-Tech platforms


## 🙌 Contributing

Feel free to create issues or pull requests for improvements!


## 📬 Contact

Ruchita Patil Email: pruchita565@gmail.com

LinkedIn Profile: www.linkedin.com/in/patil-ruchita
