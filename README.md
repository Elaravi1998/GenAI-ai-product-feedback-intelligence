# 🧠 AI Product Feedback Intelligence

Analyze customer feedback to discover sentiment, recurring themes, feature requests, pain points, and prioritized product opportunities.

The notebook provides a runnable baseline using pandas and scikit-learn, with no paid API key required. It also prepares a grounded prompt for an optional LLM-generated narrative.

## ✨ Features

- 📥 Load CSV feedback or use synthetic demo data
- 🧹 Normalize customer text
- 💬 Estimate baseline sentiment
- 🧩 Discover themes using TF-IDF and K-Means
- 🔎 Flag potential feature requests and pain points
- 🚦 Rank opportunities using an explainable heuristic
- 🤖 Prepare an optional evidence-grounded LLM prompt
- 📤 Export CSV, JSON, and Markdown reports
- 🧪 Smoke tests for exported reports

> **Limitations:** Lexicon sentiment is approximate, clusters require human interpretation, and the priority score is a triage heuristic—not a validated KPI.

## 🏗️ Architecture

```text
CSV / Demo Feedback
        |
        v
Text Cleaning
   |         |
   v         v
Sentiment  TF-IDF + K-Means
   |         |
   +----+----+
        v
Feature Requests + Pain Points
        |
        v
Opportunity Prioritization
        |
        v
CSV / JSON / Markdown + Optional LLM Narrative
```

## 🛠️ Tech stack

- Python 3.10+
- pandas, NumPy
- scikit-learn (TF-IDF and K-Means)
- Matplotlib
- Jupyter Notebook / Google Colab
- Optional LLM provider for narrative summaries

## 📁 Repository structure

```text
ai-product-feedback-intelligence/
├── AI_Product_Feedback_Intelligence.ipynb
├── README.md
├── customer_feedback.csv
└── product_feedback_output/
    ├── feedback_with_insights.csv
    ├── theme_summary.csv
    ├── product_opportunities.csv
    ├── product_feedback_report.json
    └── product_feedback_report.md
```

Input data and generated outputs are optional. Do not commit private customer data or credentials.

## 🚀 Getting started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/ai-product-feedback-intelligence.git
cd ai-product-feedback-intelligence
```

### 2. Create a virtual environment

Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
```

### 3. Install dependencies

```bash
pip install jupyter pandas numpy scikit-learn matplotlib
```

### 4. Launch

```bash
jupyter notebook
```

Open `AI_Product_Feedback_Intelligence.ipynb` and run the cells in order. The built-in sample data lets you test the pipeline immediately.

## 📄 Input data format

For your own CSV, provide a `feedback_text` column. Recommended optional columns:

| Column | Purpose |
|---|---|
| `feedback_id` | Unique identifier |
| `product` | Product or feature name |
| `rating` | Rating, typically 1–5 |
| `feedback_text` | **Required** review/comment |
| `date` | Feedback date |
| `channel` | Survey, app store, support, etc. |

Set `USE_CSV = True` and update `CSV_PATH` in the notebook.

## 📊 Output artifacts

| File | Purpose |
|---|---|
| `feedback_with_insights.csv` | Cleaned feedback, sentiment, clusters, flags |
| `theme_summary.csv` | Cluster keywords, size, negative share, rating |
| `product_opportunities.csv` | Ranked themes and heuristic scores |
| `product_feedback_report.json` | Machine-readable report |
| `product_feedback_report.md` | Human-readable report |

## 🧠 Prioritization

The score combines theme volume, negative sentiment share, and low-rating share, scaled to 0–100. Treat it as an initial triage aid. Product decisions should also consider user reach, severity, business value, implementation cost, and real customer examples.

## 🤖 Optional LLM narrative

The notebook builds a prompt from computed opportunities and sample feedback. Pass it to your chosen LLM provider using its current official SDK. Ask the model to use only supplied evidence, avoid inventing counts, distinguish facts from hypotheses, and cite feedback IDs. Keep API keys in environment variables or a secret manager.

## 🧪 Evaluation

The notebook checks that report files exist and scores stay in range. For production:

- Build a human-labeled sentiment evaluation set.
- Measure precision, recall, and F1 by class.
- Review theme coherence and representative examples.
- Test feature-request detection across products and channels.
- Compare generated themes with product-manager annotations.

## 🔒 Privacy and responsible use

- Minimize personal data collection and redact sensitive identifiers where appropriate.
- Follow consent, access-control, and retention requirements.
- Do not commit customer data or secrets to GitHub.
- Treat predictions as uncertain signals, not definitive statements about customer intent.
- Keep human review in the decision loop.

## 🗺️ Roadmap

- [ ] Transformer-based sentiment
- [ ] Aspect-based sentiment for individual features
- [ ] Multilingual feedback analysis
- [ ] Duplicate/spam detection
- [ ] Weekly trends and release comparisons
- [ ] Streamlit dashboard and filters
- [ ] PII detection and redaction
- [ ] Human-in-the-loop theme review
- [ ] Model evaluation and experiment tracking
- [ ] RAG over product documentation and release notes

## 💼 Resume project description

**AI Product Feedback Intelligence | Python, NLP, scikit-learn, LLMs**

Built a customer feedback analytics pipeline to estimate sentiment, discover themes with TF-IDF and clustering, identify feature requests and pain points, and prioritize product opportunities. Added CSV/JSON/Markdown exports, an optional evidence-grounded LLM narrative workflow, and evaluation and privacy safeguards.

## 📌 GitHub topics

`generative-ai` `customer-feedback` `sentiment-analysis` `nlp` `product-analytics` `text-mining` `scikit-learn` `llm` `python` `jupyter-notebook`

## 📄 License

Choose a license such as MIT before publishing, and confirm any included datasets can legally be redistributed.
