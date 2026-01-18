# Logs, Linux, & Database QA Exercises (Sprint 6)

# 🗓️Project Details

- **Type:** QA Bootcamp Project (TripleTen LatAm)
- **Execution Date:** May 2025
- **Status:** Completed and Approved
- **Testing Type:** Backend QA – Log Analysis & Database Queries

---

# 📌Project Overview
This project consists of **backend-focused exercises** for log analysis, error handling, and database querying in a QA context.

The objective was to practice **troubleshooting skills** using Linux commands for logs and SQL for data validation, simulating real-world debugging and backend QA scenarios.

Exercises included:
- Log filtering for specific IPs and errors.
- Directory creation and file separation for error logs.
- SQL queries on a Chicago Taxi database for counts, aggregations, classifications, and joins.

---

# 🛠️Tools & QA Techniques
# Tools Used:

- **Linux CLI** – Commands like grep, mkdir for log processing
- **Google Docs** – Documentation of results (e.g., txt files)
- **SQL Client** – Query execution on remote chicago_taxi database
- **Jira** – Potential defect tracking (not required here)

# QA Techniques Applied:

- Command-line filtering and extraction
- Data aggregation and classification
- Query optimization with GROUP BY, HAVING, CASE, JOINs

---

# 🌍Test Environment
- **Remote Server** – Logs in /logs/2019/12/
- **Database** – chicago_taxi DB with tables: neighborhoods, cabs, trips, weather_records

---

# 📋Test Artifacts
The following artifacts were created and documented:

- **Exercise 1: IP Log Filtering**  
  Command: `grep -R "^233.201" logs/2019/12`  
  Sample Logs: Examples of matching entries provided.

- **Exercise 2: Error Log Separation**  
  Commands: `mkdir bug1; mkdir bug1/events`  
  Filtering: `grep '\" [45]00 ' /home/morty/logs/2019/12/apache_2019-12-30.txt > ~/bug1/main.txt`  
  Separation: `grep '\" 400 ' ~/bug1/main.txt > ~/bug1/events/400.txt` and similar for 500.txt  
  400.txt: [https://docs.google.com/document/d/1B5WT8ol7AykZZPEdUNLFGEPWYpNb4wNhpCQSKV1Ae-A/edit?usp=sharing](https://docs.google.com/document/d/1B5WT8ol7AykZZPEdUNLFGEPWYpNb4wNhpCQSKV1Ae-A/edit?usp=sharing)  
  500.txt: [https://docs.google.com/document/d/1_GL119ZKO4JJ3z-iE3kVgjpXN0SiHM4reKbsYIixOz4/edit?usp=sharing](https://docs.google.com/document/d/1_GL119ZKO4JJ3z-iE3kVgjpXN0SiHM4reKbsYIixOz4/edit?usp=sharing)

- **Database Exercise 1: Taxi Count**  
  Query: `SELECT COUNT(DISTINCT vehicle_id) AS total_vehicles FROM cabs;`  
  Result: 5500

- **Database Exercise 2: Taxis per Company**  
  Query: `SELECT company_name, COUNT(DISTINCT vehicle_id) as cnt FROM cabs GROUP BY company_name HAVING COUNT(DISTINCT vehicle_id) < 100 ORDER BY cnt DESC;`  
  Result: List of companies with <100 taxis.
  <img width="452" height="715" alt="image" src="https://github.com/user-attachments/assets/a64b7940-9ba2-42bb-b2b0-ed7b73954706" />


- **Database Exercise 3: Weather Conditions**  
  Query: `SELECT ts, description, CASE WHEN description LIKE '%rain%' THEN 'bad' WHEN description LIKE '%storm%' THEN 'bad' ELSE 'good' END AS weather_conditions FROM weather_records WHERE ts BETWEEN '2017-11-05 00:00:00' AND '2017-11-06 00:00:00';`  
  Result: Table with timestamps and conditions.
  <img width="676" height="490" alt="image" src="https://github.com/user-attachments/assets/e10e2c8a-edfb-45a0-aa7f-052fc8d952be" />


- **Database Exercise 4: Trip Counts**  
  Query: `SELECT cabs.company_name, COUNT(trips.trip_id) as trips_amount FROM cabs LEFT JOIN trips on trips.cab_id = cabs.cab_id WHERE start_ts::date IN ('2017-11-15', '2017-11-16') GROUP BY cabs.company_name ORDER BY trips_amount DESC;`  
  Result: Table with company trip counts.
  <img width="525" height="793" alt="image" src="https://github.com/user-attachments/assets/a7563a11-e51a-475b-9865-a36ec2983da9" />


---

# 🐞Bug Reporting
No formal bugs reported, as this was exercise-based. Focus was on accurate command/query execution and result validation.

---

# 📊Test Metrics
- **Exercises Completed:** 6 (2 Linux, 4 SQL)
- **Successful Outputs:** 100%
- **Key Focus:** Data extraction and query accuracy

---

# 🎯Key Takeaways

- Hands-on experience with Linux CLI for log debugging
- Advanced SQL skills for data analysis and validation
- Practical backend QA techniques for troubleshooting
- Emphasis on precise command and query writing

---

## 🌐 Language Note (Important)

> ⚠️ **Documentation Language Notice**  
All test cases and bug reports for this project were originally created and delivered in **Spanish**, as required by the project guidelines at the time of execution.

To preserve authenticity and avoid misinterpretation, the original documents have been kept in Spanish.  
This README provides a **clear English summary** of the scope, execution, and results for international reviewers.
 of the scope, execution, and results for international reviewers.
