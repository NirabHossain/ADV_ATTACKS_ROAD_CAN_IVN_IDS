# Adversarial Evaluation of CAN-Bus Intrusion Detection Systems (IDS)

This repository contains the full implementation and experimental pipeline for evaluating **adversarial robustness of machine-learning–based Intrusion Detection Systems (IDS)** operating on the **Controller Area Network (CAN)** using the **ROAD dataset**.

The work systematically analyzes **false alarms (false positives)** and **missed attacks (false negatives)** under **protocol-compliant, payload-level adversarial perturbations**, following a unified evaluation framework.

This repository accompanies the research paper:

> **Evaluating False Alarm and Missing Attacks in CAN IDS**  
> *Nirab Hossain, Pablo Moriano*  
> University of Colorado Boulder & Oak Ridge National Laboratory

---

## 📌 Project Overview

Modern vehicles rely on the CAN bus for safety-critical communication but lack built-in security mechanisms. Machine-learning–based IDS have shown strong baseline detection performance, yet their **robustness against adversarial manipulation** remains underexplored.

### Main Objectives
- Evaluate **adversarial failure modes** of CAN IDS:
  - **False alarms** (benign → malicious)
  - **Missed attacks** (malicious → benign)
- Apply **protocol-compliant adversarial attacks** on CAN payload bytes
- Compare robustness across **shallow ML models and deep neural networks**
- Quantify robustness using **ASR (Attack Success Rate)** and **MCC**

---

## 🧠 Models Evaluated

The following IDS architectures are implemented and evaluated:

| Model | Type |
|-----|-----|
| Decision Tree (DT) | Shallow |
| Random Forest (RF) | Ensemble |
| Extra Trees (ET) | Ensemble |
| XGBoost (XGB) | Boosted Trees |
| Deep Neural Network (DNN) | Fully-connected |

All models operate at the **frame level**, using **CAN payload bytes (D0–D7)** as features.

---

## 🧪 Adversarial Threat Model

- **White-box attacker**
- **Protocol-compliant constraints**
  - CAN ID and DLC fixed
  - Payload bytes only
  - Values clipped to `[0, 255]`
- **Gradient-based attacks** generated using **ART**:
  - FGSM
  - BIM
  - PGD
- Perturbation budgets: `ε ∈ {1, 5}`

---

## 📂 Dataset

We use the **ROAD CAN IDS Dataset**:

- ~3.5 hours of real vehicle CAN traffic
- ~1.5M benign frames
- ~50K malicious frames
- Realistic **fabrication & masquerade attacks**

### Attack Types Used
- FA (Fuzzing Attack)
- MECTA (Max Engine Coolant Temperature)
- MSA (Max Speedometer)
- RLOFFA (Reverse Light Off)
- RLONA (Reverse Light On)
- CSA (Correlated Signal Attack)

📖 Dataset reference:  
Verma et al., *PLOS ONE*, 2024

---

## 📁 Repository Structure

