# Terraform_Workspaces_Notes

Workspaces in Terraform are simply independently managed state files. A workspace contains everything that Terraform needs to manage a given collection of infrastructure, and separate Workspaces function like completely separate working directories. We can manage multiple environments with Workspaces.

- With Workspaces, we can set deploy different environment with same terraform configuration files.
- To manage multiple distinct sets of infrastructure resources (e.g. multiple environments), we can use Workspaces.
- Workspaces isolate Terraform state. It is a best practice to have separate state per environment. Workspaces are technically equivalent to renaming your state file.
- Workspaces ensure that the environments are isolated and mirrored.
- Workspaces are the successor to old Terraform Environments.

---
# Implementation

If only one environment
```
terraform init   
```
```
terraform plan
```
```
terraform apply 
```
To apply a particular tfvars (stage.tfvars) use below
```
terraform apply -var-file=stage.tfvars
```

1. Create a new workspace in Terraform 
```
terraform workspace new dev
```
```
terraform workspace new stage
```
```
terraform workspace new prod
```


2. To switch to a particular workspace
```
terraform workspace select dev
```

```
terraform workspace show
```
(This shows the current working workspace)


3. Now initialize and apply the Terraform in particular workspace
```
terraform init 
```
```
terraform apply
```


4. Now switch to a different workspace
```
terraform workspace select stage
```


5. Apply the configuration in the selected workspace
```
terraform apply
```

Similarly, you can perform for prod
