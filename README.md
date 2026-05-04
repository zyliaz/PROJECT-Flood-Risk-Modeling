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

- Step 1 Loss ratio prediction using Random Forest
- Step 2 Uninsured Loss Estimation Model

---

## Repository Structure

```
├── data/       # Raw, intermediate, and final model datasets
│               # (Some raw files excluded due to size; download links provided)
├── model/      # 01 explorative data analysis of model dataset, 02 the full model
└── output/     # Graphs and figures produced during model evaluation
```

---

## How to Run

To get started, open this repository on your local machine using one of the following methods:

1. Clone this repository:
   bash    git clone https://github.com/zyliazhang/PROJECT-flood-risk-modeling.git    cd PROJECT-flood-risk-modeling

2. Install the required dependencies:
   bash    pip install -r requirements.txt

3. Open and run the notebook:
      [model/02_loss_estimation_model.ipynb](model/02_loss_estimation_model.ipynb)   

---

## Results and Discussion
**Key Findings**
- 58% of estimated total flood losses across 5 Eastern NC counties from 1996 to 2018 went uninsured — approximately $271 million out of $468 million total.
- Insurance coverage improved dramatically over the study period. Early storms (1996–1999) had uninsured shares of 65–95%; recent storms (2016–2018) had uninsured shares of 7–18%.
- Lenoir and Beaufort counties carry the largest insurance gaps — both in percentage terms (76% and 68%) and in absolute dollars.
- Building age is the single most important predictor of loss ratio, confirming that older building stock is systematically more flood-vulnerable.
- The GeoTIFF-derived flood_ratio is a critical improvement over the county-level flood count variable used previously — it provides genuine grid-level exposure information that varies across space, not just across events.

**Limitations**
- The NC Buildings GDB records 2010 replacement values. For early storms (1996–2003), this overstates the building values at risk and inflates estimated total losses. The uninsured percentage trend (early storms > late storms) is directionally robust, but early-storm dollar figures are likely too high.
- total_bldg_val in the FEMA records captures only insured buildings. True uninsured losses are likely larger than estimated, because uninsured buildings are not counted in the denominator.
- flood_ratio is a binary measure (inundated or not) derived from 30m rasters. It does not capture water depth, which is the primary engineering driver of flood damage. This limits the model's R² at the grid level.
- Cross-validated R² = 0.207 reflects inherent variability in localized flood damage. The model is reliable at the storm and county aggregate level, but individual grid-cell predictions carry significant uncertainty.
- The study covers 5 counties and 7 storms from 1996 to 2018. Generalization to other counties or future storms requires validation with additional data.