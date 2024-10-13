# AWS VPC using Terraform
In our previous project, we manually created a VPC, subnets, route tables, and other services in AWS. While this approach worked, doing things manually can be time-consuming and prone to errors. Imagine if you had to create hundreds of resources—doing it one by one would be overwhelming.

In the world of DevOps, automation is your best friend. Automating tasks not only saves time but also reduces the risk of human error. This is where Infrastructure as Code (IaC) comes into play. IaC allows you to define your infrastructure using code, making it repeatable, consistent, and scalable.

Two popular tools for IaC are Terraform and CloudFormation, but in this project, we’ll be focusing on Terraform.

# What is Infrastructure as Code (IaC)?
Infrastructure as Code (IaC) is a key DevOps practice that involves managing and provisioning computing infrastructure through machine-readable configuration files, rather than through physical hardware configuration or interactive configuration tools. This approach brings several benefits:

1. Automation: Automating the setup of infrastructure reduces manual errors, increases efficiency, and speeds up the deployment process.
Consistency: Ensures that the same environment is provisioned every time, reducing discrepancies between different environments (e.g., development, testing, production).
2. Version Control: Infrastructure configurations can be versioned and stored in repositories (e.g., Git), allowing teams to track changes, revert to previous states, and collaborate more effectively.
3. Scalability: IaC makes it easier to scale infrastructure up or down by simply modifying the configuration files.

## Why Use Terraform?
Terraform is a popular IaC tool developed by HashiCorp. It allows you to define, provision, and manage infrastructure across various cloud providers and services using a high-level configuration language. Some of the key features and benefits of Terraform include:

1. Multi-Provider Support: Terraform supports a wide range of cloud providers (e.g., AWS, Azure, Google Cloud), making it a versatile tool for managing infrastructure across different platforms.
2. Declarative Language: Terraform uses a declarative language (HashiCorp Configuration Language - HCL) to define infrastructure. This means you describe the desired state of your infrastructure, and Terraform takes care of achieving that state.
3. State Management: Terraform keeps track of the state of your infrastructure, allowing it to detect changes and apply only the necessary updates. This state management is crucial for maintaining the consistency of your infrastructure.
4. Modularity: Terraform supports the use of modules, which are reusable components that encapsulate specific pieces of infrastructure. This modularity promotes code reuse and simplifies the management of complex infrastructures.
5. Community and Ecosystem: Terraform has a vibrant community and a rich ecosystem of providers and modules, making it easier to find resources and get support.



---

## This guide provides an overview of key Terraform commands to help you manage your infrastructure efficiently.


### `terraform init`

**Purpose**: Initializes a new or existing Terraform working directory**Usage**: Prepares your directory for Terraform operations by downloading necessary provider plugins.

```bash
terraform init
```

### `terraform plan`

**Purpose**: Creates an execution plan showing what changes Terraform will make to your infrastructure.

**Usage**: Review planned changes before applying them.

```bash
terraform plan
```

### `terraform apply`

**Purpose**: Applies the changes required to reach the desired state as defined in your configuration files.

**Usage**: Executes the actions proposed by `terraform plan`.

```bash
terraform apply
```

### `terraform destroy`

**Purpose**: Destroys the Terraform-managed infrastructure.

**Usage**: Removes all resources defined in your configuration files.

```bash
terraform destroy
```

### `terraform validate`

**Purpose**: Validates the configuration files for syntax and internal consistency.

**Usage**: Checks for errors before running other commands.

```bash
terraform validate
```

### `terraform fmt`

**Purpose**: Formats Terraform configuration files to follow a canonical style.

**Usage**: Ensures consistent formatting of your configuration files.

```bash
terraform fmt
```

### `terraform show`

**Purpose**: Displays a human-readable output of the state or plan.

**Usage**: Inspects the current state or details of a plan.

```bash
terraform show
```

### `terraform output`

**Purpose**: Reads and displays the values of output variables from the state file.

**Usage**: Accesses outputs defined in your configuration.

```bash
terraform output
```

### `terraform state`

**Purpose**: Advanced management of the Terraform state file.

**Usage**: Includes subcommands to inspect and modify the state.

```bash
terraform state list
```


For more detailed information about this commands, visit the [Terraform Documentation](https://www.terraform.io/docs).
## To do this project you need to have the following.

1. A Valid AWS account with full permissions to create and manage AWS VPC service.
2. Setup terraform on an ec2 instance, ensure you have a valid IAM role attached to the instance with VPC provisioning permissions.


We are going to spin up an ec2 instance and attach the following IAM roles to it:

- AmazonVPCFullAccess
- AmazonEC2FullAccess

 ![pic](img/Screenshot%20(574).png)

 ![pic](img/Screenshot%20(575).png)

  ![pic](img/Screenshot%20(576).png)

   ![pic](img/Screenshot%20(577).png)

   ![pic](img/Screenshot%20(578).png)

![pic](img/Screenshot%20(579).png)

![pic](img/Screenshot%20(580).png)

![pic](img/Screenshot%20(581).png)

![pic](img/Screenshot%20(582).png)
![pic](img/Screenshot%20(583).png)
![pic](img/Screenshot%20(584).png)

![pic](img/Screenshot%20(585).png)

## Now create an EC2 instance, Ubuntu 22.04

## let us the attach the role created earlier to the instance

![pic](img/Screenshot%20(586).png)

![pic](img/Screenshot%20(588).png)

![pic](img/Screenshot%20(589).png)

![pic](img/Screenshot%20(590).png)


##  Connect to your instance via ssh 

- ssh into the instance
- install terraform
```
sudo snap install terraform

```

# Terraform AWS VPC Creation Workflow

Note: The VPC and subnets for this demo is created based on the VPC design document.

We will be creating the VPC with the following

1. CIDR Block: 10.0.0.0/16
2. Region: us-west-2
3. Availability Zones: us-west-2a, us-west-2b, us-west-2c
4. Subnets: 15 Subnets (One per availability Zone)
5. Public Sunets (3)
6. App Subets (3)
7. DB Subnets (3)
8. Management Subnet (3)
9. Platform Subnet (3)
10. NAT Gateway for Private subnets
11. Internet Gateway for public subnets.

## Step 1:  Clone thge repo into the instance and CD in the Cloned Repository
- clone it using the following command.
```
git clone https://github.com/TobiOlajumoke/Terraform-VPC.git
```

- Then cd in to the terraform-vpc folder
```
cd terraform-vpc
```





![pic](img)

![pic](img)


![pic](img)

