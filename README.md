Table of Contents
=================

   * [Table of Contents](#table-of-contents)
   * [LLM Based vCores Management and Optimization](#llm-based-vcores-management-and-optimization)
      * [Installation](#installation)
         * [Requirements](#requirements)
         * [Connected App](#connected-app)
         * [Properties configurations](#properties-configurations)
         * [LLM Configuration](#llm-configuration)
         * [Login User Setup](#login-user-setup)
      * [Considerations](#considerations)
      * [Final Notes](#final-notes)

# LLM Based vCores Management and Optimization
The **LLM Based vCores Management and Optimization utility** is a Mule application with a user interface which helps the user to efficiently manage the vCores of each application based on AI Suggestions. This utility will connect to your cloudhub organization and list the Environments and applications in each environment.

User can view the stats of the Mule application by clicking on stats icon ![Alt text](readme-assets\image-1.png) in the 'Actions' column which show the statistics(Events, CPU and Memory) of last 5 days and also shows the AI Suggested worker and worker size based on the current CPU/Memory utilization.

Based on the AI recommendations user can update the workers by clicking on edit button ![Alt text](readme-assets\image.png) in Actions column which enables the worker selection fields, once the workers are updated user can then click update icon ![Alt text](readme-assets\image-2.png) in Actions column to update the workers in Cloudhub.

Efficient vCore configuration is crucial for balancing performance and cost in any MuleSoft integration setup. With the help of MuleSoft's AI Chain Connectors, this utility simplifies the process by:

✅ Offering intelligent recommendations based on workloads.\
✅ Enhancing decision-making with predictive insights.\
✅ Reducing manual effort and potential errors.\
✅ Ability to update the worker setup of application directly from the UI based on AI recommendations

![Alt text](readme-assets\image-3.png)

## Installation

### Requirements
- Mule Runtime 4 or above
- Only CloudHub deployment model is supported

### Connected-app
  - A Connected App (client credentials) with the following scopes (make sure to include all Sub Orgs and all environments you want to manage):
    - Runtime Manager
      - Manage Applications
      - Read Applications
    - General
      - View Environment
      - View Organization
  - <u>DO NOT</u> give production access to the Connected App if you dont intent to manage your vcores from this UI.

### Properties configurations

- Organization Id and connected app credentials are defined in `/src/main/resources/properties.yaml`.
- Login user configurations are also defined in `/src/main/resources/properties.yaml`. Leave the values for these empty and give the values in the settings page during deployment.
- Make sure to encrypt all sensitive data using the Secure Properties Module. provide the security.key value in the settings page. This is already added to mule-artifact.json to be masked.
- Password encryption is done using AES Algorithm.

### LLM Configuration

- LLM Keys used in the Mulesoft AI Chain connector must be specified in file `/src/main/resources/envVars.yaml`.
- Use your own LLM by changing the configuration in the Mulesoft AI Chain connector config.

### Login User Setup
  - Default Admin user is already setup with password as 'admin'
  - These crednetials must be changed and must be added as a masked value in the settings when deploying. 
  - Once deployed use the cloudhub URL- <u>{cloudbub_url}/</u> to Login to home page with default username 'admin' and password 'admin'.


## Considerations

- This application uses the Anypoint Platform APIs for to communicate with Cloudhub 1.0.
- Production environment is not shown in the list of Environments in the UI. A filter is applied to remove the production environment. This can be changed in the dataweave.

## Final Notes
Enjoy and provide feedback / contribute :)



