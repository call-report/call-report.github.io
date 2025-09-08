# Code Library

Open-source Python libraries and tools for collecting and analyzing bank regulatory data.

## Active Projects

### ffiec-data-connect
[![PyPI](https://img.shields.io/pypi/v/ffiec-data-connect)](https://pypi.org/project/ffiec-data-connect/)
[![Python](https://img.shields.io/pypi/pyversions/ffiec-data-connect)](https://pypi.org/project/ffiec-data-connect/)
[![License](https://img.shields.io/github/license/call-report/ffiec-data-connect)](https://github.com/call-report/ffiec-data-connect)

Modern Python wrapper for the FFIEC Webservice API, supporting both legacy SOAP and modern REST protocols.

#### Installation
```bash
pip install ffiec-data-connect
```

#### Quick Start
```python
from ffiec_data_connect import FfiecDataConnect
from ffiec_data_connect.constants import ReportingPeriod

# Initialize client
client = FfiecDataConnect()

# Fetch Call Report data
data = client.get_call_report(
    rssd_id="0000012345",
    reporting_period=ReportingPeriod.MARCH_31_2025
)

# Get data as DataFrame
df = client.get_ubpr_ratio(
    rssd_id="0000012345",
    reporting_period="2025-03-31",
    output_format="pandas"
)
```

#### Features
- Automatic protocol selection (REST with OAuth2 or SOAP fallback)
- Higher rate limits with REST API (2500 vs 1000 requests/hour)
- Multiple output formats (lists, Pandas DataFrames, Polars DataFrames)
- Built-in retry logic and error handling
- Type hints and comprehensive documentation

[View on GitHub](https://github.com/call-report/ffiec-data-connect) | [Documentation](https://github.com/call-report/ffiec-data-connect#readme)

---

### data-collector
[![PyPI](https://img.shields.io/pypi/v/ffiec-data-collector)](https://pypi.org/project/ffiec-data-collector/)
[![Python](https://img.shields.io/pypi/pyversions/ffiec-data-collector)](https://pypi.org/project/ffiec-data-collector/)

Universal bulk data collector for FFIEC and US Government Bank Regulatory data.

#### Installation
```bash
pip install ffiec-data-collector
```

#### Command Line Usage
```bash
# Download Call Report data
ffiec-data-collector call-report --period 2025Q1 --output-dir ./data

# Download UBPR data
ffiec-data-collector ubpr --period 2025Q1 --format csv

# Bulk download multiple periods
ffiec-data-collector bulk --start 2024Q1 --end 2025Q1
```

#### Python Usage
```python
from ffiec_data_collector import CallReportCollector

collector = CallReportCollector()

# Download all Call Reports for Q1 2025
collector.collect(
    period="2025Q1",
    output_format="parquet",
    output_dir="./data"
)
```

#### Features
- Version 2.0 with improved efficiency
- Direct HTTP downloads (no browser automation required)
- Supports multiple formats (XBRL, CSV, TSV, Parquet)
- Parallel downloads for faster collection
- Progress bars and logging
- Resume capability for interrupted downloads

[View on GitHub](https://github.com/call-report/data-collector) | [Documentation](https://github.com/call-report/data-collector#readme)

---

## Utility Scripts

### CDR Taxonomy Processor
Converts XBRL-based taxonomy files into hierarchical JSON format for easier processing.

```python
# Available in scripts-toolkit repository
python cdr_taxonomy_processor.py --input taxonomy.xsd --output taxonomy.json
```

[View Script](https://github.com/call-report/scripts-toolkit/tree/main/python/cdr_taxonomy_xbrl_to_json)

### MDRM Data Dictionary Collector
Downloads and processes the latest data dictionary from the Federal Reserve.

```python
# Available in scripts-toolkit repository
python mdrm_collector.py --output mdrm_dictionary.json
```

[View Script](https://github.com/call-report/scripts-toolkit/tree/main/python/mdrm_data_dictionary_collect_process)

---

## Installation Guide

### Prerequisites
- Python 3.10 or higher
- pip package manager

### Setting Up Your Environment

1. **Create a virtual environment** (recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. **Install the libraries**:
```bash
# For API access
pip install ffiec-data-connect

# For bulk data collection
pip install ffiec-data-collector

# For data analysis (optional)
pip install pandas polars jupyter
```

3. **Verify installation**:
```python
import ffiec_data_connect
import ffiec_data_collector

print(f"ffiec-data-connect version: {ffiec_data_connect.__version__}")
print(f"ffiec-data-collector version: {ffiec_data_collector.__version__}")
```

---

## Example Notebooks

### Basic Data Retrieval
```python
# Example: Fetch and analyze bank data
import pandas as pd
from ffiec_data_connect import FfiecDataConnect

client = FfiecDataConnect()

# Get list of reporting institutions
institutions = client.get_reporting_institutions("2025-06-30")

# Fetch data for top 10 banks
top_banks = institutions[:10]
data = []

for bank in top_banks:
    report = client.get_call_report(bank['rssd_id'], "2025-06-30")
    data.append(report)

# Convert to DataFrame for analysis
df = pd.DataFrame(data)
print(df.describe())
```

### Bulk Data Collection
```python
# Example: Collect historical data
from ffiec_data_collector import CallReportCollector
import pandas as pd

collector = CallReportCollector()

# Collect 2 years of quarterly data
quarters = ["2024Q1", "2024Q2", "2024Q3", "2024Q4", 
            "2025Q1", "2025Q2"]

for quarter in quarters:
    print(f"Collecting {quarter}...")
    collector.collect(
        period=quarter,
        output_format="parquet",
        output_dir=f"./data/{quarter}"
    )

# Load and combine data
dfs = []
for quarter in quarters:
    df = pd.read_parquet(f"./data/{quarter}/call_reports.parquet")
    df['quarter'] = quarter
    dfs.append(df)

combined = pd.concat(dfs, ignore_index=True)
print(f"Total records: {len(combined)}")
```

---

## Contributing

We welcome contributions! Please see our [Contributing Guide](https://github.com/call-report/.github/blob/main/CONTRIBUTING.md) for details.

### Development Setup
```bash
# Clone the repository
git clone https://github.com/call-report/ffiec-data-connect.git
cd ffiec-data-connect

# Install in development mode
pip install -e ".[dev]"

# Run tests
pytest

# Run linting
ruff check .
```

---

## Support

- **Issues**: [GitHub Issues](https://github.com/call-report/ffiec-data-connect/issues)
- **Discussions**: [GitHub Discussions](https://github.com/call-report/ffiec-data-connect/discussions)
- **Email**: m@mikeh.dev

---

## Legacy Projects

The following projects are no longer actively maintained but remain available for reference:

- [scripts-toolkit](https://github.com/call-report/scripts-toolkit) - Legacy ETL scripts (last updated: 2022)