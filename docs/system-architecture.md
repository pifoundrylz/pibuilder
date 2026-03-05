# PI Builder — System Architecture

PI Builder is a **geospatial computation platform** designed to automate hydrology analysis for infrastructure design workflows such as bridges, culverts, and drainage structures.

The system separates responsibilities into modular layers so that heavy geospatial computations can scale while development remains fast during the MVP stage.

---

# Architecture Overview

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
