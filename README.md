# Proof of Work

Everything I've built as an AI engineer, in one place: what it does, a number that proves it works, and links to the live app and the code.

By [Tarun Chauhan](https://tarunchauhan.vercel.app) · B.Tech AI & Data Science, 2026 · Jaipur, India

---

## Index

| # | Project | Result | Live | Code |
|---|---|---|---|---|
| 1 | **CodeCave**: bilingual (English/Hindi) LLM code tutor | Explains code in Hindi and English | [trustcodecave.vercel.app](https://trustcodecave.vercel.app) | [repo](https://github.com/TarunSinghChauhan/codecave) |
| 2 | **Multi-Agent Code Review**: LangGraph review agents | Caught 4 critical vulnerabilities | none | [repo](https://github.com/TarunSinghChauhan/multi-agent-code-review) |
| 3 | **RAG Ops Platform**: Qdrant + Redis + drift detection | 75% cache hit rate | none | [repo](https://github.com/TarunSinghChauhan/rag-ops-platform) |
| 4 | **LLM Evaluation Harness**: GPT-4o vs Claude Sonnet | Cohen's κ = 0.81, 20+ adversarial patterns | none | [repo](https://github.com/TarunSinghChauhan/llm-eval-harness) |
| 5 | **HITL Approval Agent**: human-in-the-loop agent | Auto-runs at confidence ≥ 0.75, pauses otherwise | [live](https://hitl-approval-agent.vercel.app) | [repo](https://github.com/TarunSinghChauhan/hitl-approval-agent) |
| 6 | **LLM Inference Engine**: local CPU serving, batching, quantization | +19% throughput from micro-batching | none | [repo](https://github.com/TarunSinghChauhan/llm-inference-engine) |

---

## How to read this

Each project answers one question I wanted a real answer to:

- **CodeCave**: can an LLM tutor teach code to someone who thinks in Hindi?
- **Multi-Agent Code Review**: do multiple specialised agents find more than one?
- **RAG Ops Platform**: how do you keep a RAG system fast and notice when embeddings drift?
- **Eval Harness**: how do you measure model quality so the score can be trusted (inter-rater κ, adversarial cases)?
- **HITL Approval Agent**: when should an agent act alone and when should it ask?
- **Inference Engine**: what actually speeds up local LLM serving, and what doesn't?

Details for the inference engine are in [benchmarks/inference-engine.md](benchmarks/inference-engine.md), including a result that didn't work.

---

## Links

- Portfolio: [tarunchauhan.vercel.app](https://tarunchauhan.vercel.app)
- GitHub: [github.com/TarunSinghChauhan](https://github.com/TarunSinghChauhan)
- LinkedIn: [linkedin.com/in/tarunchauhanml](https://linkedin.com/in/tarunchauhanml)
- Email: tarunsinghchauhan088@gmail.com
