# 📊 Student Performance Analysis Using AI

This project uses OpenAI's GPT-4 to analyze academic performance patterns, board exam results, and risk indicators among osteopathic medical students. It simulates an AI-powered academic performance analyst working with historical and real-time data.

> ⚠️ **Note:** This project is designed as a prototype and proof-of-concept. It is not currently in production use or linked to any institutional database.

---

## 🎯 Objectives

- Identify correlations between academic data and board outcomes (COMSAE, COMLEX)
- Use AI to summarize patterns and risk profiles in medical student performance
- Generate early warning insights to flag students at risk of COMLEX failure
- Recommend data-driven academic support strategies
- Perform logistic regression modeling to evaluate risk thresholds

---

## 📥 Input Variables

- `COMSAE`: Practice board exam score (numeric)  
- `COMLEX`: Official board exam result (`P` = Pass, `F` = Fail)  
- `CRXX`: Course grades (e.g., `CRXX`, `CRXX2`) on a 0–100 scale  
- `TotalYear1 Grades` / `TotalYear3 Grades`: Average numeric grades per year  
- `Year`: Expected graduation class (e.g., 2025)  
- Demographics or other features as needed  

---

## 🤖 Prompt Overview

The following logic is passed to GPT-4 via the OpenAI API:

- Analyze correlations between course performance and COMLEX failure  
- Identify early signs of risk from Y1 and Y2 grades  
- Model COMLEX outcome as a binary variable and apply logistic regression  
- Return feedback with statistical rationale, structured into bullet points or short analytical paragraphs  

---

## 💻 Sample Code Snippet

```python
from openai import OpenAI

client = OpenAI(api_key="your-secret-key")

response = client.chat.completions.create(
    model="gpt-4-turbo",
    messages=[
        {
            "role": "system",
            "content": "You are an expert performance analyst..."
        },
        {
            "role": "user",
            "content": f"""
Please analyze the following student performance data:

**Column Definitions:**
- COMSAE, COMLEX, DOxxx, TotalYear 1 Grades, etc.

**Data:**
{data_str}

**Focus Areas:**
1. COMSAE and COMLEX patterns
2. TotalYear 1 Grades and Y2 correlations
3. Logistic regression using COMLEX outcome
4. Early warning signs
5. Intervention suggestions
"""
        }
    ]
)

print(response.choices[0].message.content)
```
---

## 📌 Sample Insights (AI-Generated)

- Students scoring < 75 on `TotalYear1 Grades` had a **3.2x higher odds** of COMLEX failure  
- `CRXX2` and `CRXX` course grades were **strong predictors** of COMLEX outcomes  
- A **logistic regression model** showed significant p-values (**p < 0.01**) for `TotalYear 1 Grades`  
- Recommended **targeted tutoring** and **academic coaching** for students scoring < 72  
- **COMSAE scores < 400** frequently preceded COMLEX failure  

---

## 📂 Files Included

- `performance_analysis_gpt4.py` – Jupyter Notebook or Python Script  
  

---

## 🔗 Related Projects

- [COMLEX Question Generator](https://github.com/danabr21285/comlex-question-generator)  
- [FIRE Program Clustering](https://github.com/danabr21285/fire-program-clustering)  

---

## 👩‍🏫 Author

**Dana Brooks**  
Executive Director of Admissions  
📧 danatallent@yahoo.com  
🔗 [LinkedIn](https://linkedin.com/in/dana-tallent-brooks-a15977a0)

---
