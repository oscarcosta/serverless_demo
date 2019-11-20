# Serverless Demo - Apache OpenWhisk on IBM Cloud

## Prepare the Environment

1. Register and login into <https://cloud.ibm.com/>

2. Go to "IBM Cloud Functions", download and install the CLI

3. Follow the instructions *(some commands in the page are deprecated)*

  - `$ ibmcloud login`
  - `$ ibmcloud plugin install cloud-functions`
  - `$ ibmcloud target --cf`
  - `$ ibmcloud fn list`
  
4. Install the OpenWhisk tools
  
  - OpenWhisk CLI (wsk) <https://github.com/apache/openwhisk-cli>
  
  - OpenWhisk Deploy (wskdeploy) <https://github.com/apache/openwhisk-wskdeploy>
  
## Deploying actions with Apache OpenWhisk

1. Implement the action/function

  - Example of action: <https://openwhisk.apache.org/documentation.html#go>

2. Upload the action code to the platform

  `$ wsk action create helloGo hello.go`

3. Invoke the action (-r shows the result and -p pass the parameters)

  `$ wsk action invoke helloGo -r -p name gopher`

4. Deploying the action and an API using the *Whisk Deploy*

  - Create the manifest file

  - Run the deployment
  
  `$ wskdeploy -m manifest.yaml`
  
Command to list the available APIS

  `$ wsk api list`

In the "IBM Cloud Functions - Actions" page it is possible to manage all the functions features (actions/apis/triggers/monitoring).

  <https://cloud.ibm.com/functions/actions>

## Deploying actions with IBM Cloud tools (Alternative)

1. Implement the action

  - Example of action: <https://github.com/IBM/ibm-cloud-functions-action-trigger-rule>

2. Poll the activation log to see what is happening *(optional)*

  `$ ibmcloud fn activation poll` 

3. Upload the action file as a Cloud Function *(in a terminal different from the log poll)*

  `$ ibmcloud fn action create handler handler.js `

4. Invoke the action manually

  `$ ibmcloud fn action invoke --blocking handler`

5. Deploying the action and a trigger via shell script *(the IBM Cloud tooling does not have a deploy tool like Whisk Deploy)*

  `$ ./deploy.sh --install`

In the "IBM Cloud Functions - Actions" page it is possible to manage all the functions features (actions/apis/triggers/monitoring).

  <https://cloud.ibm.com/functions/actions>
