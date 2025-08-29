# 📌 Resume-Parser-OCR

This project parses resumes using **AI** and **OCR** methods, and stores results in the `ResumeData` entity using the **Base44 API**.

---

## 🚀 API Integration Guide

### 🔹 Base URL
```
https://app.base44.com/api/apps/68a7356f0285cfad28e93976/entities/ResumeData
```

### 🔹 Authentication
All requests must include the API key in the request headers:
```json
{
  "api_key": "1509d055851f48b39d83b1252f15b343",
  "Content-Type": "application/json"
}
```

---

## 📖 API Examples (JavaScript)

### 1. Reading Entities
You can fetch all stored resume entries and filter them by fields such as  
`original_filename`, `file_url`, `parsing_method`, `parsing_status`, `parsed_data`, `processing_time`, and `confidence_score`.

```javascript
// JavaScript Example: Reading Entities
// Filterable fields: original_filename, file_url, parsing_method, parsing_status, parsed_data, processing_time, confidence_score
async function fetchResumeDataEntities() {
    const response = await fetch(`https://app.base44.com/api/apps/68a7356f0285cfad28e93976/entities/ResumeData`, {
        headers: {
            'api_key': '1509d055851f48b39d83b1252f15b343', // or use await User.me() to get the API key
            'Content-Type': 'application/json'
        }
    });
    const data = await response.json();
    console.log(data);
}
```

---

### 2. Updating an Entity
You can update any resume entry by its `entityId`.

```javascript
// JavaScript Example: Updating an Entity
// Filterable fields: original_filename, file_url, parsing_method, parsing_status, parsed_data, processing_time, confidence_score
async function updateResumeDataEntity(entityId, updateData) {
    const response = await fetch(`https://app.base44.com/api/apps/68a7356f0285cfad28e93976/entities/ResumeData/${entityId}`, {
        method: 'PUT',
        headers: {
            'api_key': '1509d055851f48b39d83b1252f15b343', // or use await User.me() to get the API key
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(updateData)
    });
    const data = await response.json();
    console.log(data);
}
```

---

## 🔹 Filterable / Updatable Fields
- `original_filename` (string) → Original resume filename  
- `file_url` (string) → URL of uploaded file  
- `parsing_method` (`ai_powered` | `ocr`)  
- `parsing_status` (`processing` | `completed` | `failed`)  
- `parsed_data` (object) → Resume data structured into JSON  
- `processing_time` (number) → Time taken to process in seconds  
- `confidence_score` (0–100) → Parsing confidence score  

---

## ✅ Usage
- Use the **fetch function** to retrieve parsed resume data.  
- Use the **update function** to modify resume entries (e.g., change parsing status or add additional metadata).  

---

📌 **Note**: Replace the hardcoded `api_key` with `await User.me()` for secure runtime fetching in production.
