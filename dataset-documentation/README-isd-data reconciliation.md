# ISD Data Reconciliation and Compliance

This repository contains a data analysis pipeline for the Boston Inspectional Services Department (ISD) focused on improving rental registration compliance. The project integrates and reconciles multiple civic datasets to identify likely unregistered rental properties, uncover data quality issues, and develop tools to support more proactive inspections and outreach.

There are currently three major components of this project:

1. Identifying likely unregistered rental properties through cross-dataset comparison
2. Analyzing registration and ownership patterns using demographic and geographic factors
3. Building visualizations and reporting tools for actionable insights and future use

## Getting Started

The `notebooks/` folder contains Jupyter Notebooks demonstrating how to run data cleaning, address standardization, and reconciliation logic. Each major task is organized in a separate notebook:

- `address_standardization.ipynb` – cleans and normalizes address fields
- `registration_analysis.ipynb` – explores patterns in registration by ward, owner, manager, etc.
- `unregistered_properties.ipynb` – matches across datasets to infer likely unregistered rentals

You can find relevant datasets in the `data/` directory or linked from the [project Google Drive](https://drive.google.com/drive/folders/17W3eOY5tnY3JO7sHMJ2rUTcnqAVJAVd1?usp=sharing). Final visualizations are available in `visuals/`.

---

## Overview

Boston’s Rental Registration Ordinance requires all rental units to be registered with ISD. However, many rental properties remain unregistered due to tenant turnover, lack of awareness, or clerical oversight. This gap prevents ISD from fully enforcing housing quality standards and limits proactive inspections.

This project helps bridge that gap. By integrating registration data with complaints, student housing, address registries, and violation records, we can identify high-probability unregistered rentals, analyze compliance trends, and recommend strategies for enforcement and outreach.

Ultimately, this work supports the city’s goal of ensuring clean, safe, and legal housing for all residents.

---

## Project Description

The ISD Data Reconciliation and Compliance project has three main goals:

1. **Data Reconciliation and Flagging**  
   Clean and merge datasets (SAM, 311, student housing, violations, rental registry) to create a unified view of housing activity and flag properties likely acting as unregistered rentals.

2. **Pattern Analysis and Visualization**  
   Explore compliance patterns by neighborhood, ownership structure, property type, and complaint frequency. Generate dashboards and maps to support targeted enforcement.

3. **Documentation and Future-Proofing**  
   Deliver reproducible, well-documented code and cleaned datasets. Provide detailed notes and a roadmap so future Spark! teams can build on this work.

---

## Project Checklist

1. Clean and standardize all addresses using the SAM reference dataset
2. Identify duplicate or stale registrations
3. Match rental registry with external datasets (311, student housing, violations, ownership)
4. Flag likely unregistered rentals using logic rules
5. Visualize patterns in registration by ward, property size, owner type, etc.
6. Create draft outreach list and recommendations for ISD
7. Document all cleaning steps and blockers for future teams

---

## Proposed Solution

1. **Reconciliation Logic:**  
   Standardize addresses using SAM data and fuzzy matching. Cross-reference registry with 311 complaints, student housing, and violation records. Flag properties present in external datasets but missing from the registry as likely unregistered.

2. **Pattern Detection:**  
   Analyze where compliance is low using statistical summaries and geographic heatmaps. Identify trends in under-registration based on property size, management structure, or ward-level demographics.

3. **Scalability and Documentation:**  
   Create a well-documented, reproducible workflow with reusable code for address cleaning, matching logic, and report generation. Support continuous improvement across semesters.

---

## Other Folders

### `./notebooks`  
Contains Jupyter notebooks used for analysis, cleaning, and visualization.  
Includes EDA, registration overlap analysis, and property-level comparison.

### `./data`  
Raw and cleaned datasets, including:
- Rental Registry (Jan 2025)
- SAM Address Management
- 311 ISD Complaints
- Student Housing Addresses
- Building Violations

### `./scripts`  
Standalone Python scripts for fuzzy matching, owner standardization, and preprocessing logic.

### `./visuals`  
Contains exported graphs, maps, and dashboards used in reporting and client deliverables.

---

## Resources

### Datasets  
- [Active Rental Registry](https://drive.google.com/...)  
- [SAM Standardized Address Management](https://drive.google.com/...)  
- [311 Housing Complaints](https://data.boston.gov/dataset/311-service-requests)  
- [Student Housing Addresses – BU](https://drive.google.com/...)  
- [Violations Data](https://drive.google.com/...)

### Client and Course Links  
- [ISD Project Drive Folder](https://drive.google.com/drive/folders/17W3eOY5tnY3JO7sHMJ2rUTcnqAVJAVd1)  
- [Spark! GitHub Organization](https://github.com/BU-Spark)  
- [City of Boston Rental Registry Ordinance](https://www.boston.gov/departments/inspectional-services/rental-property-registration)

---

## References

1. City of Boston Rental Registration Analysis (2024)
2. Spark! Project Guidelines and Dataset Standards
3. U.S. Census data on rental housing (for geographic validation)
4. Python libraries: `pandas`, `fuzzywuzzy`, `geopandas`, `matplotlib`, `seaborn`

---

## Contributors

- Dhruv Gandhi (dhruvg@bu.edu)  
- Benson Yu (benson@bu.edu)  
- David Ueda (davidu@bu.edu)  
- Louie Belile (lbelile@bu.edu)

Project Advisors:
- Abby Gualda (Spark! Fellow)  
- Lina Dellanno (Project Manager)  
- Caslow Chien (TPM)  
- Marcio Fonseca, Gina Belmonte, Sebastian Olascoaga (ISD)

---

## License  
This project is for academic use only. Data used in this project is subject to the terms of access as granted by the City of Boston and Boston University.
