# Casual-Analysis-Conversational-Data

📌 Problem Overview

Customer support conversations often end in outcomes such as escalation, complaints, fraud investigation, or refunds.
While these outcomes are known, the reasons behind them are not always clear.

This project focuses on grounded explanation and reasoning over conversational data, rather than prediction.

The goal is to:

analyze multi-turn customer–agent conversations

identify why certain outcomes occur

support explanations using verbatim dialogue evidence

📂 Dataset

File: Conversational_Transcript_Dataset.json

Total conversations: 5,037

Domains: Banking, Healthcare, Telecom, E-commerce, Insurance

Each conversation contains:

transcript_id

domain

intent (final outcome)

reason_for_call

ordered conversation turns (Agent / Customer)

🧠 Approach Overview

We implemented a rule-based, explainable reasoning pipeline designed for faithfulness and interpretability, which aligns with the hackathon evaluation criteria.

The system focuses on:

retrieving relevant conversations

extracting escalation and issue signals from dialogue

generating human-readable explanations

grounding every claim with transcript evidence

No hallucination or synthetic text is introduced.

🧪 Task 1 – Single-turn Explanation
Objective

Given a single analytical question (e.g. “Why do customers escalate calls in banking conversations?”), generate a grounded explanation.

Methodology

Infer intent from the question using keyword matching

Retrieve relevant conversations based on intent

Extract customer escalation signals (e.g. requests for managers, complaints)

Aggregate common linguistic patterns

Generate a concise explanation supported by representative transcript IDs

Output

Natural language explanation

Verbatim dialogue snippets

3–5 representative transcript IDs as evidence

This ensures:

Faithfulness – all claims are grounded

Clarity – concise, human-readable output

Relevance – no unnecessary data dumping

🔄 Task 2 – Multi-turn Follow-up Reasoning
Objective

Handle follow-up questions while maintaining context, consistency, and evidence reuse.

Key Feature: Conversational Memory

A memory object stores:

inferred intent

retrieved conversations

transcript IDs used as evidence

Behavior

For follow-up questions, previously analyzed conversations are reused

For new topics, fresh retrieval is performed

Analysis focus can shift (customer behavior → agent behavior → domain-level patterns)

Transcript IDs remain consistent across turns

Example Follow-ups

“Which agent responses made the situation worse?”

“Is this behavior common across other domains?”

🏗️ Project Structure
.
├── Conversational_Transcript_Dataset.json
├── Task1_Task2.ipynb
├── predictive powerhouse.ipynb
├── task1_queries_outputs.csv
└── README.md

⚙️ How to Run

Install dependencies:

pip install pandas


Open the notebook:

jupyter notebook Task1_Task2.ipynb


Run cells sequentially to execute:

Task 1 (single-question explanation)

Task 2 (multi-turn follow-up reasoning)

✅ Evaluation Alignment

This solution is designed to maximize:

Faithfulness – no hallucinated content

ID Recall – correct and relevant transcript IDs

Relevance – answers directly address the question

Explainability – easy to interpret and justify

The approach intentionally prioritizes clarity and grounding over complex modeling.

🚀 Final Notes

This is an analysis and explanation system, not a prediction model

Representative transcript IDs are intentionally used instead of exhaustive listing

The system is robust, transparent, and judge-defensible

👥 Team

The Outliers

(Sk Aziz Jalaluddin, Soham Swain, Shubham Acharya)
