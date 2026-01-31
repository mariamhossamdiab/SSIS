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
  
# 2. SSIS Package Workflow
An SSIS package is divided into **Control Flow** and **Data Flow** components:
```mermaid
flowchart TB
    subgraph subgraph1["Data Flow"]
        direction TB
        D[Source] --> E[Transformations]
        E --> F[Destination]
    end
    subgraph subGraph0["Control Flow"]
        B1[Execute SQL Task]        
        B3[Script Task]
        B4[File System Task]
        B2["Data Flow"]
    end
```

- **SSIS Package**: The overall container that includes all components.
- **Control Flow**: Manages the sequence of tasks (e.g., Execute SQL Task, Data Flow Task, Script Task, File System Task).
- **Data Flow**: A subsection of the Control Flow that manages the flow of data from sources to destinations, using transformations such as data conversions and lookups.
  
# 3. Control Flow vs. Data Flow
Control Flow and Data Flow are distinct components in SSIS. Below is a visual representation showing examples of each:

```mermaid
graph TB
    subgraph Control Flow
        A[Data Flow]
        B[Execute SQL Task]
        C[Script Task]
    end
    subgraph Data Flow
        D[Data Transformation]
        E[Lookup]
        F[Aggregation]
    end
```
# 4. Connections in SSIS

SSIS uses various connection types to integrate with different data sources:

- **OLE DB Connection**: For SQL Server databases.
- **Excel Connection**: To read from or write to Excel files.
- **Flat File Connection**: To handle CSV or text files.

Connections are used within the Data Flow to connect **Sources** and **Destinations**.

## 5. Error Handling in SSIS

Error handling is critical in SSIS to maintain data quality. The diagram below shows how to handle errors in a Data Flow Task:

```mermaid
flowchart TB
    A[Data Flow Task] --> B{Error Output?}
    B -->|Yes| C[Redirect to Error Output]
    C --> D[Flat File Destination]
    B -->|No| E[Continue Processing]
```

- **Error Output**: Errors are redirected to an output path for further review.
- **Flat File Destination**: Failed rows are saved for analysis.
    
# Pipline
<img width="893" height="466" alt="image" src="https://github.com/user-attachments/assets/fcfb6033-bf57-4411-9050-783d5fd2bf56" />

# Data flow & Transformation 
<img width="817" height="451" alt="image" src="https://github.com/user-attachments/assets/ac668757-b858-4c49-a386-2d3a19cdcd9b" />

# Deployment

# API Call for Currency Conversion
<img width="1918" height="507" alt="image" src="https://github.com/user-attachments/assets/6f97ab81-a62b-4d84-8f8d-18677cd48960" />

![WhatsApp Image 2026-01-30 at 1 01 46 AM](https://github.com/user-attachments/assets/c91f7fb5-cef9-40ee-8c7f-0f7cd11beaf6)
