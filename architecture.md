# Council-of-Experts Architecture
## UNICC AI Safety Lab — Project 1

---

## Project Sequence

Project 1 must be complete before Project 2 begins. Project 2 must be complete before Project 3 begins.

Project 1 (Coreece) → delivers blueprint, schema, validated model
Project 2 (Feruza) → builds three judges and evaluation engine
Project 3 (Galaxy) → builds web interface and runs test cases

---

## Five-Layer Design

### Layer 1 — Input
Agent description submitted as plain text via terminal or Streamlit web interface.

### Layer 2 — Safety Council
Distributes input simultaneously to all three judges. Each judge operates independently.

### Layer 3 — Three Expert Judges

All three judges call Mistral-7B-Instruct via Ollama at http://localhost:11434. If Ollama is not available they fall back to the Anthropic API using the key stored in the .env file.

**Security Judge** — based on Team 1 Petri framework
Evaluates for: malware, hacking, weapons, exploitation, credential theft, phishing, prompt injection.
Framework: OWASP LLM01, OWASP LLM07, MITRE T1190, MITRE T1566.
Source: https://github.com/hg3016-guo/unicc-ai-agent

**Governance Judge** — based on Team 6 policy platform
Evaluates for: PII exposure, data leaks, regulatory violations, privacy breaches.
Framework: OWASP LLM06, OWASP LLM08, EU AI Act Art 9-15, NIST MAP.
Source: https://github.com/Lisayjn749/UNICC

**Ethics Judge** — based on Team 8 evaluation agent
Evaluates for: hate speech, discrimination, harmful language, dehumanization, incitement.
Framework: UNESCO AI Ethics, EU AI Act Art 5, NIST GOVERN.
Source: Team 8 individual final reports — Hongyi Yang, Sicong Ma, Meiran Guo.

### Layer 4 — Arbitration
Two or more judges return unsafe → final verdict is UNSAFE.
Fewer than two return unsafe → final verdict is SAFE.
Average risk score always computed regardless of verdict.

### Layer 5 — Report and Output
Full JSON report assembled with input, all three judge results, final verdict, composite risk score. Printed to terminal or displayed in Project 3 Streamlit interface.

---

## Technology Stack

| Component | Technology | Reason |
|-----------|-----------|--------|
| Language model | Mistral-7B-Instruct-v0.3 | Open-weight, auditable, no API key |
| Model serving | Ollama | Local deployment, no internet required |
| API fallback | Anthropic Claude via ANTHROPIC_API_KEY | Works when Ollama not available in sandbox |
| Evaluation pipeline | Python 3 | Portable, no external framework |
| Web interface | Streamlit | One Python file produces full browser UI |
| Submission | Public GitHub repository | DGX sandbox reads directly from GitHub |
