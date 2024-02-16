# Remote Container Management Application

## Introduction
This application facilitates remote management of containers via MQTT (Message Queuing Telemetry Transport) protocol. It enables users to control Docker containers remotely by publishing commands to a specified MQTT broker.

## Prerequisites
Ensure that the host machine running this application meets the following requirements:
1. Latest versions of Go and Docker are installed.
2. The `paho mqtt` client is exported using the command:go get github.com/eclipse/paho.mqtt.golang
3. An MQTT Broker is running on port 1883.

## Dependencies
Refer to the `go.mod` file for a list of dependencies required by the application.

## Usage
To start the service, execute the following command:go run main.go

## Available Commands
Publish commands to the topic "remote docker" in the MQTT broker using JSON format. The supported commands are as follows:
1. `stop_container`: Stops a specified Docker container.
2. `run_container`: Runs a Docker container.
3. `list_containers`: Lists all Docker containers.
4. `remove_container`: Removes a Docker container.

### Command Format
Publish messages in JSON format to the topic "remote docker" with the following structure:{
"Action": "stop_container",
"ContainerID": "425f2631be05"
}
Replace `"stop_container"` with the desired command and provide the appropriate `ContainerID` as needed.

## Example
Here's an example of publishing a command to stop a container:{
"Action": "stop_container",
"ContainerID": "425f2631be05"
}

## Note
As of now, only the aforementioned four commands are supported.


