# TerraSight: Remote Sensing Data Analysis 

## Overview

TerraSight is a scalable solution designed for processing and analyzing remote sensing data. This system leverages cloud-based technologies and aims to streamline the process of downloading, converting, and analyzing TIF files sourced from NASA repositories. These TIF files contain vital spatial information obtained through remote sensing technologies and are crucial for various environmental and geographical studies. 

## Objectives

1. **Data Extraction**: TerraSight automates the process of downloading TIF files from NASA's data repositories. This reduces manual intervention and enhances the speed of data acquisition.

2. **Data Conversion**: TerraSight includes a built-in functionality that converts the downloaded TIF files into a format suitable for data analysis. This conversion process makes the files ready to be ingested by various analytical models.

3. **Scalable Analysis**: TerraSight uses distributed computing to run models on the converted data. This enables the handling of large data sets and scales up the speed of analysis.

## Key Components

### Docker

Docker is extensively used to provide an isolated and reproducible environment for running the TerraSight application. Docker images are built containing all the necessary dependencies and libraries needed for the application, enabling the application to be run on any system with Docker installed, regardless of the underlying hardware and OS configuration.

### Ray

Ray is a high-performance distributed computing library that allows the project to run models on multiple servers simultaneously. Ray efficiently manages the utilization of computing resources and improves the speed and performance of data processing.

### Python

Python serves as the primary programming language for this project due to its extensive library support for data analysis and processing. 

## Operation

TerraSight supports both local and multi-server deployment. This scalability makes it suitable for small-scale experiments as well as large-scale data processing tasks. The project comes with detailed instructions for setting up both environments. 

## Potential Applications

The TerraSight project, with its robust capabilities, can be used for a variety of applications that require remote sensing data analysis, such as climate change studies, environmental monitoring, agricultural planning, land use management, and more.

## Setting Up Locally

Follow these steps to build and run the project locally:

1. Build the Docker image:
    ```
    docker build -t terrasight-image .
    ```

2. Run the Docker container:
    ```
    docker run --network="host" -d terrasight-image:latest
    ```

3. To obtain the container ID of the running instance, use the `docker ps` command.

4. Initiate an interactive shell in the container:
    ```
    docker exec -t -i <container-id> bash
    ```

5. To validate the TerraSight instance, run the following command:
    ```
    python application.py --urls=1
    ```

## Multi-Server Deployment

For deployment on multiple servers, ensure Docker is installed on all servers. Follow the instructions from the [DigitalOcean Docker Installation Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04) for detailed steps.

### Head Node Setup

1. Build the Docker image:
    ```
    sudo docker build -t terrasight-image .
    ```

2. Run the Docker container:
    ```
    sudo docker run -d --network="host" --shm-size=2.48gb terrasight-image:latest
    ```

### Worker Node Setup

1. Build the Docker image:
    ```
    sudo docker build -t terrasight-image .
    ```

2. Run the Docker container and specify the IP address of the head node:
    ```
    sudo docker run --network="host" --shm-size=2.48gb -d terrasight-image:latest worker <head-node-IP-address>
    ```

### Application Launch

Run the following commands on the head node:

1. Obtain the container ID of the running instance using `sudo docker ps`.

2. Initiate an interactive shell in the container:
    ```
    sudo docker exec -t -i <container-id> bash
    ```

3. Validate the TerraSight instance by running:
    ```
    python application.py --urls=1
    ```

Please feel free to report any issues or suggestions, as your feedback is greatly appreciated. Enjoy your experience with TerraSight!