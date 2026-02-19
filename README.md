# 🏥 AI Health Chatbot — Symptom-Based Disease Prediction

> Built to explore how machine learning can bridge the gap in 
> healthcare access for underserved communities.

---

## Why I Built This

Access to a doctor isn't always immediate due to cost, location, and 
time. Millions of people face these barriers every day. 
In many rural and low-income communities, people make critical 
health decisions without any professional guidance, turning to 
Google and either panicking over minor symptoms or dismissing 
something that genuinely needs attention.

I wanted to build something that could change that. This chatbot takes your symptoms, asks intelligent 
follow-up questions, and predicts the most likely condition 
along with practical precautions and health tips. It's not a 
replacement for a doctor, but it's a starting point for people 
who don't have easy access to one.

This is a proof-of-concept for something I care deeply about: 
using AI to reduce healthcare inequality. Deployed as a mobile 
app or WhatsApp bot, a tool like this could genuinely reach the 
people who need it most.

---

## What It Does

- Understands symptoms written in plain English (not medical terms)
- Handles typos and informal language using NLP + fuzzy matching
- Asks intelligent follow-up questions based on the predicted disease
- Returns a diagnosis with a confidence score
- Gives actionable precautions and a motivational note

---

## How It Works

**1. Symptom Extraction**
The user types naturally: "I have a bad stomach ache and fever." 
The system uses synonym mapping, exact matching, and fuzzy 
matching (difflib) to extract valid medical symptoms from 
free-form text.

**2. Machine Learning Model**
A Random Forest Classifier trained on 4,920 patient records 
across 42 diseases. Features are binary symptom vectors 
(132 symptoms). Achieved strong accuracy on held-out test data.

**3. Guided Follow-Up**
Once an initial prediction is made, the chatbot asks about 
additional symptoms associated with that disease — refining 
its prediction before giving a final answer.

**4. Output**
- Predicted disease + confidence %
- Plain-English description of the condition
- Up to 4 specific precautions
- Motivational health tip

---

## Project Structure
```
AI-Health-Chatbot/
│
├── Data/
│   ├── Training.csv        # 4,920 encoded symptom records
│   └── Testing.csv         # Held-out evaluation data
│
├── MasterData/
│   ├── symptom_Description.csv   # Disease descriptions
│   ├── symptom_precaution.csv    # Precaution recommendations
│   └── Symptom_severity.csv      # Severity weights per symptom
│
├── Health_Chat_bot.py      # Main chatbot script
└── README.md
```

---

## Setup & Run
```bash
# Clone the repo
git clone https://github.com/Tsion-Woldeselassie/AI-Health-Chatbot.git
cd AI-Health-Chatbot

# Install dependencies
pip install pandas numpy scikit-learn

# Run the chatbot
python Health_Chat_bot.py
```

---

## Dataset Notes

The training data covers **42 conditions** across **132 symptoms**.  
During exploration, I noticed some column name inconsistencies 
in the raw data (e.g. `foul_smell_of urine`, `dischromic _patches`) 
which were retained to preserve alignment with the master 
symptom files.

---

## Future directions I'm exploring:
- Multilingual symptom input (Amharic, Hindi, Spanish, Swahili)
- Deployment as a lightweight web or WhatsApp interface
- Integration of severity scoring to flag emergency cases
- Expanding the disease library with WHO datasets

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core language |
| Scikit-learn | Random Forest model |
| Pandas / NumPy | Data processing |
| difflib | Fuzzy symptom matching |
| CSV / NLP | Knowledge base & text parsing |

---

## ⚠️ Disclaimer

This tool is for **educational purposes only** and does not 
constitute medical advice. Always consult a qualified 
healthcare professional for diagnosis and treatment.

---

*If you're working on AI for social good or healthcare access, 
I'd love to connect.*