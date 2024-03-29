# Introduction
Testing out Pulumi  "Modern infrastructure as code" Azure Nextgen Python libraries to create Azure Resource Group, storage account and Kubernetes cluster (AKS)

## Prerequisites
pipenv, version 2022.1.8

Note: New pulumi version comes out with venv by default.

pulumi v3.26.1

azure-cli  2.34.1

Python 3.10.0

## Create a new project
Using existing azure-nextgen-python template:

```
mkdir pulumi-azure-nextgen
pulumi new  azure-nextgen-python -g

Note: I'm using -g do not install default venv as I'm using pipenv.
```

## Development
Set up virtualenv:
```
pipenv shell
pipenv install
pipenv install --dev

```
IaC is defined in __main__.py.

## Pulumi in action

Deploy infrastructure:
```
pulumi up
Previewing update (dev)


     Type                                             Name               Plan       
 +   pulumi:pulumi:Stack                              azure-nextgen-dev  create     
 +   ├─ azure-nextgen:resources/latest:ResourceGroup  resource_group     create     
 +   └─ azure-nextgen:storage/latest:StorageAccount   sa                 create     
 
Resources:
    + 3 to create

Do you want to perform this update?  [Use arrows to move, enter to select, type to filter]
> yes
  no
  details


```

For viewing stack output (connection strings etc):
```
pulumi stack output
Current stack outputs (1):
    OUTPUT               VALUE
    primary_storage_key  <value>
```

To destroy resources:
```
pulumi destroy

Previewing destroy (dev)


     Type                                             Name               Plan       
 -   pulumi:pulumi:Stack                              azure-nextgen-dev  delete     
 -   ├─ azure-nextgen:storage/latest:StorageAccount   sa                 delete     
 -   └─ azure-nextgen:resources/latest:ResourceGroup  resource_group     delete     
 
Outputs:
  - primary_storage_key: "<key>"

Resources:
    - 3 to delete

Do you want to perform this destroy?  [Use arrows to move, enter to select, type to filter]
> yes
  no
  details
```

To deploy k8s cluster follow guide in https://www.pulumi.com/registry/packages/kubernetes/how-to-guides/aks/

# Links
https://www.pulumi.com/docs/reference/pkg/azure-nextgen/
https://www.pulumi.com/registry/packages/kubernetes/how-to-guides/aks/
