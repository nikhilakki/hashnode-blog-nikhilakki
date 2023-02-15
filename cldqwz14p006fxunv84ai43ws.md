# Introduction to Terraform

Terraform is an infrastructure as code (IAC) tool that enables you to define, configure, and deploy cloud infrastructure using a high-level configuration language. It supports multiple cloud providers, including AWS, GCP, and Azure, as well as on-premises and other infrastructure. Terraform allows you to automate the process of creating, updating, and deleting infrastructure, making it easier to manage your infrastructure consistently and repeatably.

Here's a simple example of how Terraform can be used to provision an Amazon Web Services (AWS) EC2 instance.

```ini
provider "aws" {
  region = "ap-south-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c33b869cb23fe1f0"
  instance_type = "t2.micro"
}
```

In this example, the `provider` block declares that we're using AWS as our cloud provider. The `resource` block creates an EC2 instance using the specified Amazon Machine Image (AMI) and instance type. By running the Terraform configuration, this EC2 instance will be created in the specified AWS region.

This is just a simple example, but Terraform can be used to manage much more complex infrastructure, including multiple resources and dependencies between them.

To run this Terraform configuration, you'll need to have Terraform installed on your local machine.

%[https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli] 

Then, you can follow these steps:

1. Initialize Terraform: Run `terraform init` in the directory where your Terraform configuration files are located. This will download the necessary plugins and modules for the specified provider (in this case, AWS).
    
2. Preview the changes: Run `terraform plan`. This will show you what changes Terraform will make to your infrastructure without actually making them. This allows you to review the changes before applying them.
    
3. Apply the changes: Run `terraform apply`. This will apply the changes to your infrastructure and create the EC2 instance. Terraform will prompt you to confirm the changes before applying them.
    
4. Destroy the infrastructure: If you want to delete the EC2 instance, run `terraform destroy`. This will remove the infrastructure and return your environment to its pre-existing state.
    

These steps should get you started with running Terraform, but I recommend checking out the Terraform documentation for more information and best practices.

### References

%[https://developer.hashicorp.com/terraform/docs] 

%[https://spacelift.io/blog/terraform-tutorial]