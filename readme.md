# Circular Economy Improvement Using Machine Learning (EcoShop)
### *Classifying Products as Recyclable or Biodegradable Through Image Analysis*


> **Final Year Bachelor of Technology Project** submitted in partial fulfillment of the requirements for the award of the degree in **Bachelor of Technology in Computer Science and Engineering (Data Science & Artificial Intelligence)**.
>
> **Looking to install and run the project locally?** See the complete [**Project Setup & Developer Guide (`PROJECT_SETUP_README.md`)**](./PROJECT_SETUP_README.md).

---

## Academic Project Details

| Field | Details |
| :--- | :--- |
| **Project Title** | **Circular Economy Improvement Using Machine Learning: Classifying Products as Recyclable or Biodegradable Through Image Analysis** |
| **Application Name** | **EcoShop** — A Sustainable Circular Economy E-Commerce & Community Platform |
| **Student Name** | **C. Harichselvam** |
| **Registration Number** | `211191101045` |
| **Degree & Branch** | Bachelor of Technology (B.Tech) in Computer Science and Engineering (DS & AI) |
| **Department** | Department of Computer Science and Engineering |
| **Institution** | **Dr. M.G.R. Educational and Research Institute** (Deemed to be University, NAAC `A+` Accredited, ISO 21001:2018 Certified), Periyar E.V.R. High Road, Maduravoyal, Chennai-600095, Tamil Nadu, India |
| **Project Supervision** | **Dr. / Prof. T.V. Ananthan** & **Prof. Rekha** (Project Guides) |
| **Project Coordinator** | **Prof. Jerald** |
| **Head of Department** | **Prof. Dr. S. Geetha** |
| **Project Report** | [`HARICHSELVAM_PROJECT_REPORT-2.docx.pdf`](./HARICHSELVAM_PROJECT_REPORT-2.docx.pdf) |

---

## Author's Research Publication & Related Work

Alongside this Bachelor's degree project, also conducted and published peer-reviewed research in multimodal artificial intelligence and clinical decision support systems:

### **CardioPredict: Multimodal Cardiovascular Disease Assessment**
An automated multimodal diagnostic framework combining tabular clinical indicators (Random Forest on Cleveland & Framingham cohorts), 1D convolutional ECG signal processing (MIT-BIH arrhythmia classification), and 2D computer vision (12-lead ECG printout diagnosis) with decision-level risk fusion.

- **Journal:** *Journal of Emerging Technologies and Innovative Research (JETIR)*
- **Author Tracking ID:** `557335`
- **JETIR Author & Paper Portal:** [https://www.jetir.org/trackauthorhome.php?a_rid=557335](https://www.jetir.org/trackauthorhome.php?a_rid=557335)
- **Research Source Code Repository:** [https://github.com/harichselvamc/CVD_Research_work](https://github.com/harichselvamc/CVD_Research_work)

---

## Problem Statement & Proposed Solution

### **Problem Statement**
Global solid waste generation is projected to increase by **70% by 2050** (World Bank), driven by the traditional linear *"take-make-dispose"* economy. Existing waste management systems suffer from three critical bottlenecks:
1. **Error-Prone Manual Sorting:** Conventional waste segregation relies heavily on manual inspection, leading to high sorting latency and contamination of recyclable streams by non-recyclable waste.
2. **Low Public Awareness:** Citizens frequently lack real-time guidance on whether everyday materials are recyclable or biodegradable, or how items can be creatively reused.
3. **Fragmented Circular Ecosystems:** There is a lack of unified digital platforms that connect automated waste classification with peer-to-peer sustainable commerce and community-led environmental action.

### **Proposed Solution**
**EcoShop** is an AI-powered Circular Economy web platform that automates waste categorization and extends product lifecycles through four integrated modules:
1. **Real-Time CNN Waste Classification:** A custom Convolutional Neural Network (`TensorFlow`/`Keras`) analyzes user-uploaded product images and automatically classifies items as **Recyclable (`recycle`)** or **Biodegradable (`organic`)** with **93% validation accuracy** in `~1.2s`.
2. **Generative AI Upcycling Assistant:** Powered by `Qwen/Qwen2.5-0.5B` and `LangChain`, an interactive AI assistant generates actionable, step-by-step reuse and recycling ideas tailored to user-specified items.
3. **Hybrid Recommendation Marketplace:** A peer-to-peer e-commerce marketplace for sustainable and reusable goods, featuring a hybrid recommendation engine (`0.7 × TF-IDF text similarity + 0.3 × MinMax-scaled numeric similarity`).
4. **Community Sustainability Hub:** A collaborative portal enabling users to organize, discover, and participate in local recycling drives and sustainability events.

---

## Documentation & Quick Links

- [**Project Setup & Developer Guide (`PROJECT_SETUP_README.md`)**](./PROJECT_SETUP_README.md) — Detailed installation instructions, dependencies, folder structure, MongoDB schema, and route documentation.
- [**Full B.Tech Project Report (`HARICHSELVAM_PROJECT_REPORT-2.docx.pdf`)**](./HARICHSELVAM_PROJECT_REPORT-2.docx.pdf) — Complete academic thesis, system design diagrams, UI screenshots, and bibliography.
- [**CVD Research Work Repository**](https://github.com/harichselvamc/CVD_Research_work) — Author's multimodal cardiovascular disease assessment research code.
- [**JETIR Publication Portal (Author ID: 557335)**](https://www.jetir.org/trackauthorhome.php?a_rid=557335) — Published research paper tracking portal.

---
