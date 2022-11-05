# SSEMMI
## Salish Sea Ecosystem Monitoring and Modeling Infrastructure
This is the public repository for the SSEMMI project: A decentralised and communitarian project aiming at pooling citizen science data in support of whale and environmental observations. We welcome your help designing and developing this open source code that demonstrates the ecological, scientific, and societal advantages of a a web3 technologies (see our [contributing guidance](https://github.com/Typehuman/SSEMMI/blob/main/CONTRIBUTING.md#contributing-code)).

In 2020-22, phase 1 of the project developed a working prototype of [Acartia](https://acartia.io), a distributed open data cooperative sharing marine animal location data in real time across the range of the endangered orcas (from California to Alaska, USA). Phase 2 in 2023 aims to add features to the prototype and diversify the data providers and end uses in the U.S. Phase 3 will aspire to share data across the US-Canada border and integrate with other applications to enhance regional ecosystem understanding and management for marine conservation.

For project context and updates, don't miss the [Acartia wiki](https://github.com/Typehuman/SSEMMI/wiki). There you will also find additional information for design-UXers, open source developers, devops leads, and system administrators.

<br>

## Installation and running locally
  
Install all dependencies and packages of the backend
```

$ npm install

```

<br>

Install all dependencies and packages of the front-end
```

$ cd src/client && npm install

```

<br>

Once dependencies of both "ends" have been installed you can run test the application on a local server by doing the following:
```

$ npm run start

or

$ npm run dev

```
Use this within the root directory to start the backend activity of the server as well as the database. 
 > Note that if you were to use "npm run dev" it triggers a hotfix or a live reload if changes were to be made to the code.

<br>

This will start the front-end build and serving and a localhost port will be generated for local development use.
```

$ cd src/client && npm run serve

``` 
 > Note that the "cd src/client" script is only used if you are in the main directory.


<br>

## API
Below are the sightings API endpoints that can be used to create and consume open source 
data. Before using this API, you are required to create an account and generate an API key on 
the [SSEMMI Project Dashboard](https://acartia.io/).

More information on how to contribute data to the project can be found [here](CONTRIBUTING.md#contributing-data),
and more information on contributing to the codebase can be found [here](CONTRIBUTING.md#contributing-code).


- [Sightings](#sightings)
  - [Contribute sightings](#contribute-sightings)
  - [Delete specific sightings](#delete-specific-sightings)
  - [Retrieve current sightings](#retrieve-current-sightings)
  - [Retrieve sightings marked as trusted](#retrieve-sightings-marked-as-trusted)
  - [Retrieve specific sightings](#retrieve-specific-sightings)


___


# Sightings

## Contribute sightings
[Back to top](#api)

```
POST https://acartia.io/api/v1/sightings
```

### Parameters - `Parameter`

| Name     | Type       | Description                           |
|----------|------------|---------------------------------------|
| access_token | `String` | User access_token. |

### Success response

#### Success response - `Success 200`

| Name     | Type       | Description                           |
|----------|------------|---------------------------------------|
| Entry | `Object` | of sighting. |

### Error response

#### Error response - `Error 4xx`

| Name     | Type       | Description                           |
|----------|------------|---------------------------------------|
| 400 |  | Invalid input. |

## Delete specific sightings
[Back to top](#api)

```
DELETE https://acartia.io/api/v1/sightings/:id
```

### Parameters - `Parameter`

| Name     | Type       | Description                           |
|----------|------------|---------------------------------------|
| access_token | `String` | User access_token. |

### Success response

#### Success response - `Success 200`

| Name     | Type       | Description                           |
|----------|------------|---------------------------------------|
| 200 | `Object` | Deleted sighting entry. |

## Retrieve current sightings
[Back to top](#api)

```
GET https://acartia.io/api/v1/sightings/current
```

### Success response

#### Success response - `Success 200`

| Name     | Type       | Description                           |
|----------|------------|---------------------------------------|
| List | `Object` | of sightings. |

## Retrieve sightings marked as trusted
[Back to top](#api)

```
GET https://acartia.io/api/v1/sightings/trusted
```

### Parameters - `Parameter`

| Name     | Type       | Description                           |
|----------|------------|---------------------------------------|
| access_token | `String` | User access_token. |

### Success response

#### Success response - `Success 200`

| Name     | Type       | Description                           |
|----------|------------|---------------------------------------|
| Sightings | `Object` | with trusted source. |

## Retrieve specific sightings
[Back to top](#api)

```
GET https://acartia.io/api/v1/sightings/:id
```

### Parameters - `Parameter`

| Name     | Type       | Description                           |
|----------|------------|---------------------------------------|
| access_token | `String` | User access_token. |

### Success response

#### Success response - `Success 200`

| Name     | Type       | Description                           |
|----------|------------|---------------------------------------|
| Sighting | `Object` | based on id. |



A complete version of the API documentation can be found in [DOCS.md](DOCS.md).
# Direct Interactions With OrbitDB

The following is a link to the github repository of Orbit DB. There you can find the API documentation to the docs type Orbit DB database which is used with SSEMMI, along with the full documentation of the database.

https://github.com/orbitdb/orbit-db/blob/master/API.md#orbitdbdocsnameaddress-options
