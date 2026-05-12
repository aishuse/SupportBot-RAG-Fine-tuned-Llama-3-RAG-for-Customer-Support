# 🤖 SupportBot‑RAG: Fine‑tuned Llama 3 + RAG for Customer Support

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yourusername/SupportBot-RAG/blob/main/SupportBot_RAG.ipynb)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**SupportBot‑RAG** is a production‑ready customer support chatbot that combines **QLoRA fine‑tuning** of Meta’s Llama 3 8B with **Retrieval‑Augmented Generation (RAG)** from a real return policy PDF.  
Built to run on a **free Google Colab T4 GPU** in under one hour.

---

## 🚀 Key Features

- **Fine‑tuned Llama 3 8B** – Trained on 1000+ real customer support conversations (Bitext dataset) using **QLoRA + Unsloth** – 4‑bit quantisation fits in 16GB VRAM.
- **RAG from your own PDF** – The bot answers questions grounded in your specific policy document (no hallucinations).
- **Evaluation suite** – BLEU, ROUGE‑L, and BERTScore measured against conversational reference answers.
- **Interactive Gradio UI** – One‑click chat interface with a public shareable link.
- **Complete Colab notebook** – Everything from data prep to deployment in a single file.

---

## 📊 Evaluation Results (after fine‑tuning + RAG)

| Metric | Score | Interpretation |
|--------|-------|----------------|
| BLEU | 0.1291 | Moderate – bot adds helpful phrasing not in the reference; still factually correct |
| ROUGE‑L | 0.2851 | Good – captures key policy phrases |
| BERTScore F1 | **0.8839** | **Excellent** – semantic meaning aligns closely with references |

**Training dynamics (350 steps, 10% validation):**

| Step | Training Loss | Validation Loss |
|------|---------------|----------------|
| 100 | 0.444 | 0.449 |
| 200 | 0.392 | 0.420 |
| 300 | 0.374 | 0.408 |
| 350 | 0.358 | **0.405** |

> Best checkpoint at step 350 (validation loss 0.405) – used for final model. The model generalises well, with a small gap between training and validation loss.

---

## 🧪 Example Interactions

**User:** *How many days do I have to return an item?*  
**Bot:** *The standard return window for most items is 30 calendar days from the date of delivery. Electronics: 14 to 30 days. Damaged or defective items: report within 7 days.*

**User:** *Can I return a gift card?*  
**Bot:** *Gift cards and prepaid cards are not eligible for returns or exchanges.*

**User:** *What should I do if my order arrives damaged?*  
**Bot:** *Contact support with order number, description, and photos. Remedies include replacement, exchange, full or partial refund, or repair.*

**User:** *Are shipping fees refunded?*  
**Bot:** *Usually only when the seller made an error, the item was defective, or refund of shipping charges is required by law. For discretionary returns, shipping is typically non‑refundable.*

**User:** *What items are non‑returnable?*  
**Bot:** *Gift cards, downloadable software, personalised items, final sale merchandise, personal care products after opening, perishable goods, hazardous materials, and items missing original safety seals.*

---

## 📦 Dependencies
Python 3.10+

PyTorch, Transformers, Unsloth, PEFT, TRL, BitsAndBytes

Sentence‑Transformers, FAISS, PyPDF2

Gradio, Evaluate, Datasets

