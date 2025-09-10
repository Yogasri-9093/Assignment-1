# Assignment 1 – Docker Compose Project

## Course
Cloud Computing for Data Analysis (ITCS 6190/8190, Fall 2025)  
Instructor: Prof. Marco Vieira  

---

## Project Overview
This project demonstrates a **two-service Docker Compose setup**:

- **Database Service (PostgreSQL)**  
  - Preloaded with a `trips` table and sample data from `init.sql`.  

- **Python App Service**  
  - Connects to the PostgreSQL database.  
  - Runs queries and computes statistics.  
  - Writes results into `/out/summary.json`.  

This assignment introduces **multi-container workflows**, **service networking**, **environment variables**, and **reproducible setups** using Docker.

---

## Requirements
- Docker Desktop  
- Docker Compose (comes with Docker Desktop)  
- Git & GitHub  

---

## Project Structure
.
├── app/
│ ├── Dockerfile
│ └── main.py
├── db/
│ ├── Dockerfile
│ └── init.sql
├── out/ # JSON results appear here
├── compose.yml
└── Makefile

--

## How to Run

### 1. Build and Start Services
```bash
make up
2. Stop Services
make down
3. Clean and Reset Everything
make clean
Example Output
After running make up, you should see output in the terminal and in out/summary.json:
{
  "total_trips": 6,
  "avg_fare_by_city": [
    {
      "city": "Charlotte",
      "avg_fare": 16.25
    },
    {
      "city": "New York",
      "avg_fare": 19.0
    },
    {
      "city": "San Francisco",
      "avg_fare": 20.25
    }
  ],
  "top_by_minutes": [
    {
      "city": "San Francisco",
      "minutes": 28,
      "fare": 29.3
    },
    {
      "city": "New York",
      "minutes": 26,
      "fare": 27.1
    },
    {
      "city": "Charlotte",
      "minutes": 21,
      "fare": 20.0
    }
  ]
}
Troubleshooting
Database not ready
Run:
make clean && make up
Port already in use (5432)
Edit compose.yml and change:
ports:
  - "5433:5432"
Permission errors on out/ folder
Delete and recreate the out/ folder with proper permissions:
rm -rf out && mkdir out
Reflection
In this assignment, I learned how to:
Set up and manage a multi-container system with Docker Compose.
Use environment variables, health checks, and service networking between containers.
Ensure reproducibility with a Makefile and a clear README.
The most useful part was understanding how containers communicate and how to automate workflows.
For future improvements, I would:
Add more complex SQL queries for deeper analysis.
Optimize images by using smaller base images to reduce build size.
Author
Yogasri Lella
