## Data Collection
### Data Sources:
1. **Claims** (FEMA NFIP): https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2 and NC 
2. **Buildings** (NC Buildings GDB): https://sdd.nc.gov/buildingfootprints2010
3. **Flood** (GeoTIFF of 7 flood events from 1996–2018)

## Target Scope and Resolution
- Spatial Scope: 5 selected NC counties (Beaufort、Edgecombe、Lenoir、Robeson、Wayne)
- Spatial Resolution: 0.1° * 0.1° grid cell
- Temporal Resolution and Scope: 7 discrete flood events from 1996-2018

## Data Cleaning
1. filter **Claims** and **Buildings** data to 5 selected counties
2. aggregate **Claims** and **Buildings** data by grid cell
3. combine with grid-level **Flood** data

### key parameter calculations at cell-level
    - loss ratio = total claims amount / total building value
    - flood ratio = flooded pixels / all pixels
    - mean height of first flour: mean_hag = mean(FFE - LIDAR_LAG) 

## Final Model Dataset
`../data/dataset aggregation/output/agg_model_dataset.csv`
1. target varable: 
    - loss_ratio (claims)
2. predictor variables: 
    - flood_ratio (flood)
    - mean_hag (building)
    - pct_elevated (building)
    - res_ratio (building)
    - bldg_density (building)
    - mean_bldg_value (building)
    - mean_sqft (building)
    - areaSqKm_developed (building)