# Serverless Demo with IBM Cloud and Apache OpenWhisk

## Prepare the Environment

1. Register and login into <https://cloud.ibm.com/>

2. Go to "IBM Cloud Functions", download and install the CLI

3. Follow the instructions *(some commands are deprecated)*

  - `$ ibmcloud login`
  - `$ ibmcloud plugin install cloud-functions`
  - `$ ibmcloud target --cf`
  - `$ ibmcloud fn list`
  
4. Install the OpenWhisk tools
  
  - OpenWhisk Cli (wsk) <https://github.com/apache/openwhisk-cli>
  
  - OpenWhisk Deploy (wskdeploy) <https://github.com/apache/openwhisk-wskdeploy>
  
## Option 1 - Deploying an action with IBM Cloud

1. Implement the action

Example of action: <https://github.com/IBM/ibm-cloud-functions-action-trigger-rule>

2. Poll the activation log *(optional)*

`$ ibmcloud fn activation poll` 

3. Upload the action file as a Cloud Function *(in another terminal)*

`$ ibmcloud fn action create handler handler.js `

4. Invoke the action manually

`$ ibmcloud fn action invoke --blocking handler`

5. See the actions, edit the code or invoke the action in the "IBM Cloud Functions - Actions" page

<https://cloud.ibm.com/functions/actions>

## Option 2 - Deploying an action with Apache OpenWhisk

1. Implement the action

Example of action: <https://openwhisk.apache.org/documentation.html#go>

2. Upload the action file

`$ wsk action create helloGo hello.go`

3. Invoke the action

`$ wsk action invoke helloGo -r -p name gopher`

4. Deploy the action using the *Whisk Deploy*

  - Create the manifest file

  - Run the deployment
  
  `$ wskdeploy -m manifest.yaml`

