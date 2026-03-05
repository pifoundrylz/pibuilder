# System Architecture v0.001

```mermaid
flowchart TB

%% USER
U[Engineer / User]

%% FRONTEND
U --> UI[Web Map Interface]

%% BACKEND
UI --> API[FastAPI Backend]

%% COMPUTE MODULES
API --> GIS[GIS Engine]
API --> RAIN[Rainfall Engine]
API --> HYDRO[Hydrology Engine]
API --> HYDRAULIC[Hydraulics Engine]

%% ENGINE FLOW
GIS --> HYDRO
RAIN --> HYDRO
HYDRO --> HYDRAULIC

%% OUTPUT
HYDRAULIC --> REPORT[Report Generator]
REPORT --> UI

%% DATA
DEM[(DEM Terrain Data)]
RAIN_DATA[(Rainfall Data)]
SOIL[(Soil / IRC Tables)]
DB[(Spatial Database)]

DEM --> GIS
RAIN_DATA --> RAIN
SOIL --> HYDRO

GIS --> DB
RAIN --> DB
HYDRO --> DB
HYDRAULIC --> DB
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
