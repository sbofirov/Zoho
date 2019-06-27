# Zoho

### How to start
Just execute docker-compose up. When container is ready and running application will be available at https://localhost:8443
Please be patient, it takes some time to start the server.

### Configuration
"Alias URL to access the application" is random hash and must be changed!

Go to Settings > Advanced Settings > Alias URL to access the application

### Database
Usually PostgreSQL files are mounted under /home/<your-username>/docker/docker/volumes/zoho_data-postgre/_data
DB credentials are different on every installation. They could be found in container /app/Analytics/ColDB/conf/coldb.properties

* userName=postgres
* password=varies
* databaseName=zreportsdb
* port=33366
