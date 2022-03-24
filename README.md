# rafay

Private repository to develop and test automated deployment of Basyx container on top of Cisco IKS Kubernetes cluster running on FlexPod with NetApp Trident.
To protect the containerized workloads Veeam - Kasten K10 is part of the solution to export data into NetApp StoraGRID via S3.

Trident Installation:

Step1: Deploy the trident operator.   -> trident-operator
  
Step2: Configure the Snapshot provider for Trident.   -> trident-snapshot

Step3: Configure the storage backend and the storage class.  -> trident-ontap-nas

       Deployment dependent due to local storage configurations (svm name, IPs, user, password)

Veeam Kasten K10:

  Step1: Deploy the Kasten K10 software, using the Trident storage provider for local persistency.   -> k10
  
        The StorageProvider name in the value.yaml file is not set. Take care that the Trident storage provider is the only default in the cluster
  
  Step2: Configure the infrastructure provider (VCSA), the location profile (S3 destination), and backup policies.  -> k10-config

        Deployment dependent due to local VCSA and S3 configuration.
  
Basys:

  Step1: Deploy a namespace dependent MongoDB operator.   -> mongodb-operator
  
  Step2: Configure the secret to download the images from Fraunhofer repository server.    -> erbenschell
  
  Step4: Deploy Basyx.   -> basyx


!!! Attention !!!!

value.yaml files are moved to __ __values__ __ as the value-file is specified in Rafay seperatly. 

For helm install use --value <value file>
  
