# Class Notes: WOA7017 Security Risk Analysis and Evaluation
## Week 9 Summary
**Lecturer:** Prof. Ts. Dr. Omar Zakaria
**Date:** 22 May 2025
**Time:** 1800H
---
### **Introduction to Individual Assignment**
*   The lecturer introduced an **individual assignment** focused on Security Risk Analysis and Evaluation.
*   **Purpose:** To provide practical exposure and allow students to apply course concepts.
*   The assignment involves using a provided table to document the risk assessment process.

---
### **Assignment Task: Asset Risk Assessment and Justification**
*   Students are required to provide **two examples of assets**.
*   For each asset, students must conduct a risk assessment using the supplied table format.
*   The core task is to **justify** whether each asset (or its associated controls) should be:
    *   **Improved:** Enhance existing methods or controls for the same asset.
    *   **Maintained:** Continue with the current methods or controls without change.
    *   **Upgraded:** Replace the asset or controls with a newer version or a different solution (e.g., software version 1 to version 2, or changing a product entirely).
*   The justification needs to be clear and convincing, as if presenting to top management.

---
### **Structure of the Risk Assessment Table**
The assignment uses a table (provided as a file, likely `Individual Assignment WOA7017.docx` or similar) structured into four main sections. This table serves as a **summary** for management.

#### **1. Risk Identification**
*   **Label/ID:** A unique identifier for the risk (e.g., `SW-07`). Students can create their own.
*   **Asset Name & Description:**
    *   Clear description of the asset being assessed.
    *   Example given: "ABC Antivirus installed at server, PC, and user laptops." (Lecturer advised against using real brand names like "Sophos" in the assignment to avoid issues, suggesting generic names like "ABC Antivirus").
*   **Quantity:** Number of assets. For software with site licenses, this is typically `1`.
*   **Asset Owner:** The department or entity that owns the asset and is primarily affected by its risks.
    *   Example: Human Resource Department (if the assessment is sampling assets in HR).
*   **Asset Custodian:** The department or entity responsible for maintaining, updating, and securing the asset.
    *   Example: IT Department.
    *   Note: If sampling in the IT department, both owner and custodian could be IT.
*   **Location:** The physical or logical location of the asset or where the risk is observed.
    *   Example: "Data Center Human Resource," or a specific user's workstation like "Abu's laptop at Human Resource." This helps pinpoint where a vulnerability (e.g., inability to detect malware) occurs.
*   **Threat Description:** A brief statement of the most significant threat(s) to the asset.
    *   Example: "Malware and software malfunction."
*   **Descriptive Description (Vulnerability/Complaint):** Details about the specific problem or vulnerability.
    *   Example: "Lack of control against malware (e.g., current antivirus cannot scan/detect the latest viruses)," "Lack of adequate maintenance." This section should reflect observed issues or complaints.

#### **2. Risk Analysis**
*   **CIA Rating (Confidentiality, Integrity, Availability):**
    *   Assessed on a scale of **1 (Low), 2 (Medium), 3 (High)** for each component.
    *   Example (Antivirus issue): C=1, I=1, **A=2** (Availability is higher because if a virus attacks files, information cannot be retrieved).
    *   Example (Electricity): C=1, I=1, **A=3**.
    *   Example (Money in a bank): **C=3, I=3**, A=1 or 2.
*   **Risk Impact:** The overall potential negative consequence if the risk materializes.
    *   Rated on a scale (e.g., 1-Low, 2-Medium, 3-High). Example given: `2` (Medium) for the antivirus.
*   **Likelihood (Lollywood in transcript, likely a typo for Likelihood):** The probability of the threat occurring.
    *   Rated on a scale (e.g., 1-Low, 2-Medium, 3-High). Example given: `3` (High) for a new, undetectable virus affecting outdated antivirus software.
*   **Gross Risk:** The risk level **before** any controls are considered (often a combination of impact and likelihood).
    *   Example: `High`.
*   **Risk Owner:** The department or individual responsible for managing this specific risk.
    *   Example: IT Department (for the antivirus risk). This can be the same as Asset Custodian or differ based on organizational structure.

#### **3. Risk Evaluation**
*   **Existing Control:** Describe the current measures in place to mitigate the risk.
    *   Example: "Scheduled maintenance by third party" (which was identified as a potential issue itself).
*   **Control Effectiveness for Existing Control:** How effective the current controls are.
    *   Rated on a scale (e.g., 1-Low, 2-Medium, 3-High).
    *   Example: `1` (Low) if the existing control (e.g., third-party maintenance) is not working well. A high rating (3) would mean the existing control is very effective.
*   **Net Risk:** The risk level **after** considering the effectiveness of existing controls.
    *   Example: `Medium`.
*   **Risk Position:** The organization's intended response to the net risk.
    *   Options include: **Reduce, Maintain, Avoid, Transfer**.
    *   Example: `Reduce` (if the goal is to lower the risk through new/improved controls). If "Maintain," it means no change.

#### **4. Risk Treatment**
*   **Treatment Plan / Recommendation:** The specific action(s) proposed to address the risk. This is where the decision to **improve, maintain, or upgrade** is detailed.
    *   Example: "Procurement of new antivirus software," "Implement biometrics," "Improve employee termination procedures."
*   **Start Date / End Date:** Projected timeline for implementing the treatment plan. (Example dates given were illustrative).
*   **Risk Treatment Owner:** The department or individual responsible for implementing the treatment plan.
    *   Example: IT Department.
*   **Evidence:** How the successful implementation of the treatment plan will be verified.
    *   Example: "Produce the report for the new installment."
*   **Control Effectiveness for Treatment Plan:** The **expected** effectiveness of the proposed new/improved control.
    *   Rated on a scale (e.g., 1-Low, 2-Medium, 3-High).
    *   Example: `2` (Medium), aiming for an improvement over the existing control's effectiveness.
*   **Residual Risk:** The risk level expected to remain **after** the treatment plan is successfully implemented.
    *   Example: `Low`.
    *   **Important:** Residual risk should ideally be lower than net risk but **never zero**.

---
### **Key Considerations for the Assignment**
*   **Justification is Crucial:** The primary goal is to convince "the boss" (the lecturer) of the need for the proposed action (improve, maintain, or upgrade) using the structured summary in the table.
*   **Practical Examples:** Students need to choose **two distinct examples** of assets/scenarios.
    *   Example 1 (from lecture): An existing antivirus ("ABC Antivirus") is ineffective (complaints, cannot detect new viruses). The proposal might be to **upgrade** to a new antivirus product.
    *   Example 2 (suggested): Flawed employee termination process leading to security risks. The proposal might be to **improve** the procedures.
    *   Example 3 (suggested): Using simple passwords for system access poses an impersonation risk. The proposal might be to **upgrade** to biometric authentication.
*   **Cost Implication:** Proposed changes (especially upgrades) often have cost implications ("Money, money, money"). A strong justification helps secure approval and funding.
*   **Focus on the Summary Table:** The assignment requires filling out the provided table for two examples. While a detailed write-up might be part of a real-world scenario, this assignment emphasizes the **summary for management decision-making**. The boss wants to see a short, sharp summary.

---
### **Assignments & Deadlines**
*   **Individual Assignment:**
    *   Complete the risk assessment table for **two asset examples**.
    *   Focus on justifying the decision to **improve, maintain, or upgrade**.
*   **Deadline:** Week 13, by **17:59** (5:59 PM), before the class starts.

---
### **Announcements**
*   The lecturer mentioned a potential absence for approximately 2-3 weeks in September for a personal trip ("balik kampung").

---
### **Key Takeaways from this Lecture**
*   The individual assignment is designed as a practical exercise in conducting and presenting a security risk analysis and evaluation.
*   A clear understanding of the four stages (Risk Identification, Risk Analysis, Risk Evaluation, and Risk Treatment) and their components is essential.
*   The structured table format serves as a concise and effective way to communicate risks and proposed treatments to management for decision-making.
*   The core of the assignment lies in the ability to **justify** recommendations to improve, maintain, or upgrade assets/controls based on the risk assessment.