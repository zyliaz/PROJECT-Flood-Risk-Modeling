## Motivation & Research Question

NFIP data captures insured losses only. A large share of flood-prone buildings carry no coverage, meaning that real economic damage routinely disappears from the official record. 

**Research Questions:**
- What building and flood characteristics drive the NFIP loss ratio across 5 Eastern NC counties?
- How much total flood loss went uninsured across 7 hurricanes (1996–2018)?

---

## Data Sources & Cleaning

Detailed data cleaning notes can be found at [`data/data cleaning notes.md`](data/data%20cleaning%20notes.md).

---

## Model

The estimation pipeline runs in two steps:

Step 1 Loss ratio prediction using Random Forest
Step 2 Uninsured Loss Estimation Model

---

## Repository Structure

```
├── data/       # Raw, intermediate, and final model datasets
│               # (Some raw files excluded due to size — download links provided)
├── model/      # 01_eda.ipynb · 02_loss_estimation_model.ipynb
└── output/     # Graphs and figures produced during model evaluation
```

---

## How to Run

1. Clone the repository and activate the project virtual environment.
2. Open and run [`model/02_loss_estimation_model.ipynb`](model/02_loss_estimation_model.ipynb) in Jupyter.