# Hoen Scanner

A Dropwizard-based microservice that serves rental car and hotel search results by city.

## What was accomplished

- Set up the local development environment with IntelliJ and OpenJDK
- Created `Search` class with a serialisable `city` field using Jackson `@JsonProperty`
- Created `SearchResult` class with serialisable `city`, `kind`, and `title` fields
- Loaded `rental_cars.json` and `hotels.json` into a combined list of search results in `HoenScannerApplication.run()`
- Created `SearchResource` with a POST `/search` endpoint that filters results by city
- Registered the resource in the application's `run` method
- Tested the API using Postman with POST requests to `localhost:8080/search`

## Running the application

```
mvn clean package
java -jar target/hoen-scanner-1.0-SNAPSHOT.jar server config.yml
```
Sometimes the port 8080 could be already in use. You can use the command below to pkill the application and new build. 
```
sudo kill $(sudo lsof -t -i:8080) 
```
## Example request

```
POST localhost:8080/search
Content-Type: application/json

{"city": "petalborough"}
```