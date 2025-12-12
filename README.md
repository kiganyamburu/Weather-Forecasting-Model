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

- Historical weather data analysis
- Temperature trends and patterns
- Precipitation analysis
- Wind conditions monitoring
- Atmospheric pressure tracking
- Weather event detection (snow, fog, etc.)

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
Python 3.x
pandas
numpy
matplotlib (for visualization)
scikit-learn (for forecasting models)
```

### Installation

```bash
# Clone the repository
git clone https://github.com/kiganyamburu/Weather-Forecasting-Model.git

# Navigate to the project directory
cd Weather-Forecasting-Model

# Install required packages
pip install -r requirements.txt
```

## Usage

```python
import pandas as pd

# Load the weather data
df = pd.read_csv('BUFFALO NIAGARA INTERNATIONAL.csv')

# Basic data exploration
print(df.head())
print(df.info())
```

## Project Structure

```
Weather-Forecasting-Model/
│
├── BUFFALO NIAGARA INTERNATIONAL.csv    # Main dataset
├── README.md                             # Project documentation
└── (additional scripts and notebooks)
```

## Potential Analyses

- **Temperature Forecasting**: Predict future temperatures based on historical patterns
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
