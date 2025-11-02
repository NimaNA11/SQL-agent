# 🧠 SQL Agent — Natural Language to SQL with LangChain & Gemini

An **AI-powered SQL agent** built with **LangChain** and **Google Gemini**, capable of converting natural language questions into safe, validated SQL queries — executing them, fixing errors automatically, and returning human-readable answers.

---

## 🚀 Features

✅ **Natural Language to SQL** – Ask questions like *“List the top 5 highest-paid employees in each department.”*  
✅ **Automatic Query Generation** – Generates accurate `SELECT` queries using the database schema.  
✅ **Safety Validation** – Ensures only safe, single-statement `SELECT` queries are executed.  
✅ **Error Fixing** – Detects and corrects SQL syntax or logic errors automatically.  
✅ **Human-Readable Answers** – Converts SQL results into clear, natural language responses.  
✅ **Extensible Design** – Easily add new tools or connect to different databases.  

---

## 🏗️ Architecture Overview

The SQL Agent uses a **tool-based LangChain workflow**:

1. **get_database_schema** → Retrieve schema info  
2. **generate_sql_query** → Convert question → SQL  
3. **validate_sql_query** → Check for safety & syntax  
4. **execute_sql_query** → Run query on SQLite DB  
5. **fix_sql_error** → Repair invalid queries  
6. **analyze_query_results** → Summarize results in natural language  

---

## ⚙️ Installation

```bash
# Clone the repo
git clone https://github.com/<your-username>/sql-agent.git
cd sql-agent

# Install dependencies
pip install -qU langchain langchain_chroma langchain_core langchain_community
pip install -qU langchain-google-genai python-dotenv
```

---

## 🔑 Environment Setup

Create a `.env` file in the project root:

```bash
GOOGLE_API_KEY=your_gemini_api_key_here
```

---

## 🧩 Usage

```python
from sql_agent import ask_sql

# Example query
ask_sql("List the top 5 highest paid employees in each department.")
```

The agent will:
1. Inspect your database schema  
2. Generate and validate a SQL query  
3. Execute it safely  
4. Fix any issues if needed  
5. Return a natural-language summary of results  

---

## 🗄️ Example Database

By default, the example uses a **SQLite database**:
```python
db = SQLDatabase.from_uri("sqlite:///employees_db-full-1.0.6.db")
```
You can replace it with any other SQLite file or modify the URI for another SQL backend.

---

## 🧠 Tech Stack

- **[LangChain](https://python.langchain.com)**
- **[Google Gemini API](https://ai.google.dev/)**
- **SQLite**
- **Python 3.10+**

---

## 🧰 Tools Used

| Tool | Description |
|------|--------------|
| `get_database_schema` | Fetch full or partial DB schema |
| `generate_sql_query` | Translate question → SQL |
| `validate_sql_query` | Verify safety and syntax |
| `execute_sql_query` | Run validated SQL safely |
| `fix_sql_error` | Auto-correct failed queries |
| `analyze_query_results` | Generate natural language summary |

---

## 🧪 Example Output

**Input:**
> “List the top 5 highest paid employees in each department.”

**Generated SQL:**
```sql
SELECT department, employee_name, salary
FROM employees
ORDER BY department, salary DESC
LIMIT 5;
```

**Output:**
> “The top 5 highest-paid employees per department are displayed, showing names and salaries.”

---

## 🧱 Future Improvements

- 🔗 Multi-database support (PostgreSQL, MySQL)
- 🧩 Streamlit/Gradio UI
- 🔒 Advanced query sanitization
- 🤖 Chain-of-thought debugging visualization

---

## 📜 License

This project is licensed under the **MIT License** – free to use and modify.

---

## 💡 Acknowledgments

Built with ❤️ using [LangChain](https://www.langchain.com) and [Google Gemini](https://ai.google.dev) to make databases conversational.
