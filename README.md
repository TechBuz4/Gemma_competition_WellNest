
# WellNest – Technical Writeup  
### Google Gemma 3n Impact Challenge Submission

---

## Overview

**WellNest** is an AI-powered,  perinatal care companion that supports women from early pregnancy through postpartum recovery. Built on **Gemma 3n**, the app delivers predictive health alerts, personalized wellness guidance, mental health screening, and empathetic virtual support community, all while preserving user privacy and working in low-connectivity environments.

---

## Problem Statement

 - Every day in 2023, over 700 women died from preventable causes
   related to pregnancy and childbirth. [1]
   
 - A maternal death occurred almost every 2 minutes in 2023. [1]
 - Approximately 1 in 10 women will experience postpartum depression after giving birth, with some studies reporting 1 in 7 women. [2]

Maternal healthcare faces critical gaps in early risk detection, postpartum mental health, and access to continuous care, especially in remote or underserved areas. Many women lack access to real-time, personalized guidance and community support during this vital life stage.


---

## 💡 Solution

WellNest addresses these challenges by combining:

- **A Gemma 3n-powered Prenatal risk prediction** from using body vitals to predict low, mid or high risk pregnancy
- **Postpartum depression screening** through the use of EPDS score to ssess mental risk
- A **Gemma 3n-powered virtual assistant Nestie** for empathetic interaction, mentall health help, advices and many more
- **Community insights and personalized wellness nudges**

---

## ⚙️ System Architecture

User Input (Text)  
↓  
Gemma 3n Local Inference
↓  
Core Services:
-   Risk Prediction
-   Mental Health Screening
-  Virtual doula (Virtual Assistant)
-   Community (Recommendations Engine)

### Key Components:

- **Frontend:** Web app using Loveable for deployment
- The core model backend is built using **Gemma 3n E2B**, optimized for local deployment and fine-tuned using **Unsloth** for both performance and efficiency. Specifically, we fine-tuned two distinct models:

-  **Pregnancy Health Predictor:** Fine-tuned to analyze self-reported symptoms, health logs, and uploaded reports to assess potential prenatal risk factors.
    
-  **Virtual Health Companion:** Trained to understand user tone, monitor mental health status, and offer personalized support. It can detect signs of emotional distress, screen for potential postpartum depression, and recommend appropriate next steps.
- **Data Privacy Layer:** User data is encrypted and never leaves the device  
- **NLP Pipeline:** Summarization, intent detection, and emotional tone analysis via fine-tuned Gemma layers  

---

## 🤖 Use of Gemma 3n

Gemma 3n is at the heart of WellNest’s intelligence and impact.

We used **Gemma 3n E2B**, fine-tuned via **Unsloth**, to power two key components of our application:

1.  **Risk Prediction Engine:** Gemma 3n processes user-input body vitals (e.g., heart rate, blood pressure, reported symptoms) and health logs to assess potential prenatal complications. The model is trained on perinatal datasets and medical QA corpora to provide personalized, AI-driven health insights in real time.
    
2.  **AI Virtual Health Companion:** A second fine-tuned instance of Gemma 3n acts as an empathetic, conversational assistant. It understands natural language, detects emotional tone, screens for signs of postpartum depression, and offers supportive dialogue. When needed, it guides users to verified local and national mental health resources.
    

By leveraging Gemma 3n’s multimodal understanding,off-line, on-device readiness, and compact architecture, WellNest demonstrates how AI can deliver real, private, and personalized care, even in low-resource or offline environments. This makes it uniquely suited for maternal health support at scale.

---

## 🧪 Model Fine-Tuning

Gemma 3n was fine-tuned using:

- **Medical QA and symptom datasets** (MIMIC-III, n2c2 clinical notes)
- **Maternal Health dataset** from Kaggle

Fine-tuning was executed using **Unsloth** for memory-optimized training on limited hardware.

---

## 🚧 Technical Challenges & Solutions

| Challenge             | Solution                                                                 |
|-----------------------|--------------------------------------------------------------------------|
| Limited Technical Expertise    | As a small team without deep ML Ops or deployment experience, we chose **Lovable Studio** (a no-/low-code platform) for frontend and orchestration. This allowed us to focus on AI behavior, product design, and user experience, without getting blocked by infrastructure.       |
| Model Deployment  | We used **Google Vertex AI** to deploy our fine-tuned Gemma 3n models. Vertex AI provided a simple, reliable way to create scalable endpoints and test iterations quickly without heavy DevOps overhead.         |
| Hyperparameter Tuning      | Fine-tuning Gemma 3n via **Unsloth** involved experimenting with numerous hyperparameter combinations — including learning rates, quantization formats, batch sizes, and LoRA configurations — to achieve the balance between performance, model size, and speed   |
| Healthcare Data Access & Privacy  | Working with healthcare data was especially challenging due to HIPAA compliance, ethical concerns, and data scarcity. We overcame this by relying on publicly available, de-identified datasets, weak supervision, and synthetic data generation to augment our training corpora while maintaining privacy and safety standards.|

---
Here’s a cleaned-up and well-formatted version of your project resource links, perfect for including in your **README**, **documentation**, or **competition submission**:

---

## 🔗 Project Resources

### Demo Video

[Watch the WellNest AI Demo](https://youtu.be/ADWLehSOrto)

---

### Repositories

* **Main GitHub Repository:**
  [TechBuz/Gemma\_competition\_WellNest](https://github.com/TechBuz4/Gemma_competition_WellNest)

* **Live App Source Code:**
  [edidiongetetim/well-nest](https://github.com/edidiongetetim/well-nest)

---

### Live Web App

🔗 [Try the WellNest Web App](https://well-nest.lovable.app/)

---

### Hugging Face Models

* **Risk Predictor (Gemma 3N):**
  [TechBuz/gemma-3N-risk\_predictor](https://huggingface.co/TechBuz/gemma-3N-risk_predictor)

* **Chatbot - Nestie (Gemma 3N):**
  [TechBuz/gemma\_3n\_chatbot\_Nestie](https://huggingface.co/TechBuz/gemma_3n_chatbot_Nestie)

---

### Ollama Local Deployments

* **Risk Predictor (4-bit Gemma 3N):**
  [wellnest\_risk\_predictor](https://ollama.com/bosaosanwo/wellnest_risk_predictor)

* **Chatbot - Nestie (4-bit Gemma 3N):**
  [wellnest\_gemma\_3n\_nestie](https://ollama.com/bosaosanwo/wellnest_gemma_3n_nestie)

---

Let me know if you'd like this turned into a PDF one-pager, website section, or GitHub `README.md`.

## References

- Google Gemma 3n Documentation  
- Unsloth Fine-Tuning Guide  
- Edinburgh Postnatal Depression Scale (EPDS)  
- WHO Maternal Health & Childbirth Datasets  
- Ollama for Local LLM Inference  
