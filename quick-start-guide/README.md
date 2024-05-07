# Quick Start Guide - IDS Basecamp

### This is a demo and a faster way to up the ids-basecamp ecosystem and understand how it works.

## Supported Systems

- Linux (or WSL on windows)
- Mac Os

## Requirements

- Git
- Docker

## How to run

- Clone the [ids-basecamp](https://github.com/ids-basecamp/ids-basecamp) repository
- Go to quick-start-guide directory

- To start the environment run the code below:

> docker compose -p ids-basecamp up -d

- To shutdown the environment run the code below:

> docker compose down

## About the containers

About the containers

In this demo environment, the following containers will be launched:

- Postgres
  - Relational database used by Broker, Container 1, Container 2 and Clearing House App containers

- DAPS
  - [IDS DAPS](https://github.com/International-Data-Spaces-Association/IDS-G/blob/main/Components/IdentityProvider/DAPS/README.md) implementation used by Broker, Container 1, Container 2 and Clearing House EDC containers

- Clearing House App
  - [IDS Clearing House](https://github.com/International-Data-Spaces-Association/IDS-G/blob/main/Components/ClearingHouse/README.md) implementation, with a REST API

- Clearing House EDC
  - [Multipart protocol API](https://github.com/International-Data-Spaces-Association/IDS-G/blob/main/Communication/protocols/multipart/README.md#42-clearing-house-interactions) to communicate with Clearing House App REST API, used by Connector 1 and Connector 2 containers

- Broker
  - [IDS Broker](https://github.com/International-Data-Spaces-Association/IDS-G/tree/main/Components/MetaDataBroker) implementation used by Connector 1 and Connector 2 containers

- Connector 1 and Connector 2
  - [IDS Connector](https://github.com/International-Data-Spaces-Association/IDS-G/blob/main/Components/Connector/README.md) implementations using a EDC Milestone 8 implementation

## About environments

The configurations variables can be found in .env file located into quick-start-guide folder

| Variable                     | Description                                                                                             |
|------------------------------|:--------------------------------------------------------------------------------------------------------|
| POSTGRES_USER                | Database default user                                                                                   |
| POSTGRES_PASSWORD            | Database default password                                                                               |
| API_AUTH_KEY                 | Connectors REST API access key                                                                          |
| KEYSTORE_PASSWORD            | Keystore password of keystore files (.jks) with the DAPS communication certificates                     |
| KEYSTORE_CERTIFICATE         | Alias of the certificate from keystore file                                                             |
| KEYSTORE_PRIVATE_KEY         | Alias of private key from keystore file                                                                 |
| JWT_AUDIENCE                 | claim aud of JWT token to exchange between Clearing House EDC and Clearing House APP                    |
| JWT_ISSUER                   | claim iss of JWT token to exchange between Clearing House EDC and Clearing House APP                    |
| JWT_SIGN_SECRET              | secret of token JWT token to exchange between Clearing House EDC and Clearing House APP                 |
| JWT_EXPIRES_AT               | Expiration time (in seconds) of JWT token to exchange between Clearing House EDC and Clearing House APP |
| CH_APP_SERVICE_LOG           | ID of service log module from Clearing House APP                                                        |
| BROKER_DELAY_SECONDS         | Time to the first execution of the broker crawler                                                       |
| BROKER_PERIOD_SECONDS        | Time to the next executions of the broker crawler                                                       |                   
| BROKER_NUM_CRAWLERS          | Number of concurrents instances to be created from the broker crawler                                   |
| BROKER_CLIENT_ID             | DAPS oAuth client ID of Broker container                                                                |
| CH_EDC_CLIENT_ID             | DAPS oAuth client ID of Clearing House EDC container                                                    |
| CONNECTOR_1_CLIENT_ID        | DAPS oAuth client ID of Connector 1 container                                                           |
| CONNECTOR_2_CLIENT_ID        | DAPS oAuth client ID of Connector 2 container                                                           |
| POSTGRES_PORT                | Database local access port                                                                              |
| CONNECTOR_1_MANAGEMENT_PORT  | Connnector 1 API Managment local access port                                                            |
| CONNECTOR_1_IDS_PORT         | Connector 1 IDS API local access port                                                                   |
| CONNECTOR_2_MANAGEMENT_PORT  | Connnector 2 API Managment local access port                                                            |
| CONNECTOR_2_IDS_PORT         | Connector 2 IDS API local access port                                                                   |