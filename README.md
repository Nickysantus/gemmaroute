<div align="center">
  <h1>GemmaRoute</h1>
  <p><strong>A semantic routing layer for enterprise AI infrastructure.</strong></p>

  <p>
    <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js" />
    <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
    <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind CSS" />
    <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI" />
    <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
    <img src="https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white" alt="SQLite" />
  </p>
</div>

GemmaRoute evaluates incoming prompts and dynamically routes them to either a local lightweight model or a cloud-based frontier model based on cognitive complexity, optimizing for both inference cost and latency.

## Architecture

* **Frontend:** Next.js, Tailwind CSS, TypeScript
* **Backend:** FastAPI, Python, SQLite
* **Local Inference (Edge):** AMD ROCm running Gemma 2
* **Cloud Inference:** Fireworks AI running Llama 3.1 405B

## Routing Logic

* **Simple/Trivial:** Processed locally via AMD ROCm ($0 cost). Example: Password resets, business hours.
* **Complex:** Escalated to cloud LLMs (Paid compute). Example: Legal SLA analysis, multi-step reasoning.

## Local Setup

```bash
npm install
npm run dev
```

Access the application at [http://localhost:3000](http://localhost:3000).

## Fallback Routing

If the Python backend is disconnected, the frontend relies on a client-side ML scoring dictionary to simulate routing behavior.

### Test prompts for routing:

* **Local:** "How do I reset my password?"
* **Cloud:** "I have a complex legal SLA violation and need to review section 4B of my contract."
