# Azure_Docker_CLI_installer.ado
Use this template for installing the specific version of Docker CLI on an agent machine in Azure Devops Pipeline.

## Parameters:

The pipeline requires the following parameters to be defined:


| Name  | Displayname | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | :-------------: | :-------------: | ------------- | :-------------: | ------------- |
| dockerVersion | Docker Version | string | 17.09.0-ce | | Required | Specifies the version of the Docker CLI to install |
| releaseType | Release type | string | stable | stable, edge, test, nightly | Optional | Specifies the release type to install. The value nightly is not supported on Windows |

--------------------------------------------------------------------------------------------------------------------------------------------------

These parameters provide multiple use case options for the template, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

You can directly call a particular template as per the requirement. for example: 

  ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/Azure_Docker_CLI_installer.ado
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  steps:
  # passing the parameters
  - template: Azure_Docker_CLI_installer.yml
    parameters:
      dockerVersion: '${{parameters.dockerVersion}}' 
      releaseType: '${{parameters.releaseType}}'
  ```
  
Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.
