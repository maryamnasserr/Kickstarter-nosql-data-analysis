# Kickstarter NoSQL Data Analysis (MongoDB & Cassandra)

## Overview
This project analyzes Kickstarter crowdfunding project data using two NoSQL database systems: MongoDB and Cassandra. The goal is to preprocess and engineer meaningful features from raw project data, then implement analytical queries across both database models to compare their suitability for large-scale structured and semi-structured data analysis.

The dataset includes project-level attributes such as funding goals, pledged amounts, categories, launch dates, and final project states.

## Dataset
The dataset contains Kickstarter project records with the following attributes:
- Project ID and name
- Category and main category
- Funding goal and pledged amounts
- Currency and country
- Launch and deadline dates
- Number of backers
- Project state (successful, failed, canceled, etc.)
- USD-normalized goal and pledged values

## Project Objectives
- Perform data exploration and preprocessing on raw Kickstarter data
- Clean and transform dataset for analytical use
- Engineer meaningful features for deeper insights
- Design and implement schemas in MongoDB and Cassandra
- Execute analytical queries across both database systems
- Compare NoSQL modeling approaches

## Technologies Used
- Python
- Pandas
- MongoDB
- Apache Cassandra
- NoSQL data modeling
- Jupyter Notebook

## Project Workflow

### 1. Data Exploration & Preprocessing
The dataset was explored to understand structure, missing values, and inconsistencies. The following preprocessing steps were applied:
- Handling missing values
- Removing duplicate records
- Filtering out projects with state = "live"
- Ensuring consistency in numeric and date fields

### 2. Feature Engineering
New features were created to enhance analytical capabilities:

- **CampaignDuration (days)**  
  Difference between deadline and launch date

- **FundingRatio**  
  usd_pledged_real / usd_goal_real

- **GoalCategory**
  - Low Goal: < $10,000  
  - Medium Goal: $10,000 – $100,000  
  - High Goal: > $100,000  

- **LaunchMonth**  
  Extracted month from launch date

## Data Modeling

### MongoDB (Document Model)
The dataset was stored as a document-based structure in MongoDB. Each project is represented as a document containing all attributes and engineered fields.

### Cassandra (Wide-Column Model)
The dataset was modeled using a wide-column structure. Partition keys and clustering keys were designed to support efficient querying based on category, country, and project state.

Schema design decisions were made to optimize query performance for analytical workloads.

## Analysis Performed

The following analytical queries were implemented in both MongoDB and Cassandra:

- Success rate per main category
- Countries with highest average pledged amount (USD)
- Top 5 projects by funding ratio
- Category with highest number of failed projects
- Average campaign duration (successful vs failed)
- Month with highest number of successful projects
- Average number of backers per main category
- Percentage of projects meeting or exceeding funding goals

## Key Findings
- Funding success varies significantly across categories and countries
- Campaign duration shows variation between successful and failed projects
- A small number of projects achieve exceptionally high funding ratios
- Seasonal trends can be observed in successful project launches

## Repository Contents
```text
├── CasandraKS.ipynb
├── MongoKS.ipynb
└── README.md
