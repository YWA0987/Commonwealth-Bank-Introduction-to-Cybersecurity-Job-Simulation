# Commonwealth-Bank-Introduction-to-Cybersecurity-Job-Simulation
This repository documents my work from the **Commonwealth Bank Introduction to Cybersecurity Job Simulation on Forage


The simulation provided hands-on experience across several areas of cybersecurity, including:

- Security data analysis with Splunk
- Fraud detection and visualization
- Incident response
- Security awareness
- Web application security
- Technical documentation

I completed **Tasks 1–3 independently** using the provided instructions, datasets, and scenarios.

For the penetration testing portion in **Task 4**, I first attempted the exercises myself. When I needed additional help, I reviewed PortSwigger's educational material and guidance, reproduced the techniques within the authorized training environment, and focused on understanding why each vulnerability worked and how it could be prevented.

> **Disclaimer:** This was an educational job simulation completed through Forage and does not represent employment with Commonwealth Bank. All web security testing was performed exclusively within PortSwigger Web Security Academy's intentionally vulnerable and authorized training environments.

---

## Project Overview

The simulation consisted of four cybersecurity-focused tasks:

1. **Fraud Detection Analysis using Splunk**
2. **Incident Response Analysis**
3. **Password Security and Security Awareness**
4. **Web Application Security using PortSwigger Web Security Academy**

The project gave me experience working with security-related data, investigating cybersecurity scenarios, communicating security recommendations, and developing an introductory understanding of common web application vulnerabilities.

---

# Task 1 — Fraud Detection Analysis with Splunk

## Objective

The first task involved analyzing transaction data using **Splunk Enterprise** and creating a dashboard to identify and visualize fraudulent activity.

I imported the provided transaction dataset into Splunk, configured the data for searching, explored the available fields, created SPL searches, and built a dashboard containing multiple visualizations.

This task was completed independently.

## Tools Used

- Splunk Enterprise
- Search Processing Language (SPL)
- CSV transaction data
- Splunk dashboards
- Data visualization

## Analysis Performed

The dashboard included analysis of:

- Transaction count by category
- Total fraudulent transactions
- Transaction count by age group
- Transaction count by merchant
- Fraudulent transactions by category
- Fraudulent transactions by age group
- Fraudulent transactions by transaction step/month code
- Fraudulent transactions by gender and category
- Fraudulent activity by age group and merchant

The analyzed dataset contained **92 fraudulent transactions**.

## Example SPL Searches

### Search the imported dataset

```spl
sourcetype="fraud_detection.csv"
```

### Filter fraudulent transactions

```spl
sourcetype="fraud_detection.csv" fraud="1"
```

### Count fraudulent transactions by category

```spl
sourcetype="fraud_detection.csv" fraud="1"
| stats count by category
```

### Compare fraud by gender and category

```spl
sourcetype="fraud_detection.csv" fraud="1"
| chart count over category by gender
```

## Troubleshooting

While completing the exercise, I encountered an issue where an example SPL query referenced a different sourcetype than the one assigned to my imported dataset.

I recognized that Splunk was searching for events using the wrong sourcetype and updated the query to reference:

```spl
sourcetype="fraud_detection.csv"
```

After correcting the sourcetype, the expected search results and visualizations appeared.

This helped reinforce my understanding of how Splunk searches depend on correctly referencing indexed data and its associated metadata.

## What I Learned

The biggest concept I learned from this task was the basic Splunk analysis workflow:

```text
Import Data → Search → Filter → Aggregate → Visualize → Interpret
```

I also gained practical experience using SPL to summarize structured data and convert search results into visualizations that communicate useful patterns.

---

# Task 2 — Incident Response

## Objective

The second task focused on responding to a simulated cybersecurity incident.

I reviewed the provided incident information, analyzed the situation, considered the potential security impact, and developed a structured response based on the scenario.

This task was completed independently.

## Areas Considered

The exercise required thinking about several parts of cybersecurity incident response:

- Understanding what occurred
- Identifying affected systems or information
- Evaluating potential impact
- Determining appropriate response actions
- Considering containment
- Considering recovery
- Recommending preventative measures
- Communicating findings clearly

## What I Learned

This task helped me understand that cybersecurity incident response involves more than identifying the technical cause of an event.

Security teams must also determine:

- What was affected
- How serious the incident is
- What should be contained first
- How normal operations can be restored
- How similar incidents can be prevented
- How findings should be communicated to stakeholders

The exercise also gave me practice organizing security findings into a professional written deliverable.

---

# Task 3 — Password Security and Security Awareness

## Objective

The third task focused on password security and communicating cybersecurity guidance to users.

Using the provided scenario and requirements, I created security-awareness material designed to communicate safer password and authentication practices.

This task was completed independently.

## Topics Covered

- Strong password practices
- Authentication security
- Avoiding insecure password behavior
- User security awareness
- Preventative security controls
- Communicating technical concepts to non-technical users

## What I Learned

One of the main lessons from this task was that cybersecurity is not only a technical problem.

Employees and users are an important part of an organization's security posture.

Security controls are more effective when users understand:

- Why the controls exist
- What risks they help prevent
- How to follow security practices correctly

This task also gave me experience translating cybersecurity concepts into guidance intended for a non-technical audience.

---

# Task 4 — Web Application Security

## Objective

The final task introduced web application security concepts using **PortSwigger Web Security Academy**.

PortSwigger provides intentionally vulnerable web applications specifically designed for safe and legal cybersecurity training.

I completed **11 beginner-level labs** covering several common web application vulnerability categories.

I first attempted each challenge myself. When I was unable to fully solve or understand a lab, I used PortSwigger's educational resources and additional guidance to understand the solution.

I then reproduced the technique within the authorized training environment and focused on understanding:

- What caused the vulnerability
- Why the technique worked
- What security impact it could have
- How the vulnerability could be prevented

This portion represents **guided cybersecurity learning**, not independent professional penetration testing.

---

## Vulnerabilities Studied

### SQL Injection

The SQL injection exercises demonstrated how insecure database queries can allow user-controlled input to modify SQL logic.

Topics included:

- Authentication bypass
- Hidden data exposure
- Manipulating SQL query conditions

One exercise demonstrated how SQL comment syntax could alter an insecure authentication query.

For example:

```text
administrator'--
```

The apostrophe closes the existing SQL string, while `--` causes the remaining portion of the SQL statement to be treated as a comment.

In an insecure authentication query, this can cause the password comparison to no longer be evaluated.

Another exercise demonstrated the use of:

```text
' OR 1=1--
```

Because:

```text
1=1
```

is always true, the condition can cause a vulnerable query to return records that would normally remain hidden.

These exercises helped me understand why **parameterized queries and prepared statements** are important defenses against SQL injection.

---

### Reflected Cross-Site Scripting

The reflected XSS lab demonstrated how user-controlled input can become executable browser content when an application returns that input without safely encoding it.

I learned that applications should treat untrusted input as data rather than executable content.

---

### Stored Cross-Site Scripting

The stored XSS exercise demonstrated how malicious input can become more dangerous when it is saved by an application and later displayed to other users.

This helped me understand the difference between:

- Reflected XSS
- Stored XSS

---

### DOM-Based Cross-Site Scripting

The DOM-based XSS exercise demonstrated that security vulnerabilities can also originate from client-side JavaScript.

I learned that insecure processing of user-controlled data inside the browser can create vulnerabilities even when the server itself is not directly generating malicious content.

---

### Broken Access Control

The access-control exercises demonstrated why simply hiding administrative functionality is not sufficient security.

Sensitive functionality should always have server-side authorization controls that verify whether a user is actually permitted to access it.

---

### Hidden Administrative Functionality

Another exercise demonstrated the risks of relying on hidden or unlinked administrative pages.

A major takeaway was:

> **A resource being difficult to find does not make it secure.**

Authorization must still be enforced by the application.

---

### Username Enumeration

The username-enumeration exercise demonstrated how differences in authentication responses can unintentionally reveal whether an account exists.

This showed how seemingly small differences in error messages or application behavior can provide useful information to an attacker.

---

### Two-Factor Authentication Bypass

This exercise demonstrated that multi-factor authentication only provides protection when every stage of authentication is correctly enforced.

If application logic allows a required authentication step to be skipped, the additional security control can become ineffective.

---

### File Path Traversal

The path-traversal exercise demonstrated how insecure handling of user-controlled file paths can allow access to files outside the directory intended by an application.

I learned why applications should restrict filesystem access and avoid trusting raw user-supplied paths.

---

### Operating System Command Injection

The command-injection exercise demonstrated the danger of allowing user-controlled input to influence operating system commands.

This introduced me to the importance of:

- Separating user input from executable commands
- Validating inputs
- Using allowlists
- Avoiding unnecessary operating system commands
- Following the principle of least privilege

---

## What I Learned from PortSwigger

The main goal of this portion was not to memorize exploit payloads.

Instead, I focused on understanding the patterns that caused the vulnerabilities.

Several concepts appeared repeatedly:

- User-controlled input should never automatically be trusted.
- Database commands should remain separate from user-controlled data.
- Browser output should safely handle untrusted content.
- Authentication must be enforced on the server.
- Authorization should protect every sensitive resource.
- Hidden functionality is not the same as protected functionality.
- Filesystem access should be restricted.
- Applications should avoid unsafe operating system command execution.

One of the biggest lessons was that understanding **why** a technique works is more useful than simply knowing what input completes a training lab.

---

# Skills Developed

Through this simulation, I gained introductory hands-on experience with:

- Splunk Enterprise
- Search Processing Language (SPL)
- Security data analysis
- Dashboard development
- Data visualization
- Fraud analysis
- Incident response
- Security documentation
- Security awareness
- Authentication concepts
- Web application security
- SQL injection fundamentals
- Cross-site scripting concepts
- Access-control concepts
- Path traversal concepts
- Command-injection concepts
- Technical troubleshooting
- Communicating technical findings

---

# Key Takeaways

The Commonwealth Bank cybersecurity simulation exposed me to several areas of cybersecurity within a single project.

The **Splunk task** gave me practical experience importing, searching, analyzing, and visualizing structured data.

The **incident-response task** introduced me to analyzing a cybersecurity incident from both a technical and organizational perspective.

The **security-awareness task** demonstrated the importance of communicating cybersecurity guidance effectively to users.

The **PortSwigger labs** provided introductory exposure to how common web application vulnerabilities occur and why secure application-development practices are important.

A major lesson throughout the simulation was:

> Cybersecurity is not only about finding a vulnerability. It also requires understanding why the vulnerability exists, determining its potential impact, communicating the problem clearly, and identifying how it can be prevented.

---

# Repository Structure

```text
commonwealth-bank-cybersecurity-simulation/
│
├── README.md
│
├── splunk-fraud-analysis/
│   ├── fraud-detection-dashboard.pdf
│   
│
├── incident-response/
│   └── incident-response-report.pdf
│
├── security-awareness/
│   └── password-security-awareness.pdf
│
└── web-security/
    └── portswigger-learning-notes.md
```

---

# Ethical and Educational Use

All cybersecurity activities documented in this repository were performed within authorized educational environments.

The web application security exercises were completed exclusively using **PortSwigger Web Security Academy**, which provides intentionally vulnerable applications specifically for legal security training.

No techniques documented in this project were tested against unauthorized websites, systems, applications, or infrastructure.

---

# About the Simulation

This project was completed through the **Commonwealth Bank Introduction to Cybersecurity Job Simulation on Forage**.

It was an educational simulation designed to provide exposure to cybersecurity-related work.

This experience does **not** represent employment, an internship, contract work, or professional cybersecurity services performed for Commonwealth Bank.

---

## Author

**Yaqub Wafi Ahmed**
**Interests:** Information Technology, Cloud Infrastructure, Networking, and Cybersecurity
