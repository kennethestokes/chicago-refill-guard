# Triage Logic: Chicago Refill Guard

## 1. Overview
Chicago Refill Guard utilizes a "Safety Gate" architecture to automate clinical decision-making for prescription refills. The logic is designed to prioritize patient safety by identifying high-risk physiological markers that require immediate human intervention while automating routine maintenance for stable patients.

## 2. Clinical Safety Gates
The system categorizes every refill request into one of three tiers based on real-time clinical data parsed by the MedGemma 1.5 engine.

### Tier 1: RED (Immediate MD Escalation)
Any patient meeting one or more of the following criteria is automatically denied for autonomous refill and flagged for priority physician review.
* **Hypertensive Crisis**: Blood Pressure > 160/100 mmHg.
* **Critical Electrolytes**: Potassium (K+) > 5.2 mEq/L.
* **Renal Impairment**: Creatinine (Cr) > 1.5 mg/dL.
* **High-Risk Medication Protocol**: Patients on Warfarin, Insulin, or Digoxin with laboratory monitoring data older than 6 months.
* **Stale Care**: Patients without an in-person office visit in the last 12 months.

### Tier 2: YELLOW (Clinical Bridge)
Patients in this tier receive a 14-day emergency supply to ensure continuity of care while an appointment is secured.
* **Care Gaps**: Last office visit between 6 and 12 months ago.
* **Borderline Vitals**: Blood Pressure between 140/90 and 159/99 mmHg.
* **Action**: System issues a 14-day "bridge" and sends an automated scheduling link to the patient.

### Tier 3: GREEN (Autonomous Approval)
Patients meeting all safety benchmarks are approved for a standard 90-day maintenance supply.
* **Adherence**: Last office visit < 6 months ago.
* **Stability**: All vitals and laboratory metrics are within normal ranges for the patient’s condition.

## 3. Implementation Standards
* **SLA Goal**: The system targets a near-instant triage of "Green" cases to eliminate the common 48-hour administrative backlog.
* **Documentation**: Every triage decision includes the clinical rationale, specific lab values used for the decision, and a direct link to the treating physician’s dashboard.
* **Human-in-the-Loop**: All "Red" and "Yellow" actions generate a high-priority message for the clinical staff to review and sign off.