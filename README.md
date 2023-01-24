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
  

`docker ps`

```
CONTAINER ID   IMAGE                      COMMAND       CREATED             STATUS             PORTS     NAMES
64d262a4d010   dai-func-service-bus:1.0   "/bin/bash"   About an hour ago   Up About an hour             awesome_burnell
```


`docker images`

```
REPOSITORY                    TAG       IMAGE ID       CREATED             SIZE
dai-func-service-bus          1.0       f705770c0651   About an hour ago   619MB
dai-func-sp-secret-created    1.0       7cd8ea7f3884   8 days ago          739MB
dai-func-sp-secret-expiring   1.1       7b1c8a1f34c6   13 days ago         738MB
dai-func-sp-secret-expiring   1.0       6e5ea1403dff   2 weeks ago         738MB
docker101tutorial             latest    f31889622667   4 weeks ago         46.5MB
alpine/git                    latest    9793ee61fc75   2 months ago        43.4MB
hello-world                   latest    46331d942d63   10 months ago       9.14kB
```
`az acr login --name prodfixdseus2tmlengacr01`

```
Login Succeeded
```


`az acr list --resource-group prodfix-ds-tmleng-eastus2-rg-01 --query "[].{acrLoginServer:loginServer}" --output table`

```
AcrLoginServer
-----------------------------------
prodfixdseus2tmlengacr01.azurecr.io
```



`docker tag dai-func-service-bus:1.0 prodfixdseus2tmlengacr01.azurecr.io/dai-func-service-bus:v1 `

`docker images`


```
REPOSITORY                                                 TAG       IMAGE ID       CREATED             SIZE
dai-func-service-bus                                       1.0       f705770c0651   About an hour ago   619MB
prodfixdseus2tmlengacr01.azurecr.io/dai-func-service-bus   v1        f705770c0651   About an hour ago   619MB
dai-func-sp-secret-created                                 1.0       7cd8ea7f3884   8 days ago          739MB
dai-func-sp-secret-expiring                                1.1       7b1c8a1f34c6   13 days ago         738MB
dai-func-sp-secret-expiring                                1.0       6e5ea1403dff   2 weeks ago         738MB
docker101tutorial                                          latest    f31889622667   4 weeks ago         46.5MB
alpine/git                                                 latest    9793ee61fc75   2 months ago        43.4MB
hello-world                                                latest    46331d942d63   10 months ago       9.14kB
```

`docker push prodfixdseus2tmlengacr01.azurecr.io/dai-func-service-bus:v1`

```
The push refers to repository [prodfixdseus2tmlengacr01.azurecr.io/dai-func-service-bus]
d02eaeabb3c0: Pushed 
6247d791352e: Pushed 
7f5598734951: Pushed 
f9c7f00aa561: Pushed 
4fc39c6a35fc: Pushed 
0219d3d7fa6e: Pushed 
5f70bf18a086: Pushed 
5fe4ff93a619: Pushed 
e21de659be2f: Pushed 
1207054020ee: Pushed 
a76be9efdb17: Pushed 
ee208316b1de: Pushed 
aa621ecc8262: Pushed 
85cbe3c3bbc1: Pushed 
b33ff346ea32: Pushed 
1e70059397e5: Pushed 
afd7e44a4e08: Pushed 
v1: digest: sha256:9cdbee15989a371e8abf3c36db61753c3d4bf68622ba15d09c2ee03418c05abb size: 3881
```



`az acr repository list --name  prodfixdseus2tmlengacr01 --output table`

```
Result
--------------------
ado-base-agent
ado-databricks-agent
ado-java-agent
ado-node-agent
ado-python-agent
dai-func-service-bus
dai-hdfs2adls
dsdeploy
```


``

```

```


``

```

```
