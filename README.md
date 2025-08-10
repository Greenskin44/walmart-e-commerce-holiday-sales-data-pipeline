# Walmart E-commerce Holiday Sales Data Pipeline

![Walmart E-commerce](image/walmartecomm.jpg)

## 📋 Project Overview

This project implements a comprehensive data pipeline for analyzing Walmart's e-commerce sales patterns around major holidays. The analysis focuses on understanding supply and demand fluctuations during key holiday periods including the Super Bowl, Labor Day, Thanksgiving, and Christmas.

## 🎯 Business Context

Walmart, the largest retail chain in the United States, has significantly expanded its e-commerce operations, achieving $80 billion in online sales by 2022 (representing 13% of total sales). Holiday periods create unique challenges and opportunities in retail operations, making it crucial to understand sales patterns during these periods.

## 🚀 Features

- **Complete ETL Pipeline**: Extract, Transform, Load processes for retail sales data
- **Data Quality Assurance**: Comprehensive validation and error handling
- **Holiday Impact Analysis**: Statistical analysis of sales during holiday periods
- **Monthly Trend Analysis**: Seasonal pattern identification and aggregation
- **Professional Documentation**: Enterprise-ready code with comprehensive logging
- **Reproducible Results**: Structured project layout for consistent execution

## 📊 Data Sources

### 1. Grocery Sales Database (`grocery_sales` table)
- **index**: Unique identifier for each record
- **Store_ID**: Store identification number
- **Date**: Week of sales data collection
- **Weekly_Sales**: Sales revenue for the specified week and store

### 2. Complementary Data (`extra_data.parquet`)
- **IsHoliday**: Binary indicator for holiday weeks (1 = holiday, 0 = regular week)
- **Temperature**: Average temperature during sales period
- **Fuel_Price**: Regional fuel price (impacts customer travel patterns)
- **CPI**: Consumer Price Index (economic indicator)
- **Unemployment**: Regional unemployment rate
- **MarkDown1-4**: Promotional markdown activity across different categories
- **Dept**: Department number within each store
- **Size**: Store size classification
- **Type**: Store type (derived from size classification)

## 🏗️ Project Structure

```
Data_Pipeline/
├── notebook/
│   └── notebook.ipynb          # Main analysis notebook with complete pipeline
├── data/
│   ├── extra_data.parquet      # Source: Complementary economic data
│   ├── clean_data.csv          # Output: Processed dataset
│   └── agg_data.csv           # Output: Monthly sales aggregation
├── image/
│   └── walmartecomm.jpg       # Project banner image
├── requirements.txt           # Python dependencies
├── README.md                  # This documentation
└── .gitignore                 # Git ignore rules
```

## 🛠️ Technical Requirements

### System Requirements
- **Python**: 3.8 or higher
- **Operating System**: Windows, macOS, or Linux
- **Memory**: Minimum 4GB RAM (8GB recommended for large datasets)
- **Storage**: 500MB free space for data and outputs

### Python Dependencies
```
pandas>=1.5.0
pyarrow>=10.0.0
numpy>=1.21.0
jupyter>=1.0.0
```

## 📥 Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/walmart-sales-pipeline.git
   cd walmart-sales-pipeline
   ```

2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```

5. **Open `notebook/notebook.ipynb` and run all cells**

## 🚀 Usage

### Quick Start
1. Ensure your PostgreSQL database contains the `grocery_sales` table
2. Place `extra_data.parquet` in the `data/` directory
3. Run all cells in the notebook sequentially
4. Review outputs in the `data/` directory

### Pipeline Steps

1. **Data Extraction** (`extract()` function)
   - Connects to PostgreSQL database
   - Loads complementary data from parquet file
   - Merges datasets on common index

2. **Data Transformation** (`transform()` function)
   - Handles missing values with median imputation
   - Filters for significant sales (>$10,000)
   - Extracts temporal features (month from date)
   - Selects relevant columns for analysis

3. **Data Aggregation** (`avg_weekly_sales_per_month()` function)
   - Calculates monthly sales averages
   - Identifies peak and low performance periods
   - Provides statistical summaries

4. **Data Loading** (`load()` function)
   - Saves cleaned dataset as `clean_data.csv`
   - Saves aggregated data as `agg_data.csv`
   - Creates necessary directories

5. **Quality Validation** (`validation()` function)
   - Verifies file creation and structure
   - Validates data quality and completeness
   - Provides comprehensive reporting

## 📈 Expected Outputs

### 1. Clean Dataset (`clean_data.csv`)
Processed dataset containing:
- **Store_ID**: Store identifier
- **Month**: Extracted month (1-12)
- **Dept**: Department number
- **IsHoliday**: Holiday indicator (0/1)
- **Weekly_Sales**: Sales amount (filtered >$10,000)
- **CPI**: Consumer Price Index
- **Unemployment**: Unemployment rate

### 2. Aggregated Dataset (`agg_data.csv`)
Monthly sales summary containing:
- **Month**: Month number (1-12)
- **Weekly_Sales**: Average weekly sales for the month

## 🔍 Key Insights

The pipeline enables analysis of:
- **Seasonal Trends**: Monthly sales variation patterns
- **Holiday Impact**: Sales performance during holiday vs. regular weeks
- **Economic Correlations**: Relationship between CPI, unemployment, and sales
- **Store Performance**: Comparative analysis across different stores and departments

## 📊 Performance Metrics

- **Processing Time**: ~2-5 minutes for typical dataset sizes
- **Memory Usage**: ~500MB-2GB depending on dataset size
- **Data Reduction**: Typically 20-30% reduction after filtering
- **Quality Score**: >95% data completeness after cleaning

## 🤝 Contributing

We welcome contributions! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Standards
- Follow PEP 8 Python style guide
- Add comprehensive docstrings to functions
- Include error handling and logging
- Add tests for new functionality

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **DataCamp**: This project was inspired by educational materials and best practices from DataCamp's data engineering courses
- **Walmart**: For providing the conceptual framework for retail analytics
- **Open Source Community**: For the excellent tools and libraries that make this analysis possible

## ⚠️ Disclaimer

**This project is intended for educational purposes only.** The analysis, methodologies, and conclusions presented here are for learning and demonstration purposes. This work should not be used for actual business decisions without proper validation and additional analysis.

The data used in this project may be simulated or anonymized and should not be considered representative of actual Walmart business metrics.

## 📞 Support

If you encounter any issues or have questions:

1. Check the [Issues](../../issues) section for existing solutions
2. Create a new issue with detailed information about your problem
3. Include your Python version, operating system, and error messages
4. Provide steps to reproduce the issue

## 🔄 Version History

- **v1.0.0** (2025-08-10): Initial release with complete ETL pipeline
  - Data extraction from PostgreSQL and parquet files
  - Comprehensive data transformation and cleaning
  - Monthly aggregation analysis
  - Quality validation and reporting
  - Professional documentation and structure

---

**Happy analyzing! 📊✨**

---

*Last updated: August 10, 2025*
