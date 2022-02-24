# morning-devops-01
step-1: deploy the database manifest files first always
step-2: deploy the application manifest files
step-3: delete pvc if for the database or applications
step-4: delete the pv.
Note: if we delete pv first, as pvc might have been bound to it, untill pvc deleteion, pv wont get deleted
step-5: delete the configmap if any
step-6: delete the secrets if any
