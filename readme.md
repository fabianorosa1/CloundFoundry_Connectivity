Learn from blog [Part 2: How to use SAP Cloud Platform Connectivity and Cloud Connector in the Cloud Foundry environment](https://blogs.sap.com/2017/07/13/part-2-how-to-use-the-sap-cloud-platform-connectivity-and-the-cloud-connector-in-the-cloud-foundry-environment/#comment-403420).

# 2018-05-29 5:20PM

configuration file: xs-app.json

Add the routes (destinations) for the specific application (for example, node-hello-world) to the env section application’s deployment manifest (manifest.yml).

* Every route configuration that forwards requests to a micro service has property destination. 

* The destination is a name that refers to the same name in the destinations configuration. 

* The destinations configuration is specified in an environment variable passed to the approuter application.

The start script (for example, approuter.js) is mandatory; the start script is executed after application deployment.

### destination

A destination defines the back-end connectivity. In its simplest form, a destination is an URL to which requests are forwarded. There has to be a destination for every single app (microservice) that is a part of the business application.

The value of the destination "name" property ("name":“backend” in the example below) must match the value of the destinations property configured for a route in the corresponding application-router configuration file (xs-app.json).

* source in configuration file: Describes a regular expression that matches the incoming request URL.
* target: The incoming request path is rewritten to this target

The application router is used to serve **static content**, propagates user information, and acts as a proxy to forward requests to other micro services. The routing configuration for an application is defined in one or more destinations. 

## SCN blogs

[part 2: How to use SAP Cloud Platform Connectivity and Cloud Connector in the Cloud Foundry environment](https://blogs.sap.com/2017/07/13/part-2-how-to-use-the-sap-cloud-platform-connectivity-and-the-cloud-connector-in-the-cloud-foundry-environment/)

## Jerry application info

xsuaa: xsuaa-jerry-demo

destination name( sub account level): jerry-abap-backend

jerry-destination-lite: destination instance in dev space - bind to application

connectivity-instance: connectivity-jerry-demo, bind to application

app name: connectivity-jerry-demo

# 2018-05-30 11:54AM

status: CRASHED. See [blog](https://docs.cloudfoundry.org/devguide/deploy-apps/troubleshoot-app-health.html#start)

cf logs connectvity-demo-approuter --recent

cf push -f ./