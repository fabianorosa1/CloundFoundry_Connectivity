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

application name: connectivity-jerry-demo

## Jerry account

SAP internal endpoint: https://api.cf.sap.hana.ondemand.com

account id: 116608ce-d2e8-4330-b92a-9bb874a3b491

# 2018-05-30 11:54AM

status: CRASHED. See [blog](https://docs.cloudfoundry.org/devguide/deploy-apps/troubleshoot-app-health.html#start)

cf logs connectvity-demo-approuter --recent

cf push -f ./approuter-manifest.yml

# 2018-06-04

1. Could not find service xsuaa-jerry-demo to bind to connectivity-jerry-demo 3:31PM
why app router can automatically bind?! 3:52PM

2. 4:04PM root cause found: 我的api endpoint用错了。

4:28PM 幺蛾子又来了：Service instance jerry-destination-lite of service xsuaa not bound to application

4:35PM 新的幺蛾子：detailMessage

"com.sap.cloud.sample.connectivity.cf.exceptions.DestinationNotFoundException: Destination 'abapBackend1' could not be found"

https://api.cf.eu10.hana.ondemand.com

neo-app.json: destination in SCP cockpit, bound to connector 

终于通了。No service found for namespace , name EPM_REF_APPS_SHOP_SRV, version 0001

[application log](https://help.sap.com/viewer/ee8e8a203e024bbb8c8c2d03fce527dc/Cloud/en-US/68454d44ad41458788959485a24305e2.html)

# SCN blogs

