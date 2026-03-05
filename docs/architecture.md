# System Architecture v0.1

```mermaid
flowchart TB

%% USER LAYER
U[Engineer / User] --> UI[Web Map Interface]

%% API LAYER
UI --> API[PI Builder API]

%% ENGINE LAYER
API --> GIS[GIS Engine]
API --> RAIN[Rainfall Engine]
API --> HYDRO[Hydrology Engine]
API --> HYDRAULIC[Hydraulics Engine]
API --> REPORT[Report Generator]

%% DATA FLOW BETWEEN ENGINES
GIS --> HYDRO
RAIN --> HYDRO
HYDRO --> HYDRAULIC
HYDRAULIC --> REPORT

%% DATA LAYER
DEM[(DEM Terrain Data)]
RAIN_DATA[(IMD Rainfall Data)]
GAUGE[(Rain Gauge Stations)]
SOIL[(Soil Maps / IRC Tables)]
DB[(Spatial Database)]

DEM --> GIS
RAIN_DATA --> RAIN
GAUGE --> RAIN
SOIL --> HYDRO

GIS --> DB
RAIN --> DB
HYDRO --> DB
HYDRAULIC --> DB

REPORT --> UI
```




## Core Components

- Web Application
- API Layer
- GIS Engine
- Rainfall Engine
- Runoff Engine
- Hydrology Engine
- Hydraulic Engine
- Report Generator

## Processing Pipeline

User location → watershed extraction → rainfall analysis → runoff → discharge → HFL → report
