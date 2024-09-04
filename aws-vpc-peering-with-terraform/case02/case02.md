# # Exploring AWS VPC Peering with Terraform
## Case-02 Scenario 

*Output*

```
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case02$ terraform init
Initializing the backend...
Initializing provider plugins...
- Finding hashicorp/aws versions matching "~> 5.0"...
- Installing hashicorp/aws v5.65.0...
- Installed hashicorp/aws v5.65.0 (signed by HashiCorp)
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
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case02$ 

```
```
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case02$ terraform plan

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # aws_iam_instance_profile.ssm_profile will be created
  + resource "aws_iam_instance_profile" "ssm_profile" {
      + arn         = (known after apply)
      + create_date = (known after apply)
      + id          = (known after apply)
      + name        = "SSM-Instance-Profile"
      + name_prefix = (known after apply)
      + path        = "/"
      + role        = "SSM-Role"
      + tags_all    = (known after apply)
      + unique_id   = (known after apply)
    }

  # aws_iam_role.ssm_role will be created
  + resource "aws_iam_role" "ssm_role" {
      + arn                   = (known after apply)
      + assume_role_policy    = jsonencode(
            {
              + Statement = [
                  + {
                      + Action    = "sts:AssumeRole"
                      + Effect    = "Allow"
                      + Principal = {
                          + Service = "ec2.amazonaws.com"
                        }
                    },
                ]
              + Version   = "2012-10-17"
            }
        )
      + create_date           = (known after apply)
      + force_detach_policies = false
      + id                    = (known after apply)
      + managed_policy_arns   = (known after apply)
      + max_session_duration  = 3600
      + name                  = "SSM-Role"
      + name_prefix           = (known after apply)
      + path                  = "/"
      + tags_all              = (known after apply)
      + unique_id             = (known after apply)

      + inline_policy (known after apply)
    }

  # aws_iam_role_policy_attachment.ssm_policy will be created
  + resource "aws_iam_role_policy_attachment" "ssm_policy" {
      + id         = (known after apply)
      + policy_arn = "arn:aws:iam::aws:policy/AmazonSSMManagedInstanceCore"
      + role       = "SSM-Role"
    }

  # aws_instance.servers["ab"] will be created
  + resource "aws_instance" "servers" {
      + ami                                  = "ami-009c9406091cbd65a"
      + arn                                  = (known after apply)
      + associate_public_ip_address          = true
      + availability_zone                    = (known after apply)
      + cpu_core_count                       = (known after apply)
      + cpu_threads_per_core                 = (known after apply)
      + disable_api_stop                     = (known after apply)
      + disable_api_termination              = (known after apply)
      + ebs_optimized                        = (known after apply)
      + get_password_data                    = false
      + host_id                              = (known after apply)
      + host_resource_group_arn              = (known after apply)
      + iam_instance_profile                 = "SSM-Instance-Profile"
      + id                                   = (known after apply)
      + instance_initiated_shutdown_behavior = (known after apply)
      + instance_lifecycle                   = (known after apply)
      + instance_state                       = (known after apply)
      + instance_type                        = "t2.micro"
      + ipv6_address_count                   = (known after apply)
      + ipv6_addresses                       = (known after apply)
      + key_name                             = (known after apply)
      + monitoring                           = (known after apply)
      + outpost_arn                          = (known after apply)
      + password_data                        = (known after apply)
      + placement_group                      = (known after apply)
      + placement_partition_number           = (known after apply)
      + primary_network_interface_id         = (known after apply)
      + private_dns                          = (known after apply)
      + private_ip                           = (known after apply)
      + public_dns                           = (known after apply)
      + public_ip                            = (known after apply)
      + secondary_private_ips                = (known after apply)
      + security_groups                      = (known after apply)
      + source_dest_check                    = true
      + spot_instance_request_id             = (known after apply)
      + subnet_id                            = (known after apply)
      + tags                                 = {
          + "Name" = "Server-AB"
        }
      + tags_all                             = {
          + "Name" = "Server-AB"
        }
      + tenancy                              = (known after apply)
      + user_data                            = (known after apply)
      + user_data_base64                     = (known after apply)
      + user_data_replace_on_change          = false
      + vpc_security_group_ids               = (known after apply)

      + capacity_reservation_specification (known after apply)

      + cpu_options (known after apply)

      + ebs_block_device (known after apply)

      + enclave_options (known after apply)

      + ephemeral_block_device (known after apply)

      + instance_market_options (known after apply)

      + maintenance_options (known after apply)

      + metadata_options (known after apply)

      + network_interface (known after apply)

      + private_dns_name_options (known after apply)

      + root_block_device (known after apply)
    }

  # aws_instance.servers["ac"] will be created
  + resource "aws_instance" "servers" {
      + ami                                  = "ami-009c9406091cbd65a"
      + arn                                  = (known after apply)
      + associate_public_ip_address          = true
      + availability_zone                    = (known after apply)
      + cpu_core_count                       = (known after apply)
      + cpu_threads_per_core                 = (known after apply)
      + disable_api_stop                     = (known after apply)
      + disable_api_termination              = (known after apply)
      + ebs_optimized                        = (known after apply)
      + get_password_data                    = false
      + host_id                              = (known after apply)
      + host_resource_group_arn              = (known after apply)
      + iam_instance_profile                 = "SSM-Instance-Profile"
      + id                                   = (known after apply)
      + instance_initiated_shutdown_behavior = (known after apply)
      + instance_lifecycle                   = (known after apply)
      + instance_state                       = (known after apply)
      + instance_type                        = "t2.micro"
      + ipv6_address_count                   = (known after apply)
      + ipv6_addresses                       = (known after apply)
      + key_name                             = (known after apply)
      + monitoring                           = (known after apply)
      + outpost_arn                          = (known after apply)
      + password_data                        = (known after apply)
      + placement_group                      = (known after apply)
      + placement_partition_number           = (known after apply)
      + primary_network_interface_id         = (known after apply)
      + private_dns                          = (known after apply)
      + private_ip                           = (known after apply)
      + public_dns                           = (known after apply)
      + public_ip                            = (known after apply)
      + secondary_private_ips                = (known after apply)
      + security_groups                      = (known after apply)
      + source_dest_check                    = true
      + spot_instance_request_id             = (known after apply)
      + subnet_id                            = (known after apply)
      + tags                                 = {
          + "Name" = "Server-AC"
        }
      + tags_all                             = {
          + "Name" = "Server-AC"
        }
      + tenancy                              = (known after apply)
      + user_data                            = (known after apply)
      + user_data_base64                     = (known after apply)
      + user_data_replace_on_change          = false
      + vpc_security_group_ids               = (known after apply)

      + capacity_reservation_specification (known after apply)

      + cpu_options (known after apply)

      + ebs_block_device (known after apply)

      + enclave_options (known after apply)

      + ephemeral_block_device (known after apply)

      + instance_market_options (known after apply)

      + maintenance_options (known after apply)

      + metadata_options (known after apply)

      + network_interface (known after apply)

      + private_dns_name_options (known after apply)

      + root_block_device (known after apply)
    }

  # aws_instance.servers["b"] will be created
  + resource "aws_instance" "servers" {
      + ami                                  = "ami-009c9406091cbd65a"
      + arn                                  = (known after apply)
      + associate_public_ip_address          = false
      + availability_zone                    = (known after apply)
      + cpu_core_count                       = (known after apply)
      + cpu_threads_per_core                 = (known after apply)
      + disable_api_stop                     = (known after apply)
      + disable_api_termination              = (known after apply)
      + ebs_optimized                        = (known after apply)
      + get_password_data                    = false
      + host_id                              = (known after apply)
      + host_resource_group_arn              = (known after apply)
      + iam_instance_profile                 = "SSM-Instance-Profile"
      + id                                   = (known after apply)
      + instance_initiated_shutdown_behavior = (known after apply)
      + instance_lifecycle                   = (known after apply)
      + instance_state                       = (known after apply)
      + instance_type                        = "t2.micro"
      + ipv6_address_count                   = (known after apply)
      + ipv6_addresses                       = (known after apply)
      + key_name                             = (known after apply)
      + monitoring                           = (known after apply)
      + outpost_arn                          = (known after apply)
      + password_data                        = (known after apply)
      + placement_group                      = (known after apply)
      + placement_partition_number           = (known after apply)
      + primary_network_interface_id         = (known after apply)
      + private_dns                          = (known after apply)
      + private_ip                           = (known after apply)
      + public_dns                           = (known after apply)
      + public_ip                            = (known after apply)
      + secondary_private_ips                = (known after apply)
      + security_groups                      = (known after apply)
      + source_dest_check                    = true
      + spot_instance_request_id             = (known after apply)
      + subnet_id                            = (known after apply)
      + tags                                 = {
          + "Name" = "Server-B"
        }
      + tags_all                             = {
          + "Name" = "Server-B"
        }
      + tenancy                              = (known after apply)
      + user_data                            = (known after apply)
      + user_data_base64                     = (known after apply)
      + user_data_replace_on_change          = false
      + vpc_security_group_ids               = (known after apply)

      + capacity_reservation_specification (known after apply)

      + cpu_options (known after apply)

      + ebs_block_device (known after apply)

      + enclave_options (known after apply)

      + ephemeral_block_device (known after apply)

      + instance_market_options (known after apply)

      + maintenance_options (known after apply)

      + metadata_options (known after apply)

      + network_interface (known after apply)

      + private_dns_name_options (known after apply)

      + root_block_device (known after apply)
    }

  # aws_instance.servers["c"] will be created
  + resource "aws_instance" "servers" {
      + ami                                  = "ami-009c9406091cbd65a"
      + arn                                  = (known after apply)
      + associate_public_ip_address          = false
      + availability_zone                    = (known after apply)
      + cpu_core_count                       = (known after apply)
      + cpu_threads_per_core                 = (known after apply)
      + disable_api_stop                     = (known after apply)
      + disable_api_termination              = (known after apply)
      + ebs_optimized                        = (known after apply)
      + get_password_data                    = false
      + host_id                              = (known after apply)
      + host_resource_group_arn              = (known after apply)
      + iam_instance_profile                 = "SSM-Instance-Profile"
      + id                                   = (known after apply)
      + instance_initiated_shutdown_behavior = (known after apply)
      + instance_lifecycle                   = (known after apply)
      + instance_state                       = (known after apply)
      + instance_type                        = "t2.micro"
      + ipv6_address_count                   = (known after apply)
      + ipv6_addresses                       = (known after apply)
      + key_name                             = (known after apply)
      + monitoring                           = (known after apply)
      + outpost_arn                          = (known after apply)
      + password_data                        = (known after apply)
      + placement_group                      = (known after apply)
      + placement_partition_number           = (known after apply)
      + primary_network_interface_id         = (known after apply)
      + private_dns                          = (known after apply)
      + private_ip                           = (known after apply)
      + public_dns                           = (known after apply)
      + public_ip                            = (known after apply)
      + secondary_private_ips                = (known after apply)
      + security_groups                      = (known after apply)
      + source_dest_check                    = true
      + spot_instance_request_id             = (known after apply)
      + subnet_id                            = (known after apply)
      + tags                                 = {
          + "Name" = "Server-C"
        }
      + tags_all                             = {
          + "Name" = "Server-C"
        }
      + tenancy                              = (known after apply)
      + user_data                            = (known after apply)
      + user_data_base64                     = (known after apply)
      + user_data_replace_on_change          = false
      + vpc_security_group_ids               = (known after apply)

      + capacity_reservation_specification (known after apply)

      + cpu_options (known after apply)

      + ebs_block_device (known after apply)

      + enclave_options (known after apply)

      + ephemeral_block_device (known after apply)

      + instance_market_options (known after apply)

      + maintenance_options (known after apply)

      + metadata_options (known after apply)

      + network_interface (known after apply)

      + private_dns_name_options (known after apply)

      + root_block_device (known after apply)
    }

  # aws_internet_gateway.igw will be created
  + resource "aws_internet_gateway" "igw" {
      + arn      = (known after apply)
      + id       = (known after apply)
      + owner_id = (known after apply)
      + tags     = {
          + "Name" = "Main IGW"
        }
      + tags_all = {
          + "Name" = "Main IGW"
        }
      + vpc_id   = (known after apply)
    }

  # aws_route_table.rt_a will be created
  + resource "aws_route_table" "rt_a" {
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
          + {
              + cidr_block                 = "192.168.0.0/16"
              + vpc_peering_connection_id  = (known after apply)
                # (11 unchanged attributes hidden)
            },
        ]
      + tags             = {
          + "Name" = "Route Table VPC-A"
        }
      + tags_all         = {
          + "Name" = "Route Table VPC-A"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table.rt_bc[0] will be created
  + resource "aws_route_table" "rt_bc" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + cidr_block                 = "10.1.0.0/16"
              + vpc_peering_connection_id  = (known after apply)
                # (11 unchanged attributes hidden)
            },
        ]
      + tags             = {
          + "Name" = "Route Table VPC-B"
        }
      + tags_all         = {
          + "Name" = "Route Table VPC-B"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table.rt_bc[1] will be created
  + resource "aws_route_table" "rt_bc" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + cidr_block                 = "10.1.0.0/16"
              + vpc_peering_connection_id  = (known after apply)
                # (11 unchanged attributes hidden)
            },
        ]
      + tags             = {
          + "Name" = "Route Table VPC-C"
        }
      + tags_all         = {
          + "Name" = "Route Table VPC-C"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table_association.rta_a["a_subnet1"] will be created
  + resource "aws_route_table_association" "rta_a" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.rta_a["a_subnet2"] will be created
  + resource "aws_route_table_association" "rta_a" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.rta_bc["b_subnet1"] will be created
  + resource "aws_route_table_association" "rta_bc" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.rta_bc["c_subnet1"] will be created
  + resource "aws_route_table_association" "rta_bc" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_security_group.security_groups["a"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP and SSH traffic"
      + egress                 = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 0
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "-1"
              + security_groups  = []
              + self             = false
              + to_port          = 0
                # (1 unchanged attribute hidden)
            },
        ]
      + id                     = (known after apply)
      + ingress                = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = -1
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "icmp"
              + security_groups  = []
              + self             = false
              + to_port          = -1
                # (1 unchanged attribute hidden)
            },
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 22
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "tcp"
              + security_groups  = []
              + self             = false
              + to_port          = 22
                # (1 unchanged attribute hidden)
            },
        ]
      + name                   = "Allow ICMP and SSH VPC-A"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP and SSH traffic VPC-A"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP and SSH traffic VPC-A"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_security_group.security_groups["b"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP and SSH traffic"
      + egress                 = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 0
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "-1"
              + security_groups  = []
              + self             = false
              + to_port          = 0
                # (1 unchanged attribute hidden)
            },
        ]
      + id                     = (known after apply)
      + ingress                = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = -1
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "icmp"
              + security_groups  = []
              + self             = false
              + to_port          = -1
                # (1 unchanged attribute hidden)
            },
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 22
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "tcp"
              + security_groups  = []
              + self             = false
              + to_port          = 22
                # (1 unchanged attribute hidden)
            },
        ]
      + name                   = "Allow ICMP and SSH VPC-B"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP and SSH traffic VPC-B"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP and SSH traffic VPC-B"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_security_group.security_groups["c"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP and SSH traffic"
      + egress                 = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 0
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "-1"
              + security_groups  = []
              + self             = false
              + to_port          = 0
                # (1 unchanged attribute hidden)
            },
        ]
      + id                     = (known after apply)
      + ingress                = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = -1
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "icmp"
              + security_groups  = []
              + self             = false
              + to_port          = -1
                # (1 unchanged attribute hidden)
            },
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 22
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "tcp"
              + security_groups  = []
              + self             = false
              + to_port          = 22
                # (1 unchanged attribute hidden)
            },
        ]
      + name                   = "Allow ICMP and SSH VPC-C"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP and SSH traffic VPC-C"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP and SSH traffic VPC-C"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_subnet.subnets["a_subnet1"] will be created
  + resource "aws_subnet" "subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = (known after apply)
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.1.1.0/24"
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
          + "Name" = "Subnet-A-subnet1"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-A-subnet1"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.subnets["a_subnet2"] will be created
  + resource "aws_subnet" "subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = (known after apply)
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.1.2.0/24"
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
          + "Name" = "Subnet-A-subnet2"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-A-subnet2"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.subnets["b_subnet1"] will be created
  + resource "aws_subnet" "subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = (known after apply)
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "192.168.1.0/24"
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
          + "Name" = "Subnet-B-subnet1"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-B-subnet1"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.subnets["c_subnet1"] will be created
  + resource "aws_subnet" "subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = (known after apply)
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "192.168.2.0/24"
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
          + "Name" = "Subnet-C-subnet1"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-C-subnet1"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_vpc.vpcs["a"] will be created
  + resource "aws_vpc" "vpcs" {
      + arn                                  = (known after apply)
      + cidr_block                           = "10.1.0.0/16"
      + default_network_acl_id               = (known after apply)
      + default_route_table_id               = (known after apply)
      + default_security_group_id            = (known after apply)
      + dhcp_options_id                      = (known after apply)
      + enable_dns_hostnames                 = true
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
          + "Name" = "VPC-A"
        }
      + tags_all                             = {
          + "Name" = "VPC-A"
        }
    }

  # aws_vpc.vpcs["b"] will be created
  + resource "aws_vpc" "vpcs" {
      + arn                                  = (known after apply)
      + cidr_block                           = "192.168.0.0/16"
      + default_network_acl_id               = (known after apply)
      + default_route_table_id               = (known after apply)
      + default_security_group_id            = (known after apply)
      + dhcp_options_id                      = (known after apply)
      + enable_dns_hostnames                 = true
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
          + "Name" = "VPC-B"
        }
      + tags_all                             = {
          + "Name" = "VPC-B"
        }
    }

  # aws_vpc.vpcs["c"] will be created
  + resource "aws_vpc" "vpcs" {
      + arn                                  = (known after apply)
      + cidr_block                           = "192.168.0.0/16"
      + default_network_acl_id               = (known after apply)
      + default_route_table_id               = (known after apply)
      + default_security_group_id            = (known after apply)
      + dhcp_options_id                      = (known after apply)
      + enable_dns_hostnames                 = true
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
          + "Name" = "VPC-C"
        }
      + tags_all                             = {
          + "Name" = "VPC-C"
        }
    }

  # aws_vpc_peering_connection.peering[0] will be created
  + resource "aws_vpc_peering_connection" "peering" {
      + accept_status = (known after apply)
      + auto_accept   = true
      + id            = (known after apply)
      + peer_owner_id = (known after apply)
      + peer_region   = (known after apply)
      + peer_vpc_id   = (known after apply)
      + tags          = {
          + "Name" = "VPC-A to VPC-B Peering"
        }
      + tags_all      = {
          + "Name" = "VPC-A to VPC-B Peering"
        }
      + vpc_id        = (known after apply)

      + accepter (known after apply)

      + requester (known after apply)
    }

  # aws_vpc_peering_connection.peering[1] will be created
  + resource "aws_vpc_peering_connection" "peering" {
      + accept_status = (known after apply)
      + auto_accept   = true
      + id            = (known after apply)
      + peer_owner_id = (known after apply)
      + peer_region   = (known after apply)
      + peer_vpc_id   = (known after apply)
      + tags          = {
          + "Name" = "VPC-A to VPC-C Peering"
        }
      + tags_all      = {
          + "Name" = "VPC-A to VPC-C Peering"
        }
      + vpc_id        = (known after apply)

      + accepter (known after apply)

      + requester (known after apply)
    }

Plan: 27 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + test_instructions = (known after apply)

────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

Note: You didn't use the -out option to save this plan, so Terraform can't guarantee to take exactly these actions if you run "terraform apply" now.
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case02$ 
```

```
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case02$ terraform apply -auto-approve

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # aws_iam_instance_profile.ssm_profile will be created
  + resource "aws_iam_instance_profile" "ssm_profile" {
      + arn         = (known after apply)
      + create_date = (known after apply)
      + id          = (known after apply)
      + name        = "SSM-Instance-Profile"
      + name_prefix = (known after apply)
      + path        = "/"
      + role        = "SSM-Role"
      + tags_all    = (known after apply)
      + unique_id   = (known after apply)
    }

  # aws_iam_role.ssm_role will be created
  + resource "aws_iam_role" "ssm_role" {
      + arn                   = (known after apply)
      + assume_role_policy    = jsonencode(
            {
              + Statement = [
                  + {
                      + Action    = "sts:AssumeRole"
                      + Effect    = "Allow"
                      + Principal = {
                          + Service = "ec2.amazonaws.com"
                        }
                    },
                ]
              + Version   = "2012-10-17"
            }
        )
      + create_date           = (known after apply)
      + force_detach_policies = false
      + id                    = (known after apply)
      + managed_policy_arns   = (known after apply)
      + max_session_duration  = 3600
      + name                  = "SSM-Role"
      + name_prefix           = (known after apply)
      + path                  = "/"
      + tags_all              = (known after apply)
      + unique_id             = (known after apply)

      + inline_policy (known after apply)
    }

  # aws_iam_role_policy_attachment.ssm_policy will be created
  + resource "aws_iam_role_policy_attachment" "ssm_policy" {
      + id         = (known after apply)
      + policy_arn = "arn:aws:iam::aws:policy/AmazonSSMManagedInstanceCore"
      + role       = "SSM-Role"
    }

  # aws_instance.servers["ab"] will be created
  + resource "aws_instance" "servers" {
      + ami                                  = "ami-009c9406091cbd65a"
      + arn                                  = (known after apply)
      + associate_public_ip_address          = true
      + availability_zone                    = (known after apply)
      + cpu_core_count                       = (known after apply)
      + cpu_threads_per_core                 = (known after apply)
      + disable_api_stop                     = (known after apply)
      + disable_api_termination              = (known after apply)
      + ebs_optimized                        = (known after apply)
      + get_password_data                    = false
      + host_id                              = (known after apply)
      + host_resource_group_arn              = (known after apply)
      + iam_instance_profile                 = "SSM-Instance-Profile"
      + id                                   = (known after apply)
      + instance_initiated_shutdown_behavior = (known after apply)
      + instance_lifecycle                   = (known after apply)
      + instance_state                       = (known after apply)
      + instance_type                        = "t2.micro"
      + ipv6_address_count                   = (known after apply)
      + ipv6_addresses                       = (known after apply)
      + key_name                             = (known after apply)
      + monitoring                           = (known after apply)
      + outpost_arn                          = (known after apply)
      + password_data                        = (known after apply)
      + placement_group                      = (known after apply)
      + placement_partition_number           = (known after apply)
      + primary_network_interface_id         = (known after apply)
      + private_dns                          = (known after apply)
      + private_ip                           = (known after apply)
      + public_dns                           = (known after apply)
      + public_ip                            = (known after apply)
      + secondary_private_ips                = (known after apply)
      + security_groups                      = (known after apply)
      + source_dest_check                    = true
      + spot_instance_request_id             = (known after apply)
      + subnet_id                            = (known after apply)
      + tags                                 = {
          + "Name" = "Server-AB"
        }
      + tags_all                             = {
          + "Name" = "Server-AB"
        }
      + tenancy                              = (known after apply)
      + user_data                            = (known after apply)
      + user_data_base64                     = (known after apply)
      + user_data_replace_on_change          = false
      + vpc_security_group_ids               = (known after apply)

      + capacity_reservation_specification (known after apply)

      + cpu_options (known after apply)

      + ebs_block_device (known after apply)

      + enclave_options (known after apply)

      + ephemeral_block_device (known after apply)

      + instance_market_options (known after apply)

      + maintenance_options (known after apply)

      + metadata_options (known after apply)

      + network_interface (known after apply)

      + private_dns_name_options (known after apply)

      + root_block_device (known after apply)
    }

  # aws_instance.servers["ac"] will be created
  + resource "aws_instance" "servers" {
      + ami                                  = "ami-009c9406091cbd65a"
      + arn                                  = (known after apply)
      + associate_public_ip_address          = true
      + availability_zone                    = (known after apply)
      + cpu_core_count                       = (known after apply)
      + cpu_threads_per_core                 = (known after apply)
      + disable_api_stop                     = (known after apply)
      + disable_api_termination              = (known after apply)
      + ebs_optimized                        = (known after apply)
      + get_password_data                    = false
      + host_id                              = (known after apply)
      + host_resource_group_arn              = (known after apply)
      + iam_instance_profile                 = "SSM-Instance-Profile"
      + id                                   = (known after apply)
      + instance_initiated_shutdown_behavior = (known after apply)
      + instance_lifecycle                   = (known after apply)
      + instance_state                       = (known after apply)
      + instance_type                        = "t2.micro"
      + ipv6_address_count                   = (known after apply)
      + ipv6_addresses                       = (known after apply)
      + key_name                             = (known after apply)
      + monitoring                           = (known after apply)
      + outpost_arn                          = (known after apply)
      + password_data                        = (known after apply)
      + placement_group                      = (known after apply)
      + placement_partition_number           = (known after apply)
      + primary_network_interface_id         = (known after apply)
      + private_dns                          = (known after apply)
      + private_ip                           = (known after apply)
      + public_dns                           = (known after apply)
      + public_ip                            = (known after apply)
      + secondary_private_ips                = (known after apply)
      + security_groups                      = (known after apply)
      + source_dest_check                    = true
      + spot_instance_request_id             = (known after apply)
      + subnet_id                            = (known after apply)
      + tags                                 = {
          + "Name" = "Server-AC"
        }
      + tags_all                             = {
          + "Name" = "Server-AC"
        }
      + tenancy                              = (known after apply)
      + user_data                            = (known after apply)
      + user_data_base64                     = (known after apply)
      + user_data_replace_on_change          = false
      + vpc_security_group_ids               = (known after apply)

      + capacity_reservation_specification (known after apply)

      + cpu_options (known after apply)

      + ebs_block_device (known after apply)

      + enclave_options (known after apply)

      + ephemeral_block_device (known after apply)

      + instance_market_options (known after apply)

      + maintenance_options (known after apply)

      + metadata_options (known after apply)

      + network_interface (known after apply)

      + private_dns_name_options (known after apply)

      + root_block_device (known after apply)
    }

  # aws_instance.servers["b"] will be created
  + resource "aws_instance" "servers" {
      + ami                                  = "ami-009c9406091cbd65a"
      + arn                                  = (known after apply)
      + associate_public_ip_address          = false
      + availability_zone                    = (known after apply)
      + cpu_core_count                       = (known after apply)
      + cpu_threads_per_core                 = (known after apply)
      + disable_api_stop                     = (known after apply)
      + disable_api_termination              = (known after apply)
      + ebs_optimized                        = (known after apply)
      + get_password_data                    = false
      + host_id                              = (known after apply)
      + host_resource_group_arn              = (known after apply)
      + iam_instance_profile                 = "SSM-Instance-Profile"
      + id                                   = (known after apply)
      + instance_initiated_shutdown_behavior = (known after apply)
      + instance_lifecycle                   = (known after apply)
      + instance_state                       = (known after apply)
      + instance_type                        = "t2.micro"
      + ipv6_address_count                   = (known after apply)
      + ipv6_addresses                       = (known after apply)
      + key_name                             = (known after apply)
      + monitoring                           = (known after apply)
      + outpost_arn                          = (known after apply)
      + password_data                        = (known after apply)
      + placement_group                      = (known after apply)
      + placement_partition_number           = (known after apply)
      + primary_network_interface_id         = (known after apply)
      + private_dns                          = (known after apply)
      + private_ip                           = (known after apply)
      + public_dns                           = (known after apply)
      + public_ip                            = (known after apply)
      + secondary_private_ips                = (known after apply)
      + security_groups                      = (known after apply)
      + source_dest_check                    = true
      + spot_instance_request_id             = (known after apply)
      + subnet_id                            = (known after apply)
      + tags                                 = {
          + "Name" = "Server-B"
        }
      + tags_all                             = {
          + "Name" = "Server-B"
        }
      + tenancy                              = (known after apply)
      + user_data                            = (known after apply)
      + user_data_base64                     = (known after apply)
      + user_data_replace_on_change          = false
      + vpc_security_group_ids               = (known after apply)

      + capacity_reservation_specification (known after apply)

      + cpu_options (known after apply)

      + ebs_block_device (known after apply)

      + enclave_options (known after apply)

      + ephemeral_block_device (known after apply)

      + instance_market_options (known after apply)

      + maintenance_options (known after apply)

      + metadata_options (known after apply)

      + network_interface (known after apply)

      + private_dns_name_options (known after apply)

      + root_block_device (known after apply)
    }

  # aws_instance.servers["c"] will be created
  + resource "aws_instance" "servers" {
      + ami                                  = "ami-009c9406091cbd65a"
      + arn                                  = (known after apply)
      + associate_public_ip_address          = false
      + availability_zone                    = (known after apply)
      + cpu_core_count                       = (known after apply)
      + cpu_threads_per_core                 = (known after apply)
      + disable_api_stop                     = (known after apply)
      + disable_api_termination              = (known after apply)
      + ebs_optimized                        = (known after apply)
      + get_password_data                    = false
      + host_id                              = (known after apply)
      + host_resource_group_arn              = (known after apply)
      + iam_instance_profile                 = "SSM-Instance-Profile"
      + id                                   = (known after apply)
      + instance_initiated_shutdown_behavior = (known after apply)
      + instance_lifecycle                   = (known after apply)
      + instance_state                       = (known after apply)
      + instance_type                        = "t2.micro"
      + ipv6_address_count                   = (known after apply)
      + ipv6_addresses                       = (known after apply)
      + key_name                             = (known after apply)
      + monitoring                           = (known after apply)
      + outpost_arn                          = (known after apply)
      + password_data                        = (known after apply)
      + placement_group                      = (known after apply)
      + placement_partition_number           = (known after apply)
      + primary_network_interface_id         = (known after apply)
      + private_dns                          = (known after apply)
      + private_ip                           = (known after apply)
      + public_dns                           = (known after apply)
      + public_ip                            = (known after apply)
      + secondary_private_ips                = (known after apply)
      + security_groups                      = (known after apply)
      + source_dest_check                    = true
      + spot_instance_request_id             = (known after apply)
      + subnet_id                            = (known after apply)
      + tags                                 = {
          + "Name" = "Server-C"
        }
      + tags_all                             = {
          + "Name" = "Server-C"
        }
      + tenancy                              = (known after apply)
      + user_data                            = (known after apply)
      + user_data_base64                     = (known after apply)
      + user_data_replace_on_change          = false
      + vpc_security_group_ids               = (known after apply)

      + capacity_reservation_specification (known after apply)

      + cpu_options (known after apply)

      + ebs_block_device (known after apply)

      + enclave_options (known after apply)

      + ephemeral_block_device (known after apply)

      + instance_market_options (known after apply)

      + maintenance_options (known after apply)

      + metadata_options (known after apply)

      + network_interface (known after apply)

      + private_dns_name_options (known after apply)

      + root_block_device (known after apply)
    }

  # aws_internet_gateway.igw will be created
  + resource "aws_internet_gateway" "igw" {
      + arn      = (known after apply)
      + id       = (known after apply)
      + owner_id = (known after apply)
      + tags     = {
          + "Name" = "Main IGW"
        }
      + tags_all = {
          + "Name" = "Main IGW"
        }
      + vpc_id   = (known after apply)
    }

  # aws_route_table.rt_a will be created
  + resource "aws_route_table" "rt_a" {
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
          + {
              + cidr_block                 = "192.168.0.0/16"
              + vpc_peering_connection_id  = (known after apply)
                # (11 unchanged attributes hidden)
            },
        ]
      + tags             = {
          + "Name" = "Route Table VPC-A"
        }
      + tags_all         = {
          + "Name" = "Route Table VPC-A"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table.rt_bc[0] will be created
  + resource "aws_route_table" "rt_bc" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + cidr_block                 = "10.1.0.0/16"
              + vpc_peering_connection_id  = (known after apply)
                # (11 unchanged attributes hidden)
            },
        ]
      + tags             = {
          + "Name" = "Route Table VPC-B"
        }
      + tags_all         = {
          + "Name" = "Route Table VPC-B"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table.rt_bc[1] will be created
  + resource "aws_route_table" "rt_bc" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + cidr_block                 = "10.1.0.0/16"
              + vpc_peering_connection_id  = (known after apply)
                # (11 unchanged attributes hidden)
            },
        ]
      + tags             = {
          + "Name" = "Route Table VPC-C"
        }
      + tags_all         = {
          + "Name" = "Route Table VPC-C"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table_association.rta_a["a_subnet1"] will be created
  + resource "aws_route_table_association" "rta_a" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.rta_a["a_subnet2"] will be created
  + resource "aws_route_table_association" "rta_a" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.rta_bc["b_subnet1"] will be created
  + resource "aws_route_table_association" "rta_bc" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.rta_bc["c_subnet1"] will be created
  + resource "aws_route_table_association" "rta_bc" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_security_group.security_groups["a"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP and SSH traffic"
      + egress                 = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 0
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "-1"
              + security_groups  = []
              + self             = false
              + to_port          = 0
                # (1 unchanged attribute hidden)
            },
        ]
      + id                     = (known after apply)
      + ingress                = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = -1
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "icmp"
              + security_groups  = []
              + self             = false
              + to_port          = -1
                # (1 unchanged attribute hidden)
            },
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 22
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "tcp"
              + security_groups  = []
              + self             = false
              + to_port          = 22
                # (1 unchanged attribute hidden)
            },
        ]
      + name                   = "Allow ICMP and SSH VPC-A"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP and SSH traffic VPC-A"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP and SSH traffic VPC-A"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_security_group.security_groups["b"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP and SSH traffic"
      + egress                 = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 0
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "-1"
              + security_groups  = []
              + self             = false
              + to_port          = 0
                # (1 unchanged attribute hidden)
            },
        ]
      + id                     = (known after apply)
      + ingress                = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = -1
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "icmp"
              + security_groups  = []
              + self             = false
              + to_port          = -1
                # (1 unchanged attribute hidden)
            },
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 22
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "tcp"
              + security_groups  = []
              + self             = false
              + to_port          = 22
                # (1 unchanged attribute hidden)
            },
        ]
      + name                   = "Allow ICMP and SSH VPC-B"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP and SSH traffic VPC-B"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP and SSH traffic VPC-B"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_security_group.security_groups["c"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP and SSH traffic"
      + egress                 = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 0
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "-1"
              + security_groups  = []
              + self             = false
              + to_port          = 0
                # (1 unchanged attribute hidden)
            },
        ]
      + id                     = (known after apply)
      + ingress                = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = -1
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "icmp"
              + security_groups  = []
              + self             = false
              + to_port          = -1
                # (1 unchanged attribute hidden)
            },
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + from_port        = 22
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "tcp"
              + security_groups  = []
              + self             = false
              + to_port          = 22
                # (1 unchanged attribute hidden)
            },
        ]
      + name                   = "Allow ICMP and SSH VPC-C"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP and SSH traffic VPC-C"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP and SSH traffic VPC-C"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_subnet.subnets["a_subnet1"] will be created
  + resource "aws_subnet" "subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = (known after apply)
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.1.1.0/24"
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
          + "Name" = "Subnet-A-subnet1"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-A-subnet1"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.subnets["a_subnet2"] will be created
  + resource "aws_subnet" "subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = (known after apply)
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.1.2.0/24"
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
          + "Name" = "Subnet-A-subnet2"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-A-subnet2"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.subnets["b_subnet1"] will be created
  + resource "aws_subnet" "subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = (known after apply)
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "192.168.1.0/24"
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
          + "Name" = "Subnet-B-subnet1"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-B-subnet1"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.subnets["c_subnet1"] will be created
  + resource "aws_subnet" "subnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = (known after apply)
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "192.168.2.0/24"
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
          + "Name" = "Subnet-C-subnet1"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-C-subnet1"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_vpc.vpcs["a"] will be created
  + resource "aws_vpc" "vpcs" {
      + arn                                  = (known after apply)
      + cidr_block                           = "10.1.0.0/16"
      + default_network_acl_id               = (known after apply)
      + default_route_table_id               = (known after apply)
      + default_security_group_id            = (known after apply)
      + dhcp_options_id                      = (known after apply)
      + enable_dns_hostnames                 = true
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
          + "Name" = "VPC-A"
        }
      + tags_all                             = {
          + "Name" = "VPC-A"
        }
    }

  # aws_vpc.vpcs["b"] will be created
  + resource "aws_vpc" "vpcs" {
      + arn                                  = (known after apply)
      + cidr_block                           = "192.168.0.0/16"
      + default_network_acl_id               = (known after apply)
      + default_route_table_id               = (known after apply)
      + default_security_group_id            = (known after apply)
      + dhcp_options_id                      = (known after apply)
      + enable_dns_hostnames                 = true
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
          + "Name" = "VPC-B"
        }
      + tags_all                             = {
          + "Name" = "VPC-B"
        }
    }

  # aws_vpc.vpcs["c"] will be created
  + resource "aws_vpc" "vpcs" {
      + arn                                  = (known after apply)
      + cidr_block                           = "192.168.0.0/16"
      + default_network_acl_id               = (known after apply)
      + default_route_table_id               = (known after apply)
      + default_security_group_id            = (known after apply)
      + dhcp_options_id                      = (known after apply)
      + enable_dns_hostnames                 = true
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
          + "Name" = "VPC-C"
        }
      + tags_all                             = {
          + "Name" = "VPC-C"
        }
    }

  # aws_vpc_peering_connection.peering[0] will be created
  + resource "aws_vpc_peering_connection" "peering" {
      + accept_status = (known after apply)
      + auto_accept   = true
      + id            = (known after apply)
      + peer_owner_id = (known after apply)
      + peer_region   = (known after apply)
      + peer_vpc_id   = (known after apply)
      + tags          = {
          + "Name" = "VPC-A to VPC-B Peering"
        }
      + tags_all      = {
          + "Name" = "VPC-A to VPC-B Peering"
        }
      + vpc_id        = (known after apply)

      + accepter (known after apply)

      + requester (known after apply)
    }

  # aws_vpc_peering_connection.peering[1] will be created
  + resource "aws_vpc_peering_connection" "peering" {
      + accept_status = (known after apply)
      + auto_accept   = true
      + id            = (known after apply)
      + peer_owner_id = (known after apply)
      + peer_region   = (known after apply)
      + peer_vpc_id   = (known after apply)
      + tags          = {
          + "Name" = "VPC-A to VPC-C Peering"
        }
      + tags_all      = {
          + "Name" = "VPC-A to VPC-C Peering"
        }
      + vpc_id        = (known after apply)

      + accepter (known after apply)

      + requester (known after apply)
    }

Plan: 27 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + test_instructions = (known after apply)
aws_vpc.vpcs["a"]: Creating...
aws_vpc.vpcs["c"]: Creating...
aws_iam_role.ssm_role: Creating...
aws_vpc.vpcs["b"]: Creating...
aws_iam_role.ssm_role: Creation complete after 2s [id=SSM-Role]
aws_iam_instance_profile.ssm_profile: Creating...
aws_iam_role_policy_attachment.ssm_policy: Creating...
aws_iam_role_policy_attachment.ssm_policy: Creation complete after 1s [id=SSM-Role-20240904045108415500000001]
aws_iam_instance_profile.ssm_profile: Creation complete after 2s [id=SSM-Instance-Profile]
aws_vpc.vpcs["a"]: Still creating... [10s elapsed]
aws_vpc.vpcs["c"]: Still creating... [10s elapsed]
aws_vpc.vpcs["b"]: Still creating... [10s elapsed]
aws_vpc.vpcs["a"]: Creation complete after 11s [id=vpc-01f7f6416ea84664e]
aws_vpc.vpcs["b"]: Creation complete after 11s [id=vpc-058aaf52618f67601]
aws_internet_gateway.igw: Creating...
aws_vpc.vpcs["c"]: Creation complete after 11s [id=vpc-0ef85bbf333e81ec2]
aws_subnet.subnets["a_subnet2"]: Creating...
aws_vpc_peering_connection.peering[0]: Creating...
aws_security_group.security_groups["a"]: Creating...
aws_subnet.subnets["a_subnet1"]: Creating...
aws_subnet.subnets["b_subnet1"]: Creating...
aws_vpc_peering_connection.peering[1]: Creating...
aws_subnet.subnets["c_subnet1"]: Creating...
aws_security_group.security_groups["c"]: Creating...
aws_security_group.security_groups["b"]: Creating...
aws_internet_gateway.igw: Creation complete after 1s [id=igw-0eca98843118df1a4]
aws_subnet.subnets["a_subnet1"]: Creation complete after 0s [id=subnet-0479fe1de69957b24]
aws_subnet.subnets["a_subnet2"]: Creation complete after 0s [id=subnet-0fadefa76713ba20d]
aws_subnet.subnets["b_subnet1"]: Creation complete after 0s [id=subnet-00a4cf93a9c91659d]
aws_subnet.subnets["c_subnet1"]: Creation complete after 0s [id=subnet-0e06d1461afbfcc64]
aws_vpc_peering_connection.peering[0]: Creation complete after 1s [id=pcx-03350e4a086d987b6]
aws_route_table.rt_a: Creating...
aws_vpc_peering_connection.peering[1]: Creation complete after 1s [id=pcx-01c23bbe456e6df4f]
aws_route_table.rt_bc[0]: Creating...
aws_route_table.rt_bc[1]: Creating...
aws_route_table.rt_bc[1]: Creation complete after 1s [id=rtb-0929746b8657ad255]
aws_route_table.rt_bc[0]: Creation complete after 1s [id=rtb-0fb53a6db328557c4]
aws_route_table_association.rta_bc["b_subnet1"]: Creating...
aws_route_table_association.rta_bc["c_subnet1"]: Creating...
aws_security_group.security_groups["b"]: Creation complete after 2s [id=sg-0cce6817ac2ecd093]
aws_security_group.security_groups["c"]: Creation complete after 2s [id=sg-09232b7656beb976a]
aws_security_group.security_groups["a"]: Creation complete after 2s [id=sg-0f6fa8bd3c3bf0e7a]
aws_instance.servers["c"]: Creating...
aws_instance.servers["ac"]: Creating...
aws_instance.servers["ab"]: Creating...
aws_instance.servers["b"]: Creating...
aws_route_table_association.rta_bc["b_subnet1"]: Creation complete after 0s [id=rtbassoc-013ed056fd192ab00]
aws_route_table_association.rta_bc["c_subnet1"]: Creation complete after 0s [id=rtbassoc-06c5485838bdcbab5]
aws_route_table.rt_a: Creation complete after 1s [id=rtb-0903f5698419cb121]
aws_route_table_association.rta_a["a_subnet1"]: Creating...
aws_route_table_association.rta_a["a_subnet2"]: Creating...
aws_route_table_association.rta_a["a_subnet1"]: Creation complete after 1s [id=rtbassoc-016df4fcb3437b7fc]
aws_route_table_association.rta_a["a_subnet2"]: Creation complete after 1s [id=rtbassoc-006400f37ac92f0b6]
aws_instance.servers["c"]: Still creating... [10s elapsed]
aws_instance.servers["ac"]: Still creating... [10s elapsed]
aws_instance.servers["ab"]: Still creating... [10s elapsed]
aws_instance.servers["b"]: Still creating... [10s elapsed]
aws_instance.servers["ab"]: Creation complete after 13s [id=i-05fc2c9d6066dbb6a]
aws_instance.servers["ac"]: Creation complete after 13s [id=i-0a4d58c278e0ab91f]
aws_instance.servers["b"]: Creation complete after 13s [id=i-00a256442c7086b11]
aws_instance.servers["c"]: Still creating... [20s elapsed]
aws_instance.servers["c"]: Creation complete after 22s [id=i-003c43e8bd6ddf6de]

Apply complete! Resources: 27 added, 0 changed, 0 destroyed.

Outputs:

test_instructions = <<EOT

1. SSH into Server-AB or Server-AC using their public IPs.
   Server-AB Public IP: 18.143.116.250
   Server-AC Public IP: 18.143.184.86

2. From Server-AB, try to ping Server-B:
   Server-B Private IP: 192.168.1.226

3. To test connectivity with Server-C:
   a. Go to the AWS VPC Console
   b. Find the route table for VPC-A
   c. Edit the route for 192.168.0.0/16
   d. Change the target to the peering connection with VPC-C

4. After changing the route, from Server-AC, try to ping Server-C:
   Server-C Private IP: 192.168.2.126

5. Remember to switch the route back to the peering connection with VPC-B if you want to test connectivity with Server-B again.


EOT
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case02$ 
```

```
      - force_detach_policies = false -> null
      - id                    = "SSM-Role" -> null
      - managed_policy_arns   = [
          - "arn:aws:iam::aws:policy/AmazonSSMManagedInstanceCore",
        ] -> null
      - max_session_duration  = 3600 -> null
      - name                  = "SSM-Role" -> null
      - path                  = "/" -> null
      - tags                  = {} -> null
      - tags_all              = {} -> null
      - unique_id             = "AROAZX37QZCVDQ35OZ27S" -> null
        # (3 unchanged attributes hidden)
    }

  # aws_iam_role_policy_attachment.ssm_policy will be destroyed
  - resource "aws_iam_role_policy_attachment" "ssm_policy" {
      - id         = "SSM-Role-20240904045108415500000001" -> null
      - policy_arn = "arn:aws:iam::aws:policy/AmazonSSMManagedInstanceCore" -> null
      - role       = "SSM-Role" -> null
    }

  # aws_instance.servers["ab"] will be destroyed
  - resource "aws_instance" "servers" {
      - ami                                  = "ami-009c9406091cbd65a" -> null
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:instance/i-05fc2c9d6066dbb6a" -> null
      - associate_public_ip_address          = true -> null
      - availability_zone                    = "ap-southeast-1a" -> null
      - cpu_core_count                       = 1 -> null
      - cpu_threads_per_core                 = 1 -> null
      - disable_api_stop                     = false -> null
      - disable_api_termination              = false -> null
      - ebs_optimized                        = false -> null
      - get_password_data                    = false -> null
      - hibernation                          = false -> null
      - iam_instance_profile                 = "SSM-Instance-Profile" -> null
      - id                                   = "i-05fc2c9d6066dbb6a" -> null
      - instance_initiated_shutdown_behavior = "stop" -> null
      - instance_state                       = "running" -> null
      - instance_type                        = "t2.micro" -> null
      - ipv6_address_count                   = 0 -> null
      - ipv6_addresses                       = [] -> null
      - monitoring                           = false -> null
      - placement_partition_number           = 0 -> null
      - primary_network_interface_id         = "eni-0c945f0242a83c8fe" -> null
      - private_dns                          = "ip-10-1-1-160.ap-southeast-1.compute.internal" -> null
      - private_ip                           = "10.1.1.160" -> null
      - public_dns                           = "ec2-18-143-116-250.ap-southeast-1.compute.amazonaws.com" -> null
      - public_ip                            = "18.143.116.250" -> null
      - secondary_private_ips                = [] -> null
      - security_groups                      = [] -> null
      - source_dest_check                    = true -> null
      - subnet_id                            = "subnet-0479fe1de69957b24" -> null
      - tags                                 = {
          - "Name" = "Server-AB"
        } -> null
      - tags_all                             = {
          - "Name" = "Server-AB"
        } -> null
      - tenancy                              = "default" -> null
      - user_data_replace_on_change          = false -> null
      - vpc_security_group_ids               = [
          - "sg-0f6fa8bd3c3bf0e7a",
        ] -> null
        # (7 unchanged attributes hidden)

      - capacity_reservation_specification {
          - capacity_reservation_preference = "open" -> null
        }

      - cpu_options {
          - core_count       = 1 -> null
          - threads_per_core = 1 -> null
            # (1 unchanged attribute hidden)
        }

      - credit_specification {
          - cpu_credits = "standard" -> null
        }

      - enclave_options {
          - enabled = false -> null
        }

      - maintenance_options {
          - auto_recovery = "default" -> null
        }

      - metadata_options {
          - http_endpoint               = "enabled" -> null
          - http_protocol_ipv6          = "disabled" -> null
          - http_put_response_hop_limit = 2 -> null
          - http_tokens                 = "required" -> null
          - instance_metadata_tags      = "disabled" -> null
        }

      - private_dns_name_options {
          - enable_resource_name_dns_a_record    = false -> null
          - enable_resource_name_dns_aaaa_record = false -> null
          - hostname_type                        = "ip-name" -> null
        }

      - root_block_device {
          - delete_on_termination = true -> null
          - device_name           = "/dev/xvda" -> null
          - encrypted             = false -> null
          - iops                  = 3000 -> null
          - tags                  = {} -> null
          - tags_all              = {} -> null
          - throughput            = 125 -> null
          - volume_id             = "vol-0ddbfede2d90fced1" -> null
          - volume_size           = 8 -> null
          - volume_type           = "gp3" -> null
            # (1 unchanged attribute hidden)
        }
    }

  # aws_instance.servers["ac"] will be destroyed
  - resource "aws_instance" "servers" {
      - ami                                  = "ami-009c9406091cbd65a" -> null
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:instance/i-0a4d58c278e0ab91f" -> null
      - associate_public_ip_address          = true -> null
      - availability_zone                    = "ap-southeast-1c" -> null
      - cpu_core_count                       = 1 -> null
      - cpu_threads_per_core                 = 1 -> null
      - disable_api_stop                     = false -> null
      - disable_api_termination              = false -> null
      - ebs_optimized                        = false -> null
      - get_password_data                    = false -> null
      - hibernation                          = false -> null
      - iam_instance_profile                 = "SSM-Instance-Profile" -> null
      - id                                   = "i-0a4d58c278e0ab91f" -> null
      - instance_initiated_shutdown_behavior = "stop" -> null
      - instance_state                       = "running" -> null
      - instance_type                        = "t2.micro" -> null
      - ipv6_address_count                   = 0 -> null
      - ipv6_addresses                       = [] -> null
      - monitoring                           = false -> null
      - placement_partition_number           = 0 -> null
      - primary_network_interface_id         = "eni-08fce221a4783b64f" -> null
      - private_dns                          = "ip-10-1-2-59.ap-southeast-1.compute.internal" -> null
      - private_ip                           = "10.1.2.59" -> null
      - public_dns                           = "ec2-18-143-184-86.ap-southeast-1.compute.amazonaws.com" -> null
      - public_ip                            = "18.143.184.86" -> null
      - secondary_private_ips                = [] -> null
      - security_groups                      = [] -> null
      - source_dest_check                    = true -> null
      - subnet_id                            = "subnet-0fadefa76713ba20d" -> null
      - tags                                 = {
          - "Name" = "Server-AC"
        } -> null
      - tags_all                             = {
          - "Name" = "Server-AC"
        } -> null
      - tenancy                              = "default" -> null
      - user_data_replace_on_change          = false -> null
      - vpc_security_group_ids               = [
          - "sg-0f6fa8bd3c3bf0e7a",
        ] -> null
        # (7 unchanged attributes hidden)

      - capacity_reservation_specification {
          - capacity_reservation_preference = "open" -> null
        }

      - cpu_options {
          - core_count       = 1 -> null
          - threads_per_core = 1 -> null
            # (1 unchanged attribute hidden)
        }

      - credit_specification {
          - cpu_credits = "standard" -> null
        }

      - enclave_options {
          - enabled = false -> null
        }

      - maintenance_options {
          - auto_recovery = "default" -> null
        }

      - metadata_options {
          - http_endpoint               = "enabled" -> null
          - http_protocol_ipv6          = "disabled" -> null
          - http_put_response_hop_limit = 2 -> null
          - http_tokens                 = "required" -> null
          - instance_metadata_tags      = "disabled" -> null
        }

      - private_dns_name_options {
          - enable_resource_name_dns_a_record    = false -> null
          - enable_resource_name_dns_aaaa_record = false -> null
          - hostname_type                        = "ip-name" -> null
        }

      - root_block_device {
          - delete_on_termination = true -> null
          - device_name           = "/dev/xvda" -> null
          - encrypted             = false -> null
          - iops                  = 3000 -> null
          - tags                  = {} -> null
          - tags_all              = {} -> null
          - throughput            = 125 -> null
          - volume_id             = "vol-041bb0ce7c318123c" -> null
          - volume_size           = 8 -> null
          - volume_type           = "gp3" -> null
            # (1 unchanged attribute hidden)
        }
    }

  # aws_instance.servers["b"] will be destroyed
  - resource "aws_instance" "servers" {
      - ami                                  = "ami-009c9406091cbd65a" -> null
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:instance/i-00a256442c7086b11" -> null
      - associate_public_ip_address          = false -> null
      - availability_zone                    = "ap-southeast-1c" -> null
      - cpu_core_count                       = 1 -> null
      - cpu_threads_per_core                 = 1 -> null
      - disable_api_stop                     = false -> null
      - disable_api_termination              = false -> null
      - ebs_optimized                        = false -> null
      - get_password_data                    = false -> null
      - hibernation                          = false -> null
      - iam_instance_profile                 = "SSM-Instance-Profile" -> null
      - id                                   = "i-00a256442c7086b11" -> null
      - instance_initiated_shutdown_behavior = "stop" -> null
      - instance_state                       = "running" -> null
      - instance_type                        = "t2.micro" -> null
      - ipv6_address_count                   = 0 -> null
      - ipv6_addresses                       = [] -> null
      - monitoring                           = false -> null
      - placement_partition_number           = 0 -> null
      - primary_network_interface_id         = "eni-0f4e858477fcd1d92" -> null
      - private_dns                          = "ip-192-168-1-226.ap-southeast-1.compute.internal" -> null
      - private_ip                           = "192.168.1.226" -> null
      - secondary_private_ips                = [] -> null
      - security_groups                      = [] -> null
      - source_dest_check                    = true -> null
      - subnet_id                            = "subnet-00a4cf93a9c91659d" -> null
      - tags                                 = {
          - "Name" = "Server-B"
        } -> null
      - tags_all                             = {
          - "Name" = "Server-B"
        } -> null
      - tenancy                              = "default" -> null
      - user_data_replace_on_change          = false -> null
      - vpc_security_group_ids               = [
          - "sg-0cce6817ac2ecd093",
        ] -> null
        # (9 unchanged attributes hidden)

      - capacity_reservation_specification {
          - capacity_reservation_preference = "open" -> null
        }

      - cpu_options {
          - core_count       = 1 -> null
          - threads_per_core = 1 -> null
            # (1 unchanged attribute hidden)
        }

      - credit_specification {
          - cpu_credits = "standard" -> null
        }

      - enclave_options {
          - enabled = false -> null
        }

      - maintenance_options {
          - auto_recovery = "default" -> null
        }

      - metadata_options {
          - http_endpoint               = "enabled" -> null
          - http_protocol_ipv6          = "disabled" -> null
          - http_put_response_hop_limit = 2 -> null
          - http_tokens                 = "required" -> null
          - instance_metadata_tags      = "disabled" -> null
        }

      - private_dns_name_options {
          - enable_resource_name_dns_a_record    = false -> null
          - enable_resource_name_dns_aaaa_record = false -> null
          - hostname_type                        = "ip-name" -> null
        }

      - root_block_device {
          - delete_on_termination = true -> null
          - device_name           = "/dev/xvda" -> null
          - encrypted             = false -> null
          - iops                  = 3000 -> null
          - tags                  = {} -> null
          - tags_all              = {} -> null
          - throughput            = 125 -> null
          - volume_id             = "vol-0b510b5c3ba33c587" -> null
          - volume_size           = 8 -> null
          - volume_type           = "gp3" -> null
            # (1 unchanged attribute hidden)
        }
    }

  # aws_instance.servers["c"] will be destroyed
  - resource "aws_instance" "servers" {
      - ami                                  = "ami-009c9406091cbd65a" -> null
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:instance/i-003c43e8bd6ddf6de" -> null
      - associate_public_ip_address          = false -> null
      - availability_zone                    = "ap-southeast-1b" -> null
      - cpu_core_count                       = 1 -> null
      - cpu_threads_per_core                 = 1 -> null
      - disable_api_stop                     = false -> null
      - disable_api_termination              = false -> null
      - ebs_optimized                        = false -> null
      - get_password_data                    = false -> null
      - hibernation                          = false -> null
      - iam_instance_profile                 = "SSM-Instance-Profile" -> null
      - id                                   = "i-003c43e8bd6ddf6de" -> null
      - instance_initiated_shutdown_behavior = "stop" -> null
      - instance_state                       = "running" -> null
      - instance_type                        = "t2.micro" -> null
      - ipv6_address_count                   = 0 -> null
      - ipv6_addresses                       = [] -> null
      - monitoring                           = false -> null
      - placement_partition_number           = 0 -> null
      - primary_network_interface_id         = "eni-0b12d9cab20df2659" -> null
      - private_dns                          = "ip-192-168-2-126.ap-southeast-1.compute.internal" -> null
      - private_ip                           = "192.168.2.126" -> null
      - secondary_private_ips                = [] -> null
      - security_groups                      = [] -> null
      - source_dest_check                    = true -> null
      - subnet_id                            = "subnet-0e06d1461afbfcc64" -> null
      - tags                                 = {
          - "Name" = "Server-C"
        } -> null
      - tags_all                             = {
          - "Name" = "Server-C"
        } -> null
      - tenancy                              = "default" -> null
      - user_data_replace_on_change          = false -> null
      - vpc_security_group_ids               = [
          - "sg-09232b7656beb976a",
        ] -> null
        # (9 unchanged attributes hidden)

      - capacity_reservation_specification {
          - capacity_reservation_preference = "open" -> null
        }

      - cpu_options {
          - core_count       = 1 -> null
          - threads_per_core = 1 -> null
            # (1 unchanged attribute hidden)
        }

      - credit_specification {
          - cpu_credits = "standard" -> null
        }

      - enclave_options {
          - enabled = false -> null
        }

      - maintenance_options {
          - auto_recovery = "default" -> null
        }

      - metadata_options {
          - http_endpoint               = "enabled" -> null
          - http_protocol_ipv6          = "disabled" -> null
          - http_put_response_hop_limit = 2 -> null
          - http_tokens                 = "required" -> null
          - instance_metadata_tags      = "disabled" -> null
        }

      - private_dns_name_options {
          - enable_resource_name_dns_a_record    = false -> null
          - enable_resource_name_dns_aaaa_record = false -> null
          - hostname_type                        = "ip-name" -> null
        }

      - root_block_device {
          - delete_on_termination = true -> null
          - device_name           = "/dev/xvda" -> null
          - encrypted             = false -> null
          - iops                  = 3000 -> null
          - tags                  = {} -> null
          - tags_all              = {} -> null
          - throughput            = 125 -> null
          - volume_id             = "vol-0450c2ef6249eb179" -> null
          - volume_size           = 8 -> null
          - volume_type           = "gp3" -> null
            # (1 unchanged attribute hidden)
        }
    }

  # aws_internet_gateway.igw will be destroyed
  - resource "aws_internet_gateway" "igw" {
      - arn      = "arn:aws:ec2:ap-southeast-1:669745465514:internet-gateway/igw-0eca98843118df1a4" -> null
      - id       = "igw-0eca98843118df1a4" -> null
      - owner_id = "669745465514" -> null
      - tags     = {
          - "Name" = "Main IGW"
        } -> null
      - tags_all = {
          - "Name" = "Main IGW"
        } -> null
      - vpc_id   = "vpc-01f7f6416ea84664e" -> null
    }

  # aws_route_table.rt_a will be destroyed
  - resource "aws_route_table" "rt_a" {
      - arn              = "arn:aws:ec2:ap-southeast-1:669745465514:route-table/rtb-0903f5698419cb121" -> null
      - id               = "rtb-0903f5698419cb121" -> null
      - owner_id         = "669745465514" -> null
      - propagating_vgws = [] -> null
      - route            = [
          - {
              - cidr_block                 = "0.0.0.0/0"
              - gateway_id                 = "igw-0eca98843118df1a4"
                # (11 unchanged attributes hidden)
            },
          - {
              - cidr_block                 = "192.168.0.0/16"
              - vpc_peering_connection_id  = "pcx-03350e4a086d987b6"
                # (11 unchanged attributes hidden)
            },
        ] -> null
      - tags             = {
          - "Name" = "Route Table VPC-A"
        } -> null
      - tags_all         = {
          - "Name" = "Route Table VPC-A"
        } -> null
      - vpc_id           = "vpc-01f7f6416ea84664e" -> null
    }

  # aws_route_table.rt_bc[0] will be destroyed
  - resource "aws_route_table" "rt_bc" {
      - arn              = "arn:aws:ec2:ap-southeast-1:669745465514:route-table/rtb-0fb53a6db328557c4" -> null
      - id               = "rtb-0fb53a6db328557c4" -> null
      - owner_id         = "669745465514" -> null
      - propagating_vgws = [] -> null
      - route            = [
          - {
              - cidr_block                 = "10.1.0.0/16"
              - vpc_peering_connection_id  = "pcx-03350e4a086d987b6"
                # (11 unchanged attributes hidden)
            },
        ] -> null
      - tags             = {
          - "Name" = "Route Table VPC-B"
        } -> null
      - tags_all         = {
          - "Name" = "Route Table VPC-B"
        } -> null
      - vpc_id           = "vpc-058aaf52618f67601" -> null
    }

  # aws_route_table.rt_bc[1] will be destroyed
  - resource "aws_route_table" "rt_bc" {
      - arn              = "arn:aws:ec2:ap-southeast-1:669745465514:route-table/rtb-0929746b8657ad255" -> null
      - id               = "rtb-0929746b8657ad255" -> null
      - owner_id         = "669745465514" -> null
      - propagating_vgws = [] -> null
      - route            = [
          - {
              - cidr_block                 = "10.1.0.0/16"
              - vpc_peering_connection_id  = "pcx-01c23bbe456e6df4f"
                # (11 unchanged attributes hidden)
            },
        ] -> null
      - tags             = {
          - "Name" = "Route Table VPC-C"
        } -> null
      - tags_all         = {
          - "Name" = "Route Table VPC-C"
        } -> null
      - vpc_id           = "vpc-0ef85bbf333e81ec2" -> null
    }

  # aws_route_table_association.rta_a["a_subnet1"] will be destroyed
  - resource "aws_route_table_association" "rta_a" {
      - id             = "rtbassoc-016df4fcb3437b7fc" -> null
      - route_table_id = "rtb-0903f5698419cb121" -> null
      - subnet_id      = "subnet-0479fe1de69957b24" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_route_table_association.rta_a["a_subnet2"] will be destroyed
  - resource "aws_route_table_association" "rta_a" {
      - id             = "rtbassoc-006400f37ac92f0b6" -> null
      - route_table_id = "rtb-0903f5698419cb121" -> null
      - subnet_id      = "subnet-0fadefa76713ba20d" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_route_table_association.rta_bc["b_subnet1"] will be destroyed
  - resource "aws_route_table_association" "rta_bc" {
      - id             = "rtbassoc-013ed056fd192ab00" -> null
      - route_table_id = "rtb-0fb53a6db328557c4" -> null
      - subnet_id      = "subnet-00a4cf93a9c91659d" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_route_table_association.rta_bc["c_subnet1"] will be destroyed
  - resource "aws_route_table_association" "rta_bc" {
      - id             = "rtbassoc-06c5485838bdcbab5" -> null
      - route_table_id = "rtb-0929746b8657ad255" -> null
      - subnet_id      = "subnet-0e06d1461afbfcc64" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_security_group.security_groups["a"] will be destroyed
  - resource "aws_security_group" "security_groups" {
      - arn                    = "arn:aws:ec2:ap-southeast-1:669745465514:security-group/sg-0f6fa8bd3c3bf0e7a" -> null
      - description            = "Allow ICMP and SSH traffic" -> null
      - egress                 = [
          - {
              - cidr_blocks      = [
                  - "0.0.0.0/0",
                ]
              - from_port        = 0
              - ipv6_cidr_blocks = []
              - prefix_list_ids  = []
              - protocol         = "-1"
              - security_groups  = []
              - self             = false
              - to_port          = 0
                # (1 unchanged attribute hidden)
            },
        ] -> null
      - id                     = "sg-0f6fa8bd3c3bf0e7a" -> null
      - ingress                = [
          - {
              - cidr_blocks      = [
                  - "0.0.0.0/0",
                ]
              - from_port        = -1
              - ipv6_cidr_blocks = []
              - prefix_list_ids  = []
              - protocol         = "icmp"
              - security_groups  = []
              - self             = false
              - to_port          = -1
                # (1 unchanged attribute hidden)
            },
          - {
              - cidr_blocks      = [
                  - "0.0.0.0/0",
                ]
              - from_port        = 22
              - ipv6_cidr_blocks = []
              - prefix_list_ids  = []
              - protocol         = "tcp"
              - security_groups  = []
              - self             = false
              - to_port          = 22
                # (1 unchanged attribute hidden)
            },
        ] -> null
      - name                   = "Allow ICMP and SSH VPC-A" -> null
      - owner_id               = "669745465514" -> null
      - revoke_rules_on_delete = false -> null
      - tags                   = {
          - "Name" = "Allow ICMP and SSH traffic VPC-A"
        } -> null
      - tags_all               = {
          - "Name" = "Allow ICMP and SSH traffic VPC-A"
        } -> null
      - vpc_id                 = "vpc-01f7f6416ea84664e" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_security_group.security_groups["b"] will be destroyed
  - resource "aws_security_group" "security_groups" {
      - arn                    = "arn:aws:ec2:ap-southeast-1:669745465514:security-group/sg-0cce6817ac2ecd093" -> null
      - description            = "Allow ICMP and SSH traffic" -> null
      - egress                 = [
          - {
              - cidr_blocks      = [
                  - "0.0.0.0/0",
                ]
              - from_port        = 0
              - ipv6_cidr_blocks = []
              - prefix_list_ids  = []
              - protocol         = "-1"
              - security_groups  = []
              - self             = false
              - to_port          = 0
                # (1 unchanged attribute hidden)
            },
        ] -> null
      - id                     = "sg-0cce6817ac2ecd093" -> null
      - ingress                = [
          - {
              - cidr_blocks      = [
                  - "0.0.0.0/0",
                ]
              - from_port        = -1
              - ipv6_cidr_blocks = []
              - prefix_list_ids  = []
              - protocol         = "icmp"
              - security_groups  = []
              - self             = false
              - to_port          = -1
                # (1 unchanged attribute hidden)
            },
          - {
              - cidr_blocks      = [
                  - "0.0.0.0/0",
                ]
              - from_port        = 22
              - ipv6_cidr_blocks = []
              - prefix_list_ids  = []
              - protocol         = "tcp"
              - security_groups  = []
              - self             = false
              - to_port          = 22
                # (1 unchanged attribute hidden)
            },
        ] -> null
      - name                   = "Allow ICMP and SSH VPC-B" -> null
      - owner_id               = "669745465514" -> null
      - revoke_rules_on_delete = false -> null
      - tags                   = {
          - "Name" = "Allow ICMP and SSH traffic VPC-B"
        } -> null
      - tags_all               = {
          - "Name" = "Allow ICMP and SSH traffic VPC-B"
        } -> null
      - vpc_id                 = "vpc-058aaf52618f67601" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_security_group.security_groups["c"] will be destroyed
  - resource "aws_security_group" "security_groups" {
      - arn                    = "arn:aws:ec2:ap-southeast-1:669745465514:security-group/sg-09232b7656beb976a" -> null
      - description            = "Allow ICMP and SSH traffic" -> null
      - egress                 = [
          - {
              - cidr_blocks      = [
                  - "0.0.0.0/0",
                ]
              - from_port        = 0
              - ipv6_cidr_blocks = []
              - prefix_list_ids  = []
              - protocol         = "-1"
              - security_groups  = []
              - self             = false
              - to_port          = 0
                # (1 unchanged attribute hidden)
            },
        ] -> null
      - id                     = "sg-09232b7656beb976a" -> null
      - ingress                = [
          - {
              - cidr_blocks      = [
                  - "0.0.0.0/0",
                ]
              - from_port        = -1
              - ipv6_cidr_blocks = []
              - prefix_list_ids  = []
              - protocol         = "icmp"
              - security_groups  = []
              - self             = false
              - to_port          = -1
                # (1 unchanged attribute hidden)
            },
          - {
              - cidr_blocks      = [
                  - "0.0.0.0/0",
                ]
              - from_port        = 22
              - ipv6_cidr_blocks = []
              - prefix_list_ids  = []
              - protocol         = "tcp"
              - security_groups  = []
              - self             = false
              - to_port          = 22
                # (1 unchanged attribute hidden)
            },
        ] -> null
      - name                   = "Allow ICMP and SSH VPC-C" -> null
      - owner_id               = "669745465514" -> null
      - revoke_rules_on_delete = false -> null
      - tags                   = {
          - "Name" = "Allow ICMP and SSH traffic VPC-C"
        } -> null
      - tags_all               = {
          - "Name" = "Allow ICMP and SSH traffic VPC-C"
        } -> null
      - vpc_id                 = "vpc-0ef85bbf333e81ec2" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_subnet.subnets["a_subnet1"] will be destroyed
  - resource "aws_subnet" "subnets" {
      - arn                                            = "arn:aws:ec2:ap-southeast-1:669745465514:subnet/subnet-0479fe1de69957b24" -> null
      - assign_ipv6_address_on_creation                = false -> null
      - availability_zone                              = "ap-southeast-1a" -> null
      - availability_zone_id                           = "apse1-az2" -> null
      - cidr_block                                     = "10.1.1.0/24" -> null
      - enable_dns64                                   = false -> null
      - enable_lni_at_device_index                     = 0 -> null
      - enable_resource_name_dns_a_record_on_launch    = false -> null
      - enable_resource_name_dns_aaaa_record_on_launch = false -> null
      - id                                             = "subnet-0479fe1de69957b24" -> null
      - ipv6_native                                    = false -> null
      - map_customer_owned_ip_on_launch                = false -> null
      - map_public_ip_on_launch                        = false -> null
      - owner_id                                       = "669745465514" -> null
      - private_dns_hostname_type_on_launch            = "ip-name" -> null
      - tags                                           = {
          - "Name" = "Subnet-A-subnet1"
        } -> null
      - tags_all                                       = {
          - "Name" = "Subnet-A-subnet1"
        } -> null
      - vpc_id                                         = "vpc-01f7f6416ea84664e" -> null
        # (4 unchanged attributes hidden)
    }

  # aws_subnet.subnets["a_subnet2"] will be destroyed
  - resource "aws_subnet" "subnets" {
      - arn                                            = "arn:aws:ec2:ap-southeast-1:669745465514:subnet/subnet-0fadefa76713ba20d" -> null
      - assign_ipv6_address_on_creation                = false -> null
      - availability_zone                              = "ap-southeast-1c" -> null
      - availability_zone_id                           = "apse1-az3" -> null
      - cidr_block                                     = "10.1.2.0/24" -> null
      - enable_dns64                                   = false -> null
      - enable_lni_at_device_index                     = 0 -> null
      - enable_resource_name_dns_a_record_on_launch    = false -> null
      - enable_resource_name_dns_aaaa_record_on_launch = false -> null
      - id                                             = "subnet-0fadefa76713ba20d" -> null
      - ipv6_native                                    = false -> null
      - map_customer_owned_ip_on_launch                = false -> null
      - map_public_ip_on_launch                        = false -> null
      - owner_id                                       = "669745465514" -> null
      - private_dns_hostname_type_on_launch            = "ip-name" -> null
      - tags                                           = {
          - "Name" = "Subnet-A-subnet2"
        } -> null
      - tags_all                                       = {
          - "Name" = "Subnet-A-subnet2"
        } -> null
      - vpc_id                                         = "vpc-01f7f6416ea84664e" -> null
        # (4 unchanged attributes hidden)
    }

  # aws_subnet.subnets["b_subnet1"] will be destroyed
  - resource "aws_subnet" "subnets" {
      - arn                                            = "arn:aws:ec2:ap-southeast-1:669745465514:subnet/subnet-00a4cf93a9c91659d" -> null
      - assign_ipv6_address_on_creation                = false -> null
      - availability_zone                              = "ap-southeast-1c" -> null
      - availability_zone_id                           = "apse1-az3" -> null
      - cidr_block                                     = "192.168.1.0/24" -> null
      - enable_dns64                                   = false -> null
      - enable_lni_at_device_index                     = 0 -> null
      - enable_resource_name_dns_a_record_on_launch    = false -> null
      - enable_resource_name_dns_aaaa_record_on_launch = false -> null
      - id                                             = "subnet-00a4cf93a9c91659d" -> null
      - ipv6_native                                    = false -> null
      - map_customer_owned_ip_on_launch                = false -> null
      - map_public_ip_on_launch                        = false -> null
      - owner_id                                       = "669745465514" -> null
      - private_dns_hostname_type_on_launch            = "ip-name" -> null
      - tags                                           = {
          - "Name" = "Subnet-B-subnet1"
        } -> null
      - tags_all                                       = {
          - "Name" = "Subnet-B-subnet1"
        } -> null
      - vpc_id                                         = "vpc-058aaf52618f67601" -> null
        # (4 unchanged attributes hidden)
    }

  # aws_subnet.subnets["c_subnet1"] will be destroyed
  - resource "aws_subnet" "subnets" {
      - arn                                            = "arn:aws:ec2:ap-southeast-1:669745465514:subnet/subnet-0e06d1461afbfcc64" -> null
      - assign_ipv6_address_on_creation                = false -> null
      - availability_zone                              = "ap-southeast-1b" -> null
      - availability_zone_id                           = "apse1-az1" -> null
      - cidr_block                                     = "192.168.2.0/24" -> null
      - enable_dns64                                   = false -> null
      - enable_lni_at_device_index                     = 0 -> null
      - enable_resource_name_dns_a_record_on_launch    = false -> null
      - enable_resource_name_dns_aaaa_record_on_launch = false -> null
      - id                                             = "subnet-0e06d1461afbfcc64" -> null
      - ipv6_native                                    = false -> null
      - map_customer_owned_ip_on_launch                = false -> null
      - map_public_ip_on_launch                        = false -> null
      - owner_id                                       = "669745465514" -> null
      - private_dns_hostname_type_on_launch            = "ip-name" -> null
      - tags                                           = {
          - "Name" = "Subnet-C-subnet1"
        } -> null
      - tags_all                                       = {
          - "Name" = "Subnet-C-subnet1"
        } -> null
      - vpc_id                                         = "vpc-0ef85bbf333e81ec2" -> null
        # (4 unchanged attributes hidden)
    }

  # aws_vpc.vpcs["a"] will be destroyed
  - resource "aws_vpc" "vpcs" {
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:vpc/vpc-01f7f6416ea84664e" -> null
      - assign_generated_ipv6_cidr_block     = false -> null
      - cidr_block                           = "10.1.0.0/16" -> null
      - default_network_acl_id               = "acl-0b9493896a4a34b18" -> null
      - default_route_table_id               = "rtb-00fa411b1f300ffa5" -> null
      - default_security_group_id            = "sg-054f9589694a15902" -> null
      - dhcp_options_id                      = "dopt-06b97e6ae44d1358c" -> null
      - enable_dns_hostnames                 = true -> null
      - enable_dns_support                   = true -> null
      - enable_network_address_usage_metrics = false -> null
      - id                                   = "vpc-01f7f6416ea84664e" -> null
      - instance_tenancy                     = "default" -> null
      - ipv6_netmask_length                  = 0 -> null
      - main_route_table_id                  = "rtb-00fa411b1f300ffa5" -> null
      - owner_id                             = "669745465514" -> null
      - tags                                 = {
          - "Name" = "VPC-A"
        } -> null
      - tags_all                             = {
          - "Name" = "VPC-A"
        } -> null
        # (4 unchanged attributes hidden)
    }

  # aws_vpc.vpcs["b"] will be destroyed
  - resource "aws_vpc" "vpcs" {
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:vpc/vpc-058aaf52618f67601" -> null
      - assign_generated_ipv6_cidr_block     = false -> null
      - cidr_block                           = "192.168.0.0/16" -> null
      - default_network_acl_id               = "acl-0dd6fe7c7d4801b0a" -> null
      - default_route_table_id               = "rtb-052a08ca916404f0e" -> null
      - default_security_group_id            = "sg-09751624c38282837" -> null
      - dhcp_options_id                      = "dopt-06b97e6ae44d1358c" -> null
      - enable_dns_hostnames                 = true -> null
      - enable_dns_support                   = true -> null
      - enable_network_address_usage_metrics = false -> null
      - id                                   = "vpc-058aaf52618f67601" -> null
      - instance_tenancy                     = "default" -> null
      - ipv6_netmask_length                  = 0 -> null
      - main_route_table_id                  = "rtb-052a08ca916404f0e" -> null
      - owner_id                             = "669745465514" -> null
      - tags                                 = {
          - "Name" = "VPC-B"
        } -> null
      - tags_all                             = {
          - "Name" = "VPC-B"
        } -> null
        # (4 unchanged attributes hidden)
    }

  # aws_vpc.vpcs["c"] will be destroyed
  - resource "aws_vpc" "vpcs" {
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:vpc/vpc-0ef85bbf333e81ec2" -> null
      - assign_generated_ipv6_cidr_block     = false -> null
      - cidr_block                           = "192.168.0.0/16" -> null
      - default_network_acl_id               = "acl-035ad09efba2b5966" -> null
      - default_route_table_id               = "rtb-073dd017bbeaf66fa" -> null
      - default_security_group_id            = "sg-09855bce055cbe1d4" -> null
      - dhcp_options_id                      = "dopt-06b97e6ae44d1358c" -> null
      - enable_dns_hostnames                 = true -> null
      - enable_dns_support                   = true -> null
      - enable_network_address_usage_metrics = false -> null
      - id                                   = "vpc-0ef85bbf333e81ec2" -> null
      - instance_tenancy                     = "default" -> null
      - ipv6_netmask_length                  = 0 -> null
      - main_route_table_id                  = "rtb-073dd017bbeaf66fa" -> null
      - owner_id                             = "669745465514" -> null
      - tags                                 = {
          - "Name" = "VPC-C"
        } -> null
      - tags_all                             = {
          - "Name" = "VPC-C"
        } -> null
        # (4 unchanged attributes hidden)
    }

  # aws_vpc_peering_connection.peering[0] will be destroyed
  - resource "aws_vpc_peering_connection" "peering" {
      - accept_status = "active" -> null
      - auto_accept   = true -> null
      - id            = "pcx-03350e4a086d987b6" -> null
      - peer_owner_id = "669745465514" -> null
      - peer_region   = "ap-southeast-1" -> null
      - peer_vpc_id   = "vpc-058aaf52618f67601" -> null
      - tags          = {
          - "Name" = "VPC-A to VPC-B Peering"
        } -> null
      - tags_all      = {
          - "Name" = "VPC-A to VPC-B Peering"
        } -> null
      - vpc_id        = "vpc-01f7f6416ea84664e" -> null

      - accepter {
          - allow_remote_vpc_dns_resolution = false -> null
        }

      - requester {
          - allow_remote_vpc_dns_resolution = false -> null
        }
    }

  # aws_vpc_peering_connection.peering[1] will be destroyed
  - resource "aws_vpc_peering_connection" "peering" {
      - accept_status = "active" -> null
      - auto_accept   = true -> null
      - id            = "pcx-01c23bbe456e6df4f" -> null
      - peer_owner_id = "669745465514" -> null
      - peer_region   = "ap-southeast-1" -> null
      - peer_vpc_id   = "vpc-0ef85bbf333e81ec2" -> null
      - tags          = {
          - "Name" = "VPC-A to VPC-C Peering"
        } -> null
      - tags_all      = {
          - "Name" = "VPC-A to VPC-C Peering"
        } -> null
      - vpc_id        = "vpc-01f7f6416ea84664e" -> null

      - accepter {
          - allow_remote_vpc_dns_resolution = false -> null
        }

      - requester {
          - allow_remote_vpc_dns_resolution = false -> null
        }
    }

Plan: 0 to add, 0 to change, 27 to destroy.

Changes to Outputs:
  - test_instructions = <<-EOT
        1. SSH into Server-AB or Server-AC using their public IPs.
           Server-AB Public IP: 18.143.116.250
           Server-AC Public IP: 18.143.184.86
        
        2. From Server-AB, try to ping Server-B:
           Server-B Private IP: 192.168.1.226
        
        3. To test connectivity with Server-C:
           a. Go to the AWS VPC Console
           b. Find the route table for VPC-A
           c. Edit the route for 192.168.0.0/16
           d. Change the target to the peering connection with VPC-C
        
        4. After changing the route, from Server-AC, try to ping Server-C:
           Server-C Private IP: 192.168.2.126
        
        5. Remember to switch the route back to the peering connection with VPC-B if you want to test connectivity with Server-B again.
    EOT -> null
aws_route_table_association.rta_a["a_subnet1"]: Destroying... [id=rtbassoc-016df4fcb3437b7fc]
aws_iam_role_policy_attachment.ssm_policy: Destroying... [id=SSM-Role-20240904045108415500000001]
aws_route_table_association.rta_bc["b_subnet1"]: Destroying... [id=rtbassoc-013ed056fd192ab00]
aws_route_table_association.rta_a["a_subnet2"]: Destroying... [id=rtbassoc-006400f37ac92f0b6]
aws_route_table_association.rta_bc["c_subnet1"]: Destroying... [id=rtbassoc-06c5485838bdcbab5]
aws_instance.servers["ab"]: Destroying... [id=i-05fc2c9d6066dbb6a]
aws_instance.servers["c"]: Destroying... [id=i-003c43e8bd6ddf6de]
aws_instance.servers["ac"]: Destroying... [id=i-0a4d58c278e0ab91f]
aws_instance.servers["b"]: Destroying... [id=i-00a256442c7086b11]
aws_route_table_association.rta_bc["c_subnet1"]: Destruction complete after 0s
aws_route_table_association.rta_bc["b_subnet1"]: Destruction complete after 0s
aws_route_table_association.rta_a["a_subnet2"]: Destruction complete after 0s
aws_route_table_association.rta_a["a_subnet1"]: Destruction complete after 0s
aws_route_table.rt_bc[1]: Destroying... [id=rtb-0929746b8657ad255]
aws_route_table.rt_bc[0]: Destroying... [id=rtb-0fb53a6db328557c4]
aws_route_table.rt_a: Destroying... [id=rtb-0903f5698419cb121]
aws_route_table.rt_bc[1]: Destruction complete after 1s
aws_route_table.rt_bc[0]: Destruction complete after 1s
aws_route_table.rt_a: Destruction complete after 1s
aws_internet_gateway.igw: Destroying... [id=igw-0eca98843118df1a4]
aws_vpc_peering_connection.peering[1]: Destroying... [id=pcx-01c23bbe456e6df4f]
aws_vpc_peering_connection.peering[0]: Destroying... [id=pcx-03350e4a086d987b6]
aws_iam_role_policy_attachment.ssm_policy: Destruction complete after 1s
aws_vpc_peering_connection.peering[0]: Destruction complete after 0s
aws_vpc_peering_connection.peering[1]: Destruction complete after 0s
aws_instance.servers["ab"]: Still destroying... [id=i-05fc2c9d6066dbb6a, 10s elapsed]
aws_instance.servers["c"]: Still destroying... [id=i-003c43e8bd6ddf6de, 10s elapsed]
aws_instance.servers["ac"]: Still destroying... [id=i-0a4d58c278e0ab91f, 10s elapsed]
aws_instance.servers["b"]: Still destroying... [id=i-00a256442c7086b11, 10s elapsed]
aws_internet_gateway.igw: Still destroying... [id=igw-0eca98843118df1a4, 10s elapsed]
aws_instance.servers["ab"]: Still destroying... [id=i-05fc2c9d6066dbb6a, 20s elapsed]
aws_instance.servers["c"]: Still destroying... [id=i-003c43e8bd6ddf6de, 20s elapsed]
aws_instance.servers["ac"]: Still destroying... [id=i-0a4d58c278e0ab91f, 20s elapsed]
aws_instance.servers["b"]: Still destroying... [id=i-00a256442c7086b11, 20s elapsed]
aws_internet_gateway.igw: Still destroying... [id=igw-0eca98843118df1a4, 20s elapsed]
aws_instance.servers["c"]: Still destroying... [id=i-003c43e8bd6ddf6de, 30s elapsed]
aws_instance.servers["ab"]: Still destroying... [id=i-05fc2c9d6066dbb6a, 30s elapsed]
aws_instance.servers["b"]: Still destroying... [id=i-00a256442c7086b11, 30s elapsed]
aws_instance.servers["ac"]: Still destroying... [id=i-0a4d58c278e0ab91f, 30s elapsed]
aws_instance.servers["ab"]: Destruction complete after 30s
aws_internet_gateway.igw: Still destroying... [id=igw-0eca98843118df1a4, 30s elapsed]
aws_instance.servers["c"]: Still destroying... [id=i-003c43e8bd6ddf6de, 40s elapsed]
aws_instance.servers["ac"]: Still destroying... [id=i-0a4d58c278e0ab91f, 40s elapsed]
aws_instance.servers["b"]: Still destroying... [id=i-00a256442c7086b11, 40s elapsed]
aws_internet_gateway.igw: Still destroying... [id=igw-0eca98843118df1a4, 40s elapsed]
aws_instance.servers["c"]: Still destroying... [id=i-003c43e8bd6ddf6de, 50s elapsed]
aws_instance.servers["ac"]: Still destroying... [id=i-0a4d58c278e0ab91f, 50s elapsed]
aws_instance.servers["b"]: Still destroying... [id=i-00a256442c7086b11, 50s elapsed]
aws_instance.servers["c"]: Destruction complete after 50s
aws_internet_gateway.igw: Still destroying... [id=igw-0eca98843118df1a4, 50s elapsed]
aws_internet_gateway.igw: Destruction complete after 57s
aws_instance.servers["b"]: Still destroying... [id=i-00a256442c7086b11, 1m0s elapsed]
aws_instance.servers["ac"]: Still destroying... [id=i-0a4d58c278e0ab91f, 1m0s elapsed]
aws_instance.servers["ac"]: Destruction complete after 1m1s
aws_instance.servers["b"]: Still destroying... [id=i-00a256442c7086b11, 1m10s elapsed]
aws_instance.servers["b"]: Still destroying... [id=i-00a256442c7086b11, 1m20s elapsed]
aws_instance.servers["b"]: Destruction complete after 1m21s
aws_subnet.subnets["b_subnet1"]: Destroying... [id=subnet-00a4cf93a9c91659d]
aws_subnet.subnets["c_subnet1"]: Destroying... [id=subnet-0e06d1461afbfcc64]
aws_security_group.security_groups["c"]: Destroying... [id=sg-09232b7656beb976a]
aws_subnet.subnets["a_subnet2"]: Destroying... [id=subnet-0fadefa76713ba20d]
aws_iam_instance_profile.ssm_profile: Destroying... [id=SSM-Instance-Profile]
aws_subnet.subnets["a_subnet1"]: Destroying... [id=subnet-0479fe1de69957b24]
aws_security_group.security_groups["a"]: Destroying... [id=sg-0f6fa8bd3c3bf0e7a]
aws_security_group.security_groups["b"]: Destroying... [id=sg-0cce6817ac2ecd093]
aws_subnet.subnets["a_subnet2"]: Destruction complete after 1s
aws_subnet.subnets["c_subnet1"]: Destruction complete after 1s
aws_security_group.security_groups["a"]: Destruction complete after 1s
aws_security_group.security_groups["b"]: Destruction complete after 1s
aws_security_group.security_groups["c"]: Destruction complete after 1s
aws_subnet.subnets["a_subnet1"]: Destruction complete after 1s
aws_subnet.subnets["b_subnet1"]: Destruction complete after 1s
aws_vpc.vpcs["a"]: Destroying... [id=vpc-01f7f6416ea84664e]
aws_vpc.vpcs["c"]: Destroying... [id=vpc-0ef85bbf333e81ec2]
aws_vpc.vpcs["b"]: Destroying... [id=vpc-058aaf52618f67601]
aws_iam_instance_profile.ssm_profile: Destruction complete after 2s
aws_iam_role.ssm_role: Destroying... [id=SSM-Role]
aws_vpc.vpcs["a"]: Destruction complete after 1s
aws_vpc.vpcs["b"]: Destruction complete after 1s
aws_vpc.vpcs["c"]: Destruction complete after 1s
aws_iam_role.ssm_role: Destruction complete after 1s

Destroy complete! Resources: 27 destroyed.
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case02$ 
```
