# Data Sources

Federal Financial System Regulatory Data sources are fragmented across various Federal agency web site. This page is a compilation of the locations and respective data sources, organized by data source "families."

## Bank Regulatory Data

### About

#### Time Series Frequency

Most all public bank regulatory data is time series data with a quarterly frequency. Some data, particularly for smaller financial institutions' data is semi-annual. 

#### Publishing frequency

Regulatory agencies receive data on a rolling basis. Bulk data downloads are updated approximately monthly, while "webservice" feeds are updated soon after bank regulatory filings are submitted and validated.

#### Fields and Data Dictionaries

Time series are published by field name (an "MDRM"), the ID of the reporting institution, and the reporting date (typically quarterly). 

The data release date is not included in the datasets themselves, but can be inferred from the data publication data.

The data dictionary to describe the MDRM fields is available at: [https://www.federalreserve.gov/apps/mdrm/pdf/MDRM.zip](https://www.federalreserve.gov/apps/mdrm/pdf/MDRM.zip), and is updated daily.


### Sources

#### 2001 - present

##### Bulk Data Downloads

- Historical data is provided from 2001 until the present day by the Federal Financial Institutions Examination Council (FFIEC).

- Bulk data downloads are generated from the rolling filings on monthly basis, typically released mid-month. 
  
- Data is provided in XBRL and CSV format.

- The permanent lnk to download bulk regulatory data is available at [https://cdr.ffiec.gov/public/PWS/DownloadBulkData.aspx](https://cdr.ffiec.gov/public/PWS/DownloadBulkData.aspx)

##### Webservice Access

TBD

#### 1978 - 2010

- Historical bank regulatory data is provided by the Federal Reserve Bank of Chicago (the "Chicago" dataset) at two links: 
  - 1976-2000: [https://www.chicagofed.org/banking/financial-institution-reports/commercial-bank-data-complete-1976-2000](https://www.chicagofed.org/banking/financial-institution-reports/commercial-bank-data-complete-1976-2000)

  - 2000-2010: [https://www.chicagofed.org/banking/financial-institution-reports/commercial-bank-data-complete-2001-2010](https://www.chicagofed.org/banking/financial-institution-reports/commercial-bank-data-complete-2001-2010)


- Note that the "Chicago" dataset overlaps with the FFIEC dataset; if combining the two datasets, for overlapping data points, to utilize the FFIEC dataset in lieu of the Chicago dataset.
- Data is provided in SAS XPORT format. (Python import script is TBD.)