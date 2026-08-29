# Incident Response Analysis

## 1. Likely Attack Vector

The incident was likely caused by an **email phishing attack that led to a ransomware infection**.

Employees received an email pretending to be from a legitimate source and were directed to a fake login portal. After entering their usernames and passwords, their credentials were stolen.

---

## 2. Initial Incident Response Actions

The initial response should include:

- Identify and document the affected users and systems
- Examine the phishing email and any malicious link or file
- Review relevant logs for indicators of compromise
- Determine the scope of the incident
- Preserve evidence for investigation
- Escalate and report the incident through the organization's incident-response process
- Isolate systems that are actively affected when necessary

---

## 3. Containment, Resolution, and Recovery

### Contain

- Isolate affected computers from the network
- Disable compromised employee accounts

### Resolve

- Identify and remove malicious software from affected systems
- Patch or secure any vulnerabilities related to the incident

### Recover

- Restore affected systems from clean backups
- Reset compromised credentials
- Verify that restored systems are clean
- Monitor systems for additional suspicious activity

---

## 4. Preventative Measures

Recommended measures to reduce the likelihood or impact of similar incidents include:

- Employee phishing and security-awareness training
- Network segmentation
- Multi-factor authentication (MFA)
- Updating security controls and incident-response procedures
