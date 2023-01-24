#   Push Docker images to Azure Container Registry

A Key Vault access policy determines whether a given security principal, namely a user, application or user group, can perform different operations on Key Vault secrets, keys, and certificates.

Key vault supports up to 1024 access policy entries, with each entry granting a distinct set of permissions to a particular security principal.


##  Here are steps to assign Access Policy in Key Vaults

- Step 1 : In the Azure portal, navigate to the Key Vault resource. Go to Secrets and check if you are authorized to see the secrets in the keyvault
  
  
  If you are unauthorized to view the secrets, move to next steps
  ![img1](./docs/img1.png)


- Step 2 : Go to Access Control (IAM) and view my access
  ![img2](./docs/img2.png)
  
  
   Make sure you have a contributor Role
  ![img3](./docs/img3.png)
  
  
 - Step 3 : Navigate to Access Policies, select Create to assign the access policy
  ![img4](./docs/img4.png)


 - Step 4 : In Create an access policy , choose Select All in Secret Management Operations, then Next
  ![img5](./docs/img5.png)
  
  
 - Step 5 : In Principal, type `ds-aad-su`, then Next
  ![img6](./docs/img6.png) 


 - Step 6 : In Application (Optional), then choose Next
  ![img7](./docs/img7.png) 
  
  - Step 7 : Choose Create to finish Assign Access Policies
  ![img8](./docs/img8.png) 
  
