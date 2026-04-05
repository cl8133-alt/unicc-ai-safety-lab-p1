# Governance Framework Mapping
## UNICC AI Safety Lab — Project 1

OWASP and MITRE ATT&CK are mandatory per memorandum.

---

## OWASP Top 10 for LLM Applications — Mandatory

| OWASP Risk | System Layer | How Addressed |
|------------|-------------|---------------|
| LLM01 — Prompt Injection | Security Judge | Detects instruction override attempts and jailbreak patterns |
| LLM02 — Insecure Output Handling | Governance Judge | Checks for unsafe output patterns and information leakage |
| LLM03 — Training Data Poisoning | Input layer | Agent lineage documentation required at submission |
| LLM04 — Model Denial of Service | Infrastructure | DGX cluster partition isolation |
| LLM05 — Supply Chain Vulnerabilities | Deployment config | Open-weight model with documented version |
| LLM06 — Sensitive Information Disclosure | Governance Judge | PII detection and disclosure behavior checks |
| LLM07 — Insecure Plugin Design | Security Judge | Tool-calling behavior evaluation |
| LLM08 — Excessive Agency | Governance Judge | Autonomous action detection and human oversight checks |
| LLM09 — Overreliance | Ethics Judge | Transparency gap detection |
| LLM10 — Model Theft | Infrastructure | Access control and partition isolation |

---

## MITRE ATT&CK — Mandatory

| Technique | ID | How Addressed |
|-----------|-----|---------------|
| Exploit Public-Facing Application | T1190 | Security Judge adversarial prompt injection battery |
| Phishing | T1566 | Security Judge social engineering pattern detection |
| Command and Scripting Interpreter | T1059 | Governance Judge code execution attempt detection |
| Valid Account impersonation | T1078 | Security Judge identity override and role-play jailbreak detection |
| Obfuscated Files or Information | T1027 | Security Judge encoded prompt detection |
| Data from Cloud Storage | T1530 | Governance Judge unauthorized data access detection |
| Data Manipulation | T1565 | Ethics Judge hallucination and manipulation detection |

---

## EU AI Act 2024

| Requirement | Implementation |
|-------------|---------------|
| Prohibited practices Art 5 | Ethics Judge checks for biometric categorization and social scoring |
| High-risk requirements Art 9-15 | Governance Judge evaluates risk management documentation |
| Transparency obligations Art 50 | Ethics Judge verifies AI systems disclose their AI nature |
| Human oversight Art 14 | Any three-way judge disagreement escalates to human review |

---

## NIST AI RMF 2023

| Function | Implementation |
|----------|---------------|
| GOVERN | Three-judge council structure and policy refresh mechanism |
| MAP | Each judge maps submitted agent to appropriate risk dimension |
| MEASURE | Three-judge scoring with composite 0-1 risk score |
| MANAGE | SAFE or UNSAFE verdict with specific violations listed |

---

## UNESCO AI Ethics

| Principle | Implementation |
|-----------|---------------|
| Proportionality and do no harm | Three-judge evaluation ensures proportional assessment |
| Fairness and non-discrimination | Governance and Ethics judges both evaluate for bias |
| Right to privacy | Governance Judge performs PII detection on every submission |
| Transparency | Each judge provides specific reasons not just a score |
| Human oversight | Full audit trail enables human review of every decision |
