Learn from blog [Part 2: How to use SAP Cloud Platform Connectivity and Cloud Connector in the Cloud Foundry environment](https://blogs.sap.com/2017/07/13/part-2-how-to-use-the-sap-cloud-platform-connectivity-and-the-cloud-connector-in-the-cloud-foundry-environment/#comment-403420).

# 2018-05-29 5:20PM

configuration file: xs-app.json

Add the routes (destinations) for the specific application (for example, node-hello-world) to the env section application’s deployment manifest (manifest.yml).

* Every route configuration that forwards requests to a micro service has property destination. 

* The destination is a name that refers to the same name in the destinations configuration. 

* The destinations configuration is specified in an environment variable passed to the approuter application.

The start script (for example, approuter.js) is mandatory; the start script is executed after application deployment.