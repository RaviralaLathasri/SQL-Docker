# NY Taxi Data Engineering Project (Docker + Jupyter + PostgreSQL)

## Project Overview

This project shows how to use Docker to run Jupyter Notebook, PostgreSQL, and pgAdmin, and load NYC Yellow Taxi data into PostgreSQL.

---

## Folder Structure

```
ny_taxi_project/
│
├── docker-compose.yml
├── data/
│   ├── taxi_zone_lookup.csv
│   └── yellow_tripdata_2021-01.csv.gz
└── notebooks/
    └── load_data.ipynb
```

---

## Step 1: Prerequisites

Make sure these are installed:

* Docker
* Docker Compose
* Web Browser

Check installation:

```bash
docker --version
docker compose version
```

---

## Step 2: Start Docker Containers

From project root folder:

```bash
docker compose up -d
```

Check running containers:

```bash
docker ps
```

---

## Step 3: Open Jupyter Notebook

Get Jupyter token:

```bash
docker logs <jupyter_container_name>
```

Open browser:

```
http://localhost:8888
```

Paste the token when asked.

---

## Step 4: Upload Data Files

Download and upload these files into the `data/` folder in Jupyter:

Taxi zone lookup:

```
https://d37ci6vzurychx.cloudfront.net/misc/taxi_zone_lookup.csv
```

Yellow taxi data:

```
https://github.com/DataTalksClub/nyc-tlc-data/releases/download/yellow/yellow_tripdata_2021-01.csv.gz
```

---

## Step 5: Load Data in Jupyter Notebook

Create a new notebook and run the following code:

```python
import pandas as pd
from sqlalchemy import create_engine

engine = create_engine(
    "postgresql://postgres:postgres@postgres:5432/ny_taxi"
)

df = pd.read_csv("data/yellow_tripdata_2021-01.csv.gz")
df.to_sql("yellow_taxi_data", engine, if_exists="replace", index=False)
```

---

## Step 6: Open pgAdmin and Connect PostgreSQL

Open browser:

```
http://localhost:5050
```

Login:

* Email: [admin@admin.com](mailto:admin@admin.com)
* Password: admin

Register Server:

* Host: postgres
* Port: 5432
* Username: postgres
* Password: postgres
* Database: ny_taxi

---

## Verify Data

Run this query in pgAdmin:

```sql
SELECT * FROM yellow_taxi_data LIMIT 10;
```

---

## Final Output

* Docker containers running
* Data loaded into PostgreSQL
* Accessible via pgAdmin
* Analysis ready in Jupyter

---

## Next Steps

* Join taxi zones table
* Write analytical SQL queries
* Automate ingestion using Python scripts
* Add indexes for performance


