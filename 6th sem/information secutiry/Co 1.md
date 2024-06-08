**CO-1**

**1-mark MCQ**

**Easy**
1. **Which of the following is a primary objective of the General Data Protection Regulation (GDPR)?**
   a) To increase government surveillance on personal communications.  
   b) To harmonize data privacy laws across Europe and protect EU citizens' data privacy.  
   c) To promote the unrestricted sharing of personal data between companies.  
   d) To ensure that all personal data is stored indefinitely.

   **Answer:** b) To harmonize data privacy laws across Europe and protect EU citizens' data privacy.

2. **Which access control model uses attributes of users, resources, and the environment to determine access permissions dynamically?**  
   a) Discretionary Access Control (DAC)  
   b) Mandatory Access Control (MAC)  
   c) Role-Based Access Control (RBAC)  
   d) Attribute-Based Access Control (ABAC)

   **Answer:** d) Attribute-Based Access Control (ABAC)

**Moderate**
1. **Which confidentiality policy model focuses on preventing the unauthorized disclosure of information by enforcing 'no read up' and 'no write down' rules?**
   a) Bell-LaPadula Model  
   b) Biba Model  
   c) Clark-Wilson Model  
   d) Brewer and Nash Model

   **Answer:** a) Bell-LaPadula Model

2. **In Role-Based Access Control (RBAC), which of the following best describes the relationship between roles and permissions?**
   a) Each user is directly assigned a set of permissions without any intermediary.  
   b) Users are assigned to roles, and roles are assigned a set of permissions, creating an indirect relationship between users and permissions.  
   c) Permissions are assigned directly to tasks, which users perform without any roles.  
   d) Each role is assigned to a single user, with permissions dynamically changing based on tasks.

   **Answer:** b) Users are assigned to roles, and roles are assigned a set of permissions, creating an indirect relationship between users and permissions.

**Hard**
1. **Which of the following is an internationally recognized standard for information security management systems (ISMS)?**
   a) ISO/IEC 27001  
   b) PCI-DSS  
   c) HIPAA  
   d) GDPR

   **Answer:** a) ISO/IEC 27001

**5-mark question**

**Easy**
1. **Write short notes on the following access control models:**
   
   **i) Role-Based Access Control (RBAC):**  
   Role-Based Access Control (RBAC) is a policy-neutral access control mechanism defined around roles and privileges. The components of RBAC include roles, which are named job functions within an organization, and permissions, which are the approval of a mode of access to a resource. Users are assigned roles based on their responsibilities and qualifications. This model simplifies management as roles can be created for various job functions and permissions can be assigned to those roles, and then users can be assigned to roles.

   **ii) Task-Based Access Control (TBAC):**  
   Task-Based Access Control (TBAC) is centered around tasks that users need to perform, rather than their roles within an organization. In this model, permissions are assigned to tasks, and users are granted access rights necessary to perform specific tasks. This model can be more dynamic and adaptable in environments where tasks and responsibilities frequently change, as it allows for finer granularity and more flexible assignment of permissions.

**Moderate**
1. **Explain the concept of a reference monitor in information security. What are its key properties, and why is it important for maintaining system security? Provide an example to illustrate your explanation.**

   A reference monitor is an abstract machine that mediates all access to objects by subjects. It ensures that all attempted accesses are validated against a set of authorization policies before they are allowed to proceed. The key properties of a reference monitor include:

   - **Completeness:** It must monitor all access to ensure no bypass.
   - **Isolation:** It must be tamper-proof to ensure integrity.
   - **Verifiability:** It must be small enough to be subject to analysis and testing to ensure correctness.
   - **Enforcement:** It must enforce access controls effectively and efficiently.

   The reference monitor is crucial for maintaining system security as it ensures that no unauthorized access occurs, thus protecting sensitive data and resources. For example, in an operating system, the reference monitor controls user access to files and system resources, ensuring that users can only access data for which they have permissions.

**Hard**
1. **Discuss the challenges and considerations involved in implementing security policies in a large organization. How can an organization ensure that its security policies are effectively enforced and adapted to changing threats? Provide specific strategies and examples to support your explanation.**

   Implementing security policies in a large organization involves several challenges:

   - **Complexity:** Large organizations have diverse operations, systems, and data, making it difficult to create a one-size-fits-all policy.
   - **Scalability:** Policies must scale to handle the number of users, devices, and data without becoming overly burdensome.
   - **Adaptability:** Policies need to adapt to new threats and technological changes.
   - **Compliance:** Ensuring policies meet legal and regulatory requirements.

   Strategies to address these challenges include:

   - **Risk Assessment:** Regularly conduct risk assessments to understand current and emerging threats.
   - **Clear Policies:** Develop clear, comprehensive, and accessible policies that are regularly reviewed and updated.
   - **Training and Awareness:** Regularly train employees on security policies and the importance of compliance.
   - **Automation and Tools:** Use automated tools to enforce policies and detect violations.
   - **Monitoring and Auditing:** Continuously monitor and audit systems to ensure compliance and detect breaches early.
   - **Incident Response Plan:** Have a well-defined incident response plan to quickly address and mitigate security breaches.

   For example, a large financial institution might implement a policy requiring multi-factor authentication for all sensitive transactions. They would use automated systems to enforce this policy, provide regular training to employees, and continuously monitor access logs for any anomalies, adapting their policies as new threats emerge.

**10-mark question**

**Easy**
1. **Define access control model. List and explain its elements. Also describe any two access control models in detail.**

   **Access Control Model Definition:**
   An access control model is a framework that defines how access permissions are granted, managed, and enforced within a system. It determines how users can interact with resources based on policies and rules.

   **Elements of Access Control Model:**
   - **Subjects:** Entities (users or processes) that request access to resources.
   - **Objects:** Resources (data, applications, systems) to which access is controlled.
   - **Permissions:** Specific rights or privileges granted to subjects to perform actions on objects.
   - **Policies:** Rules that define how permissions are assigned and enforced.

   **Two Access Control Models:**

   **i) Discretionary Access Control (DAC):**
   In DAC, the owner of the resource determines who has access to it and what permissions they have. This model is flexible and allows resource owners to control access but can be prone to security breaches if not managed properly. For example, a file owner can set read, write, and execute permissions for other users.

   **ii) Mandatory Access Control (MAC):**
   In MAC, access to resources is controlled by a central authority based on security classifications. Users and data objects are assigned security labels, and access is granted based on these labels. This model is highly secure and used in environments requiring stringent security, such as military systems. For example, a user with a "Top Secret" clearance can access data labeled "Top Secret" but not "Confidential."

**Moderate**
1. **Enlist and explain any six international standards used in information security.**

   **i) ISO/IEC 27001:**
   This standard specifies requirements for establishing, implementing, maintaining, and continually improving an information security management system (ISMS). It helps organizations manage the security of assets such as financial information, intellectual property, and employee details.

   **ii) ISO/IEC 27002:**
   This standard provides guidelines and best practices for information security controls. It is designed to be used by organizations implementing commonly accepted information security controls within the context of an ISMS.

   **iii) NIST SP 800-53:**
   A publication by the National Institute of Standards and Technology (NIST) providing a catalog of security and privacy controls for federal information systems and organizations to protect against threats.

   **iv) PCI-DSS:**
   The Payment Card Industry Data Security Standard is a set of security standards designed to ensure that all companies that process, store, or transmit credit card information maintain a secure environment.

   **v) HIPAA:**
   The Health Insurance Portability and Accountability Act sets the standard for protecting sensitive patient data. Organizations that deal with protected health information (PHI) must have physical, network, and process security measures in place and follow them.

   **vi) COBIT:**
   Control Objectives for Information and Related Technologies is a framework created by ISACA for IT management and governance. It helps organizations create optimal value from IT by maintaining a balance between realizing benefits and optimizing risk levels and resource use.

**Hard**
1. **Write short notes on non-interference, policy composition.**

   **Non-Interference:**
   Non-interference is a security property ensuring that actions of one user do not affect the system states visible to another user, preventing information leakage. It is particularly relevant in multilevel security systems where users of different clearance levels access shared resources. Non-interference aims to prevent covert channels where sensitive information might be inferred from the system's behavior.

   **Policy Composition:**
   Policy composition refers to the method of combining multiple security policies into a unified policy that governs a system's behavior. This is necessary in environments