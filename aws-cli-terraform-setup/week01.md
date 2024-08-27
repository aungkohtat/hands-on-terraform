

## Setting Up Terraform, AWS CLI, and Your AWS Environment
![](./images/aws%20diagram.webp)

This guide walks you through the process of setting up your AWS environment and installing Terraform on your system.

### Step 1: Setting Up Your AWS Account
1. **Sign Up for AWS**: Create an AWS account.
2. **Access Root User**: Use the root account only to create other users with limited permissions.
3. **Access IAM**: Navigate to the IAM console to manage user accounts.
4. **Add a New User**: Create a new IAM user with programmatic access.
5. **Assign Permissions**: Attach the necessary IAM policies to the new user.
6. **Attach AdministratorAccess Policy**: For learning, attach the AdministratorAccess policy.
7. **Get AWS Credentials**: Save the Access Key ID and Secret Access Key.

### Step 2: Installing Terraform
1. **Download Terraform**: Get the appropriate Terraform package for your OS.
2. **Extract the ZIP File**: Unzip the downloaded file to a chosen directory.
3. **Add Terraform to PATH**: Update your system's PATH to include the Terraform directory.
4. **Verify Installation**: Run `terraform` in the Command Prompt to confirm installation.


### 1. Prepare Your Workstation: Navigate to VSCode and go to the Terraform Directory:
### 2. Create Terraform Configuration Files: Create two files: main.tf and variables.tf
### 3. Define Variables in variables.tf : add the following content to variables.tf file :


## running terraform cli
```
terraform init
terraform plan
terraform apply
terraform destroy

```


### output

```
vagrant@cloud-native-box:~/hands-on-terraform/aws-cli-terraform-setup$ terraform init
Initializing the backend...
Initializing provider plugins...
- Finding latest version of hashicorp/aws...
- Installing hashicorp/aws v5.64.0...
- Installed hashicorp/aws v5.64.0 (signed by HashiCorp)
Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
vagrant@cloud-native-box:~/hands-on-terraform/aws-cli-terraform-setup$ terraform plan
data.aws_availability_zones.available: Reading...
data.aws_availability_zones.available: Read complete after 1s [id=us-east-1]

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # aws_eip.nat_gateway_eip will be created
  + resource "aws_eip" "nat_gateway_eip" {
      + allocation_id        = (known after apply)
      + arn                  = (known after apply)
      + association_id       = (known after apply)
      + carrier_ip           = (known after apply)
      + customer_owned_ip    = (known after apply)
      + domain               = "vpc"
      + id                   = (known after apply)
      + instance             = (known after apply)
      + network_border_group = (known after apply)
      + network_interface    = (known after apply)
      + private_dns          = (known after apply)
      + private_ip           = (known after apply)
      + ptr_record           = (known after apply)
      + public_dns           = (known after apply)
      + public_ip            = (known after apply)
      + public_ipv4_pool     = (known after apply)
      + tags                 = {
          + "Name" = "demo_nat_gateway_eip"
        }
      + tags_all             = {
          + "Name" = "demo_nat_gateway_eip"
        }
      + vpc                  = (known after apply)
    }

  # aws_internet_gateway.internet_gateway will be created
  + resource "aws_internet_gateway" "internet_gateway" {
      + arn      = (known after apply)
      + id       = (known after apply)
      + owner_id = (known after apply)
      + tags     = {
          + "Name" = "demo_igw"
        }
      + tags_all = {
          + "Name" = "demo_igw"
        }
      + vpc_id   = (known after apply)
    }

  # aws_nat_gateway.nat_gateway will be created
  + resource "aws_nat_gateway" "nat_gateway" {
      + allocation_id                      = (known after apply)
      + association_id                     = (known after apply)
      + connectivity_type                  = "public"
      + id                                 = (known after apply)
      + network_interface_id               = (known after apply)
      + private_ip                         = (known after apply)
      + public_ip                          = (known after apply)
      + secondary_private_ip_address_count = (known after apply)
      + secondary_private_ip_addresses     = (known after apply)
      + subnet_id                          = (known after apply)
      + tags                               = {
          + "Name" = "demo_nat_gateway"
        }
      + tags_all                           = {
          + "Name" = "demo_nat_gateway"
        }
    }

  # aws_route_table.private_route_table will be created
  + resource "aws_route_table" "private_route_table" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + cidr_block                 = "0.0.0.0/0"
              + nat_gateway_id             = (known after apply)
                # (11 unchanged attributes hidden)
            },
        ]
      + tags             = {
          + "Name"      = "demo_private_rtb"
          + "Terraform" = "true"
        }
      + tags_all         = {
          + "Name"      = "demo_private_rtb"
          + "Terraform" = "true"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table.public_route_table will be created
  + resource "aws_route_table" "public_route_table" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + cidr_block                 = "0.0.0.0/0"
              + gateway_id                 = (known after apply)
                # (11 unchanged attributes hidden)
            },
        ]
      + tags             = {
          + "Name"      = "demo_public_rtb"
          + "Terraform" = "true"
        }
      + tags_all         = {
          + "Name"      = "demo_public_rtb"
          + "Terraform" = "true"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table_association.private["private_subnet_1"] will be created
  + resource "aws_route_table_association" "private" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.private["private_subnet_2"] will be created
  + resource "aws_route_table_association" "private" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.private["private_subnet_3"] will be created
  + resource "aws_route_table_association" "private" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.public["public_subnet_1"] will be created
  + resource "aws_route_table_association" "public" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.public["public_subnet_2"] will be created
  + resource "aws_route_table_association" "public" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.public["public_subnet_3"] will be created
  + resource "aws_route_table_association" "public" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_subnet.private_subnets["private_subnet_1"] will be created
  + resource "aws_subnet" "private_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1b"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.1.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "private_subnet_1"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "private_subnet_1"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.private_subnets["private_subnet_2"] will be created
  + resource "aws_subnet" "private_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1c"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.2.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "private_subnet_2"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "private_subnet_2"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.private_subnets["private_subnet_3"] will be created
  + resource "aws_subnet" "private_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1d"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.3.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "private_subnet_3"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "private_subnet_3"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.public_subnets["public_subnet_1"] will be created
  + resource "aws_subnet" "public_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1b"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.101.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = true
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "public_subnet_1"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "public_subnet_1"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.public_subnets["public_subnet_2"] will be created
  + resource "aws_subnet" "public_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1c"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.102.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = true
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "public_subnet_2"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "public_subnet_2"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.public_subnets["public_subnet_3"] will be created
  + resource "aws_subnet" "public_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1d"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.103.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = true
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "public_subnet_3"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "public_subnet_3"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_vpc.vpc will be created
  + resource "aws_vpc" "vpc" {
      + arn                                  = (known after apply)
      + cidr_block                           = "10.0.0.0/16"
      + default_network_acl_id               = (known after apply)
      + default_route_table_id               = (known after apply)
      + default_security_group_id            = (known after apply)
      + dhcp_options_id                      = (known after apply)
      + enable_dns_hostnames                 = (known after apply)
      + enable_dns_support                   = true
      + enable_network_address_usage_metrics = (known after apply)
      + id                                   = (known after apply)
      + instance_tenancy                     = "default"
      + ipv6_association_id                  = (known after apply)
      + ipv6_cidr_block                      = (known after apply)
      + ipv6_cidr_block_network_border_group = (known after apply)
      + main_route_table_id                  = (known after apply)
      + owner_id                             = (known after apply)
      + tags                                 = {
          + "Environment" = "demo_environment"
          + "Name"        = "demo_vpc"
          + "Terraform"   = "true"
        }
      + tags_all                             = {
          + "Environment" = "demo_environment"
          + "Name"        = "demo_vpc"
          + "Terraform"   = "true"
        }
    }

Plan: 18 to add, 0 to change, 0 to destroy.

────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

Note: You didn't use the -out option to save this plan, so Terraform can't guarantee to take exactly these actions if you run "terraform apply" now.
vagrant@cloud-native-box:~/hands-on-terraform/aws-cli-terraform-setup$ terraform apply
data.aws_availability_zones.available: Reading...
data.aws_availability_zones.available: Read complete after 1s [id=us-east-1]

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # aws_eip.nat_gateway_eip will be created
  + resource "aws_eip" "nat_gateway_eip" {
      + allocation_id        = (known after apply)
      + arn                  = (known after apply)
      + association_id       = (known after apply)
      + carrier_ip           = (known after apply)
      + customer_owned_ip    = (known after apply)
      + domain               = "vpc"
      + id                   = (known after apply)
      + instance             = (known after apply)
      + network_border_group = (known after apply)
      + network_interface    = (known after apply)
      + private_dns          = (known after apply)
      + private_ip           = (known after apply)
      + ptr_record           = (known after apply)
      + public_dns           = (known after apply)
      + public_ip            = (known after apply)
      + public_ipv4_pool     = (known after apply)
      + tags                 = {
          + "Name" = "demo_nat_gateway_eip"
        }
      + tags_all             = {
          + "Name" = "demo_nat_gateway_eip"
        }
      + vpc                  = (known after apply)
    }

  # aws_internet_gateway.internet_gateway will be created
  + resource "aws_internet_gateway" "internet_gateway" {
      + arn      = (known after apply)
      + id       = (known after apply)
      + owner_id = (known after apply)
      + tags     = {
          + "Name" = "demo_igw"
        }
      + tags_all = {
          + "Name" = "demo_igw"
        }
      + vpc_id   = (known after apply)
    }

  # aws_nat_gateway.nat_gateway will be created
  + resource "aws_nat_gateway" "nat_gateway" {
      + allocation_id                      = (known after apply)
      + association_id                     = (known after apply)
      + connectivity_type                  = "public"
      + id                                 = (known after apply)
      + network_interface_id               = (known after apply)
      + private_ip                         = (known after apply)
      + public_ip                          = (known after apply)
      + secondary_private_ip_address_count = (known after apply)
      + secondary_private_ip_addresses     = (known after apply)
      + subnet_id                          = (known after apply)
      + tags                               = {
          + "Name" = "demo_nat_gateway"
        }
      + tags_all                           = {
          + "Name" = "demo_nat_gateway"
        }
    }

  # aws_route_table.private_route_table will be created
  + resource "aws_route_table" "private_route_table" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + cidr_block                 = "0.0.0.0/0"
              + nat_gateway_id             = (known after apply)
                # (11 unchanged attributes hidden)
            },
        ]
      + tags             = {
          + "Name"      = "demo_private_rtb"
          + "Terraform" = "true"
        }
      + tags_all         = {
          + "Name"      = "demo_private_rtb"
          + "Terraform" = "true"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table.public_route_table will be created
  + resource "aws_route_table" "public_route_table" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + cidr_block                 = "0.0.0.0/0"
              + gateway_id                 = (known after apply)
                # (11 unchanged attributes hidden)
            },
        ]
      + tags             = {
          + "Name"      = "demo_public_rtb"
          + "Terraform" = "true"
        }
      + tags_all         = {
          + "Name"      = "demo_public_rtb"
          + "Terraform" = "true"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table_association.private["private_subnet_1"] will be created
  + resource "aws_route_table_association" "private" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.private["private_subnet_2"] will be created
  + resource "aws_route_table_association" "private" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.private["private_subnet_3"] will be created
  + resource "aws_route_table_association" "private" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.public["public_subnet_1"] will be created
  + resource "aws_route_table_association" "public" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.public["public_subnet_2"] will be created
  + resource "aws_route_table_association" "public" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.public["public_subnet_3"] will be created
  + resource "aws_route_table_association" "public" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_subnet.private_subnets["private_subnet_1"] will be created
  + resource "aws_subnet" "private_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1b"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.1.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "private_subnet_1"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "private_subnet_1"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.private_subnets["private_subnet_2"] will be created
  + resource "aws_subnet" "private_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1c"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.2.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "private_subnet_2"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "private_subnet_2"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.private_subnets["private_subnet_3"] will be created
  + resource "aws_subnet" "private_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1d"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.3.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "private_subnet_3"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "private_subnet_3"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.public_subnets["public_subnet_1"] will be created
  + resource "aws_subnet" "public_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1b"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.101.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = true
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "public_subnet_1"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "public_subnet_1"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.public_subnets["public_subnet_2"] will be created
  + resource "aws_subnet" "public_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1c"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.102.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = true
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "public_subnet_2"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "public_subnet_2"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.public_subnets["public_subnet_3"] will be created
  + resource "aws_subnet" "public_subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1d"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.103.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = true
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name"      = "public_subnet_3"
          + "Terraform" = "true"
        }
      + tags_all                                       = {
          + "Name"      = "public_subnet_3"
          + "Terraform" = "true"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_vpc.vpc will be created
  + resource "aws_vpc" "vpc" {
      + arn                                  = (known after apply)
      + cidr_block                           = "10.0.0.0/16"
      + default_network_acl_id               = (known after apply)
      + default_route_table_id               = (known after apply)
      + default_security_group_id            = (known after apply)
      + dhcp_options_id                      = (known after apply)
      + enable_dns_hostnames                 = (known after apply)
      + enable_dns_support                   = true
      + enable_network_address_usage_metrics = (known after apply)
      + id                                   = (known after apply)
      + instance_tenancy                     = "default"
      + ipv6_association_id                  = (known after apply)
      + ipv6_cidr_block                      = (known after apply)
      + ipv6_cidr_block_network_border_group = (known after apply)
      + main_route_table_id                  = (known after apply)
      + owner_id                             = (known after apply)
      + tags                                 = {
          + "Environment" = "demo_environment"
          + "Name"        = "demo_vpc"
          + "Terraform"   = "true"
        }
      + tags_all                             = {
          + "Environment" = "demo_environment"
          + "Name"        = "demo_vpc"
          + "Terraform"   = "true"
        }
    }

Plan: 18 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

aws_eip.nat_gateway_eip: Creating...
aws_vpc.vpc: Creating...
aws_eip.nat_gateway_eip: Creation complete after 3s [id=eipalloc-0f0895b1f82943775]
aws_vpc.vpc: Creation complete after 5s [id=vpc-0c5f81992b21ab9eb]
aws_subnet.private_subnets["private_subnet_1"]: Creating...
aws_internet_gateway.internet_gateway: Creating...
aws_subnet.private_subnets["private_subnet_2"]: Creating...
aws_subnet.public_subnets["public_subnet_2"]: Creating...
aws_subnet.public_subnets["public_subnet_3"]: Creating...
aws_subnet.private_subnets["private_subnet_3"]: Creating...
aws_subnet.public_subnets["public_subnet_1"]: Creating...
aws_subnet.private_subnets["private_subnet_2"]: Creation complete after 1s [id=subnet-0a4c3bfa7134229d9]
aws_subnet.private_subnets["private_subnet_1"]: Creation complete after 2s [id=subnet-0167ba9c47b945577]
aws_internet_gateway.internet_gateway: Creation complete after 2s [id=igw-098bca9f4fd3c0c75]
aws_subnet.private_subnets["private_subnet_3"]: Creation complete after 2s [id=subnet-0cd0331734357117e]
aws_route_table.public_route_table: Creating...
aws_route_table.public_route_table: Creation complete after 3s [id=rtb-033cf201a1cabd1bb]
aws_subnet.public_subnets["public_subnet_2"]: Still creating... [10s elapsed]
aws_subnet.public_subnets["public_subnet_3"]: Still creating... [10s elapsed]
aws_subnet.public_subnets["public_subnet_1"]: Still creating... [10s elapsed]
aws_subnet.public_subnets["public_subnet_2"]: Creation complete after 12s [id=subnet-0cc506dada5053d0f]
aws_subnet.public_subnets["public_subnet_3"]: Creation complete after 13s [id=subnet-08f1f1b0a502744fd]
aws_subnet.public_subnets["public_subnet_1"]: Creation complete after 13s [id=subnet-06c5d89a956fd7192]
aws_route_table_association.public["public_subnet_1"]: Creating...
aws_route_table_association.public["public_subnet_3"]: Creating...
aws_nat_gateway.nat_gateway: Creating...
aws_route_table_association.public["public_subnet_2"]: Creating...
aws_route_table_association.public["public_subnet_2"]: Creation complete after 1s [id=rtbassoc-075f1585c05bfeabe]
aws_route_table_association.public["public_subnet_3"]: Creation complete after 1s [id=rtbassoc-0b3106c8490b0426c]
aws_route_table_association.public["public_subnet_1"]: Creation complete after 1s [id=rtbassoc-057e9379f4f4ef822]
aws_nat_gateway.nat_gateway: Still creating... [10s elapsed]
aws_nat_gateway.nat_gateway: Still creating... [20s elapsed]
aws_nat_gateway.nat_gateway: Still creating... [30s elapsed]
aws_nat_gateway.nat_gateway: Still creating... [40s elapsed]
aws_nat_gateway.nat_gateway: Still creating... [50s elapsed]
aws_nat_gateway.nat_gateway: Still creating... [1m0s elapsed]
aws_nat_gateway.nat_gateway: Still creating... [1m10s elapsed]
aws_nat_gateway.nat_gateway: Still creating... [1m20s elapsed]
aws_nat_gateway.nat_gateway: Still creating... [1m30s elapsed]
aws_nat_gateway.nat_gateway: Still creating... [1m40s elapsed]
aws_nat_gateway.nat_gateway: Creation complete after 1m49s [id=nat-0bb9d1a0f4ef9ec0d]
aws_route_table.private_route_table: Creating...
aws_route_table.private_route_table: Creation complete after 2s [id=rtb-09e882e14f593b0da]
aws_route_table_association.private["private_subnet_2"]: Creating...
aws_route_table_association.private["private_subnet_1"]: Creating...
aws_route_table_association.private["private_subnet_3"]: Creating...
aws_route_table_association.private["private_subnet_2"]: Creation complete after 2s [id=rtbassoc-0c799784283847a32]
aws_route_table_association.private["private_subnet_1"]: Creation complete after 2s [id=rtbassoc-0d81dc2b2705012a4]
aws_route_table_association.private["private_subnet_3"]: Creation complete after 3s [id=rtbassoc-07f717853e6c723e2]

Apply complete! Resources: 18 added, 0 changed, 0 destroyed.
vagrant@cloud-native-box:~/hands-on-terraform/aws-cli-terraform-setup$ 
```


*Happy Terraform ...!!!*