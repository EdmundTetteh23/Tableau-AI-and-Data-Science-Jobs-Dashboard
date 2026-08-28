# AI & Data Science Salary & Employment Intelligence (2026)
A multi-dimensional Tableau intelligence project designed to evaluate global compensation benchmarks and experience-based salary distributions in AI and Data Science. The project transforms a monolithic job dataset into a star-schema relational model to help job applicants benchmark market rates, and negotiate salaries effectively.

## Table of Contents
- [Overview](#overview)
- [Problem Statement and Project Objectives](#Problem-Statement-and-Project-Objectives)
- [Data Pipeline and Architecture](#Data-Pipeline-and-Architecture)
- [Data Transformation and Cleaning](#Data-Transformation-and-Cleaning)
- [Data Model and Relationships](#Data-Model-and-Relationships)
- [Tableau Calculations and Business Logic](#Tableau-Calculations-and-Business-Logic)
- [Dashboards and Visualizations](#Dashboards-and-Visualizations)
- [Key Insights](#Key-Insights)
- [Strategic Recommendations](#Strategic-Recommendations)
- [Tech Stack](#Tech-Stack)

## Overview
Navigating compensation in AI and Data Science is challenging due to rapid role evolution, regional pay disparities, and varying company sizes. This project builds a centralized business intelligence model using Tableau, transforming unorganized flat file job records into a structured data warehouse schema. The solution allows job seekers and professionals to filter compensation distributions dynamically across geographic locations, experience tiers, and industry sectors.

## Problem Statement and Project Objectives
### Problem Statement
AI and Data Science job applicants frequently lack transparent visibility into baseline salaries and realistic compensation benchmarks across different markets. Without standardized salary insights, candidates struggle to evaluate job offers, and determine appropriate compensation expectations during interview negotiations, leading to significant salary undervaluation.

### Project Objectives
- Compensation Benchmarking: Provide transparent salary insights across global regions, experience levels, and job titles.
- Geographic Pay Transparency**: Measure compensation variations across company locations.
- Role & Industry Profiling: Evaluate salary distributions across distinct industries, and primary technical skill requirements to pinpoint high-paying sectors.
- Career Trajectory & Experience Mapping: Track level experience, management responsibilities, and specialized education correlate with baseline pay and total compensation growth.

## Data Pipeline and Architecture
[Raw Dataset] ➔ [Power Query ETL] ➔ [Star Schema Data Model] ➔ [Calculated Fields & Parameters] ➔ [Interactive Tableau Workbook]

## Data Transformation and Cleaning
To prepare the flat dataset (ai_ds_job_salaries_2026) for optimal modeling and star-schema integration, several Power Query ETL transformations were applied:

- Schema Decomposition: Deconstructed the single, dense flat table into a central fact table (fact_jobs) and 9 dedicated lookup dimension tables to eliminate data redundancy and enhance report performance.
- Geographic Code Expansion: Standardized two-letter ISO country codes in company_location and employee_residence fields into full country names to improve map visualization readability.
<img width="1366" height="768" alt="country_loc" src="https://github.com/user-attachments/assets/3a1b4a30-e3e4-48ca-a64e-e319b28adab9" />

- Surrogate Key Generation: Created unique index keys across all dimension tables to establish clean one-to-many dimensional relationships.

## Data Model and Relationships
The transformed data architecture follows a clean Star Schema built inside Tableau's Logical Layer, centering around fact_jobs with one-to-many single-direction relationships to all supporting dimensions:
<img width="1600" height="900" alt="Tableau DM" src="https://github.com/user-attachments/assets/3a92ec6e-6e86-47e2-969e-d2dcd24162d8" />

- fact_jobs: Core transactional fact table recording financial metrics and quantitative attributes (salary_usd, bonus_pct, equity_offered_pct, certifications_count, job_satisfaction_score, manages_people, remote_ratio, team_size, weekly_hours).

- dim_company_location: Lookup table mapping employer geography (comp_loc_id, company_loc, company_location).

- dim_company_size: Classification table for employer scale (cmp_size_id, cmp_size, company_size).

- dim_emp_residence: Lookup table tracking candidate residence geography (emp_residence_id, emp_residence, employee_residence).

- dim_employment_type: Employment status lookup (emp_type_id, employment_type).

- dim_experience_level: Experience tier lookup (exp_lvl_id, experience_level).

- dim_job_title: Master job taxonomy table (job_id, job_title).

- dim_industry: Business sector directory (industry_id, industry).

- dim_primary_skill: Technical proficiency lookup (primary_lang_id, primary_language).

- dim_education_level: Academic qualification directory (edu_level_id, education_level).

## Tableau Calculations and Business Logic
Analytical logic and metric parameter switching implemented via dynamic Tableau Calculated Fields and Dynamic Parameters.

<img width="558" height="659" alt="Metric Parameter" src="https://github.com/user-attachments/assets/ffa0e715-685d-45ae-826a-52e161b2717c" />

<img width="731" height="427" alt="Metric" src="https://github.com/user-attachments/assets/7febcc70-b16b-47c3-8b08-4804539b5e0a" />

<img width="730" height="426" alt="Job Count" src="https://github.com/user-attachments/assets/18d5f769-a897-4a98-9b3a-325cc2732f18" />

<img width="728" height="428" alt="Avg  Salary" src="https://github.com/user-attachments/assets/42d1486c-3497-4fa7-a0b4-fcbef5b5dea4" />

## Dashboards and Visualizations
The solution features a dynamic dashboard layout controlled by an upper Metric Switcher (Job Count vs. Avg. Salary), allowing job candidates to toggle seamlessly between market demand volume and compensation benchmarks across identical visual categories:
<img width="1600" height="900" alt="Job Count" src="https://github.com/user-attachments/assets/bf1a9e2e-3ef2-4a3f-aa74-12f126fc3ad5" />

<img width="1600" height="900" alt="Avg  Salary" src="https://github.com/user-attachments/assets/561b384d-9067-47d4-b5e3-6a634e88f6f1" />

- Executive KPI Summary: Top-level performance tiles capturing 5.0K Total Jobs, an overall Average Salary of $98.6K, and 12 Distinct Roles.
- Role & Sector Breakdown: Visualizes listings and compensation across 12 distinct job titles (led by Data Scientist with 709 listings; highest paid being Data Science Manager at $114.4K, LLM Engineer at $110.9K, and AI Engineer at $110.9K) and industries (Technology dominating volume with 1,528 listings; Finance leading pay at $111.8K).
- Geographic Compensation Distribution: Regional analysis charting market footprint and compensation across company locations (USA leading with 1,786 jobs and $135.7K avg. salary, followed by Australia at $107.3K and Canada at $102.3K).
- Technical Proficiency Requirements: Demand and pay distribution across primary programming languages (Python dominating demand with 3,129 jobs; Scala and Java commanding the highest average pay at $102.4K and $100.0K).
- Demographic & Employment Structure: Categorizes roles by Education Level (Bachelors leading volume at 1,903 jobs; PhD leading pay at $114.6K), Experience Level (Entry at $61.0K up to Executive at $164.7K), and Employment Type (Full-time dominating with 4,159 listings and $101.7K average pay).

## Key Insights
- High-Value Specialized Roles: Specialized titles like LLM Engineer ($110.9K), AI Engineer ($110.9K), and Machine Learning Engineer ($110.4K) command significantly higher average salaries than generalist roles like Data Analyst ($75.5K) and Business Intelligence Analyst ($75.0K).
- Geographic Pay Premiums: The USA leads both hiring volume (1,786 listings) and compensation ($135.7K), surpassing European hubs (Great Britain at $100.6K, Germany at $96.4K) and emerging markets (India at 782 listings but lower relative local base compensation).
- Python Ubiquity vs. Niche Language Pay: Python is the absolute industry standard for job volume (3,129 postings, over 60% of all roles), but niche languages like Scala ($102.4K) and Java ($100.0K) yield higher average pay due to specialized enterprise pipeline requirements.
- Experience & Academic Returns: Advanced academic credentials (PhD at $114.6K) and senior experience tiers (Senior at $109.7K, Lead at $136.3K, Executive at $164.7K) provide steep salary escalation compared to entry-level baselines ($61.0K).

## Strategic Recommendations
- Target High-Yield Specializations: Candidates aiming to maximize salary negotiation leverage should target specialized LLM, AI, and MLOps engineering tracks rather than general BI analytics roles to capture a $35K + compensation premium.
- Benchmark Regional Parity During Negotiations: Job seekers evaluating remote or cross-border offers should benchmark base pay against US ($135.7K) and Australian ($107.3K) baselines to ensure remote offers reflect true global market value.
- Pair Python Fluency with Enterprise Tools: While Python is mandatory for securing high interview volume, candidates should build proficiency in enterprise pipeline tools (Scala/Java/SQL) to qualify for top-tier salary bands.

## Tech Stack
- Data Cleaning & ETL: Power Query Excel
- Data Modeling: Tableau Logical Layer
- Calculations and Metrics: Tableau Calculated Fields and Dynamic Parameters
- Visualization: Tableau Desktop
