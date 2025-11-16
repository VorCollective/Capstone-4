# Mpox Genomic Surveillance Analysis

[![Project Status](https://img.shields.io/badge/Project-Public%20Health%20Analytics-blue)](https://github.com/your-username/mpox-surveillance)
[![Python Version](https://img.shields.io/badge/Python-3.8%2B-green)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen)](https://github.com/your-username/mpox-surveillance)

## Table of Contents

- [Quick Links](#quick-links)
- [Project Overview](#project-overview)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [Data Sources](#data-sources)
- [Analytical Features](#analytical-features)
- [Output Dashboard](#output-dashboard)
- [Use Cases](#use-cases)
- [Technical Implementation](#technical-implementation)
- [Example Results](#example-results)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Quick Links

**Technical Article**: [Global Genomic Surveillance of Mpox: An Integrated Analysis of Sequencing Coverage and Epidemiological Trends](https://lebensons.hashnode.dev/global-genomic-surveillance-of-mpox-an-integrated-analysis-of-sequencing-coverage-and-epidemiological-trend)

**Live Dashboard**: [Mpox Genomic Explorer](https://mpox.lovable.app)

## Project Overview

This project provides a data-driven assessment of global Mpox genomic surveillance capabilities by analyzing the integration of epidemiological case reporting with viral genome sequencing efforts. The analysis identifies surveillance gaps, evaluates country-level performance, and generates actionable insights for public health decision-making.

**Key Questions Addressed:**
- How effectively were genomic surveillance systems deployed relative to case detection?
- What were the geographical and temporal patterns in sequencing coverage?
- Which countries demonstrated optimal integration of epidemiological and genomic surveillance?

## Project Structure

```
mpox-genomic-surveillance/
├── data/
│   ├── raw/
│   │   ├ sequences_file.csv          # Raw genomic sequence metadata
│   │   └ cases_file.csv             # Raw epidemiological case data
│   └── processed/
│       └── concatenated_output.csv   # Merged dataset
├── analysis/
│   └── mpox_surveillance_analysis.py # Main analysis script
├── outputs/
│   ├── Country_Summary.csv          # Geographical performance analysis
│   ├── Daily_Timeline.csv           # High-resolution temporal trends
│   ├── Monthly_Aggregate.csv        # Aggregated trend analysis
│   ├── Lineage_Data.csv             # Genomic variant surveillance
│   └── Sequence_Details.csv         # Technical metadata
├── visuals/
│   └── surveillance_trends.png      # Generated analysis plots
└── README.md
```

## Installation & Setup

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn biopython
```

### Quick Start
1. Clone or download this repository
2. Place your input files in the `data/raw/` directory:
   - `sequences_file.csv`
   - `cases_file.csv`
3. Run the main analysis script:

```bash
python analysis/mpox_surveillance_analysis.py
```

### Verification
After running the script, check the `outputs/` directory for generated files:
- `Country_Summary.csv`
- `Daily_Timeline.csv` 
- `Monthly_Aggregate.csv`
- `Lineage_Data.csv`
- `Sequence_Details.csv`

## Data Sources

### Primary Data Inputs

| Dataset | Source | Key Fields | Purpose |
|---------|--------|------------|---------|
| **Genomic Surveillance Data**<br>`sequences_file.csv` | NCBI Virus, GISAID, or other genomic repositories | `['Accession', 'Collection_Date', 'Geo_Location', 'MPXV_Lineage']` | Viral sequence metadata and lineage information |
| **Epidemiological Data**<br>`cases_file.csv` | WHO, CDC, or national health authority reports | `['NEW_CONF_CASES', 'DATE', 'COUNTRY', 'ISO3']` | Case counts and reporting information |

## Analytical Features

### Key Analytical Components

| Feature | Description | Metrics |
|---------|-------------|---------|
| **Data Integration** | Combines epidemiological and genomic datasets with quality validation | Data completeness, schema validation |
| **Spatiotemporal Analysis** | Geographical and temporal alignment of case and sequence data | Country-level coverage, monthly trends |
| **Surveillance Metrics** | Calculates sequencing coverage rates and performance indicators | Coverage rates, performance tiers |
| **Performance Stratification** | Categorizes countries by surveillance effectiveness | Excellent/Adequate/Moderate/Limited |
| **Gap Analysis** | Identifies surveillance blind spots and capacity needs | Coverage gaps, resource allocation |

### Performance Thresholds

```python
SURVEILLANCE_TIERS = {
    'Excellent': '≥20% coverage',
    'Adequate': '10-20% coverage', 
    'Moderate': '5-10% coverage',
    'Limited': '<5% coverage'
}
```

## Output Dashboard

### Generated Output Files

| File | Purpose | Key Fields & Metrics |
|------|---------|---------------------|
| `Country_Summary.csv` | Geographical performance analysis | `['COUNTRY', 'TOTAL_CASES', 'TOTAL_SEQUENCES', 'SEQUENCING_RATE', 'FIRST_CASE_DATE', 'ISO3']` |
| `Daily_Timeline.csv` | High-resolution temporal trends | `['DATE', 'COUNTRY', 'NEW_CONF_CASES', 'NEW_SEQUENCES', 'CUMULATIVE_CASES', 'ISO3']` |
| `Monthly_Aggregate.csv` | Aggregated trend analysis | `['YEAR_MONTH', 'GLOBAL_CASES', 'GLOBAL_SEQUENCES', 'GLOBAL_SEQUENCING_RATE', 'COUNTRIES_AFFECTED']` |
| `Lineage_Data.csv` | Genomic variant surveillance | `['COLLECTION_DATE', 'LINEAGE', 'COUNTRY', 'ISO3', 'ACCESSION_ID']` |
| `Sequence_Details.csv` | Technical metadata analysis | `['ACCESSION_ID', 'COUNTRY', 'ISO3', 'COLLECTION_DATE', 'RELEASE_DATE', 'LINEAGE', 'SUBMISSION_LAG']` |

## Use Cases

### Public Health Applications

| Use Case | Benefit | Stakeholders |
|----------|---------|-------------|
| **Surveillance Gap Identification** | Pinpoint countries/periods with inadequate sequencing coverage | Public health agencies, WHO |
| **Resource Allocation** | Guide investments in genomic sequencing capacity building | Funding organizations, Ministries of Health |
| **Outbreak Response Assessment** | Evaluate effectiveness of surveillance systems during emergencies | Emergency response teams, Epidemiologists |
| **Performance Benchmarking** | Compare country performance against global standards | International health organizations, Researchers |

### Research Applications
- **Genomic Epidemiology**: Study viral evolution and spread patterns
- **Methodology Development**: Framework for assessing other pathogen surveillance
- **Policy Analysis**: Evidence for public health policy recommendations
- **Capacity Planning**: Strategic planning for laboratory networks

## Technical Implementation

### Core Processing Pipeline

```python
def analytical_pipeline(sequences_file, cases_file):
    # 1. Data Integration & Validation
    merged_df = integrate_and_validate_data(sequences_file, cases_file)
    
    # 2. Spatiotemporal Integration
    integrated_df, sequences, cases = integrate_sequences_with_cases(merged_df)
    
    # 3. Surveillance Metrics Calculation
    coverage_metrics = analyze_sequencing_coverage(integrated_df)
    
    # 4. Trend Analysis & Visualization
    temporal_trends = analyze_trends(integrated_df)
    
    # 5. Dashboard Dataset Generation
    dashboard_data = create_dashboard_ready_data(merged_df)
    
    return analytical_results
```

### Key Analytical Methods

| Method | Purpose | Output |
|--------|---------|--------|
| **Geographical Standardization** | Parse and standardize country names from location data | Consistent country-level analysis |
| **Temporal Aggregation** | Aggregate data to monthly resolution for trend analysis | Monthly coverage trends, outbreak progression |
| **Coverage Calculation** | Compute sequencing rates with mathematical error handling | Performance metrics, surveillance assessment |
| **Performance Benchmarking** | Categorize countries by surveillance effectiveness | Actionable insights, capacity building priorities |

### Data Validation Framework

```python
def validate_dataset(df):
    """Comprehensive data quality checks"""
    
    # Primary key validation
    assert df['Accession'].is_unique, "Accession must be unique"
    assert df['Accession'].isna().sum() == 0, "No null Accessions"
    
    # Critical field completeness
    assert df['Country_Clean'].isna().sum() == 0, "No null countries"
    
    # Temporal plausibility
    current_year = datetime.now().year
    valid_years = df['Collection_Year'].between(1950, current_year)
    assert valid_years.all(), "Invalid collection years"
```

## Example Results

### Surveillance Performance Summary

```
=== MPOX SEQUENCING SURVEILLANCE SUMMARY ===

KEY METRICS:
- Total sequences: 15,247
- Total cases: 89,327  
- Global sequencing rate: 17.1%
- Countries with sequences: 48
- Time period: 2022-05 to 2023-08

TOP SEQUENCING COUNTRIES:
- United States: 4,892 sequences (22.3% coverage)
- United Kingdom: 3,451 sequences (25.1% coverage)
- Spain: 1,892 sequences (18.7% coverage)

PUBLIC HEALTH ASSESSMENT:
ADEQUATE surveillance - sufficient for major variant monitoring
```

### Performance Interpretation Guide

| Coverage Tier | Interpretation | Recommended Action |
|---------------|----------------|-------------------|
| **Excellent (≥20%)** | Robust variant detection capability | Maintain capacity, share best practices |
| **Adequate (10-20%)** | Sufficient for major variant monitoring | Sustain current efforts, minor improvements |
| **Moderate (5-10%)** | Some gaps in variant detection | Targeted capacity building, technical assistance |
| **Limited (<5%)** | Significant surveillance blind spots | Urgent intervention, resource allocation, training |

## Contributing

We welcome contributions to enhance this analytical framework:

### Bug Reports
- Open an issue with detailed description
- Include error messages and reproduction steps
- Specify environment details (OS, Python version)

### Feature Requests
- Suggest new analytical modules or visualizations
- Propose enhancements to existing functionality
- Recommend additional data sources or integrations

### Code Contributions
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Data Partnerships
- Collaborate on expanding data sources
- Share validated datasets for testing
- Contribute to data quality improvements

### Priority Areas for Contribution
- Additional visualization types
- Machine learning integration for trend prediction
- Real-time data pipeline enhancements
- Multi-pathogen analysis framework

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

**Permissions**:
- Commercial use
- Modification
- Distribution
- Private use

**Conditions**:
- Include license and copyright notice

**Limitations**:
- No liability
- No warranty

## Acknowledgments

### Data Providers
- **NCBI** - National Center for Biotechnology Information
- **GISAID** - Global Initiative on Sharing All Influenza Data
- **WHO** - World Health Organization
- **National Public Health Agencies** - Various country-level data contributors

### Technical Dependencies
- **Pandas** - Data manipulation and analysis
- **NumPy** - Numerical computing
- **Matplotlib** - Visualization and plotting
- **Seaborn** - Statistical data visualization
- **Biopython** - Biological computation

### Institutional Support
- Public health laboratories worldwide
- Bioinformatics and genomics communities
- Open-source software contributors

### Special Thanks
- Frontline healthcare workers during the Mpox outbreak
- Public health professionals implementing surveillance systems
- Researchers advancing genomic epidemiology methods

---

**Maintained by**: [Your Name/Organization]  
**Last Updated**: October 2023  
**Project Status**: Active

[Technical Article](https://lebensons.hashnode.dev/global-genomic-surveillance-of-mpox-an-integrated-analysis-of-sequencing-coverage-and-epidemiological-trend) | [Live Dashboard](https://mpox.lovable.app)
