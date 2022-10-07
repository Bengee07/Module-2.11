## Brief

### Preparation


### Self Study Check In

Q1: How important security for you?

Q2: Do you trust people around you?

Q3: How do you manage permissions for people and machines?


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

## Part 2 - Best Practice for Security - Group Discussion

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


### Detection

We can use detective controls to identify a potential security threat or incident. They are an essential part of governance frameworks and can be used to support a quality process, a legal or compliance obligation, and for threat identification and response efforts. There are different types of detective controls. For example, conducting an inventory of assets and their detailed attributes promotes more effective decision making (and lifecycle controls) to help establish operational baselines. We can also use internal auditing, an examination of controls related to information systems, to ensure that practices meet policies and requirements and that we have set the correct automated alerting notifications based on defined conditions. These controls are important reactive factors that can help our organization identify and understand the scope of anomalous activity.

In AWS, we can implement detective controls by processing logs, events, and monitoring that allows for auditing, automated analysis, and alarming. CloudTrail logs, AWS API calls, and CloudWatch provide monitoring of metrics with alarming, and AWS Config provides configuration history. Amazon GuardDuty is a managed threat detection service that continuously monitors for malicious or unauthorized behavior to help us protect your AWS accounts and workloads. Service-level logs are also available, for example, we can use Amazon Simple Storage Service (Amazon S3) to log access requests.


**Q: How do you detect and investigate security events?**

Capture and analyze events from logs and metrics to gain visibility. Take action on security events and potential threats to help secure your workload.

**Best Practices for Detection:**

- **Configure service and application logging:** Configure logging throughout the workload, including application logs, resource logs, and AWS service logs. For example, ensure that AWS CloudTrail, Amazon CloudWatch Logs, Amazon GuardDuty and AWS Security Hub are enabled for all accounts within your organization.
- **Analyze logs, findings, and metrics centrally:** All logs, metrics, and telemetry should be collected centrally, and automatically analyzed to detect anomalies and indicators of unauthorized activity. A dashboard can provide you easy to access insight into real-time health. For example, ensure that Amazon GuardDuty and Security Hub logs are sent to a central location for alerting and analysis.
- **Automate response to events:** Using automation to investigate and remediate events reduces human effort and error, and enables you to scale investigation capabilities. Regular reviews will help you tune automation tools, and continuously iterate. For example, automate responses to Amazon GuardDuty events by automating the first investigation step, then iterate to gradually remove human effort.
- **Implement actionable security events:** Create alerts that are sent to and can be actioned by your team. Ensure that alerts include relevant information for the team to take action. For example, ensure that Amazon GuardDuty and AWS Security Hub alerts are sent to the team to action, or sent to response automation tooling with the team remaining informed by messaging from the automation framework.


Log management is important to a Well-Architected workload for reasons ranging from security or forensics to regulatory or legal requirements. It is critical that you analyze logs and respond to them so that you can identify potential security incidents. AWS provides functionality that makes log management easier to implement by giving you the ability to define a data-retention lifecycle or define where data will be preserved, archived, or eventually deleted. This makes predictable and reliable data handling simpler and more cost effective.


### Infrastructure Protection

Infrastructure protection encompasses control methodologies, such as defense in depth, necessary to meet best practices and organizational or regulatory obligations. Use of these methodologies is critical for successful, ongoing operations in either the cloud or on-premises.

In AWS, we can implement stateful and stateless packet inspection, either by using AWS-native technologies or by using partner products and services available through the AWS Marketplace. We should use Amazon Virtual Private Cloud (Amazon VPC) to create a private, secured, and scalable environment in which we can define our topology—including gateways, routing tables, and public and private subnets.

**Q: How do you protect your network resources?**

Any workload that has some form of network connectivity, whether it’s the internet or a private network, requires multiple layers of defense to help protect from external and internal network-based threats.


**Best Practices for Infrastructure Protection:**

- **Create network layers:** Group components that share reachability requirements into layers. For example, a database cluster in a VPC with no need for internet access should be placed in subnets with no route to or from the internet. In a serverless workload operating without a VPC, similar layering and segmentation with microservices can achieve the same goal.
- **Control traffic at all layers:** Apply controls with a defense in depth approach for both inbound and outbound traffic. For example, for Amazon Virtual Private Cloud (VPC) this includes security groups, Network ACLs, and subnets. For AWS Lambda, consider running in your private VPC with VPC-based controls.
- **Automate network protection:** Automate protection mechanisms to provide a self-defending network based on threat intelligence and anomaly detection. For example, intrusion detection and prevention tools that can pro-actively adapt to current threats and reduce their impact.
- **Implement inspection and protection:** Inspect and filter your traffic at each layer. For example, use a web application firewall to help protect against inadvertent access at the application network layer. For Lambda functions, third-party tools can add application-layer firewalling to your runtime environment.


### Data Protection

Before architecting any system, foundational practices that influence security should be in place. For example, data classification provides a way to categorize organizational data based on levels of sensitivity, and encryption protects data by way of rendering it unintelligible to unauthorized access. These tools and techniques are important because they support objectives such as preventing financial loss or complying with regulatory obligations.

In AWS, the following practices facilitate protection of data:

- As an AWS customer you maintain full control over your data.
- AWS makes it easier for you to encrypt your data and manage keys, including regular key rotation, which can be easily automated by AWS or maintained by you.
- Detailed logging that contains important content, such as file access and changes, is available.
- AWS has designed storage systems for exceptional resiliency. For example, Amazon S3 Standard, S3 Standard–IA, S3 One Zone-IA, and Amazon Glacier are all designed to provide 99.999999999% durability of objects over a given year. This durability level corresponds to an average annual expected loss of 0.000000001% of objects.
- Versioning, which can be part of a larger data lifecycle management process, can protect against accidental overwrites, deletes, and similar harm.
- AWS never initiates the movement of data between Regions. Content placed in a Region will remain in that Region unless you explicitly enable a feature or leverage a service that provides that functionality.


**Q: How do you classify your data?**

Classification provides a way to categorize data, based on criticality and sensitivity in order to help you determine appropriate protection and retention controls.

Best Practices:
- Identify the data within your workload: This includes the type and classification of data, the associated business processes. data owner, applicable legal and compliance requirements, where it’s stored, and the resulting controls that are needed to be enforced. This may include classifications to indicate if the data is intended to be publicly available, if the data is internal use only such as customer personally identifiable information (PII), or if the data is for more restricted access such as intellectual property, legally privileged or marked sensititve, and more.
- Define data protection controls: Protect data according to its classification level. For example, secure data classified as public by using relevant recommendations while protecting sensitive data with additional controls.
- Automate identification and classification: Automate identification and classification of data to reduce the risk of human error from manual interactions.
- Define data lifecycle management: Your defined lifecycle strategy should be based on sensitivity level, as well as legal and organization requirements. Aspects including the duration you retain data for, data destruction, data access management, data transformation, and data sharing should be considered.

**Q: How do you protect your data at rest?**
Protect your data at rest by implementing multiple controls, to reduce the risk of unauthorized access or mishandling.

Best Practices:
- Implement secure key management: Encryption keys must be stored securely, with strict access control, for example, by using a key management service such as AWS KMS. Consider using different keys, and access control to the keys, combined with the AWS IAM and resource policies, to align with data classification levels and segregation requirements.
- Enforce encryption at rest: Enforce your encryption requirements based on the latest standards and recommendations to help protect your data at rest.
- Automate data at rest protection: Use automated tools to validate and enforce data at rest protection continuously, for example, verify that there are only encrypted storage resources.
- Enforce access control: Enforce access control with least privileges and mechanisms, including backups, isolation, and versioning, to help protect your data at rest. Prevent operators from granting public access to your data.
- Use mechanisms to keep people away from data: Keep all users away from directly accessing sensitive data and systems under normal operational circumstances. For example, provide a dashboard instead of direct access to a data store to run queries. Where CI/CD pipelines are not used, determine which controls and processes are required to adequately provide a normally disabled break-glass access mechanism.


### Incident Response

Even with extremely mature preventive and detective controls, our organization should still put processes in place to respond to and mitigate the potential impact of security incidents. The architecture of our workload strongly affects the ability of your teams to operate effectively during an incident, to isolate or contain systems, and to restore operations to a known good state. Putting in place the tools and access ahead of a security incident, then routinely practicing incident response through game days, will help you ensure that your architecture can accommodate timely investigation and recovery.

In AWS, the following practices facilitate effective incident response:

- Detailed logging is available that contains important content, such as file access and changes.
- Events can be automatically processed and trigger tools that automate responses through the use of AWS APIs.
- We can pre-provision tooling and a “clean room” using AWS CloudFormation. This allows us to carry out forensics in a safe, isolated environment.


**Q: How do you anticipate, respond to, and recover from incidents?**

Preparation is critical to timely and effective investigation, response to, and recovery from security incidents to help minimize disruption to your organization.


Best Practices:

- **Identify key personnel and external resources:** Identify internal and external personnel, resources, and legal obligations that would help your organization respond to an incident.
- **Develop incident management plans:** Create plans to help you respond to, communicate during, and recover from an incident. For example, you can start an incident response plan with the most likely scenarios for your workload and organization. Include how you would communicate and escalate both internally and externally.
- **Prepare forensic capabilities:** Identify and prepare forensic investigation capabilities that are suitable, including external specialists, tools, and automation.
- **Automate containment capability:** Automate containment and recovery of an incident to reduce response times and organizational impact.
- **Pre-provision access:** Ensure that incident responders have the correct access pre-provisioned into AWS to reduce the time for investigation through to recovery.
- **Pre-deploy tools:** Ensure that security personnel have the right tools pre-deployed into AWS to reduce the time for investigation through to recovery.
- **Run game days:** Practice incident response game days (simulations) regularly, incorporate lessons learned into your incident management plans, and continuously improve.

---
