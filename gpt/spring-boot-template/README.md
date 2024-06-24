# Spring Boot Template
This repository contains the Backstage Template used to create the openshift resources needed to build/deploy a simple springboot application.
# [Devfile reference]
# Spring Boot App can be found skeleton directory

# Template Manifest:template.yaml

This is most important element in this repository. 

## parameters

This is where you define steps which are rendered in the frontend with the form input.

It defines several input parameters with default values.
All these parameters are then used during code generation. If you would like to have more customizations in the template, this would be the intended manifest of interest for you.


## steps
This section in the manifest defines the actions required to create a new app in Developer Hub.
1. **Generating the Source Code Component | _action: fetch:template_**  
We need to generate the spring boot app source by filling the template inside the skeleton directory with the parameters defined in the manifest, by calling fetch:template action.
2. **Generating the CI Component| _action: fetch:template_**  
We need to generate the CI componenets by filling the template inside skeleton directory (../skeleton/ci/tekton) with the parameters defined in the manifest, by calling fetch:template action.
3. **Generating the Catalog Info Component | _action: fetch:template_**  
We need to generate the catalog-info.yaml by filling the template inside skeleton directory (../skeleton/catalog-info) with the parameters defined in the manifest, by calling fetch:template action.
4. **Publishing to the Source Code Repository | _action: publish:gitlab_**  
Then we publish the generated code in the newly created gitlab repo by calling the publish:gitlab action
5. **Registering the Catalog Info Component | _action: catalog:register_**  
We register the new componenet in the Backstage catalog by calling the catalog:register action.
6. **Generating Deployment Resources | _action: fetch:template_**
We need to generate the CD componenets by filling the template inside skeleton directory (../skeleton/gitops/) with the parameters defined in the manifest, by calling fetch:template action.
7. **Publishing to Resource Repository | _action: publish:gitlab_**  
Then we publish the gitops resources of teh newly geenrated app.
8. **Create ArgoCD Resources | _action: argocd:create-resources_**  
Basically creating argocd resource for the newly generated app.

## output  
This section can be used define to public links for newly generated app like links to:  
1. Source Code Repository
2. Catalog Info Component
3. argocd
