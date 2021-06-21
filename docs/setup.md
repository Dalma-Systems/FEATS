# Setup

Before being able to simulate the system operation, we need to provide some information to the system, namely:
- ORION entities:
  - AMR
  - Warehouse
  - Idle Station
  - Work Stations
- MySQL DBs

## Creating MySQL databases

FEATS requires two databases for its operation, `dalma_jobs` and `dalmadb`. To create these, we need to go inside the mysql-db container:
```shell
$ docker exec -it mysql-db bash
```
Next, we are going to access MySQL directly using the CLI:
```shell
$ root@mysql-db:/# mysql
$ mysql> CREATE DATABASE dalmadb;
Query OK, 1 row affected (0.01 sec)
$ mysql> CREATE DATABASE dalma_jobs;
Query OK, 1 row affected (0.01 sec)
```

## Creating ORION entities

For the creation of the various entities on ORION, we will be using [Postman](https://www.postman.com/). The collection of requests to be used can be found in the repository (`dalma_feats.postman_collection.json`) and should be imported into Postman.

Before proceeding, make sure the Postman enviroment is correctly set up. For this, select "dalma demo" in the Environment drop-down and then click the 'eye' icon next to it. This shows the required enviroment variables and their values. For a local enviroment, these should be the set values:

| Variable   | Value                  |
| ---        | ---                    |
| orion_url  | http://localhost:21026 |
| url_latte  | http://localhost:8091  |
| url_coffee | http://localhost:8092  |
| url        | http://localhost:8080  |

After importing, let us create the different entities:

### Adding an AMR

1. Go into `latte > robot` and select the POST request titled "add robot".
2. In the "Body" section of the request, change the `macAddress` value to any one you want (we recommend `aa:bb:cc:dd:ee:ff`). If you choose a different one from the recommendation, please be aware that you will also need to change the `ROBOT_ID` environment variable in the `firos` container of the `docker-compose.yml` file.
3. Send the request -- the response should be 201.

### Adding a warehouse


### Adding an idle station


### Adding two work stations

