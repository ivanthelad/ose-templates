To use. 
The idea is to have one project build the images while the other project consumer the image and deploys it. 

to use, 
# create project 
 oc new-project  builds 
# import build template 
 oc create -f build-template.yaml 
# process and create template 
 oc process building-template | oc create -f -
# create deployable project
 oc new-project  deploys
# import template 
 oc create -f deploy-template.yaml 
# process and create template  
 oc process deployer-template | oc create -f -

# add pull rights to deploy project 
 oc policy add-role-to-group  system:image-puller system:serviceaccounts:builds -n deploys
 
