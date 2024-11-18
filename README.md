# Power Plant Production Plan API

This project is a ptyhon Flask-based API used in the code challenge intending to calculate power distribution using request parameters such as: load, fuels, and powerplants.

## Prerequisites

We assume that you need to have the following components in order to build and launch this application:

* Docker
* Docker Compose

## Project Structure
.  
├── app/  
│   ├── __init__.py        # Initializes the Flask application  
│   ├── routes.py          # Defines the API routes  
│   ├── utils.py           # Defines the utils methods  
│   ├── services.py        # Contains the logic for calculating power distribution  
├── run.py                 # Entry point for running the Flask application  
├── requirements.txt       # Lists the project dependencies  
├── Dockerfile             # Dockerfile for building the Docker image  
├── docker-compose.yml     # Docker Compose file for setting up the services  
└── README.md              # Documentation for the project  

## Setup and Installation
### Using Docker

1. **Build the Docker image:**

    ```bash
    docker-compose build
    ```

1. Run the Docker container

    ```bash
    docker-compose build
    ```

1. The API will be available at http://localhost:8888.
    * port 8888 is used following the requirement

## API Endpoints

```/productionplan```

* **Method**: ```POST```
* **Description**: Calculates power distribution based on load, fuels, and powerplants.
* **Request Body (schema)**:
    ```json
    {
        "load": "<< Integer containing the amount of energy (MWh) that need to be generated during one hour >>",
        "fuels": {
            "gas(euro/MWh)": "<< Float number containing the price of gas per MWh >>",
            "kerosine(euro/MWh)": "<< Float number containing the price of kerosine per MWh >>",
            "co2(euro/ton)": "<< Integer number containing the price of emission allowances >>",
            "wind(%)": "<< Integer number containing the percentage of wind >>"
        },
        "powerplants": [
            {
            "name": "<< String containing the powerplant name >>",
            "type": "<< Type on the powerplante (gasfired, turbojet or windturbine) >>",
            "efficiency": "<< Float number containing the efficiency at which they convert a MWh of fuel into a MWh of electrical energy >>",
            "pmin": "<< Number with the maximum amount of power the powerplant can generate >>",
            "pmax": "<< Number with the minimum amount of power the powerplant generates when switched on >>"
            }
        ]
    }
    ```
* **Response (schema)**:
    ```json
    [
        {
            "name": "<< string representing powerplant name >>",
            "p": "<< float number representing how much power was produced >>"
        }
    ]
    ```

## Running unit tests:
For unit tests executions, please run the following command:

```bash
docker-compose run test
```