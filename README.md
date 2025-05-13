# Analyzing FEMA's National Flood Insurance Program (NFIP) Data With DuckDB
Author: Mark Bauer

### Table of Contents
* [1. Introduction](#1-Introduction)  
* [2. Notebooks](#2-Notebooks)  
* [3. Data](#3-Data)  
* [4. Additional Resources](#4-Additional-Resources) 
    * [FEMA](#FEMA) 
    * [Academic Research](#Academic-Research) 
    * [NFIP Redacted Claims & Policies Analysis](#NFIP-Redacted-Claims--Policies-Analysis) 
    * [Community Open Data](#Community-Open-Data)
    * [Other](#Other)
* [5. Say Hello!](#5-Say-Hello)  

Note: This analysis uses the Federal Emergency Management Agency’s OpenFEMA API, but is not endorsed by FEMA. The Federal Government or FEMA cannot vouch for the data or analyses derived from these data after the data have been retrieved from the Agency's website(s).

Read more about OpenFEMA's [Terms and Conditions](https://www.fema.gov/about/openfema/terms-conditions).

Data as of 05-04-2025.

-- 

Table xx. Number and Amount Paid on NFIP Claims (both in millions). Total amount paid, in this analysis, is defined as the total amount paid for all Building, Contents, and Increased Cost of Compliance (ICC) claims.
|   countClaimM |   paidTotalClaimM |   paidBuildingM |   paidContentsM |   paidICCM |
|--------------:|------------------:|----------------:|----------------:|-----------:|
|          2.71 |          87775.00 |        71337.63 |        15486.14 |     951.23 |




![year-count](figures/year-count.png)
Figure xx. Number of NFIP Claims by Year from 1978 to 2024.

![year-amount-paid](figures/year-amount-paid.png)
Figure xx. Total Amount Paid on NFIP Claims by Year from 1978 to 2024 (Adjusted in 2024 Dollars).


Table xx. Top 10 Most Costly Flood Events By Total Amount Paid on NFIP Claims ($ millions). Table is ranked on Total Amount Paid in 2025 dollars (i.e. paidTotalClaimM2025). The column paidTotalClaimM is the amount paid ($ millions) when occurred.
|   rank |   yearOfLoss | floodEvent               |   countClaims |   paidTotalClaimM |   paidTotalClaimM2025 |   averagePaidClaim2025 |
|-------:|-------------:|:-------------------------|--------------:|------------------:|----------------------:|-----------------------:|
|      1 |         2005 | Hurricane Katrina        |        208348 |             16261 |                 27088 |                 130017 |
|      2 |         2012 | Hurricane Sandy          |        144848 |              8957 |                 12553 |                  86668 |
|      3 |         2017 | Hurricane Harvey         |         92397 |              9055 |                 11846 |                 128210 |
|      4 |         2024 | Hurricane Helene         |         57738 |              5802 |                  5976 |                 103509 |
|      5 |         2022 | Hurricane Ian            |         48755 |              4830 |                  5457 |                 111945 |
|      6 |         2008 | Hurricane Ike            |         58126 |              2702 |                  4067 |                  69972 |
|      7 |         2016 | Mid-summer severe storms |         30018 |              2533 |                  3397 |                 113169 |
|      8 |         2004 | Hurricane Ivan           |         20137 |              1325 |                  2273 |                 112900 |
|      9 |         2001 | Tropical Storm Allison   |         35561 |              1104 |                  2004 |                  56373 |
|     10 |         2011 | Hurricane Irene          |         52493 |              1347 |                  1943 |                  37026 |



![figures/count-claims-map](figures/count-claims-map.png)
Figure xx. Number of NFIP Claims by State.

![figures/count-claims-norm-map](figures/count-claims-norm-map.png)
Figure xx. Number of NFIP Claims Normalized by State Area.

# 1. Introduction
The [National Flood Insurance Program](https://www.fema.gov/flood-insurance) (NFIP) is managed by [FEMA](https://www.fema.gov/) and provides flood insurance to mitigate the socio-economic impacts of floods. In 2019, FEMA [released](https://www.fema.gov/press-release/20230425/fema-publishes-nfip-claims-and-policy-data) two datasets on [OpenFEMA](https://www.fema.gov/about/reports-and-data/openfema) related to the NFIP to promote transparency, reduce complexity for public data requests, and to improve how the agency’s stakeholders interact with and understand the NFIP:
1) [NFIP Redacted Policies](https://www.fema.gov/openfema-data-page/fima-nfip-redacted-policies-v2)
2) [NFIP Redacted Claims](https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2)

With over 69 million policies and 2.7 million claims transactions as of May 04, 2025, this is one of the largest openly available insurance datasets in the United States and possibly the world. This project examines the NFIP Redacted Claims dataset, but more importantly, demonstrates how to query and manipulate the data with ease.

Due to its large file size, accessing the dataset can be a challenge, even for experienced analysts. To address this, I designed a tutorial demonstrating how to analyze the dataset with my local laptop. To achieve this, I utilized [DuckDB](https://duckdb.org/), a lightweight, high-performance SQL OLAP database management system. DuckDB offers a smooth experience, is blazing-fast, includes a robust Python API, and is open-source. I used SQL via the [Python Client API](https://duckdb.org/docs/api/python/overview.html) for data analysis and used [GeoPandas](https://geopandas.org/en/stable/) for mapping.

The ultimate goal of this project is to promote the dataset for academic research and to assist communities in analyzing and downloading the data. This dataset is one of my favorites, and I hope you find these tutorials helpful in advancing the study and analysis of the NFIP.

To learn more about the NFIP:
- [NFIP Website](https://www.fema.gov/flood-insurance)
- For more information about what’s covered and to find a policy, visit [FloodSmart](https://www.floodsmart.gov/why-buy-flood-insurance)

Note: This analysis uses the Federal Emergency Management Agency’s OpenFEMA API, but is not endorsed by FEMA. The Federal Government or FEMA cannot vouch for the data or analyses derived from these data after the data have been retrieved from the Agency's website(s). Please refer to the [OpenFEMA Terms and Conditions](https://www.fema.gov/about/openfema/terms-conditions) for further information regarding the usage and access of OpenFEMA datasets.

# 2. Notebooks
- [Download Data](https://github.com/mebauer/duckdb-fema-nfip/blob/main/download-data.ipynb): Demonstrates how to download the NFIP Claims dataset from OpenFEMA.
- [Analysis](https://github.com/mebauer/duckdb-fema-nfip/blob/main/analysis.ipynb): Explores NFIP Claims data with DuckDB with ease.
- [Generate Figures](https://github.com/mebauer/duckdb-fema-nfip/blob/main/figures.ipynb): Dedicated to generating figures and tables displayed on this page. For a more detailed analysis of the NFIP data, refer to the [analysis.ipynb](https://github.com/mebauer/duckdb-fema-nfip/blob/main/analysis.ipynb) notebook.
- [Metadata](https://github.com/mebauer/duckdb-fema-nfip/blob/main/metadata.ipynb): Examines the metadata for the NFIP Claims dataset. Here, we retrieve and save the [data dictionary](https://github.com/mebauer/duckdb-fema-nfip/blob/main/data-dictionary.csv).

# 3. Data 
OpenFEMA Dataset: FIMA NFIP Redacted Claims - v2. Retrieved from https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2. This product uses the FEMA OpenFEMA API, but is not endorsed by FEMA. The Federal Government or FEMA cannot vouch for the data or analyses derived from these data after the data have been retrieved from the Agency's website(s).

Please refer to the [OpenFEMA Terms and Conditions](https://www.fema.gov/about/openfema/terms-conditions) for further information regarding the usage and access of OpenFEMA datasets.

# 4. Additional Resources
## FEMA:
- NFIP:
    - [Historical NFIP Claims Information and Trends](https://www.floodsmart.gov/historical-nfip-claims-information-and-trends?map=countries/us/us-all&region=us&miny=all&maxy=all&county=&gtype=country)
    - [Flood Insurance Data and Analytics](https://nfipservices.floodsmart.gov/reports-flood-insurance-data)
    - [Frequently Asked Questions about NFIP Policies and Claims Data](https://nfipservices.floodsmart.gov/frequently-asked-questions-about-nfip-policies-and-claims-data)
- OpenFEMA:
    - [FEMA NFIP Claims and Policy Data Press Release (2019)](https://www.fema.gov/press-release/20230425/fema-publishes-nfip-claims-and-policy-data)
    - [OpenFEMA Dataset: FIMA NFIP Redacted Claims - v2](https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2)
    - [OpenFEMA Dataset: FIMA NFIP Redacted Policies - v2](https://www.fema.gov/openfema-data-page/fima-nfip-redacted-policies-v2)
    
## Academic Research:
- Wing, O.E.J., Pinter, N., Bates, P.D. *et al*. New insights into US flood vulnerability revealed from flood insurance big data. *Nat Commun* **11**, 1444 (2020). https://doi.org/10.1038/s41467-020-15264-2

## NFIP Redacted Claims & Policies Analysis:
**The Wharton School of the University of Pennsylvania**  
- Flood Insurance in the US: Lessons from FEMA’s Recent Data Release (2020):
    - [Part I](https://esg.wharton.upenn.edu/news/flood-insurance-in-the-us-lessons-from-femas-recent-data-release-part-i/)
    - [Part II](https://esg.wharton.upenn.edu/climate-center/flood-insurance-in-the-us-lessons-from-femas-recent-data-release-part-ii/)
    
**The Natural Resources Defense Council (NRDC)**  
- [FEMA Flood Data: 2.4 Million Damage Claims and Counting (2019)](https://www.nrdc.org/bio/anna-weber/fema-flood-data-24-million-damage-claims-and-counting)
- [FEMA Flood Data: What We Still Need to Know (2019)](https://www.nrdc.org/bio/anna-weber/fema-flood-data-what-we-still-need-know)
- [FEMA Puts New Data on the Map for Policymakers (2020)](https://www.huduser.gov/portal/periodicals/cityscpe/vol22num1/ch10.pdf)

**Milliman**
- [Residential Flood Risk in the United States: Quantifying Flood Losses, Mortgage Risk and Sea Level Rise (2020)](https://www.soa.org/globalassets/assets/files/resources/research-report/2020/soa-flood-report.pdf)
- [Insights into consumer demand for flood insurance: Trends in take-up (2021)](https://www.milliman.com/en/insight/insights-into-consumer-demand-for-flood-insurance-trends-in-take-up)
- [Estimating undisclosed flood risk in real estate transactions (2025)](https://edge.sitecorecloud.io/millimaninc5660-milliman6442-prod27d5-0001/media/Milliman/PDFs/2025-Articles/1-13-25_NRDC_Estimating-Undisclosed-Flood-Risk.pdf)

**Verisk**
- [Modeling Fundamentals: Evaluating U.S. Flood Model Loss Output with Historical Loss Experience (2020](https://www.verisk.com/blog/modeling-fundamentals-evaluating-u-s--flood-model-loss-output-with-historical-loss-experience/)

**Insurance Information Institute**
- [Flood: State of the Risk (2023)](https://www.iii.org/article/flood-state-of-the-risk)
- [Spotlight on: Flood insurance (2024)](https://www.iii.org/article/spotlight-on-flood-insurance)
- [Facts + Statistics: Flood insurance (2024)](https://www.iii.org/fact-statistic/facts-statistics-flood-insurance)
    
## Community Open Data:
**Norfolk Open Data**  
- [Norfolk Claims from the FEMA National Flood Insurance Program](https://data.norfolk.gov/stories/s/FEMA-National-Flood-Insurance-Program-Redacted-Cla/gi5t-nkzw/)
- [FEMA NFIP Claims Dataset](https://data.norfolk.gov/Government/FEMA-NFIP-Claims/suf7-r643/about_data)

## Other:
**DHS/FEMA**    
- [DHS/FEMA/PIA-050 National Flood Insurance Program (NFIP) PIVOT System (2018)](https://www.dhs.gov/publication/dhsfemapia-050-national-flood-insurance-program-nfip-pivot-system)

# 5. Say Hello!
Feel free to reach out.
- LinkedIn: [markebauer](https://www.linkedin.com/in/markebauer/)   
- Portfolio: [mebauer.github.io](https://mebauer.github.io/)
- GitHub: [mebauer](https://github.com/mebauer) 
