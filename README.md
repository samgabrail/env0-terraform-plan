# Overview

This is a tutorial to teach how to use `terraform plan`.

## Demo Steps

### Creation of a New Resource

1. Check the `main.tf`, `variables.tf`, and `terraform.tfvars` files.
2. Run `terraform init`
3. Run `terraform plan`
4. Run `terraform apply`
5. Run `docker ps`
6. Go to the ports tab and view the NGINX welcome screen

### Modification of an Existing Resource

1. Change the restart to `restart = "on-failure"` in `main.tf`
2. Run `terraform plan`
3. Change the external port to `8081` in `terraform.tfvars`
4. Run `terraform plan`

### Deletion of an Existing Resource

1. Comment out the `docker_container` resource in `main.tf`
2. Run `terraform plan`
3. Run `terraform apply`

### Refresh Only Mode

1. Run `terraform apply`
2. Run `docker rmi nginx:1.23.3`
3. Run `terraform plan -refresh-only`
4. Check `terraform.tfstate`
5. Run `terraform apply -refresh-only`
6. Check `terraform.tfstate` again

### The -out Flag

1. Run `terraform plan -out tfplan`
2. Run `terraform apply tfplan`

### The -replace Flag

1. Run `terraform plan -replace docker_container.nginx_container`
2. Run `terraform apply -replace docker_container.nginx_container`

### The -var and -var-file Flags

1. Comment out all the contents of the `terraform.tfvars` file
2. Run `terraform plan`
3. Run `terraform plan -var image_name=nginx -var image_tag=1.23.3`
4. Check the `my_variables_file` in the `a_random_directory` folder
5. Run `terraform plan -var-file a_random_directory/my_variables_file.txt`

### The -destroy Flag

1. Run `terraform plan -destroy`
2. Run `terraform apply -destroy`

### Resource Targeting

1. Run `terraform apply`
2. Change the `image_tag` from `1.23.3` to `1.23.1` in the `terraform.tfvars` file
3. Run `terraform plan`
4. Run `terraform plan -target docker_image.nginx_image`
5. Run `terraform apply -target docker_image.nginx_image`
