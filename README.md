# Forest Fire Prediction and Spread Simulation System

A comprehensive machine learning system for predicting forest fire likelihood and simulating fire spread patterns using geospatial data and environmental factors.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Data Sources](#data-sources)
- [Model Architecture](#model-architecture)
- [Output Files](#output-files)
- [Scenarios](#scenarios)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## Overview

This project implements a complete forest fire prediction and spread simulation system using:
- **Machine Learning**: Random Forest classifier for fire likelihood prediction
- **Geospatial Analysis**: Rasterio for processing satellite and environmental data
- **Fire Spread Simulation**: Custom cellular automaton model for fire spread dynamics
- **Visualization**: Interactive maps and animations of fire spread patterns
- **Scenario Analysis**: Multiple environmental scenarios (drought, summer, urban interface, windy conditions)

## Features

### Core Functionality
- ✅ **Fire Prediction**: ML-based fire likelihood prediction using environmental factors
- ✅ **Spread Simulation**: Time-based fire spread simulation with customizable parameters
- ✅ **Multi-Scenario Analysis**: Support for drought, summer, urban interface, and windy scenarios
- ✅ **Comprehensive Visualization**: Maps, correlation matrices, and animated fire spread
- ✅ **Model Persistence**: Save/load trained models for reuse
- ✅ **Data Quality Assessment**: Automatic data validation and quality metrics

### Technical Features
- 🔧 **Modular Architecture**: Object-oriented design with separate classes for processing, modeling, and simulation
- 🔧 **Flexible Data Pipeline**: Supports various raster formats and projections
- 🔧 **Memory Efficient**: Optimized for large geospatial datasets
- 🔧 **Error Handling**: Robust error handling and logging
- 🔧 **Cross-Platform**: Works on Windows, macOS, and Linux

## Project Structure

```
forest/
├── forest_fire_prediction.ipynb    # Main Jupyter notebook
├── README.md                       # This file
├── requirements.txt               # Python dependencies
├── data/                          # Input data directory
│   ├── dem.tif                   # Digital Elevation Model
│   ├── fire_labels.tif           # Historical fire occurrence data
│   ├── humidity.tif              # Humidity data
│   ├── lulc.tif                  # Land Use/Land Cover
│   ├── rainfall.tif              # Rainfall data
│   ├── roads.tif                 # Road network data
│   ├── settlements.tif           # Settlement data
│   ├── temperature.tif           # Temperature data
│   ├── wind_dir.tif              # Wind direction
│   ├── wind_speed.tif            # Wind speed
│   └── scenarios/                # Scenario-specific data
│       ├── drought_scenario/
│       ├── summer_scenario/
│       ├── urban_interface/
│       └── windy_scenario/
├── models/                        # Trained models
│   └── fire_prediction_model.pkl
└── output/                        # Generated outputs
    ├── comprehensive_results.png
    ├── correlation_matrix.csv
    ├── fire_conditions_summary.csv
    ├── fire_prediction.tif
    ├── fire_probability.tif
    ├── fire_spread_*.tif
    ├── fire_spread_animation.gif
    └── model_report.csv
```

## Installation

### Prerequisites
- Python 3.8 or higher
- Jupyter Notebook or JupyterLab
- GDAL (for rasterio)

### Setup Instructions

1. **Clone or download the project:**
   ```bash
   git clone <repository-url>
   cd forest
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Install GDAL (if not already installed):**
   - **Windows**: Download from https://www.lfd.uci.edu/~gohlke/pythonlibs/#gdal
   - **macOS**: `brew install gdal`
   - **Linux**: `sudo apt-get install gdal-bin libgdal-dev`

### Required Python Packages
```
numpy>=1.21.0
pandas>=1.3.0
scikit-learn>=1.0.0
rasterio>=1.2.0
matplotlib>=3.4.0
seaborn>=0.11.0
joblib>=1.0.0
tqdm>=4.62.0
```

## Usage

### Quick Start

1. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook forest_fire_prediction.ipynb
   ```

2. **Run the notebook:**
   - Execute all cells in order
   - Choose between training a new model or using an existing one
   - Review the comprehensive results in the final summary cell

### Model Training Options

When you run the notebook, you'll be prompted to choose:
- **Option 1**: Train a new model (recommended for first run)
- **Option 2**: Use existing model (if `models/fire_prediction_model.pkl` exists)

### Key Parameters

You can modify these parameters in the notebook:
```python
# Model parameters
n_estimators = 100          # Number of trees in Random Forest
max_depth = 10              # Maximum depth of trees
test_size = 0.2             # Train/test split ratio

# Simulation parameters
max_iterations = 100        # Maximum simulation steps
wind_influence = 0.3        # Wind effect on spread
humidity_threshold = 0.5    # Humidity threshold for spread
```

## Data Sources

### Input Data Requirements

The system expects the following raster files in the `data/` directory:

| File | Description | Format | Resolution |
|------|-------------|--------|------------|
| `dem.tif` | Digital Elevation Model | GeoTIFF | 30m |
| `fire_labels.tif` | Historical fire occurrence | GeoTIFF | 30m |
| `humidity.tif` | Relative humidity (%) | GeoTIFF | 30m |
| `lulc.tif` | Land use/land cover | GeoTIFF | 30m |
| `rainfall.tif` | Annual rainfall (mm) | GeoTIFF | 30m |
| `roads.tif` | Distance to roads (m) | GeoTIFF | 30m |
| `settlements.tif` | Distance to settlements (m) | GeoTIFF | 30m |
| `temperature.tif` | Average temperature (°C) | GeoTIFF | 30m |
| `wind_dir.tif` | Wind direction (degrees) | GeoTIFF | 30m |
| `wind_speed.tif` | Wind speed (m/s) | GeoTIFF | 30m |

### Data Preparation

If you don't have the required data files, the notebook includes a data generation function that creates realistic synthetic data based on geographical patterns and environmental correlations.

## Model Architecture

### Machine Learning Pipeline

1. **Data Preprocessing**
   - Raster data loading and alignment
   - Missing value handling
   - Feature scaling and normalization

2. **Feature Engineering**
   - Elevation-based features
   - Distance calculations
   - Environmental indices

3. **Model Training**
   - Random Forest Classifier
   - Cross-validation
   - Hyperparameter optimization

4. **Evaluation**
   - Accuracy, precision, recall, F1-score
   - Feature importance analysis
   - Confusion matrix

### Fire Spread Simulation

The cellular automaton model considers:
- **Environmental factors**: Temperature, humidity, wind
- **Topographical features**: Elevation, slope
- **Infrastructure**: Roads, settlements
- **Fuel load**: Vegetation type and density

## Output Files

### Raster Outputs
- `fire_prediction.tif`: Binary fire/no-fire prediction
- `fire_probability.tif`: Fire probability (0-1)
- `fire_spread_*.tif`: Fire spread maps at different time intervals

### Visualization Outputs
- `comprehensive_results.png`: Multi-panel visualization
- `fire_spread_animation.gif`: Animated fire spread

### Analysis Reports
- `model_report.csv`: Model performance metrics
- `correlation_matrix.csv`: Feature correlation analysis
- `fire_conditions_summary.csv`: Fire condition statistics

## Scenarios

The system includes four pre-configured scenarios:

### 1. Drought Scenario
- Reduced humidity and rainfall
- Increased temperature
- Higher fire risk conditions

### 2. Summer Scenario
- Peak temperature conditions
- Typical summer weather patterns
- Seasonal fire risk assessment

### 3. Urban Interface Scenario
- Mixed urban-wildland areas
- Infrastructure considerations
- Population exposure analysis

### 4. Windy Scenario
- High wind speed conditions
- Directional fire spread
- Rapid fire propagation

## Troubleshooting

### Common Issues

1. **GDAL Installation Error**
   ```
   Error: Cannot install rasterio
   Solution: Install GDAL first, then rasterio
   ```

2. **Memory Issues**
   ```
   Error: Out of memory
   Solution: Reduce raster resolution or process in chunks
   ```

3. **File Not Found**
   ```
   Error: Data file not found
   Solution: Run data generation cell or check file paths
   ```

4. **Model Loading Error**
   ```
   Error: Cannot load model
   Solution: Train a new model or check model file path
   ```

### Performance Optimization

- **Large datasets**: Use data chunking or reduce resolution
- **Slow training**: Reduce `n_estimators` or use parallel processing
- **Memory usage**: Close unnecessary variables and clear cache

### Data Quality Issues

- **Missing data**: Check for NaN values in input rasters
- **Projection mismatch**: Ensure all rasters have the same CRS
- **Resolution differences**: Resample to common resolution

## Contributing

### Development Guidelines

1. **Code Style**: Follow PEP 8 conventions
2. **Documentation**: Add docstrings to all functions
3. **Testing**: Include unit tests for new features
4. **Performance**: Profile code for large datasets

### Reporting Issues

Please report issues with:
- System specifications
- Error messages
- Data characteristics
- Steps to reproduce

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Environmental data providers
- Open-source geospatial community
- Machine learning libraries (scikit-learn, pandas, numpy)
- Visualization tools (matplotlib, seaborn)

---

**Note**: This system is for research and educational purposes. For operational fire management, please consult with local fire authorities and use certified fire prediction systems.
