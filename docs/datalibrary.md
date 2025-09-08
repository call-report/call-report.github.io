# Data Library

Curated datasets, data dictionaries, and reference materials for bank regulatory data analysis.

## Overview

The Data Library provides essential reference data and resources to support your analysis of Federal financial system regulatory data. All resources are freely available and regularly updated.

## Data Resources Repository

Access our curated datasets at [github.com/call-report/data-resources](https://github.com/call-report/data-resources)

### Available Datasets

#### Federal Reserve Attribute Files
Historical attribute data for Federal Reserve regulated institutions (through 2019).

- **Format**: CSV
- **Coverage**: All Fed-regulated institutions
- **Fields**: RSSD ID, institution name, location, charter type, regulatory agency
- **Update Frequency**: Historical archive (no longer updated)

#### UBPR Technical Manual
Uniform Bank Performance Report technical specifications in JSON format.

- **Format**: JSON
- **Contents**: Ratio calculations, variable definitions, formulas
- **Use Case**: Understanding UBPR metrics and calculations

#### Data Dictionaries
Comprehensive data dictionaries for regulatory reports.

- **MDRM Dictionary**: Micro Data Reference Manual from the Federal Reserve
- **Call Report Dictionary**: Field definitions and validations
- **Format**: CSV and JSON
- **Update Frequency**: Quarterly

## Quick Access Guide

### Download Data Dictionaries
```python
import pandas as pd
import requests

# Download MDRM dictionary
url = "https://raw.githubusercontent.com/call-report/data-resources/main/dictionaries/mdrm_dictionary.csv"
mdrm_dict = pd.read_csv(url)

# View available fields
print(mdrm_dict.columns.tolist())
print(f"Total MDRM items: {len(mdrm_dict)}")
```

### Load Attribute Data
```python
# Load Federal Reserve attribute file
url = "https://raw.githubusercontent.com/call-report/data-resources/main/attributes/fed_attributes_2019.csv"
attributes = pd.read_csv(url)

# Filter for active banks
active_banks = attributes[attributes['active_flag'] == 1]
print(f"Active institutions: {len(active_banks)}")
```

## Data Dictionary Structure

### MDRM (Micro Data Reference Manual)

The MDRM contains definitions for all data elements collected by the Federal Reserve.

| Field | Description |
|-------|-------------|
| `mnemonic` | Unique identifier for the data element |
| `item_name` | Descriptive name |
| `description` | Detailed description |
| `data_type` | Numeric, text, or date |
| `unit` | Unit of measurement (dollars, percentage, etc.) |
| `frequency` | Reporting frequency |

### Call Report Schedule Mappings

Maps Call Report line items to MDRM mnemonics.

| Field | Description |
|-------|-------------|
| `schedule` | Call Report schedule (RC, RI, etc.) |
| `line_item` | Line item number |
| `mnemonic` | Corresponding MDRM code |
| `description` | Line item description |

## Working with Reference Data

### Institution Identifiers

```python
# Example: Cross-reference RSSD to FDIC Certificate
import pandas as pd

# Load crosswalk data
crosswalk = pd.read_csv("path/to/rssd_fdic_crosswalk.csv")

# Find FDIC cert for a given RSSD
rssd_id = 12345
fdic_cert = crosswalk[crosswalk['rssd'] == rssd_id]['fdic_cert'].values[0]
print(f"RSSD {rssd_id} corresponds to FDIC Cert {fdic_cert}")
```

### Understanding Report Schedules

Call Reports are organized into schedules:

- **Schedule RC**: Balance Sheet
- **Schedule RI**: Income Statement
- **Schedule RC-R**: Regulatory Capital
- **Schedule RC-L**: Derivatives and Off-Balance Sheet
- **Schedule RC-M**: Memoranda

### Data Quality Notes

1. **Historical Changes**: Be aware of reporting requirement changes over time
2. **Confidential Data**: Some data elements may be masked for confidentiality
3. **Restatements**: Institutions may revise previously reported data
4. **Missing Data**: Not all institutions report all data elements

## Useful Resources

### External Data Sources

- [FFIEC Central Data Repository](https://cdr.ffiec.gov/public/)
- [Federal Reserve Economic Data (FRED)](https://fred.stlouisfed.org/)
- [FDIC BankFind Suite](https://banks.data.fdic.gov/)
- [National Information Center](https://www.ffiec.gov/npw/FinancialReport/FinancialDataDownload)

### Documentation

- [Call Report Instructions](https://www.ffiec.gov/forms031.htm)
- [UBPR User Guide](https://www.ffiec.gov/ubpr.htm)
- [FR Y-9C Instructions](https://www.federalreserve.gov/reportforms/forms/FR_Y-9C20230331_i.pdf)

## Contributing Data Resources

We welcome contributions of useful datasets and reference materials. Please ensure:

1. Data is publicly available or properly licensed
2. Include documentation describing the data
3. Provide scripts for data processing if applicable
4. Follow our data format standards

Submit contributions via [GitHub pull request](https://github.com/call-report/data-resources/pulls).

## License

All data resources are provided under Creative Commons Attribution 4.0 International License unless otherwise specified.

## Updates

- **September 2025**: Updated MDRM dictionary with latest definitions
- **August 2025**: Added 2025 Q2 reference data
- **July 2025**: New crosswalk tables for institution identifiers

## Contact

For questions about data resources:
- Open an issue on [GitHub](https://github.com/call-report/data-resources/issues)
- Email: m@mikeh.dev