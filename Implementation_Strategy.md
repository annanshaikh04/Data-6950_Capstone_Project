# Implementation Plan: Investment Intelligence Platform

**Goal**: Transform your existing ML scripts into a cohesive "Investment Intelligence Platform" for Venture Capitalists. 
**Why**: This satisfies the **Syllabus A++ requirements** (SQL, Data Warehouse) and creates **Real-World Impact** (a usable tool for investors) without excessive new work.

## 1. The Strategy: "From Script to Product"

Instead of just predicting "Success/Fail", we build a tool that answers: *"Should I invest in this specific startup?"*

### Core Components
1.  **Backend (Syllabus Goal)**: Migrate data from Excel to a **SQL Data Warehouse**.
2.  **Intelligence Layer (Thesis Goal)**: Implement **Phase 3 Deep-LLM** (Dual-Encoder) for state-of-the-art accuracy.
3.  **Frontend (Impact Goal)**: A **Streamlit Dashboard** for VCs to visualize "Hidden Gems" and "Overfunded Risks".

## 2. Methodology Steps

### Step 1: Data Engineering (Syllabus Alignment)
*   **Current**: `startup_data.xlsx` -> Pandas.
*   **New**: `startup_data.xlsx` -> **Star Schema Data Warehouse** (SQLite).
    *   **Fact Table**: `fact_funding_rounds` (dates, amounts, investors).
    *   **Dim Tables**: `dim_startup` (descriptions, category), `dim_time` (year/quarter), `dim_location` (city, region).
*   **Impact**: Demonstrates "Data Warehousing" and "SQL" proficiency required by the syllabus.

### Step 2: Advanced Modeling (Thesis Alignment)
*   **Current**: Single embedding (MPNet) or Category embedding (MiniLM).
*   **New**: **Dual-Encoder Fusion** (Phase 3).
    *   Use MPNet for *Startup Descriptions*.
    *   Use MiniLM for *Funding Narratives*.
    *   Fuse them for the final prediction.
*   **Impact**: Higher accuracy (0.71+ AUC) and technical depth.

### Step 3: "VC Copilot" Dashboard (Real-World Impact)
*   **Tool**: **Streamlit** (Python-only, fast to build).
*   **Features**:
    *   **"Hidden Gem Detector"**: List startups with High Success Prob but Low Funding.
    *   **"Investment Memo Generator"**: Use the LLM/SHAP to explain *why* a startup is good (e.g., "+15% because strong semantic match to Biotech winners").
    *   **"Portfolio Simulator"**: "If I invested in top 10 predicted startups in 2015, what would be my return?"

## 3. Why This Wins
*   **Syllabus**: You check off SQL, DB Design, and Data Warehouse.
*   **Real World**: You solve the "Information Asymmetry" problem for VCs (explicitly mentioned in your thesis).
*   **Effort**: You reuse your existing data and simpler ML code, just wrapping it in a better architecture. No new data collection needed.

## 4. Resources & Costs (User Question)
*   **Cost**: **$0.00**.
    *   **Database**: SQLite is built-in to Python. No Monthly Cloud Fees.
    *   **Dashboard**: Streamlit is free open-source. Runs locally on your laptop.
    *   **Compute**: Your laptop GPU/CPU is sufficient for these models (Deep-LLM uses pre-trained transformers which run fine for inference/small training).
*   **Difficulty**: **Easy**.
    *   I (the AI) will write the SQL schemas, the Streamlit code, and the Model pipeline.
    *   You (the User) only need to run the scripts.

## 5. Execution Roadmap
- [ ] **Database Setup**: Create SQLite DB and ETL script to load Excel data.
- [ ] **Model Upgrade**: Update `capstone_p4.py` to implement Phase 3 logic.
- [ ] **Dashboard**: Create `app.py` with Streamlit to visualize results from the DB.
