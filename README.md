# issue-mongodb-update-nested-array
Reproducing issue with attempt to update nested array

The DotNet solution reproduces the issue.

## Steps
1. Clone the repo
2. Compile
3. Run an instance of MongoDb at `localhost:27017` with username `root` and password `example`. Use the following `docker-compose.yml` as an example, or tweak the integration test accordingly
```
version: '3.7'
services:
    mongo:
        image: mongo:latest
        restart: always
        ports:
            - 27017:27017
        environment:
            - MONGO_INITDB_ROOT_USERNAME=root
            - MONGO_INITDB_ROOT_PASSWORD=example

    mongo-express:
        image: mongo-express:latest
        restart: always
        ports:
            - 8081:8081
        environment:
            - ME_CONFIG_MONGODB_ADMINUSERNAME=root
            - ME_CONFIG_MONGODB_ADMINPASSWORD=example
        depends_on:
            - mongo
# Run
# docker-compose -f mongodb.yml up -d 
# and connect to http://localhost:8081/ to view admin mongo-express
# and connectionString will be `mongodb://root:example@localhost:27017/admin?ssl=false`
```
4. Run the integration test