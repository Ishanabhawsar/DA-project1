
# DA-project1: Data Cleaning with Python, Pandas & NumPy

A beginner-friendly data cleaning project that takes a deliberately messy, hand-built employee dataset and turns it into a clean, consistent table using plain Python, Pandas and NumPy.

## Overview

Real-world data is rarely tidy. This project simulates that by starting with a small dataset full of common problems: inconsistent casing, stray whitespace, impossible ages, salaries stored as text with currency symbols, malformed emails, missing values and duplicate rows. The script then fixes each problem step by step.

## Dataset

The dataset is defined directly in the script as a Python dictionary (15 records) with these columns:

| Column | Issues present |
|--------|----------------|
| `Name` | Mixed case, extra spaces, missing values, duplicates (`Rahul` / `rahul`) |
| `Age` | Missing values, negative and unrealistic values (`-5`, `150`, `200`) |
| `City` | Mixed case, extra spaces, empty strings, missing values |
| `Salary` | Stored as strings, with commas and the `₹` symbol, empty or missing |
| `Email` | Missing domains, wrong formats, mixed case, empty or missing |

## Cleaning Steps

1. **Age**: values below 18 are set to 18 and values above 65 are set to 65. Missing ages are filled with the (integer) mean age.
2. **Salary**: removes `₹` and commas, converts to integers, turns empty strings into missing values, then fills missing salaries with the mean salary.
3. **City**: trims whitespace, standardizes capitalization (`bhopal`, `BHOPAL` become `Bhopal`), and fills empty or missing cities with `Unknown`.
4. **Email**:
   - trims whitespace and lowercases
   - fixes incomplete domains (`aman@gmail` becomes `aman@gmail.com`, `amitgmail.com` becomes `amitgmail.com@gmail.com`)
   - keeps valid `@yahoo.com` addresses
   - discards emails that are 20 characters or longer as invalid
   - rebuilds missing emails from the person's name (`name@gmail.com`)
5. **Name**: trims whitespace, capitalizes, and fills missing names from the email username. Names are then kept consistent with the email username.
6. **Duplicates**: removes duplicate rows with `drop_duplicates()` and resets the index.
7. **Types**: converts `Age` to an integer column once missing values are filled.

## Tech Stack

- Python 3
- [Pandas](https://pandas.pydata.org/)
- [NumPy](https://numpy.org/)

## Project Structure

```
DA-project1/
├── project1.py   # Full cleaning script
├── project2.py   # Notebook-style version of the same pipeline (ends by displaying the DataFrame)
├── LICENSE       # MIT License
└── README.md
```

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/AnimeshSharma0425/DA-project1.git
   cd DA-project1
   ```
2. Install the dependencies:
   ```bash
   pip install pandas numpy
   ```
3. Run the script:
   ```bash
   python project1.py
   ```
   Add `print(df)` at the end of the script to see the cleaned DataFrame, or paste the code into a Jupyter notebook (as in `project2.py`) to display it directly.

## What You'll Learn

- Handling missing values with the mean and with placeholder values
- Cleaning and converting text columns with string methods
- Detecting and clipping outliers (invalid ages)
- Removing duplicate records
- Deriving missing values from related columns
- Changing column data types in Pandas

## License

This project is licensed under the [MIT License](LICENSE).

## Author

[Animesh Sharma](https://github.com/AnimeshSharma0425)
