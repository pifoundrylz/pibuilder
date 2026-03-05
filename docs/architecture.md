# System Architecture v0.001

```mermaid
flowchart LR

%% User Layer
A[User / Engineer] --> B[Web Map Interface]

%% API Layer
B --> C[PI Builder API]

%% Core Engines
C --> D[GIS Engine]
C --> E[Rainfall Engine]
C --> F[Hydrology Engine]
C --> G[Hydraulics Engine]

%% GIS Processing
D --> H[Watershed Extraction]
H --> I[Catchment Metrics]

%% Rainfall Processing
E --> J[Rainfall Data Cleaning]
J --> K[Rainfall Frequency Analysis]

%% Hydrology
I --> F
K --> F
F --> L[Runoff & Flood Discharge]

%% Hydraulics
L --> G
G --> M[High Flood Level Estimation]

%% Output
M --> N[Hydrology Report Generator]
N --> B

%% Data Sources
O[DEM Terrain Data] --> D
P[IMD Rainfall Data] --> E
Q[Rain Gauge Stations] --> E
R[Soil Maps / IRC Tables] --> F

%% Storage
S[(Spatial Database)]
D --> S
E --> S
F --> S
G --> S
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
