## Software Verification & Validation: Comprehensive Notes (Weeks 1-11)

**Chapter 1: Introduction to Software Testing (Week 1)**

**1.1 What is Software Testing?**

Software testing is a crucial process, not merely a single activity, encompassing a range of techniques and methodologies.  It systematically evaluates software to identify defects, assess its quality attributes, and ensure it meets specified requirements and behaves as expected under diverse conditions.  Effective testing goes beyond simply running the software; it involves carefully designing test cases, analyzing results, and providing feedback to improve the development process.

**1.2 Why Test Software?  The Cost of Failure**

Software failures can have a wide range of consequences, impacting safety, finances, and reputation:

* **Safety-critical systems:** Failures in software controlling airplanes, medical devices, or nuclear power plants can be life-threatening.
* **Financial loss:** Software bugs in financial systems can lead to significant monetary losses.
* **Reputational damage:**  Software failures can erode customer trust and negatively affect a company's image.
* **Project delays:**  Finding and fixing defects late in development can lead to costly project delays and rework.

Proactive testing helps minimize these risks and contributes to a higher-quality, more reliable software product.

**1.3  Key Concepts: Understanding the Terminology**

* **Software Fault/Defect:** A flaw, error, or bug in the code or design that can cause the software to behave incorrectly.  A defect is the underlying cause of an error.
* **Software Error:** An incorrect internal state within the software that is the manifestation of a fault. It's a deviation from the expected behavior.
* **Software Failure:** An external, observable incorrect behavior of the software. A failure occurs when an error leads to an undesirable outcome.


**1.4 Verification and Validation (V&V)**

* **Verification:**  Focuses on ensuring that the software is built correctly according to the specifications.  Think of it as checking the steps along the way. It asks: "Are we building the system right?" Activities include:
    * **Reviews:** Manual inspection of documents, code, and other artifacts.
    * **Inspections:** More formal reviews with defined roles and procedures.
    * **Walkthroughs:**  Less formal reviews led by the author of the artifact.
    * **Static Analysis:** Automated code analysis to detect potential issues.
* **Validation:**  Focuses on ensuring that the built software meets the user's needs and intended usage. It asks: "Are we building the right system?" It's about checking the final product against real-world usage scenarios.  Activities include:
    * **User Acceptance Testing (UAT):** End-user validation.
    * **System Testing:** Evaluating the complete integrated system.


**1.5 Quality Assurance (QA)**

Quality Assurance is an umbrella term for all planned and systematic activities implemented within the quality system to ensure that software quality requirements will be fulfilled. It includes V&V processes but also extends to other aspects like process improvement and quality planning.

**1.6 Test Cases: A Detailed Blueprint**

A test case is a detailed, specific procedure for testing a particular aspect of the software. It provides a clear set of instructions for testers to execute and evaluate the results.  Key components:

* **Test Case ID:** A unique identifier (e.g., TC-001).
* **Test Scenario:** A high-level description of the test's purpose (e.g., "Verify login functionality").
* **Test Steps:**  A numbered list of specific actions to be performed (e.g., "Enter username," "Enter password," "Click Login").
* **Test Data:**  The specific data values used as input for the test (e.g., username "testuser," password "password123").
* **Expected Result:**  The expected outcome of the test (e.g., "User is redirected to the homepage").
* **Actual Result:** The observed outcome when the test is executed.
* **Pass/Fail Status:** Whether the actual result matches the expected result.
* **Preconditions:** Conditions that must be true before the test can be executed (e.g., "User is logged out").
* **Postconditions:** Conditions that will be true after the test has been executed (e.g., "User is logged in").

**1.7 7 Principles of Testing: Guiding Principles for Effective Testing**

1. **Testing shows presence of defects:** Testing can only reveal the presence of defects, but it cannot guarantee their absence.  Even with extensive testing, some defects may remain undiscovered.
2. **Exhaustive testing is impossible:** Testing every possible input, combination of inputs, and execution path is practically impossible for most software systems.  Testers must prioritize based on risk and available resources.
3. **Early testing:** Testing should begin as early as possible in the software development lifecycle. Early detection of defects significantly reduces the cost and effort of fixing them.
4. **Defect clustering:** A small number of modules usually contains most of the defects discovered during pre-release testing or shows the most operational failures. Focusing testing efforts on these areas can be more efficient.
5. **Pesticide paradox:** If the same tests are repeated over and over again, eventually the same set of test cases will no longer find any new bugs.  Test cases need to be regularly reviewed and revised, and new and different tests need to be written to exercise different parts of the software or system to find more defects.
6. **Testing is context dependent:** The testing approach and techniques used should be tailored to the specific context of the software being tested, such as its intended use, risk level, and development methodology.
7. **Absence-of-errors is a fallacy:**  A system that is 99% bug-free might still be unusable if that 1% of bugs prevents core functionality from working or makes the system extremely difficult to use.  Testing should focus not just on finding defects but also on ensuring the software meets user needs and expectations.

**1.8 Software Development Models & Testing: Aligning Testing with Development**

The choice of software development model significantly influences the testing approach:

* **V-Model:**  A sequential model where testing activities are planned in parallel with development phases.  Each development phase has a corresponding testing phase (e.g., requirements gathering is paired with acceptance testing, system design with system testing).
* **Agile:** An iterative and incremental approach where testing is integrated throughout the development process.  Tests are often written *before* the code in a Test-Driven Development (TDD) approach.
* **W-Model:**  An extension of the V-Model where testing activities are not only planned but also executed concurrently with development.  This emphasizes early testing and tighter integration between development and testing.
* **Iterative Incremental:** The software is developed and tested in a series of iterations, with each iteration adding new functionality. Testing is an ongoing process in each iteration.


**1.9 Test Levels: A Hierarchy of Testing**

1. **Unit Testing:**  Focuses on testing the smallest units of the software in isolation (e.g., individual functions, methods, or classes).
2. **Integration Testing:**  Focuses on testing the interaction between different units or components after they have been integrated.
3. **System Testing:**  Focuses on testing the fully integrated system as a whole to verify it meets the specified requirements.
4. **Acceptance Testing:**  Focuses on validating the system against user needs and acceptance criteria to ensure it is ready for deployment.

**1.10 Drivers and Stubs: Facilitating Isolated Testing**

* **Drivers:**  A driver is a software module used to invoke a component under test. It simulates the part of the system that would normally call the unit being tested.  It provides inputs and controls the execution of the unit.
* **Stubs:**  A stub is a skeletal or special-purpose implementation of a software module. It replaces a component that the unit being tested depends on. It provides canned responses and simulates the behavior of the missing component.


**Chapter 2: System and Acceptance Testing (Week 2)**

**2.1 System Testing: Evaluating the Complete System**

System testing is a crucial testing level that focuses on evaluating the fully integrated software system as a whole. It verifies that the system meets specified requirements, functions as intended, and performs adequately under realistic conditions.

* **Strategies based on Non-Functional Requirements (NFRs):** Non-functional requirements define the system's quality attributes. ISO 9126 quality characteristics provide a framework for defining and testing NFRs:
    * **Functionality:**  Is the system providing the required functions?  Are all features working correctly?
    * **Reliability:** Is the system stable and reliable under normal conditions? How does it handle errors?
    * **Usability:**  Is the system easy to use and understand?  Is the user interface intuitive and user-friendly?
    * **Efficiency:**  Does the system perform efficiently in terms of resource usage (memory, CPU, network bandwidth)?  Are response times acceptable?
    * **Maintainability:** How easy is it to maintain and modify the system? Is the code well-structured and documented?
    * **Portability:** Can the system be easily ported to different platforms and environments?


* **Tools for NFR Testing:**
    * **JMeter:** An open-source tool for load testing and performance measurement.  It can simulate a large number of users accessing the system concurrently.
    * **LoadRunner:**  A commercial tool for performance and load testing. It provides comprehensive performance analysis and reporting capabilities.


* **System Portability Testing:**  This type of testing verifies the system's ability to function correctly on different platforms and environments.  This includes different operating systems (Windows, macOS, Linux), different web browsers (Chrome, Firefox, Safari), and different hardware configurations.


* **Challenges in System Testing:**
    * **Defining clear acceptance criteria:**  It can be challenging to define precise and measurable criteria for system test success.
    * **Managing complex test environments:** Setting up and managing realistic test environments that replicate the production environment can be complex and time-consuming.
    * **Addressing indistinct customer requirements:**  Vague or incomplete requirements can make it difficult to design effective test cases and assess system compliance.


**2.2 Acceptance Testing: Validating User Needs**

Acceptance testing is the final stage of testing before the system is released to end-users. It focuses on validating the system against user needs and acceptance criteria.  Different types of acceptance testing serve specific purposes:

* **User Acceptance Testing (UAT):**  Conducted by end-users to verify the system meets their needs and expectations in a real-world usage scenario.  It is the primary form of validation.
* **Operational Acceptance Testing:** Conducted by system administrators to ensure the system can be deployed, operated, and maintained effectively. Tests include backup/restore procedures, disaster recovery, security hardening, and performance monitoring.
* **Contract and Regulation Acceptance Testing:** Verifies that the system complies with contractual obligations and regulatory standards (e.g., government regulations, industry standards).
* **Alpha & Beta Testing:**
    * **Alpha Testing:**  Early testing performed by a small group of users at the developer's site to identify critical bugs before beta testing.
    * **Beta Testing:**  Testing performed by a larger group of representative end-users at their own locations to gain feedback on the system's usability and identify any remaining defects.


**2.3 Conducting UAT: A Step-by-Step Process**

1. **Detailed Business Requirements Analysis:**  Thoroughly understand the business requirements, user stories, and use cases to define the scope and objectives of UAT.
2. **Develop UAT Test Plan:**  Create a comprehensive plan that outlines the UAT strategy, scope, test objectives, test environment, test data, entry and exit criteria, and schedule.
3. **Develop Test Scenarios:**  Develop realistic scenarios that represent typical user interactions and workflows. These scenarios provide a context for the test cases.
4. **Create UAT Test Cases:**  Design detailed test cases that specify the steps to be performed, the expected results, and the test data for each scenario.  Each test case should validate a specific aspect of the system's functionality.
5. **Test Data Preparation:** Prepare realistic test data that represents the actual data that the system will be used with.  This data should cover various valid and invalid scenarios.
6. **Run Test Cases:**  Execute the UAT test cases in the designated test environment.  Document the actual results and any observed issues.
7. **Gather Feedback:** Collect feedback from the UAT participants. This feedback can be collected through surveys, questionnaires, interviews, or bug reports.
8. **Evaluate and Report:**  Analyze the test results and feedback to identify any issues or areas for improvement. Prepare a comprehensive UAT report summarizing the findings and recommendations.


**Chapter 3: Unit Testing and Test-Driven Development (Week 3)**

**3.1 Unit Testing**

Unit testing focuses on isolating and testing individual components or modules of the software.

* **Benefits:** Easier debugging, improved code design, increased confidence in code changes.
* **Drivers & Stubs:** These are essential tools for unit testing.
    * **Driver:**  Simulates the part of the system that calls the component being tested.
    * **Stub:** Simulates the components called by the unit being tested.

**3.2 Test-Driven Development (TDD)**

TDD is a development approach where tests are written *before* the code they are intended to test.

* **TDD Principle:** "Red, Green, Refactor"
    1. **Red:** Write a failing test case.
    2. **Green:**  Write the minimal code necessary to make the test pass.
    3. **Refactor:**  Improve the code structure and design while ensuring the tests still pass.
* **3 Laws of TDD:**
    1. You may not write production code unless you have a failing unit test.
    2. You may not write more of a unit test than is sufficient to fail.
    3. You may not write more production code than is sufficient to pass the one failing unit test.
* **TDD Process Cycle:**
    1. Add a little test.
    2. Run all tests and see the new one fail.
    3. Make a little change (write the minimal code to pass the test).
    4. Run the tests and see them all succeed.
    5. Refactor to remove duplication.
* **Benefits:** Improved code design, reduced defects, easier maintenance, higher code confidence.
* **Limitations:**  Difficult for legacy code, requires experienced programmers, might not be suitable for all types of software (e.g., GUIs, complex database interactions).
* **Common Objections (and Rebuttals):**
    * "I'm paid to write code, not tests":  Writing tests actually *saves* time and money in the long run by reducing debugging time and rework.
    * "We are working on a tight deadline":  While TDD might seem to add overhead initially, it helps prevent costly defects and delays later in the project.

**3.3 JUnit Framework**

JUnit is a popular Java framework for writing and running unit tests.

* **Key Concepts:**
    * **Test Fixture:**  Sets up the necessary data and objects for running tests.
    * **Unit Test:** Tests a single class.
    * **Test Case:**  Tests the response of a single method to a specific set of inputs.
    * **Test Suite:** A collection of test cases.
    * **Test Runner:** Software that runs tests and reports results.
    * **Integration Test:** Tests the interaction between multiple classes. (JUnit has limited support for this).
* **Assert Methods:**  Used to verify expected outcomes. Examples: `assertEquals()`, `assertTrue()`, `assertNull()`.
* **AAA Pattern:** Arrange-Act-Assert is a common pattern for structuring test cases.
* **Test Fixtures (Annotations):**
    * `@Before`:  Runs before each test case (for setup).
    * `@After`: Runs after each test case (for cleanup).
    * `@BeforeClass`: Runs once before all test cases in a class.
    * `@AfterClass`: Runs once after all test cases in a class.


**Chapter 4: Mocking (Week 4)**

**4.1 Introduction to Mocking: Decoupling for Testability**

In unit testing, isolation is key. Mocking allows us to isolate the unit under test by simulating its dependencies. This is particularly important when dealing with external resources like databases, web services, or other complex components.

**4.2 Test Doubles:  Stand-ins for Real Components**

Test doubles are objects that stand in for real dependencies during testing. There are several types of test doubles:

* **Dummy:**  A dummy object is passed around but never actually used. It fulfills parameter requirements but has no other purpose.
* **Stub:** A stub provides canned responses to method calls. It allows us to control the behavior of the dependency and test specific scenarios.
* **Fake:** A fake is a working implementation, but it takes shortcuts or simplifies complex logic for testing purposes. For example, an in-memory database can be a fake for a real database.
* **Mock:** A mock is similar to a stub but also verifies interactions. It asserts that specific methods were called on the mock with expected arguments.

**4.3 Why Use Test Doubles?**

* **Isolation:** Isolate the unit under test to ensure that test results are not affected by external factors.
* **Speed:** Tests run faster because they don't interact with real dependencies.
* **Control:**  Control the behavior of dependencies to simulate different scenarios and edge cases.
* **Predictability:**  Ensure that tests are repeatable and produce consistent results.
* **Early Verification:**  Test interactions and behavior early in the development process, even when dependencies are not fully implemented.

**4.4 The Mock or Not Mock Debate**

Mocking can be beneficial, but overusing it can lead to tightly coupled tests and obscure design flaws. Consider the trade-offs and strive for a balance:

* **Avoid Over-Mocking:**  If possible, refactor the code to reduce dependencies and simplify testing.
* **Employ Mocking Strategically:** Use mocks when dependencies are complex, slow, or unavailable during testing.

**4.5 Mocking with Mockito: A Practical Approach**

Mockito is a popular mocking framework for Java.

* **Creating Mocks:** Use `mock(Class)` to create a mock object.
* **Stubbing Methods:** Use `when(mock.methodCall()).thenReturn(value)` to define canned responses.
* **Verifying Interactions:** Use `verify(mock).methodCall(arguments)` to ensure that specific methods were called on the mock.
* **Example:**

```java
// Create a mock for the MaxService interface
MaxService cloudService = mock(MaxService.class);

// Stub the maxNumber method to return 500
when(cloudService.maxNumber(400, 500)).thenReturn(500);

// Create an instance of the Maximum class using the mock
Maximum m = new Maximum(cloudService);

// Call the method under test
int result = m.maxNumberPerform(400, 500);

// Assert the expected result
assertEquals(300, result);

// Verify that the maxNumber method was called on the mock with the correct arguments
verify(cloudService).maxNumber(400, 500);

```

**4.6 Integrating Mockito with Maven**

Add the Mockito dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-core</artifactId>
    <version>3.12.4</version> <!-- Or latest version -->
    <scope>test</scope>
</dependency>
```

**4.7  MongoDB for Persistence**

When integrating with external databases like MongoDB, mocks are essential during unit testing.  Use a mock or fake database to avoid dependencies on the actual database during development and to speed up test execution.

**Chapter 5: Static Testing - Software Validation (Week 5)**

**5.1 Static vs. Dynamic Testing**

* **Static Testing:**  Analyzes the software *without* executing it. Focuses on reviewing documents, code, and other artifacts to identify defects early. Techniques include:
    * Reviews
    * Inspections
    * Walkthroughs
    * Static Analysis
* **Dynamic Testing:**  Evaluates the software by *executing* it.  Focuses on observing the system's behavior and identifying runtime errors. Techniques include unit testing, integration testing, system testing, and acceptance testing.

**5.2 Reviews: Early Defect Detection**

Reviews are a fundamental static testing technique. They involve manual examination of software artifacts to identify defects, improve quality, and facilitate communication.

* **Purpose and Value:**  Find defects early, improve understanding, share knowledge, and build consensus.
* **When and What to Review:** Review any software artifact as soon as it's available.  This includes requirements documents, design specifications, code, test plans, user documentation, etc.
* **What Reviews Find:**  Reviews can uncover various defects, including:
    * Deviations from standards
    * Requirement defects (ambiguities, inconsistencies)
    * Design flaws
    * Code errors (logic errors, security vulnerabilities)
    * Usability issues
    * Documentation errors

**5.3 Review Types:  A Spectrum of Formality**

* **Informal Review:**  Lightweight review with minimal process overhead.  Good for quick feedback and early defect detection.
* **Walkthrough:** A review led by the author of the artifact, who explains it to a group of reviewers.  Primarily for educational purposes and knowledge sharing.
* **Technical Review:**  A more formal review involving technical experts to assess compliance with standards and identify potential technical issues.
* **Inspection:**  A highly structured and formal review process with defined roles, entry and exit criteria, and detailed documentation.  The most rigorous review type, focused on finding defects.
* **Management Review:**  Focuses on reviewing the project's status and progress against plans and objectives. Not directly concerned with the technical details of the software.
* **Audit:** An independent evaluation of the software product and processes to ensure compliance with standards, regulations, guidelines, and procedures.

**5.4 Review Roles: Defined Responsibilities for Effective Collaboration**

* **Manager:**  Decides on executing reviews, allocates resources, and ensures review objectives are met.
* **Moderator:** Leads the review, manages the meeting, and facilitates discussion.
* **Author:**  The creator of the artifact being reviewed. Responsible for explaining the artifact and addressing reviewer comments.
* **Reviewer/Inspector:**  Technical experts who examine the artifact and identify defects.
* **Scribe:** Documents the defects and issues found during the review.

**5.5 Review Processes:  Structured Approaches**

* **Synchronous Review (Meeting-Based):**
    1. Planning/Overview: Define scope, objectives, and select participants.
    2. Preparation: Reviewers familiarize themselves with the artifact.
    3. Inspection/Review Meeting:  Reviewers discuss the artifact and identify defects.
    4. Rework: Author addresses the identified defects.
    5. Follow-up: Moderator ensures all defects are resolved and closes the review.
* **Asynchronous Review (Email/Tool-Based):**
    1. Planning and Setup: Select personnel, organize documentation, and choose tools.
    2. Individual Review: Reviewers independently review the artifact.
    3. Consolidation: Feedback is collected and consolidated.
    4. Public Review (Optional):  Consolidate feedback is discussed and voted upon.
    5. Rework: Author addresses the identified defects.


**5.6  Challenges and Pitfalls of Reviews**

* **Insufficient preparation:** Reviewers not adequately prepared can hinder the effectiveness of the review.
* **Moderator domination:**  A dominant moderator can stifle discussion and prevent full participation from reviewers.
* **Incorrect review rate:**  Rushing through the review can lead to missed defects, while going too slowly can be inefficient.
* **Ego involvement:**  Personal biases and ego can hinder objective evaluation and create conflict.
* **Lack of management support:**  Reviews need management support to ensure resources and time are allocated appropriately.

**Chapter 6: Review and Inspection Process - Software Validation (Static Testing) Continued (Week 6)**

This chapter provides a deep dive into the review and inspection processes introduced in Week 5, focusing on the practical aspects of conducting effective reviews.

**6.1 Review Materials: Essential Documents and Tools**

* **Source Document:** The artifact being reviewed (e.g., requirements document, design specification, code).
* **Checklist:** A list of specific items or criteria that reviewers should focus on during the review.
* **Supporting Documents:** Any documents that provide context or background information relevant to the source document (e.g., previous versions, related specifications).
* **Invitation:**  Formal notification sent to participants, including the review's purpose, date, time, and location (if applicable).
* **Master Plan:**  A high-level document that outlines the overall review strategy and schedule.
* **Issue/Defect Log:**  A document used to record the defects and issues identified during the review, including their severity, location, and description.
* **Data Summary:** A summary report of the review findings, including the number of defects found, their severity distribution, and other relevant metrics.

**6.2 Review Methods: Synchronous vs. Asynchronous**

* **Synchronous Review (Meeting-Based):**  Real-time reviews where participants meet together, either physically or virtually.  Best suited for complex artifacts and situations requiring collaborative discussion.
* **Asynchronous Review (Email/Tool-Based):**  Reviews conducted over time, where participants review the artifact independently and submit feedback. Best suited for simpler artifacts or when scheduling conflicts make synchronous reviews difficult.

**6.3 Synchronous Review Process: The Fagan Inspection**

The Fagan Inspection is a formal, structured approach to synchronous reviews, particularly effective for finding defects.

1. **Planning:** Define the review's scope, objectives, and entry and exit criteria.  Select participants and assign roles.
2. **Overview:** Introduce the artifact to the reviewers and provide context.  Ensure all participants understand the review's goals.
3. **Preparation:** Reviewers individually examine the artifact using checklists and supporting documents.  They identify potential defects and prepare for the review meeting.
4. **Inspection Meeting:**  The team meets to discuss the artifact and identify defects. The moderator leads the meeting and the scribe documents the findings.  Focus on finding defects, not fixing them.
5. **Rework:** The author addresses the defects identified in the inspection meeting.
6. **Follow-up:**  The moderator verifies that all defects have been resolved and meet the exit criteria.  If necessary, a re-inspection is scheduled.


**6.4 Roles in Synchronous Reviews:  Specific Responsibilities**

* **Manager:**  Oversees the review process, allocates resources, and makes decisions about the artifact's disposition.
* **Moderator:**  Leads the review meeting, facilitates discussion, keeps the review focused, and ensures all participants have a chance to contribute.
* **Author:** Presents the artifact, answers questions, clarifies ambiguities, and is responsible for addressing the identified defects.
* **Reviewer/Inspector:**  Examines the artifact, identifies defects, and raises questions. Should have specific expertise related to the artifact.
* **Scribe/Recorder:** Documents all issues, defects, and decisions made during the review meeting.

**6.5 Asynchronous Review Process:  Flexibility and Independence**

Asynchronous reviews leverage tools and communication channels (like email or specialized review platforms) to facilitate reviews where participants contribute independently.

1. **Planning and Setup:** Similar to synchronous reviews, the scope, objectives, and participants are defined. The necessary tools and communication channels are set up.
2. **Individual Review:**  Reviewers examine the artifact independently at their own pace and record their feedback using the chosen tools.
3. **Consolidation:** The moderator or a designated reviewer collects and consolidates the feedback from individual reviewers.
4. **Public Review (Optional):**  The consolidated feedback can be discussed and voted on in a public forum or virtual meeting.  This step can help achieve consensus on complex issues.
5. **Rework:** The author addresses the identified defects.
6. **Follow-up:**  The moderator ensures that all defects have been resolved and closes the review.

**6.6 Review Pitfalls: Common Challenges to Avoid**

* **Insufficient Preparation:** Reviewers lacking sufficient understanding of the artifact or the review process can lead to unproductive reviews.
* **Moderator Domination:**  A moderator who dominates the discussion can prevent other reviewers from fully participating.
* **Incorrect Review Rate:**  Rushing through the review can lead to missed defects. Conversely, a slow pace can be inefficient.
* **Ego Involvement and Personality Conflicts:**  Personal biases and conflicts can hinder objective evaluation.
* **Issue Resolution During the Meeting:** Focus on identifying defects, not solving them.  Resolving issues during the review can take valuable time and derail the process.
* **Recording Difficulties and Clerical Overhead:**  Incomplete or unclear documentation can make it difficult to track and resolve defects.

**Chapter 7: Test Design Techniques & Prototyping in Static Testing (Week 7)**

**7.1 Test Design Techniques: Strategies for Effective Testing**

Test design techniques provide systematic approaches to creating test cases that effectively cover different aspects of the software.

* **Specification-Based (Black-Box) Techniques:** These techniques focus on the software's external behavior and are based on the functional and non-functional requirements. No knowledge of the internal code or structure is required.
    * **Equivalence Partitioning:** Divides the input domain into equivalence classes, where each class represents a set of inputs that are expected to be treated similarly by the software. Test cases are designed to cover at least one value from each equivalence class.
    * **Boundary Value Analysis (BVA):** Focuses on testing values at the boundaries of equivalence classes, as defects often occur at these edges. Test cases include values at the boundary, just above the boundary, and just below the boundary.
    * **Decision Table Testing:**  Used to test complex business rules and logical conditions.  A decision table lists all possible combinations of conditions and their corresponding actions. Test cases are derived from each row of the decision table.
* **Structure-Based (White-Box) Techniques:**  These techniques require knowledge of the internal code structure and logic. They focus on testing specific paths and branches within the code. Examples include statement coverage, branch coverage, and path coverage.
* **Experience-Based Techniques:** These techniques rely on the tester's experience, intuition, and knowledge of common defects to design test cases. Examples include exploratory testing and error guessing.


**7.2 Prototyping in Static Testing: Early Validation of User Interface and User Experience**

Prototypes are early representations of the software, typically used to gather feedback on the user interface (UI) and user experience (UX) before full development begins.  While not fully functional, prototypes provide enough detail for static testing techniques to be applied.

* **Benefits of Using Prototypes:**
    * **Early Feedback:** Gather feedback from stakeholders early in the process and identify potential design flaws before significant development effort is invested.
    * **Validate Requirements:** Ensure that the prototype aligns with the documented requirements and meets user expectations.
    * **Visual Representation:**  Provide a concrete visualization of the UI/UX, making it easier for stakeholders to understand and provide feedback.

* **Types of Prototypes:**
    * **Low-Fidelity Prototypes:** Simple sketches, wireframes, or mockups that represent the basic structure and layout of the UI. Useful for early-stage feedback and concept validation.
    * **High-Fidelity Prototypes:**  Interactive prototypes that closely resemble the final product in terms of visual design and functionality. Useful for detailed usability testing and identifying more subtle design flaws.

* **Static Testing Techniques for Prototypes:**
    * **Walkthroughs:** The author or designer presents the prototype and explains its features and functionality to stakeholders.  Reviewers provide feedback on the design and identify potential issues.
    * **Peer Reviews:** A group of peers or stakeholders reviews the prototype and provides feedback on its design, usability, and compliance with standards.
    * **Requirement Reviews:**  The prototype is compared against the requirements document to ensure it meets all specified requirements.
    * **Usability Reviews:**  Focus specifically on the user experience of the prototype. Reviewers evaluate the ease of use, intuitiveness, and accessibility of the UI.


* **How to Conduct Static Testing on Prototypes:**
    1. Plan: Define objectives and select participants.
    2. Prepare: Create the prototype and any supporting materials.
    3. Conduct Walkthrough/Review: Present the prototype and gather feedback.
    4. Document Findings:  Record all comments, suggestions, and defects.
    5. Update and Iterate:  Revise the prototype based on feedback and conduct another review if needed.
    6. Close the Review:  Ensure all defects are resolved and the review is completed.

**Chapter 8: Software Metrics (Week 8)**

**8.1 Introduction to Software Metrics: Quantifying Software Quality**

Software metrics are quantifiable measures used to assess different aspects of a software product or process. They provide objective data that can be used to track progress, identify areas for improvement, and make informed decisions.  Metrics can be applied throughout the software development lifecycle, from requirements gathering to maintenance.

**8.2 Types of Software Metrics: A Broad Categorization**

Software metrics can be broadly categorized into:

* **Product Metrics:** These metrics measure characteristics of the software product itself, such as its size, complexity, reliability, and maintainability.  Examples include lines of code, cyclomatic complexity, defect density, and mean time to failure.
* **Process Metrics:** These metrics measure the effectiveness and efficiency of the software development process.  Examples include effort, schedule adherence, defect detection rate, and review effectiveness.
* **Project Metrics:** These metrics measure the overall progress and success of a software project. Examples include earned value, cost variance, schedule variance, and customer satisfaction.

**8.3 Code Metrics: Measuring Code Characteristics**

Code metrics provide insights into the quality and complexity of the source code. They can be further classified into:

* **Size-Oriented Metrics:** These metrics measure the size of the codebase, typically in terms of lines of code (LOC) or thousands of lines of code (KLOC).  While simple, LOC can be a useful indicator of project size and effort.
* **Complexity-Oriented Metrics:** These metrics quantify the complexity of the code, often indicating how difficult it is to understand and maintain.  Examples include cyclomatic complexity, which measures the number of independent paths through the code, and Halstead metrics, which analyze the number of operators and operands in the code.
* **Object-Oriented Metrics:**  These metrics are specific to object-oriented programming and measure characteristics like inheritance depth, coupling between objects, and cohesion within classes. Examples include the Chidamber-Kemerer metrics suite and metrics for object-oriented design.

**8.4 Process Metrics: Evaluating Development Processes**

Process metrics focus on the effectiveness and efficiency of the software development process. They can be used to identify bottlenecks, improve workflows, and optimize resource allocation. Some key process metrics include:

* **Code Churn:**  Measures the rate at which code is added, modified, or deleted over time. High churn can indicate instability or frequent changes in requirements.
* **Code Ownership:** Tracks which developers are responsible for different parts of the codebase.  This can be helpful for prioritizing bug fixes and identifying areas where knowledge sharing is needed.
* **Context of Changes:**  Classifies code changes by their purpose, such as bug fixes, refactoring, or adding new features. This helps analyze the impact of different types of changes on the codebase.
* **Change Deltas:**  Measures the differences between successive versions of the software, providing insights into the evolution of the codebase and the impact of changes.
* **Internal Communication:**  Quantifies communication within the development team, such as email exchanges or discussions in collaboration tools. This can help identify communication bottlenecks or improve team collaboration.

**8.5 Test Measurement of Structural Coverage: Ensuring Thorough Testing**

Structural coverage metrics assess the extent to which the test suite exercises different parts of the software's structure. These metrics are typically expressed as a percentage and help ensure that testing is thorough and comprehensive. Common types of structural coverage include:

* **Statement Coverage:**  Measures the percentage of lines of code executed by the test suite.
* **Branch Coverage:** Measures the percentage of decision points (if-else statements, loops) exercised by the test suite.
* **Path Coverage:**  Measures the percentage of all possible execution paths through the code covered by the test suite.

**8.6  Software Testing Metrics: Monitoring Test Activities**

Software testing metrics are used to measure and monitor the test activities and provide insights into the test progress, productivity, and the quality of the system under test. Examples include:

* **Result Metrics:** These metrics provide absolute measures of testing activities, such as the number of test cases executed, passed, or failed.
* **Predictive Metrics:** These metrics are derived from other metrics and provide early warnings of potential problems, such as the rate of defect fixing compared to the rate of defect detection.

**8.7 The Fundamental Test Metrics:  Basic Building Blocks**

Fundamental test metrics are the basic building blocks for other metrics. They include absolute numbers such as:

* Total number of test cases
* Number of test cases passed, failed, or blocked
* Number of defects found, accepted, rejected, or deferred
* Number of critical defects
* Planned and actual test hours
* Number of bugs found after shipping

**8.8 Derivative Test Metrics:  Gaining Deeper Insights**

Derivative test metrics are calculated from the fundamental metrics and provide more meaningful insights into testing effectiveness and efficiency.  Examples include:

* Passed test case percentage
* Failed test case percentage
* Blocked test case percentage
* Fixed defect percentage
* Average time for the development team to repair defects


**Chapter 9: AI in Software Quality & SVV (Test Cases) (Week 10)**

**9.1 Introduction to AI in Software Testing: Automating Quality Assurance**

Artificial intelligence (AI) is rapidly transforming software testing and verification and validation (SVV) processes.  AI-powered tools can automate various tasks, from test case generation to defect prediction, improving efficiency and effectiveness.

**9.2 AI-Powered Test Case Generation:  Creating Tests Automatically**

Traditional test case generation can be time-consuming and prone to human error.  AI algorithms can automatically generate test cases based on requirements specifications, code analysis, or user behavior models.

* **Model-Based Testing:**  AI algorithms can analyze models of the system under test (e.g., state diagrams, use case diagrams) and generate test cases that cover different paths and scenarios.
* **Code-Based Testing:**  AI can analyze the source code and automatically generate unit tests or integration tests that target specific functions or components.
* **Requirement-Based Testing:** AI can process natural language requirements documents and generate test cases that verify the specified functionality.


**9.3 AI for Test Prioritization and Optimization: Focusing on Critical Tests**

AI can prioritize test cases based on their importance, risk, or likelihood of revealing defects.  This is especially valuable for large test suites where executing every test case is impractical.

* **Risk-Based Prioritization:** AI can identify high-risk areas of the software and prioritize test cases that target these areas.
* **Change-Impact Analysis:**  AI can analyze code changes and prioritize test cases that are most likely to be affected by the changes.

**9.4 AI-Driven Defect Prediction: Anticipating and Preventing Bugs**

AI can predict the likelihood of defects in different parts of the codebase, enabling proactive testing and early bug detection. (See Chapter 10 for more detail).


**9.5 AI for Test Data Generation: Creating Realistic Test Inputs**

Generating realistic and diverse test data is crucial for effective testing. AI can automatically generate test data that covers various scenarios and edge cases.

**9.6 AI in Automated Test Execution and Reporting: Streamlining the Testing Process**

AI can automate the execution of test cases, analyze the results, and generate comprehensive reports.

* **Robotic Process Automation (RPA):**  RPA tools can automate repetitive testing tasks, such as UI testing or data entry.
* **Intelligent Test Execution:** AI can dynamically adjust the test execution sequence based on real-time feedback and results.


**Chapter 10: AI in Software Defect Prediction (Week 11)**

**(This chapter builds upon the introduction to defect prediction in Chapter 9 and includes the content from your slides).**

**10.1 Software Defect Prediction: An Overview**

Software defect prediction (SDP) aims to identify parts of a software system that are likely to contain defects. This allows for the prioritization of testing and code reviews, focusing resources on the most critical areas and improving software quality while reducing costs.  SDP models are "Just-In-Time Quality Assurance," allowing developers to address risky changes while fresh in mind.

**10.2  What is Software Defect Prediction?  Key Terminology**

* **Defect:** A static fault in the source code.
* **Error:** An incorrect internal state, the manifestation of a fault.
* **Failure:**  External, observable incorrect behavior, the result of an error.

**10.3  Machine Learning for Defect Prediction**

Machine learning (ML) is the core technology driving SDP. It involves training algorithms on historical data to learn complex patterns and predict the likelihood of defects in new code.


**10.4  Types of Machine Learning**

* **Supervised Learning:**  The algorithm is trained on labeled data (examples with known outcomes). Common algorithms include Naïve Bayes, Logistic Regression, and Support Vector Machines.  Examples of applications include advertisement popularity prediction, spam classification, and face recognition.
* **Unsupervised Learning:**  The algorithm learns from unlabeled data, identifying patterns and clusters.  This is useful for exploring data and discovering hidden relationships. Applications include recommender systems and grouping user logs.
* **Reinforcement Learning:**  The algorithm learns through trial and error, receiving rewards or penalties for its actions. This type of learning is well-suited for problems where the optimal solution is not known beforehand. Used for video games, industrial simulations, and resource management.


**10.5 Software Metrics for Defect Prediction**

SDP relies on various software metrics as input to ML models.  These metrics can be extracted from the codebase, version control systems, bug tracking systems, and other sources. These software metrics can be classified into two main categories: code metrics and process metrics. Code metrics further include size oriented, complexity oriented, and object oriented metrices. Common metrics include lines of code (LOC), lines added/deleted, number of developers modifying files, and developer experience. (Full list of metrics and definitions as provided in your slides - Chapter 8)

**10.6 Building a Defect Prediction Model: A Step-by-Step Approach**

1. **Data Acquisition:** Collect historical data from various sources, including version control systems, bug tracking systems, and code analysis tools.
2. **Data Preprocessing:** Clean the data, handle missing values, and normalize or standardize the data.
3. **Feature Selection:** Select the most relevant metrics for the prediction model.
4. **Model Training:** Train a machine learning algorithm on the prepared data. Examples include:
    * Naive Bayes
    * Logistic Regression
    * Extreme Gradient Boosting (XGBoost)
5. **Model Evaluation:** Evaluate the performance of the model using appropriate metrics, such as accuracy, precision, recall, and F-measure. (Example code for each algorithm as provided in your slides).
6. **Model Deployment:** Integrate the trained model into the development process to provide real-time defect predictions.


**10.7 Model Results and Evaluation: Measuring Prediction Accuracy**

The accuracy of a prediction model is crucial.  Common evaluation metrics include:

* Accuracy: The overall percentage of correctly classified instances (defective or clean).
* Precision: The percentage of correctly predicted defects out of all predicted defects.
* Recall: The percentage of correctly predicted defects out of all actual defects.
* F-measure:  The harmonic mean of precision and recall.


**10.8 Tools and Datasets for Defect Prediction**

There are various tools and datasets available for building SDP models:

* **Tools:**  Examples include PROMISE repository tools (Bugzilla dataset).
* **Datasets:** Publicly available datasets, such as the PROMISE repository and NASA datasets, can be used for training and evaluating models. Example: Bugzilla dataset (as shown in your slides) and steps of model building using different machine learning techniques.


**Chapter 11: Model Checking (Week 13)**

**(This chapter includes the content from your slides).**

**11.1 Introduction to Model Checking: Automated Verification**

Model checking is a formal verification technique used to ensure that a system behaves as expected under all conditions.  It involves systematically exploring all possible states of a finite-state model and checking if they satisfy specified properties.

**11.2 What is Model Checking?**

Model checking is an automated technique for verifying finite-state systems against formal specifications.  It ensures that the system behaves as expected under all conditions. It is used in various applications, including protocol verification, safety-critical systems, and distributed systems.  Examples include verifying autopilot behavior in aviation systems, ensuring reliable data transmission in network protocols, and checking designs for correctness in hardware verification.

**11.3 Key Concepts in Model Checking**

* **Finite-State Models:** Represent systems as state machines or transition systems. These models have a finite number of states and transitions between states. They model the system's behavior and possible execution paths. Key components include states (configurations), transitions (changes between states), and labels (describing properties). For example, a traffic light controller can be modeled with states (Red, Yellow, Green) and transitions defining how the lights change.
* **Temporal Logic:**  A formalism for reasoning about sequences of states or events over time.  Used to specify and verify dynamic behaviors of systems. Two main types:
    * Linear Temporal Logic (LTL): Focuses on sequences of states.  Example: "Eventually a request is granted."  Key operators include X (Next), G (Globally), F (Finally), and U (Until).
    * Computation Tree Logic (CTL): Considers branching possibilities. Example: "In all possible paths, a request is eventually granted."  Key operators include path quantifiers (A - For All Paths, E - Exists a Path) and state operators (X, G, F, U).

**11.4 Components of Model Checking**

* **Input:**
    * A formal model of the system (e.g., state diagram, transition system).
    * Temporal logic specifications of the desired properties.
* **Output:**
    * Verification result (pass/fail).
    * Counterexamples demonstrating violations of the properties. This helps in debugging.
* **Challenges:**
    * **State Explosion Problem:**  The number of states can grow exponentially with the system's complexity, making it challenging to explore all possible states within reasonable time and memory limits.

**11.5 Tools for Model Checking**

* SPIN:  Focuses on LTL specifications.
* NuSMV:  Works with both CTL and LTL.
* UPPAAL:  Used for real-time systems.


**11.6 Demo: Model Checking a Simple Problem (Traffic Light)**

(As described in your slides - includes defining states, transitions, and properties, followed by verification using a tool like SPIN)

**11.7 Case Studies:**

* **Expense Manager System:** (As described in your slides - includes use case, system model, specifications, and verification result.)
* **Elevator System:** (As described in your slides - includes states, transitions, LTL properties, and a state diagram.)
* **Automated Warehouse System:** (As described in your slides - includes key safety and liveness properties.)
* **Robot-Enabled Warehouse System:** (As described in your slides - includes system behavior, FSM, and questions on formulating safety and liveness properties.)
* **Traffic Control System:** (As described in your slides - includes states, FSM, and questions on formulating safety, liveness, and additional properties.)
* **Distributed IoT Sensor System:** (As described in your slides - includes system description, states, FSM, and questions on formulating safety, liveness, and path-specific properties, and discussing fault tolerance and reliability.)

**11.8 Advantages and Limitations of Model Checking**

* **Advantages:**
    * High level of automation.
    * Guarantees correctness for finite models.
    * Provides counterexamples for failed properties, aiding debugging.
* **Limitations:**
    * Scalability (state explosion problem).
    * Requires expertise for modeling and specifying properties.
    * Limited to finite-state systems.

**11.9  Future Directions in Model Checking**

* Integration with AI/ML for scalable solutions.
* Application in cyber-physical systems.
* Advancements in symbolic methods and abstraction techniques.

**11.10  Differences between LTL and CTL** (As provided in your table).

Key Differences between Linear Temporal Logic (LTL) and Computation Tree Logic (CTL)**

| Feature          | LTL                                       | CTL                                                    |
|-------------------|--------------------------------------------|---------------------------------------------------------|
| **Time Model**   | Linear-time: Considers a single execution path.  | Branching-time: Considers all possible execution paths.  |
| **Path Quantifiers** | Implicit: Formulas apply to *all* paths.       | Explicit: Uses `A` (for all paths) and `E` (exists a path). |
| **Operators**     | Temporal operators (X, F, G, U) apply directly to propositions. | Path quantifiers (A, E) are paired with temporal operators (X, F, G, U). |
| **Expressiveness** | Expresses properties about a *single* path.   | Expresses properties about *multiple* paths and the branching structure of the system. |
| **Suitable for...** | Verifying properties along a specific execution sequence. Useful when the order of events is critical.  | Verifying properties that hold across all possible futures or at least one possible future. Useful for concurrent and non-deterministic systems. |
| **Example: "Eventually, a request is granted."** | `F(granted)` -  Eventually, on the current path, the request will be granted. | `AF(granted)` - On *all* paths, the request will eventually be granted. <br> `EF(granted)` - There *exists* a path where the request will eventually be granted. |
| **Example: "Always, if a request is made, it is eventually granted."** | `G(request -> F(granted))` - Always, on the current path, if a request is made, it will eventually be granted.  | `AG(request -> AF(granted))` - On all paths, always, if a request is made, it will eventually be granted (on all branches from that point). <br> `AG(request -> EF(granted))` -  On all paths, always, if a request is made, there exists some path from that point where it is eventually granted. |


More tables:


**Table 1: Software Testing Levels**

| Test Level | Focus | Objectives | Techniques |
|---|---|---|---|
| Unit Testing | Individual components (functions, methods, classes) | Verify the smallest units of code work in isolation | White-box testing, JUnit, Mocking |
| Integration Testing | Interactions between components | Verify components work together correctly | White-box and black-box testing |
| System Testing | Fully integrated system | Verify the entire system meets requirements | Black-box testing, performance testing, security testing |
| Acceptance Testing | User needs and acceptance criteria | Validate the system is ready for release | Black-box testing, UAT, operational acceptance testing |


**Table 2: Software Metrics Categories and Examples**

| Metric Category | Description | Examples | Tools |
|---|---|---|---|
| Product Metrics | Characteristics of the software product | Size, complexity, reliability, maintainability | LOC, Cyclomatic Complexity, Defect Density, Radon |
| Process Metrics | Effectiveness and efficiency of the development process | Effort, schedule adherence, defect detection rate | Code Churn, Code Ownership |
| Project Metrics | Overall progress and success of the project | Earned value, cost variance, customer satisfaction | Project management tools |
| Code Metrics: Size-Oriented | Size of the codebase | Lines of Code (LOC), KLOC | Code counters |
| Code Metrics: Complexity-Oriented | Complexity of the code | Cyclomatic Complexity, Halstead Metrics | Static analysis tools |
| Code Metrics: Object-Oriented | Characteristics of object-oriented code | Inheritance Depth, Coupling Between Objects | Code analysis tools |
| Test Metrics: Structural Coverage | Extent to which tests exercise code structure | Statement Coverage, Branch Coverage, Path Coverage | Code coverage tools |


**Table 3: Machine Learning Types for Defect Prediction**

| Type | Description | Algorithms | Applications in SDP |
|---|---|---|---|
| Supervised Learning | Learns from labeled data (examples with known outcomes) | Naïve Bayes, Logistic Regression, Support Vector Machines, XGBoost | Predicting defect-prone modules or components |
| Unsupervised Learning | Learns from unlabeled data, finding patterns | Clustering algorithms | Exploring defect data, identifying clusters of similar defects |
| Reinforcement Learning | Learns through trial and error, receiving rewards or penalties | Q-learning, Deep Reinforcement Learning | Optimizing testing strategies, automatically learning which tests are most effective |



**Table 4: Roles in a Formal Software Review (e.g., Fagan Inspection)**

| Role | Responsibilities |
|---|---|
| Manager | Decides on executing reviews, allocates resources |
| Moderator | Leads the review meeting, facilitates discussion |
| Author | Presents the artifact, addresses reviewer comments |
| Reviewer/Inspector | Examines the artifact, identifies defects |
| Scribe/Recorder | Documents defects and decisions |


**Table 5: Key Components of a Test Case**

| Component | Description |
|---|---|
| Test Case ID | Unique identifier |
| Test Scenario | High-level description of the test's purpose |
| Test Steps | Detailed, numbered instructions |
| Test Data | Input values used for the test |
| Expected Result | Anticipated outcome |
| Actual Result | Observed outcome |
| Pass/Fail Status | Whether the actual result matches the expected result |
| Preconditions | Conditions that must be true before the test |
| Postconditions | Conditions that will be true after the test |


**Table 6:  Linear Temporal Logic (LTL) Operators**

| Operator | Description | Example |
|---|---|---|
| X (Next) | The next state satisfies... | X(p) - p is true in the next state |
| G (Globally) | Always satisfies... | G(p) - p is always true |
| F (Finally) | Eventually satisfies... | F(p) - p will be true at some future state |
| U (Until) | Condition holds until... | p U q - p holds until q becomes true |


**Table 7: Computation Tree Logic (CTL) Operators**

| Operator | Type | Description | Example |
|---|---|---|---|
| A | Path Quantifier | For all paths... | AG(p) - p is true in all states on all paths |
| E | Path Quantifier | There exists a path... | EF(p) - there exists a path where p is eventually true |
| X | State Operator | The next state satisfies... | AX(p) -  p is true in the next state on all paths |
| G | State Operator | Globally satisfies... (on a path) | EG(p) - there exists a path where p is always true |
| F | State Operator | Finally satisfies... (on a path) | AF(p) - p is eventually true on all paths |
| U | State Operator | Until... (on a path) | A(p U q) - on all paths, p holds until q becomes true |