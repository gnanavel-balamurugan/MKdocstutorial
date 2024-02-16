# TD Engine Database Query Application

## Introduction
This application queries data from a TD Engine database running on a specified host with the database named "power" running on port 6030. It also requires an MQTT broker running on port 1883. The application is written in Go and utilizes the `paho mqtt` client for MQTT communication and the `taosSql` library for interacting with the TD Engine database.

## Prerequisites
Ensure that the host machine running this application meets the following requirements:
1. Latest version of Go is installed.
2. The `paho mqtt` client is exported using the command:
   ```bash
   go get github.com/eclipse/paho.mqtt.golang
   ```
3.Taos SQL library is installed using:
```bash
    go get github.com/taosdata/driver-go/v3/taosSql
```
## Usage
```bash
    go run main.go
```
## MQTT Topic
Publish commands under the topic tdengine/data/subtable_name.
Publish commands under the topic tdengine/data/subtable_name.
example topic:
```bash
tdengine/data/d1001
```
## Data Format
```bash
{
  "Starttime": "2024-02-13 10:43:30.873",
  "EndTime": "2024-02-13 10:46:50.871"
}

```
## Note
1 Only data from the subtables d1001, d1002, d1003, d1004 can be queried.
2 The provided time range should be within the data available in the specified subtables.
## Exit Gracefully
To exit the application gracefully, send an interrupt signal (typically `Ctrl+C`). The application waits for ongoing processes to finish before exiting.

   
