# Hypoxia and Intraoperative Mean Arterial Pressure Analysis

**Author:** Jackson Rapp

**Project:** Final Analysis Report

## Study Overview

This project examines the relationship between hypoxia (specifically, minimum nocturnal SaO2) and cardiovascular morbidity among adult patients with obstructive sleep apnea (OSA). The study builds upon prior work by shifting the primary exposure to minimum nocturnal SaO2 to clarify its predictive relationship with intraoperative time-weighted average of mean arterial pressure (TWA MAP) and the intraoperative administration of vasopressors.

## Dataset

The analysis utilizes a retrospective Cleveland Clinic dataset consisting of 281 adult patients with OSA who underwent laparoscopic bariatric procedures.

* **Data File:** `hypoxia.Rdata`

* **Primary Exposure:** Minimum Nocturnal SaO2 (%)

* **Primary Outcome:** Intraoperative TWA MAP (mmHg)

* **Secondary Outcome:** Intraoperative Vasopressor Use (Binary)

* **Confounders Included:** Age, Sex, Race, BMI, Smoking Status, Diabetes Diagnosis, Hypertension, CAD, Preoperative Antihypertensive Medications, CPAP use, and Type of Surgery.

*Note: Missing data was handled via list-wise deletion, yielding a complete dataset of 281 observations.*

## Statistical Methods

The study is divided into two primary aims:

1. **Primary Analysis (Aim 1):** A multivariable linear regression model was built to quantify the association between minimum nocturnal SaO2 and intraoperative TWA MAP, adjusting for pre-specified clinical confounders. Rigorous diagnostic tests were performed, including Component+Residual (CR) plots for linearity, Q-Q plots for normality, residuals vs. fitted values for homoscedasticity, Generalized Variance Inflation Factors (GVIF) for collinearity, and Cook's Distance for influential observations. A sensitivity analysis was also conducted.

2. **Secondary Analysis (Aim 2):** A multivariable logistic regression model was constructed to model the relationship between minimum nocturnal SaO2 and the intraoperative administration of vasopressors. This included testing for potential effect modification (interaction) by a patient's diabetes status.

All primary statistical significance was evaluated against a Bonferroni-corrected threshold of $\alpha = 0.025$.

## Results and Discussion

* **Aim 1 Results:** A statistically significant association was found between minimum nocturnal SaO2 and intraoperative TWA MAP ($p = 0.019$). Holding confounders constant, every 1% absolute increase in minimum nocturnal SaO2 was associated with a 0.16 mmHg increase in TWA MAP. This finding diverges from prior literature (Turan et al.) due to the use of a comprehensive confounder model rather than automated backward selection, which likely prevented omitted variable bias.

* **Aim 2 Results:** The association between minimum nocturnal SaO2 and vasopressor administration was not statistically significant ($p = 0.494$). While an interaction trend between severe nocturnal hypoxia and diabetes was observed, it did not meet the strict statistical significance criteria for effect modification ($p = 0.040$).

## How to Run the Code

To reproduce this analysis and generate the final Word document report, follow these steps:

1. **Prerequisites:** Ensure you have R and RStudio installed on your machine.

2. **Install Required Packages:** You will need the following R libraries installed:

   * `tidyverse`

   * `janitor`

   * `patchwork`

   * `car`

   * `gtsummary`

   * `flextable`

3. **File Setup:** Ensure the following three files are located in the exact same working directory (folder):

   * `hypoxia_follow_up.rmd` (The main analysis script)

   * `hypoxia.Rdata` (The dataset)

   * `reference_style.docx` (The custom Word formatting template)

4. **Execution:**

   * Open `hypoxia_follow_up.rmd` in RStudio.

   * Click the **"Knit"** button (or use the shortcut `Ctrl+Shift+K` / `Cmd+Shift+K`) to compile the document to Word.

   * The output will automatically apply the styles defined in `reference_style.docx` and generate the final Word document containing all tables, plots, and narrative text.