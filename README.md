# MongoDB European Restaurants Dataset Analysis

## Overview
This project is part of the **Big Data Management** course at the **University of Piraeus**. It involves processing and analyzing a large-scale dataset of European restaurants using **MongoDB**. The dataset, sourced from TripAdvisor, contains over **1,083,397 records** with detailed information about restaurants, including **location, cuisine types, operating hours, average ratings, and review counts**.

## Objectives
The project focuses on the following key areas:
- **Data Ingestion:** Importing the dataset into a MongoDB instance running in a Docker container.
- **Data Retrieval:** Querying the database to extract meaningful insights.
- **Query Optimization:** Enhancing query performance using indexing strategies.

## Technologies Used
- **MongoDB**: NoSQL database for data storage and querying.
- **Docker**: Containerized environment for MongoDB instance.
- **PowerShell & Bash**: Command-line interfaces for managing Docker and MongoDB operations.

## Project Structure
1. **Data Ingestion**
   - Copy dataset to Docker container.
   - Import data into MongoDB using `mongoimport`.
   - Verify data integrity and completeness.
2. **Data Retrieval**
   - Implement various queries to extract restaurant insights.
   - Filter, sort, and aggregate data based on specific criteria.
3. **Query Optimization**
   - Analyze query execution plans.
   - Implement indexes to improve query performance.
   - Compare performance before and after optimization.

## Key Queries & Insights
- **Top-rated vegan-friendly breakfast restaurants in Athens.**
- **Most popular cuisines among vegan-friendly restaurants.**
- **Cities outside Greece with the highest number of Greek restaurants.**
- **City with the highest number of highly-rated restaurants.**
- **Greek regions with the most top-rated restaurants.**

## Query Performance Optimization
- Used `.explain(ExecutionStats)` to analyze query execution plans.
- Implemented indexes on frequently queried fields to reduce execution time from **hundreds of milliseconds to single-digit milliseconds**.
- Improved efficiency by switching from **full collection scans (COLLSCAN) to indexed scans (IXSCAN)**.

## How to Run the Project
1. **Setup MongoDB in Dock**

   Must have Docker Desktop installed. https://docs.docker.com/get-started/get-docker/

   Dataset Here https://imisathena-my.sharepoint.com/personal/stavmars_imis_athena-innovation_gr/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Fstavmars%5Fimis%5Fathena%2Dinnovation%5Fgr%2FDocuments%2Fmongo%5Flab%5Fproject%2Ftripadvisor%5Feuropean%5Frestaurants%2Ezip&parent=%2Fpersonal%2Fstavmars%5Fimis%5Fathena%2Dinnovation%5Fgr%2FDocuments%2Fmongo%5Flab%5Fproject&ga=1

3. **Run MongoDB as a Docker Container**
   ```powershell
   docker run -d -p 27017:27017 --name MONGO_CONTAINER mongo:latest
   ```

4. **Setup MongoDB in Docker**
   ```bash
   docker run --name MONGO_CONTAINER -d mongo
   ```
5. **Copy Dataset to Container**
   ```powershell
   docker cp path/to/tripadvisor_european_restaurants.json MONGO_CONTAINER:/tmp/
   ```
6. **Import Data into MongoDB**
   ```bash
   docker exec -it MONGO_CONTAINER bash
   mongoimport --db TripAdvisor --collection restaurants --file /tmp/tripadvisor_european_restaurants.json --jsonArray
   ```
7. **Run Queries in MongoDB Shell**
   ```bash
   mongosh
   use TripAdvisor
   db.restaurants.find().limit(5).pretty()
   ```

## Conclusion
This project demonstrates the power of **MongoDB** in handling large-scale datasets efficiently. Through **indexing and query optimization**, we significantly improved performance, making complex queries **faster and more scalable**. The insights derived from the dataset provide valuable information about restaurant trends across Europe.

## Author
**Michalis Koveos**  
University of Piraeus  
Email: mixalis.koveos@gmail.com  

## License
This project is for educational purposes only.

