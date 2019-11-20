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

1. Implement the action

  - Example of action: <https://openwhisk.apache.org/documentation.html#go>

2. Upload the action file

  `$ wsk action create helloGo hello.go`

3. Invoke the action

  `$ wsk action invoke helloGo -r -p name gopher`

4. Deploy the action and API using the *Whisk Deploy*

  - Create the manifest file

  - Run the deployment
  
  `$ wskdeploy -m manifest.yaml`
  
5. See the list of APIS

  `$ wsk api list`

5. See the actions, edit the code or invoke the action in the "IBM Cloud Functions - Actions" page

  <https://cloud.ibm.com/functions/actions>

## Deploying actions with IBM Cloud tools (Option)

1. Implement the action

  - Example of action: <https://github.com/IBM/ibm-cloud-functions-action-trigger-rule>

2. Poll the activation log *(optional)*

  `$ ibmcloud fn activation poll` 

3. Upload the action file as a Cloud Function *(in another terminal)*

  `$ ibmcloud fn action create handler handler.js `

4. Invoke the action manually

  `$ ibmcloud fn action invoke --blocking handler`

5. See the actions, edit the code or invoke the action in the "IBM Cloud Functions - Actions" page

  <https://cloud.ibm.com/functions/actions>
