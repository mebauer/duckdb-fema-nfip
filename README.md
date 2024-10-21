# Analyzing FEMA's National Flood Insurance Program (NFIP) Data With DuckDB
Author: Mark Bauer

![hurricane-ida](figures/hurricane-ida.png)  
*NFIP claims ($) related to Hurricane Ida by county, normalized by county area. Yellow indicates higher claims, purple indicates lower.*

# 1. Introduction
I've been enjoying [DuckDB](https://duckdb.org/) for the past few weeks, particularly how smooth the Python API feels. With its impressive speed and friendly SQL interface, analyzing moderately large datasets within a Jupyter Notebook is almost effortless. This project aims to demonstrate just how excited I am to use and to learn more about this incredible tool.

The analysis presented here is solely focused on the [FIMA NFIP Redacted Claims](https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2) dataset, which fortunately is available in Parquet format. With more than 2M rows, this dataset provides detailed information about the [National Flood Insurance Program (NFIP)](https://www.floodsmart.gov/about) claims transations and is redated to protect policy holders.

Given the substantial size of this dataset, it provided an opportunity to explore and utilize DuckDB, a high-performance analytical database. While this guide offers valuable insights, users are encouraged to supplement their understanding by referring to the [official documentation](https://duckdb.org/docs/) provided on DuckDB's website.

# 2. Notebook
Explore how DuckDB can query 2.6M rows and 70 columns within a Jupyter Notebook in seconds: [analysis.ipynb](https://github.com/mebauer/duckdb-fema-nfip/blob/main/analysis.ipynb).

# 3. Data 
OpenFEMA Dataset: FIMA NFIP Redacted Claims - v2. Retrieved from https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2. This product uses the FEMA OpenFEMA API, but is not endorsed by FEMA. The Federal Government or FEMA cannot vouch for the data or analyses derived from these data after the data have been retrieved from the Agency's website(s).

Please refer to the [OpenFEMA Terms and Conditions](https://www.fema.gov/about/openfema/terms-conditions) for further information regarding the usage and access of OpenFEMA datasets.

# 4. Additional Resources
## FEMA:
- NFIP:
    - Flood Insurance Data and Analytics: https://nfipservices.floodsmart.gov/reports-flood-insurance-data
    - Frequently Asked Questions about NFIP Policies and Claims Data: https://nfipservices.floodsmart.gov/frequently-asked-questions-about-nfip-policies-and-claims-data
- OpenFEMA:
    - FEMA NFIP Claims and Policy Data Press Release (2019): https://www.fema.gov/press-release/20230425/fema-publishes-nfip-claims-and-policy-data
    - OpenFEMA Dataset: FIMA NFIP Redacted Claims - v2: https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2
    - OpenFEMA Dataset: FIMA NFIP Redacted Policies - v2: https://www.fema.gov/openfema-data-page/fima-nfip-redacted-policies-v2
    - OpenFEMA Platform: https://www.fema.gov/about/reports-and-data/openfema
    
## Academic Research:
- Wing, O.E.J., Pinter, N., Bates, P.D. *et al*. New insights into US flood vulnerability revealed from flood insurance big data. *Nat Commun* **11**, 1444 (2020). https://doi.org/10.1038/s41467-020-15264-2

## NFIP Redacted Claims & Policies Analysis:
**The Wharton School of the University of Pennsylvania**  
- Flood Insurance in the US: Lessons from FEMA’s Recent Data Release (2020):
    - Part I: https://esg.wharton.upenn.edu/news/flood-insurance-in-the-us-lessons-from-femas-recent-data-release-part-i/
    - Part II: https://esg.wharton.upenn.edu/climate-center/flood-insurance-in-the-us-lessons-from-femas-recent-data-release-part-ii/
    
**The Natural Resources Defense Council (NRDC)**  
- FEMA Flood Data: 2.4 Million Damage Claims and Counting (2019): https://www.nrdc.org/bio/anna-weber/fema-flood-data-24-million-damage-claims-and-counting
- FEMA Flood Data: What We Still Need to Know (2019): https://www.nrdc.org/bio/anna-weber/fema-flood-data-what-we-still-need-know
- FEMA Puts New Data on the Map for Policymakers (2020): https://www.huduser.gov/portal/periodicals/cityscpe/vol22num1/ch10.pdf

**Verisk**
- Modeling Fundamentals: Evaluating U.S. Flood Model Loss Output with Historical Loss Experience (2020): https://www.verisk.com/blog/modeling-fundamentals-evaluating-u-s--flood-model-loss-output-with-historical-loss-experience/

**Insurance Information Institute**
- Facts + Statistics: Flood insurance: https://www.iii.org/fact-statistic/facts-statistics-flood-insurance
    
## Community Open Data:
**Norfolk Open Data**  
- Norfolk Claims from the FEMA National Flood Insurance Program: https://data.norfolk.gov/stories/s/FEMA-National-Flood-Insurance-Program-Redacted-Cla/gi5t-nkzw/
- FEMA NFIP Claims Dataset: https://data.norfolk.gov/Government/FEMA-NFIP-Claims/suf7-r643/about_data

## Other:
**DHS/FEMA/PIA-050 National Flood Insurance Program (NFIP) PIVOT System**  
    - DHS/FEMA/PIA-050 National Flood Insurance Program PIVOT System - March 2018: https://www.dhs.gov/sites/default/files/publications/privacy-pia-fema-050-nfippivot-march2018_0.pdf
    - DHS/FEMA/PIA-050 National Flood Insurance Program PIVOT System - PIA Appendix - September 2022: https://www.dhs.gov/sites/default/files/2022-09/privacy-pia-fema-050-nfippivot-sep2022.pdf
    
**OIG**  
    - FIMA Made Progress Modernizing Its NFIP System, but Data Quality Needs Improvement (2020): https://www.oig.dhs.gov/sites/default/files/assets/2020-11/OIG-21-04-Nov20.pdf 

# 5. Say Hello!
Feel free to reach out.
- LinkedIn: [markebauer](https://www.linkedin.com/in/markebauer/)   
- Portfolio: [mebauer.github.io](https://mebauer.github.io/)
- GitHub: [mebauer](https://github.com/mebauer) 
