### What is Terragrunt

Terragrunt is an additional wrapper that is built on top of the Terraform. Terraform is a great Infrastructure as Code tool for managing your cloud infrastructure. But as the project size grows and you have multiple environments (Development, Testing, Staging, Production, etc..) to manage then you will realize Terraform has a lot of gaps for managing a complex and large project.

## Challenges with Terraform

If you are managing multiple environments (Development, Testing, Staging, and Production etc..) infrastructure with Terraform then here are the challenges you might face with Terraform -

## Redundancy of code 

Multiple copies of the same code for each environment.
Manual update of code - If there are the same variables that are being used for all the environments then you have to remember and manually update each variable.
Terragrunt by gruntwork was built to improve the shortcomings around the Terraform for effectively managing the infrastructure code so that developers can use the same code without any kind of duplication by keeping the terraform code dry. Terragrunt not only helps you with managing your terraform workspaces effectively but it can also help you with multiple terraform modules, managing Terraform remote state, etc. 

### Installation 
~~~~

$ wget https://github.com/gruntwork-io/terragrunt/releases/download/v0.18.7/terragrunt_linux_amd64
$ mv terragrunt_linux_amd64 terragrunt
$ chmod +x terragrunt
$ sudo mv terragrunt /usr/local/bin

~~~~

## Terragrunt Commands

~~~~

terragrunt init

terragrunt plan

terragrunt apply -auto-approve

terragrunt destroy -auto-approve

~~~~