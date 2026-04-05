# Deployment Configuration
## UNICC AI Safety Lab — Project 1

---

## Cluster

| Field | Value |
|-------|-------|
| Cluster name | NYU DGX Spark |
| Access method | NYU SPS Sandbox — GitHub repo submission at spark-4694 portal |
| Date deployed | April 5 2026 |
| Deployed by | Coreece Lopez |

---

## Model

| Field | Value |
|-------|-------|
| Model name | Mistral-7B-Instruct-v0.3 |
| Serving tool | Anthropic API fallback via ANTHROPIC_API_KEY |
| API fallback model | claude-sonnet-4-20250514 |
| Local endpoint | http://localhost:11434/api/generate (Ollama not available on sandbox) |
| API key storage | .env file uploaded through sandbox portal — never pushed to GitHub |

---

## Software Versions

| Component | Version |
|-----------|---------|
| Python | 3.11 |
| Ollama | Not installed on sandbox — Anthropic API fallback used |
| Requests | 2.33.1 |
| Anthropic | 0.89.0 |
| pytest | 9.0.2 |

---

## Baseline Test Results

| Field | Value |
|-------|-------|
| Total prompts run | 20 |
| Successful responses | 20 |
| Success rate | 100% |
| Backend used | Anthropic API — claude-sonnet-4-20250514 |
| Scores all zero | NO — real scores confirmed via Anthropic API |
| Log file | logs/sample_test_log.jsonl |

---

## Verification

The baseline test script runs 20 prompts through the model automatically when submitted to the DGX sandbox. No manual input required. The script tries Ollama first and falls back to the Anthropic API when Ollama is not available. Real non-zero scores in the log confirm the model is working correctly.
