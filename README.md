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
![image](https://github.com/Pavan-1997/Terraform_Workspaces_Notes/assets/32020205/3a33f0d3-d0ba-436a-a2bc-05052de376bb)


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
![image](https://github.com/Pavan-1997/Terraform_Workspaces_Notes/assets/32020205/d0d43aad-7d59-452d-80a3-05bb050be1e1)


4. Now switch to a different workspace
```
terraform workspace select stage
```


5. Apply the configuration in the selected workspace
```
terraform apply
```

Similarly, you can perform for prod

![image](https://github.com/Pavan-1997/Terraform_Workspaces_Notes/assets/32020205/fe68d4e9-43d8-4196-8bdc-826560e6ae33)

![image](https://github.com/Pavan-1997/Terraform_Workspaces_Notes/assets/32020205/b77455ff-c5c2-4c3a-a5b1-844824058fc7)

