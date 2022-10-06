## Brief

### Preparation

Write about any preparations needed for the lesson, such as tools, installations, prior-knowledge, etcs.

### Lesson Overview

This module focuses on the security pillar. This will help to meet the business and regulatory requirements by following current AWS recommendations. It’s intended for those in technology roles, such as chief technology officers (CTOs), chief information security officers (CSOs/CISOs), architects, developers, and operations team members.

After reading this module, we will understand AWS current recommendations and strategies to use when designing cloud architectures with security in mind. This module doesn’t provide implementation details or architectural patterns but does include references to appropriate resources for this information. By adopting the practices in this module, we can build architectures that protect our data and systems, control access, and respond automatically to security events.

---

## Part 1 - Security Design Principles

In the cloud, there are a number of principles that can help you strengthen your workload security:

- **Implement a strong identity foundation:** Implement the principle of least privilege and enforce separation of duties with appropriate authorization for each interaction with your AWS resources. Centralize identity management, and aim to eliminate reliance on long-term static credentials.
- Enable traceability: Monitor, alert, and audit actions and changes to your environment in real time. Integrate log and metric collection with systems to automatically investigate and take action.
- **Apply security at all layers:** Apply a defense in depth approach with multiple security controls. Apply to all layers (for example, edge of network, VPC, load balancing, every instance and compute service, operating system, application, and code).
- **Automate security best practices:** Automated software-based security mechanisms improve your ability to securely scale more rapidly and cost-effectively. Create secure architectures, including the implementation of controls that are defined and managed as code in version-controlled templates.
- **Protect data in transit and at rest:** Classify your data into sensitivity levels and use mechanisms, such as encryption, tokenization, and access control where appropriate.
- **Keep people away from data:** Use mechanisms and tools to reduce or eliminate the need for direct access or manual processing of data. This reduces the risk of mishandling or modification and human error when handling sensitive data.
- **Prepare for security events:** Prepare for an incident by having incident management and investigation policy and processes that align to your organizational requirements. Run incident response simulations and use tools with automation to increase your speed for detection, investigation, and recovery.


---

## Part 2 - Best Practice for Security

There are six best practice areas for security in the cloud:

- Security
- Identity and Access Management
- Detection
- Infrastructure Protection
- Data Protection
- Incident Response

### Security

To operate our workload securely, we must apply overarching best practices to every area of security. Take requirements and processes that we have defined in operational excellence at an organizational and workload level, and apply them to all areas.

Staying up to date with AWS and industry recommendations and threat intelligence helps us evolve our threat model and control objectives. Automating security processes, testing, and validation allow us to scale our security operations.

**Q: How do you securely operate your workload?**

To operate our workload securely, we must apply overarching best practices to every area of security. Take requirements and processes that we have defined in operational excellence at an organizational and workload level, and apply them to all areas. Staying up to date with AWS and industry recommendations and threat intelligence helps us evolve our threat model and control objectives. Automating security processes, testing, and validation allow us to scale our security operations.


**Best Practices For Security:**

- **Separate workloads using accounts:** Organize workloads in separate accounts and group accounts based on function or a common set of controls rather than mirroring your company’s reporting structure. Start with security and infrastructure in mind to enable your organization to set common guardrails as your workloads grow.
- **Secure AWS account:** Secure access to your accounts, for example by enabling MFA and restrict use of the root user, and configure account contacts.
- **Identify and validate control objectives:** Based on your compliance requirements and risks identified from your threat model, derive and validate the control objectives and controls that you need to apply to your workload. Ongoing validation of control objectives and controls help you measure the effectiveness of risk mitigation.
- **Keep up to date with security threats:** Recognize attack vectors by staying up to date with the latest security threats to help you define and implement appropriate controls.
- **Keep up to date with security recommendations:** Stay up to date with both AWS and industry security recommendations to evolve the security posture of your workload.
- **Automate testing and validation of security controls in pipelines:** Establish secure baselines and templates for security mechanisms that are tested and validated as part of your build, pipelines, and processes. Use tools and automation to test and validate all security controls continuously. For example, scan items such as machine images and infrastructure as code templates for security vulnerabilities, irregularities, and drift from an established baseline at each stage.
- **Identify and prioritize risks using a threat model:** Use a threat model to identify and maintain an up-to-date register of potential threats. Prioritize your threats and adapt your security controls to prevent, detect, and respond. Revisit and maintain this in the context of the evolving security landscape.
- **Evaluate and implement new security services and features regularly:** AWS and APN Partners constantly release new features and services that allow you to evolve the security posture of your workload.


### Identity and Access Management

Identity and access management are key parts of an information security program, ensuring that only authorized and authenticated users and components are able to access your resources, and only in a manner that we intend. For example, we should define principals (that is, accounts, users, roles, and services that can perform actions in our account), build out policies aligned with these principals, and implement strong credential management. These privilege-management elements form the core of authentication and authorization.

In AWS, privilege management is primarily supported by the AWS Identity and Access Management (IAM) service, which allows us to control user and programmatic access to AWS services and resources. We should apply granular policies, which assign permissions to a user, group, role, or resource. We also have the ability to require strong password practices, such as complexity level, avoiding re-use, and enforcing multi-factor authentication (MFA). We can use federation with our existing directory service. For workloads that require systems to have access to AWS, IAM enables secure access through roles, instance profiles, identity federation, and temporary credentials.


**Q: How do you manage identities for people and machines?**

There are two types of identities we need to manage when approaching operating secure AWS workloads. Understanding the type of identity you need to manage and grant access helps you ensure the right identities have access to the right resources under the right conditions. Human Identities: Our administrators, developers, operators, and end users require an identity to access our AWS environments and applications. These are members of our organization, or external users with whom we collaborate, and who interact with your AWS resources via a web browser, client application, or interactive command-line tools. Machine Identities: Our service applications, operational tools, and workloads require an identity to make requests to AWS services - for example, to read data. These identities include machines running in your AWS environment such as Amazon EC2 instances or AWS Lambda functions. We may also manage machine identities for external parties who need access. Additionally, we may also have machines outside of AWS that need access to our AWS environment.

**Best Practices for Identity and Access Management:**

- **Use strong sign-in mechanisms:** Enforce minimum password length, and educate users to avoid common or re-used passwords. Enforce multi-factor authentication (MFA) with software or hardware mechanisms to provide an additional layer.
- **Use temporary credentials:** Require identities to dynamically acquire temporary credentials. For workforce identities, use AWS Single Sign-On, or federation with IAM roles to access AWS accounts. For machine identities, require the use of IAM roles instead of long term access keys.
- **Store and use secrets securely:** For workforce and machine identities that require secrets such as passwords to third party applications, store them with automatic rotation using the latest industry standards in a specialized service.
- **Rely on a centralized identity provider:** For workforce identities, rely on an identity provider that enables you to manage identities in a centralized place. This enables you to create, manage, and revoke access from a single location making it easier to manage access. This reduces the requirement for multiple credentials and provides an opportunity to integrate with HR processes.
- **Audit and rotate credentials periodically:** When you cannot rely on temporary credentials and require long term credentials, audit credentials to ensure that the defined controls (for example, MFA) are enforced, rotated regularly, and have appropriate access level.
- **Leverage user groups and attributes:** Place users with common security requirements in groups defined by your identity provider, and put mechanisms in place to ensure that user attributes that may be used for access control (e.g., department or location) are correct and updated. Use these groups and attributes, rather than individual users, to control access. This allows you to manage access centrally by changing a user’s group membership or attributes once, rather than updating many individual policies when a user’s access needs change.


---

## Part 3 - Insert Summary

Insert Instructions
