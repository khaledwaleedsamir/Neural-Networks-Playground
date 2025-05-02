# Arabic LLM Benchmarking: Q/A Evaluation across Dialects and Domains

## Overview

This project benchmarks multiple Arabic-supporting Large Language Models (LLMs) on a 100-question Q/A dataset covering Modern Standard Arabic (MSA), Classical Arabic, and various dialects (e.g., Egyptian). The goal is to assess factual accuracy, fluency, dialectal comprehension, and hallucination rates.

## Models Evaluated

* **Meta LLaMA3-70B** (`llama3-70b-8192` via Groq)
* **DeepSeek-R1 Distilled LLaMA-70B** (`deepseek-r1-distill-llama-70b`)
* **Gemma2-9B-IT** (Google multilingual model)
* **Allam-2-7B** (Arabic-native model from KSA)
* **Qwen-QWQ-32B** (multilingual model with Arabic capabilities)
* **GPT-4.0 (OpenAI)** for comparison with commercial-grade LLMs

## Dataset

* **100 Q/A pairs** with gold-standard human-annotated answers
* **5 questions from each of 20 topics** (e.g., History, Religion, Culture, Geography, Science, etc.)
* Annotated with:

  * Dialect used (MSA, Egyptian, etc.)
  * Topic

## Evaluation Criteria

### Automatic Metrics

* **BLEU**: Measures n-gram overlap between LLM output and gold answer.
* **ROUGE**: Measures recall and overlap, especially for longer answers.
* **STS (Semantic Textual Similarity)**: Measures meaning similarity beyond surface text.

### Human Evaluation

Scored from 1 to 5:

* **Accuracy**: Is the answer factually correct?
* **Fluency**: Is the answer grammatically and stylistically natural?
* **Relevance**: Does the answer address the question fully?
* **Hallucination**: Any incorrect or fabricated content?

## Pipeline

1. **Excel Preparation**: Master sheet with all questions, gold answers, dialect, topic, and placeholders for each LLM.
2. **Answer Collection**: Python scripts call each LLM via its API and fill in the corresponding column in the Excel sheet.
3. **Evaluation**:

   * Automatic metrics calculated using `sacrebleu`, `rouge_score`, `sentence-transformers`
   * Human evaluators fill in scores manually

## Requirements

* Python 3.8+
* `openpyxl`, `pandas`, `openai`, `groq`, `sacrebleu`, `rouge-score`, `sentence-transformers`

## How to Run

1. Set up API keys in environment variables or config file
2. Run `generate_excel.py` to create the base spreadsheet
3. Run `generate_answers.py` for each model
4. Run `evaluate_automatic.py` to compute BLEU, ROUGE, STS

## Results (Sample Placeholder)

| Model  | Avg BLEU | Avg ROUGE-L | Avg STS | Accuracy | Fluency | Relevance | Hallucination Rate |
| ------ | -------- | ----------- | ------- | -------- | ------- | --------- | ------------------ |
| LLaMA3 | 0.54     | 0.68        | 0.82    | 4.2      | 4.5     | 4.4       | 3%                 |

## License

MIT License

## Contributors

* \[Your Name Here]
* \[Teammates, if any]
