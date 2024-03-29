# Optimal Item Combination Solution

This project implements a Spring Boot microservice to determine the optimal combination of items based on weight and value constraints. It is designed for scenarios where maximizing total value within defined weight limits is desired.

## Overview

The service exposes a REST API that accepts requests with a set of items and a maximum weight limit. It returns the set of items that maximizes total value without exceeding the weight limit

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Cloning the Repository

To clone the project, run the following command:

  ```bash
  git clone https://github.com/markort147/theBoxProblem.git
  ```

### Starting the Application using Maven

To start the application, navigate to the root directory of the project and run the following command:

On Linux:
```bash
./mvnw spring-boot:run
```

On Windows
```dtd
mvnw.cmd spring-boot:run
```

This will start the Spring Boot application using Maven. The application will be accessible at http://localhost:8080 by default.

### Starting the Application using Docker

Alternatively, you can run the application by building a Docker image.

For building the image, launch the following command:
```bash
docker build -t theboxproblem .
```

For running the application, launch the followign command:
```bash
docker run -p 8080:8080 theboxproblem
```

## Application Configuration

The service can be configured through the `application.properties` file. The following parameters can be adjusted:

- `constraint.items.max-number`: Maximum number of items per request (e.g., 15).
- `constraint.items.max-weight`: Maximum weight per individual item (e.g., 100).
- `constraint.items.max-price`: Maximum price per individual item (e.g., 100).
- `constraint.box.max-weight`: Total maximum weight for the box (e.g., 100).
- `data-format.weight-decimals`: Number of decimal places to use for weight (e.g., 2). 

## API Usage

The API can be accessed via the following endpoint: 
  ```
  POST /api/best-combination
  ```

### Request Format

The API expects a JSON request with the following structure:

```json
{
  "max_weight": 100,
  "items": [
    {
      "Item ID": 1,
      "Weight": 20.35,
      "Price": 5
    },
    {
      "Item ID": 2,
      "Weight": 25,
      "Price": 15.15
    }
    // additional items...
  ]
}
```

- `max_weight`: The maximum weight the box can carry.
- `items`: A list of items, each with an id, weight, and price. Items can be listed in any order.
  - `Item ID`: unique ID of the item
  - `Weight`: weight of the item
  - `Price`: price of the item


### Response Format

The response will be a JSON object containing the best combination of item IDs:

```json
{
  "items": [1, 2, ...]
}
```
