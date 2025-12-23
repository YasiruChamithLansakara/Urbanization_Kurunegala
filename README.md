# 🏙️ Urbanization Analysis - Kurunegala District, Sri Lanka

A comprehensive satellite-based urban growth analysis and prediction system using Landsat 8/9 imagery to monitor, analyze, and forecast urbanization patterns in Kurunegala District (2013-2030).

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Data Requirements](#data-requirements)
- [Usage Guide](#usage-guide)
- [Methodology](#methodology)
- [Outputs](#outputs)
- [Results Interpretation](#results-interpretation)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## 🎯 Overview

This project provides a complete workflow for analyzing urban growth in Kurunegala District using satellite remote sensing data. It combines multiple techniques including:

- **Multi-spectral index analysis** (NDVI, NDBI, UI, MNDWI)
- **Time series analysis** (2013-2025)
- **Advanced machine learning models** (Prophet, ARIMA, Random Forest, XGBoost, LSTM)
- **Spatial analysis** (potential growth mapping)
- **Deep learning predictive modeling** (forecasts to 2030)

### 🗺️ Study Area

**Kurunegala District, North Western Province, Sri Lanka**
- 30 administrative divisions
- Mix of urban centers, agricultural land, and natural vegetation
- Experiencing rapid urbanization and economic growth

---

## ✨ Features

### 1. **Urban Area Detection**
- Multi-index approach for robust urban classification
- Automated processing of Landsat scenes
- Monthly and yearly statistics generation
- Change detection mapping

### 2. **Growth Analysis**
- Temporal trend analysis (2013-2025)
- Seasonal pattern identification
- Growth rate calculations
- Division-level statistics

### 3. **Potential Growth Mapping**
- Identifies high-potential areas for future development
- 5-zone classification (Very Low to Very High potential)
- Considers proximity to existing urban areas and terrain suitability
- Planning recommendations

### 4. **Predictive Modeling**
- Six model comparison (Prophet, ARIMA, Random Forest, XGBoost, LSTM, K-Means)
- LSTM-based forecast to 2030 with confidence intervals
- Iterative prediction using deep learning
- Year-by-year growth projections
- Infrastructure planning insights with uncertainty quantification

---

## 📁 Project Structure

```
Urbanization_Kurunegala/
│
├── AOI/                                    # Area of Interest data
│   ├── gadm41_LKA.gpkg                    # Sri Lanka administrative boundaries
│   └── kurunegala_District_AOI.geojson    # Kurunegala district boundary
│
├── Code/                                   # Analysis notebooks
│   ├── AOI Kurunegala District.ipynb     # Extract district boundary
│   ├── Urbanization Analysis.ipynb       # Main urbanization analysis
│   ├── Potential Urban Growth Area Mapping/
│   │   └── Potential Urban Growth Area Mapping.ipynb
│   │                                      # Growth potential mapping
│   └── Urban Growth Prediction Models Comparison/
│       └── Urban Growth Prediction Models Comparison.ipynb
│                                          # Future predictions (2026-2030)
│
├── Processed_Monthly/                     # Analysis outputs
│   ├── NDVI_YYYYMMDD.tif                 # Vegetation indices
│   ├── NDBI_YYYYMMDD.tif                 # Built-up indices
│   ├── UI_YYYYMMDD.tif                   # Urban indices
│   ├── MNDWI_YYYYMMDD.tif                # Water indices
│   ├── Urban_YYYYMMDD.tif                # Urban classifications
│   ├── UrbanChange_*.tif                 # Change detection maps
│   ├── Kurunegala_Urbanization_Stats.csv # Statistics
│   └── *.png                             # Visualizations
│
├── Potential_Growth_Areas/                # Growth potential outputs
│   ├── Kurunegala_Potential_Score.tif    # Development scores
│   ├── Kurunegala_Potential_Zones.tif    # Zone classifications
│   └── *.png                             # Maps and charts
│
├── Urban_Growth_Predictions/              # Prediction outputs
│   ├── Kurunegala_Forecast_2026_2030_LSTM.csv  # LSTM year-by-year forecasts
│   ├── Model_Comparison_Results.csv      # All 6 models performance
│   ├── KMeans_Temporal_Clusters.png      # Growth phase clusters
│   ├── Kurunegala_Clusters.csv           # Cluster assignments
│   └── *.png                             # Forecast visualizations
│
└── README.md                              # This file
```

---

## 🔧 Prerequisites

### Software Requirements

- **Python 3.11+** (recommended)
- **Jupyter Notebook** or **JupyterLab**
- **Git** (for version control)

### Python Libraries

Install all dependencies using:

```bash
pip install geopandas rasterio numpy pandas matplotlib seaborn tqdm prophet statsmodels scikit-learn xgboost tensorflow
```

**Core Libraries:**
- `geopandas` - Vector data handling
- `rasterio` - Raster data processing
- `numpy` - Numerical computations
- `pandas` - Data analysis
- `matplotlib` / `seaborn` - Visualization
- `tqdm` - Progress bars

**Machine Learning & Deep Learning:**
- `prophet` - Facebook's time series forecasting
- `statsmodels` - ARIMA modeling
- `scikit-learn` - Random Forest and K-Means clustering
- `xgboost` - Gradient boosting (XGBoost)
- `tensorflow` / `keras` - Deep learning (LSTM neural networks)

### GIS Software (Optional but Recommended)

- **QGIS** (free) - View and analyze GeoTIFF outputs
- **ArcGIS** (commercial)
- Download QGIS: https://qgis.org/

---

## 📥 Data Requirements

### 1. Administrative Boundaries

✅ **Already included** in `AOI/gadm41_LKA.gpkg`

Source: [GADM](https://gadm.org/)

### 2. Satellite Imagery

**Data Source:** USGS EarthExplorer
- **Link:** https://earthexplorer.usgs.gov/
- **Dataset:** Landsat 8-9 Collection 2 Level-2 (Surface Reflectance)
- **Period:** 2013-2025
- **Cloud Cover:** < 20% recommended

**Required Bands:**
- Band 2 (Blue) - SR_B2.TIF
- Band 3 (Green) - SR_B3.TIF
- Band 4 (Red) - SR_B4.TIF
- Band 5 (NIR) - SR_B5.TIF
- Band 6 (SWIR1) - SR_B6.TIF
- Band 7 (SWIR2) - SR_B7.TIF

### 3. Data Organization

Organize downloaded Landsat data by year:

```
D:\Satellite Image Processing\Satellite Images\
├── 2013/
│   ├── LC08_*_SR_B2.TIF
│   ├── LC08_*_SR_B3.TIF
│   ├── LC08_*_SR_B4.TIF
│   ├── LC08_*_SR_B5.TIF
│   ├── LC08_*_SR_B6.TIF
│   └── LC08_*_SR_B7.TIF
├── 2014/
├── 2015/
...
└── 2025/
```

---

## 🚀 Installation

### 1. Clone or Download Project

```bash
git clone <repository-url>
cd Urbanization_Kurunegala
```

### 2. Install Python Dependencies

```bash
pip install -r requirements.txt
```

Or manually install:

```bash
pip install geopandas rasterio numpy pandas matplotlib seaborn tqdm prophet statsmodels scikit-learn xgboost tensorflow scipy plotly
```

### 3. Verify Installation

```python
import geopandas as gpd
import rasterio
import pandas as pd
from prophet import Prophet

print("✅ All libraries installed successfully!")
```

---

## 📖 Usage Guide

### Step 1: Extract Area of Interest (AOI)

**Notebook:** `Code/AOI Kurunegala District.ipynb`

```python
# Run this notebook to extract Kurunegala district boundary
# Output: AOI/kurunegala_District_AOI.geojson
```

**What it does:**
- Loads GADM administrative boundaries
- Filters for Kurunegala district (30 divisions)
- Saves as GeoJSON for analysis

**Runtime:** ~1 minute

---

### Step 2: Urbanization Analysis (Main Analysis)

**Notebook:** `Code/Urbanization Analysis.ipynb`

**⚠️ Prerequisites:**
- Landsat data organized in year folders
- AOI boundary created (Step 1)

**What it does:**
1. Loads Kurunegala district boundary
2. Processes each Landsat scene:
   - Clips to district boundary
   - Calculates spectral indices (NDVI, NDBI, UI, MNDWI)
   - Classifies urban areas using multi-index approach
3. Generates monthly statistics
4. Creates visualizations and change maps

**Processing Time:** 2-5 minutes per scene (depends on your computer)

**Urban Classification Criteria:**
- NDBI > 0.0 (Built-up indicator)
- NDVI < 0.3 (Low vegetation)
- UI > 0.0 (Urban index positive)
- MNDWI < 0.0 (Not water)

**Outputs:**
- `Processed_Monthly/` folder with:
  - Urban classification maps (Urban_YYYYMMDD.tif)
  - Spectral indices (NDVI, NDBI, UI, MNDWI)
  - Kurunegala_Urbanization_Stats.csv
  - Trend visualizations (6-panel analysis)
  - Change detection maps (4-class classifications)

---

### Step 3: Potential Growth Mapping (Optional)

**Notebook:** `Code/Potential Urban Growth Area Mapping/Potential Urban Growth Area Mapping.ipynb`

**⚠️ Prerequisites:**
- Completed Step 2 (Urbanization Analysis)

**What it does:**
1. Loads latest urban and NDVI maps
2. Calculates development potential based on:
   - Proximity to existing urban areas (50% weight)
   - Terrain suitability / NDVI (50% weight)
3. Classifies areas into 5 zones (Very Low to Very High potential)
4. Provides planning recommendations

**Zone Classifications:**
- **Zone 5:** Very High Potential (priority development)
- **Zone 4:** High Potential (secondary phase)
- **Zone 3:** Medium Potential (long-term)
- **Zone 2:** Low Potential
- **Zone 1:** Very Low Potential

**Outputs:**
- `Potential_Growth_Areas/` folder with:
  - Kurunegala_Potential_Score.tif (0-1 normalized scores)
  - Kurunegala_Potential_Zones.tif (5-zone classification)
  - Analysis visualizations (multi-panel maps)
  - Planning recommendations and statistics

**Runtime:** 2-3 minutes

---

### Step 4: Future Predictions (2026-2030)

**Notebook:** `Code/Urban Growth Prediction Models Comparison/Urban Growth Prediction Models Comparison.ipynb`

**⚠️ Prerequisites:**
- Completed Step 2 (Urbanization Analysis)
- Kurunegala_Urbanization_Stats.csv generated

**What it does:**
1. Loads urbanization statistics from CSV
2. Trains and compares **6 prediction models**:
   - **Prophet** (Facebook's time series forecasting)
   - **ARIMA** (AutoRegressive Integrated Moving Average)
   - **Random Forest** (Ensemble machine learning)
   - **XGBoost** (Gradient boosting - typically best accuracy)
   - **LSTM** (Deep learning neural network - BEST MODEL)
   - **K-Means** (Clustering for growth phase identification)
3. Evaluates models using MAE, RMSE, R², MAPE metrics
4. Identifies LSTM as best performing model
5. **Uses LSTM for final 2026-2030 forecasts** with iterative prediction
6. Generates confidence intervals (95%) based on training errors
7. Provides detailed urban planning insights

**Model Performance:**
- **LSTM** achieves lowest RMSE (best accuracy)
- Captures non-linear urban growth patterns
- Learns long-term dependencies from historical data
- Iterative forecasting maintains temporal coherence

**Outputs:**
- `Urban_Growth_Predictions/` folder with:
  - **Kurunegala_Forecast_2026_2030_LSTM.csv** - Final LSTM predictions
  - Model_Comparison_Results.csv - All 6 models performance
  - Model_Forecast_Comparison.png - Visual comparison
  - Kurunegala_Urbanization_Forecast_2026_2030_LSTM.png - LSTM forecast
  - KMeans_Temporal_Clusters.png - Growth phase clusters
  - Kurunegala_Clusters.csv - Cluster assignments

**Runtime:** 3-5 minutes (LSTM training takes longer but provides best accuracy)

---

## 🔬 Methodology

### Urban Classification Algorithm

```
Urban Pixel = (NDBI > 0.0) AND 
               (NDVI < 0.3) AND 
               (UI > 0.0) AND 
               (MNDWI < 0.0)
```

**Where:**

**NDVI** (Vegetation Index):
```
NDVI = (NIR - Red) / (NIR + Red)
```

**NDBI** (Built-up Index):
```
NDBI = (SWIR1 - NIR) / (SWIR1 + NIR)
```

**UI** (Urban Index):
```
UI = (SWIR2 - NIR) / (SWIR2 + NIR)
```

**MNDWI** (Water Index):
```
MNDWI = (Green - SWIR1) / (Green + SWIR1)
```

### Potential Growth Scoring

```
Potential Score = 0.5 × Proximity Score + 0.5 × Terrain Suitability
```

**Proximity Score:**
- < 1 km from urban: 0.9
- 1-3 km (optimal): 1.0
- 3-5 km: 0.6
- > 5 km: 0.3

**Terrain Suitability:**
- NDVI < 0.2: 1.0 (very suitable)
- NDVI 0.2-0.4: 0.8 (suitable)
- NDVI 0.4-0.6: 0.5 (moderate)
- NDVI > 0.6: 0.2 (preserve vegetation)

---

## 📊 Outputs

### 1. Raster Products (GeoTIFF)

**Spectral Indices:**
- `NDVI_YYYYMMDD.tif` - Vegetation index (-1 to +1)
- `NDBI_YYYYMMDD.tif` - Built-up index (-1 to +1)
- `UI_YYYYMMDD.tif` - Urban index (-1 to +1)
- `MNDWI_YYYYMMDD.tif` - Water index (-1 to +1)

**Classifications:**
- `Urban_YYYYMMDD.tif` - Binary urban map (0=non-urban, 1=urban)
- `UrbanChange_*.tif` - Change map (-1=lost urban, 0=no change, +1=new urban)

**Potential Growth:**
- `Kurunegala_Potential_Score.tif` - Development potential (0-1)
- `Kurunegala_Potential_Zones.tif` - Zone classification (0-5)

### 2. Statistics (CSV)

**Kurunegala_Urbanization_Stats.csv**
```csv
Date,Year,Month,Urban_Pixels,Valid_Pixels,Urban_Area_km2,Urban_Percentage
2013-05-26,2013,5,125430,2456789,112.89,5.11
...
```

**Kurunegala_Forecast_2026_2030_LSTM.csv**
```csv
Date,Predicted_Urban_km2,Lower_Bound_km2,Upper_Bound_km2
2026-01-01,145.32,138.45,152.19
...
```

**Model_Comparison_Results.csv**
```csv
Model,MAE (km²),RMSE (km²),R²,MAPE (%)
Prophet,2.45,3.21,0.95,1.85
ARIMA,3.12,4.05,0.89,2.34
Random Forest,2.78,3.56,0.92,2.10
XGBoost,2.31,3.02,0.96,1.76
LSTM,2.18,2.89,0.97,1.65
```

### 3. Visualizations (PNG)

- **Temporal Trends:** Line charts showing urban growth over time
- **Change Maps:** Visual representation of urban expansion
- **Seasonal Analysis:** Monsoon season patterns
- **Zone Maps:** Color-coded potential development areas
- **Forecast Charts:** Future predictions with confidence intervals

---

## 📈 Results Interpretation

### Understanding NDVI Values

| NDVI Range | Land Cover Type |
|------------|-----------------|
| -1.0 to 0.0 | Water, clouds, snow |
| 0.0 to 0.2 | Bare soil, sand, urban |
| 0.2 to 0.4 | Sparse vegetation, grassland |
| 0.4 to 0.6 | Moderate vegetation |
| 0.6 to 0.9 | Dense vegetation, forests |

### Understanding NDBI Values

| NDBI Range | Interpretation |
|------------|----------------|
| < -0.1 | Water bodies |
| -0.1 to 0.0 | Vegetation |
| 0.0 to 0.1 | Bare soil / mixed |
| 0.1 to 0.3 | Built-up areas |
| > 0.3 | Dense urban |

### Urban Growth Metrics

**Current Urbanization (Example):**
- Urban Area: ~120 km²
- District Coverage: ~5% urbanized
- Average Annual Growth: 2-3%

**2030 Prediction (Example):**
- Projected Urban Area: ~145 km²
- Expected Growth: ~25 km² (20% increase)
- New Development Needed: ~2,500 hectares

---

## 🛠️ Troubleshooting

### Common Issues

**1. "No Landsat data found"**
```
Solution: Check satellite data path in notebook
Update: SATELLITE_DATA_DIR = r"D:\Satellite Image Processing\Satellite Images"
```

**2. "AOI file not found"**
```
Solution: Run AOI_POLYGON.ipynb first to create boundary
```

**3. "Memory Error"**
```
Solution: Process fewer years at once or increase RAM
Reduce: YEARS = range(2020, 2026)  # Instead of 2013-2026
```

**4. "Prophet installation fails"**
```bash
# On Windows, install from conda
conda install -c conda-forge prophet

# Or use pip with specific version
pip install prophet==1.1.5
```

**5. "Rasterio errors on Windows"**
```bash
# Install from conda-forge
conda install -c conda-forge rasterio

# Or use OSGeo4W
```

---

## 🌟 Best Practices

### Data Quality

1. **Cloud Cover:** Use scenes with < 20% cloud cover
2. **Temporal Consistency:** Regular intervals for better predictions
3. **Quality Check:** Manually review urban classifications

### Processing Tips

1. **Start Small:** Test with 1-2 years first
2. **Backup Data:** Keep original Landsat files safe
3. **Version Control:** Track changes in analysis notebooks
4. **Documentation:** Note any manual adjustments

### Analysis Workflow

```
1. Extract AOI → 2. Run Urbanization Analysis → 
3. Validate Results → 4. Growth Mapping → 5. Predictions
```

---

## 📚 References

### Scientific Papers

1. Zha, Y., et al. (2003). "Use of normalized difference built-up index in automatically mapping urban areas from TM imagery"
2. Rouse, J.W., et al. (1974). "Monitoring vegetation systems in the Great Plains with ERTS"
3. Xu, H. (2006). "Modification of normalised difference water index (NDWI) to enhance open water features"

### Data Sources

- **Landsat Data:** USGS EarthExplorer - https://earthexplorer.usgs.gov/
- **Administrative Boundaries:** GADM - https://gadm.org/
- **Sri Lanka Data:** Survey Department of Sri Lanka

### Tools & Libraries

- **Rasterio:** https://rasterio.readthedocs.io/
- **GeoPandas:** https://geopandas.org/
- **Prophet:** https://facebook.github.io/prophet/
- **QGIS:** https://qgis.org/

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### How to Contribute

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Areas for Improvement

- [x] Add more prediction models (LSTM, XGBoost) ✅ **Completed**
- [ ] Include population data integration
- [ ] Add web-based dashboard
- [ ] Implement real-time monitoring
- [ ] Add automated report generation
- [ ] Ensemble predictions combining LSTM + XGBoost
- [ ] GPU acceleration for LSTM training

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 📧 Contact

**Project Maintainer:** Yasiru Lansakara
- Email: yasiruchamithlansakara@gmail.com
- GitHub: [@YasiruChamithLansakara](https://github.com/YasiruChamithLansakara)

---

## 🙏 Acknowledgments

- USGS for providing free Landsat imagery
- GADM for administrative boundary data
- Facebook Research for the Prophet forecasting library
- Open source GIS community

---

## 📌 Citation

If you use this project in your research, please cite:

```bibtex
@software{kurunegala_urbanization_2025,
  author = {Yasiru Lansakara},
  title = {Urbanization Analysis - Kurunegala District},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/YasiruChamithLansakara/urbanization-kurunegala}
}
```

---

## 🔄 Version History

- **v1.1.0** (2025-Current) - Advanced modeling update
  - Added XGBoost gradient boosting model
  - Added LSTM deep learning model
  - LSTM-based forecasting (2026-2030)
  - Six-model comparison framework
  - Iterative prediction with confidence intervals

- **v1.0.0** (2025-12-07) - Initial release
  - Multi-index urban classification
  - Time series analysis (2013-2025)
  - Growth potential mapping
  - Predictive modeling to 2030

---

## 📝 Notes

### System Requirements

- **RAM:** 8GB minimum, 16GB recommended
- **Storage:** 150GB for Landsat data + 10GB for outputs
- **CPU:** Multi-core processor recommended for faster processing

### Processing Time Estimates

| Task | Scenes | Estimated Time |
|------|--------|----------------|
| AOI Extraction | N/A | 1 minute |
| Urbanization Analysis | 100 scenes | 3-5 hours |
| Growth Mapping | N/A | 2-3 minutes |
| Predictions | N/A | 1-2 minutes |

**Total Project Time:** 4-6 hours (including data download)

---

**🏙️ Happy Analyzing! Contribute to sustainable urban planning in Kurunegala District! 🌿**
