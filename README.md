# Pre-requisites
- VS2019 community
- SQLServer Management Studio developer edition

# Business Request
The business has customer purchase data in local currency, but needs that data converted and needs the Customer contact information with it.
The purchase data is in SQL Server, the currency conversion data is in Excel, and the customer contact information is in a csv file.
You task is to bring this data together in a new SQL Server database for the business.
# 1. ETL Process Overview
The ETL process in SSIS consists of three main stages:
```mermaid
graph TB
    subgraph1[Data Sources] --> B[Extract]
    B -->C[Transform]
    subgraph subgraph1["Data Sources"]
        direction TB
        E[SQL Server]
        F[Excel]
        G[Flat Files]
    end
    C -->|Data Conversion| H[Load]
    C -->|Lookup| H
    H --> D[Data Warehouse]
```

- **Extract**: Retrieve data from various sources like SQL Server, Excel, and flat files.
- **Transform**: Apply transformations such as data conversions and lookups.
- **Load**: Store the transformed data into a data warehouse.
  
# Pipline
<img width="893" height="466" alt="image" src="https://github.com/user-attachments/assets/fcfb6033-bf57-4411-9050-783d5fd2bf56" />

# Data flow & Transformation 
<img width="817" height="451" alt="image" src="https://github.com/user-attachments/assets/ac668757-b858-4c49-a386-2d3a19cdcd9b" />

# 1. ETL Process Overview
The ETL process in SSIS consists of three main stages:
```mermaid
graph TB
    subgraph1[Data Sources] --> B[Extract]
    B -->C[Transform]
    subgraph subgraph1["Data Sources"]
        direction TB
        E[SQL Server]
        F[Excel]
        G[Flat Files]
    end
    C -->|Data Conversion| H[Load]
    C -->|Lookup| H
    H --> D[Data Warehouse]
```

- **Extract**: Retrieve data from various sources like SQL Server, Excel, and flat files.
- **Transform**: Apply transformations such as data conversions and lookups.
- **Load**: Store the transformed data into a data warehouse.
# Deployment

# API Call for Currency Conversion
<img width="1918" height="507" alt="image" src="https://github.com/user-attachments/assets/6f97ab81-a62b-4d84-8f8d-18677cd48960" />

![WhatsApp Image 2026-01-30 at 1 01 46 AM](https://github.com/user-attachments/assets/c91f7fb5-cef9-40ee-8c7f-0f7cd11beaf6)
