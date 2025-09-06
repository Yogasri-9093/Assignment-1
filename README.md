Assignment 1

Cloud Computing for Data Analysis (ITCS 6190/8190, Fall 2025)

Overview

This project demonstrates a simple two-service Docker Compose setup:

- Database service (PostgreSQL) seeded with a trips table and sample data.
  
- Python app service that connects to the database, runs queries, computes statistics, and writes results to /out/summary.json.
  
This assignment introduces Docker multi-container workflows, service networking, environment variables, and reproducible setups.

Requirements

- Docker Desktop
- Docker Compose (included with Docker Desktop)
- Git & GitHub

Project Structure
.
├── app/
│   ├── Dockerfile
│   └── main.py
├── db/
│   ├── Dockerfile
│   └── init.sql
├── out/               # JSON results appear here
├── compose.yml
└── Makefile

How to Run

Build and start everything:
make up

Stop services:
make down

Clean and reset:
make clean

Example Output
After running make up, you should see something like this in your terminal and in out/summary.json:

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

- Database not ready → Run `make clean` then `make up` again.
  
- Port already in use → Change `5432:5432` in compose.yml to `5433:5432`.
  
- Permission errors on out/ → Delete and recreate the out/ folder with correct permissions.

Reflection

In this assignment, I learned how to set up and manage a multi-container system with Docker Compose, 

including a database and an application service. I practiced using environment variables, health checks, 

and service networking. The most useful part was learning how to ensure reproducibility with a Makefile 

and a clear README. If I were to improve this project, I would add more complex queries and containerize 

with smaller base images to optimize build size.

