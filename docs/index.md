# Call.Report: A Resource for Bank and Holding Company Regulatory Data

Welcome to Call.Report - your open-source gateway to U.S. bank regulatory data analysis.

## Quick Start

Get started with bank regulatory data in under 5 minutes:

```bash
# Install the main Python library
pip install ffiec-data-connect

# Fetch data for specific institutions
from ffiec_data_connect import FfiecDataConnect

client = FfiecDataConnect()
data = client.get_call_report("0000012345", "2025-06-30")
```

## Why Call.Report?

Accessing and processing US bank regulatory data without expensive subscriptions is challenging. Call.Report provides free, open-source tools and resources to democratize access to this critical financial data.

### What We Offer

- **Modern Python Libraries** - Production-ready packages for data collection
- **Comprehensive Documentation** - Guides for working with regulatory data
- **Data Resources** - Curated datasets and data dictionaries
- **Active Community** - Support from developers and analysts

## Featured Tools

### [ffiec-data-connect](https://github.com/call-report/ffiec-data-connect)
[![PyPI version](https://badge.fury.io/py/ffiec-data-connect.svg)](https://pypi.org/project/ffiec-data-connect/)
[![GitHub stars](https://img.shields.io/github/stars/call-report/ffiec-data-connect)](https://github.com/call-report/ffiec-data-connect)

Modern Python wrapper for FFIEC Webservice APIs with automatic protocol selection, OAuth2 authentication, and multiple output formats.

```python
pip install ffiec-data-connect
```

### [data-collector](https://github.com/call-report/data-collector)
[![PyPI version](https://badge.fury.io/py/ffiec-data-collector.svg)](https://pypi.org/project/ffiec-data-collector/)

Universal bulk data collector for FFIEC/US Bank Regulatory data with CLI interface and efficient HTTP-based collection.

```python
pip install ffiec-data-collector
```

## Navigation

| Section | Description |
|---------|-------------|
| [Code Library](/code) | Python libraries and tools for data collection |
| [Data Library](/datalibrary) | Curated datasets and resources |
| [Data Sources](/datasources/banktimeseries/) | Information on regulatory data sources |
| [API Documentation](/apis) | Technical API references |
| [License](/license) | Creative Commons Attribution 4.0 |

## Latest Updates

- **September 2025** - ffiec-data-connect actively maintained with REST API support
- **August 2025** - data-collector v2.0 released with improved efficiency
- **Ongoing** - Active development and community support

## Questions and Support

- 📝 [Report Issues](https://github.com/call-report/ffiec-data-connect/issues)
- 💬 [Discussions](https://github.com/call-report/ffiec-data-connect/discussions)
- 📧 Contact: m@mikeh.dev

## Important Disclaimer

**This site does not offer investment advice. This site is intended and must be used for informational purposes only.**