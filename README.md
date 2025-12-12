# Weather Forecasting Model

A weather forecasting and analysis project using historical weather data from Buffalo Niagara International Airport.

## Dataset

The project uses weather observation data from **Buffalo Niagara International Airport (KBUF)**, NY, US.

### Data Source

- **Station ID**: 72528014733
- **Location**: Buffalo Niagara International Airport, NY, US
- **Coordinates**: 42.94°N, 78.74°W
- **Elevation**: 218.2m
- **Time Period**: Starting from January 1, 2014

### Key Weather Parameters

The dataset contains comprehensive meteorological observations including:

- Temperature (TMP) and Dew Point (DEW)
- Wind Direction and Speed (WND)
- Sea Level Pressure (SLP)
- Ceiling Height (CIG) and Visibility (VIS)
- Precipitation data
- Cloud coverage
- Weather phenomena (snow, fog, freezing conditions, etc.)
- Various atmospheric measurements

## Features

- **Machine Learning Temperature Forecasting**: Predicts daily temperatures using historical patterns
- **Time Series Analysis**: Uses lag features and rolling averages for predictions
- **Multiple ML Models**: Implements both Linear Regression and Random Forest models
- **Model Comparison**: Evaluates and compares model performance using Mean Absolute Error (MAE)
- **Data Visualization**: Plots actual vs predicted temperatures
- Historical weather data cleaning and preprocessing

## Data Format

The data is provided in CSV format with the following main fields:

- `STATION`: Weather station identifier
- `DATE`: Observation date and time (ISO format)
- `LATITUDE`/`LONGITUDE`: Geographic coordinates
- `NAME`: Station name
- `TMP`: Air temperature
- `DEW`: Dew point temperature
- `SLP`: Sea level pressure
- `WND`: Wind observations
- `VIS`: Visibility
- Various weather codes and quality control flags

## Getting Started

### Prerequisites

```bash
Python 3.7+
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
scikit-learn>=1.0.0
```

### Installation

```bash
# Clone the repository
git clone https://github.com/kiganyamburu/Weather-Forecasting-Model.git

# Navigate to the project directory
cd Weather-Forecasting-Model

# Install required packages
pip install pandas numpy matplotlib scikit-learn

# Or use requirements.txt if available
pip install -r requirements.txt

# Launch Jupyter Notebook
jupyter notebook Weather_Forecasting_Model.ipynb
```

## Usage

### Running the Notebook

The main analysis is in `Weather_Forecasting_Model.ipynb`. The notebook includes:

1. **Data Loading and Preprocessing**: Loads the CSV data and parses dates
2. **Temperature Data Cleaning**: Extracts and scales temperature values, handles missing data
3. **Feature Engineering**: Creates lag features and rolling averages for time series prediction
4. **Model Training**: Trains Linear Regression and Random Forest models
5. **Evaluation**: Compares models using MAE and visualizes predictions

### Quick Start

```python
import pandas as pd
import numpy as np
from sklearn.ensemble import RandomForestRegressor

# Load the weather data
df = pd.read_csv('BUFFALO NIAGARA INTERNATIONAL.csv')
df['DATE'] = pd.to_datetime(df['DATE'])

# Clean temperature data
df['temp_str'] = df['TMP'].astype(str).str.split(',').str[0]
df['temp_str'] = df['temp_str'].replace('+9999', np.nan)
df['temperature'] = df['temp_str'].astype(float) / 10.0

# Resample to daily averages
df = df.set_index('DATE')
daily_df = df['temperature'].resample('D').mean().to_frame()
```

## Project Structure

```
Weather-Forecasting-Model/
│
├── BUFFALO NIAGARA INTERNATIONAL.csv     # Historical weather dataset
├── Weather_Forecasting_Model.ipynb       # Main ML forecasting notebook
├── README.md                              # Project documentation
└── requirements.txt                       # Python dependencies
```

## Machine Learning Approach

### Models Implemented

1. **Linear Regression**

   - Simple baseline model
   - Fast training and prediction
   - Good for understanding linear relationships

2. **Random Forest Regressor**
   - Ensemble learning method
   - Captures non-linear patterns
   - More robust to outliers
   - Better performance on complex weather patterns

### Features Used

- **lag_1**: Previous day's temperature
- **lag_2**: Temperature from 2 days ago
- **rolling_mean_3**: 3-day moving average
- **rolling_mean_7**: 7-day moving average

These features capture short-term and medium-term temperature trends, helping the models predict future temperatures.

## Potential Analyses

### Current Implementation

- **Temperature Forecasting**: Daily temperature prediction using ML models
- **Time Series Feature Engineering**: Lag variables and rolling averages
- **Model Performance Comparison**: Linear Regression vs Random Forest

### Future Enhancements

- **Advanced Models**: LSTM, ARIMA, or Prophet for better time series forecasting
- **Multi-variable Prediction**: Incorporate wind, pressure, and humidity as features
- **Precipitation Prediction**: Forecast rainfall and snowfall events
- **Seasonal Analysis**: Study weather patterns across different seasons
- **Extreme Weather Detection**: Identify and analyze severe weather events
- **Climate Trends**: Long-term temperature and precipitation trend analysis

## Data Quality

The dataset includes quality control flags (`QUALITY_CONTROL`) and various report types (`REPORT_TYPE`) to ensure data reliability:

- FM-12: Synoptic reports
- FM-15: METAR aviation reports
- FM-16: Special aviation reports
- SOD/SOM: Summary of day/month reports

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open source and available under the MIT License.

## Repository

GitHub: [kiganyamburu/Weather-Forecasting-Model](https://github.com/kiganyamburu/Weather-Forecasting-Model)

## Acknowledgments

- Data source: National Weather Service / NOAA
- Station: Buffalo Niagara International Airport (KBUF)

---

**Note**: This is a data analysis and forecasting project. Always refer to official weather services for real-time weather forecasts and warnings.
