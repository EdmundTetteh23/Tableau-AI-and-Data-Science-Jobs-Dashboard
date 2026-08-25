# AI & Data Science Salary & Employment Intelligence (2026)
A multi-dimensional Tableau intelligence project designed to evaluate global compensation benchmarks and experience-based salary distributions in AI and Data Science. The project transforms a monolithic job dataset into a star-schema relational model to help job applicants benchmark market rates, and negotiate salaries effectively.

## Table of Contents
- [Overview](#overview)
- [Problem Statement and Project Objectives](#Problem-Statement-and-Project-Objectives)
- [Data Pipeline and Architecture](#Data-Pipeline-and-Architecture)
- [Data Transformation and Cleaning](#Data-Transformation-and-Cleaning)
- [Data Model and Relationships](#Data-Model-and-Relationships)
- [Core DAX Measures and Formulas](#Core-DAX-Measures-and-Formulas)
- [Dashboards and Visualizations](#Dashboards-and-Visualizations)
- [Key Business Insights](#Key-Business-Insights)
- [Strategic Recommendations](#Strategic-Recommendations)
- [Tech Stack](#Tech-Stack)

## Overview
Navigating compensation in AI and Data Science is challenging due to rapid role evolution, regional pay disparities, and varying company sizes. This project builds a centralized business intelligence model using Tableau, transforming unorganized flat file job records into a structured data warehouse schema. The solution allows job seekers and professionals to filter compensation distributions dynamically across geographic locations, experience tiers, and industry sectors.

## Problem Statement
AI and Data Science job applicants frequently lack transparent visibility into baseline salaries and realistic compensation benchmarks across different markets. Without standardized salary insights, candidates struggle to evaluate job offers, and determine appropriate compensation expectations during interview negotiations, leading to significant salary undervaluation.

## Project Objectives
- Compensation Benchmarking: Provide transparent salary insights across global regions, experience levels, and job titles.
- Geographic Pay Transparency**: Measure compensation variations across company locations.
- Role & Industry Profiling: Evaluate salary distributions across distinct industries, and primary technical skill requirements to pinpoint high-paying sectors.
- Career Trajectory & Experience Mapping: Track level experience, management responsibilities, and specialized education correlate with baseline pay and total compensation growth.

## Data Transformation and Cleaning
To prepare the flat dataset (`ai_ds_job_salaries_2026`) for optimal modeling and star-schema integration, several Power Query ETL transformations were applied:

- Schema Decomposition: Deconstructed the single, dense flat table into a central fact table (`fact_jobs`) and 9 dedicated lookup dimension tables to eliminate data redundancy and enhance report performance.
- Geographic Code Expansion: Standardized two-letter ISO country codes in `company_location` and `employee_residence` fields into full country names to improve map visualization readability.
<img width="1366" height="768" alt="country_loc" src="https://github.com/user-attachments/assets/3a1b4a30-e3e4-48ca-a64e-e319b28adab9" />

- Surrogate Key Generation: Created unique index keys across all dimension tables to establish clean one-to-many dimensional relationships.

---

## Data Model and Relationships
The transformed data architecture follows a clean Star Schema built inside Tableau's Logical Layer, centering around fact_jobs with one-to-many single-direction relationships to all supporting dimensions:

- fact_jobs: Core transactional fact table recording financial metrics and quantitative attributes (`salary_usd`, `bonus_pct`, `equity_offered_pct`, `certifications_count`, `job_satisfaction_score`, `manages_people`, `remote_ratio`, `team_size`, `weekly_hours`).
- dim_company_location: Lookup table mapping employer geography (comp_loc_id, company_loc, company_location).
- dim_company_size: Classification table for employer scale (cmp_size_id, cmp_size, company_size).
- dim_emp_residence: Lookup table tracking candidate residence geography (emp_residence_id, emp_residence, employee_residence).
- dim_employment_type: Employment status lookup (emp_type_id, employment_type).
- dim_experience_level: Experience tier lookup (exp_lvl_id, experience_level).
- dim_job_title: Master job taxonomy table (job_id, job_title).
- dim_industry: Business sector directory (industry_id, industry).
- dim_primary_skill: Technical proficiency lookup (primary_lang_id, primary_language).
- dim_education_level: Academic qualification directory (edu_level_id, education_level).

## Tech Stack
- Data Cleaning & ETL: Power Query Excel
- Data Modeling: Tableau Logical Layer
- Calculations and Metrics: Tableau Calculated Fields and Dynamic Parameters
- Visualization: Tableau Desktop
