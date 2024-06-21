# Spring Boot Template
This repository contains the Backstage Template used to create the openshift resources needed to build/deploy a simple springboot application.

# Template Manifest:template.yaml

This is most important element in this repository. 

## parameters

This is where you define steps which are rendered in the frontend with the form input.

It defines several input parameters with default values.
All these parameters are then used during code generation. If you would like to have more customizations in the template, this would be the intended manifest of interest for you.


## steps
This section in the manifest defines the actions required to create a new app in Developer Hub.
* We need to generate the spring boot app source by filling the template inside the skeleton directory with the parameters defined in the manifest.
* Then we publish the generated code in the newly created gitlab repo. 
* We register the new componenet in the Backstage catalog by calling the catalog:register action.
