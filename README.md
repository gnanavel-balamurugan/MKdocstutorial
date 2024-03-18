# Project Title

## Description
This project is a Golang service built on the Fiber framework. It interacts with a TD engine database by querying data. The service is designed to receive data via a POST request to a REST endpoint. The JSON body of the request includes information such as the table name, start time, end time, tag names (column names), and operations to be executed (e.g., minimum, maximum, average, total) on the tags.

Upon receiving the request, the service parses the JSON body, processes the specified operations on the data, and returns the results in JSON format as the response to the POST request. This response can then be visualized using tools like Postman.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Features](#features)
- [Contributing](#contributing)
- [License](#license)

## Installation
Before you begin, ensure you have the latest version of Golang installed on your system. You can download and install it from the [official Golang website](https://golang.org/dl/).

Additionally, you need to install the Fiber framework module by running the following command in your terminal:
```bash
go get github.com/gofiber/fiber/v2
```
## Usage

### Running the Service Locally
1. Clone the repository to your local machine.
2. Navigate to the project directory.
3. Run the following command to start the service:
    ```bash
    go run main.go
    ```
4. Once the service is running, it will be available at http://localhost:3000/sensordata.

### Sending Requests

#### Notes:
- The request body must be in JSON format.
- Specify the start time and end time in the format: YYYY-MM-DD HH:mm:ss.sss.
- Provide the table name and tags (column names) to be queried.
- When the OPERATION field is empty, the service queries all data within the specified time range from the specified tags.
- If operations are specified, the service performs only those operations on the specified tags within the time range.

#### Steps:
1. Ensure you have the service running locally as instructed above.
2. Use an API testing tool such as Postman or Thunder Client to send a POST request to the /sensordata endpoint.
3. In the request body, provide the required parameters in the JSON format as described in the sample format.
4. Send the request and observe the response returned by the service.

#### Sample Request:
```json
{
    "TABLE_NAME": "d1001",
    "START_TIME": "2024-03-08 17:47:12.540",
    "END_TIME": "2024-03-08 17:48:42.500",
    "TAGS": [
        "cycle_count",
        "part_count"
    ],
    "OPERATION": {
        "cycle_count": ["total", "average", "minimum", "maximum"],
        "part_count": ["total", "average", "minimum", "maximum"]
    }
}
```
### Sample Output:
```json
[
    {
        "sum(cycle_count)": 676
    },
    {
        "avg(cycle_count)": 67.6
    },
    {
        "min(cycle_count)": 9
    },
    {
        "max(cycle_count)": 93
    },
    {
        "sum(part_count)": 622
    },
    {
        "avg(part_count)": 62.2
    },
    {
        "min(part_count)": 35
    },
    {
        "max(part_count)": 85
    }
]
```json
