# 🧠 LLM-Enhanced SQL Query System for Employee Insights

This project demonstrates how to integrate a structured relational database with a Large Language Model (LLM) to allow users to ask natural language questions about employee data and receive accurate, SQL-generated responses.

---

## 📌 Overview

This project integrates OpenAI's GPT-4 with an SQLite database using the LangChain framework. It showcases how LLMs can autonomously generate and execute SQL queries based on natural language inputs. The system is benchmarked and improved iteratively to handle advanced questions, including those requiring external knowledge (e.g., historical recession periods).

---

## 🛠️ Features

- ✅ Natural language to SQL conversion via GPT-4
- ✅ LangChain SQL agent with custom prompt
- ✅ Synthetic employee database (100 records across 10 employees × 10 weeks)
- ✅ Support for advanced questions with reasoning
- ✅ SerpAPI integration for real-time web lookup (e.g., recession dates)
- ✅ Multi-agent tool selection via `zero-shot-react-description`

---

## 📊 Data Generation

We created a synthetic employee activity dataset with the following structure:

### **Schema**

- `employee_id`: INT  
- `name`: TEXT  
- `email`: TEXT  
- `department`: TEXT  
- `job_title`: TEXT  
- `hire_date`: TEXT (randomized from 2018–2024)  
- `week_number`: INT (1–10)  
- `num_meetings`: INT  
- `total_sales_rmb`: REAL  
- `hours_worked`: REAL  
- `activities`: TEXT (randomly selected curated templates)

### **Generation Tooling**

- Language: **Python**
- Libraries: **pandas, sqlite3, datetime, random**

The database was exported to `employee_activity.db` and used by the LLM via LangChain.

---

## 🤖 System Architecture

- **LLM**: OpenAI GPT-4 (`gpt-4`)
- **Database**: SQLite (`employee_activity.db`)
- **Framework**: LangChain
- **Agent Type**: `create_sql_agent` + `zero-shot-react-description`
- **Tools Used**:
  - `Employee Database Agent`: answers queries using SQL
  - `Recession Search`: finds historical recession periods using SerpAPI

---

## 📈 Benchmarks

### **Benchmark 1: Initial Evaluation**

- 20 natural language queries were run through the LLM
- SQL was generated and executed
- Results were collected
- Issues identified:
  - No access to external data (Query 13 failed)
  - Limited contextual understanding (Query 14 incomplete)

---

### **System Improvements**

| Improvement Area | Technique Used |
|------------------|----------------|
| External Knowledge | Integrated SerpAPI via LangChain Tool |
| Schema Completeness | Added retention-related phrases in `activities` |
| Prompt Enhancement | Custom prefix with clear SQL-only instructions |
| Agent Behavior | Switched to `zero-shot-react-description` for tool selection |

---

### **Benchmark 2: After Improvements**

- Query 13: Now correctly identifies employees hired during 2008–2010 recession
- Query 14: Returns employees facing customer retention issues with proposed solutions
- Overall improved completeness, reasoning, and factual accuracy

---

## 📌 Key Learnings

- Prompt engineering significantly improves LLM output structure and correctness
- Tool-based architecture allows LLMs to handle hybrid (database + web) tasks
- Schema design is critical: aligning `activities` column with real-world query intent is essential
- Zero-shot agents can reason about tool use dynamically with no additional training

---

## 📁 Repository Structure

```
├── data_generation.py       # Code to generate synthetic employee data
├── employee_activity.db     # SQLite database used in the system
├── employee_activity.csv    # Exported version of the DB as CSV
├── LLM_SQL_Project.pptx     # Final project presentation
├── README.md                # You're here!
```

---

## 📞 Contact

Created by **Xinhe Wu**  
MS in Data Science, University of Michigan  
For questions, reach out via [GitHub Issues](https://github.com/your-repo/issues) or email.