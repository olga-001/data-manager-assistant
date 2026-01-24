# 🧠 Multi-Agent AI System for Automated Data Enrichment & Catalog Management

## 📌 Project Overview
This project is a **multi-agent AI system** designed for automated analysis, enrichment, and structuring of data for public places and business listings.
The system processes **unstructured text, screenshots, and photos**, extracts reliable information from multiple sources, and carefully updates records in a database **without overwriting existing data**, while maintaining status control and error logging.
The solution is implemented as a production-grade workflow with clear business logic, data safety mechanisms, and scalability in mind.

---

## 🎯 Business Problem
Automating a routine and time-consuming process of filling and maintaining place listings, which previously required:
- analyzing fragmented data sources,
- reviewing photos and screenshots,
- carefully filling multiple fields,
- complying with internal data quality rules.

---

## 🧩 Solution Architecture
The system follows a **multi-agent architecture** and consists of several logical stages:

### 1️⃣ Entry Assistant (AI Agent #1)
- analyzes a unified input object (Unified Input),
- processes text, screenshots, and photos,
- extracts and normalizes structured data (contacts, type, location, etc.),
- returns **strictly valid JSON output**.

### 2️⃣ Location Assistant (AI Agent #2)
- uses the output of the first agent combined with the original input data,
- generates a **neutral, SEO-oriented description** of the listing,
- follows strict constraints (no advertising language, no subjective judgments, no addresses or opening hours).

### 3️⃣ Data Update Control
- **only empty fields** are updated,
- **only allowed fields** are modified,
- manual data is protected from being overwritten.

### 4️⃣ Status Management
- `Ready to process` — workflow trigger  
- `Processing` — item is being processed  
- `Ready to check` — processing completed, manual review required  
- `Error` — error occurred with detailed logging  
- `Done` — item fully processed and manually approved  

---

## 🛠 Technology Stack
- **n8n (self-hosted)** — workflow orchestration
- **OpenAI GPT-4o** — multimodal text and image processing
- **Notion API** — database (current implementation)
- **Google Drive** — image storage
- **JavaScript (Code nodes)** — parsing, validation, business logic

---

## 🔁 Adaptability & Limitations
⚠️ In its current form, the solution is **not a universal out-of-the-box product**, however:
- the architecture,
- the multi-agent logic,
- the safe data update principles

can be **easily adapted to other systems and domains**.

---

## 🧱 Replaceable Components
A similar architecture can be implemented using:

### Databases
- PostgreSQL / MySQL  
- Airtable  
- Google Sheets  
- CRM / PIM systems  
- Custom APIs / internal databases  

### Image Storage
- Amazon S3 / S3-compatible storage  
- Cloudinary  
- Dropbox  
- local file storage  

### Orchestration
- n8n  
- Make  
- Airflow  
- serverless functions  

---

## 🌍 Potential Use Cases
This approach can be adapted for:

- 🛒 **product catalogs** (descriptions, attributes, images)
- 🏨 **real estate and hotel listings**
- 🏥 **medical and service directories**
- 🗺️ **mapping and travel platforms**
- 🧾 **internal corporate registries and databases**

---

## 💡 Key Value
- production-oriented LLM usage,
- multi-agent architecture,
- data quality control,
- protection against uncontrolled overwrites,
- scalable and transparent logic.

---

## 📎 Project Status
✅ Implemented  
🔧 Can be adapted to other databases and domains
