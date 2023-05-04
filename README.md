# Automate-Infrastructure-With-IaC-using-Terraform.-Part-4 - Terraform-Cloud.

We will be introducing Packer and Ansible to our existing repository from Automate-Infrastructure-With-IaC-using-Terraform.-Part-3. The following files will be added:

* AMI: for building Packer images
* Ansible: for Ansible scripts to configure the infrastructure

### Action plan:

- Build images using Packer and verify the AMIs in the console.
- Update the Terraform script with the new AMI IDs generated from Packer build.
- Create a Terraform Cloud account and backend.
- Run the Terraform script.
- Update the Ansible script with values from the Terraform output, including:
     - RDS endpoints for WordPress and tooling
     - Database name, password, and username for WordPress and tooling
     - Access point ID for WordPress and tooling
     - Internal load balancer DNS for nginx reverse proxy
- Run the Ansible script.
- Check the website.
Overall, this project will involve using Packer to build images, Ansible to configure infrastructure, and Terraform to manage the infrastructure. The goal is to ensure a reliable and scalable infrastructure for hosting a WordPress and Tooling site.



Run the packer build command for each of the necessary files, and verify that the Amazon Machine Images (AMIs) were successfully created in the console.
