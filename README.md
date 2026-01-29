# Chicago Refill Guard 🏥
### Safety-First Grounded Triage for Urban Medication Deserts

**Chicago Refill Guard** is a clinical triage framework powered by **MedGemma 1.5** and **Google Cloud Vertex AI**. It is architected to address the 20.7-year life expectancy gap between Chicago's Loop and West Garfield Park by automating routine medication refills, allowing clinicians to focus on high-risk, life-saving interventions.

---

## 📊 The Strategic Problem
In Chicago, geography is destiny. Administrative bottlenecks in underserved "medication deserts" force high-risk patients into the same manual queues as routine cases. This delay creates care gaps that can prove fatal. This project uses AI as a **force multiplier** to reclaim clinical time and prioritize patient safety.

## 🛠 Technical Architecture
The system utilizes a **Grounded Retrieval-Augmented Generation (RAG)** workflow to ensure zero hallucinations and absolute clinical reproducibility.

* **Model:** MedGemma 1.5 (4B-it)
* **Grounding:** Vertex AI Search (Grounded in Chicago Clinical Audit Data)
* **Infrastructure:** Google Cloud Platform (GCP)
* **Logic:** Deterministic Multi-Gate Safety Protocol (**Temperature: 0.0**)

## 🚦 Safety Gate Logic
The framework categorizes every refill request into three strict, deterministic gates:
1. **🔴 RED (High Risk):** Immediate block and MD escalation for critical lab values (e.g., $K^+ > 5.2$ mmol/L) or care gaps > 12 months.
2. **🟡 YELLOW (Moderate Risk):** Automated 14-day bridge supply for patients with care gaps between 6–12 months.
3. **🟢 GREEN (Low Risk):** Automated 90-day approval for stable profiles with clinical visits within < 6 months.

## 📈 Impact & Validation
During stress-testing against a 25-patient clinical audit:
* **Automation:** **68%** of the routine backlog safely cleared for automated approval.
* **Safety:** **100% catch rate** for critical hyperkalemia and high-risk care gaps.
* **Efficiency:** Reclaims **~20 hours** of clinical staff time weekly per 500 refills.

## 📂 Repository Structure
* `clinical_triage_config.json`: The core model configuration, temperature settings, and safety instructions.
* `audit_results.md`: Documentation of the 100% safety catch rate during pilot testing.
* `visuals/`: Chicago mortality gap mapping and system architecture diagrams.

---
**Lead Strategist:** Kenneth Stokes  
**Project Status:** Developed for the MedGemma Impact Challenge (2026)
