# Heart-Disease-Predictive-Analytics-Pipeline

This repository contains a scalable, automated data engineering pipeline developed using Apache Spark (PySpark) to ingest, clean, standardize, and analyze clinical heart disease records[cite: 4]. By standardizing clinical outcomes into universally recognized ICD-10 codes and leveraging distributed in-memory computing, this project provides a reproducible framework for clinical decision support systems[cite: 4].

## Project Architecture
* **Data Ingestion & Transformation:** Utilizes PySpark to ingest the UCI Cleveland Heart Disease dataset (CSV), enforcing an explicit schema and handling missing values by replacing '?' characters with `None` and dropping them[cite: 2, 4]. The pipeline binarizes diagnostic labels and maps them to standardized ICD-10 clinical codes: `I25.1` for atherosclerotic heart disease and `Z00.0` for general medical examination[cite: 2, 4].
* **Data Lakehouse Storage:** The processed dataset is exported to local storage as an Apache Parquet columnar format (`heart_disease_lakehouse`) using an overwrite mode[cite: 2, 4]. This architecture significantly reduces storage footprints, provides ACID-like durability, and accelerates read performance for downstream analytics[cite: 4].
* **Machine Learning (Spark MLlib):** A Random Forest Classifier configured with 100 trees and a fixed seed (`seed=42`) is trained using an 80/20 train-test split[cite: 2]. The model evaluates heterogeneous risk features—including age, sex, resting blood pressure, cholesterol, and maximum heart rate—achieving an overall predictive accuracy of 84.78%[cite: 2, 4].
* **Business Intelligence:** An interactive Power BI dashboard leverages the curated Lakehouse Gold dataset to visualize diagnostic distributions, patient risk clusters, and physiological trends[cite: 4].

## Repository Structure
* `/src`: Contains the primary PySpark pipeline implementation (`.ipynb`), which handles `SparkSession` initialization, data cleaning, feature assembly via `VectorAssembler`, and model evaluation[cite: 2]. 
* `/docs`: Includes the comprehensive project manuscript, `REPORT.docx` ("Scalable Data Pipeline for Heart Disease Predictive Analytics Regional Health Trend Harmonization"), which details the methodology, system design, and literature review[cite: 4].
* `/dashboard`: Houses the Power BI layout and metadata files used to render the executive clinical decision-making dashboard[cite: 3, 4].

## Technologies Used
* **Data Processing & Engineering:** Apache Spark, PySpark[cite: 2, 4]
* **Machine Learning:** Spark MLlib[cite: 2, 4]
* **Storage:** Data Lakehouse, Apache Parquet[cite: 2, 4]
* **Visualization:** Power BI[cite: 4]

## Author
**Jeanette Hauw Chandra**  
Data Engineering, Faculty of Computing  
Universiti Teknologi Malaysia (UTM), Johor Bahru, Malaysia[cite: 4]
