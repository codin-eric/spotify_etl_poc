# Spotify ETL POC
This POC extract data from the Spotify API, transform the data filtering unwanted records and loads to PG database using Alembic for database versioning.

## Inspired on
Karolina Sowinska - Data Engineering
https://www.youtube.com/playlist?list=PLNkCniHtd0PNM4NZ5etgYMw4ojid0Aa6i

## Extract
I am using the spotify api to extract data from my account
### Get Spotify creds
https://developer.spotify.com/dashboard/login


## Transform
Using pandas I can filter the unwanted records, as you can see you have a loosly time window and I am plainning on running this as tasks of Airflow :P

## Load

## Local postgres db
```
docker run -d --name spoty_etl_pg -v my_dbdata:/var/lib/postgresql/data -p 5432:5432 -e POSTGRES_PASSWORD=postgres -e POSTGRES_USER=postgres -e POSTGRES_DB=spotipy postgres
```
test it with
```
docker exec -it spoty_etl_pg psql -h localhost -U postgres -W spotipy
```

## Alembic
Add alembic to the project
```
alembic init alembic
```

### Known issue
when instaling alembic you might need to also add
```
poetry add psycopg2-binary
```

### Create a Migration Script
```
alembic revision --autogenerate -m "First"
```

### Running our First Migration
```
alembic upgrade head
```