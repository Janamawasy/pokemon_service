# Pokemon-Project

This service is part of a microservice architecture project. It acts as a FastAPI server that interacts with a MySql database and the Pokemon API to store and manage Pokemon data. 

## Gateway Project
For more details on the entire microservice architecture, refer to :
[gateway project](https://github.com/Janamawasy/getaway-poke-service/tree/master).

## Features

- Search Pokemon by id or name
- Search all Pokemons by trainer or type
- Search all trainers of a specific Pokemon
- Add new Pokemon using external API
- Add new trainer
- Add Pokemon to trainer
- Delete Pokemon or trainer
- Delete Pokemon from trainer
- Evolve Pokemon of specific trainer

## Technologies Used

- Python
- FastAPI
- SQLAlchemy
- PyMySQL
- Requests

## Endpoints
![Description of the image](/poke_endpoints.png)


## env Setup

   ```
   DATABASE_USERNAME=[YOUR DATABASE USERNAME]
   DATABASE_PASSWORD=[YOUR DATABASE PASSWORD]
   DATABASE_HOST=[YOUR DATABASE HOST]
   DATABASE_PORT=[YOUR DATABASE PORT]
   DATABASE_NAME=[YOUR SCHEME NAME]
   SERVER_HOST=[YOUR SERVER HOST]
   SERVER_PORT=[YOUR SERVER PORT]
   DATABASE_DOCKER_HOST=[YOUR DOCKER HOST]
  ```

## Running the Application in Docker
1. make sure of database_url in 'database_connection/database.py':
   ```
   database_URL = f'mysql+pymysql://{username}:@{docker_host}:{port}/{database_name}'
   ```
2. Initialize the database**: To migrate data from `data/pokemons_data.json` to MySql, ensure `config.json` is set to:
   ```
   {
    "poke_api_URL": "https://pokeapi.co/api/v2/pokemon",
    "database_editor": 1,
    "create_database": 1
    }
   ```
3. Set up environment: Ensure .env contains docker host according to MySQL image name in 'docker-compose.yml' in my case it mymysql:
   ```
      DATABASE_DOCKER_HOST = mymysql
   ```

4. docker up:
    ```sh
      docker-compose up
    ```

## Running the Application Locally
1. make sure of database_url in 'database_connection/database.py':
   ```
    database_URL = f'mysql+pymysql://{username}:{password}@{local_host}:{port}/{database_name}'
   ```
1. Initialize the database: To migrate data from data/pokemons_data.json to MongoDB, ensure config.json is set to:   ```
   ```
   {
    "poke_api_URL": "https://pokeapi.co/api/v2/pokemon",
    "database_editor": 0,
    "create_database": 0
    }
   ```
  - if the database already stored in Mongo db, no need to reset 'data/pokemons_data.json', it should be:
  ```
   {
    "poke_api_URL": "https://pokeapi.co/api/v2/pokemon",
    "database_editor": 1,
    "create_database": 1
    }
   ```
2. Set up environment: Ensure .env contains:
   ```
      MONGO_DB_HOST = localhost
   ```

1. Start the FastAPI server:
    ```sh
      uvicorn server:app --reload --port 8001
    ```


## Testing

run the tests:
    ```
    tests/pokemons.py
    tests/trainers.py
    tests/evolve.py
    ```
