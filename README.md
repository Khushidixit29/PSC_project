#  Agentic AI for Early Sepsis Detection in ICU (MIMIC-IV)
### **Multimodal • Fuzzy Logic • GA Optimization • LLM Reasoning**

---

##  Overview

Early detection of sepsis is a life-critical problem — every hour of delay significantly increases mortality.  
Traditional methods depend on **late-stage organ dysfunction (Sepsis-3)**, causing delays of 6–12 hours.

This project builds a **multimodal, interpretable, agentic AI system** for early ICU sepsis risk detection using a **10,000-stay subset of MIMIC-IV**.

The system integrates:

-  **Time-series Vitals**
-  **Laboratory Trends**
-  **Fuzzy Logic Risk Scoring**
-  **GA Optimization** (threshold tuning)
-  **LLM Agent** (clinical reasoning + action suggestions)
-  **Clinical Notes** (discharge & radiology text)

Unlike black-box ML models, this pipeline provides:  
✔ Numerical predictions  
✔ Clinically interpretable fuzzy risk  
✔ Human-like, agentic reasoning  

---

#  Project Highlights

##  1. Multimodal Data Fusion
Combines vitals, labs, demographics, diagnoses, and clinical text from MIMIC-IV.

---

##  2. GA-Optimized Fuzzy Logic
A transparent fuzzy risk score capturing early abnormalities in HR, BP, RR, SpO₂.

**Genetic Algorithm tunes:**
- High HR threshold  
- Low SBP threshold  

---

##  3. Agentic LLM Clinical Reasoning
A Gemini-based agent generates:
- Clinical interpretations  
- Risk assessments  
- Suggested actions  

Forms a closed loop: **Perceive → Reason → Suggest**

---

##  4. ICU-Ready Interpretability
Doctors can clearly understand *why* the model gives a risk score.

---

##  5. Fully Reproducible Kaggle Notebook
End-to-end pipeline:
- Load subset files  
- Feature engineering  
- Fuzzy scoring  
- GA optimization  
- LLM agent reasoning  

---

#  Architecture
<img width="1875" height="2250" alt="image" src="https://github.com/user-attachments/assets/2b35025d-d2f1-48ad-87b5-344869ee293b" />


---

#  Dataset Used

10k ICU-stay subset extracted from MIMIC-IV:

- `icustay_subset.csv`
- `chartevents_filtered.csv` (vitals)
- `labevents_filtered.csv` (labs)
- `patients_subset.csv`
- `admissions_subset.csv`
- `diagnoses_withstayids.csv`
- `discharge_notes_clean.csv`
- `radiology_notes_clean.csv`

---

#  Fuzzy Logic Model

### **Input Variables**
- HR_mean  
- SBP_mean  
- RR_mean  
- SpO₂_mean  

### **Membership Functions**
- High HR  
- Low SBP  
- High RR  
- Low SpO₂  

### **Aggregation**
Additive fuzzy inference:

Risk = HR_high + SBP_low + RR_high + SpO2_low

### **Defuzzification**
Soft defuzzification:

fuzzy_score = tanh(aggregated_risk)

Produces a crisp **0–1 sepsis risk score**.

---

#  Genetic Algorithm (GA) Optimization

Optimizes fuzzy cutpoints:

- HR_high_cut  
- SBP_low_cut  

Uses **AUROC** as fitness.

Example output:
Best GA parameters: [118.36, 51.25]

---

#  LLM Agent Component

### **Inputs:**
- Vital summaries  
- Lab summaries  
- Fuzzy score  
- Clinical notes (optional)  

### **Outputs:**
- Clinical interpretation  
- Risk narrative  
- Suggested actions  

**Example:**
> “The patient shows moderate tachycardia and low SBP. Recommend fluid assessment and lactate re-check.”

This creates a full **agentic loop**.

---

#  How to Run (Kaggle)

1. Upload your MIMIC subset files to `/kaggle/input`  
2. Open the notebook  
3. Run these steps:
   - Load data  
   - Preprocess  
   - Fuzzy Logic  
   - GA Optimization  
   - LLM Agent  
4. Retrieve final risk score + explanation  

---

#  Outputs

- `fuzzy_score` (0–1)  
- GA-optimized thresholds  
- LLM explanation  
- Risk severity summary  

---

#  Key Contributions

✔ Novel agentic architecture  
✔ Combined **Fuzzy Logic + GA + LLM**  
✔ Transparent early-warning scoring  
✔ Real-world medical interpretability  
✔ Multimodal clinical data fusion  
✔ Fully reproducible  

---

#  Future Work

- Add Sepsis-3 label extraction  
- Integrate real-time streaming vitals  
- Build transformer-based note embeddings  
- Expand fuzzy rule base  
- Develop ICU bedside dashboard  

---

#  Acknowledgements

This project uses data from the **MIMIC-IV** database (MIT-PhysioNet).  
CITI certification and MIMIC-IV access approval required.

---

# 📘 License

Academic & research use under MIMIC-IV data sharing restrictions.
