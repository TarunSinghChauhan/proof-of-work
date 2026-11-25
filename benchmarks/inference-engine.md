# LLM Inference Engine: benchmark notes

Repo: [llm-inference-engine](https://github.com/TarunSinghChauhan/llm-inference-engine)

Setup: Qwen2.5-3B (GGUF) via llama.cpp / llama-cpp-python, FastAPI + Redis, Windows, **CPU only**, no API keys.

## 1. Concurrency and batching

| Setup | Concurrency | p50 | p99 | Throughput |
|---|---|---|---|---|
| Baseline | 1 | 14.58s | 18.86s (p95) | 0.069 req/s |
| Lock (serialized) | 5 | 81.5s | 99.0s | 0.069 req/s |
| Micro-batcher | 5 | 59.4s (-27%) | 110.9s | 0.082 req/s (+19%) |

- Found and fixed a bug: `engine.generate()` was blocking the asyncio event loop and causing Redis timeouts under load. Fix: `run_in_executor` + `asyncio.Lock`.
- Batcher: window-based, max 8 requests or 50ms wait. llama-cpp-python still processes prompts sequentially inside, so the gain is lower scheduling overhead, not parallel decode.

## 2. Quantization (5 prompts each)

| Variant | Size | p50 | Tokens/s |
|---|---|---|---|
| Q3_K_M | 1644 MB | 9.3s | 14.03 |
| **Q4_K_M** | 2007 MB | **7.7s** | **16.56** |
| Q8_0 | 3449 MB | 11.6s | 10.28 |

Q4_K_M is the sweet spot. The smallest variant is not the fastest, likely because of dequantization overhead at lower bit-widths on CPU.

## 3. Speculative decoding (prompt lookup): negative result

Slower than baseline on all three prompt types: **0.24x to 0.45x**. The n-gram search and verification overhead cost more than the speculation saved, on a CPU with a 3B model. Kept in the repo on purpose.
