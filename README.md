# exploratory-data-analysis
This project is about exploratory data analysis using MySQL.

Overview

This project focuses on analyzing yearly layoffs across companies and industries using **MySQL**.
The goal of this Exploratory Data Analysis (EDA) is to uncover key trends, identify high-impact industries, and understand how layoffs evolve over time.

---

Dataset Description

The dataset includes company-level yearly layoffs with the following fields:

| Column         | Description                  |
| -------------- | ---------------------------- |
| `company`      | Name of the company          |
| `industry`     | Industry or sector           |
| `country`      | Country of operation         |
| `year`         | Year of reported layoffs     |
|`total_laid_off`| Number of employees laid off |

---

Technologies Used

* **MySQL**
* MySQL Workbench / phpMyAdmin
* CSV for data import

---

Database Setup

### Create Table
```
CREATE TABLE layoffs (
    id INT AUTO_INCREMENT PRIMARY KEY,
    company VARCHAR(255),
    industry VARCHAR(255),
    country VARCHAR(255),
    year INT,
    total_laid_off INT
);

### Import Data
```
LOAD DATA INFILE 'layoffs.csv'
INTO TABLE layoffs
FIELDS TERMINATED BY ','
IGNORE 1 ROWS;

---

## EDA Using SQL

### 📈 Total Layoffs Per Year
```
SELECT year, SUM(total_laid_off) AS total_layoffs
FROM layoffs
GROUP BY year
ORDER BY year;

### Layoffs by Industry
```
SELECT industry, SUM(laid_off) AS total_layoffs
FROM layoffs
GROUP BY industry
ORDER BY total_layoffs DESC;

### Top Companies with Highest Layoffs

```
SELECT company_name, SUM(laid_off) AS total_layoffs
FROM layoffs
GROUP BY company_name
ORDER BY total_layoffs DESC
LIMIT 10;
```

### Layoffs by Country

```
SELECT country, SUM(total_laid_off) AS total_layoffs
FROM layoffs
GROUP BY country
ORDER BY total_layoffs DESC;
```

---

## Key Insights

* Industries with the highest layoff activity
* Years with significant spikes in layoffs
* Companies responsible for the largest layoff totals
* Economic patterns reflected in the data

---

إذا تريد، أقدر أجهّز لك نسخة **منسقة تلقائيًا** كملف جاهز للتحميل، أو أضيف **شعارات + Badges + صور**.

