# PDF to Text Parsing and Storing Data to SQL DB

This project provides a solution for extracting data from bank statements in PDF format and storing the parsed data into a structured SQL database. The project employs Python libraries to read, clean, process, and finally load the data into a MySQL database.

## Problem Statement

When dealing with PDF bank statements, extracting meaningful data for analysis can be cumbersome. This project simplifies this process by automatically extracting the transaction details, processing them into a structured format, and storing them into an SQL database, making it easier for further analysis or integration with other data systems.

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Setup and Installation](#setup-and-installation)
- [Project Workflow](#project-workflow)
- [Database Schema](#database-schema)
- [Usage](#usage)
- [Contributing](#contributing)

## Features

- Extracts text data from PDF bank statements.
- Cleans and processes extracted text into a structured format.
- Identifies transaction details such as date, particulars, debit, credit, and balance.
- Assigns unique IDs to each transaction and classifies them as "Credit" or "Debit."
- Stores the cleaned data into a MySQL database.
- Outputs the data in JSON format as well for further use.

## Technologies Used

- **Python Libraries**: PyPDF2, Pandas, uuid, json, mysql-connector-python
- **Database**: MySQL

## Setup and Installation

### Prerequisites

- Python 3.x
- MySQL Server
- Required Python packages: PyPDF2, pandas, mysql-connector-python

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/gaurav190901/pdf-to-sql-parser.git
   ```
2. Install the required packages:
   ```bash
   pip install PyPDF2 pandas mysql-connector-python
   ```
3. Ensure MySQL is installed and running on your machine.

## Project Workflow

1. **Extract Text from PDF**: Reads PDF files and extracts text content line by line.
2. **Remove Unnecessary Data**: Removes unwanted rows (headers) from the extracted data.
3. **Process Transaction Data**: Parses transaction details such as date, description, debit, credit, and total balance.
4. **Assign Unique IDs**: Generates unique IDs for each transaction.
5. **Data Transformation**: Prepares data for insertion into the database.
6. **Database Storage**: Creates the MySQL database and table, then inserts transaction data into the SQL table.

## Database Schema

The SQL table structure used for storing transaction data:

| Column           | Data Type     | Description                  |
|------------------|---------------|------------------------------|
| `unique_id`      | CHAR(36)      | Unique identifier for each transaction |
| `date`           | DATE          | Date of the transaction      |
| `description`    | TEXT          | Transaction particulars      |
| `amount`         | DECIMAL(10,2) | Amount credited/debited      |
| `transaction_type` | ENUM('CREDIT', 'DEBIT') | Type of transaction |

## Usage

### 1. Extracting Text from PDF

Use the `extract_text_from_pdf` function to extract text from a PDF:
```python
pdf_text = extract_text_from_pdf(r"sample_bank_statement.pdf")
```

### 2. Processing Data

Remove unwanted rows and split transaction details:
```python
pdf_lines_cleaned = remove_first_rows(pdf_text, 15)
```

### 3. Storing Data in SQL Database

Create a MySQL database and table, and then insert data:
```python
create_database_and_table()
insert_dataframe(df1)
```

### 4. Exporting to JSON

Save the parsed data into a JSON file:
```python
df.to_json('transaction_output.json', orient='records', lines=True)
```

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Create a pull request.

