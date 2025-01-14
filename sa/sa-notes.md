**Chapter Outline:**

1.  **Introduction to Software Architecture and Quality Attributes** (*Based on the overview of software architecture PDF)*
    *   This will cover the fundamental concepts of software architecture, its importance, and its relationship to business goals. It'll also define quality attributes and their importance. We'll cover the basic architecture framework, not diving too deeply.
2.  **Specifying and Classifying Quality Attributes** (*Based on the first PDF on Quality attributes*)
    *   This chapter delves into the classification of QAs into runtime and development categories, the elements of QA scenarios, and how to define them with concrete and general scenarios.
3. **Tactics for Achieving Quality Attributes** *(This should be a big chapter, covering all "Tactics" slides)*
    *   This chapter will introduce the concept of architectural tactics, including the model of how tactics influence the response, and will include sub-sections for different type of tactics and how each relates to quality attributes (Availability, Security, Modifiability, Performance, Usability).
4.  **Architectural Styles and Patterns: Software Interfaces**
    *   This chapter focuses on patterns for structuring software interfaces, including REST, RPC, client-server, layered, tiered, stateless, cacheable systems.
5.   **Architectural Styles and Patterns: Virtualization and Cloud Computing**
    * This chapter covers virtualization techniques (VMs, containers, pods, etc) and Cloud computing patterns (load balancers, stateful and stateless systems).
6.  **Architectural Styles and Patterns: Mobile Systems**
    * This will focus on mobile systems design and the specific architectural challenges in this domain
7. **The Attribute-Driven Design (ADD) Method** (*Based on the design process PDF*)
    * A detailed discussion on the ADD method, including the roadmap for each type of system (greenfield, brownfield, novel), and the process of choosing, implementing, and refining design decisions and techniques.
8.  **Advanced Topics and Case Studies**
    * This chapter will provide an opportunity to address advance topics such as a deeper dive into performance and security. It will also include case studies or examples to put it all together.



## Chapter 1: Introduction to Software Architecture and Quality Attributes

### 1.1 Defining Software Architecture: More Than Just a Diagram

Software architecture is not merely a collection of interconnected components; it's the fundamental structure of a software system that dictates how it will behave, evolve, and meet the needs of its stakeholders. It is important to note that architecture is a set of structures required to reason about the system. It is not the final design blueprint, it is an *abstraction* of the system that selects certain details and supresses others. Software Architecture can be viewed from multiple perspectives: Enterprise architecture and System architecture.

*   **Enterprise Architecture:** This is a high-level view describing the structure and behaviour of an organization's processes, information flow, personnel, and subunits. It provides a broad scope within which a system resides and interacts with other areas of a business.

*   **System Architecture**: This is a more specific view that focuses on the software system itself, showing how functionality maps onto hardware and software components. The system architecture deals with the interaction with users, mapping software architecture onto a hardware architecture.

### 1.2 Key Principles of Software Architecture

*   **Business Alignment:** A core principle of software architecture is that every software system is built to satisfy the specific business goals of the organization. These goals are the main reason a software is created, and therefore, must be reflected in the overall structure and behaviour of the application.

*   **Architecture is Design but not all design is Architecture:** Architectural design is about designing a system, but not every design aspect of an application is necessarily an architectural concern. While design may touch the implementation details of an application, architecture focuses on the big-picture, large-scale and structural design aspects of a system.

*   **Every system has an architecture, but not all architecture is good architecture**: Regardless of whether the architectural decisions are explicit or implicit, all software systems will have an architecture. This also means that any system does not have a "good" or "bad" architecture, it is either fit or unfit for its own purpose.

*   **Architecture Includes Behaviors:** The architecture is more than just a static diagram of the system elements, it needs to include all of the behaviours of each element or component of the application.

### 1.3 The Three Pillars of Software Design

Software architecture is driven by three types of requirements: functional requirements, quality attributes, and constraints. All of these work together to form a well-rounded system

1.  **Functional Requirements:** As we already covered, functional requirements are the specific tasks or actions that the system needs to perform. It is the list of features that the system is intended to do.
    *   Examples include user authentication, processing payments, generating reports etc
    *  These are satisfied through proper responsibilities assigned throughout the design.
2.  **Quality Attributes (Non-Functional Requirements):** These describe *how well* the system performs its functionalities. This is the non-negotiable properties of the system.
    *   *Examples*: Performance, availability, security, and usability.
    * These are satisfied by using structures design into the architecture, including the behaviors and interactions of elements
3.  **Constraints**: These are limitations or restrictions placed on the system and include things like limited budget, technology limitation, security and privacy requirements, time-to-market pressure.
    *   These are satisfied by accepting the design decisions and reconciling it with other affected design decisions.

### 1.4 Introducing Quality Attributes

Quality attributes (QAs) are the “-ilities” of a software system that dictate its behaviour when the system is in operation or during the development process. A system can provide all functionalities that are needed, but that does not necessarily make the system a good system. In fact, if these quality attributes are not properly addressed, the system can be completely unusable.

*   **The Significance of Quality Attributes**: If functionality is about the *what*, quality attributes are all about the *how well*. These attributes determine whether a software system meets the expectations of stakeholders and how reliable, secure, usable, and adaptable it is. It helps us to create a well functioning software.

*   **Quality attributes are not "add-ons"**: They have to be factored into the system from the beginning of the design process, because to add them later may be expensive or impossible

*   **The Impact of Quality Attributes:** They significantly influence architecture and must guide design decisions from the onset.
   
### 1.5 Architectural Structures and Views

*   Architectural views represent different perspectives on the system's architecture, each emphasizing specific aspects. They are representations intended to facilitate communication among stakeholders. A view presents a coherent set of architectural elements and their relationships, as written and read by stakeholders.

*   A structure is the set of elements itself, as they exist in software or hardware. A view is an abstraction—a selection of details and a suppression of others. Many structures can be present in a software system, but no single structure constitutes "the" architecture.

Common Architectural Views:

*   **Module View**: Shows the static decomposition of the system into code and data modules. This view is often used to reason about the system's organization, build dependencies, and code reuse. It is related to how the system is structured as a set of implementation units.

*   **Component and Connector (C&C) View**: Illustrates runtime interactions between components (processes, threads, objects) and their communication mechanisms (message queues, procedure calls, shared memory). This view focuses on the system's runtime behavior and dynamic interactions.

*   **Allocation View**: Depicts the mapping of software elements to non-software elements, including hardware (processors, memory, network devices), development teams, deployment environments (cloud, on-premise), and organizational structures. This view is essential for understanding deployment, resource allocation, and organizational responsibilities.


### 1.6 Why is a Software Architecture Important?

*   **Reasoning about a System**: The most important role of software architecture is that it provides a structure and abstraction to allow for developers to reason about the system. Without a solid architecture, understanding and reasoning about the application can be daunting.
*   **Achieving Quality Attributes**: Architecture is the primary mechanism by which quality attributes are achieved. It determines how components are structured and interact to deliver these. Without proper architecture, a system may perform all functionalities, but will still be a poor system if it is too slow, keeps crashing, or is not easily upgraded.
*   **Blueprint for Development**: Software architecture also provides a high-level map and guidance for system development. It acts as a communication bridge between stakeholders and developers and guides implementation.
*   **A Starting Point**: The architecture is the starting point to address design concerns and implementation details that affect multiple parts of the system.
*   **Reuse**: Finally, a good architecture can be reused for other applications, and also allows for components of the architecture to be reused for other systems.

**Key Takeaways of Chapter 1:**

*   Software architecture is a core part of software engineering practice that needs to satisfy an organizations business goals, and needs to be evaluated for fitness for purpose.
*   Software architecture is not just a final plan, it is an abstraction of the system to be created.
*   Software design is supported by three pillars: functional requirements, quality attributes and constraints.
*   Quality attributes are about *how well* the system achieves functionalities rather than what the application *does*.



## Chapter 2: Specifying and Classifying Quality Attributes

### 2.1 Runtime vs. Development Quality Attributes

As we discussed in the previous chapter, quality attributes dictate *how well* a system performs. These can be broadly categorized into two types: those focused on system behavior during operation (runtime) and those focused on characteristics during the development phase.

1.  **Runtime Quality Attributes**

    *   These attributes describe the system when it's actively being used. They are concerned with the user’s experience, the performance of the system, and its ability to maintain a proper level of service. The goal here is to make the application *work well*.
    *   Examples of runtime quality attributes include:
        *   **Availability**: Measures how reliably the system is operational and accessible when needed. This is often expressed as the percentage of uptime. For example, a web server might need 99.999% availability.
        *   **Performance**: Assesses the system's responsiveness and speed. This is also about how efficiently the system uses its resources in terms of memory and bandwidth. For example, an online trading system would need low response time during peak hours.
        *   **Security**: Focuses on the protection of the system and its data from unauthorized access, use, disclosure, disruption, modification, or destruction. For example, a financial system requires strong encryption and authentication methods.
        *   **Usability**:  Determines how easy the system is to learn and use. This is measured by how much effort a user has to exert in order to use the system. For example, an application should have an intuitive user interface so that even non-technical users can navigate it well.
        *   **Interoperability**: Measures how well the system interacts with other systems. This is crucial in a complex software landscape where multiple applications need to work together. For example, a hotel booking system should seamlessly integrate with multiple flight booking systems.
        *   **Reliability**: Defines how dependably the system performs without failures in a given environment and under given circumstances for a period of time. For example, an autonomous car needs to perform reliably in all conditions, without fail.

2. **Development Quality Attributes**
    *   These attributes are related to aspects of the software development lifecycle. These attributes focus on making sure that the software can be changed, tested, or reused, etc. The purpose is to make the system *easy to develop, test, and evolve*.
    *   Examples of development quality attributes include:
        *   **Modifiability:** Measures the ease with which the system can be changed or adapted to new requirements or functionality. This is crucial for applications that need to evolve with new technologies or business needs. For example, a system should be designed so that it's easy to add a new payment gateway
        *   **Testability**: Assesses how easily and efficiently the software can be tested. This can reduce the testing time and costs. For example, a banking system must have easily testable code for its critical components, such as credit card payment processing or fraud detection.
        *   **Scalability**: Measures the ability of the system to handle increased workloads or user volumes. This is vital for a system to deal with growth in demand. For example, an e-commerce system should be able to scale to handle a sudden surge in website traffic on black friday.
        *   **Integrability:** Measures how easy it is to combine the system with other systems. Integrability becomes important when different components of a system or different systems must exchange information. For example, an enterprise application is required to integrate with other systems within the same organization.
        * **Reusability:** Measures the ability to reuse the architectural components of an application in new contexts. For example, a utility library can be designed to be reusable in various applications and various organizations.

**Key Takeaway:** Understanding both types of quality attributes is essential to build software that is not only functional but also high-performing, maintainable, and secure.

### 2.2  Defining Quality Attributes through QA Scenarios

As mentioned in Chapter 1, QA scenarios are critical for establishing clear and testable quality attribute requirements. A QA scenario helps by specifying the conditions under which a specific quality attribute is evaluated. A QA scenario consist of six elements: the *Source of Stimulus*, *Stimulus*, *Environment*, *Artifact*, *Response*, and *Response Measure*. Let's dive a little deeper into these aspects.

1.  **Source of Stimulus:** This is the actor or entity that initiates the action, trigger, or event in the system. Understanding the source helps to identify various types of inputs or interaction that will occur during run time. The source of the stimulus can be:
    *   **External**: These are external entities of the application, including users, other systems, or hardware interacting with the application.
        *   *Examples*: A customer logging in, another system requesting data, or a hardware failure detected by a monitoring component
    *   **Internal**: This consists of internal components of the application or the system.
       *   *Examples*: An internal function that requests data, the database initiating a backup, or a system timer triggers a background process.

2.  **Stimulus**: This is a condition or event that triggers a specific reaction from the system. It can be one of the following:
    *   A signal or action that needs to be responded to, or a state that the system will react to
    *   A situation, such as a system overload or underload, that requires a specific system response.
    *   *Examples*: User attempts to login, sensor data change, or system failure

3.  **Environment:** This is the state of conditions under which the stimulus occurs. This can be categorized as:
    *   **Normal operation:** The system functioning under typical conditions with normal workload.
    *   **Emergency mode:** System is working under high stress or high load
    *   **Degraded mode:** System working at a reduced capacity due to component failures.
    *   **Startup or Shutdown process** The system starting or shutting down.
    *   *Examples:* The environment for a user authentication could be a normal operation, while a backup could be an emergency operation

4.  **Artifact**: This identifies the component of the system being affected by the stimulus. It could be one of the following:
    *   A software component or module.
    *   A hardware element such as a processor, memory or interface.
    *   A data resource or other related persistent storage
    *   *Examples:* The artifact for a login request might be the authentication module, whereas a network fault’s artifact will be the communication channels.

5.  **Response**: This is the action taken by the system as a result of the stimulus and the environment. The response can be categorized as one of the following:
    *   Actions to mitigate the fault and return to normal operation.
    *   Actions to degrade the system gracefully to still be able to handle critical operations.
    *   Notification messages that alert stakeholders about the issue.
    *   *Examples:* A user interface displays a specific error message, a backup module taking over responsibilities, a system shutting down safely or a module logging the errors

6.  **Response Measure**: These metrics describe *how well* a system reacts to a specific stimulus. It provides a concrete, measurable outcome to evaluate if the systems response is acceptable. Response measure is defined by:
    *  Numeric values, such as latency, number of concurrent requests etc.
    *  Binary outcomes, such as success or fail.
    * *Examples*: Time taken to log in, the amount of available memory during peak usage, or time taken to backup.

**Key Takeaway:**  By considering all six parts of a QA scenario, we can thoroughly define the quality attribute requirements for a system and also ensure that they're testable.

### 2.3  General vs. Concrete QA Scenarios

As we discussed in Chapter 1, quality attributes are typically captured by writing a general or concrete scenario. This section will expand on the difference between these two:

*   **General Scenarios**:
    *   These are system-independent and are used to describe and communicate overall quality requirements.
    *   They do not deal with specific use cases of a particular application, instead, they describe the abstract intention of a specific QA.
    *   It should be noted that general scenarios will not be directly tested since they are not testable.
    *   General scenarios are useful for communicating high-level objectives.
    *   *Examples*: A general availability scenario might state that "The system must remain operational under normal operating conditions," which provides broad requirements for availability, but nothing specific. A general performance scenario might say, "The system should respond rapidly to user requests," or “The system needs to be scalable".
*   **Concrete Scenarios**:
    *   These are system-specific and specify requirements that are testable.
    *   It is not compulsory for concrete scenarios to have all six parts, it depends on how detailed we want to be.
    *   The purpose is to provide a specific use case to test the system's ability to satisfy the QA requirement.
    *   Concrete scenarios are required during the design and implementation phase to test and verify if the system satisfies a quality attribute.
    *   *Examples:* A concrete availability scenario might state, "The login module must be available for 99.9% of all weekdays." A concrete performance scenario can be, "The checkout page should load within 2 seconds at a peak traffic of 1000 user requests per minute”.

**Key Takeaway:** While general scenarios help understand the high level quality of the system, a concrete scenario is crucial when making design choices for the system to be tested.

### 2.4 Examples of General and Concrete Availability Scenarios

Here are two examples that highlight the difference between general and concrete scenarios for the *availability* quality attribute:

#### 2.4.1 General Availability Scenario

| Source of Stimulus       | Stimulus       | Environment                                       | Artifact                                | Response                                                                                                       | Response Measure                                                                                                     |
|--------------------------|-----------------|----------------------------------------------------|-----------------------------------------|---------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
| Internal / External: people, hardware, software, physical environment    | Fault: omission, crash, incorrect timing, incorrect response | Normal Operation, startup, shutdown, repair mode, degraded operation, overloaded operation | Processors, communication channels, persistent storage, processes | Prevent fault from becoming failure; detect, log, notify; recover; disable source, or be unavailable, fix/mask, degrade mode. | Time or Time Interval System should be available, Availability percentage, time in degraded mode, repair time, faults system handles. |

#### 2.4.2 Concrete Availability Scenario

| Source of Stimulus | Stimulus        | Environment    | Artifact | Response                | Response Measure |
|--------------------|-----------------|----------------|----------|-------------------------|------------------|
| Heartbeat Monitor  | Server Unresponsive | Normal operation | Process  | Inform Operator, Continue to Operate | No Downtime       |

**Key Takeaway**: It is important to note how much more specific a concrete scenario is when compared to a general scenario.

### 2.5 Key Takeaways

*   Quality attributes can be classified as runtime or development.
*   A QA scenario can help define a quality attribute requirement.
*   A QA scenario has six parts: Source of stimulus, stimulus, environment, artifact, response, and response measure.
*   There are two types of scenarios: general and concrete scenario. A general scenario helps you to describe the concept of the QA while a concrete scenario is a way to test your system.


## Chapter 3: Tactics for Achieving Quality Attributes

### 3.1 Introduction to Architectural Tactics

As we've established, achieving quality attributes is not accidental; it requires purposeful design choices. Architectural tactics are the design decisions that architects make to influence the quality attributes. These are specific design techniques which are used to address a single concern or response. They are the actions we take in an architecture to achieve a specific quality response.

* **Tactics and Design Decisions:** Architectural tactics, are design choices that are intended to make a single impact (or response). They focus on how a system responds to specific issues or problems that could otherwise cause it to break a certain QA. These tactics are the building blocks for building quality attributes into your application. They also form the basis of a "design vocabulary" for architects to communicate and build applications efficiently.

* **Tactics as "Tools":** A tactic can be thought of as a "tool" in an architect’s toolbox, and they are not meant to work on their own. They are often combined and integrated to create more complex responses from the system.

* **Tactics and Quality Response:** These tactics are intended to control the response from the system as a result of a given stimulus. They ensure that quality attributes can be predictably achieved in software applications

### 3.2 The Tactic Model

To understand the role of tactics, let's revisit the simple model from Chapter 1:

![Alt text](https://i.imgur.com/fV5k95A.png)

*   The *Stimulus*: Represents the initiating event or condition that triggers the system.
*   The *Tactic*: Acts as a control mechanism that is implemented in a component, the architecture, or system, that influences how the system handles a response.
*   The *Response*: Is the observable action or result achieved by the system due to the presence of a specific architectural tactic.

### 3.3 Categorizing Tactics

Tactics can be categorized by the primary quality attribute they address. It is important to note that different kinds of tactics are used to control one particular aspect of an application, and that it is often difficult to decouple these tactics, as there are interrelations between them, although they do address one main quality attribute. They provide solutions to problems such as, "How do we make a system more available?"

In our context, the main focus is on these specific QAs: availability, performance, usability, security, and modifiability.

### 3.4 Tactics for Availability
Availability ensures that the system is consistently operational when needed and that it provides continuous service. To make a system available when it experiences a fault, it needs to detect the fault, then recover from the fault, and put in systems to prevent such faults from recurring.

#### 3.4.1 Fault Detection Tactics
 These tactics are implemented to detect faults in a system, they help to recognise when something has gone wrong:

*   **Ping/Echo**: This tactic involves exchanging asynchronous request/response message pairs between nodes in a system. It is used to determine if a connection or a component is still alive and responding. The ping is initiated by a monitoring component that waits for the echo message. If the echo is not received within a set timeout, the component is considered as failed or timed out.

*   **Monitor**: This component is used to observe the health and state of another part of the system. Monitors may initiate self-tests, or detect missed heartbeats or faulty timestamps. It also helps to coordinate other tactics within the fault detection category to detect malfunctioning components. A specialized type of monitor is a *watchdog*, that is tasked to observe specific things within the system.

*   **Heartbeat**: This is a fault detection mechanism that employs a regular, *periodic* exchange of messages between a monitor and the component being monitored. This provides a very quick way for the monitor to understand if the other component has failed.

*   **Timestamp**: This tactic is used to detect incorrect sequences of events. A timestamp is the act of assigning a local time clock to an event immediately after it occurs. Timestamps can be simple sequence numbers as well.

*   **Sanity Checking:** This tactic is used to check if the outputs or operations of a component are valid or reasonable. The sanity check is based on the knowledge of internal design of the application. They are generally done at the interfaces of components to determine if data is being handled appropriately.

*   **Condition Monitoring**: This tactic involves checking the operational conditions of a component, process or device. For example, using checksum calculations to verify data integrity.

*  **Voting**: This technique uses multiple identical or different components to perform the same function, then a voter system determines if the output is correct by observing all components outputs. Triple Modular Redundancy (TMR) is a form of voting with three identical components doing the same thing. There are three types of voting:
   * **Replication**: Uses exact clones or identical components that receive the same input and produce the same output. This can protect against random hardware failures, but does not protect against implementation errors.
    *   **Functional Redundancy**: It uses components that are diversely implemented but have the same functional intention. The components can be different, but for a given input, it should be able to produce the same output.
    *   **Analytical Redundancy**: Components can have different inputs, outputs, and different internal design. This is used when some input sources may be unavailable, or to detect for specification error. The key aspect is that they solve the same problem, even if their implementations are completely different. For example, there can be multiple ways to determine the altitude in an airplane.

* **Exception Detection**: This involves identifying conditions that disrupt the normal execution flow. This can be done by three different approaches:
   *   **System Exceptions**: Detecting faults such as division by zero, bus faults or illegal instructions
    *   **Parameter fence**: Detects if an object has been over-written due to wrong memory handling
    * **Timeout:** Raising an exception when it takes too long to respond to an event, or a component has taken to long to meet its timing constraint.

*   **Self-Test**: Components runs procedures to test itself, to check if it is still in good health. A self-test can be initiated by the component itself, or invoked by the monitor.

#### 3.4.2 Fault Recovery Tactics

These tactics are activated when a fault is detected, and their aim is to get the system back to normal operation:

**Preparation and Repair**
 These tactics help to restore the component by either introducing redundancy or re-trying computations.

*   **Active Redundancy (Hot Spare)**: All nodes (both active and spares) in a protection group receive and process identical inputs in parallel. Redundant spares are kept in synchronous state with active nodes and can take over in milliseconds. This is often used in critical applications that requires very quick switch over. A common example is "1+1" redundancy, where there is one active node, and one hot spare.

*   **Passive Redundancy (Warm Spare):** The active component processes input traffic, while providing updates of the application’s state periodically to the redundant spare components. It’s used when high-speed failover is not needed, such as when the switch-over time can be in seconds instead of milliseconds.

*   **Spare (Cold Spare):** Redundant spares remain out of service until a fail-over occurs. A power-on-reset procedure is initiated on the redundant spare when a fault occurs and before it takes over the application. This is used in cases where speed of switchover is not important.

*   **Exception Handling:** The way an exception is handled depends on the programming environment. This can be a simple return code, or exception classes which allows for more detailed error information to be passed.

*   **Rollback:** When a failure is detected, the system reverts back to a previously known good state (a checkpoint). After this, the system continues from this point onwards. This can often be combined with active or passive redundancy. After a rollback the spare can be promoted to active status.

*   **Software Upgrade**: Aims to achieve in-service upgrades without affecting the application. This can be done by:
    *   **Function patch:** In procedural programming, the updated function is loaded by the incremental linker/loader to a pre-allocated target memory
    *   **Class patch:** In object-oriented code, classes have a backdoor to dynamically add member data and functions.
    *   **Hitless In-Service Software Upgrade (ISSU):** Uses active and passive redundancy to achieve non-service-affecting upgrades to software and associated schema.

*   **Retry**: Assume that the fault is transient, and retrying the operation may be sufficient to overcome the issue. The retry is done after a certain amount of delay.
     *   *Example*: Retrying a network call can be beneficial since a faulty network can quickly recover.

*   **Ignore Faulty Behavior:** This tactic involves identifying and ignoring messages or other information from a specific source, when those are deemed spurious.
    *   *Example:* When a server detects that it is experiencing a denial of service attack, it may ignore that data from the attacker.

*   **Degradation:** This tactic helps to maintain the most critical systems function, while dropping less critical function. The system will continue to operate with a reduced feature set, instead of completely shutting down.

*   **Reconfiguration:** This tactic re-assigns responsibilities to remaining components after a component fails. It helps to maintain as much functionality as possible in the system.
 **Reintroduction**
 These tactics deal with reintroducing the component back into the system.

*   **Shadow**: A component that has failed, or upgraded, operates in "shadow mode" before going back to an active role. The shadow component will be observed for a period to determine if there are any issues, and its state will be repopulated incrementally during this period.

*   **State Resynchronization**: This is used with active and passive redundancy. In the case of hot spare, the active and standby components are kept in sync all the time, while warm spares are kept synchronised periodically.

*   **Escalating Restart**: A system restarts components at different granularities, so as to minimize the level of service that is affected. The more severe the issue, the more components are restarted.
    *   *Example:* A system may support four levels of restart from level 0 (where all child threads are restarted), up to level 3 (where all the components of the application is reloaded)

*  **Non-Stop Forwarding (NSF)**: This tactic is based on router design, where functionality is split into two parts: control plane (managing connectivity) and data plane (routing data from source to destination). The data plane continues to work even when the supervisory plane fails, and when a supervisor comes back online it will use graceful restart to re-establish the connection with the control plane.

#### 3.4.3 Fault Prevention Tactics
 These tactics help to prevent a fault from even happening in the first place.

*   **Removal from Service/Software Rejuvenation**: This tactic temporarily takes a component out of service, to allow the system to be reset and remove latent faults, such as memory leaks or fragmentation.

*   **Transactions:** This tactic utilizes transaction semantics for asynchronous messages in distributed components. The messages must be atomic, consistent, isolated and durable (the "ACID" properties). The two-phase commit protocol (2PC) is a specific implementation.

*   **Predictive Model:** This is used to monitor the health of the system and to predict possible faults by observing performance metrics.
     *  *Examples:* Session establishment rate, statistics of process states.

*   **Exception Prevention:** Utilizes programming languages and programming tools to prevent exceptions from happening.
     *   *Examples*:  Exception classes, smart pointers.

*   **Increase Competence Set:** Designing components to handle more kinds of faults as a normal operation. The component is specifically designed so that it’s competent to operate within many states.

### 3.5 Tactics for Performance

Performance is about the timeliness and efficiency of the system. There are two main categories when it comes to performance: how much time a system spends doing work, and the time a system waits to do work.

*   **Processing Time:** The time a system takes when actively responding to a stimulus, where it uses system resources like CPU, memory and bandwidth.
*   **Blocked Time:** The time that a system waits for resources to become available or dependencies to be resolved.

With this in mind, there are two strategies to address these issues: by controlling the demand for resources, and by managing the resources themselves.

#### 3.5.1 Control Resource Demand Tactics

These tactics focus on limiting or controlling how a system uses resources.

*  **Manage Sampling Rate**: Reducing the frequency with which a data stream is captured. For example, using a lower resolution camera to send images instead of a higher resolution camera.
*   **Limit Event Response**: Limiting the rate at which the system processes events when there is a burst of messages.  The incoming requests will then be placed in a queue, until it can be properly handled. For example, when there is a burst of login requests, the login process will be limited so that the system does not get overwhelmed.
*   **Prioritize Events**: Imposing a priority scheme that dictates the order in which the events are processed. High priority events are processed first, and low priority events might be ignored if there are not sufficient resources available to handle them. For example, a system can prioritize a fire alarm before dealing with a change in temperature in a building.
*   **Reduce Overhead**: This means to reduce computational overhead by removing extra steps to process events. The overhead can be caused by, but not limited to, the use of intermediaries and separation of concerns. For example, locating cooperating components on the same server can reduce the time delay of network communication, or the system periodically clearing resources that have become inefficient.
*  **Bound Execution Times**: Limiting how much time a component spends to respond to an event. This limits how much resource can be consumed by an event.

*  **Increase Resource Efficiency**: Improving algorithms in critical parts of the application to reduce resource usage and processing time. The focus is on streamlining how resources are being used.

#### 3.5.2 Manage Resource Tactics

These tactics are focused on managing and enhancing the resources available to the system.
*  **Increase Resources**: Increasing the resources of the system, such as adding more memory, faster CPUs, faster networks to improve system performance.
* **Introduce Concurrency:** Processing different parts of a system in parallel to reduce overall blocked time and achieve faster response times
   *  *Examples*: Choosing scheduling policies, using different priority levels.
*   **Maintain Multiple Copies of Computations:** Duplicating services such as web servers, microservices, to reduce contention and increase availability. This is typically implemented with a load balancer that distributes the load across available servers.
*   **Maintain Multiple Copies of Data (Caching):** Duplicating data on storage with different access speeds to reduce contention when multiple access requests arrive. The copies must be synchronized and the data to be cached needs to be appropriately selected.
    *   *Example*: Local copies of frequently used data can be stored locally, and infrequently used data can be stored remotely.
*   **Bound Queue Sizes:** Setting a maximum number of requests that can be queued in the system to protect against resource exhaustion when there is a surge of requests.
*   **Schedule Resources:** Using scheduling strategies for processors, buffers, and networks to ensure that resources are efficiently used. Examples include using different priority levels, and using different scheduling systems (e.g., round-robin, static scheduling, dynamic scheduling, etc.)

### 3.6 Tactics for Usability

Usability is about making the system easy for users to accomplish their tasks. Architectural tactics for usability emphasize the system’s support for user interaction and workflow.

#### 3.6.1 Support User Initiative Tactics

These tactics allow users to take the initiative and control the flow and behaviour of the system by providing feedback and allowing for suitable responses

*   **Cancel:** This allows the user to terminate or interrupt an operation. The system should be able to terminate the operation, free up any resources, inform all involved components and resume normal operation.
*   **Undo:** This tactic allows the system to revert to a previously known state. The system should maintain enough information about its states so that it can reverse an operation. Note that some operations are not easily reversed such as ringing a bell.

*  **Pause/Resume**: This enables users to stop a long running process, temporarily free resources, and continue later. The system should be able to release the resources to be temporarily re-allocated.
*   **Aggregate:** Enables users to perform a set of repetitive operations as a single action. This allows the user to perform a function on many objects at once, rather than repeatedly selecting each object.

#### 3.6.2 Support System Initiative Tactics

These tactics are about enabling the system to predict the user's needs, to provide support. They help to determine what the system *thinks* or model of its behaviours or user's intentions. These tactics require a certain kind of model or data to be maintained by the system.

* **Maintain Task Model**: By maintaining a model of the tasks the user is attempting, the system can determine the context of the user action to provide assistance.
* **Maintain User Model**: This requires a representation of the users knowledge of the application, behaviors, and their preferences. Based on the user’s model the system can automatically provide information or suggestions to guide the user through the application.

*   **Maintain System Model**: This tactic involves maintaining an explicit model of the system itself to determine the expected behavior. This helps the system predict behaviours, such as a progress bar indicating how long it will take to complete an operation.

#### 3.6.3 UI Separation

Finally, it's important to also separate the UI, which is a UI pattern, which increases both modifiability and usability. UI separation allows UI choices to be made without re-coding, and minimizes ripple effects when UI changes occur. This is achieved by localizing UI responsibilities and restricting the dependencies to the UI layer. By separating UI, the application can change a UI without having to refactor other parts of the application.

**Key Takeaway:** By implementing support for both user and system initiatives, a system can have a good usability experience. It also helps to achieve both modifiability and usability.

### 3.7 Tactics for Security

Security is crucial to protecting the integrity of the system. Security tactics address risks and vulnerabilities. The approach is categorized based on what needs to be done: to prevent an attack from happening, to resist an attack if it has happened, to react to an attack and to recover from an attack after it has completed.

#### 3.7.1 Detect Attacks

*   **Detect Intrusion**: Monitoring the system to find if any system breach has occurred, such as unauthorized access.
*   **Detect Service Denial:** Identifying an attack that may render the system or service unusable.
    *   *Example:* A denial of service (DOS) attack.
*   **Verify Message Integrity**: Check that messages or data has not been tampered with during transmission.
    *  *Example*: Using hash algorithms to verify the integrity of data transferred.
*   **Detect Message Delay**: Identify if data is being delivered with significant delays, which can be a sign of an attack.

#### 3.7.2 Resist Attacks

*   **Authenticate Actors**: Require users and systems to provide identity verification to access the system. This can be through password authentication or more complex authentication systems using multiple factors.
*   **Authorize Actors**: After authentication, the system authorizes user actions based on a set of roles and permissions. This limits what an authenticated user can do.
*   **Limit Access**: Control the amount of access that any user has to the system. This is based on a least-privilege approach where the minimum access possible will be given to a user to accomplish a task.
*   **Limit Exposure:** Limit the amount of data or resources that can be accessed. For example, limit the visibility of data by giving access only to data that is required for a certain role in the organization.
*   **Encrypt Data**: All data must be encrypted at rest and in transit, to ensure confidentiality.
*   **Separate Entities:** Grouping software components with similar security level, such as grouping all the core security components separately from the rest of the application so that any breach on other parts of the application will not compromise security.
*   **Change Default Settings:** Always change default passwords and usernames so that security is not compromised through default credentials.

#### 3.7.3 React to Attacks
*  **Revoke Access**: If unauthorized behaviour is detected, the system revokes all access to the resource or service.
*  **Lock Computer**: Lockdown user's computer if it’s at risk of unauthorized access.
*  **Inform Actors:** Alert users and other concerned parties about a security breach or potential threat.

#### 3.7.4 Recover from Attacks
* **Maintain Audit Trail**: Maintain records of system operations which can be used for root cause analysis during and after a breach.
*   **Restore**: Restore or return the system to a safe operational state after an attack or compromise. This could be restoring data from backup or reverting the system to a known good state.

### 3.8 Tactics for Modifiability

Modifiability allows for the system to be easily changed and evolved in response to new or changed requirements. The goal of these techniques is to address the problem of *change*, and provide ways for the application to be more flexible.

* **Reduce the Size of a Module:** Reducing the size of individual modules to improve readability and reduce complexity and reduce overall development time of a module. If the module has multiple responsibilities, the module will need to be split.

* **Increase Cohesion** This tactic ensures that all elements within a module has high semantic coherence and can be viewed as logically grouped together. Increasing semantic coherence within a module will help to manage changes, since changes will be required to less parts of the module. It can also reduce the impact when changes occur. Cohesion should apply within individual modules, as well as with co-location of module responsibilities.

*   **Reduce Coupling:** Reducing the dependency or tight-coupling between modules reduces the ripple effect when changes are made. Changes in one module should not affect other modules. Decoupling also enables the system to be changed independently. This can be achieved by one of the following strategies:
    *   **Encapsulation:**  Making sure that modules have private state so that only they have direct access to the data, reducing dependencies and coupling.
    *   **Using an intermediary:** Adding an intermediary component between the interacting components, such as a mediator or a broker, reduces coupling between them.
    *   **Restrict Dependencies:** Using the minimum possible number of dependencies to achieve specific goals. Limiting dependencies means changes to one module will have less chance of affecting another module.
* **Refactor**: Changes of code without changing the behaviour of the application to be more clear and efficient.
*   **Abstract Common Services**: By identifying common services that are shared by components, these can be abstracted out into a reusable component, that is easier to maintain and evolve.
*   **Defer Binding**: This tactic is about separating the decision points of a software, so that decisions can be made at runtime or at deployment. This allows the system to be changed more easily when they are not statically linked.
   *   *Example:* UI can be changed without requiring re-code.

### 3.9 Key Takeaways

*   Architectural tactics are the tools used to influence a system’s responses to achieve the desired quality attributes.
*   Tactics can be categorized based on what qualities they primarily influence.
*   Tactics for availability focus on detecting, recovering from, and preventing faults.
*   Tactics for performance aim to control resource demands and manage resources efficiently.
*   Tactics for usability enhance the user experience by supporting user and system initiatives.
*   Tactics for security help to protect a system and its data from threats and unauthorized access.
*   Tactics for modifiability ensure that the system can evolve to support changing requirements.

## Chapter 4: Architectural Styles and Patterns: Software Interfaces

### 4.1 Introduction to Software Interfaces

Software interfaces are the crucial boundaries across which different parts of a system, or even different systems, interact. They define how components communicate and coordinate with each other. A well-designed interface is the key to building modular, scalable, and maintainable software. It is where two or more components will exchange information.

*   **Interface as a Contract:** An interface establishes a contractual specification that allows elements to collaborate and exchange information. The interface defines all the methods, types, data structures and protocols used for information exchange.

*   **Types of Interfaces**: When building software, there are two major types of interfaces that needs to be considered:
    *   **External Interfaces**: These are interfaces between your system and other systems and users. It specifies how your application will communicate with the outside world.
    *   **Internal Interfaces**: These are interfaces between the different components of your application. This is how the internal workings of your application will interact with each other.

*   **Beyond Code:** It is also important to note that interfaces can also represent physical or hardware boundaries, such as network interfaces or other communication channels.

### 4.2 Key Concepts and Terminology in Interfaces

1.  **Interface**:  This is a boundary across which elements meet and interact. It is a well-defined way through which software components exchange information. An interface is a contract that defines how two components will interact, including the method signature, parameters and return types.

2.  **Element:** This is the software component or module with which the interface interacts. It is the part of a system that offers an interface to other components.

3.  **Actors**: These are the other elements, users, or systems that interact with the element through its interfaces. These are the entities that will call or use the interfaces.

4.  **Resource:** This is a construct or data that provides the points of direct interaction with an element, such as input/output arguments or return values. They are the information which is being exchanged through an interface.

### 4.3 Principles of Interface Design

To create effective and robust interfaces, you must follow a few key principles:

1.  **Principle of Least Surprise:** An interface should behave consistently with the expectations of the actors that use it. The interface should do what the user expect that it will do. This means, it should conform to the common established practices, so that the users are not surprised by how it works.

2.  **Small Interfaces Principle:** If two elements need to interact, they should exchange as little information as possible. This reduces coupling between them, making them independent and easier to modify or test.
    * The more information is being exposed, the more potential interactions there are, and the more complex the system becomes.

3.  **Uniform Access Principle**: The internal details should be abstracted and not visible to the outside world through the interfaces.
    * Users of an interface should only interact through the prescribed API, without knowing the details of the internal components that implement the interface.

4.  **"Don't Repeat Yourself" (DRY) Principle**: Interfaces should provide a small and composable set of primitives that can perform the required operations, rather than multiple redundant ways of accomplishing the same thing. If there are multiple ways of doing the same thing, it creates redundant code paths that are not easy to manage or test.

### 4.4 Common Software Interface Styles

Software systems rely on a number of established interface styles that help developers design and build system. In general we will be focusing on two main interface styles: Remote Procedure Call (RPC) and Representational State Transfer (REST)

#### 4.4.1 Remote Procedure Call (RPC)

*   **Definition:** Remote Procedure Call (RPC) is a technique that enables a program to request a service from a program in a different computer over a network, without knowing the underlying details of the network. In effect, RPC makes a call over the network as if it's a local procedure call. RPC is also used to call other processes on the same system.

*   **Key Characteristics:**
    *   **Procedure-Oriented:** RPC is based on calling a procedure or a function on the remote component.
    *   **Location Transparency:** The client does not need to know the location of the server.
    *   **Strong Coupling:** RPC tends to result in strong coupling between client and server, as clients typically know the API of the server.

*   **How RPC Works**
    1.  The client initiates by calling the local client stub.
    2.  The client stub takes the parameters and packs it into a message.
    3.  The client stub then makes a system call to send the message over the network.
    4. The message is passed to the server’s OS which then delivers it to the server stub.
    5.  The server stub then unpacks the data from the message and calls the correct server function or procedure.

*   **Use Cases**: Useful for making distributed and client-server based applications, especially when the client knows what the server provides, and there are no major changes happening over the network, or for tightly coupled applications where communication is straightforward.

#### 4.4.2 Representational State Transfer (REST)

*   **Definition:** Representational State Transfer (REST) is an architectural style that emphasizes a client-server approach for building web services. It is based on a few core ideas and principles.

*   **Key Characteristics:**

    *   **Client-Server**: REST separates the user interface concerns from the data storage concerns.
    *   **Layered**: REST systems can be designed with multiple layers, so that each layer only interact with the immediate layers above and below them.
    *   **Tiered**: Each layer can be scaled independently.
    *   **Stateless**: The server does not maintain information about the client. Each request is handled independently.
    *   **Cacheable**: The responses should be able to be cached, thus reducing load on servers.

*   **Core Concepts in REST:**

    *   **State:** Data that is being transferred by an application (such as user’s info)
    *   **Representational:** The format used to transmit data, such as JSON, XML, YAML, HTML, etc
    *   **Transfer**: The act of transmitting data between client and server using protocols, such as HTTP.

*  **How REST Works:** The client sends a request via HTTP and receives a response that contains the data. REST systems can use different formats to send data (XML, JSON, or YAML, etc).

*   **Use Cases**: Well-suited for web applications and systems that need to be scalable, flexible and easily integrate different services, and where the interface between the client and server may change.

### 4.5 Architectural Patterns for Interfaces

Along with REST and RPC, software interfaces also make use of other architectural patterns, namely, client-server, layered, tiered, stateless, and cacheable systems.

* **Client-Server Architecture:** A client-server architecture divides the responsibilities between two components: A server that provides a service or resource, and one or more clients that use that resource.
    * The server handles heavy computation and orchestration, while the client primarily consumes that data and functionality.

* **Layered Architectures:** These architectures organise components into different layers based on their responsibility. Layered approach allows developers to separate concerns by loosely coupling components that interact with each other. They are typically structured with a "shared layer" that contains generic functionality.
  *  The advantage of this approach is that layers may be independently modified without impacting other layers of the system.

*   **Tiered Architectures**: Similar to layered architectures, but each "tier" resides in different physical or virtual environments. This separation allows for independent scaling and deployment.

*   **Stateless Architecture**: In this pattern, the server does not store any session information about the client. This removes the need for servers to create and manage user sessions. The client manages the state and provides it with every request.
    * Stateless systems are often used for authentication, keeping track of context, etc.

*   **Cacheable Architecture**: This design focuses on caching data which is frequently accessed but does not change often. This reduces the load on the system by reusing the cached data rather than fetching the data from the source every time.
    * Caching can be implemented on the client-side (browser), or on the server side

### 4.6 Key Takeaways
* Interfaces are the boundaries where components interact, and must be well-defined.
* Architectural style dictates how software interfaces are built and operate.
* The principles of Interface Design can help you to create high quality, and flexible interfaces
* Remote Procedure Calls are good for tightly coupled applications, while Representational State Transfer are well suited for web applications.
* Architectural patterns, such as layered, tiered, stateless, and cacheable can all influence the way the interfaces are designed and used.

## Chapter 5: Architectural Styles and Patterns: Virtualization and Cloud Computing

### 5.1 Introduction to Virtualization and Cloud Computing

Virtualization and cloud computing are two fundamental concepts that have transformed the landscape of modern software systems. Virtualization creates an abstraction layer between physical resources and software, enabling the execution of multiple environments on a single physical machine. Cloud computing builds upon this, delivering on-demand access to a shared pool of resources over the internet, allowing for greater scalability, and cost efficiency.

*   **Virtualization: Abstraction of Resources**: Virtualization techniques allow you to run different operating systems on a single machine at the same time. This allows for better resource utilization.
*  **Cloud Computing: Resource as a Service**: Cloud computing provides access to shared computing resources on-demand over the internet.

### 5.2 Virtual Machines

Virtual Machines (VMs) are a core component of virtualization. They are a software-based emulation of a computer system that runs on a physical host.

*   **Core Concepts:**
    *   **VM**:  A simulated or virtual computer running on top of a physical computer, referred to as the guest machine.
    *   **Host Computer**: The physical machine that the virtual machines operate on.
    *   **Hypervisor**: A software layer (operating system) that enables multiple VMs to share the hardware resources of the host machine. There are two types of hypervisors:
        *   **Type 1 Hypervisor**: A hypervisor that runs directly on the hardware.
        *   **Type 2 Hypervisor**: A hypervisor that runs as an application on a host operating system.

*   **VM Images**: VMs can be created using pre-built or custom images. Images provide a way to capture and save VM’s state for later use and re-use.
     *   You can find a VM image that already runs the software that you require.
        *   You can start from an existing image and customize it.
         *   You can create an image from scratch.

*   **Use Cases of VMs**:
    * VMs allow you to run different operating systems or applications that are not compatible on the physical hardware, or in different OS’s at the same time
    *  They provide a clean and consistent environment for development and testing, by creating identical testing environments, so that the software works consistently in every machine and by providing pre-configured environments.
    *   They allow for resource utilization and management by allowing multiple VMs to run simultaneously.

### 5.3 Containers

Containers are another form of virtualization which takes a different approach than VMs. They are a lightweight and portable way of packaging applications and their dependencies. Unlike VMs, containers share the operating system’s kernel. This results in a faster startup time and better resource utilization.

*   **Core Concepts:**
    *   **Container:** A self-contained package that includes everything an application needs to run.
    *   **Docker Engine:** A software that manages and runs containers.
    *   **Host Operating System**: The container is built on the Linux kernel.

* **How Containers Work**:
    *   Containers use the operating system's kernel for managing system calls, providing process and network isolation.
    * Unlike VMs, containers do not need an entire operating system, they only provide necessary libraries to run the application, thus resulting in less overhead and faster startup time.

*   **Use Cases for Containers**
    *   Containers are highly portable and can run without changes on compatible systems, and can easily be deployed across different systems or clouds.
    *   Containers enable high density and resource utilization because they share the underlying operating system kernel, which allows for efficient use of computer resources.
     * They are often used in microservices architectures.

### 5.4 Pods in Kubernetes

In many instances containers are not run by themselves. They often exist with other containers, especially when used for microservices. Kubernetes is a tool that is used to manage containers and their orchestration. Kubernetes organizes the containers into logical groups called **pods**.

*   **Core Concepts:**
    *   **Pod**:  The smallest execution unit in Kubernetes. A pod can have multiple applications and containers within it, but they are designed to be closely coupled and co-located.
    *   Pods are ephemeral, this means that pods can be automatically replicated by Kubernetes if the pod or its node fails.

*  **How Pods Work:**

   *  Pods encapsulate applications.
  *  They can have a collection of containers.
  *  Pods use the services of a node.
  *  A pod is ephemeral in that, if it fails it is automatically removed, and Kubernetes will start another pod to carry on the process.

*   **Use Cases for Pods**:
     * Used to deploy and scale containers in a cloud environment.
     *  Provide a base structure for Kubernetes to manage and orchestrate containers.
     *  Helps in managing high-availability and reliability in the application.

### 5.5 Architectural Patterns for Cloud Computing

Along with virtualization, there are other architectural patterns that are often used in Cloud Computing, including Load Balancer, and State Management techniques

*   **Load Balancer**: In many cases an application will have more than one server. Load balancers are used to distribute network traffic or requests across a cluster of servers to prevent any server from being overwhelmed.

   *  Load balancers help to achieve performance, scalability, and fault tolerance by managing network traffic, and also allow for new servers to be added easily.
    *  Load balancers are often a dedicated server in an application’s architecture, which may present an additional single point of failure risk.
* **State Management Techniques:** In distributed computing, the way an application manages state is very important.
      * **Stateful Systems:** State is stored within the server component, this is not scalable or reliable as all requests must go to the same server.
          * In a stateful system when a server goes down, session information is lost, which causes the application to crash or be unusable.
    * **Stateless Systems:** No information is stored by the server, instead, state is maintained by the client with every request. All the data needed to perform an operation is part of the request.
      *  Stateless systems help to increase scalability and reliability as any server can process any incoming request at any given point in time, making the application more fault-tolerant.

* **Data Coordination Strategies:** When there are multiple components in a distributed system, there has to be a method to ensure data consistency and integrity, especially in a shared system where more than one actor may be updating the same information.
    *   **The Paxos Algorithm:** One example is the Paxos Algorithm, which is a mechanism that allows for distributed systems to continue working even when there is network partitioning and server failures. This involves proposers, acceptors, and learners in a process that attempts to reach a consensus.

* **Time Coordination:** Distributed systems also require time to be coordinated correctly to ensure that actions are done in sequence, without conflicts.
    *  An Architect must carefully consider whether time needs to be synchronized according to the actual time, or whether it is enough to ensure the order of sequence.

### 5.6 Key Takeaways

*   Virtualization and cloud computing are foundational for building modern scalable systems.
*   Virtual Machines are powerful software emulations of computer systems and they provide isolation, but can be heavy-weight compared to other solutions.
*   Containers are a lightweight approach to packaging and running applications, which are portable, and have smaller footprints.
*   Kubernetes, and pods, are used to manage and orchestrate containers.
*   Cloud-based applications need to be built for scalability and availability, hence load balancers and state management are necessary for them.

## Chapter 6: Architectural Styles and Patterns for Mobile Systems

### 6.1 Introduction to Mobile System Architecture

Mobile systems present unique architectural challenges due to their inherent constraints and mobility. Unlike traditional desktop or server-based applications, mobile systems need to function within limitations in processing power, memory, connectivity, and battery life. This chapter explores architectural patterns and strategies for building robust mobile applications that address these specific concerns.

*   **Unique Challenges of Mobile Systems:** The core challenge of mobile systems is that they operate in mobile, dynamic environments, with unreliable power, with unreliable network, and limited resources. Architects are required to design systems that can perform in such conditions.

*   **Architectural Focus**: The key aspect of mobile systems is mobility. The applications needs to work when the system is moving or in motion, and still deliver a consistent experience.

### 6.2 Key Characteristics of Mobile Systems

*   **Limited Energy Source:** Mobile devices run on batteries, which means a core part of any mobile design is to conserve power.
*   **Network Connectivity Challenges:** Mobile systems rely on wireless networks which can be unreliable. The type of connection might also change rapidly when a user is moving around, from WiFi to 5G to 4G, or even no service at all.
*   **Sensor and Actuator Availability**: Mobile devices are equipped with numerous sensors and actuators that can be used for interaction. These can be used to gather data from the environment or from user behaviours.
*   **Resource Constraints**: Mobile devices have limited processing, memory, and storage resources compared to desktop systems. Applications need to be designed to operate within those constraints.
*   **Dynamic Environments**: Unlike desktop applications that may have the benefit of working in the same type of location every time, mobile applications are always moving around in different environments.
*   **Life Cycle and Testing:** Mobile applications have a unique design, testing, and deployment lifecycle, which needs to be considered.

### 6.3 Architectural Tactics for Mobile Systems

As mobile devices deal with mobility in addition to other factors, there are a number of architectural tactics to tackle these problems.

#### 6.3.1 Tactics for Power Management (Energy)

Mobile applications always require consideration about power usage. Following tactics can help in managing power usage:

*   **Monitoring Power Consumption:**
     *   Monitoring the status of the battery can help determine how much time the system can run for.
        *  A battery management system (BMS) will need to be built to measure or get a reading from a hardware component.
     *   Applications need to monitor memory usage and CPU utilization, which impact power usage and can give insight into which parts of the application is consuming the most energy.

*   **Throttling Energy Usage:**
    *   Terminating or degrading portions of the system when necessary, such as when the power is low to extend battery usage time.
    *   Reducing number of CPU cores when necessary.
   *   Reducing the speed of the processor or clock to save energy.
    * Reducing the frequency that a sensor is used.

*   **Tolerating a Loss of Power:** The mobile application should be able to save the state and gracefully restore its operation within 30 seconds when power is resumed. The application needs to protect itself from loss of data when the system shuts down unexpectedly, due to power loss.

#### 6.3.2 Tactics for Managing Network Connectivity

Mobile systems operate in an environment where network connectivity is not always assured or consistent. These tactics address the challenges of moving around the network.

*   **Support Multiple Interfaces:** Mobile systems should support multiple communication interfaces to optimise power consumption, for example, using Bluetooth when it is nearby or using WiFi when it’s available. The system must determine the connection in use dynamically.

*  **Movement Between Interfaces:** System must allow the user to move from one network to another, while still using the application. When moving from one protocol to another, the application must be able to seamlessly switch without any issue. For example moving from a WiFi network to a Cellular network.

*   **Dynamic Protocol Selection:** When multiple protocols are available, the system must dynamically choose the correct one to use to optimize resource and power consumption. For example, to use WiFi to stream video, but when a WiFi is not available use a more expensive mobile network.

*  **Modifiability** is important because the underlying networking protocols can often be changed, making it necessary to update the application with new information, and therefore must be easy to modify.
*   **Bandwidth**: Using a lower bandwidth when network is unstable is a key aspect to conserve energy and also to ensure the application is not affected by slow or intermittent connectivity.
*   **Intermittent/Limited Connectivity:** Mobile systems are often used in areas with intermittent or limited connectivity. The system should be able to deal with this type of unstable connections by caching data, or implementing offline mode, or data synchronization strategies.
*   **Security**: Security must be at the heart of mobile communication. Authentication, encryption and authorization must be correctly implemented.

#### 6.3.3 Tactics for Managing Sensors and Actuators

Sensors and actuators are core to mobile functionality, and proper architectural design should take this into account:

*   **Reading Raw Data:** Software drivers are used to directly interact with the sensors and actuators to read raw data from hardware, to control hardware components.
*  **Smoothing Data:** Mobile sensors can generate noisy data which has to be smoothed, so that the application is not affected by variations in input signals.
*   **Converting Data:** Data from sensors come in many different formats. The application should be able to convert it into standard formats to make it easier for it to be used.
*  **Sensor Fusion:** Data coming from multiple sensors can be combined to create a more complete picture of what is happening, such as determining the location and orientation of the device or what it is doing.

#### 6.3.4 Managing Resources in Mobile Devices

Mobile devices are limited by resources, so specific strategies are required.
*  **Fit of the Electronic Control Unit (ECU)** to function, to choose the correct micro controller to perform a specific function.  For example, when needing a graphical interface, the mobile application would use a controller with a graphic processing unit.
*   **Criticality powerful ECU:** Choosing a controller with higher capacity for critical application, such as medical devices.
*  **Location in the vehicle:** This specifies the positioning of the ECU in an area, as this can impact performance.
    *   For example, first-class passenger seating may offer better connectivity than second class seating.
*   **Connectivity:** All ECUs in a mobile system should be able to communicate with one another.
*   **Locality of Communication:** The architectural design should ensure that the communication devices are correctly positioned so as not to interfere with each other.

#### 6.3.5 Mobile System Life Cycle

There are a few unique factors that must be taken into account for mobile systems during its lifecycle:

*  **Hardware First:** Mobile applications often begin with a hardware choice, where developers need to work within the constraint set by the hardware.
*   **Testing**: Mobile system testing also needs to take into account how things are presented across different sizes of screens and device specifications, rather than the static environment desktop applications are developed for.
*  **Deploying Updates**: Software deployments needs to take into account the safety of users and how updates are pushed to devices when the user is in motion, or even how it is done in a background without affecting the normal user experience.
*   **Logging**: Logging mechanisms must be in place for all mobile systems so that issues can be easily identified and fixed.

### 6.4 Key Takeaways

*   Mobile systems have different requirements compared to traditional applications.
*   Energy management is a core component of mobile systems design.
*   Architects need to have specific strategies for dealing with network instability in a mobile system.
*   Sensors and actuators are essential in a mobile system design.
*   Resource constraints and the mobile lifecycle needs to be considered during the design phase.   

## Chapter 7: Tactics for Achieving Quality Attributes (Continued)

### 7.1 Introduction

In chapter 3, we introduced the concept of tactics as design decisions influencing a specific quality response. In this chapter, we dive deeper into applying tactics for specific quality attributes and combine the knowledge from different sub-chapters on "Tactics".

### 7.2 Tactics for Modifiability

Modifiability concerns how easily changes can be made to a system to adapt to new requirements or correct issues. It’s essential for the long-term maintainability and evolvability of a software system. There are some core strategies that are employed by architects, namely, to manage the size of components, reduce coupling and improve cohesion, and to establish modular patterns.

#### 7.2.1 Reducing Module Size
* **Rationale:** Smaller, well-defined modules are easier to understand, modify, and test than larger, more complex ones. This can reduce overall complexity of the application.
*   **Techniques:** Breaking down larger modules into smaller, more focused pieces. Often requires identifying specific functional aspects of an application, and to create modules around these.
*   **Benefits**:
    * Improves readability and maintainability by reducing complexity
    * Reduces the risk of introducing bugs when making changes.
    *   Facilitates reuse and simplifies testing.

#### 7.2.2 Improving Semantic Cohesion

*   **Rationale:** Cohesion is about the relatedness of the elements within a module. High cohesion means that a module’s elements work together towards a single, well-defined purpose.
*   **Techniques:**
     * Grouping together elements that are functionally similar.
    *  Combining all code that relate to a single feature into a single module.
*   **Benefits**:
    *  Improved clarity and understandability of modules.
    *   Reduced complexity, and simplifies maintenance and modification.
    *   Making sure all elements of a module are connected for a common purpose reduces the change of ripple effects.

#### 7.2.3 Reducing Coupling

Coupling defines the degree of dependency between different modules. Low coupling means that modules can operate independently.

*   **Rationale:** Tightly coupled modules can lead to ripple effects: changes in one module may require changes in another. The goal here is to make the modules as independent as possible, so that it is possible to update a part of the system without any impact on another.

*   **Techniques**:
    *   **Encapsulation**: Encapsulating data behind well-defined interfaces limits direct access to data and therefore reduces coupling. This hides how a certain module works by protecting its internal properties and methods.
    *   **Use an Intermediary:** An intermediary layer can reduce the direct dependencies between modules. This can be a broker system, or a mediator.
    *   **Restrict Dependencies**: Only use the needed dependencies, and not adding extra. Having a higher number of dependencies between different parts of a system makes them highly coupled, and the system becomes brittle.

*   **Benefits**:
    *  Modules are more independent, allowing for flexibility and modularity.
    *  Reduced ripple effects when making changes, and easier to introduce changes without fear of breaking the system.
    * Improves testability because changes to components do not effect others.

#### 7.2.4 Other Modifiability Tactics
* **Refactor:** Improving code and structure by changing the implementation or code-base, without changing the behaviour of the application itself. Refactoring can improve readability and flexibility for future changes.
 * **Abstract Common Services**: Identifying and abstracting common functionalities used by multiple components into a reusable module. This reduces redundancy and duplication and improves modifiability since those service are reused rather than rewritten
  *   **Defer Binding**: Delay decisions (or the “binding” of components and modules) as much as possible to keep the system flexible.
     *   *Examples:* Delaying decisions on what implementation to use until runtime. This includes making UI choices without having to recode, or choosing the correct implementation based on a specific environment.

**Key Takeaway:** By reducing coupling, increasing cohesion, and maintaining smaller modules, applications can be made easier to modify and evolve.

### 7.3 Tactics for Usability (Revisited)

As we saw before, Usability ensures that a system is easy for users to understand and accomplish their tasks with. This involves using specific patterns that allow the user to initiate behaviours or for the system to provide support and assistance.

#### 7.3.1 Supporting User Initiatives

*   **Cancel**: Provides users the ability to terminate operations that are in progress. By listening for a cancel command, the system has the responsibility to terminate the processes and release all resources which may be held up.
*  **Undo**: Provides a way for users to revert their actions. This is done by saving information on the current state of the system, so that the application can go back to that state.
 * Not all operations can be undone, for example, if a bell is rung, it cannot be "unrung" or erased.
*   **Pause/Resume:** Allows user to stop and resume an ongoing process, for example stopping a download when bandwidth is needed for something else. It requires the system to release the resources being used to be re-allocated to a different task.

*   **Aggregate**: Used for performing an action on a group of objects or repetitive operations. This will reduce repetitive user interactions and make using a system quicker for the user.

#### 7.3.2 Supporting System Initiatives

*   **Maintain Task Model:** By having a model of the actions that are performed by the user, the system can attempt to understand user’s context and intention, and provide assistance when needed.

*   **Maintain User Model:** A user model represents the specific user's profile, how that person uses the application, along with any specific preferences or access levels. Based on this, the system may provide suggestions to help the user, which will streamline the application.

*   **Maintain System Model:** By maintaining an explicit representation of itself, the system can predict its behaviors. This allows it to provide accurate status information to users, for instance a progress bar or ETA.

#### 7.3.3 UI Separation

While not being strictly a “support” tactic, UI separation is key to enabling usability and modifiability. The goal here is to separate the UI layer of an application, as this tends to be volatile.
* By separating the UI layer, other parts of the application are not dependent on changes in the UI, thus making it easier to develop and test new interfaces.
*   By keeping UI responsibilities and dependencies separate, ripple effects are minimized when a UI change occurs.
*   It allows UI choice to be made without impacting the implementation, allowing different UIs to be tested or deployed for different users.

**Key Takeaway**: By combining tactics for both user and system initiatives and with a separate UI layer, the usability of an application can be enhanced.

### 7.4 Tactics for Performance (Revisited)

As discussed previously, performance focuses on the efficiency and speed of a system. It's a key QA to ensure a great user experience, with quick response times, minimal delay, and that resources are not unnecessarily wasted. To do this, the core approach is to manage resource demand and availability.

#### 7.4.1 Controlling Resource Demand

This group of tactics focuses on reducing the number of operations needed for a user request.

*   **Manage Sampling Rate**: Instead of processing all data, you may chose to decrease the rate of sampling to reduce the amount of data that needs to be processed.
   *   *Example:* A video stream can operate at a lower resolution during times when there are many concurrent users.

*  **Limit Event Response**: Reduce the rate at which events are processed. When there are bursts of events, they can be put in a queue and processed slower, or if the burst is too high, the events may be ignored.

*  **Prioritize Events**: Handling events in terms of their criticality, so that more important events are handled sooner. High-priority events should be serviced before those with lower priorities. Lower priority events may be dropped if there are no resources available to handle them.

*  **Reduce Overhead**: Minimizing unnecessary or redundant steps that slow down processing. This tactic has the goal of reducing operational overhead by simplifying data transfer, communication, or resource allocation.
*   **Bound Execution Times**:  Limiting the maximum time a component spends responding to any single event. This tactic is about making sure that a component has a timeout if it takes too long to execute.

*  **Increase Resource Efficiency**: Improves the quality of algorithms or processes so that the system can perform with less resource usage, and can deliver better latency and more throughput. For example, an algorithm can be re-designed to use less memory to do the same task.

#### 7.4.2 Managing Resources (Revisited)

The goal here is not to reduce the number of operations, but to make sure that resources are handled efficiently.

*   **Increase Resources**: Improving system hardware, such as by adding memory, using faster CPUs, faster network connections, etc. This is the most straight forward way to address latency issues, since more resources can process the same amount of work quicker.

*   **Introduce Concurrency**:  This involves processing tasks in parallel to reduce wait times. This needs careful implementation as there are risks with concurrency such as race conditions, deadlocks, etc. To use concurrency requires the appropriate choice of scheduling policies.

* **Common Scheduling Policies**: Scheduling policies specify which thread or process will be scheduled next. Some common scheduling policies are:
    * **First-In-First-Out (FIFO):** All requests for resources are treated equally and are processed sequentially.
   *  **Fixed Priority Scheduling**: Requests are given a priority (based on different metrics) and resources are allocated based on that priority.
        *   Semantic Importance - priority based on the type of request
        *   Deadline Monotonic - priority based on the deadline
         *   Rate Monotonic - Priority based on how often the request is made
   *   **Dynamic Priority Scheduling**: Resources are allocated based on dynamic rules
        *  Round Robin - Processes are given equal share of resources
         *  Earliest Deadline First - Processes are prioritized based on their pending deadline

   *  **Static Scheduling:** The priority or sequence of assignment is determined offline or in advance. This implies that all parameters are known.

*   **Maintain Multiple Copies of Computation**: This tactic involves creating multiple copies of a service to reduce contention. Multiple web servers working in parallel can greatly increase the throughput of the application. This requires the implementation of a load balancer.

*   **Maintain Multiple Copies of Data (Caching)**:  Caching means to store frequently accessed information on different levels of storage so that it can be retrieved quicker. Data can be stored on a memory cache, or on a local disk.

*   **Bound Queue Sizes**: Setting limits on the amount of queued requests, to avoid resource depletion or overflow.
*  **Schedule Resources**: Using an approach to schedule resources, such as using a specific scheduling algorithm.

### 7.5 Tactics for Security (Revisited)

Security tactics aim to prevent, resist, react to and recover from security breaches. They are not just a specific functionality that can be used, instead, they need to be baked into the architecture of the system from the beginning.

*   **Detect Attacks:**
    *  **Detect Intrusion:** Requires a monitor to identify system breaches.
    * **Detect Service Denial:** Identifying attacks that render a service unusable, such as DDOS attacks.
    *   **Verify Message Integrity**: Checking data to ensure that it has not been tampered with.
    *   **Detect Message Delay**: Identifying message delays which could indicate an attack.

*   **Resist Attacks:**
    *   **Authenticate Actors:** Verifying user or system identity before providing access.
    *   **Authorize Actors:** Verify what an identified actor can perform within the system.
    *   **Limit Access:** Providing access to only the minimum required resources using principles of least-privilege.
    *   **Limit Exposure:** Reduce the attack surface by exposing only the required components.
    *   **Encrypt Data:** Using cryptographic methods to protect sensitive information.
    *   **Separate Entities:** Grouping security sensitive components separately from others to reduce the impact of a breach.
    *   **Change Default Settings:** Default settings are always a security risk and must always be changed during the configuration of the system.

*   **React to Attacks:**
    *   **Revoke Access:** Deny access to resources from potentially malicious users or components.
    *   **Lock Computer:** Locking computers that are at risk to prevent further misuse.
    *  **Inform Actors:** Sending notifications to users or administrators about security breaches.

*   **Recover from Attacks:**
    *   **Maintain Audit Trail:** Records of system operation need to be collected to determine root cause analysis of a breach and to improve processes in the future
     *   **Restore:** The ability to return to a safe state after a security incident, such as by restoring data or by reverting to an earlier application state.

### 7.6 Putting it all Together
Architects use many different tactics, each working toward a single goal. These are tools that must be chosen based on specific situations and priorities. For example, if availability is a primary goal, an architect would chose tactics for redundant components; or to reduce resource usage and optimize performance. This does not mean that the other attributes are ignored, it means they are addressed in a way to meet the demands and goals of the architecture.

### 7.7 Key Takeaways
*   Tactics are building blocks for constructing a specific system. They are the core tools for architects.
*   Architectural tactics are used by architects to influence how systems behave and address specific quality concerns.
* Modifiability tactics help to create an application that is easy to maintain and change.
 * Usability tactics help to make the application more intuitive to use.
 * Performance tactics focus on using resources correctly and efficiently.
 * Security tactics aim to protect the integrity of the system, and its data.

## Chapter 8: The Attribute-Driven Design (ADD) Method

### 8.1 Introduction to Attribute-Driven Design (ADD)

The Attribute-Driven Design (ADD) method provides a structured, iterative approach to designing software architectures. Unlike ad-hoc design, ADD emphasizes a principled and systematic approach, ensuring that quality attributes are explicitly addressed throughout the design process. ADD is an iterative approach to design, where key decisions are taken step-by-step and continuously re-evaluated. This approach helps to reduce risks and ensure that architectures are tailored to specific needs. It provides a way to create a “good enough” design, and it is not meant to be a big-design-up-front approach.

*   **A Structured Process:** ADD provides step-by-step guidance for making design decisions, based on the requirements of the software project.
*   **Iterative Nature:** ADD is designed to be iterative, which implies that designs can be refined through several rounds of the design process.
*   **Explicit Quality Focus**: Quality attributes are not an afterthought; they are central to the decision-making process, with the overall design being driven by the prioritized requirements of the application.

### 8.2 The ADD Process

ADD’s architectural design is performed in a series of rounds, where each round may represent a sprint or other project iteration. Within these rounds, a series of design iterations are performed. ADD provides specific guidelines on the tasks for each iteration:

1.  **Review Inputs:** At the start of every round or iteration, review the core inputs to make sure the whole system context is clear. The input will contain key aspects of the project, including:

    *   **Design purpose**: The overall goals and intent of the software being created.
    *   **Primary functional requirements:** High level view of what the software is required to do.
    *  **Quality Attribute Scenarios:** High-level list of all the required quality attributes which will be addressed in the design.
    *   **Constraints:** The limitations on time, budget, or other factors.
    *   **Architectural Concerns**: All other concerns, which may or may not be documented.

2.  **Establish Iteration Goal:** Identify the objective or the main goal for this specific iteration of design. This involves breaking up the whole problem into smaller, manageable tasks, and then selecting which sub-problem to tackle in the current iteration. This is also about explicitly choosing which architectural drivers to prioritize and what to achieve within the iteration. The specific drivers chosen at this step will guide the rest of the design decisions in this iteration.

3.  **Choose Elements to Refine:** This step focuses on deciding which specific elements or parts of the system need to be worked on during the current iteration. It is based on the choice of the previous step, and determines the next steps of how to design that aspect of the system.

4.  **Choose Design Concepts**: This step involves selecting the design concepts (such as tactics and patterns) that will be used to satisfy the drivers chosen in step 2. It is the step where concrete strategies are selected to handle a certain aspect of the system.

5.  **Instantiate Architectural Elements, Allocate Responsibilities, and Define Interfaces**: In this step, the chosen design concepts are implemented in a concrete manner. This includes:
   *   Creating actual architectural components or elements.
    *   Allocating specific functionalities or responsibilities to each component
     *   Defining the interfaces for these components, to specify how they interact with each other.

6.  **Sketch Views and Record Decisions**: Here you sketch a diagram representing the architecture. This sketch may only be part of the whole system and should capture design decisions. This helps to make the architecture visible and to record key decisions. It is not meant to be formal and complete documentation, but to provide quick reference points for future decisions.

7. **Perform Analysis and Review:** The final step involves analyzing the existing architecture created so far to assess if it meets the requirements defined in steps 1 & 2, and if the architecture still addresses the goals and requirements. Based on this review the designer will determine whether the current round is sufficient, or whether a new iteration is necessary to fix some issues.

### 8.3 Roadmaps for Using ADD

The ADD process is not necessarily a rigid or fixed path, and you may take different routes depending on the software being developed. Here are different roadmaps based on the project at hand:

*   **Greenfield Systems for Mature Domains**: When building a system for a well-understood domain, you can take advantage of existing experience and knowledge.
     *   In the first iteration, you will establish the overall architecture, based on reference architectures and deployment patterns, using externally available components.
    *   Then in subsequent iterations you will define architectural patterns to support primary functions, and then chose specific tactics and deployment patterns to satisfy any remaining drivers.
*   **Greenfield Systems for Novel Domains**: When the problem and domain is novel, it’s harder to develop a design, as there are no clear best practices.
     *   You will often need to work from first principles and there may be few externally available components.
     *   The design concepts are still helpful, though it is often guided by prototyping to confirm the design.
    *  The iterations focus on refining previously created structures to address the design drivers.
*   **Existing Systems (Brownfield):** In existing systems, the goal is often to correct issues and add new features.
    *   You will usually refine the design based on existing architectural and design decisions, with a focus on adding new functionality or correcting quality issues.
    * There may not be a need to create a new overall architecture, unless a major refactoring is performed.

### 8.4 Identifying Design Concepts

Identifying design concepts is a crucial part of the ADD process, as you need to find the patterns and tactics to apply to your specific situation.
*   There are dozens of design patterns and tactics to chose from, and they may be scattered across multiple sources, from textbooks to journals and even online resources.
*    Therefore, you will need to select appropriate designs based on their advantages and disadvantages, or in their impact to your system.
* Once you identified different choices, you need to compare them and select what’s the best option.

### 8.5 Selecting Design Concepts

After choosing the available options, you need to select the best one.

* **How?** One method is to create a table, that lists all the pros and cons of each method.
* **When needed** This is not always sufficient, so you might need to prototype a design option to evaluate its real-world impact.
* **Caution:** Prototypes, while being useful, can be costly in time and resources. A throwaway prototype should only be built when needed, as determined by a proper evaluation.

### 8.6 Producing Structures and Defining Interfaces

Architects need to choose a design option, but those options will not by themselves help to satisfy requirements unless concrete structures are created and implemented.

*   **Instantiating Elements**: In ADD, instantiation refers to the creation of the actual components and connectors that make up the software, and the connections among them. It also involves assigning responsibilities to those components.
*   **Types of Structures:** As described in previous chapters, we are mostly concerned with three types of software structures, and we might need to implement more than one structure for a design decision.
    *   **Module structures:** Elements at development time, like files, modules, and classes.
   *   **Component and Connector (C&C) Structures:** Elements that are present during runtime, such as threads and processes.
    *  **Allocation Structures:** Software components and how they are allocated to non-software elements, such as file system, hardware, and development teams.
*   **Defining Interfaces**: The final aspect is to create the contractual specifications which allow components to interact.
     *   **External Interfaces**: These are the interfaces between your system and the outside world.
     *   **Internal Interfaces**: Interfaces that define communication between internal parts of the system.
     * Sequence diagrams, are very useful to show the interactions among components

### 8.7 Documenting During Design

The documentation process should be an integral part of the design process, although formal documentation of the design is not required. There are many aspects that should be recorded:

*   **Recording Design Decisions**: In each iteration key design decisions are made, such as choosing components, defining interfaces, and selecting architectural tactics and patterns. All of these need to be recorded.

*   **Design Rationale**: The reasons for the design decisions, in addition to the chosen option also needs to be recorded. The "why" behind those decisions is important and needs to be captured.
    *  This can also include who made each decision, if shortcuts were made, and what kind of tradeoffs or assumptions were made in the process.

*   **Recording Sketches**: Sketches, not full documentation, are also key for future reference. A legend should be included to define the symbols and their meanings.
*   **Tracking Design Progress**: Tracking progress is important in any type of software development. This can be done through a backlog, and by visualising the tasks in a Kanban board.

### 8.8 Key Takeaways

*   The ADD method is an iterative and principled approach to software design.
*   ADD is done in rounds where you have a series of iterations, and within an iteration you are working to solve part of the problem.
*   A proper roadmap should be followed during the design based on the requirements of the system or project.
*   Selecting a design concepts require an evaluation of advantages and disadvantages, and that prototypes should only be created if truly needed.
*   During the process, structures must be created and interfaces defined.
*   Throughout the process, decision and rationale needs to be documented and a method to track the progress should be adopted.