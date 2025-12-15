<p align="center">
  <img src="https://img.icons8.com/fluency/96/rocket.png" alt="GigOptimizer Logo" width="80"/>
</p>

<h1 align="center">GigOptimizer</h1>

<p align="center">
  <strong>Maximize Your Freelance Earnings with AI-Powered Project Selection</strong>
</p>

<p align="center">
  <a href="https://gigoptimizer.streamlit.app">
    <img src="https://static.streamlit.io/badges/streamlit_badge_black_white.svg" alt="Open in Streamlit"/>
  </a>
  <img src="https://img.shields.io/badge/Python-3.9+-blue.svg" alt="Python"/>
  <img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License"/>
  <img src="https://img.shields.io/badge/Optimization-MILP-orange.svg" alt="MILP"/>
</p>

<p align="center">
  <a href="#-the-problem">Problem</a> •
  <a href="#-the-solution">Solution</a> •
  <a href="#-live-demo">Demo</a> •
  <a href="#-how-it-works">How It Works</a> •
  <a href="#-demo-video">Video</a>
</p>

---

## 🎯 The Problem

### Freelancers Are Leaving Money on the Table

The gig economy has exploded to **$1.27 trillion** with **64 million Americans** freelancing in 2023. Platforms like Upwork, Fiverr, and Toptal have made finding work easier than ever—but they've created a new challenge:

> **Too many opportunities. Not enough time to evaluate them properly.**

A successful freelancer might receive **10-15 project invitations per week**, each with different pay rates, time requirements, deadlines, and skill requirements. Most make decisions based on **gut feeling**:

- *"This one pays well, I'll take it"*
- *"I like this client"*
- *"This seems interesting"*

But with 8 potential projects and only 80 hours available, there are **256 possible combinations**. The difference between a good selection and the **optimal** selection can mean **thousands of dollars per month**.

### Who Faces This Problem?

| User Type | Pain Point |
|:----------|:-----------|
| 🆕 **New Freelancers** | Undervalue their time, accept low-paying work |
| 💼 **Experienced Freelancers** | Overcommit, miss deadlines, experience burnout |
| 🏢 **Agency Owners** | Struggle to allocate team capacity optimally |
| ⏰ **Side Hustlers** | Limited hours demand maximum efficiency |

### The Impact

For a freelancer earning **$75/hour** working **100 hours/month**, a **10% improvement** in project selection efficiency equals an extra **$9,000/year**.

---

## 💡 The Solution

### Prescriptive Analytics for Project Selection

**GigOptimizer** treats freelance project selection as what it really is: a **resource allocation optimization problem**—the same class of problems solved by:

- 📦 **Amazon** for warehouse logistics
- ✈️ **Airlines** for crew scheduling  
- 💰 **Investment firms** for portfolio construction

### The Mathematical Model

We use **Mixed Integer Linear Programming (MILP)** to find the mathematically optimal solution:

```
Maximize:    Σ (pay_i × x_i)           ← Total Earnings

Subject to:  Σ (hours_i × x_i) ≤ H    ← Time Constraint
             skill_i ≥ threshold       ← Quality Constraint
             x_i ∈ {0, 1}             ← Binary Decision (take or skip)
```

### Why MILP Over Simple Heuristics?

| Approach | Limitation | GigOptimizer |
|:---------|:-----------|:-------------|
| Highest pay first | Ignores time constraints | ✅ Considers full portfolio |
| Highest hourly rate | Misses high-value projects | ✅ Balances rate and volume |
| Gut feeling | Cognitive bias, inconsistent | ✅ Mathematically optimal |
| Spreadsheet | Time-consuming, manual | ✅ Instant, automated |

---

## 🚀 Live Demo

<p align="center">
  <a href="https://gigoptimizer.streamlit.app">
    <img src="https://img.shields.io/badge/🚀_Try_GigOptimizer-Live_Demo-brightgreen?style=for-the-badge&logoColor=white" alt="Live Demo"/>
  </a>
</p>

**👉 [https://gigoptimizer.streamlit.app](https://gigoptimizer.streamlit.app)**

---

## ⚙️ How It Works

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  📝 Enter       │───▶│  ⚙️ Set         │───▶│  🚀 Run         │───▶│  🎯 Get         │
│  Projects       │    │  Constraints    │    │  Optimizer      │    │  Recommendations│
└─────────────────┘    └─────────────────┘    └─────────────────┘    └─────────────────┘
```

### Step 1: Enter Your Projects
Add freelance opportunities with:
- Project name & client
- Total pay ($)
- Hours required
- Deadline (days)
- Skill match (0-100%)

### Step 2: Set Constraints
- **Hours available** this month
- **Minimum skill match** threshold

### Step 3: Get Optimal Results
- ✅ **TAKE**: Projects to accept
- ⏭️ **SKIP**: Projects to decline
- 📊 **Metrics**: Total earnings, utilization, effective rate

---

## 📊 Example

### Input: 8 Projects, 80 Hours Available

| Project | Pay | Hours | Skill |
|:--------|----:|------:|------:|
| Data Dashboard | $3,200 | 50 hrs | 90% |
| Website Redesign | $2,500 | 40 hrs | 95% |
| Mobile App UI | $1,800 | 25 hrs | 80% |
| API Integration | $1,500 | 20 hrs | 75% |
| WordPress Plugin | $2,000 | 30 hrs | 88% |
| *...3 more* | | | |

**Total potential: $13,600 requiring 205 hours**

### Output: Optimal Selection

| Recommendation | Project | Pay | Hours |
|:---------------|:--------|----:|------:|
| ✅ TAKE | Data Dashboard | $3,200 | 50 hrs |
| ✅ TAKE | Mobile App UI | $1,800 | 25 hrs |
| ⏭️ SKIP | All others | — | — |

**Result: $5,000 in 75 hours = $66.67/hr effective rate**

> 💡 A greedy "highest pay first" approach would exceed the 80-hour constraint. MILP finds the true optimal.

---

## 🧮 Technical Details

### Optimization Engine

```python
from scipy.optimize import milp, LinearConstraint, Bounds

# Objective: Maximize earnings (minimize negative)
c = -earnings_array  

# Constraint: Total hours ≤ Available hours
constraints = LinearConstraint(hours_array.reshape(1, -1), ub=available_hours)

# Binary decision variables
result = milp(c, constraints=constraints, 
              bounds=Bounds(0, 1), 
              integrality=np.ones(n_projects))
```

### Technology Stack

| Component | Technology |
|:----------|:-----------|
| Frontend | Streamlit |
| Optimization | SciPy MILP |
| Data Processing | Pandas, NumPy |
| Visualization | Plotly |
| Deployment | Streamlit Cloud |

---

## 🎬 Demo Video

<p align="center">
  <a href="https://youtu.be/5I7wl9xIAjI">
    <img src="https://img.youtube.com/vi/5I7wl9xIAjI/maxresdefault.jpg" alt="GigOptimizer Demo" width="600"/>
  </a>
</p>

<p align="center">
  <a href="https://youtu.be/5I7wl9xIAjI">
    <img src="https://img.shields.io/badge/▶️_Watch_Demo-YouTube-red?style=for-the-badge&logo=youtube" alt="YouTube"/>
  </a>
</p>

**In this video:**
1. 🎯 The Problem — Why freelancers struggle with project selection
2. 🧮 The Approach — How MILP optimization solves this
3. 💻 Live Demo — Walking through the app
4. 📚 Key Learnings — Insights from building this product

---

## 🚀 Run Locally

```bash
# Clone the repository
git clone https://github.com/jaswanthi03/GigOptimizer.git
cd GigOptimizer

# Install dependencies
pip install -r requirements.txt

# Run the app
streamlit run app.py
```

---

## 🎓 About This Project

This project was built for **ISOM 839: Prescriptive Analytics** at **Suffolk University**.

### Course Skills Applied
- ✅ Optimization modeling (Gurobi concepts, applied via SciPy)
- ✅ Prescriptive analytics (Data → Model → Recommendation)
- ✅ Product thinking (Problem → Solution → Deployment)
- ✅ AI-assisted development with Cursor

### Project Track
**Track A: Optimization Focus** — Similar to the Portfolio Optimizer built in class, applying constrained optimization to maximize an objective within resource constraints.

---

## 🔮 Future Roadmap

| Phase | Feature |
|:------|:--------|
| 🔜 Short-term | Multi-period scheduling, recurring client value |
| 📅 Medium-term | ML-enhanced hour estimates, historical tracking |
| 🚀 Long-term | Upwork/Fiverr API integration, team optimization |

### Market Opportunity
With **64 million U.S. freelancers** and no dominant project selection tool:
- 0.1% penetration × $10/month = **$7.7M ARR potential**

---

## 👤 Author

**Jaswanthi Banoth**  
📧 [saijaswanthibanoth@gmail.com](mailto:saijaswanthibanoth@gmail.com)

---

## 📄 License

MIT License — Feel free to use, modify, and build upon this project.

---

<p align="center">
  <strong>GigOptimizer</strong><br>
  <em>Because your time is your most valuable asset.</em>
</p>

<p align="center">
  Built with ❤️ for ISOM 839 at Suffolk University
</p>
