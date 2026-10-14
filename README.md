# Faith Specialist Hospital: Healthcare Analytics Report

> An analysis of patient demographics, discharge against medical advice (DAMA), chronic illness, lifestyle factors, and doctor performance, with recommendations for hospital management.

**Prepared by:** [Your Name], Data Analyst
**Tools:** [e.g., Python (pandas, matplotlib, seaborn)]
**Dataset:** 1,478 patient cases

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Background and Problem Statement](#2-background-and-problem-statement)
3. [Objectives](#3-objectives)
4. [Data Overview](#4-data-overview)
5. [Findings](#5-findings)
   - [5.1 Patient Demographics and Outcomes](#51-patient-demographics-and-outcomes)
   - [5.2 Discharge Against Medical Advice (DAMA)](#52-discharge-against-medical-advice-dama)
   - [5.3 Chronic Illnesses: Prevalence and Impact](#53-chronic-illnesses-prevalence-and-impact)
   - [5.4 Lifestyle Factors](#54-lifestyle-factors)
   - [5.5 Doctor Performance](#55-doctor-performance)
6. [Recommendations](#6-recommendations)
7. [Data Notes and Limitations](#7-data-notes-and-limitations)

---

## 1. Executive Summary

Of the 1,478 cases analysed, **276 (18.67%) ended in DAMA** and **290 patients died (about 19.6%)**. The main findings are:

- **Money is the main driver of DAMA.** Financial constraint (81.16%) and financial incapability (6.88%) together account for **88.04%** of DAMA cases.
- **DAMA clusters in specific groups.** Young adults (18-29) have the highest DAMA rate (26.56%). Patients with only SSCE or FSLC education make up about 86% of DAMA cases. Traders are the largest occupation group (31.52%).
- **CKD and stroke stand out** as the illnesses with the most DAMA cases.
- **Stroke (23.48%) and CKD (21.92%) are the most prevalent chronic illnesses.** Cancer is the deadliest, with a **53.12%** mortality rate among cancer patients, followed by diabetes at **30.72%**. Overall mortality is about 19%.
- **Mortality is concentrated in older age groups.** Older adults (30.45%) and middle-aged adults (28.03%) account for most deaths. Gender makes little difference to stay length or mortality.
- **Lifestyle factors** were modest in effect. NSAID use is linked to a longer average stay (15.63 vs 12.40 days).
- **Doctor outcomes vary widely.** Death rates and DAMA rates differ a lot between doctors, even within the same specialization.

---

## 2. Background and Problem Statement

Faith Specialist Hospital serves a diverse population and has accumulated a large amount of patient data, from demographics to admission records and health outcomes. Management has flagged three concerns:

- An increasing number of patients **discharged against medical advice**
- A rising trend in **chronic diseases**
- A concerning **mortality rate** among certain patient groups

## 3. Objectives

| #   | Objective                                                                    |
| --- | ---------------------------------------------------------------------------- |
| 1   | Analyse patient demographics in relation to hospital outcomes                |
| 2   | Identify common reasons for discharge against medical advice (DAMA)          |
| 3   | Examine the prevalence and impact of chronic illnesses                       |
| 4   | Assess the impact of lifestyle factors on hospital outcomes                  |
| 5   | Evaluate doctor performance by specialization and workload                   |
| 6   | Provide data-driven insights to improve hospital management and patient care |

## 4. Data Overview

| Item           | Detail                                                                                                                                                                                                                                     |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Total cases    | 1,478                                                                                                                                                                                                                                      |
| DAMA cases     | 276 (18.67%)                                                                                                                                                                                                                               |
| Non-DAMA cases | 1,202 (81.33%)                                                                                                                                                                                                                             |
| Deaths         | 290 (149 male, 141 female)                                                                                                                                                                                                                 |
| Key fields     | Age group, sex, education level, occupation, admission duration group, doctor and specialization, chronic illness flags (CKD, DM, stroke, PUD, cancer), lifestyle flags (alcohol, tobacco, NSAID use), outcome (dead), DAMA and its reason |

---

## 5. Findings

### 5.1 Patient Demographics and Outcomes

#### DAMA by age group

| Age group          | Range | Non-DAMA | DAMA | Total | DAMA rate (%) |
| ------------------ | ----- | -------- | ---- | ----- | ------------- |
| Young adults       | 18-29 | 94       | 34   | 128   | **26.56**     |
| Middle-aged adults | 45-59 | 326      | 82   | 408   | 20.10         |
| Adults             | 30-44 | 265      | 62   | 327   | 18.96         |
| Older adults       | 60-74 | 384      | 80   | 464   | 17.24         |
| Elderly adults     | 75+   | 128      | 16   | 144   | 11.11         |
| Under 18           | 0-17  | 2        | 0    | 2     | 0.00          |

![DAMA rate by age group (bar chart)](/images/dama_rate_by_age_group.png)

**Insight:** Young adults leave against medical advice most often, and the rate falls steadily with age. The Under 18 group has only 2 patients, so its rate is not meaningful.

#### Deaths by age group and sex

| Age group          | Deaths | Share of deaths (%) |
| ------------------ | ------ | ------------------- |
| Older adults       | 88     | 30.45               |
| Middle-aged adults | 81     | 28.03               |
| Adults             | 58     | 20.07               |
| Elderly adults     | 46     | 15.92               |
| Young adults       | 16     | 5.54                |

![Share of deaths by age group](/images/deaths_by_age_group.png)

**Insight:** Older adults and middle-aged adults account for over half of all deaths. By sex, deaths are nearly equal (149 male vs 141 female), so sex does not appear to drive mortality.

#### Admission duration by age group and sex

| Stay group     | Adults | Elderly | Middle-aged | Older | Under 18 | Young |
| -------------- | ------ | ------- | ----------- | ----- | -------- | ----- |
| Extended stay  | 98     | 53      | 125         | 134   | -        | 39    |
| Long stay      | 70     | 22      | 98          | 136   | 2        | 26    |
| Moderate stay  | 75     | 40      | 89          | 110   | -        | 25    |
| Short stay     | 61     | 21      | 68          | 56    | -        | 22    |
| Very long stay | 23     | 8       | 28          | 27    | -        | 16    |

![Admission duration group by age group](/images/admission_duration_by_age_group.png)

**Insight:** Middle-aged and Older adults spend longer in hospital, and stay length is almost identical across the sexes (for example, Extended stay: 216 female vs 235 male).

![Admission duration group by sex](/images/admission_duration_by_sex.png)

---

### 5.2 Discharge Against Medical Advice (DAMA)

#### Overall DAMA rate

| DAMA | Count | %     |
| ---- | ----- | ----- |
| No   | 1,202 | 81.33 |
| Yes  | 276   | 18.67 |

![DAMA vs non-DAMA](/images/dama_vs_non_dama.png)

#### Reasons for DAMA

| Reason                 | Count | %     |
| ---------------------- | ----- | ----- |
| Financial constraint   | 224   | 81.16 |
| Financial incapability | 19    | 6.88  |
| No improvement         | 19    | 6.88  |
| Doctors' strike        | 14    | 5.07  |

![Reasons for DAMA](/images/reasons_for_dama.png)

**Insight:** **88.04%** of DAMA cases are financial. Only 19 cases (6.88%) left because of no improvement, and 14 (5.07%) because of a doctors' strike.

**"No improvement" cases by doctor:** Dr Badmus (6), Dr Ayeni (4), Dr Ekwe (4), Dr Anyanwu (2), Dr Oikeh (1), Dr Abah (1), Dr Dase (1). Dr Badmus accounts for 6 of the 19.

!["No improvement" DAMA cases by doctor](/images/no_improvement_by_doctor.png)

#### Who leaves against medical advice

**By education level** (among DAMA cases with a recorded level, n = 274):

| Education     | Count | %     |
| ------------- | ----- | ----- |
| SSCE          | 119   | 43.43 |
| FSLC          | 116   | 42.34 |
| MSc           | 23    | 8.39  |
| Undergraduate | 13    | 4.74  |
| BSc           | 2     | 0.73  |
| HND           | 1     | 0.36  |

![DAMA cases by education level](/images/dama_by_education.png)

**Insight:** Patients with only SSCE or FSLC make up 85.77% of DAMA cases, while patients with higher qualifications contribute far fewer.

**By occupation:**

| Occupation | Count | %     |
| ---------- | ----- | ----- |
| Trading    | 87    | 31.52 |
| Farming    | 30    | 10.87 |
| Retiree    | 23    | 8.33  |
| Student    | 22    | 7.97  |
| Dependant  | 17    | 6.16  |

![DAMA cases by occupation](/images/dama_by_occupation.png)

**Insight:** Traders and farmers, who typically have irregular income, are the most affected occupations.

**By length of stay:**

| Stay group     | Count | %     |
| -------------- | ----- | ----- |
| Extended stay  | 85    | 30.80 |
| Moderate stay  | 72    | 26.09 |
| Long stay      | 55    | 19.93 |
| Short stay     | 52    | 18.84 |
| Very long stay | 12    | 4.35  |

![DAMA cases by admission duration group](/images/dama_by_admission_duration.png)

**Insight:** Most DAMA cases (56.89%) come from Extended and Moderate stays, roughly 4 to 15 days into admission. This is the point where bills build up and patients drop out.

**By illness:** CKD and stroke stood out with more DAMA cases than any other illness.

**By specialization:**

| Specialization     | DAMA cases | %     |
| ------------------ | ---------- | ----- |
| Emergency medicine | 82         | 29.71 |
| General surgery    | 54         | 19.57 |
| Nephrology         | 45         | 16.30 |
| Cardiology         | 40         | 14.49 |
| Anesthesiology     | 29         | 10.51 |
| Dermatology        | 15         | 5.43  |
| Orthopedics        | 11         | 3.99  |

![DAMA cases by specialization](/images/dama_by_specialization.png)

**Insight:** Emergency medicine contributes the most DAMA cases (29.71%), followed by general surgery and nephrology.

---

### 5.3 Chronic Illnesses: Prevalence and Impact

#### Prevalence

| Illness       | Patients | Prevalence (%) |
| ------------- | -------- | -------------- |
| Stroke        | 347      | 23.48          |
| CKD           | 324      | 21.92          |
| PUD           | 168      | 11.37          |
| Diabetes (DM) | 166      | 11.23          |
| Cancer        | 32       | 2.17           |

![Prevalence of chronic illnesses](/images/chronic_illness_prevalence.png)

#### Mortality: patients with vs without each illness

| Illness  | Death rate with illness (%) | Death rate without illness (%) |
| -------- | --------------------------- | ------------------------------ |
| Cancer   | **53.12** (17 of 32)        | 18.88                          |
| Diabetes | **30.72** (51 of 166)       | 18.22                          |
| CKD      | 22.84 (74 of 324)           | 18.72                          |
| Stroke   | 21.90 (76 of 347)           | 18.92                          |
| PUD      | 11.90 (20 of 168)           | 20.61                          |

![patterns](/images/mortality_by_illness.png)

**Insight:** Cancer more than doubles the death rate, and diabetes raises it by about 12 percentage points. CKD and stroke raise it slightly. PUD patients actually had a lower death rate than patients without PUD.

#### Which age groups carry each illness

| Illness  | Largest age group                  | Share (%) | Second largest     | Share (%) |
| -------- | ---------------------------------- | --------- | ------------------ | --------- |
| CKD      | Middle-aged adults                 | 33.44     | Older adults       | 27.55     |
| Stroke   | Middle-aged adults                 | 41.45     | Older adults       | 32.75     |
| PUD      | Older adults                       | 35.12     | Adults             | 25.00     |
| Diabetes | Middle-aged and older adults (tie) | 31.33     | Adults             | 19.28     |
| Cancer   | Older adults                       | 37.50     | Middle-aged adults | 25.00     |

![Age-group breakdown for each chronic illness](/images/age_group_by_illness.png)

**Insight:** Chronic illness is concentrated in middle-aged and older adults, so this group should be the focus of screening and management programmes.

---

### 5.4 Lifestyle Factors

#### Prevalence

| Factor          | Patients | Prevalence (%) |
| --------------- | -------- | -------------- |
| NSAID use       | 208      | 14.07          |
| Alcohol history | 143      | 9.68           |
| Tobacco history | 49       | 3.32           |

![Lifestyle factor prevalence](/images/lifestyle_prevalence.png)

<!-- #### Admission duration (days)

| Factor    | Without: median / mean | With: median / mean |
| --------- | ---------------------- | ------------------- |
| Alcohol   | 10.0 / 12.91           | 11.0 / 12.26        |
| Tobacco   | 10.0 / 12.82           | 11.0 / 13.82        |
| NSAID use | 10.0 / 12.40           | **11.5 / 15.63**    |

> 📊 **[CHART PLACEHOLDER 17: Admission duration with vs without each lifestyle factor (box plot)]**

**Insight:** NSAID use shows the clearest effect, adding about 3 days to the average stay. Alcohol and tobacco make little difference. -->

#### Mortality

| Factor    | Death rate without (%) | Death rate with (%) |
| --------- | ---------------------- | ------------------- |
| Alcohol   | 20.15                  | 14.69               |
| Tobacco   | 19.73                  | 16.33               |
| NSAID use | 20.16                  | 16.35               |

![Death rate with vs without each lifestyle factor](/images/death_rate_by_lifestyle.png)

**Insight:** Patients with a recorded lifestyle risk factor did not have higher death rates in this data. See the limitations section before drawing conclusions from this.

---

### 5.5 Doctor Performance

#### Highest DAMA rates (top 10)

| Doctor      | Specialization     | Patients | DAMA cases | DAMA rate (%) |
| ----------- | ------------------ | -------- | ---------- | ------------- |
| Dr Salu     | Nephrology         | 15       | 6          | 40.00         |
| Dr Oikeh    | Anesthesiology     | 27       | 10         | 37.04         |
| Dr Oluwole  | Anesthesiology     | 21       | 7          | 33.33         |
| Dr Ndubuisi | General surgery    | 18       | 6          | 33.33         |
| Dr Ekwe     | General surgery    | 43       | 13         | 30.23         |
| Dr Daniel   | General surgery    | 47       | 14         | 29.79         |
| Dr Badmus   | General surgery    | 52       | 15         | 28.85         |
| Dr Ogedegbe | Emergency medicine | 174      | 49         | 28.16         |
| Dr Ajakaiye | Orthopedics        | 18       | 5          | 27.78         |
| Dr Ajani    | Orthopedics        | 19       | 5          | 26.32         |

![top 10 doctors by DAMA rate](/images/top_doctors_dama_rate.png)

#### Lowest DAMA rates (bottom 10)

| Doctor      | Specialization  | Patients | DAMA cases | DAMA rate (%) |
| ----------- | --------------- | -------- | ---------- | ------------- |
| Dr Adenuga  | Orthopedics     | 8        | 0          | 0.00          |
| Dr Akinola  | Orthopedics     | 13       | 0          | 0.00          |
| Dr Anosike  | Nephrology      | 1        | 0          | 0.00          |
| Dr Alade    | Nephrology      | 24       | 1          | 4.17          |
| Dr Lash     | Dermatology     | 68       | 3          | 4.41          |
| Dr Akeju    | Orthopedics     | 16       | 1          | 6.25          |
| Dr Amadasun | Nephrology      | 15       | 1          | 6.67          |
| Dr Mahmoud  | General surgery | 15       | 1          | 6.67          |
| Dr Davies   | Nephrology      | 42       | 3          | 7.14          |
| Dr Kenneth  | Dermatology     | 32       | 3          | 9.38          |

![Bottom 10 doctors by DAMA rate](/images/bottom_doctors_dama_rate.png)

**Insight:** Rates range from 0% to 40%. General surgery and anesthesiology doctors dominate the high-DAMA list, while dermatology and several nephrology and orthopedics doctors keep DAMA low. Many of these doctors have small caseloads, so their rates are less stable.

#### Workload, mortality and DAMA (busiest doctors)

| Doctor      | Specialization     | Admissions | Median stay (days) | Death rate (%) | DAMA rate (%) |
| ----------- | ------------------ | ---------- | ------------------ | -------------- | ------------- |
| Dr Ogbu     | Emergency medicine | 210        | 6.0                | 44.29          | 15.71         |
| Dr Ogedegbe | Emergency medicine | 174        | 8.0                | 16.09          | 28.16         |
| Dr Abah     | Cardiology         | 143        | 11.0               | 18.18          | 13.99         |
| Dr Adedapo  | Cardiology         | 101        | 12.0               | 12.87          | 19.80         |
| Dr Solanke  | Nephrology         | 89         | 11.0               | 24.72          | 13.48         |
| Dr Lash     | Dermatology        | 68         | 10.0               | 26.47          | 4.41          |
| Dr Badmus   | General surgery    | 52         | 9.5                | 26.92          | 28.85         |

**Insights:**

- Emergency medicine carries the heaviest workload. Dr Ogbu (210) and Dr Ogedegbe (174) are the busiest doctors in the hospital.
- Dr Ogbu has the highest death rate among high-volume doctors (44.29%), which fits the emergency setting but should be reviewed alongside case severity.
- Some low-volume doctors show extreme death rates, for example Dr Mahmoud (80.00% of 15 admissions) and Dr Alade (37.50% of 24).
- Several doctors have very low death rates (Dr Daniel 2.13%, Dr Ekwe 2.33%, Dr Oikeh 3.70%) but high DAMA rates, suggesting patients may be leaving rather than dying in their care.

---

## 6. Recommendations

| #   | Area                      | Recommendation                                                                                                                                             | Evidence                                                                                           |
| --- | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| 1   | DAMA: cost                | Introduce financial counselling, instalment payment plans, and early billing estimates, and help patients enrol in health insurance schemes                | 88.04% of DAMA cases are financial                                                                 |
| 2   | DAMA: timing              | Run cost and care-plan reviews with patients at about day 4 of admission, before the DAMA peak                                                             | 56.89% of DAMA cases occur in Extended and Moderate stays                                          |
| 3   | DAMA: target groups       | Target outreach and discharge counselling at young adults, traders, farmers, and patients with lower education, using simple, plain-language communication | Young adults have a 26.56% DAMA rate; SSCE and FSLC patients make up 85.77% of DAMA cases          |
| 4   | DAMA: high-cost illnesses | Create cost-support pathways for CKD and stroke patients, such as dialysis and rehabilitation packages                                                     | CKD and stroke lead DAMA cases by illness                                                          |
| 5   | DAMA: service continuity  | Prepare contingency staffing plans for strikes and review patient communication in "no improvement" cases                                                  | Strikes caused 14 DAMA cases; 19 left for no improvement                                           |
| 6   | Chronic disease           | Set up screening and long-term management programmes for stroke, CKD and diabetes, focused on middle-aged and older adults                                 | Stroke (23.48%) and CKD (21.92%) are most prevalent; middle-aged and older adults carry most cases |
| 7   | High-mortality conditions | Review care pathways and early referral for cancer and diabetes patients                                                                                   | Death rates of 53.12% (cancer) and 30.72% (diabetes) vs about 18-19% for patients without them     |
| 8   | Lifestyle                 | Add medication review and NSAID stewardship at admission to reduce avoidable longer stays                                                                  | NSAID users stay about 3 days longer on average                                                    |
| 9   | Doctor performance        | Review high-DAMA and high-mortality doctors with case-mix adjustment, and share practices from low-DAMA doctors                                            | DAMA ranges 0% to 40% and death rate 0% to 80% across doctors                                      |
| 10  | Workload                  | Monitor emergency medicine workload and consider adding capacity                                                                                           | Two emergency doctors handle 384 admissions between them                                           |

---

## 7. Data Notes and Limitations

- **The dataset has no admission dates, so the rising DAMA and chronic disease trends reported by management could not be verified.**
- **Share of DAMA cases is not the same as DAMA rate.** The education, occupation, specialization and stay-length tables show each group's share of DAMA cases, which also reflects how large each group is. Rates per group would give a fairer comparison.
- **Education data covers 274 of 276 DAMA cases**, so 2 cases are missing.
- **Small samples:** Under 18 (n = 2), cancer (n = 32), tobacco history (n = 49), and many individual doctors have very few cases, so their rates can swing sharply.
- **Lifestyle and mortality results are counterintuitive** (lifestyle risk factors linked to lower death rates). This is likely due to confounding, under-recording of lifestyle history, or age differences, and should not be read as these factors being protective.
- **Age groups for chronic illness** show each group's share of that illness' cases, which is influenced by group size.
- **Stay length by age:** counts are highest for middle-aged adults partly because that group is large. As a share of its group, the elderly stand out most for Extended stays (about 37% vs 29-31% for other groups).
- **Mortality is not adjusted** for case severity or diagnosis mix, so doctor-level death rates should be interpreted with care.
- **Association only:** these results show relationships, not causes.
