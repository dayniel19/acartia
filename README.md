# SSEMMI
This is the public repository for the SSEMMI project: A decentralised and communitarian project aiming at pooling citizen science data in support of whale and environmental observations

<br>

## Installation and running locally
  

```

$ npm install

```

Install all dependencies and packages of the backend

```

$ cd src/client && npm install

```

Install all dependencies and packages of the front-end

Once dependencies of both "ends" have been installed you can run test the application on a local server by doing the following:

```

$ npm run start

or

$ npm run dev

```

Use this within the main directory to start the backend activity of the server as well as the database. 
 > Note that if you were to use "npm run dev" it triggers a hotfix or a live reload if changes were to be made to the code.

```

$ cd src/client && npm run serve

```

This will start the front-end build and serving and a localhost port will be generated for local development use. 
 > Note that the "cd src/client" script is only used if you are in the main directory.


<br>

## API
Below you can find the different ways you can interact and contribute to the data
in SSEMMI. Note that some functionalities are only availabe to use if you have the
appropriate credentials.




# orcasound-api v0.0.0




- [Auth](#auth)
	- [Authenticate](#authenticate)
	
- [PasswordReset](#passwordreset)
	- [Send email](#send-email)
	- [Submit password](#submit-password)
	- [Verify token](#verify-token)
	
- [Sightings](#sightings)
	- [Delete specific sightings](#delete-specific-sightings)
	- [Contribute sightings](#contribute-sightings)
	- [Retrieve current sightings](#retrieve-current-sightings)
	- [Retrieve specific sightings](#retrieve-specific-sightings)
	- [Retrieve sightings marked as trusted](#retrieve-sightings-marked-as-trusted)
	
- [User](#user)
	- [Create user](#create-user)
	- [Delete user](#delete-user)
	- [Retrieve current user](#retrieve-current-user)
	- [Retrieve current user requests](#retrieve-current-user-requests)
	- [Retrieve user](#retrieve-user)
	- [Retrieve users](#retrieve-users)
	- [Update password](#update-password)
	- [Update user](#update-user)
	
- [Direct Interactions With OrbitDB](#direct-interactions-with-orbitdb)

# Auth

## Authenticate



	POST /auth

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization			| String			|  <p>Basic authorization with email and password.</p>							|

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>Master access_token.</p>							|

# PasswordReset

## Send email



	POST /password-resets


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| email			| String			|  <p>Email address to receive the password reset token.</p>							|
| link			| String			|  <p>Link to redirect user.</p>							|

## Submit password



	PUT /password-resets/:token


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| password			| String			|  <p>User's new password.</p>							|

## Verify token



	GET /password-resets/:token


# Sightings

## Delete specific sightings



	DELETE /sightings/:id


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|

## Contribute sightings



	POST /sightings


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|

## Retrieve current sightings



	GET /sightings


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|

## Retrieve specific sightings



	GET /sightings/:id


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|

## Retrieve sightings marked as trusted



	GET /sightings/trusted


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|

# User

## Create user



	POST /users


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>Master access_token.</p>							|
| email			| String			|  <p>User's email.</p>							|
| password			| String			|  <p>User's password.</p>							|
| name			| String			| **optional** <p>User's name.</p>							|
| picture			| String			| **optional** <p>User's picture.</p>							|
| isApproved			| String			| **optional** <p>if the user is approved by admin.</p>							|
| role			| String			| **optional** <p>User's role.</p>							|

## Delete user



	DELETE /users/:id


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|

## Retrieve current user



	GET /users/me


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|

## Retrieve current user requests



	GET /users/requests


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|

## Retrieve user



	GET /users/:id


## Retrieve users



	GET /users


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|
| q			| String			| **optional** <p>Query to search.</p>							|
| page			| Number			| **optional** <p>Page number.</p>							|
| limit			| Number			| **optional** <p>Amount of returned items.</p>							|
| sort			| String[]			| **optional** <p>Order of returned items.</p>							|
| fields			| String[]			| **optional** <p>Fields to be returned.</p>							|

## Update password



	PUT /users/:id/password

### Headers

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| Authorization			| String			|  <p>Basic authorization with email and password.</p>							|

### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| password			| String			|  <p>User's new password.</p>							|

## Update user



	PUT /users/:id


### Parameters

| Name    | Type      | Description                          |
|---------|-----------|--------------------------------------|
| access_token			| String			|  <p>User access_token.</p>							|
| name			| String			| **optional** <p>User's name.</p>							|
| picture			| String			| **optional** <p>User's picture.</p>							|
| isApproved			| String			| **optional** <p>if the user is approved by admin.</p>							|


# Direct Interactions With OrbitDB

The following is a link to the github repository of Orbit DB. There you can find the API documentation to the docs type Orbit DB database which is used with SSEMMI, along with the full documentation of the database.

https://github.com/orbitdb/orbit-db/blob/master/API.md#orbitdbdocsnameaddress-options
