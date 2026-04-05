# UNICC AI Safety Lab
## Project 1 — Research and Platform Preparation

**Student:** Coreece Lopez — Project 1 Manager
**Course:** NYU MASY GC-4100 Applied Project Capstone — Spring 2026
**Sponsor:** Dr. Andrés Fortino | Client: UNICC | Liaison: Joseph Papa
**Team:** Coreece Lopez (P1) · Feruza Jubaeva (P2) · Galaxy Okoro (P3)
**GitHub:** https://github.com/cl8133-alt/unicc-ai-safety-lab-p1

---

## Project Sequence

Project 1 is completed first and provides the foundation for everything else.

Project 1 (Coreece) completes first → hands off to Project 2 (Feruza) → hands off to Project 3 (Galaxy)

---

## What This Project Is

Project 1 establishes the research documentation, system architecture, governance framework mapping, and validated model environment for the UNICC AI Safety Lab. Project 1 does NOT write judge code, council code, or interface code — those belong to Projects 2 and 3.

The memorandum research question:
"How can a standalone Small Language Model, trained on open-source LLM weights and deployed in an on-premises environment, be systematically evaluated, stress-tested, and incrementally trained to support governance, risk, and compliance testing of AI bots and agents?"

---

## Prerequisites

Option 1 — Local no API key needed:
1. Install Ollama from https://ollama.com
2. Run: ollama pull mistral:7b-instruct
3. Run: ollama serve

Option 2 — API fallback for sandbox environments:
1. Create a .env file in the root with this line:
   ANTHROPIC_API_KEY=your_actual_key_here
2. Upload the .env file through the sandbox portal file upload

---

## How to Run the Baseline Test

python3 scripts/test_model.py

This runs 20 prompts and logs every result. Real non-zero scores confirm the model is working. A score of 0.0 on all prompts means the model connection failed.

---

## For DGX Sandbox Evaluators

1. Add environment variable in sandbox settings:
   Name: ANTHROPIC_API_KEY
   Value: your_anthropic_api_key

   OR upload a .env file containing:
   ANTHROPIC_API_KEY=your_anthropic_api_key

2. Advanced commands:
   Runtime: Python
   Setup command: pip install -r requirements.txt
   Run command: python3 scripts/test_model.py

---

## System Architecture — Five Layers

Layer 1 — Input: Agent description submitted via terminal or web interface.
Layer 2 — Safety Council: Distributes input to all three judges simultaneously.
Layer 3 — Three Expert Judges:
  Security Judge — checks for malware, hacking, weapons, exploitation
  Governance Judge — checks for PII, data leaks, regulatory violations
  Ethics Judge — checks for hate speech, discrimination, harmful language
Layer 4 — Arbitration: Majority rule. Two of three unsafe votes = UNSAFE.
Layer 5 — Report: Full JSON safety report with individual scores and final verdict.

---

## Fall 2025 Source Teams

| Team | Members | Role |
|------|---------|------|
| Team 1 | Jitong Yu, Haoyu Guo, Ning Sun | Security Judge foundation |
| Team 6 | Yiwen Mao, Jiakai Niu, Lisa Yu | Governance Judge foundation |
| Team 8 | Hongyi Yang, Sicong Ma, Meiran Guo | Ethics Judge foundation |

Source repos:
Team 1: https://github.com/hg3016-guo/unicc-ai-agent
Team 6: https://github.com/Lisayjn749/UNICC

---

## Governance Framework Alignment

OWASP Top 10 for LLM Applications 2023 — mandatory per memorandum
MITRE ATT&CK Framework — mandatory per memorandum
EU AI Act 2024
NIST AI Risk Management Framework 2023
ISO/IEC 42001 2023
UNESCO AI Ethics Recommendations

Full mapping in docs/governance_mapping.md

---

## Repository Structure

unicc-ai-safety-lab-p1/
├── README.md
├── requirements.txt
├── .gitignore
├── docs/
│   ├── FRS.md
│   ├── architecture.md
│   ├── deployment_config.md
│   ├── governance_mapping.md
│   └── integration_spec.md
├── scripts/
│   └── test_model.py
├── logs/
│   └── sample_test_log.jsonl
└── schemas/
    └── output_schema.json

Contact: Coreece Lopez — cl8133@nyu.edu
