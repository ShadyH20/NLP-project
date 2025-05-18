# Milestone 3 Report: SQuAD v2.0 RAG Experiments

---

## Introduction

For this milestone, we set out to build and compare two Retrieval-Augmented Generation (RAG) QA systems using the SQuAD v2.0 dataset. Our main goal was to investigate how different model choices and enhancements affect QA performance, especially in handling both answerable and unanswerable questions.

---

## Logical Steps & Reasoning

### 1. **Dataset Selection**

We chose SQuAD v2.0 because it is a well-established benchmark for QA, containing both answerable and unanswerable questions. This allowed us to test not only answer extraction but also the models' ability to recognize when no answer is present.

### 2. **Experiment Design**

Based on the milestone clarifications, we needed two comparable experiments. We designed:

- **Experiment 1:** RAG with a SQuAD-pretrained model (`deepset/roberta-base-squad2`).
- **Experiment 2:** RAG with a general QA model not specifically trained on SQuAD v2.0 (`bert-large-uncased-whole-word-masking-finetuned-squad`).

Both systems used the same retrieval and evaluation pipeline, so the only variable was the model itself.

### 3. **System Implementation**

- **Document Store:** We indexed all unique contexts from SQuAD using FAISS and sentence-transformer embeddings for efficient semantic search.
- **Retriever:** We implemented enhanced retrieval using Maximum Marginal Relevance (MMR) and keyword/entity-based re-ranking to ensure diverse and relevant context selection.
- **RAG Pipeline:** For each question, the retriever fetched relevant contexts, which were then passed to the QA model to generate an answer.
- **Conversation Management:** We maintained chat history and allowed context from previous turns to influence retrieval and answering, simulating a real chatbot.
- **Caching & Optimization:** To speed up repeated queries, we cached answers and used dynamic confidence thresholds.

### 4. **Evaluation**

- We selected a balanced set of answerable and unanswerable questions from the SQuAD validation set.
- For each system, we computed F1, BLEU, ROUGE, semantic similarity, and exact match scores.
- We also performed error analysis and statistical significance testing to compare the models.

---

## Key Findings

- **SQuAD-Pretrained Model Wins on F1:** The SQuAD-pretrained model consistently outperformed the general model on F1, exact match, and handling unanswerable questions.
- **General Model Shows Strengths:** The general model sometimes produced more semantically similar or verbose answers, especially for "when", "who" and "other" questions.
- **Retrieval Quality is Crucial:** Both models benefited from our improved retrieval (MMR + keyword/entity re-ranking), confirming that good context is essential for strong QA performance.
- **Error Patterns Differ:** The SQuAD model was more cautious (lower false positives on unanswerable questions), while the general model was more likely to guess.
- **Statistical Significance:** The difference in F1 scores between the two models was statistically significant, confirming the impact of model choice.

---

## Future Improvements

- **Hybrid Model Ensemble:** Combine both models' predictions using a meta-model or confidence-weighted voting.
- **Advanced Retrieval:** Try dense passage retrieval or hybrid sparse-dense methods for even better context selection.
- **Answer Verification:** Add a post-processing step to verify answer factuality and consistency.
- **Fine-Tuning:** Fine-tune the general model on SQuAD v2.0 to see if it can close the gap.

---

## Conclusion

Through these experiments, we learned that both model selection and retrieval quality are key to building effective RAG QA systems. The SQuAD-pretrained model is better for datasets like SQuAD v2.0, but retrieval enhancements help all models. Our error analysis also highlighted areas for further improvement, especially in answer abstention and context selection. We’re excited to keep building on this foundation!

---

_Prepared by: Shady Hani & Sherifa Hammoud_  
_Semester 10, NLP Project_
