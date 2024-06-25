# Analyzing FEMA's National Flood Insurance Program (NFIP) Data With DuckDB
Author: Mark Bauer

![hurricane-ida](figures/hurricane-ida.png)  
*NFIP claims ($) related to Hurricane Ida by county, normalized by county area. Yellow indicates higher claims, purple indicates lower.*

# 1. Introduction
I've been enjoying [DuckDB](https://duckdb.org/) for the past few weeks, particularly how smooth the Python API feels. With its impressive speed and friendly SQL interface, analyzing moderately large datasets within a Jupyter Notebook is almost effortless. This project aims to demonstrate just how excited I am to use and to learn more about this incredible tool.

Given the substantial size of this dataset, it provided an opportunity to explore and utilize DuckDB, a high-performance analytical database. While this guide offers valuable insights, users are encouraged to supplement their understanding by referring to the [official documentation](https://duckdb.org/docs/) provided on DuckDB's website.

# 2. Notebook
Explore how DuckDB can query 2.6M rows and 70 columns within a Jupyter Notebook in seconds: [analysis.ipynb](https://github.com/mebauer/duckdb-fema-nfip/blob/main/analysis.ipynb).

# 3. Data
**OpenFEMA Dataset: FIMA NFIP Redacted Claims - v2**:   
The analysis presented here is solely focused on the [FIMA NFIP Redacted Claims](https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2) dataset, which fortunately is available in Parquet format. With more than 2M rows, this dataset provides detailed information about the [National Flood Insurance Program (NFIP)](https://www.floodsmart.gov/about) claims transations and is redated to protect policy holders.

Useful Links:
- [FIMA NFIP Redacted Claims](https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2)
- [National Flood Insurance Program (NFIP)](https://www.floodsmart.gov/about)
- [Flood Insurance Data and Analytics](https://nfipservices.floodsmart.gov/reports-flood-insurance-data)

**Dataset Citation:**  
OpenFEMA Dataset: FIMA NFIP Redacted Claims - v2. Retrieved from https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2 on May 9, 2024, 16:02 EST. This product uses the FEMA OpenFEMA API, but is not endorsed by FEMA. The Federal Government or FEMA cannot vouch for the data or analyses derived from these data after the data have been retrieved from the Agency's website(s).

**OpenFEMA Terms and Conditions:**    
Please refer to the [OpenFEMA Terms and Conditions](https://www.fema.gov/about/openfema/terms-conditions) for further information regarding the usage and access of OpenFEMA datasets.

# 4. Additional Resources
- Official DuckDB Documentation: https://duckdb.org/
- DuckDB Python client guide: https://duckdb.org/docs/api/python/overview
- OpenFEMA: https://www.fema.gov/about/reports-and-data/openfema
- OpenFEMA Dataset: FIMA NFIP Redacted Claims - v2: https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2

# 5. Say Hello!
Feel free to reach out.
- LinkedIn: [markebauer](https://www.linkedin.com/in/markebauer/)   
- Portfolio: [mebauer.github.io](https://mebauer.github.io/)
- GitHub: [mebauer](https://github.com/mebauer) 
