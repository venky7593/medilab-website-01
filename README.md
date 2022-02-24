# morning-devops-01
Cleaning the Cluster if already the Cluster deployed with the k8s resources
============================================================================
step-1: deploy the database manifest files first always                                                                                                                                    

step-2: deploy the application manifest files                                                                                                                               

step-3: delete pvc if for the database or applications

step-4: delete the pv.                
Note: if we delete pv first, as pvc might have been bound to it, untill pvc deleteion, pv wont get deleted

step-5: delete the configmap if any

step-6: delete the secrets if any

============================================================================
Deployment of k8s manifest files
=============================================================================
step-1: Create a branch in SCM repository and upload the k8s manifest files.

step-2: Clean the k8s cluster if already the manifest files deployed.

step-3: create SSH connection from jenkins server to k8s master machine

Step-4: Create a deployment job for the db deployment which should pull the 
deployment manifest files from the deployment branch of SCM repository.

step-5: execute the manifest files on k8s master machine
a) to do this, connect to jenkins server from k8s master machine as the SSH plug-in will
by default connected to k8s master machine via step-3 we have done.

b) copy the file from jenkins server to k8s master machine and then execute 
those files on k8s master machine.

Step-6: Create a deployment job for the application deployment which should pull the deployment manifest files from the
deployment branch of SCM repository.

step-7: execute the manifest files on k8s master machine
