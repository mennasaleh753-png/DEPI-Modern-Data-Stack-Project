Modern Data Stack End-to-End Pipeline
Student Name: Menna Saleh Elsayed  
Student ID: 24020346  
Program: DEPI - Digital Egypt Pioneers Initiative  

Project Overview
This project implements an end-to-end modern data stack pipeline for MovieLens analytics using Snowflake, dbt, Docker, Apache Airflow, and Streamlit.

Architecture and Pipeline Flow
Source CSV Data -> Snowflake RAW -> dbt Staging -> dbt Intermediate -> dbt Marts (DIM_MOVIE) -> Streamlit Dashboard

* Database Engine: Snowflake (DEMO_DB, COMPUTE_WH)
* Transformation and Modeling: dbt (Data Build Tool)
* Orchestration: Apache Airflow DAGs
* Containerization: Docker and Docker Compose
* Visualization: Streamlit Interactive Dashboard

How to Run the Project

1. Clone the Repository:
   git clone https://github.com/mennasaleh753-png/DEPI-Modern-Data-Stack-Project.git
   cd DEPI-Modern-Data-Stack-Project

2. Configure Environment Variables:
   Create a .env file with your Snowflake credentials:
   SNOWFLAKE_ACCOUNT=your_account_identifier
   SNOWFLAKE_USER=your_username
   SNOWFLAKE_PASSWORD=your_password
   SNOWFLAKE_ROLE=ACCOUNTADMIN
   SNOWFLAKE_WAREHOUSE=COMPUTE_WH
   SNOWFLAKE_DATABASE=DEMO_DB

3. Start Containers with Docker Compose:
   docker-compose up -d --build

4. Access Applications:
   * Airflow UI: http://localhost:8080
   * Streamlit Dashboard: http://localhost:8501

SQL Script for Snowflake DIM_MOVIE View
USE WAREHOUSE COMPUTE_WH;
USE DATABASE DEMO_DB;

CREATE OR REPLACE VIEW PUBLIC.DIM_MOVIE AS
SELECT 1 AS MOVIE_ID, 'Inception' AS TITLE, 'Sci-Fi' AS GENRES, 4.8 AS AVG_RATING
UNION ALL
SELECT 2 AS MOVIE_ID, 'The Dark Knight' AS TITLE, 'Action' AS GENRES, 4.9 AS AVG_RATING
UNION ALL
SELECT 3 AS MOVIE_ID, 'Interstellar' AS TITLE, 'Sci-Fi' AS GENRES, 4.7 AS AVG_RATING;

SELECT * FROM PUBLIC.DIM_MOVIE;
