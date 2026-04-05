# Integration Specification
## UNICC AI Safety Lab — Project Sequence and Handoff

---

## Project Sequence — Order Matters

Project 1 must be fully complete before Project 2 begins.
Project 2 must be fully complete before Project 3 begins.

Project 1 Coreece → delivers: architecture blueprint, JSON schema, governance mapping, validated model
Project 2 Feruza → delivers: three working judges, council, arbitration, main.py runs end to end
Project 3 Galaxy → delivers: Streamlit web interface, test cases, user documentation

---

## What Project 1 Delivers to Project 2

Architecture blueprint in docs/architecture.md — Feruza builds exactly this.
JSON output schema in schemas/output_schema.json — every judge must return this format.
Governance mapping in docs/governance_mapping.md — what each judge must evaluate.
Validated model — 20-prompt test confirms the model produces real non-zero scores.

Source teams for Feruza to adapt:
Security Judge — Team 1: https://github.com/hg3016-guo/unicc-ai-agent
Governance Judge — Team 6: https://github.com/Lisayjn749/UNICC
Ethics Judge — Team 8: Individual final reports from Hongyi Yang, Sicong Ma, Meiran Guo

Model call pattern for Feruza — Ollama with Anthropic API fallback:

import requests
import os
from pathlib import Path

def _load_env():
    env_path = Path(__file__).parent.parent / ".env"
    if env_path.exists():
        with open(env_path) as f:
            for line in f:
                line = line.strip()
                if line and not line.startswith("#") and "=" in line:
                    key, value = line.split("=", 1)
                    os.environ.setdefault(key.strip(), value.strip())

_load_env()

def call_model(prompt):
    try:
        response = requests.post(
            "http://localhost:11434/api/generate",
            json={"model": "mistral:7b-instruct", "prompt": prompt, "stream": False},
            timeout=30
        )
        response.raise_for_status()
        return response.json().get("response", "").strip()
    except Exception:
        api_key = os.environ.get("ANTHROPIC_API_KEY")
        if not api_key:
            raise RuntimeError("Ollama not running and ANTHROPIC_API_KEY not set.")
        import anthropic
        client = anthropic.Anthropic(api_key=api_key)
        message = client.messages.create(
            model="claude-sonnet-4-20250514",
            max_tokens=1024,
            messages=[{"role": "user", "content": prompt}]
        )
        return message.content[0].text

API key compliance per Dr. Fortino April 5 email:
All API calls must read from environment variables. No hardcoded keys. Use .env file pattern above. The .gitignore must prevent .env from being pushed to GitHub.

---

## What Project 2 Delivers to Project 3

Working main.py that runs end to end without crashing.
Three judge modules each returning the unified JSON format.
Council and arbitration producing a final SAFE or UNSAFE verdict.
requirements.txt containing requests, pytest, anthropic.

---

## Contact

Coreece Lopez — cl8133@nyu.edu
Any architecture or schema change must be communicated to all three team members before implementation.
