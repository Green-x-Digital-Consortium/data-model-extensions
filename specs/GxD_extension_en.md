## Green x Digital Consortium Extension for Technical Specifications for Data Exchange

### Updated March 27, 2025

---

## 1. Introduction

The purpose of this data model extension is to enable the exchange of Product Carbon Footprints (PCFs) that conform to the [CO2 Visualization Framework](https://www.gxdc.jp/pdf/CO2_VisualizationFrameworkEdition_2.0.1.pdf) (Product-based calculation, Organization-based calculation) in a manner that is interoperable between compliant host systems.

To achieve decarbonization across the entire supply chain, accurate assessment and reduction efforts are essential not only for in-house emissions (Scope 1 and 2) but also for supply chain CO2 emissions, including emissions from upstream and downstream in the supply chain (Scope 3). While the use of primary data provided by suppliers is important in calculating Scope 3 emissions, there are two challenges:

The first is the low participation rate due to the high operational burden of product-based calculations. Because product-specific data collection is required, it is a high hurdle for many companies. In response, the Green x Digital Consortium permits organization-level calculations with a lower operational burden and promotes participation in CFP calculation by requiring assurance of reliability through certificates.

The second is the difficulty of CO2 reduction efforts across the entire supply chain due to the unclear CO2 reduction potential when using products from companies with which there are no transactions. In response, the Green x Digital Consortium permits the additional use of Gate-to-Gate data provision based on the Cradle-to-Gate method, enabling the assessment of CO2 emissions throughout the product lifecycle and hotspot analysis. This enables the planning and implementation of effective CO2 reduction measures.

By utilizing this data model extension, efforts toward visualizing and reducing CO2 emissions across the entire supply chain can be strengthened.  Please refer to the following chapters for detailed specifications.


## 2. Terminology

For a complete list of terms, please refer to the [Terminology](https://wbcsd.github.io/data-exchange-protocol/v2/#terminology) section of the PACT Technical Specifications.

### Product-based calculation

A calculation method that uses Life Cycle Assessment (LCA) or Product Carbon Footprint methodology on a per-product basis.

### Organization-based calculation

A calculation method that extracts organizational emission data such as Scope 1, 2, and 3 for a specific delivery destination by allocation.


## 3. Conformance

For conformance with the PACT Network, please refer to the [Conformance](https://wbcsd.github.io/data-exchange-protocol/v2/#conformance) section of the PACT Technical Specifications.


## 4. Data Model Extension

This section defines the [data model extension](https://docs.carbon-transparency.org/v2/#dt-datamodelextension) for Product Carbon Footprints that conforms to the [PACT Network](https://docs.carbon-transparency.org/v2/#pathfinder-network).  This data model extension includes additional information in addition to the content defined in the [PACT data model](https://docs.carbon-transparency.org/v2/#data-model).


### 4.1 Data Type: Calculation Method (`calcMethod`)

| Property | Type | Requirement Level | Description |
|---|---|---|---|
| `calcMethod` | String | M | Calculation method. 0: Product-based calculation, 1: Organization-based calculation |

### 4.2 Data Type: CO2 Visualization Framework Edition (`FWedition`)

| Property | Type | Requirement Level | Description |
|---|---|---|---|
| `FWedition` | String | M | The version of the CO2 Visualization Framework referenced.  "2.0" if referencing CO2 Visualization Framework Edition 2.0. |


### 4.3 Data Type: Organization-based calculation (`organization`)

| Property | Type | Requirement Level | Description |
|---|---|---|---|
| `scope3Category` | Array<Number> | O | Calculation target categories (for organization-based calculations) |
| `scope1DistributionLevel` | String | M | Distribution level Scope 1 (for organization-based calculations) |
| `scope2DistributionLevel` | String | M | Distribution level Scope 2 (for organization-based calculations) |
| `scope3DistributionLevel` | String | M | Distribution level Scope 3 (for organization-based calculations) |
| `scope1DistributionIndex` | String | O | Distribution index Scope 1 (for organization-based calculations) |
| `scope2DistributionIndex` | String | O | Distribution index Scope 2 (for organization-based calculations) |
| `scope3DistributionIndex` | String | O | Distribution index Scope 3 (for organization-based calculations) |
| `distributionLevelComment` | String | O | Distribution level comment |
| `distributionIndexComment` | String | O | Distribution index comment |



### 4.4 Data Type: Certificate Information (`certificate`)

| Property | Type | Requirement Level | Description |
|---|---|---|---|
| `certificateAmount` | String | O | Certificate amount (including J-Credits derived from renewable energy) |
| `certificateType` | String | O | Certificate type (including J-Credits derived from renewable energy) |


### 4.5 Data Type: Gate-to-Gate Emissions (`gateToGate`)

| Property | Type | Requirement Level | Description |
|---|---|---|---|
| `gateToGateFossilGhgEmissions` | String | O | Gate-to-Gate emissions (excluding biogenic emissions and removals) |
| `gateToGateBiogenicCarbonContent` | String | O | Gate-to-Gate emissions (including biogenic emissions and removals) |
| `unitaryProductAmountComment` | String | O | Product Amount Comment. Explanation of "Product Amount" and "Declared Unit" |



## 5. Remarks

This document defines the data model extension based on the Green x Digital Consortium's [Technical Specifications for Data Exchange Version 2.0](https://www.gxdc.jp/pdf/technical_spec_2.0en.pdf). Please refer to the link above for details.

## 6. Contact

Green x Digital
green_digital@jeita.or.jp

