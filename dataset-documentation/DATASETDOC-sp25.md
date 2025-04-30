# DATASETDOC-sp25.md

## Project Information

**What is the project name?**  
ISD: Data Reconciliation and Comparison

**What is the link to your project’s GitHub repository?**  
https://github.com/BU-Spark/ds-isd-reconciliation

**What is the link to your project’s Google Drive folder?**  
https://drive.google.com/drive/folders/17W3eOY5tnY3JO7sHMJ2rUTcnqAVJAVd1

**In your own words, what is this project about? What is the goal of this project?**  
This project aims to improve compliance with Boston's Rental Registration Ordinance by identifying unregistered rental properties. By reconciling the city's rental registry with external datasets (311 complaints, student housing, violations, etc.), we aim to uncover discrepancies, analyze registration patterns, and provide ISD with tools to support more proactive enforcement and outreach.

**Who is the client for the project?**  
Boston Inspectional Services Department (ISD), Housing Division

**Who are the client contacts for the project?**  
- Marcio Fonseca (marcio.fonseca.jr@boston.gov)  
- Gina Belmonte (gina.belmonte@boston.gov)  
- Sebastian Olascoaga (sebastian.olascoaga@boston.gov)

**What class was this project part of?**  
CDS DS 539 - Spark! Practicum

---

## Dataset Information

**What data sets did you use in your project?**  
- Active Rental Registrations (Jan 2025)  
- 311 Service Requests (filtered to ISD_Housing)  
- Student Housing Data (Boston University)  
- Building and Property Violations  
- SAM Address Management  
- Registry of Deeds (Ownership info)

**Please provide a link to any data dictionaries for the datasets in this project.**  
The data dictionary is provided in the project Google Drive folder:  
https://drive.google.com/drive/folders/17W3eOY5tnY3JO7sHMJ2rUTcnqAVJAVd1

**What keywords or tags would you attach to the data set?**  
housing, compliance, Boston, rental registry, violations, property ownership, 311, data reconciliation, civic tech

**Domain(s) of Application:**  
Civic Tech, Housing, Anomaly Detection, Geospatial Analysis

---

## Motivation

**For what purpose was the dataset created?**  
To monitor and enforce rental registration compliance in the City of Boston, and to help ISD proactively identify unregistered rentals based on discrepancies across multiple civic datasets.

---

## Composition

**What do the instances that comprise the dataset represent?**  
Each dataset represents different aspects of rental property activity:  
- 311: Housing complaints (tabular, geospatial)  
- SAM: Official address records (tabular)  
- Rental Registry: Registered rental properties (tabular)  
- Student Housing: University addresses housing students (tabular)  
- Violations: Past enforcement actions (tabular)

**How many instances are there in total?**  
- Rental Registry: ~100,000  
- 311 (filtered): ~25,000  
- Student Housing: ~3,000  
- Violations: ~20,000  
- SAM Addresses: ~190,000

**Is this a sample or complete set?**  
The data is a snapshot, not exhaustive. For example, 311 only includes complaints submitted to the city and may underrepresent issues. The rental registry does not capture unregistered properties. SAM is considered complete for addresses.

**What data does each instance consist of?**  
Structured tabular records: property addresses, owner names, registration statuses, complaint types, dates, etc.

**Is there any information missing from individual instances?**  
Yes. Many records lack standardized addresses or parcel IDs, and owner name data may be outdated or inconsistent.

**Are there recommended data splits?**  
No formal splits, as the goal is not ML model training but analytical comparison and pattern recognition.

**Are there any errors, noise, or redundancies?**  
Yes – inconsistent address formatting, duplicate registrations, and outdated ownership records were common.

**Is the dataset self-contained or linked to external resources?**  
Self-contained within the provided datasets. External sources (e.g., Registry of Deeds) were integrated before analysis.

**Are there any restrictions or archival versions?**  
No known restrictions; data is from public or city-provided sources.

**Confidential or sensitive data?**  
No confidential individual data. Some ownership details could indirectly identify individuals.

**Offensive or harmful content?**  
No.

**Is it possible to identify individuals?**  
Property owner names may be personally identifying when combined with addresses.

---

## Dataset Snapshot

| Dataset                | Size    | # Instances | # Fields | Labeled Classes | # Labels |
|------------------------|---------|-------------|----------|------------------|----------|
| Rental Registry        | ~12 MB  | ~100,000     | 10–15     | Yes              | Registered / Not |
| 311 Housing Complaints | ~6 MB   | ~25,000      | 8–12      | Yes              | Complaint types |
| Student Housing (BU)   | ~1 MB   | ~3,000       | 5–8       | No               | N/A |
| Violations             | ~5 MB   | ~20,000      | 8–10      | Yes              | Violation type |
| SAM Addresses          | ~20 MB  | ~190,000     | 5–7       | No               | N/A |

---

## Collection Process

**What mechanisms were used to collect the data?**  
- City datasets downloaded from internal ISD systems and Boston’s open data portal  
- Student data provided by Boston University  
- SAM address data provided by the City  
- Registry of Deeds manually merged in via owner name/address

**Sampling strategy?**  
No formal sampling. Data reflects full available records from ISD and BU for the Spring 2025 semester.

**Timeframe?**  
Data was collected between Jan–Apr 2025. Historical data ranges from 2016–2025 depending on the dataset.

---

## Preprocessing / Cleaning / Labeling

**Was any preprocessing done?**  
Yes:
- Address standardization and fuzzy matching using string similarity and regex  
- Removal of duplicates and entries with missing critical fields  
- Adding columns for match confidence, property type, and flags for likely unregistered properties

**Transformations?**  
Yes. Cleaning nulls, merging datasets on address fields, geocoding addresses, and tagging known student housing.

**Was raw data saved?**  
Yes, stored in the project’s Google Drive folder.

**Is the preprocessing code available?**  
Yes: [GitHub link to data cleaning scripts](https://github.com/BU-Spark/ds-isd-reconciliation/tree/main/notebooks)

---

## Uses

**What tasks has the dataset been used for so far?**  
- Identifying unregistered rental properties  
- Visualizing non-compliance hotspots  
- Analyzing patterns by geography, owner type, and complaint frequency

**What other tasks could the dataset be used for?**  
- Predicting risk of violations  
- Designing targeted outreach campaigns  
- Studying urban rental dynamics over time

**Limitations for future use?**  
Address inconsistencies may limit merge accuracy; owner info may be outdated.

**Any tasks the dataset should not be used for?**  
Should not be used to enforce penalties without verification; results require human validation.

---

## Distribution

**What access type should this dataset be given?**  
Internal (Restricted) – for ISD and Spark-affiliated teams

---

## Maintenance

**Can others contribute to the dataset?**  
Yes – future Spark! teams can build on this work using our GitHub repo and documentation.

---

## Other

**Additional notes**  
This project offers a scalable model for civic data reconciliation. Future work could incorporate AI-based address standardization or integrate tax assessor data for even better accuracy.
