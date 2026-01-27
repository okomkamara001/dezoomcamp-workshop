# 01. Understanding Docker First Run

docker run with the python:3.13 in an interactive mode, use the entrypoint bash.

> **Version pip 25.3**

#### docker run -it --entrypoint=bash python:3.13

# 02. Understanding Docker networking and docker-compose
   Given the docker-compose.yaml, what is the hostname and port that pgadmin should use to connect to the postgres database?

```
services:
  db:
    container_name: postgres
    image: postgres:17-alpine
    environment:
      POSTGRES_USER: 'postgres'
      POSTGRES_PASSWORD: 'postgres'
      POSTGRES_DB: 'ny_taxi'
    ports:
      - '5433:5432'
    volumes:
      - vol-pgdata:/var/lib/postgresql/data

  pgadmin:
    container_name: pgadmin
    image: dpage/pgadmin4:latest
    environment:
      PGADMIN_DEFAULT_EMAIL: "pgadmin@pgadmin.com"
      PGADMIN_DEFAULT_PASSWORD: "pgadmin"
    ports:
      - "8080:80"
    volumes:
      - vol-pgadmin_data:/var/lib/pgadmin

volumes:
  vol-pgdata:
    name: vol-pgdata
  vol-pgadmin_data:
    name: vol-pgadmin_data
```

> db:5433

**EXPLANATION** <br>
Docker Compose automatically create network for the services and run multiple containers defined int the docker-compose.yaml. The containers can communicate with each other using their service host names as hostname

The hostname for pgAdmin to connect to PostgreSQL database is the service name of the db container, which is db. Docker setup internal DNS so container can resolve each other service names.

The internal port of the PostgreSQL (5432) is what pgAdmin should use to connect. The 5432 port specified in the ports sections is only for external excess of the PostgreSQL from your host Machine.


# 03. Counting short trips
For the trips in November 2025 (lpep_pickup_datetime between '2025-11-01' and '2025-12-01', exclusive of the upper bound), how many trips had a trip_distance of less than or equal to 1 mile?

> 8007

```SELECT 
  COUNT(1)
FROM 
  green_taxi_data t
WHERE
  CAST(t.lpep_pickup_datetime AS DATE) >= '2025-11-01' AND 
  CAST(t.lpep_pickup_datetime AS DATE) <= '2025-12-01' AND
  CAST(t.lpep_dropoff_datetime AS DATE) >= '2025-11-01' AND
  CAST(t.lpep_dropoff_datetime AS DATE) <= '2025-12-01' AND
  t.trip_distance <=1
```

# 04. Longest trip for each day
Which was the pick up day with the longest trip distance? Only consider trips with trip_distance less than 100 miles (to exclude data errors).

> 2025-11-20

# 05. Biggest pickup zone

Which was the pickup zone with the largest total_amount (sum of all trips) on November 18th, 2025?

> East Harlem South

# 06. Longest Trip
For the passengers picked up in the zone named "East Harlem North" in November 2025, which was the drop off zone that had the largest tip?

Note: it's tip , not trip. We need the name of the zone, not the ID.

> JFK Airport

# 07. Terraform Workflow

Which of the following sequences, respectively, describes the workflow for:

Downloading the provider plugins and setting up backend,
Generating proposed changes and auto-executing the plan
Remove all resources managed by terraform`



