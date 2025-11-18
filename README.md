# Design-Project

# A Hybrid Proactive & Predictive Framework for Edge–Cloud Resource Management

This repository contains the source code for **"A Hybrid Proactive and Predictive Framework for Edge-Cloud Resource Management"**, a design project developed at **IIIT Vadodara**.  
The project proposes a *future-aware*, AI-driven system that intelligently manages resources across cloud and edge devices using:

- **CNN–LSTM-based workload forecasting**
- **Deep Reinforcement Learning (DQN/DDQN) based orchestration**
- **Hybrid discrete–continuous action space**
- **Simulation using a custom iFogSim-inspired Python environment**

This hybrid design enables the system to make proactive decisions—anticipating future workload spikes, minimizing SLA violations, and drastically reducing cost and energy consumption.

---

## 📌 Project Highlights

### 🔮 1. Predictive Module — CNN + LSTM  
- Learns patterns from multivariate time-series (CPU, memory, network I/O).  
- CNN extracts short-term spatial correlations.  
- LSTM models long-term temporal dependencies.  
- Produces a forecast vector for future workload states.

### 🧠 2. DRL Orchestrator — DQN/Double-DQN  
- Receives an **extended state** containing the current system state + predicted workload.  
- Learns optimal offloading and resource-allocation strategies.  
- Designed using **Centralized Training, Decentralized Execution (CTDE)**.

### 🔗 3. Hybrid Proactive Architecture  
The novelty lies in **injecting the forecast directly into the DRL agent’s state**, enabling:
- Proactive resource allocation  
- Pre-scaling before surges  
- Drastically reduced energy/cost  
- Improved latency and throughput  

### 🏗 4. Custom Simulation Environment  
A lightweight Python-based simulator (`iFogSimEnv`) replicates:
- Edge nodes  
- Cloud datacenter  
- Network latencies  
- Dynamic workloads  
- Multi-objective reward calculations  

---

## 📊 Performance Summary

| Metric | Baseline (DDQN) | Proposed Hybrid Model |
|--------|------------------|------------------------|
| **Total Reward** | 10.54 | **50.68** |
| **Energy Consumption** | 3.75 | **0.12** |
| **Operational Cost** | 52.53 | **3.06** |
| **Latency** | 4.47 | **4.19** |
| **Throughput** | 0.101 | **0.109** |
| **Utilization** | 0.51 | **0.51** |


The hybrid model achieves **5× better overall reward**, with dramatic improvements in cost and energy efficiency.

---

---

## ⚙️ Installation & Setup

### **1. Clone the Repository**
```bash
git clone https://github.com/Anshul-Gupta-1410/Design-Project.git
cd Design-Project
```
### **2. Then run base.ipynb and Hybrid.ipynb**


🧪 How the System Works
---
Phase 1 — Predictive Module Training

- Train CNN-LSTM on historical workload dataset
- Save model for inference

Phase 2 — DRL Agent Training

- For each step:
 - Generate forecast using CNN-LSTM

 - Form extended state: [current_state, forecast]

 - DQN/DDQN selects hybrid action:

   - Discrete → Offloading target (Edge 1/2/.../Cloud)

   - Continuous → Resource allocation vector

 - Store transitions in replay buffer

 - Perform DDQN updates

 - Update target network

🛠 Technologies Used
---

Python

PyTorch

NumPy & Pandas

Matplotlib / Seaborn

Deep Reinforcement Learning

CNN + LSTM Neural Networks

📚 Research Paper
---
This codebase is aligned with the design project documented in:

"A Hybrid Proactive and Predictive Framework for Edge-Cloud Resource Management"

Authors:
---
Anika Garg, Hrikshesh Kumar, Anshul Gupta, Yashika Agarwal, Dr. Rishabh Gupta
IIIT Vadodara, Gandhinagar

🚧 Future Work
---
Incorporate Federated Learning for decentralized model training

Build an Uncertainty-Aware DRL agent using Bayesian neural networks

Explore Sim-to-Real transfer for deployment on real edge devices

Support for multi-agent orchestration (MADRL)

🤝 Contributing
---
Pull requests and feature suggestions are welcome!

⭐ Acknowledgments
---
Special thanks to
Department of IT, IIIT Vadodara
for guidance, support, and research resources.