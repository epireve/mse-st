# WOA7107: Introduction to Security Risk Analysis and Evaluation

**Course Overview:**

* **Focus:** Understanding the "why," not memorization.
* **Assessment:**
    * 2 Quizzes (Weeks 4 & 5, tentatively)
    * 1 Individual Assignment
    * 1 Group Assignment
    * Open-book final exam (Week 14, physical, lecture notes allowed).
* **Delivery:** First 3 classes online, remainder physical (contact faculty if physical attendance is problematic).


**Part 1: Foundations of Security Risk Management**

### Chapter 1: Introduction to Security Risk Analysis and Evaluation

#### 1.1 Understanding Security Risk

This chapter introduces the fundamental concepts of security risk management, emphasizing the importance of risk analysis and evaluation in protecting organizational assets. We'll explore the role of the Information Security Manager, various approaches to identifying and prioritizing security initiatives, and the distinction between accidents and incidents.  Finally, we'll examine the different types of assets that require protection.

#### 1.2 What is Security Risk Management?

Security risk management is the ongoing process of identifying, assessing, and mitigating potential threats and vulnerabilities that could harm an organization's assets.  It's a cyclical process that involves continuously evaluating the effectiveness of security controls and adapting to the changing threat landscape.  The goal is not to eliminate all risks, which is often impossible, but to reduce them to an acceptable level based on the organization's business objectives and risk tolerance.

#### 1.3 The Importance of Risk Analysis and Evaluation

Risk analysis and evaluation are core components of security risk management. They provide a structured approach to:

* **Identify Assets:** Determine what needs protection (e.g., data, systems, personnel, reputation).
* **Identify Threats:** Understand the potential dangers (e.g., malware, natural disasters, human error).
* **Identify Vulnerabilities:** Recognize weaknesses that threats could exploit.
* **Assess Risks:**  Estimate the likelihood and potential impact of threats exploiting vulnerabilities.
* **Prioritize Risks:**  Focus on the most significant risks.
* **Select Cost-Effective Controls:**  Choose security measures that provide the best balance of protection and cost.
* **Evaluate Control Effectiveness:** Ensure that controls continue to be effective over time.

Without thorough risk analysis and evaluation, organizations may overspend on unnecessary controls or, even worse, leave themselves vulnerable to significant threats.

#### 1.4 The Role of the Information Security Manager

The Information Security Manager plays a crucial role in leading and coordinating security risk management efforts.  Their responsibilities are often guided by the CIA Triad and the AAA framework:

* **CIA Triad:**
    * **Confidentiality:** Protecting sensitive information from unauthorized disclosure.
    * **Integrity:** Ensuring the accuracy and completeness of data.
    * **Availability:**  Guaranteeing reliable access to information and systems.
* **AAA Framework:**
    * **Authentication:** Verifying the identity of users and systems.
    * **Authorization:**  Granting appropriate access privileges.
    * **Accountability:** Tracking and recording user actions.

The Information Security Manager also plays a key role in developing and enforcing security policies, ensuring business continuity, planning incident and disaster response, and prioritizing security initiatives.


#### 1.5 Approaches to Identifying and Prioritizing Security Initiatives

Several factors can drive security initiatives:

* **Audit Findings:** Audits can reveal weaknesses in existing controls and provide recommendations for improvement.
* **Technological Advancements:**  New technologies can offer better security solutions or address emerging threats.  Example: Replacing a staff card system with biometrics.
* **Compliance Requirements:**  Laws, regulations, and industry standards can mandate specific security controls. Example: Implementing data encryption to comply with data protection regulations.
* **Risk Assessments:**  Risk analysis helps identify the most significant threats and vulnerabilities, which then informs the prioritization of security initiatives.


#### 1.6 Accidents vs. Incidents

* **Accident:** An unintended, unforeseen, and unexpected event that results in loss or damage.
* **Incident:** An unplanned event that *may* compromise security.  It can be intentional (e.g., a cyberattack) or unintentional (e.g., a user accidentally deleting important data). Incidents that don't cause damage are often referred to as "near misses" and are still valuable for learning and improvement.

#### 1.7 Organizational Assets vs. Information Assets

* **Organizational Assets:**  These are the resources owned or controlled by an organization that have value.  They can be tangible (buildings, equipment) or intangible (reputation, intellectual property).
* **Information Assets:**  This is a subset of organizational assets and specifically refers to information valuable to the organization. This includes data in electronic form (databases, files), physical form (documents, printouts), or even knowledge residing with personnel.

### Chapter 2: Risk Assessment Methodologies

#### 2.1  Quantitative vs. Qualitative Analysis

Risk assessment methodologies are broadly categorized as quantitative or qualitative, each with its own approach to determining risk levels.  Choosing the right method depends on factors like the availability of data, the organization's resources, and the desired level of precision.

* **Quantitative Analysis:**  This approach uses numerical data and formulas to calculate risk, aiming to assign a monetary value to potential losses. This allows for a more objective comparison of different risks and facilitates cost-benefit analysis of security controls. Key metrics and calculations in quantitative analysis include:

    * **Asset Value (AV):**  The monetary value of the asset being assessed. This can include the cost of replacement or repair, the lost revenue during downtime, or the cost of reputational damage.
    * **Exposure Factor (EF):** The percentage of the asset's value that is likely to be lost in a single incident. For example, if a fire is expected to destroy 50% of a warehouse, the EF is 0.5.
    * **Single Loss Expectancy (SLE):** AV x EF = The expected monetary loss from a single occurrence of a risk event.
    * **Annualized Rate of Occurrence (ARO):** The estimated frequency with which a threat is likely to occur in a year.  This can be based on historical data, industry averages, or expert judgment.
    * **Annualized Loss Expectancy (ALE):** SLE x ARO = The expected annual financial loss due to a specific risk.  This is a key metric for prioritizing risks and justifying security investments.
    * **Safeguard Value:**  The expected reduction in ALE after implementing a safeguard, minus the annual cost of the safeguard.  A positive safeguard value indicates a cost-effective control.  This is calculated as:  `(ALE before safeguard - ALE after safeguard) - Annual Cost of Safeguard`.

* **Qualitative Analysis:** This approach uses subjective judgment, descriptive terms (e.g., high, medium, low), and scenarios to assess risk. It relies on the expertise and experience of the assessment team and stakeholders.  Qualitative analysis is often used when precise numerical data is unavailable or when the organization prefers a more narrative approach to risk assessment.  While less precise than quantitative analysis, it can be more flexible and adaptable to different situations. Methods often involve rating threats, vulnerabilities, and impacts on scales (e.g., 1-5 or Low-Medium-High). Risk matrices are commonly used to combine likelihood and impact ratings to determine overall risk levels.


#### 2.2 Expected Loss and Probability

Expected loss is a crucial concept in quantitative risk assessment.  It calculates the average loss an organization can anticipate over time due to a specific risk.  This involves considering the probability of different outcomes and the associated losses for each outcome.  Expected loss is directly related to SLE and ALE:

* **Single Loss Expectancy (SLE):** Represents the expected financial loss from a *single* occurrence of a risk event. It is a fundamental component of calculating ALE.
* **Annualized Loss Expectancy (ALE):** Extends the concept of SLE by considering the frequency with which the risk event is expected to occur annually (ARO). This provides a more realistic estimate of the potential financial impact over time.

**Example (from slide Note 13):**

Imagine a scenario where you are flipping a coin with a friend. If it lands on heads, you win RM1; if it lands on tails, you win RM2.50.  From your friend's perspective (who is losing the money), the expected loss for a single flip is:

* Expected Loss = (Probability of Heads x Loss for Heads) + (Probability of Tails x Loss for Tails)
* Expected Loss = (0.5 x RM1) + (0.5 x RM2.50) = RM1.75

This simple example illustrates how probability and potential losses are combined to determine the expected loss.  In real-world security risk assessments, these probabilities and losses relate to specific threats and vulnerabilities impacting organizational assets.

#### 2.3 Overview of Risk Assessment Methods

Many standardized risk assessment methodologies provide frameworks and structured approaches. Each has its own strengths and weaknesses, making it suitable for different organizations and situations.  Here's a high-level overview of some common methods:

* **NIST SP 800-30 (National Institute of Standards and Technology):** A widely used, comprehensive risk assessment framework that provides step-by-step guidance for conducting risk assessments.  It's adaptable to various organizations and information systems.  It emphasizes a cyclical approach of risk assessment, risk mitigation, and ongoing monitoring.

* **OCTAVE (Operationally Critical Threat, Asset, and Vulnerability Evaluation):** A self-directed risk assessment methodology that focuses on organizational risk, emphasizing stakeholder involvement and self-assessment.  It's particularly well-suited for organizations that want to build internal risk management capabilities.

* **FRAP (Facilitated Risk Analysis Process):**  A qualitative methodology that utilizes workshops and facilitated sessions to identify and assess risks. It's known for its collaborative approach and its focus on understanding the organization's unique context.

* **CRAMM (CCTA Risk Analysis and Management Method):** A structured, semi-quantitative method developed by the UK government.  It provides a detailed framework for assessing risks to information systems and selecting appropriate controls.

* **Other Methods:**  Numerous other methodologies exist, including those specific to certain industries or regulations (e.g., HIPAA for healthcare, PCI DSS for payment card industry).

**(Further details about these methodologies, including their specific steps, advantages, and disadvantages, will be covered in a later chapter.)**
