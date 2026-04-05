# Functional Requirements Specification
## UNICC AI Safety Lab — Project 1

**TO:** Dr. Andrés Fortino
**FROM:** Coreece Lopez — Project 1 Manager
**DATE:** March 2, 2026
**COURSE:** NYU MASY GC-4100 Applied Project Capstone — Spring 2026

---

## Project Goal

Project 1 establishes the foundational research, governance framework, and system architecture for the UNICC AI Safety Lab. Project 1 must be fully complete before Project 2 (Feruza) begins. Project 1 delivers the architecture blueprint, JSON schema, governance mapping, integration spec, and validated model environment. Coreece does NOT write judge code, council code, or interface code.

**Memorandum research question:**
> "How can a standalone Small Language Model, trained on open-source LLM weights and deployed in an on-premises environment, be systematically evaluated, stress-tested, and incrementally trained to support governance, risk, and compliance testing of AI bots and agents?"

**Memorandum organizational objective:**
> "Deploy an operational AI Safety Lab based on a standalone small language model that integrates the top three AI safety testing solutions from Fall 2025 into a multi-module inference ensemble."

---

## Requirement 1 — Infrastructure and Deployment

- The system shall use Mistral-7B-Instruct-v0.3 as the open-weight SLM running via Ollama on the NYU DGX Spark cluster
- Ollama must be installed and running before the test script executes
- As a fallback the system shall use the Anthropic API when Ollama is not available
- The API key shall be stored in a .env file and never hardcoded or pushed to GitHub
- The system shall validate deployment by running a minimum of 20 predefined test prompts
- All model inputs and outputs shall be logged to JSONL format
- The system shall achieve a minimum 95% successful response rate across all 20 test prompts

## Requirement 2 — Governance Alignment

- The system shall map to OWASP Top 10 for LLM Applications — mandatory per memorandum
- The system shall map to the MITRE ATT&CK Framework — mandatory per memorandum
- The system shall align with EU AI Act 2024, NIST AI RMF 2023, ISO 42001 2023, and UNESCO AI Ethics Recommendations

## Requirement 3 — Council-of-Experts Architecture

- The system shall define a five-layer architecture integrating the top three Fall 2025 solutions as independent judge modules
- The Security Judge shall be based on Team 1 adaptive adversarial testing framework
- The Governance Judge shall be based on Team 6 policy compliance platform
- The Ethics Judge shall be based on Team 8 evaluation agent
- Arbitration logic shall apply majority rule: two of three unsafe votes produces an UNSAFE verdict
- The unified JSON output schema shall define the exact format every judge must return

## Requirement 4 — Documentation and Integration

- A complete FRS shall be submitted to Dr. Fortino by March 2 2026
- The integration specification shall define clear handoff boundaries for Projects 2 and 3
- The unified JSON output schema shall be published in schemas/output_schema.json
- All files shall be deposited in a public GitHub repository at https://github.com/cl8133-alt/unicc-ai-safety-lab-p1

---

## Deliverable Timeline

| Deliverable | Due Date | Completion Metric |
|-------------|----------|-------------------|
| FRS document | March 2 2026 | Document submitted to Dr. Fortino |
| SLM deployed on DGX | March 9 2026 | 20 prompts logged with real non-zero scores |
| Architecture blueprint | March 16 2026 | Architecture and governance mapping complete |
| Full documentation and GitHub | March 23 2026 | All 11 files in public repo, integration spec signed off with Feruza |
