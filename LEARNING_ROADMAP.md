# AI & Data Analysis Learning Roadmap
### For: Business IT Graduate — Junior AI & Data Analyst Role

---

> **Philosophy:** You already have the business brain. This roadmap teaches you the tools
> that turn business questions into data answers — and AI into your co-worker, not a mystery.
> Every skill here is learned hands-on using the real sales dataset in this repo.

---

## The Big Picture — What This Role Actually Is

```
Business Question  →  Find the Data  →  Clean & Analyse  →  Visualise  →  Communicate Insight
     (You)               (SQL/CSV)        (Python/Excel)     (Charts)       (Story + Slides)
                                              ↑
                                        AI helps here
                                      at every single step
```

You are the translator between **business people who have questions** and **data that has answers**.
AI (Claude, Copilot, ChatGPT) is your junior analyst — it does the repetitive work,
you provide the judgement and the story.

---

## Stage 1 — Foundation (Weeks 1–3)
*Goal: Be comfortable with data, GitHub, and talking to AI*

### 1.1 GitHub — Your Professional Portfolio
Why: Every employer checks GitHub. It also backs up your work and shows version history.

**Learn to:**
- [ ] Create a GitHub account and a repository
- [ ] Upload files (CSV, notebooks, images) via the web interface
- [ ] Write a clear README (see the one in this repo as a template)
- [ ] Make commits with meaningful messages ("add monthly revenue chart" not "update")
- [ ] Understand branches — work on a branch, merge when done

**Practice task:** Fork this repo, upload a chart you make, update the README.

**Resources:**
- GitHub's own "Hello World" guide (15 min, free)
- GitHub Desktop app — drag-and-drop for beginners

---

### 1.2 Claude Code & Claude.ai — Your AI Co-worker
Why: The job explicitly allows AI. Using it well is a skill, not cheating.

**Learn to:**
- [ ] Write a good prompt — be specific, give context, ask for one thing at a time
- [ ] Use Claude.ai (chat) for: explaining concepts, writing formulas, drafting reports
- [ ] Use Claude Code (this tool) for: writing Python, reviewing analysis, generating charts
- [ ] Upload a CSV to Claude and ask it questions about the data
- [ ] Iterate — if the first answer is wrong, explain *why* and ask again

**The golden rule of AI prompting:**
```
BAD:  "analyse my data"
GOOD: "I have a CSV with 400 Uganda sales transactions for 2024.
       Column net_revenue_ugx is revenue after discounts.
       Give me Python code to show total revenue by region as a bar chart."
```

**Practice task:** Upload `sales_data_2024.csv` to Claude.ai and ask it
"Which product category has the highest average profit margin?" — without writing any code.

---

### 1.3 Excel / Google Sheets — Your Swiss Army Knife
Why: Most businesses run on spreadsheets. This is non-negotiable.

**Learn to:**
- [ ] PivotTables — summarise 400 rows in 30 seconds
- [ ] VLOOKUP / XLOOKUP — join two tables
- [ ] Conditional formatting — highlight highs and lows automatically
- [ ] Basic charts: bar, line, pie — and when to use which
- [ ] IF, SUMIF, COUNTIF, AVERAGEIF formulas

**Practice task:** Open `sales_data_2024.csv` in Excel/Sheets.
Build a PivotTable showing: **Total Net Revenue by Region by Quarter**.

---

## Stage 2 — Core Skills (Weeks 4–8)
*Goal: Run real analysis and build your first dashboard*

### 2.1 Python for Data Analysis
Why: Python handles what Excel cannot — 1 million rows, automation, advanced statistics,
machine learning. You don't need to be a software engineer. You need to be *fluent enough*.

**Libraries to learn (in this order):**

| Library | What it does | Priority |
|---|---|---|
| `pandas` | Load, clean, filter, group data | **Must-have** |
| `matplotlib` | Basic charts | **Must-have** |
| `seaborn` | Beautiful statistical charts | High |
| `plotly` | Interactive charts (hover, zoom) | High |
| `openpyxl` | Read/write Excel files | Medium |
| `scikit-learn` | Machine learning (Stage 3) | Later |

**Learn to:**
- [ ] Load a CSV: `pd.read_csv()`
- [ ] Inspect data: `.head()`, `.info()`, `.describe()`
- [ ] Filter rows: `df[df["region"] == "Kampala Central"]`
- [ ] Group and aggregate: `df.groupby("category")["profit_ugx"].sum()`
- [ ] Sort: `.sort_values()`
- [ ] Handle missing values: `.isnull()`, `.fillna()`, `.dropna()`
- [ ] Create a new column: `df["revenue_per_unit"] = df["net_revenue_ugx"] / df["quantity"]`
- [ ] Plot a bar chart and save it as an image

**Practice tasks (use this repo's dataset):**
1. Find the top 3 products by total profit
2. Plot monthly net revenue as a line chart
3. Show which sales rep has the highest average order value
4. Find what % of orders were Refunded

**Where to learn Python (free):**
- Kaggle Learn — "Pandas" course (4 hours, free, with exercises)
- freeCodeCamp Python for Data Analysis (YouTube)
- Ask Claude Code to explain any line of code you don't understand

---

### 2.2 Jupyter Notebooks — Your Analysis Workbook
Why: Notebooks combine code + charts + written explanation in one document.
They are the standard deliverable for data analysis work.

**Learn to:**
- [ ] Install and launch Jupyter Lab
- [ ] Mix code cells and markdown (text) cells
- [ ] Run cells one at a time and fix errors
- [ ] Export a notebook as HTML or PDF to share with non-technical managers
- [ ] Structure a notebook: Introduction → Data Loading → Cleaning → Analysis → Conclusions

**Practice task:** Turn your Python analysis of the sales data into a clean notebook
with section headings, one chart per section, and a written 2-sentence conclusion under each chart.

---

### 2.3 Data Visualisation & Dashboards
Why: Insights that can't be communicated are worthless. Charts tell the story.

**Tools to learn:**

| Tool | Best for | Cost |
|---|---|---|
| **Looker Studio** (Google) | Shareable web dashboards, connects to Sheets/CSV | Free |
| **Power BI Desktop** | Corporate dashboards, Microsoft ecosystem | Free desktop |
| **Plotly / Dash** | Interactive Python dashboards | Free |
| **Canva** | Polishing charts for presentations | Free tier |

**Chart types to master:**
- Bar chart — comparing categories (regions, products, reps)
- Line chart — trends over time (monthly revenue)
- Pie/donut — part-to-whole (channel mix, payment method split)
- Scatter plot — correlation (discount % vs profit margin)
- Heatmap — two-dimension comparison (rep × region performance)

**Practice task:** Build a Looker Studio dashboard with 5 charts from the sales data.
Share the link with your boss/trainer for feedback.

---

## Stage 3 — AI & Advanced (Weeks 9–16)
*Goal: Use AI tools professionally and understand ML basics*

### 3.1 Working with the Claude API
Why: The job is AI analysis. Understanding how to *build* with AI, not just *chat* with it,
sets you apart from every other Business IT grad.

**Learn to:**
- [ ] Get an Anthropic API key
- [ ] Send a message to Claude via Python (5 lines of code)
- [ ] Upload a CSV and ask Claude to summarise it programmatically
- [ ] Build a simple script: reads sales data → asks Claude for insight → prints the answer
- [ ] Understand tokens, cost, and rate limits

**Example starter script:**
```python
import anthropic
import pandas as pd

client = anthropic.Anthropic()  # uses ANTHROPIC_API_KEY env variable

df = pd.read_csv("sales_data_2024.csv")
summary = df.describe().to_string()

message = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=1024,
    messages=[{
        "role": "user",
        "content": f"Here is a statistical summary of Uganda sales data for 2024:\n{summary}\n\nWhat are the 3 most important business insights from this?"
    }]
)
print(message.content[0].text)
```

---

### 3.2 SQL — Querying Databases
Why: Real companies store data in databases, not CSV files. SQL is the language of data.

**Learn to:**
- [ ] SELECT, FROM, WHERE, ORDER BY, LIMIT
- [ ] GROUP BY + aggregate functions (SUM, COUNT, AVG, MAX)
- [ ] JOIN two tables
- [ ] Subqueries

**Practice task:** Load `sales_data_2024.csv` into SQLite (free, no server needed)
and answer: "What is the total profit per sales rep, for completed orders only, ranked highest to lowest?"

**Free resource:** SQLZoo.net or Mode Analytics SQL Tutorial

---

### 3.3 Machine Learning Basics (Awareness Level)
You don't need to build ML models from scratch. You need to understand:

| Concept | Plain English | Business Example |
|---|---|---|
| Classification | Predict a category | Will this customer churn? (Yes/No) |
| Regression | Predict a number | What will next month's revenue be? |
| Clustering | Group similar things | Which customers behave alike? |
| Recommendation | Suggest the next thing | Customers who bought X also bought Y |

**Practice task:** Use `scikit-learn` to build a simple regression:
predict `profit_ugx` from `quantity`, `discount_pct`, and `category` (encoded).
Don't worry about accuracy — understand the workflow.

---

## Stage 4 — Professional Skills (Ongoing)
*Running parallel to Stages 1–3*

### Communication & Storytelling
- [ ] Learn the "So What?" test — every chart must answer a business question
- [ ] Write a one-page analysis brief: Context → Finding → Recommendation
- [ ] Practice presenting to a non-technical audience (your boss is the test subject)

### Presentation Tools
| Tool | Use case |
|---|---|
| **Google Slides / PowerPoint** | Standard business presentations |
| **Canva** | Visually polished decks |
| **Notion** | Living documents + embedded charts |
| **Claude.ai** | Draft the narrative, suggest structure |

### Professional Habits
- [ ] Comment your code so you remember what it does in 3 months
- [ ] Version control everything on GitHub — no more "final_v3_FINAL.xlsx"
- [ ] Keep a learning log — one paragraph per week on what you learned
- [ ] Follow data people on LinkedIn: data analysts, BI developers, AI practitioners in East Africa

---

## Milestone Checklist

| Milestone | Evidence | Target Week |
|---|---|---|
| GitHub repo live with README | Public repo URL | Week 1 |
| Excel PivotTable analysis done | Screenshot or file | Week 2 |
| First Python analysis notebook | `.ipynb` on GitHub | Week 6 |
| Looker Studio dashboard | Shareable link | Week 7 |
| Claude API script working | `.py` on GitHub | Week 10 |
| SQL queries on the dataset | `.sql` file on GitHub | Week 11 |
| Full analysis presentation | Slides + notebook | Week 16 |

---

## First Week Action Plan

1. **Day 1:** Create GitHub account → Fork this repo → Read the README
2. **Day 2:** Open `sales_data_2024.csv` in Google Sheets → Build one PivotTable
3. **Day 3:** Go to claude.ai → Upload the CSV → Ask 5 business questions in chat
4. **Day 4:** Install Python (Anaconda distribution) → Run the starter snippets in the README
5. **Day 5:** Write a paragraph: *"What I learned this week and what surprised me"* → commit it to GitHub

---

## Key Mindset

> **You are not learning to become a programmer.**
> You are learning to *direct* computers and AI to answer business questions faster than any human could manually.
> The business judgement is yours. The grunt work belongs to the tools.

The best data analysts ask great questions. The tools find the answers.

---

*Prepared for: Junior AI & Data Analyst Onboarding*
*Dataset: Uganda Sales Data 2024 — 400 transactions across 7 regions*
*Trainer: Review milestones at end of each stage before proceeding*
