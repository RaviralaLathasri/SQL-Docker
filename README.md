#  step1: Folder structure
ny_taxi_project/
│
├── docker-compose.yml 

#  step2: Start Docker Container
docker compose up -d
docker ps

#  step3: open Jyputer Notebook in browser
http://localhost:8888
docker logs <jupyter_container_name>     # we can get token id from this command

#  step4: Create notebook in jyputerNotebook and uplode files
https://d37ci6vzurychx.cloudfront.net/misc/taxi_zone_lookup.csv
https://github.com/DataTalksClub/nyc-tlc-data/releases/download/yellow/yellow_tripdata_2021-01.csv.gz

#  step5: Load data in Jyputer NOtebook

#  step6: Open Pgadmin in browser and connect PostgreSQL server



