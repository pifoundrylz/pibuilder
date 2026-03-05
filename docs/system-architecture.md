# System Architecture

PI Builder uses a **modular backend architecture** optimized for heavy geospatial computation.

## Architecture Diagram

```mermaid
flowchart TB

Engineer --> UI[Web Map Interface]

UI --> API[PI Builder API]

API --> GIS[GIS Engine]
API --> RAIN[Rainfall Engine]
API --> HYDRO[Hydrology Engine]
API --> HYDRAULIC[Hydraulics Engine]

GIS --> HYDRO
RAIN --> HYDRO
HYDRO --> HYDRAULIC

HYDRAULIC --> REPORT[Report Generator]
REPORT --> UI

DEM[(DEM Data)] --> GIS
RAIN_DATA[(Rainfall Data)] --> RAIN
SOIL[(Soil / IRC Tables)] --> HYDRO
DB[(PostGIS Database)]

GIS --> DB
RAIN --> DB
HYDRO --> DB
HYDRAULIC --> DB
```

## Layers

1. User Interface (map + project interface)
2. API Layer (FastAPI)
3. Domain Engines (GIS, Rainfall, Hydrology, Hydraulics)
4. Compute Workers (heavy jobs)
5. Data Layer (PostGIS + raster datasets)