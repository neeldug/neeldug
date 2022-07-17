---
title: "JBMN Systems: Embedded Systems project"
date: 2022-03-02T03:07:13.000Z
extra:
   image: /media/embedded.svg
   link: https://github.com/jjlehner/Y3-Embedded_Systems_Project_1
description: An embedded systems project aiming to be a wearable COVID tracker
taxonomies:
   tags:
     - Go
     - InfluxDB
     - Docker
---
### JBMN Systems: COVID Tracker

The project makes use of an Arduino board and MicroPython, to grab sensor data as well as Bluetooth sensor data to estimate proximity.

My contributions were namely toward the cloud-side/database querying end of the project:

* Setup of InfluxDB instance for seamless timeseries data-storage of sensor data
* Go server-side code to handle MQTT messages and query for CRUD operations to the DB
* Providing an HTTP endpoint for a web interface for proximity diagrams using Influx queries
* Dockerized the server-side code to build a localised cluster including the MQTT broker, InfluxDB and the server-side code
