Design: Design principles, representing identity, control of access and information 
flow, confinement problem.
Assurance: Building systems with assurance, formal methods, evaluating systems.


### Design Principles

Design principles for secure systems are foundational concepts aimed at ensuring the robustness and security of information systems. Key principles include:

1. **Least Privilege**:
   - Granting users and systems the minimum level of access necessary to perform their functions.
   - Reduces the risk of accidental or malicious misuse of access.

2. **Defense in Depth**:
   - Implementing multiple layers of security controls and safeguards.
   - Ensures that if one layer is breached, additional layers remain to protect the system.

3. **Fail-Safe Defaults**:
   - Default configurations should deny access unless explicitly allowed.
   - Ensures that in the event of a failure, the system remains secure.

4. **Economy of Mechanism**:
   - Keeping the design as simple and small as possible.
   - Simplifies the security review process and reduces the risk of errors.

5. **Complete Mediation**:
   - Ensuring that every access to a resource is checked against the access control policy.
   - Prevents bypassing security checks.

6. **Open Design**:
   - Security should not depend on the secrecy of the design or implementation.
   - Promotes transparency and allows for external reviews and improvements.

7. **Separation of Duties**:
   - Dividing tasks and privileges among multiple users.
   - Prevents a single user from having too much control, reducing the risk of fraud and errors.

8. **Least Common Mechanism**:
   - Minimizing the amount of mechanisms shared among users.
   - Reduces the risk of a single point of failure and potential security breaches.

9. **Psychological Acceptability**:
   - Security mechanisms should not make the system difficult to use.
   - Ensures that users comply with security measures rather than bypass them.

### Representing Identity

Identity representation involves mechanisms to uniquely identify users and systems within a network. Key concepts include:

- **Authentication**: Verifying the identity of a user or system. Methods include passwords, biometrics, and digital certificates.
- **Authorization**: Granting access to resources based on verified identity and established policies.
- **Identity Management**: Processes and technologies for managing digital identities, including creation, maintenance, and deletion.

### Control of Access and Information Flow

Controlling access and information flow involves ensuring that only authorized users can access resources and that information flows in a secure manner.

- **Access Control Models**: Frameworks like DAC, MAC, RBAC, and TBAC determine how access is granted.
- **Information Flow Control**: Policies and mechanisms to control how information is transferred between different security domains, preventing leakage of sensitive information.

### Confinement Problem

The confinement problem involves ensuring that a program cannot leak sensitive information during its execution. Key strategies include:

- **Sandboxing**: Running applications in isolated environments to limit their access to system resources.
- **Virtualization**: Using virtual machines to isolate processes and enforce strict control over resource access.
- **Capabilities**: Assigning specific permissions to processes, limiting their ability to access or modify resources.

### Assurance

Building systems with assurance involves implementing and verifying security measures to ensure they function as intended.

#### Building Systems with Assurance

- **Security by Design**: Integrating security considerations into every stage of the system development lifecycle (SDLC).
- **Code Reviews**: Systematic examination of source code to identify and fix security vulnerabilities.
- **Security Testing**: Conducting various tests, including penetration testing and vulnerability scanning, to identify weaknesses.

#### Formal Methods

Formal methods involve using mathematical and logical techniques to specify, develop, and verify systems.

- **Specification**: Defining precise, mathematical models of system requirements and behavior.
- **Verification**: Proving, through mathematical reasoning, that a system's implementation meets its specification.
- **Model Checking**: Using automated tools to verify finite-state models of systems against desired properties.

#### Evaluating Systems

Evaluating systems involves assessing their security posture and ensuring they meet required standards.

- **Security Audits**: Comprehensive reviews of an organization's security policies, practices, and controls.
- **Penetration Testing**: Simulating attacks to identify vulnerabilities and test the effectiveness of security measures.
- **Certification and Accreditation**: Formal processes to ensure systems meet specific security criteria and standards (e.g., ISO/IEC 27001, Common Criteria).

By adhering to these design principles and assurance practices, organizations can build robust and secure systems that effectively protect against various threats and vulnerabilities.