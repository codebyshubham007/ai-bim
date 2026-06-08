# BIM 2: Biologically Inspired Model

BIM 2 is a lightweight, local-first, biologically inspired sequence learning network and interactive 3D neural visualizer. It runs entirely in the browser using vanilla HTML, CSS, and JavaScript.

The model leverages concepts from Hierarchical Temporal Memory (HTM), Sparse Distributed Representations (SDR), and Hebbian learning ("cells that fire together, wire together") to learn sequential relationships between words in real-time and predict future sequences with zero server-side dependencies.

---

## 🌟 Key Features

* **3D Neural Visualizer:** A real-time rendering of $16,384$ neurons distributed across a Fibonacci sphere. Active, previous, and predicted neural states are represented with color-coded pulsing glows.
* **Hebbian Plasticity Engine:** Dynamically wires synapses in real-time as you type. Watch the learning state progress from `READY` to `WIRING...` and finally to `STABLE` as sequences are repeated.
* **Predictive Sequencing:** Recognizes and completes learned sequences (e.g., query `"Toyota made?"` to predict `"supra"`).
* **Multi-Step Look-Ahead:** Traverses grammatical stop-words (e.g., *is*, *of*, *the*) to predict the next meaningful content word.
* **Deterministic SDRs:** Maps text input into high-dimensional sparse representations ($16,384$ dimensions, $64$ active bits, $\approx 0.39\%$ sparsity) using a deterministic hashing algorithm.
* **Surprise Metric:** Outputs a real-time surprise score ($0.0$ to $1.0$) based on SDR overlap between prediction and actual input.

---

## 🚀 Quick Start

Since BIM 2 is built with vanilla web technologies, there is no build step or package installation required.

### Option 1: Double-Click
1. Clone or download this repository.
2. Navigate to the project directory.
3. Double-click [index.html](file:///d:/ai-bim/index.html) to open the application directly in any modern web browser.

### Option 2: Local Server (Recommended)
To run the project via a local development server (e.g., using Python, Node.js, or VS Code Live Server):

**Using Python 3:**
```bash
python -m http.server 8000
```
Then visit `http://localhost:8000` in your web browser.

**Using Node.js (`http-server`):**
```bash
npx http-server -p 8000
```

---

## 🧠 Interactive Training Guide

You can teach the network relationships in real-time:

1. **Input a Sequence:** Type a simple sequence such as `"Toyota made supra"` and press **Send** (or press `Enter`).
2. **Observe the Visualization:**
   * Active nodes representing the current word pulse in **Cyan**.
   * Previous nodes fade to **Purple**.
   * Synaptic lines show orange pathways during the learning phase.
3. **Repeat to Wire (3x):** Enter the exact same sequence `"Toyota made supra"` **three times**. You will see:
   * Hebbian Plasticity state change: `READY` $\rightarrow$ `WIRING...` $\rightarrow$ `STABLE`.
   * The number of **Concepts Formed** increases to `1`.
4. **Query the Model:**
   * Type `"Toyota made"` (or `"Toyota made?"`) and hit Enter.
   * The model will predict **"supra"** with **$0.00$ surprise**.
   * Predicted nodes and stable synaptic paths will glow in **Green**.

---

## 🛠️ Tech Stack & File Structure

```
├── index.html       # Mac/Linux terminal-inspired interface & canvas overlay
├── styles.css       # Glassmorphism design system & visual styling
├── app.js           # Deterministic SDR hashing, Hebbian engine, & 3D Fibonacci renderer
└── docs/
    ├── ARCHITECTURE.md          # Technical overview, algorithms, and data structures
    └── LEGAL_AND_COMPLIANCE.md  # Privacy, local-first disclaimer, compliance checklist
```

* **Frontend Structure:** Simple single-page app (SPA) layout.
* **Styling:** Vanilla CSS using custom properties (variables), backdrop filters for glassmorphism, and hardware-accelerated animations.
* **Fonts:** `Outfit` (sans-serif) for high-readability UI and `JetBrains Mono` for stats/data.

---

## ⚙️ Mathematical Parameters

* **SDR Dimensions ($N$):** $16,384$
* **Active Bits ($K$):** $64$
* **Sparsity:** $\approx 0.39\%$
* **Hebbian Learning Rate ($\eta$):** $0.34$
* **Synapse Decay Rate ($\delta$):** $0.02$
* **Connection Threshold ($\theta$):** $0.50$
* **Overlap Decoding Threshold:** $\ge 15$ bits (out of $64$)

---

## 📄 License

This project is licensed under the MIT License. Feel free to use, modify, and distribute it.
