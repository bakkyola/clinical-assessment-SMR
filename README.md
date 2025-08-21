# clinical-assessment-SMR

# Structured Medication Review with LLMs (BNF/NICE-Guided)

This repository contains code developed as part of **Olayemi Bakare’s MSc Research Work** at *Queen Mary University of London (Digital Environment and Innovation Lab)*.  
It demonstrates how Large Language Models (LLMs) can be applied to **structured medication reviews** in **polypharmacy / multimorbidity patients**, aligning prescriptions with **BNF/NICE clinical guidelines**.

---

## 📖 Overview

The project uses the Hugging Face model **DeepSeek-R1-Distill-Llama-8B** to:

- Parse patient data (`patients.json`)  
- Prompt the model as a **UK clinical pharmacist**  
- Generate a **Markdown table** per patient with:  
  - Medication  
  - Matched Diagnosis  
  - Guideline Compliance  
  - Citation (e.g., NICE guideline numbers)  
  - Notes  
  - Optimisation Recommendation (continue, discontinue, adjust, switch)  
- Save outputs as both raw text and structured CSVs for analysis.  

---

## 🛠 Requirements

- Python 3.9+  
- Recommended: virtual environment or conda  

### Install dependencies

```bash
pip install transformers pandas
```

## 🚀 How to Use
```📂 Project Structure
.
├── patients.json                              # Example patient dataset
├── medication_review_notebook.ipynb           # Jupyter Notebook (main workflow)
├── results/                                   # Raw model outputs (generated)
├── results_csv/                               # Structured CSV outputs (generated)
└── README.md
```
1. Clone this repository
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>

2. Prepare your environment
python -m venv venv
source venv/bin/activate   # On Linux/Mac
venv\Scripts\activate      # On Windows
pip install -r requirements.txt

(If you don’t have a requirements.txt, simply install transformers and pandas.)

3. Add patient data
Place your patient data in `patients.json`.
Format:
```
{
  "PAT001": {
    "patient_id": "PAT001",
    "age": 65,
    "sex": "M",
    "diagnosis": "Hypertension; Type 2 Diabetes",
    "medication": "Lisinopril; Metformin"
  },
  "PAT002": {
    "patient_id": "PAT002",
    "age": 70,
    "sex": "F",
    "diagnosis": "Atrial Fibrillation; Heart Failure",
    "medication": "Warfarin; Digoxin; Furosemide"
  }
}
```
4. Run the Notebook
Open the notebook in Jupyter:
jupyter notebook medication_review.ipynb

Or run it directly in VS Code / JupyterLab.

5. Outputs
Raw LLM outputs: saved in results/{patient_id}_medication_diagnosis_result.txt
Structured CSVs: saved in results_csv/{patient_id}_medication_diagnosis_structured.csv
Each CSV contains columns:
```
| Medication | Matched Diagnosis | Guideline Compliance | Citation | Notes | Optimisation Recommendation |
| ---------- | ----------------- | -------------------- | -------- | ----- | --------------------------- |
```
📊 Example Output
📋 Medication-Diagnosis Analysis for PAT001:
```
| Medication | Matched Diagnosis | Guideline Compliance | Citation   | Notes                          | Optimisation Recommendation |
|------------|------------------|----------------------|------------|-------------------------------|-----------------------------|
| Lisinopril | Hypertension     | First-line           | NICE NG136 | ACE inhibitor recommended      | CONTINUE - well tolerated   |
| Metformin  | Type 2 Diabetes  | First-line           | NICE NG28  | Standard first-line treatment  | CONTINUE - appropriate      |
```




⚠️ Disclaimer
This project is part of an academic research
The LLM outputs are not clinical advice and must not be used as standalone medical recommendations.
Always consult official NICE/BNF guidelines and qualified clinicians.
