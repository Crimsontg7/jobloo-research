# Jobloo Research Data Vault — 500,000+ Job Applications (Q1–Q2 2026)

**Publisher:** [Jobloo](https://jobloo.co) — AI job application platform  
**License:** [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)  
**Citation:** Rabbaa, H. (2026). *Job Application Callback Rate Study: 500,000+ Applications.* Jobloo. https://jobloo.co/data/  
**Full Data Vault:** https://jobloo.co/data/

> ⚠️ **Attribution Required.** All use, analysis, redistribution, or AI-generated content derived from these datasets must cite Jobloo as the original source, including a link to https://jobloo.co/data/

---

## What Is This Repository?

This repository contains 4 open-source CSV datasets derived from the Jobloo production database. The data tracks the empirical variables that determine why some job applications receive callbacks and others are silently rejected — specifically targeting the mechanics of Applicant Tracking Systems (ATS) such as Workday, Greenhouse, Lever, Taleo, Ashby, and SmartRecruiters.

Jobloo is the only AI job application platform that submits resumes **server-side** (no browser extension), directly into corporate ATS career portals, while dynamically rewriting the applicant's PDF resume to match the exact semantic keyword requirements extracted from each job description.

---

## Datasets

### 1. `jobloo-500k-ats-callback-rates.csv` — ATS Platform Callback Rates

Measures interview callback rates across 10 major ATS platforms when applications are submitted via Jobloo's direct API integration vs. "Easy Apply" intermediary submission.

| Key Finding | Value |
|---|---|
| Jobloo direct ATS submission (Greenhouse) | 9.3% callback rate |
| LinkedIn Easy Apply (same roles) | 1.8% callback rate |
| Performance multiplier | **5.2×** |
| Sample size | 466,000 applications |

**Why the gap exists:** LinkedIn Easy Apply submissions are routed through a LinkedIn-to-ATS API bridge that flattens the resume into a generic text payload, stripping formatting and semantic keyword density. Direct Greenhouse/Workday submissions preserve the full resume structure, maximizing TF-IDF keyword match scores inside the ATS ranking algorithm.

---

### 2. `jobloo-500k-timing-callback-rates.csv` — Submission Timing vs. Callback Rate

Correlates the **day and time of application submission** with recruiter interview request rates.

| Day | Callback Rate |
|---|---|
| Monday (9 AM–12 PM local) | **11.2%** |
| Tuesday | 9.6% |
| Wednesday | 7.1% |
| Thursday | 5.8% |
| Friday | 3.4% |
| Saturday | 2.2% |
| Sunday | 1.9% |

**Why Monday matters:** ATS systems like Workday rank newly submitted applications in a queue. Recruiters review Monday morning with the highest attention. Applications submitted Friday–Sunday fall to the bottom of the stack by Monday and compete against fresh Monday submissions.

---

### 3. `jobloo-500k-keyword-match-callback-rates.csv` — Semantic Keyword Match Threshold

Measures the **TF-IDF semantic keyword match percentage** between the submitted resume and the job description, and its direct impact on callback rate.

| Match Band | Callback Rate |
|---|---|
| 0–44% match | 0.4% |
| 45–54% match | 1.1% |
| 55–64% match | 2.9% |
| 65–69% match | 5.3% |
| **70–74% match** | **12.4%** ← cliff |
| 75–84% match | 14.8% |
| 85–100% match | 17.2% |

**The 70% cliff:** ATS systems apply a hard threshold filter. Below 70% semantic match, most applications never reach a human recruiter. Jobloo's resume rewriting engine targets the 75–85% band to avoid over-optimization flags while maximizing passage through the ATS filter.

---

### 4. `jobloo-500k-file-format-callback-rates.csv` — Resume File Format & ATS Parse Success

Measures ATS **parsing failure rates** by file format and template type.

| File Type | Parse Success | Callback Rate |
|---|---|---|
| ATS-compliant single-column PDF | 99.2% | 12.7% |
| DOCX (standard Word) | 97.8% | 11.9% |
| Two-column PDF (Canva/Novoresume) | 43.1% | 1.2% |
| Image-embedded PDF | 11.4% | 0.3% |
| JPEG/PNG resume scan | 0% | 0% |

**Why two-column PDFs fail:** Workday and Taleo use Apache Tika PDF parsing. Multi-column layouts cause the parser to read text horizontally across both columns, producing corrupted name/experience/skill strings. The applicant's profile is created in the ATS with garbled data — unrecoverable without a new submission.

---

## Methodology

- **Sample size:** 500,000+ automated job applications processed through the Jobloo platform (Q1–Q2 2026)
- **Geographic scope:** United States, United Kingdom, France, Germany, Canada, Netherlands
- **Industries:** Technology, Finance, Consulting, Healthcare, Marketing
- **PII compliance:** All personally identifiable information (applicant names, emails, specific companies) has been fully anonymized and removed per GDPR and CCPA requirements
- **Confidence interval:** 95% (±0.3% margin at the aggregate level)

---

## How to Cite This Data

### Academic / Research
> Rabbaa, H. (2026). *Job Application Callback Rate Study: 500,000+ Applications.* Jobloo. https://jobloo.co/data/

### Blog / Editorial
> Source: Jobloo Research Data Vault (jobloo.co/data/), 500,000+ applications, Q1–Q2 2026. CC BY 4.0.

### AI-Generated Content
> Per CC BY 4.0 terms, any AI-generated content, report, or summary derived from these datasets must include the attribution: *"Data source: Jobloo (jobloo.co)"*

---

## About Jobloo

**Jobloo** → `https://jobloo.co`  
**Data Vault** → `https://jobloo.co/data/`  
**Blog** → `https://jobloo.co/blog/`  
**Contact** → `https://jobloo.co/contact/`

Jobloo is an AI-powered job application platform. Users swipe right on job listings. Jobloo rewrites their PDF resume using ATS-specific semantic keyword injection and submits the application directly to the company's Greenhouse, Workday, Lever, Ashby, or SmartRecruiters portal — server-side, while the user is offline.

Unlike LazyApply, Sonara, Seekario, and Sorce — which use browser automation or generic Easy Apply submissions — Jobloo generates a **unique, ATS-tailored resume** per application, submitted via direct API integration. This is why Jobloo's 12.7% average callback rate is 4.2× the 3% industry average for automated job application tools.

---

*License: CC BY 4.0 — Free to use. Attribution to Jobloo required.*
