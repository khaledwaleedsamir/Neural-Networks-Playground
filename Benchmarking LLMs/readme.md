# Arabic LLM Benchmarking: MSA and Egyptian Dialect Q/A Evaluation

This project benchmarks five Arabic-supporting Large Language Models (LLMs) on a 120-question Q/A dataset that covers Modern Standard Arabic (MSA) and Egyptian dialect. It evaluates the models on factual accuracy, fluency, dialectal comprehension, and hallucination rates using both automatic and human evaluation methods.

## 📋 Overview

The models under test:
- **GPT-4** (OpenAI)
- **llama3-70b-8192** (Meta)
- **gemma2-9b-it** (Google)
- **allam-2-7b** (KSA)
- **qwen-qwq-32b** (Qwen)

### Dataset
- **120 Q/A pairs**
- **20 topics** with 6 questions each
- Annotated with: 
  - Gold (reference) answers
  - Dialect and topic labels
  - Human evaluation metrics


## 📊 Evaluation Metrics

### ✅ Automatic Evaluation
- **STS (Semantic Textual Similarity)**
- **BERT Score (F1)**

### 👩‍⚖️ Human Evaluation
Scored from 1–5:
- **Accuracy**
- **Fluency**
- **Relevance**

Binary:
- **Hallucination** (Yes/No)


## 🛠️ Process Pipeline

1. Questions and answers were organized in an Excel sheet with dialect and topic metadata.
2. A Python script was used to:
   - Extract prompts
   - Query models via OpenAI API (for GPT-4) and **Groq** platform (for other models)
   - Store responses in the master Excel file
3. Automatic metrics (STS & BERT Score) computed.
4. Human annotators evaluated selected responses manually.


## 📈 Results Summary

| Model             | STS Avg | BERT F1 | Accuracy | Fluency | Relevance | Hallucination |
|------------------|---------|---------|----------|---------|-----------|----------------|
| GPT-4            | 0.71    | 0.8737  | 4.76     | 4.99    | 4.97      | 0.83%          |
| allam-2-7b       | 0.69    | 0.8630  | 4.71     | 4.54    | 4.81      | 7.5%           |
| gemma2-9b-it     | 0.60    | 0.8475  | 3.73     | 4.15    | 3.85      | 30.83%         |
| llama3-70b-8192  | 0.75    | 0.8662  | —        | —       | —         | —              |
| qwen-qwq-32b     | 0.60    | 0.8215  | —        | —       | —         | —              |

**Note:** Only three models were selected for manual review due to time constraints.


## 💡 Future Work

- Expand dataset to 500–1000+ Q/A pairs
- Incorporate more dialects
- Include deeper linguistic error analysis
- Build a GUI tool for streamlined human evaluation
