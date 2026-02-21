# Project Plan: Investment Intelligence Platform for Tech Startups

**Student Name:** Annanahmed Shaikh
**Course:** DATA-6950 Capstone II
**Project Title:** Predicting Tech Startup Success Using Multi-Embedding LLM Signals & Investment Analytics

---

## 1. Background & Literature Review

### Business Motivation
The venture capital (VC) industry deploys over $300 billion annually, yet it functions with significant inefficiency: approximately 75-80% of venture-backed startups fail to return initial capital [1]. Investment decisions at the critical Seed and Angel stages are frequently driven by subjective heuristics and network effects rather than empirical evidence. This reliance on intuition creates a "capital gap" for high-potential startups that lack traditional signals, resulting in billions of dollars in misallocated funds [6].

### Academic Context
Predictive modeling for startups has historically relied on *post-traction* metrics—such as revenue growth or Series B funding—which are unavailable during the early diagnostic stages [17]. Recent research has demonstrated that textual narratives (business descriptions, mission statements) contain latent predictive signals. Zhou et al. (2023) showed that Large Language Models (LLMs) can extract semantic meaning from company descriptions to improve classification accuracy by 8-12% over baselines [23]. However, existing approaches often lack interpretability. By integrating SHAP (SHapley Additive exPlanations) values, we can ensure that these complex "black box" models provide transparent, actionable insights for investors [40].

---

## 2. Project Aims and Objectives

The primary aim is to develop an **Investment Intelligence Platform**—a production-ready decision support system that fuses Deep Learning with Structured Financial Data to predict startup success at the pre-traction stage.

### Specific Objectives:
1.  **Develop a Deep-LLM Multi-Embedding Architecture:** Implement a dual-encoder model (Phase 3) fusing MPNet (for product vision) and MiniLM (for funding narratives) with structured data to achieve **ROC-AUC > 0.71**, extending the single-embedding work of Chadha et al. [17].
2.  **Engineer a Scalable Data Warehouse:** Migrate static Excel data into a normalized **SQL Data Warehouse (Star Schema)** to enabling complex querying of historical trends and sector performance (satisfying data engineering learning outcomes).
3.  **Deploy an Interactive VC Dashboard:** Build a "VC Copilot" web application using **Streamlit** to visualize "Hidden Gems" (high probability, low funding) and "Overfunded Risks" with real-time explainability.

---

## 3. Expected Outcomes Outline

This project addresses the information asymmetry in early-stage investing by delivering:

*   **Production-Grade SQL Database:** A relational database (SQLite) storing 47,000+ startups, normalized into Fact (Rounds) and Dimension (Startup, Time, Location) tables.
*   **Predictive Investment Dashboard:** A deployed Streamlit application allowing investors to filter startups by "Predicted Success Probability" and view "Risk Scores."
*   **Novel "Deep-LLM" Model:** A validated Random Forest ensemble using PCA-reduced textual embeddings (32 components) that outperforms traditional financial-only models by ~3-5%.
*   **Actionable Investment Lists:** Automated identification of specific "Hidden Gem" startups that are statistically undervalued by the market.

---

## 4. Evaluation Criteria

Success will be measured against rigorous technical and practical metrics:

### 1. Model Performance
*   **Accuracy:** Achieve **ROC-AUC ≥ 0.71** and **Precision@200 ≥ 95%** (validating that the top 200 recommendations are highly reliable).
*   **Interpretability:** Every prediction must be accompanied by a top-3 feature attribution list (e.g., "Driven by: Strong Biotech Semantic Cluster, Top-Tier Location").

### 2. System Quality & Feasibility
*   **Data Integrity:** The SQL database must pass normalization tests (3NF) and handle join queries under 500ms.
*   **Feasibility:** The entire stack (SQLite + Streamlit + Scikit-Learn) is designed to run locally without expensive cloud infrastructure, ensuring 100% reproducibility and zero cost.

---

## 5. Timeline and Milestones

| Week | Phase | Key Tasks & Deliverables |
| :--- | :--- | :--- |
| **1-3** | **Planning** | Data Review, Project Plan Submission. <br>**Del:** Project Plan (This Doc). |
| **4** | **Data Eng** | Design Star Schema (Entity-Relationship Diagram). |
| **5** | **Data Eng** | ETL Pipeline Implementation (Excel to SQL Migration). <br>**Del:** Progress Report I. |
| **6** | **Model Dev** | Implement MPNet + MiniLM Embedding Generation. |
| **7** | **Model Dev** | Train Final Random Forest with PCA Features. <br>**Del:** Progress Report II. |
| **8** | **Review** | Midterm Presentation (Methodology & Initial Results). |
| **9** | **Break** | *Spring Break*. |
| **10** | **App Dev** | Build Streamlit Frontend (Search & Filter Logic). |
| **11** | **App Dev** | Integrate Model Inference & SQL Backend. <br>**Del:** Progress Report IV. |
| **12** | **App Dev** | Add SHAP Explanations & Visualization Charts. |
| **13** | **Polish** | Final Code Refactoring & Draft Report. |
| **14** | **Delivery** | Final Presentation Preparation. |
| **15** | **Delivery** | **Final Report (IEEE Format) & Live Demo.** |

---

## 6. References

[1] Failory, “Startup Failure Rate: How Many Startups Fail and Why in 2024?,” 2024. [Online]. Available: https://www.failory.com.
[2] CB Insights, “The Top 20 Reasons Startups Fail,” 2024.
[6] B. Klinger and M. Schündeln, “Can Entrepreneurial Activity Be Predicted?,” World Bank WP 5882, 2011.
[17] A. Chadha, S. Kumar, and R. Mehta, “Predicting Startup Success Using Machine Learning,” arXiv:2007.04271, 2020.
[23] L. Zhou et al., “LLM4Startups: Large Language Models for Startup Outcome Prediction,” arXiv:2311.01746, 2023.
[40] S. Lundberg and S.-I. Lee, “SHAP: Interpreting ML Models,” NeurIPS, 2017.
