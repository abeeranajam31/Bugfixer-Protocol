⸻


# 🐞 Bug Fixer Protocol

A hybrid retrieval-based issue analysis system that leverages semantic and keyword-based similarity using sentence embeddings, TF-IDF, and BM25. Enhanced with a customizable **MCP Processor Workflow** for deeper bug triage automation.

---

## 🚀 Getting Started

### 1. Clone the Repo

```bash
git clone https://github.com/abeeranajam31/Bugfixer-Protocol.git
cd Bugfixer-Protocol

2. Create and Activate Virtual Environment

python -m venv venv
# On macOS/Linux:
source venv/bin/activate
# On Windows:
venv\Scripts\activate

3. Install Requirements

pip install -r requirements.txt

You can generate requirements.txt using:

pip freeze > requirements.txt


⸻

🧼 Preprocess Data

python Clean_Code.py

Cleans the “Detailed Description” column from the Excel dataset and saves a refined version.

⸻

🧠 Ingest Cleaned Data

python data_ingest.py

	•	Reads the cleaned Excel file
	•	Generates:
	•	Sentence Embeddings
	•	TF-IDF Vectors
	•	BM25 Scores
	•	Stores everything in MongoDB (hybrid_retriever.issues)

⸻

🔍 Query the System

python query_issue.py

	•	Takes a new issue/query
	•	Retrieves similar past issues using:
	•	Sentence Embeddings
	•	TF-IDF Similarity
	•	BM25 Scoring
	•	MCP Workflow Match (optional)

⸻

⚙️ MCP Processor Workflow (Modular Custom Pipeline)

The MCP Workflow applies logic-based matching and customizable pattern rules to post-process retrieved results.

Example Workflow:
	•	Score boost if the root cause contains certain tokens
	•	Re-rank results based on component-module match
	•	Filter results based on environment similarity

MCP can be extended via custom Python rules or YAML templates.

⸻

🖥️ Run the FastAPI Endpoint

uvicorn api:app --reload

Serves a RESTful API for querying similar issues.

⸻

💡 Sample Query Output

Result 1 (Score: 0.8762)
Summary: Crash on missing config
Root Cause: Config loader fails when default is not set
Fix: Add fallback in config parser
Description: App crashes if VAR_ENV is undefined in staging


⸻

🗃️ MongoDB Details

Database: hybrid_retriever
Collection: issues
Stores:
	•	Original issue text
	•	TF-IDF vector
	•	Sentence embedding
	•	BM25 score
	•	MCP-derived metadata (if enabled)

⸻

📌 .gitignore Highlights

This project ignores:
	•	venv/, __pycache__/
	•	.xlsx, ~$*.xlsx
	•	*.pkl, embedding_model/

⸻

✨ Future Improvements
	•	✅ Add UI for issue submission
	•	✅ Add Elasticsearch backend for scalable BM25
	•	🚧 Integrate BERT-based re-ranking
	•	🚧 MCP rule manager via YAML configs

⸻

