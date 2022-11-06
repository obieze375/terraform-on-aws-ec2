# Terraform Command Basics

## Step-01: Introduction
- Understand basic Terraform Commands
  - terraform init
  - terraform validate
  - terraform plan
  - terraform apply
  - terraform destroy      

## Step-02: Review terraform manifest for EC2 Instance
- **Pre-Conditions-1:** Ensure you have **default-vpc** in that respective region
- **Pre-Conditions-2:** Ensure AMI you are provisioning exists in that region if not update AMI ID 
- **Pre-Conditions-3:** Verify your AWS Credentials in **$HOME/.aws/credentials**
```t
# Terraform Settings Block
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      #version = "~> 3.21" # Optional but recommended in production
    }
  }
}

# Provider Block
provider "aws" {
  profile = "default" # AWS Credentials Profile configured on your local desktop terminal  $HOME/.aws/credentials
  region  = "us-east-1"
}

# Resource Block
resource "aws_instance" "ec2demo" {
  ami           = "ami-04d29b6f966df1537" # Amazon Linux in us-east-1, update as per your region
  instance_type = "t2.micro"
}
```

## Step-03: Terraform Core Commands
```t
# Initialize Terraform
terraform init

# Terraform Validate
terraform validate

# Terraform Plan to Verify what it is going to create / update / destroy
terraform plan

# Terraform Apply to Create EC2 Instance
terraform apply 
```

## Step-04: Verify the EC2 Instance in AWS Management Console
- Go to AWS Management Console -> Services -> EC2
- Verify newly created EC2 instance



## Step-05: Destroy Infrastructure
```t
# Destroy EC2 Instance
terraform destroy

# Delete Terraform files 
rm -rf .terraform*
rm -rf terraform.tfstate*
```

## Step-08: Conclusion
- Re-iterate what we have learned in this section
- Learned about Important Terraform Commands
  - terraform init
  - terraform init -- upgrade -> For updating module changes locally for testing
  - terraform validate
  - terraform plan
  - terraform apply
  - terraform destroy
  - terraform apply -auto-approve
  - terraform destroy -auto-approve


# How to use terraform plan

### Using [Terraform Visual](https://hieven.github.io/terraform-visual/)
For people who want to quickly experience how Terraform Visual looks like

1. Generate Terraform plan in JSON format

```shell
$ terraform plan -out=plan.out                # Run plan and output as a file
$ terraform show -json plan.out > plan.json   # Read plan file and output it in JSON format
```

2. Visit [Terraform Visual](https://hieven.github.io/terraform-visual/)

3. Upload Terraform JSON to the platform

### Using [CLI](https://www.npmjs.com/package/@terraform-visual/cli)
For people who don't like to upload Terraform plan to public internet. You could install the CLI tool via NPM.

Please refer to [@terraform-visual/cli](https://www.npmjs.com/package/@terraform-visual/cli) for more details

1. Install CLI
```sh
# Using Yarn
$ yarn global add @terraform-visual/cli

# Using NPM
$ npm install -g @terraform-visual/cli
```

2. Convert Terraform Plan into JSON File
```sh
$ terraform plan -out=plan.out                # Run plan and output as a file
$ terraform show -json plan.out > plan.json   # Read plan file and output it in JSON format
```

3. Create Terraform Visual Report
```sh
$ terraform-visual --plan plan.json
```

4. Browse The Report
```sh
$ open terraform-visual-report/index.html
```

### Using [Docker](https://hub.docker.com/r/hieven/terraform-visual-cli)

For people who likes Terraform Visual and wanto to integrate it into existing CI/CD pipeline.

The Docker image is on top of offical Terraform + Terraform Visual CLI.

You can simply replace the Terraform image in your CI/CD piepline with this one and enjoy the benefit of both command line tools.

For more details, please refer to [Docker: Terraform-Visual](https://hub.docker.com/r/hieven/terraform-visual-cli)


