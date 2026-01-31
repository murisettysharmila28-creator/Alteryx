---
# Customer Location Analysis – Roadshow Planning (Alteryx)

## Overview
This lab focuses on **data wrangling and aggregation** using **Alteryx Designer** to support roadshow planning decisions.  
We analyze a dataset of customers across the United States to identify **locations (City, State)** that have **at least 10 customers**, ensuring travel efforts are efficient and impactful.

The goal is to determine:
- How many locations qualify for the roadshow
- How many customers can be reached by visiting only those locations

This workflow demonstrates core Alteryx preparation and transformation techniques. :contentReference[oaicite:0]{index=0}

![Workflow Diagram](Alteryx.png)

---

## Dataset
- **Input file:** `customers.csv`
- **Records:** 1,000 customers
- **Geography:** 300 unique locations across the U.S.
- **Key challenge:** Cities may appear in multiple states, so location must be defined using both City and State. :contentReference[oaicite:1]{index=1}

---

## Workflow Steps

### 1. Input Data
- Load `customers.csv` by either:
  - Dragging and dropping the file directly onto the canvas, or
  - Using the **Input Data** tool and setting up a file connection
- Verify the data preview appears correctly in the configuration window :contentReference[oaicite:2]{index=2}

---

### 2. Data Type Configuration (Select Tool)
- Connect a **Select** tool to the Input Data tool
- Update column data types according to the data dictionary
- Uncheck any unwanted columns to keep only relevant fields
- This step ensures data consistency for downstream processing :contentReference[oaicite:3]{index=3}

---

### 3. Create Location Field (Formula Tool)
- Connect a **Formula** tool to the Select tool
- Add a new column named `Location`
- Use the following expression:
  `[City] + ", " + [State]`

- Add a **Browse** tool and run the workflow to confirm the new column is created correctly :contentReference[oaicite:4]{index=4}

---

### 4. Aggregate Customer Counts (Summarize Tool)
- Add a **Summarize** tool
- Configure it to:
  - Group by `Location`
  - Count the number of customers per location
- Run the workflow to review customer counts for each city–state combination :contentReference[oaicite:5]{index=5}

---

### 5. Filter High-Value Locations (Filter Tool)
- Add a **Filter** tool to the Summarize output
- Keep only records where the customer count is **greater than or equal to 10**
- This step isolates locations that are worthwhile for the roadshow
- Use a **Browse** tool to verify the filtered results
- The output should show **20 locations** with 10 or more customers :contentReference[oaicite:6]{index=6}

---

### 6. Output Final Results
- Add an **Output Data** tool at the end of the workflow
- Save the results as a CSV file (e.g., `output.csv`)
- Verify the data using a Browse tool before saving
- Save the workflow itself as `customers.yxmd` :contentReference[oaicite:7]{index=7}

---

## Output
- CSV file containing only locations with **10 or more customers**
- Aggregated customer counts by `Location`
- A reduced, high-impact set of locations for roadshow planning :contentReference[oaicite:8]{index=8}

---

## Tools Used
- Input Data  
- Select  
- Formula  
- Summarize  
- Filter  
- Browse  
- Output Data  

---

## Key Learning Outcomes
- Combining fields to create meaningful geographic identifiers  
- Grouping and aggregating data using Summarize  
- Filtering datasets based on business rules  
- Validating results at each step using Browse tools  
- Preparing clean, decision-ready outputs in Alteryx :contentReference[oaicite:9]{index=9}

---

## Notes
- Browse tools should be used after each major transformation to validate results
- This workflow emphasizes **data preparation and aggregation**, not predictive modeling
- Designed for academic learning and foundational Alteryx practice :contentReference[oaicite:10]{index=10}

