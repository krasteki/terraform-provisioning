# Learn Terraform Provisioning
Companion code repository for learning to provision Terraform instances with `cloud-init`

Follow along on the [HashiCorp Learn platform](https://learn.hashicorp.com/tutorials/terraform/cloud-init?in=terraform/provision)

I. Create a local SSH key

For this tutorial, create a local SSH key to pair with the new terraform user you create on this instance.

Generate a new SSH key in your terminal called tf-cloud-init. The argument provided with the -f flag creates the key in the current directory and creates two files called tf-cloud-init and tf-cloud-init.pub. Change the placeholder email address to your email address.

`$ ssh-keygen -t rsa -C "your_email@example.com" -f ./tf-cloud-init`


scripts/add-ssh-web-app.yaml file and paste the contents of tf-cloud-init.pub into the user data ssh_authorized_keys section. You will pass this cloud-init script to your instance resource's user_data attribute.


Create a new file called terraform.tfvars then add your AWS region variable definition.  `eu-west-2`

`$ terraform init`
`$ terraform apply`

Verify instance

`$ ssh terraform@$(terraform output -raw public_ip) -i ../tf-cloud-init`

Navigate to Go directory

`$ cd go/src/github.com/hashicorp/learn-go-webapp-demo`

`$ go run webapp.go`

on port 8080 the app should be available

`$ terraform destroy`