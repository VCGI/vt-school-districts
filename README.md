# **School Districts and Supervisory Unions Annual Update**

Updated June 30, 2026

* [Contact](#bookmark=id.1md2w5rcxxk6)  
* [Timing and Lifecycle](#bookmark=id.quya2fcqdq3d)  
* [Town Boundary Synchronization](#bookmark=id.jusv9af9swi)  
* [Population Density Methodology](#bookmark=id.qd058vn7jyhg)  
* [FY2027 Update](#bookmark=id.81f3sgb9452t)  
* [FY2026 Update](#bookmark=id.wghoylfg7vk2)  
* [FY2025 Update](#bookmark=id.f6h8memmk9l8)

## **Contact**

Inquiries regarding the administrative source data, structural changes, or naming conventions are managed by the program leadership and data teams at the Vermont Agency of Education (AOE).

## **Timing and Lifecycle**

The geospatial layers for [school districts](https://geodata.vermont.gov/datasets/03147644b3db427e8117d9f7bf895a0b_56/explore) and [supervisory unions](https://geodata.vermont.gov/datasets/08c21e8c8c094771b8308ddd7bb1db1e_55/explore) are maintained on an annual cycle to align with the start of each state fiscal year on July 1 (e.g., the FY2027 data layer is finalized for publication by July 1, 2026).

Boundary and naming changes are coordinated with the AOE during late May and early June. The revised layers are processed, QA/QC-checked, and published to the Vermont Open Geodata Portal at the turn of the fiscal year.

## **Town Boundary Synchronization**

Because many school district (SD) and supervisory union (SU) boundaries are legally coincident with municipal boundaries, these layers are synchronized with the primary Vermont Town Boundaries dataset (BNDHASH).

During each annual update, corrections and modifications documented in the [BNDHASH All Lines changelog](https://www.arcgis.com/sharing/rest/content/items/ef665468eb254244b761f2f0cd13657f/info/metadata/metadata.xml?format=default&output=html) are cross-referenced. If a modified municipal border serves as an SD or SU boundary, the spatial adjustments are integrated. This synchronization runs parallel to organizational transitions (such as mergers, consolidations, or dissolutions) authorized by the AOE.

## **Population Density Methodology**

To satisfy legislative requirements defined in [16 V.S.A. § 4010](https://legislature.vermont.gov/statutes/section/16/133/04010), population density estimates within the school district layer are recalculated annually. These calculations rely on the most recent subcounty population estimates (Minor Civil Divisions, "POP-50" datasets) published by the U.S. Census Bureau.

**Note on Census Revisions:** The U.S. Census Bureau retroactively revises historical population estimates back to the most recent decennial census with each annual July 1 release. Consequently, population figures and derived densities from historical datasets may exhibit minor variances when compared to subsequent releases.

### **Spatial Anomalies and Sub-Town Geographies**

While most school districts align perfectly with one or more municipal boundaries, two persistent exceptions exist:

1. **North Bennington ID & Southwest Vermont UESD:** North Bennington ID encompasses a specific sub-geographic portion of both Shaftsbury and Bennington. Southwest Vermont UESD comprises the full municipalities of Pownal, Woodford, Bennington, and Shaftsbury, **excluding** the North Bennington ID jurisdictions. Conversely, Mt. Anthony UHSD covers the entirety of Southwest Vermont UESD but *includes* the North Bennington ID territory and population.  

![alt text](/assets/NorthBenningtonID.png)

2. **Blue Mountain USD & Oxbow UUSD:** Blue Mountain USD covers the entire municipalities of Ryegate and Groton, alongside a northeast portion of Newbury (Wells River). Oxbow UUSD comprises Bradford and Newbury, **excluding** the Wells River portion.

![alt text](/assets/RyegateNewbury.png)

### **Computational Steps**

The population density for each school district is derived using the following systematic workflow:

1. **Land Area (ALAND) Acquisition:** Land area values are extracted from Census Bureau county subdivision boundaries and the established [Sub-Town Geography reference data](https://github.com/VCGI/vt-school-districts/blob/main/data/SubTownGeography.csv).  
2. **Population Apportionment:** For standard districts, total municipal population estimates are applied directly. For split-town (sub-town) jurisdictions, population figures are apportioned using a static ratio based on the population distribution recorded during the 2020 Decennial Census. This approach assumes internal population distribution ratios remain relatively stable between decennial counts.  
3. **Aggregation:** Both ALAND and the apportioned population estimates are aggregated up to the unique school district level.  
4. **Density Calculation:** The final density value (expressed as persons per square mile) is calculated using the following formula:

Density \= Population / (ALAND / 2,589,988)

*(The constant 2,589,988 serves as the conversion factor from square meters to square miles.)* Detailed technical specifications can be found on page 100 of the [2020 Census Demographic and Housing Characteristics (DHC) Technical Documentation](https://www2.census.gov/programs-surveys/decennial/2020/technical-documentation/complete-tech-docs/demographic-and-housing-characteristics-file-and-demographic-profile/2020census-demographic-and-housing-characteristics-file-and-demographic-profile-techdoc.pdf).

## **FY2027 Update**

* **School District Layer:**  
  * No administrative or spatial changes required.  
* **Supervisory Union Layer:**  
  * No administrative or spatial changes required.  
* **Municipal Boundary Synchronization:**  
  * No changes along town boundaries that interact with SD/SU borders.  
* **Density Recalculations:**  
  * Density values updated using the 2025 Census Bureau population estimates.

## **FY2026 Update**

* **School District Layer:**  
  * **Interim Adjustment (March 4, 2026):** Following authorization from the AOE, the single district *West River Modified Union Education District (U072A/B)* was partitioned into two distinct administrative districts:  
    * **U072A (West River Modified UED):** Comprising Jamaica, Townshend, Brookline, and Newfane (governing elementary education).  
    * **U072B (West River Union ED):** Comprising Jamaica, Townshend, Brookline, Newfane, and Windham.  
    * *Context:* While the districts originally merged in FY2020, Windham only joined the secondary education portion of the district. Windham closed its local elementary school in FY2024 and began tuitioning students to Townshend Elementary, but did not formally join U072A. Consequently, the population density for U072A was recalculated to exclude Windham's land area and population.  
* **Supervisory Union Layer:**  
  * Based on structural confirmation from the Vermont Superintendents Association and the AOE, 19 entities were updated in the database attribute field SUSD from "SU" (Supervisory Union) to "SD" (Supervisory District):  
    * Addison Central (SD03)  
    * Addison Northwest (SD02)  
    * Barre (SD61)  
    * Champlain Valley (SD14)  
    * Essex Westford (SD65)  
    * Harwood (SD42)  
    * Kingdom East (SD67)  
    * Lincoln (SD70)  
    * Maple Run (SD23)  
    * Mill River (SD33)  
    * Missisquoi Valley (SD21)  
    * Montpelier Roxbury (SD69)  
    * Mount Abraham (SD01)  
    * Mount Mansfield (SD12)  
    * Orange Southwest (SD28)  
    * Rivendell Interstate (SD64)  
    * Slate Valley (SD04)  
    * Washington Central (SD32)  
* **Municipal Boundary Synchronization:**  
  * No coincident town boundary modifications occurred.  
* **Density Recalculations:**  
  * Density values updated using the 2024 Census Bureau population estimates.

## **FY2025 Update**

* **School District Layer:**  
  * Renamed *Orleans Southwest UESD* to *Mountain View UESD*.  
  * Reassigned Ferdinand's supervisory union association to *Essex North* (SU019).  
  * Reassigned Fletcher's supervisory union association to *Franklin West* (SU022).  
  * Populated the missing SUNAME attribute for Winhall (T248) with *Bennington Rutland SU*.  
* **Supervisory Union Layer:**  
  * No administrative or spatial changes required.  
* **Municipal Boundary Synchronization:**  
  * No coincident town boundary modifications occurred.  
* **Density Recalculations:**  
  * Density values updated using the 2023 Census Bureau population estimates.