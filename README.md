 LLM Prompt Injection Detection Engine

 Overview

This project is a **security system for Large Language Models (LLMs)** designed to detect and prevent **malicious prompts**, such as:

* Prompt Injection Attacks
* Jailbreak Attempts
* System Manipulation Prompts
* Unsafe or Hidden Instructions

The system analyzes user input and classifies it as **safe or risky** before it reaches the AI model.

 Purpose

The main goal of this project is to:

* Protect LLMs from **unsafe or harmful inputs**
* Detect **malicious intent in prompts**
* Provide a **risk-based decision system** (Allow / Review / Block)
* Improve **AI safety and reliability**

 How It Works

The system follows a multi-layered approach:

 1. Dataset Collection

* Uses dataset from Hugging Face:

  ```
  svannie678/red_team_repo_social_bias_prompts
  ```
* Contains **malicious (red-team) prompts**
* All samples are labeled as:

  ```
  malicious
  ```

 2. Text Vectorization

* Uses **TF-IDF (Term Frequency - Inverse Document Frequency)**
* Converts text into numerical features
* Captures:

  * Important words
  * Word combinations (unigrams + bigrams)



3. Detection Layers
 Keyword-Based Detection

Checks for suspicious phrases like:

* ignore previous instructions
* bypass safety
* reveal system prompt
* act as system
* override rules

 Similarity-Based Detection

* Uses **Cosine Similarity**
* Compares input prompt with known malicious prompts
* Detects **rephrased or hidden attacks**

 4. Risk Score Calculation

The system calculates a risk score using:

```
Risk Score = (Keyword Score × 0.5) + (Similarity Score × 0.5)
```

 5. Decision System

Based on the risk score:

| Risk Score | Decision  |
| ---------- | --------- |
| Low        | ✅ ALLOW   |
| Medium     | ⚠️ REVIEW |
| High       | 🚫 BLOCK  |

 6. Advanced Analysis

The system also provides:

* Risk Level (Low / Medium / High / Critical)
* Confidence Score (%)
* Number of Red Flags
* Triggered Security Layers
* Top Similar Malicious Prompts
Output Example

For each input prompt, the system returns:

* Decision (ALLOW / REVIEW / BLOCK)
* Risk Score
* Similarity Score
* Detected Keywords
* Explanation of why it was flagged

 Technologies Used

* Python 
* Scikit-learn
* TF-IDF Vectorizer
* Cosine Similarity
* Hugging Face Datasets

 Features

* Multi-layered detection system
* Lightweight and fast
* Explainable results
* Works without heavy deep learning models
* Easy to integrate with any LLM pipeline

 Future Improvements

* Add Machine Learning / Deep Learning classifiers
* Expand dataset with more attack types
* Real-time API integration
* Dashboard for monitoring attacks
* Integration with chatbot systems



 📄 License

This project is for educational and research purposes.


