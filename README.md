# Automate-Infrastructure-With-IaC-using-Terraform.-Part-4 ---Terraform-Cloud.

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


You need to update the IDs of the new AMIs generated from the packer build in the Terraform script

![sr15](https://user-images.githubusercontent.com/94229949/236206126-2755adc4-d01a-4dab-b8e5-8a9cd4a08118.png)

![sr16](https://user-images.githubusercontent.com/94229949/236206147-bce57b3f-7e3c-4cd2-ace6-18048666aeb8.png)

To use Terraform Cloud, you need to create an account and backend. Once you have created the account, connect it with your GitHub repository that contains the Terraform script. This connection will create a workspace in the account. The workspace will be used for running all Terraform commands such as 'plan', 'apply', and 'destroy'.

With the workspace, Terraform Cloud can detect any changes made in the repository and will run the code just like running terraform plan. You can apply the changes on the Terraform Cloud UI.


![sr17](https://user-images.githubusercontent.com/94229949/236208043-e32734bf-a20e-474f-ac02-5577a7520c28.png)

![sr18](https://user-images.githubusercontent.com/94229949/236208073-3062ce19-17de-4f97-b273-ea743a6c89ea.png)


Before we can run the Ansible script, we need to configure the AWS CLI with our credentials by running aws configure and entering the necessary information.

Also, we need to enable ssh-agent on our bastion instance so that we can easily SSH into the servers.

Once that is done, we can update our Ansible script with the following values:

   - RDS endpoints for Wordpress and Tooling
   - Database name, password, and username for Wordpress and Tooling
   - Access point ID for Wordpress and Tooling
   - Internal load balancer DNS for Nginx reverse proxy

![sr20](https://user-images.githubusercontent.com/94229949/236217559-27ffd6c3-6b68-4b62-b901-3fd7c5390531.png)


![sr21](https://user-images.githubusercontent.com/94229949/236217613-ebe5ce54-e0dc-4c88-9461-2db8b37f48fe.png)

![sr22](https://user-images.githubusercontent.com/94229949/236217646-8ce046a2-9285-4fa1-9f48-2f0ecc307592.png)


Run ansible-playbook -i inventory/aws_ec2.yml playbooks/site.yml to configure the infrastructure.

![sr23](https://user-images.githubusercontent.com/94229949/236217680-20e79035-d2af-4486-be99-59c7d451d3d1.png)


After updating the Ansible script with the necessary values, it's important to confirm that all configurations were implemented correctly. You can do this by running the Ansible script and checking the website to ensure that it's running as expected. Additionally, you can verify the RDS endpoints for WordPress and tooling, database name, password and username for WordPress and tooling, access point ID for WordPress and tooling, and internal load balancer DNS for Nginx reverse proxy to ensure that they match what you provided

![sr24](https://user-images.githubusercontent.com/94229949/236221170-09884956-2919-4381-8066-e1ce6cc43fb0.png)


![sr25](https://user-images.githubusercontent.com/94229949/236221223-7e60d155-8d54-4153-9a07-f0e66a5d04f0.png)


![sr26](https://user-images.githubusercontent.com/94229949/236221255-228478f2-eb80-43ea-a708-b60f7a1991da.png)

![sr27](https://user-images.githubusercontent.com/94229949/236221277-6f34a8d7-d919-4c5d-8e8f-44a7c4f0bf3e.png)

![sr12](https://user-images.githubusercontent.com/94229949/236222109-3f12beca-7ecc-4324-9898-eb899fa6d7da.png)

![sr13](https://user-images.githubusercontent.com/94229949/236222132-63bbf5bc-913e-4f4b-bb04-93749b560db6.png)

![sr14](https://user-images.githubusercontent.com/94229949/236222163-749d7512-92ce-4304-b100-6c7fe85acea2.png)

Check all websites are functioning correctly

# Tooling Site
![sr28](https://user-images.githubusercontent.com/94229949/236222471-cdff2006-f57a-47d5-a31a-fbffb387bdf0.png)

# Wordpress Site

![sr29](https://user-images.githubusercontent.com/94229949/236223011-1b7fda3e-5cf0-4833-ad84-4c1646df8890.png)


