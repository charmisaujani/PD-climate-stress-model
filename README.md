# Climate Scenario PD Stress Test

This project analyzes credit risk under NGFS climate transition scenarios using downscaled data from IAM models (like REMIND-MAgPIE) and macroeconomic projections (NiGEM). The output simulates future Probabilities of Default (PD) for selected sectors under different climate transition scenarios.

## 📁 Files

- `pd_climate_stress_test.py`: Main script that loads scenario data, extracts macro & transition variables, and calculates projected PDs.
- `Downscaled_REMIND-MAgPIE...xlsx`: IAM climate scenario data.
- `NiGEM_data.xlsx`: Macroeconomic data by country and scenario.
  
## 📊 What the Script Does

1. **Loads climate transition data** (e.g., carbon price, emissions)
2. **Loads macroeconomic data** (e.g., GDP projections from NiGEM)
3. **Selects scenarios** (e.g., Net Zero 2050, Delayed Transition)
4. **Calculates PD shocks** using:

    PD_new = PD_base × (1 + β_macro × GDP_shock + β_carbon × Carbon_price_increase)

## Assumptions

- `β_macro` and `β_carbon` are fixed sensitivities to macro & transition risk.
- GDP shock is calculated as relative drop from baseline year.
- Carbon price is assumed to reflect sectoral stress for energy-intensive industries.
- The model is linear for simplicity and transparency.

## Example Use Case

You can adapt this framework to stress test:
- Real Estate sector (GDP-driven)
- Utilities / Energy (Carbon price-driven)

Or expand to:
- Country-specific stress
- Sectoral portfolios
- LGD/EAD interaction
