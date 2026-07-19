# BioCrypto Education Engine: Automated Multi-LLM Orchestration & Content Pipeline

An autonomous, serverless production pipeline engineered to ingest multi-disciplinary data streams, synthesize high-engagement educational content using advanced Large Language Models (LLMs), and programmatically publish synchronized updates across social media platforms.

---

### 📌 Architectural Notice
**Repository Scope:** This repository serves as the public technical documentation, architectural blueprint, and engineering showcase for the BioCrypto Education Engine. The functional production codebase, operational execution scripts, and active deployment configurations are hosted within a secure, private environment to protect active API endpoints, cryptographic credentials, and continuous automation runtimes.

---

## 🛠️ Core Engineering & Technical Pillars

### 1. Multi-LLM Orchestration & Resilient Fallback Chains
The system features a decoupled, fault-tolerant text synthesis layer engineered to handle real-time traffic anomalies, API outages, and token rate limits seamlessly.
* **Resiliency Logic:** Configured with an automated cascading fallback mechanism utilizing the **Google GenAI SDK** as the primary synthesis engine. If a transient HTTP error code (such as a `429 Rate Limit` or `503 Service Unavailable`) is encountered, the pipeline automatically catches the exception, executes an exponential back-off strategy, and drops down to a high-throughput **Groq Cloud API** secondary chain running optimized `Llama-3.1` and `Llama-3.3` models.

### 2. Serverless Task Scheduling & State Persistence
To eliminate continuous infrastructure maintenance overhead and maintain a zero-cost operational footprint, the entire environment runs on a serverless cron schedule.
* **Stateless State Tracking:** Driven completely by **GitHub Actions CI/CD workflows**. Because serverless execution runners are inherently stateless and clear their environment upon completion, a custom data-persistence mechanism was built. The pipeline tracks historical execution history by updating a local `processed_urls.json` file on every execution loop. It then utilizes native Git automation within the workflow runner to securely commit and push the updated state dictionary back to the repository.

### 3. Fault-Tolerant Multi-API Integration
The engine concurrently synchronizes, orchestrates, and validates structured data transfers across **four distinct, heterogeneous REST APIs**:
* **Meta Graph API:** Configured to push programmatically via the high-reach page `/photos` endpoint rather than standard feed link-shares, optimizing algorithmic content distribution.
* **Google GenAI API & Groq Cloud API:** Leveraged for structured context-aware content extraction, translation, and text refinement.
* **OpenAI API:** Fully integrated within the underlying modular architecture, leaving a plug-and-play gateway open for immediate testing and hot-swappable model expansion.

### 4. Dynamic Programmatic Image Generation & RTL Typography
To guarantee high aesthetic presentation even when upstream ingestion streams lack native media elements, the system incorporates a dedicated graphics-rendering engine.
* **Visual Construction:** Uses the **Pillow (PIL)** library to dynamically calculate layout geometry, generate on-brand background canvases, and overlay synthesized copy on the fly.
* **Bi-Directional Text Shaping:** Integrates advanced text-shaping algorithms to handle complex Right-to-Left (RTL) directional formatting, font script-joining rules, and normalization for flawless typographical rendering.

---

## 🏗️ System Architecture & Data Flow


```
[ Data Ingestion ]       --> Parses multi-disciplinary educational streams
│
▼
[ Multi-LLM Processing ]    --> Cascading Logic: Google GenAI ──(Fallback)──> Groq API
│
▼
[ State Verification ]     --> Reads/Writes processed_urls.json to prevent duplication
│
▼
[ Media Synthesis ]        --> Programmatic image generation & Arabic RTL script-shaping
│
▼
[ Social Publishing ]      --> Dispatches structured payload to Meta Graph API endpoints
│
▼
[ State Commit ]          --> GitHub Actions workflow natively pushes state back to repository
```

---

## 🧰 Tech Stack & Component Architecture

* **Core Programming Language:** Python 3.x
* **CI/CD & Serverless DevOps:** GitHub Actions (YAML Workflows)
* **API Integration Matrix:** Meta Graph API, Google GenAI SDK, Groq Cloud API, OpenAI API, Requests
* **Graphics & Typography Processing:** Pillow (PIL), FontTools, Arabic-Reshaper
* **Data Storage Layer:** Structured, lightweight JSON-based state repositories

---

## 📈 Technical Proficiencies Demonstrated

* **End-to-End Automation:** Complete architecture designed to run continuously 24/7 without requiring manual intervention or persistent dedicated servers.
* **API Resiliency & Defense:** Robust try-except implementation and custom back-off wrappers designed to mitigate remote vendor rate limits and platform downtime.
* **Modular Software Patterns:** Clean separation of concerns dividing data collection, text processing, multimedia synthesis, and network publishing interfaces.

---

##​ 📦 Facebook Page URL:


