# data_ingestion
# Pine Ridge Indian Reservation - Geospatial Data Ingestion Project

## Project Overview

This project provides a data ingestion pipeline for environmental and geospatial datasets covering the Pine Ridge Indian Reservation in South Dakota. The pipeline standardizes data from multiple sources into consistent formats with proper spatial reference systems and metadata documentation.

## Data Sources

### **USGS NWIS (Hydrology)**
- **Source**: USGS National Water Information System
- **URL**: https://waterservices.usgs.gov/
- **Data Type**: Streamflow, groundwater levels, water quality
- **Temporal Coverage**: 2010-present
- **Format**: Parquet (time series), GeoJSON (site locations)

### **PRISM (Climate)**
- **Source**: PRISM Climate Group, Oregon State University
- **URL**: https://prism.oregonstate.edu/
- **Data Type**: Precipitation, temperature (min/max/mean)
- **Resolution**: 4km (~800m)
- **Temporal**: Monthly/Daily
- **Format**: NetCDF, Zarr

### **Daymet (Climate)**
- **Source**: Oak Ridge National Laboratory DAAC
- **URL**: https://daymet.ornl.gov/
- **Data Type**: Daily surface weather data
- **Resolution**: 1km
- **Temporal**: Daily (1980-present)
- **Format**: NetCDF, Zarr

### **CDL - Cropland Data Layer**
- **Source**: USDA National Agricultural Statistics Service
- **URL**: https://nassgeodata.gmu.edu/CropScape/
- **Data Type**: Crop type classification
- **Resolution**: 30m
- **Temporal**: Annual (2008-present)
- **Format**: GeoTIFF, NetCDF

### 5. **SMAP (Soil Moisture)**
- **Source**: NASA Soil Moisture Active Passive Mission
- **URL**: https://nsidc.org/data/smap
- **Data Type**: Soil moisture (0-5cm depth)
- **Resolution**: 9km (L3), 3km (L4)
- **Temporal**: Daily (2015-present)
- **Format**: HDF5, NetCDF, Zarr

## Project Structure

pine_ridge_project/
├── README.md                          # This file
├── requirements.txt                   # Python dependencies
├── scripts/                          # Data ingestion scripts
│   ├── usgs_nwis_ingest.py          # USGS hydrology
│   ├── prism_daymet_ingest.py       # Climate data
│   ├── cdl_ingest.py                # Crop classification
│   ├── smap_ingest.py               # Soil moisture
│   └── metadata_generator.py        # ISO 19115 metadata
├── notebooks/                        # Analysis notebooks
│   └── master_ingestion.ipynb       # Master workflow
├── data/                            
│   ├── boundaries/                  # Reservation boundaries
│   │   └── pine_ridge_boundary.geojson
│   ├── raw/                         # Raw downloads (not in git)
│   └── processed/                   # Standardized datasets
│       ├── hydrology/              
│       ├── climate/                
│       ├── landcover/              
│       └── soil_moisture/          
├── metadata/                        # ISO 19115 metadata files
│   ├── *.xml                       # XML metadata
│   └── *.json                      # JSON metadata
└── .gitattributes                  # Git LFS configuration
