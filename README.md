# File Format Converter

A metadata-driven ETL utility built with Python and Pandas that converts structured CSV datasets into JSON Lines format.

The project demonstrates practical Data Engineering concepts such as schema-driven processing, data transformation, command-line arguments, environment-based configuration, exception handling, and modular ETL workflows.

## Project Overview

This project reads CSV datasets from a source directory, uses schema metadata to assign the appropriate column names, loads the data into Pandas DataFrames, and converts the datasets into JSON Lines format.

The application can process:

- All available datasets
- A selected subset of datasets provided at runtime

### ETL Workflow

```text
CSV Files
    |
    v
Schema Metadata (schemas.json)
    |
    v
Pandas DataFrame
    |
    v
Data Transformation
    |
    v
JSON Lines Output
```

## Technologies Used

- Python
- Pandas
- JSON
- CSV
- Python `glob`
- Python `os`
- Python `sys`
- Python `re`
- Environment Variables
- Git & GitHub

## Project Structure

```text
file-format-converter/
|
├── app.py
├── requirements.txt
├── .gitignore
|
└── data/
    └── retail_db/
        └── schemas.json
```

The complete source dataset is excluded from the repository through `.gitignore`.

## Key Features

### 1. Metadata-Driven Processing

Instead of hardcoding column names for every dataset, the application reads column metadata from `schemas.json`.

This allows the same processing logic to work with multiple datasets.

### 2. CSV to JSON Lines Conversion

Input CSV files are loaded using Pandas:

```python
df = pd.read_csv(
    file,
    header=None,
    names=columns
)
```

The resulting DataFrame is written as JSON Lines:

```python
df.to_json(
    json_file_path,
    orient="records",
    lines=True
)
```

### 3. Selective Dataset Processing

The application supports processing only selected datasets using command-line arguments.

For example:

```powershell
python app.py '["orders", "order_items"]'
```

This processes only the `orders` and `order_items` datasets.

### 4. Process All Datasets

Running the application without a dataset argument processes all available datasets:

```powershell
python app.py
```

### 5. Environment-Based Configuration

The application supports environment variables for configuration, allowing paths and other settings to be managed without hardcoding environment-specific values.

### 6. Exception Handling

Dataset processing includes exception handling to handle errors during the ETL workflow.

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/AkashG-03/file-format-converter.git
```

### 2. Navigate to the Project

```bash
cd file-format-converter
```

### 3. Create a Virtual Environment

For Windows PowerShell:

```powershell
python -m venv ffc-venv
```

### 4. Activate the Virtual Environment

```powershell
.\ffc-venv\Scripts\Activate.ps1
```

### 5. Install Dependencies

```powershell
pip install -r requirements.txt
```

## Running the Application

### Process All Datasets

```powershell
python app.py
```

### Process Selected Datasets

```powershell
python app.py '["orders", "order_items"]'
```

## Example Processing Output

```text
Processing departments
Processing categories
Processing orders
Processing products
Processing customers
Processing order_items
```

## Concepts Demonstrated

This project applies fundamental Data Engineering concepts including:

- ETL workflows
- Data ingestion
- Data transformation
- Schema management
- Metadata-driven processing
- Pandas DataFrames
- CSV processing
- JSON and JSON Lines
- Command-line arguments
- Environment variables
- Exception handling
- Modular Python programming
- Virtual environments
- Git version control

## Future Improvements

Possible improvements to the project include:

- Add support for Parquet output
- Add data quality and schema validation
- Add structured logging
- Add processing statistics and execution-time reporting
- Add unit tests
- Add configurable input and output formats
- Add support for larger datasets and multiple input files

## Author

**Akash G**

GitHub: [AkashG-03](https://github.com/AkashG-03)
