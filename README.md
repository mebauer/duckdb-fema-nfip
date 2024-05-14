# Analyzing FEMA's National Flood Insurance Program (NFIP) Data With DuckDB
Author: Mark Bauer

![hurricane-ida](figures/hurricane-ida.png)  
*Hurricane Ida NFIP claims by county. Claims ($) are normalized by county area.*

# 1. Introduction
The FEMA National Flood Insurance Program (NFIP) website offers a trove of valuable information. Among its highlights is the [Flood Insurance Data and Analytics](https://nfipservices.floodsmart.gov/reports-flood-insurance-data) section, featuring data visualizations, tables, and reports. This project was inspired by these resources, particularly the Financial Losses by State and Policy, and Loss Statistics by Flood Zone Excel files.

Additionally, this analysis focuses solely on the [NFIP Redated Claims](https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2) dataset, and fortunately, it is available as a Parquet file. Given the size of this dataset, it was a good opportunity to utilize and learn more about [DuckDB](https://duckdb.org/). While this guide serves as a valuable resource, I encourage users to complement their learning with the [official documentation](https://duckdb.org/) available on DuckDB's website for a comprehensive understanding.

# 2. Notebook
- Explore how DuckDB can query 2.6M rows inside a Jupyter Notebook with finesse: [analysis.ipynb](https://github.com/mebauer/duckdb-fema-nfip/blob/main/analysis.ipynb).

# 3. Data
- OpenFEMA Dataset: FIMA NFIP Redacted Claims - v2: https://www.fema.gov/openfema-data-page/fima-nfip-redacted-claims-v2

# 4. Additional Resources
- Official DuckDB Documentation: https://duckdb.org/
- DuckDB Python client guide: https://duckdb.org/docs/api/python/overview
- OpenFEMA: https://www.fema.gov/about/reports-and-data/openfema

# 5. Say Hello!
Feel free to reach out.
- LinkedIn: [markebauer](https://www.linkedin.com/in/markebauer/)  
- GitHub: [mebauer](https://github.com/mebauer)  
- Portfolio: [mebauer.github.io](https://mebauer.github.io/)
