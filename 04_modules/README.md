# Modules

Terraform modules allow you to write reusable infrastructure components which you can combine like lego blocks
to build your data platform. By grouping resources together in a module, you create abstractions that behave just like
other Terraform resources. Sometimes such abstractions are so common or useful that people release them as open source modules 
(see for example https://github.com/cloudposse/terraform-aws-rds)

## Goal of this exercise

In this exercise you will create a `secure_notebook` module. A secure notebook is a SageMaker notebook 
instance with a security group attached to it. The module should have three input parameters:
- the name of the secure notebook
- the instance type of the secure notebook
- one or multiple IP addresses that are allowed to connect over SSH to the secure notebook

You don't have to create a new VPC, subnet or IAM role for the secure notebook; they have been created for you, 
and their ID's / ARN's have been stored as SSM parameters, which you can read in as a data source with the following paths:
- /terraform_workshop/notebook_role
- /terraform_workshop/notebook_vpc_id
- /terraform_workshop/notebook_subnet_id