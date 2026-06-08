# Legal and Compliance Guide

This document outlines the privacy, security, safety, and regulatory compliance profile of BIM 2 (Biologically Inspired Model).

---

## 🔒 Privacy and Data Residency

BIM 2 is designed as a **local-first, client-side application** to ensure maximum user privacy and data security.

### 1. Data Processing Location
* **100% Client-Side Execution:** All hashing, Sparse Distributed Representation (SDR) generation, synapse updates, vocabulary logging, and 3D rendering are executed locally within the user's browser runtime environment.
* **No Telemetry or APIs:** The application does not send data, telemetry, analytics, or model training inputs to external servers, cloud services, or third-party APIs.
* **Offline Operation:** The application is fully functional without an active internet connection.

### 2. Ephemeral Storage
* **Volatile Memory Only:** The Hebbian learning state (vocabulary, transition counts, and synaptic weights) is stored entirely in volatile JavaScript memory (RAM).
* **No Persistent Storage:** The codebase does not read from or write to `localStorage`, `IndexedDB`, `sessionStorage`, or HTTP Cookies.
* **Zero-Residual Footprint:** Reloading the web page instantly wipes the model vocabulary, synapse weights, and chat history. No residual data is retained on the user's hard drive.

---

## 🛡️ AI Safety and Guardrails

Unlike Large Language Models (LLMs) or deep generative models, BIM 2 is a deterministic rule-based sequence predictor. It is subject to strict, built-in structural guardrails:

### 1. Non-Generative Design
* **Closed-Vocabulary Decoding:** The decoder (`decodeSDR`) can only output words that exist in its vocabulary—meaning it can only predict words that the user has explicitly input during the active session.
* **No Hallucination:** The system is incapable of generating grammatically incorrect phrases or "hallucinated" facts unless they were directly entered by the user.
* **Overlap Verification:** A prediction is only decoded if the candidate word's SDR shares an overlap of at least $15$ bits (out of $64$) with the predicted SDR. If no vocabulary word meets this criteria, the prediction fails gracefully (returning `...`).

### 2. Resource Consumption
* **Negligible Compute Footprint:** The application runs efficiently on standard client CPUs and GPUs (via 2D Canvas rendering). It requires no heavy model servers, complex cooling, or large-scale data center energy usage.

---

## ⚖️ Intellectual Property and Licensing

### 1. Training Corpora
* **User-Owned Training:** The model is initialized with a blank vocabulary and zero active synapses. No copyrighted text datasets, scraped books, or licensed articles are embedded in the software.
* **IP Ownership of Output:** All learned sequences are created dynamically by the user. No intellectual property claims are made on the sequences or concepts trained during runtime sessions.

### 2. Open-Source permissive license
* The code is distributed under the permissive **MIT License**, permitting unrestricted commercial use, modification, and distribution.

---

## 📋 Regulatory Compliance Checklist

### 1. General Data Protection Regulation (GDPR) & California Consumer Privacy Act (CCPA)
* **Status:** **Exempt / Compliant**
* **Rationale:** BIM 2 does not collect, store, or process any Personally Identifiable Information (PII) or personal data. Data subject requests (e.g., right to access, right to erase) are fully satisfied by reloading the browser tab.

### 2. EU AI Act
* **Status:** **Minimal/No Risk Category**
* **Rationale:** The system is an educational, deterministic, rule-based algorithmic model. It does not employ deep neural networks, automated high-stakes decision-making, or biometric profiling. It does not fall under any regulated "High-Risk AI" or "General Purpose AI" classifications.

---

## ♿ Accessibility Compliance

* **Canvas Overlay:** The canvas visualizer (`#neural-canvas`) has `pointer-events: none` and is purely decorative, preventing it from interfering with screen readers.
* **Semantic HTML:** The interface utilizes semantic tags (e.g., `<form>`, `<input>`, `<button>`, `<ul>`, `<li>`) allowing assistive technology to navigate the chat interface normally.
* **Contrast and Focus:** High-contrast text values against the dark background are configured via custom CSS properties, and active controls support outline focus highlights.
