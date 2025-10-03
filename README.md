# Reinforcement Learning Programming  
**CSCN 8020 – Assignment 1**  

**Name:** Krishnareddy Bovilla  
**Student ID:** 9050861  
**GitHub Repository:** [Reinforcement-Learning-Programming-A1](https://github.com/bkrishnareddy-ai/Reinforcement-Learning-Programming-A1.git)  

---

## 📘 Introduction  
This repository contains solutions to **Assignment 1** for CSCN 8020: *Reinforcement Learning Programming*.  
The assignment explores **Markov Decision Processes (MDPs)**, **Dynamic Programming (DP)**, and **Monte Carlo Methods** applied to Gridworld problems.  

The work covers:  
- Formulating RL tasks as MDPs.  
- Solving Gridworld environments using Value Iteration.  
- Implementing variations of Value Iteration (standard vs in-place).  
- Estimating value functions using Off-policy Monte Carlo with Importance Sampling.  

---

## ⚙️ Environment Setup  

### 1. Clone the repository  
```bash
git clone https://github.com/bkrishnareddy-ai/Reinforcement-Learning-Programming-A1.git
cd Reinforcement-Learning-Programming-A1
```

### 2. Create a virtual environment  
```bash
python3 -m venv rl_env
source rl_env/bin/activate    # On Linux/Mac
rl_env\Scripts\activate       # On Windows
```

### 3. Install dependencies  
```bash
pip install -r requirements.txt
```

> 📌 If `requirements.txt` is missing, you can manually install:
```bash
pip install numpy matplotlib gym
```

---

## 📂 Assignment Problems  

### **Problem 1 – Pick-and-Place Robot (MDP Formulation)**  
- Designed the task as a **Markov Decision Process**:  
  - **States ($S$):** Positions, velocities, and joint configurations.  
  - **Actions ($A$):** Motor commands for robotic joints.  
  - **Rewards ($R$):**  
    - +10 for successful smooth placement.  
    - -5 for collisions.  
    - -1 for delays.  
  - **Transition probabilities ($P$):** Mostly deterministic with motor noise.  

---

### **Problem 2 – 2×2 Gridworld (Value Iteration)**  
- Environment: 2×2 grid with deterministic transitions.  
- Rewards:  
  - $R(s_1)=5,\; R(s_2)=10,\; R(s_3)=1,\; R(s_4)=2$.  
- Applied **two iterations of Value Iteration** using:  

$$
V_{k+1}(s) = \max_a \Big[ R(s) + \gamma \sum_{s'} P(s'|s,a) V_k(s') \Big]
$$  

- Results: Showed convergence of values and greedy policy after two iterations.  

---

### **Problem 3 – 5×5 Gridworld (Value Iteration & Variations)**  
- Rewards:  
  - $+10$ at goal $(s_{4,4})$.  
  - $-5$ at grey/unfavorable states.  
  - $-1$ elsewhere.  

- Implemented **Standard Value Iteration** to compute optimal $V^*(s)$ and $\pi^*(s)$.  
- Implemented **In-place Value Iteration** (updating values immediately).  

- **Comparison:**  
  - Standard VI → stable, needs more sweeps.  
  - In-place VI → converges faster, order-dependent.  
  - Both yield same optimal policy.  

---

### **Problem 4 – Off-Policy Monte Carlo with Importance Sampling**  
- **Behavior policy $b(a|s)$:** Random exploration.  
- **Target policy $\pi(a|s)$:** Greedy.  
- Used **importance sampling**:  

$$
V(s) = \frac{\sum_{t \in \tau(s)} \rho_{t:T-1} G_t}{\sum_{t \in \tau(s)} \rho_{t:T-1}}, \quad
\rho_{t:T-1} = \prod_{k=t}^{T-1} \frac{\pi(A_k|S_k)}{b(A_k|S_k)}
$$  

- **Results:**  
  - Monte Carlo estimates approximate true values.  
  - Requires many episodes.  
  - DP (Value Iteration) is faster but model-based.  
  - MC is model-free, can learn directly from sampled experience.  

---

## ▶️ How to Run  

Run individual problem scripts:  

### Problem 1 – MDP Formulation  
(No code, theoretical design documented in report.)  

### Problem 2 – Value Iteration (2×2 Gridworld)  
```bash
python problem2_value_iteration.py
```

### Problem 3 – Value Iteration (5×5 Gridworld)  
```bash
python problem3_value_iteration.py
```

### Problem 4 – Monte Carlo with Importance Sampling  
```bash
python problem4_monte_carlo.py
```

---

## 📊 Results Summary  

- **Problem 1:** Formulated robot task as MDP with states, actions, and rewards.  
- **Problem 2:** Showed iterative improvement of values and greedy policy.  
- **Problem 3:** Both VI methods produced same optimal solution; in-place faster.  
- **Problem 4:** Monte Carlo estimates converge with enough episodes; slower but model-free.  

---

## 📚 References  

- Sutton, R. S., & Barto, A. G. (2018). *Reinforcement Learning: An Introduction (2nd Edition)*.  
- David Silver, *Reinforcement Learning Lectures*.  
- CSCN8020 Course Materials

---

✅ **This README serves as the official documentation and report for Assignment 1.**  
