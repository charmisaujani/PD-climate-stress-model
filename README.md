# Climate Scenario PD Stress Test

This project analyzes credit risk under NGFS climate transition scenarios using downscaled data from Integrated Assessment Models (IAMs) like REMIND-MAgPIE, combined with macroeconomic projections from NiGEM. The output simulates future Probabilities of Default (PD) for selected sectors under different climate transition scenarios.

---

## Files

- **`pd_climate_stress_test.ipynb`**  
  Jupyter Notebook that loads scenario data, extracts macro & transition variables, and calculates projected PDs using both linear and logit models.

- **`Downscaled_REMIND-MAgPIE...xlsx`**  
  IAM climate scenario data.

- **`NiGEM_data.xlsx`**  
  Macroeconomic data by country and scenario.

---

## What the Script Does

- Loads climate transition data (e.g., carbon price, emissions)  
- Loads macroeconomic data (e.g., GDP projections from NiGEM)  
- Selects climate scenarios (e.g., Net Zero 2050, Delayed Transition)  

Calculates projected PD shocks using two alternative models:

### 1. Linear Model

PD_new = PD_base × (1 + β_macro × GDP_shock + β_carbon × Carbon_price_increase)


### 2. Logit-Transformed Model

logit(PD_new) = logit(PD_base) + β_macro × GDP_shock + β_carbon × Carbon_price_increase + β_emissions × Emissions_growth


Where:

- `logit(p) = log(p / (1 - p))`  
- `Emissions_growth = (Emissions_scenario - Emissions_baseline) / Emissions_baseline`

---

## 🔧 Assumptions

- `β_macro`, `β_carbon`, and `β_emissions` are fixed sensitivities representing exposure to macroeconomic, transition, and emissions-related risks.
- GDP shock is calculated as a relative deviation from a scenario baseline year.
- Carbon price is used as a proxy for transition-related stress, particularly in energy-intensive sectors.
- The linear model is simple and transparent.
- The logit model ensures projected PDs remain in the valid [0, 1] probability range and incorporates emissions dynamics.

---

## 💼 Example Use Cases

This framework can be adapted to stress test:

- **Real Estate sector** – sensitive to GDP decline  
- **Utilities / Energy sector** – sensitive to carbon price and emissions growth  

The model can eb extended to:

- **Country-specific analysis**  
- **Sectoral portfolio simulations**  
- **Integrated credit risk modeling** including LGD (Loss Given Default) and EAD (Exposure at Default)
