---
layout: post
title:  "L2M2M Protocol"
date:   2023-03-05
excerpt: "What is Lightweight M2M (LwM2M) protocol? A walkthrough with an example"
tag: false
comments: false
---

If you are working on IoT networks, you are bound to find Lightweight M2M (LwM2M) protocol useful. L2M2M is designed for remote management of devices which are light weight and constrained in power, computation and networking capabilities to realize the potential of IoT.

LwM2M provides device management functions designed for sensor network's Machine to Machine (M2M) communication. It is built on top of Constrained Application Protocol (CoAP) and uses the architecture principle of Representational State Transfer (REST) for communication. It is developed by [Open Mobile Alliance (OMA)](https://omaspecworks.org/what-is-oma-specworks/iot/lightweight-m2m-lwm2m/).

LwM2M provides core functionalities such as device configuration, firmware update, bootstrapping, connection management and data reporting.

It provides end to end secure communication using DTLS (Datagram Transport Layer Security) which provides encryption, integrity and authentication ensuring that the data exchanged between devices and server is secure. DTLS is a lightweight version of TLS (Transport Layer Security) designed for constrained environment.

A very insightful presentation on LwM2M by OMA is linked [here](https://www.openmobilealliance.org/release/LightweightM2M/Lightweight_Machine_to_Machine-v1_1-OMASpecworks.pdf)

Key components of LwM2M protocol:
1. Objects and object instances:
	- Objects represent various resources within a device and are made up of one or more instances.
	- Each object instance is identified by a unique Object Instance ID within its parent object.
2. Resources:
	- Resources are individual data points within an object instance. They can be read, written or observed. It is identified by a unique Resource ID within in parent object instance.
3. Object and resource definition:
	- LwM2M defines a set of standard objects and resources for common use, such as device management, security.
4. Operations:
	- L2M2M performs basic operations on objects and resources such as read, write, execute, delete and discover.


Let's walk through a detailed example of how a device, using the LwM2M protocol, can send and receive data from a remote server. For simplicity, let's consider a "Smart Thermostat" as our device that is communicating with a remote server, and we'll focus on managing and updating the temperature setting on the device.

1. Device Registration:
- The thermostat initiates communication by registering with the LwM2M server.
- It sends a POST request to L2M2M server for registration.
- The server responds with a unique endpoint and other registration details.

2. Object and resource definition:
- The thermostat supports the device object ID 3303 with multiple instances, where each instance represents a specific thermostat unit. Refer [this page](https://techlibrary.hpe.com/docs/otlink-wo/OMA-LWM2M-Object-Resource-and-Value-Details.html) for default details of LwM2M object IDs.
- Resources:
	- 5700: current temperature, which is readable
	- 5701: target temperature, which is readable and writable

3. Sending data to the server (updating target temperature):
- Thermostat user adjusts the temperature setting to 22 degree celcius.
- The smart thermostat sends a PUT request to the server with the new target temperature value.
- The request might look like:

```json
PUT /3303/0/5701
Content-Type: application/json

{"target_temperature": 22}
```

Server acknowledges the update and the target temperature is now set to 22 degrees Celcius.

4. Receiving data from the server (reading current temperature):
- The thermostat periodically queries the server for the current temperature.
- It sends a GET request to the server to read the current temperature value.
- The request might look like this:

```json
GET /3303/0/5700
```
- The server responds with the current temperature:

```json
{"current_temperature": 23}
```
5. Observing changes (push notification):
- The thermostat subscribes to observe the target temperature changes.
- The server sends a push notification to the smart thermostat whenever the target temperature is updated (e.g. by another user or a scheduled event).
- The notification informs the thermostat of the updated target temperature.

6. Deregistration:
- If the thermostat is no longer active or is being decommissioned, it can send a DEREGISTER request to the server.
- The server then acknowledges the deregistration and the smart thermostat is removed from the list of active/known devices.

In summary, the device interacts with the LwM2M server using CoAP requests. It registers with the server, updates the target temperature, reads the current temperature, observes changes in the target temperature, and can eventually deregister. The LwM2M protocol, based on CoAP and RESTful principles, enables efficient and lightweight communication between the IoT device and the server in a resource constrained environment.
