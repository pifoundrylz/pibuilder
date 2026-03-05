# System Architecture v0.001

```mermaid
flowchart TB

%% USER
U[Engineer / User]

%% FRONTEND
U --> UI[Web Map UI]

%% API
UI --> API[PI Builder API]

%% DOMAIN MODULES
API --> GIS[GIS Module]
API --> RAIN[Rainfall Module]
API --> HYDRO[Hydrology Module]
API --> HYDRAULIC[Hydraulics Module]
API --> REPORT[Report Module]

%% JOB WORKERS
GIS --> WORKER[Compute Workers]
RAIN --> WORKER
HYDRO --> WORKER
HYDRAULIC --> WORKER

%% DATA
DEM[(DEM Data)]
RAIN_DATA[(Rainfall Data)]
SOIL[(Soil / IRC Tables)]
DB[(PostGIS Database)]

DEM --> GIS
RAIN_DATA --> RAIN
SOIL --> HYDRO

WORKER --> DB
REPORT --> DB
REPORT --> UI
```



## Core Components

- UI
- API Layer
- GIS Engine
- Rainfall Engine
- Runoff Engine
- Hydrology Engine
- Hydraulic Engine
- Report Generator

## Processing Pipeline

User location → watershed extraction → rainfall analysis → runoff → discharge → HFL → report
