# Exploring AWS VPC Peering with Terraform

![](./images/Exploring%20AWS%20VPC%20Peering%20with%20Terraform.png)
## Caes-01 Scenario 
Output

```
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case01$ terraform init
Initializing the backend...
Initializing provider plugins...
- Reusing previous version of hashicorp/aws from the dependency lock file
- Using previously-installed hashicorp/aws v5.65.0

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case01$ 
```


```
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case01$ terraform plan

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

  # aws_route.internet_access will be created
  + resource "aws_route" "internet_access" {
      + destination_cidr_block = "0.0.0.0/0"
      + gateway_id             = (known after apply)
      + id                     = (known after apply)
      + instance_id            = (known after apply)
      + instance_owner_id      = (known after apply)
      + network_interface_id   = (known after apply)
      + origin                 = (known after apply)
      + route_table_id         = (known after apply)
      + state                  = (known after apply)
    }

  # aws_route_table.rt_a will be created
  + resource "aws_route_table" "rt_a" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
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

  # aws_route_table_association.rta_a will be created
  + resource "aws_route_table_association" "rta_a" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.rta_bc[0] will be created
  + resource "aws_route_table_association" "rta_bc" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.rta_bc[1] will be created
  + resource "aws_route_table_association" "rta_bc" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_security_group.security_groups["a"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP traffic"
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
        ]
      + name                   = "Allow ICMP VPC-A"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP traffic VPC-A"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP traffic VPC-A"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_security_group.security_groups["b"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP traffic"
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
        ]
      + name                   = "Allow ICMP VPC-B"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP traffic VPC-B"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP traffic VPC-B"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_security_group.security_groups["c"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP traffic"
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
        ]
      + name                   = "Allow ICMP VPC-C"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP traffic VPC-C"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP traffic VPC-C"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_subnet.subnets["a"] will be created
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
          + "Name" = "Subnet-A"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-A"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.subnets["b"] will be created
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
          + "Name" = "Subnet-B"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-B"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.subnets["c"] will be created
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
          + "Name" = "Subnet-C"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-C"
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
          + "Name" = "VPC-A to VPC-B Peering "
        }
      + tags_all      = {
          + "Name" = "VPC-A to VPC-B Peering "
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
          + "Name" = "VPC-A to VPC-C Peering "
        }
      + tags_all      = {
          + "Name" = "VPC-A to VPC-C Peering "
        }
      + vpc_id        = (known after apply)

      + accepter (known after apply)

      + requester (known after apply)
    }

Plan: 26 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + test_instructions = (known after apply)

────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

Note: You didn't use the -out option to save this plan, so Terraform can't guarantee to take exactly these actions if you run "terraform apply" now.
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case01$ 
```


```
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case01$ terraform apply -auto-approve

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

  # aws_route.internet_access will be created
  + resource "aws_route" "internet_access" {
      + destination_cidr_block = "0.0.0.0/0"
      + gateway_id             = (known after apply)
      + id                     = (known after apply)
      + instance_id            = (known after apply)
      + instance_owner_id      = (known after apply)
      + network_interface_id   = (known after apply)
      + origin                 = (known after apply)
      + route_table_id         = (known after apply)
      + state                  = (known after apply)
    }

  # aws_route_table.rt_a will be created
  + resource "aws_route_table" "rt_a" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
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

  # aws_route_table_association.rta_a will be created
  + resource "aws_route_table_association" "rta_a" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.rta_bc[0] will be created
  + resource "aws_route_table_association" "rta_bc" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.rta_bc[1] will be created
  + resource "aws_route_table_association" "rta_bc" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_security_group.security_groups["a"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP traffic"
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
        ]
      + name                   = "Allow ICMP VPC-A"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP traffic VPC-A"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP traffic VPC-A"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_security_group.security_groups["b"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP traffic"
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
        ]
      + name                   = "Allow ICMP VPC-B"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP traffic VPC-B"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP traffic VPC-B"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_security_group.security_groups["c"] will be created
  + resource "aws_security_group" "security_groups" {
      + arn                    = (known after apply)
      + description            = "Allow ICMP traffic"
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
        ]
      + name                   = "Allow ICMP VPC-C"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Name" = "Allow ICMP traffic VPC-C"
        }
      + tags_all               = {
          + "Name" = "Allow ICMP traffic VPC-C"
        }
      + vpc_id                 = (known after apply)
    }

  # aws_subnet.subnets["a"] will be created
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
          + "Name" = "Subnet-A"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-A"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.subnets["b"] will be created
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
          + "Name" = "Subnet-B"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-B"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.subnets["c"] will be created
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
          + "Name" = "Subnet-C"
        }
      + tags_all                                       = {
          + "Name" = "Subnet-C"
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
          + "Name" = "VPC-A to VPC-B Peering "
        }
      + tags_all      = {
          + "Name" = "VPC-A to VPC-B Peering "
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
          + "Name" = "VPC-A to VPC-C Peering "
        }
      + tags_all      = {
          + "Name" = "VPC-A to VPC-C Peering "
        }
      + vpc_id        = (known after apply)

      + accepter (known after apply)

      + requester (known after apply)
    }

Plan: 26 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + test_instructions = (known after apply)
aws_iam_role.ssm_role: Creating...
aws_vpc.vpcs["c"]: Creating...
aws_vpc.vpcs["a"]: Creating...
aws_vpc.vpcs["b"]: Creating...
aws_iam_role.ssm_role: Creation complete after 2s [id=SSM-Role]
aws_iam_instance_profile.ssm_profile: Creating...
aws_iam_role_policy_attachment.ssm_policy: Creating...
aws_iam_role_policy_attachment.ssm_policy: Creation complete after 1s [id=SSM-Role-20240904043854484000000001]
aws_iam_instance_profile.ssm_profile: Creation complete after 2s [id=SSM-Instance-Profile]
aws_vpc.vpcs["c"]: Still creating... [10s elapsed]
aws_vpc.vpcs["a"]: Still creating... [10s elapsed]
aws_vpc.vpcs["b"]: Still creating... [10s elapsed]
aws_vpc.vpcs["b"]: Creation complete after 11s [id=vpc-08734d10537b6e439]
aws_vpc.vpcs["c"]: Creation complete after 11s [id=vpc-04dd1fc8878ebd4a0]
aws_vpc.vpcs["a"]: Creation complete after 11s [id=vpc-08ef5048dd424eed1]
aws_vpc_peering_connection.peering[0]: Creating...
aws_subnet.subnets["a"]: Creating...
aws_subnet.subnets["b"]: Creating...
aws_vpc_peering_connection.peering[1]: Creating...
aws_security_group.security_groups["b"]: Creating...
aws_internet_gateway.igw: Creating...
aws_security_group.security_groups["a"]: Creating...
aws_security_group.security_groups["c"]: Creating...
aws_subnet.subnets["c"]: Creating...
aws_internet_gateway.igw: Creation complete after 1s [id=igw-0192bbe5a3160fd06]
aws_subnet.subnets["a"]: Creation complete after 1s [id=subnet-0bfac2eccf96780ed]
aws_subnet.subnets["b"]: Creation complete after 1s [id=subnet-048b1ac196e579fbc]
aws_subnet.subnets["c"]: Creation complete after 1s [id=subnet-0c60b127fa6e35de5]
aws_vpc_peering_connection.peering[0]: Creation complete after 2s [id=pcx-0af3cf5276c550d93]
aws_route_table.rt_a: Creating...
aws_vpc_peering_connection.peering[1]: Creation complete after 2s [id=pcx-0dba46795dcbc9e97]
aws_route_table.rt_bc[0]: Creating...
aws_route_table.rt_bc[1]: Creating...
aws_route_table.rt_bc[0]: Creation complete after 1s [id=rtb-05963d51131240961]
aws_route_table.rt_bc[1]: Creation complete after 1s [id=rtb-0378a7896d4d5cced]
aws_route_table_association.rta_bc[1]: Creating...
aws_route_table_association.rta_bc[0]: Creating...
aws_route_table.rt_a: Creation complete after 1s [id=rtb-0516af31ad284e3e6]
aws_route_table_association.rta_a: Creating...
aws_route.internet_access: Creating...
aws_security_group.security_groups["c"]: Creation complete after 3s [id=sg-0cb51ba7dba1c93ea]
aws_security_group.security_groups["b"]: Creation complete after 3s [id=sg-0cc99e0b418b40fe5]
aws_security_group.security_groups["a"]: Creation complete after 3s [id=sg-0d23cf1b7294c512e]
aws_instance.servers["c"]: Creating...
aws_instance.servers["ab"]: Creating...
aws_instance.servers["b"]: Creating...
aws_instance.servers["ac"]: Creating...
aws_route_table_association.rta_bc[1]: Creation complete after 0s [id=rtbassoc-067de8b590bf388d2]
aws_route_table_association.rta_bc[0]: Creation complete after 0s [id=rtbassoc-047cb69ad1d23861f]
aws_route_table_association.rta_a: Creation complete after 0s [id=rtbassoc-0721a5244f7caac95]
aws_route.internet_access: Creation complete after 0s [id=r-rtb-0516af31ad284e3e61080289494]
aws_instance.servers["c"]: Still creating... [10s elapsed]
aws_instance.servers["ab"]: Still creating... [10s elapsed]
aws_instance.servers["ac"]: Still creating... [10s elapsed]
aws_instance.servers["b"]: Still creating... [10s elapsed]
aws_instance.servers["c"]: Creation complete after 13s [id=i-0a0b12a99b902dfcd]
aws_instance.servers["ab"]: Still creating... [20s elapsed]
aws_instance.servers["ac"]: Still creating... [20s elapsed]
aws_instance.servers["b"]: Still creating... [20s elapsed]
aws_instance.servers["ab"]: Creation complete after 22s [id=i-08523984a6c049465]
aws_instance.servers["b"]: Creation complete after 22s [id=i-03ccd22fa08caffd7]
aws_instance.servers["ac"]: Still creating... [30s elapsed]
aws_instance.servers["ac"]: Creation complete after 32s [id=i-0ec016c966441ba3d]

Apply complete! Resources: 26 added, 0 changed, 0 destroyed.

Outputs:

test_instructions = <<EOT

1. SSH into Server-AB or Server-AC using their public IPs.
   Server-AB Public IP: 13.215.208.255
   Server-AC Public IP: 54.169.164.2

2. From Server-AB, try to ping Server-B:
   Server-B Private IP: 192.168.1.7

3. To test connectivity with Server-C:
   a. Go to the AWS VPC Console
   b. Find the route table for VPC-A
   c. Edit the route for 192.168.0.0/16
   d. Change the target to the peering connection with VPC-C

4. After changing the route, from Server-AC, try to ping Server-C:
   Server-C Private IP: 192.168.2.34

5. Remember to switch the route back to the peering connection with VPC-B if you want to test connectivity with Server-B again.


EOT
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case01$ 
```

```
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case01$ terraform destroy -auto-approve
aws_vpc.vpcs["b"]: Refreshing state... [id=vpc-08734d10537b6e439]
aws_iam_role.ssm_role: Refreshing state... [id=SSM-Role]
aws_vpc.vpcs["a"]: Refreshing state... [id=vpc-08ef5048dd424eed1]
aws_vpc.vpcs["c"]: Refreshing state... [id=vpc-04dd1fc8878ebd4a0]
aws_subnet.subnets["a"]: Refreshing state... [id=subnet-0bfac2eccf96780ed]
aws_internet_gateway.igw: Refreshing state... [id=igw-0192bbe5a3160fd06]
aws_subnet.subnets["b"]: Refreshing state... [id=subnet-048b1ac196e579fbc]
aws_security_group.security_groups["b"]: Refreshing state... [id=sg-0cc99e0b418b40fe5]
aws_security_group.security_groups["a"]: Refreshing state... [id=sg-0d23cf1b7294c512e]
aws_vpc_peering_connection.peering[0]: Refreshing state... [id=pcx-0af3cf5276c550d93]
aws_subnet.subnets["c"]: Refreshing state... [id=subnet-0c60b127fa6e35de5]
aws_security_group.security_groups["c"]: Refreshing state... [id=sg-0cb51ba7dba1c93ea]
aws_vpc_peering_connection.peering[1]: Refreshing state... [id=pcx-0dba46795dcbc9e97]
aws_route_table.rt_a: Refreshing state... [id=rtb-0516af31ad284e3e6]
aws_route_table.rt_bc[1]: Refreshing state... [id=rtb-0378a7896d4d5cced]
aws_route_table.rt_bc[0]: Refreshing state... [id=rtb-05963d51131240961]
aws_route_table_association.rta_a: Refreshing state... [id=rtbassoc-0721a5244f7caac95]
aws_route.internet_access: Refreshing state... [id=r-rtb-0516af31ad284e3e61080289494]
aws_route_table_association.rta_bc[1]: Refreshing state... [id=rtbassoc-067de8b590bf388d2]
aws_route_table_association.rta_bc[0]: Refreshing state... [id=rtbassoc-047cb69ad1d23861f]
aws_iam_instance_profile.ssm_profile: Refreshing state... [id=SSM-Instance-Profile]
aws_iam_role_policy_attachment.ssm_policy: Refreshing state... [id=SSM-Role-20240904043854484000000001]
aws_instance.servers["ab"]: Refreshing state... [id=i-08523984a6c049465]
aws_instance.servers["ac"]: Refreshing state... [id=i-0ec016c966441ba3d]
aws_instance.servers["c"]: Refreshing state... [id=i-0a0b12a99b902dfcd]
aws_instance.servers["b"]: Refreshing state... [id=i-03ccd22fa08caffd7]

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  - destroy

Terraform will perform the following actions:

  # aws_iam_instance_profile.ssm_profile will be destroyed
  - resource "aws_iam_instance_profile" "ssm_profile" {
      - arn         = "arn:aws:iam::669745465514:instance-profile/SSM-Instance-Profile" -> null
      - create_date = "2024-09-04T04:38:59Z" -> null
      - id          = "SSM-Instance-Profile" -> null
      - name        = "SSM-Instance-Profile" -> null
      - path        = "/" -> null
      - role        = "SSM-Role" -> null
      - tags        = {} -> null
      - tags_all    = {} -> null
      - unique_id   = "AIPAZX37QZCVMYL567HBJ" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_iam_role.ssm_role will be destroyed
  - resource "aws_iam_role" "ssm_role" {
      - arn                   = "arn:aws:iam::669745465514:role/SSM-Role" -> null
      - assume_role_policy    = jsonencode(
            {
              - Statement = [
                  - {
                      - Action    = "sts:AssumeRole"
                      - Effect    = "Allow"
                      - Principal = {
                          - Service = "ec2.amazonaws.com"
                        }
                    },
                ]
              - Version   = "2012-10-17"
            }
        ) -> null
      - create_date           = "2024-09-04T04:38:58Z" -> null
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
      - unique_id             = "AROAZX37QZCVADGEJYGPA" -> null
        # (3 unchanged attributes hidden)
    }

  # aws_iam_role_policy_attachment.ssm_policy will be destroyed
  - resource "aws_iam_role_policy_attachment" "ssm_policy" {
      - id         = "SSM-Role-20240904043854484000000001" -> null
      - policy_arn = "arn:aws:iam::aws:policy/AmazonSSMManagedInstanceCore" -> null
      - role       = "SSM-Role" -> null
    }

  # aws_instance.servers["ab"] will be destroyed
  - resource "aws_instance" "servers" {
      - ami                                  = "ami-009c9406091cbd65a" -> null
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:instance/i-08523984a6c049465" -> null
      - associate_public_ip_address          = true -> null
      - availability_zone                    = "ap-southeast-1b" -> null
      - cpu_core_count                       = 1 -> null
      - cpu_threads_per_core                 = 1 -> null
      - disable_api_stop                     = false -> null
      - disable_api_termination              = false -> null
      - ebs_optimized                        = false -> null
      - get_password_data                    = false -> null
      - hibernation                          = false -> null
      - iam_instance_profile                 = "SSM-Instance-Profile" -> null
      - id                                   = "i-08523984a6c049465" -> null
      - instance_initiated_shutdown_behavior = "stop" -> null
      - instance_state                       = "running" -> null
      - instance_type                        = "t2.micro" -> null
      - ipv6_address_count                   = 0 -> null
      - ipv6_addresses                       = [] -> null
      - monitoring                           = false -> null
      - placement_partition_number           = 0 -> null
      - primary_network_interface_id         = "eni-0d9697f1abfc01735" -> null
      - private_dns                          = "ip-10-1-1-15.ap-southeast-1.compute.internal" -> null
      - private_ip                           = "10.1.1.15" -> null
      - public_dns                           = "ec2-13-215-208-255.ap-southeast-1.compute.amazonaws.com" -> null
      - public_ip                            = "13.215.208.255" -> null
      - secondary_private_ips                = [] -> null
      - security_groups                      = [] -> null
      - source_dest_check                    = true -> null
      - subnet_id                            = "subnet-0bfac2eccf96780ed" -> null
      - tags                                 = {
          - "Name" = "Server-AB"
        } -> null
      - tags_all                             = {
          - "Name" = "Server-AB"
        } -> null
      - tenancy                              = "default" -> null
      - user_data_replace_on_change          = false -> null
      - vpc_security_group_ids               = [
          - "sg-0d23cf1b7294c512e",
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
          - volume_id             = "vol-031c301e5d824e258" -> null
          - volume_size           = 8 -> null
          - volume_type           = "gp3" -> null
            # (1 unchanged attribute hidden)
        }
    }

  # aws_instance.servers["ac"] will be destroyed
  - resource "aws_instance" "servers" {
      - ami                                  = "ami-009c9406091cbd65a" -> null
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:instance/i-0ec016c966441ba3d" -> null
      - associate_public_ip_address          = true -> null
      - availability_zone                    = "ap-southeast-1b" -> null
      - cpu_core_count                       = 1 -> null
      - cpu_threads_per_core                 = 1 -> null
      - disable_api_stop                     = false -> null
      - disable_api_termination              = false -> null
      - ebs_optimized                        = false -> null
      - get_password_data                    = false -> null
      - hibernation                          = false -> null
      - iam_instance_profile                 = "SSM-Instance-Profile" -> null
      - id                                   = "i-0ec016c966441ba3d" -> null
      - instance_initiated_shutdown_behavior = "stop" -> null
      - instance_state                       = "running" -> null
      - instance_type                        = "t2.micro" -> null
      - ipv6_address_count                   = 0 -> null
      - ipv6_addresses                       = [] -> null
      - monitoring                           = false -> null
      - placement_partition_number           = 0 -> null
      - primary_network_interface_id         = "eni-05b8398845d189a3d" -> null
      - private_dns                          = "ip-10-1-1-244.ap-southeast-1.compute.internal" -> null
      - private_ip                           = "10.1.1.244" -> null
      - public_dns                           = "ec2-54-169-164-2.ap-southeast-1.compute.amazonaws.com" -> null
      - public_ip                            = "54.169.164.2" -> null
      - secondary_private_ips                = [] -> null
      - security_groups                      = [] -> null
      - source_dest_check                    = true -> null
      - subnet_id                            = "subnet-0bfac2eccf96780ed" -> null
      - tags                                 = {
          - "Name" = "Server-AC"
        } -> null
      - tags_all                             = {
          - "Name" = "Server-AC"
        } -> null
      - tenancy                              = "default" -> null
      - user_data_replace_on_change          = false -> null
      - vpc_security_group_ids               = [
          - "sg-0d23cf1b7294c512e",
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
          - volume_id             = "vol-025bde7f785ead8ec" -> null
          - volume_size           = 8 -> null
          - volume_type           = "gp3" -> null
            # (1 unchanged attribute hidden)
        }
    }

  # aws_instance.servers["b"] will be destroyed
  - resource "aws_instance" "servers" {
      - ami                                  = "ami-009c9406091cbd65a" -> null
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:instance/i-03ccd22fa08caffd7" -> null
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
      - id                                   = "i-03ccd22fa08caffd7" -> null
      - instance_initiated_shutdown_behavior = "stop" -> null
      - instance_state                       = "running" -> null
      - instance_type                        = "t2.micro" -> null
      - ipv6_address_count                   = 0 -> null
      - ipv6_addresses                       = [] -> null
      - monitoring                           = false -> null
      - placement_partition_number           = 0 -> null
      - primary_network_interface_id         = "eni-0a012cde79c4539b5" -> null
      - private_dns                          = "ip-192-168-1-7.ap-southeast-1.compute.internal" -> null
      - private_ip                           = "192.168.1.7" -> null
      - secondary_private_ips                = [] -> null
      - security_groups                      = [] -> null
      - source_dest_check                    = true -> null
      - subnet_id                            = "subnet-048b1ac196e579fbc" -> null
      - tags                                 = {
          - "Name" = "Server-B"
        } -> null
      - tags_all                             = {
          - "Name" = "Server-B"
        } -> null
      - tenancy                              = "default" -> null
      - user_data_replace_on_change          = false -> null
      - vpc_security_group_ids               = [
          - "sg-0cc99e0b418b40fe5",
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
          - volume_id             = "vol-01d507b40bf63842f" -> null
          - volume_size           = 8 -> null
          - volume_type           = "gp3" -> null
            # (1 unchanged attribute hidden)
        }
    }

  # aws_instance.servers["c"] will be destroyed
  - resource "aws_instance" "servers" {
      - ami                                  = "ami-009c9406091cbd65a" -> null
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:instance/i-0a0b12a99b902dfcd" -> null
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
      - id                                   = "i-0a0b12a99b902dfcd" -> null
      - instance_initiated_shutdown_behavior = "stop" -> null
      - instance_state                       = "running" -> null
      - instance_type                        = "t2.micro" -> null
      - ipv6_address_count                   = 0 -> null
      - ipv6_addresses                       = [] -> null
      - monitoring                           = false -> null
      - placement_partition_number           = 0 -> null
      - primary_network_interface_id         = "eni-07c86da06e94ea312" -> null
      - private_dns                          = "ip-192-168-2-34.ap-southeast-1.compute.internal" -> null
      - private_ip                           = "192.168.2.34" -> null
      - secondary_private_ips                = [] -> null
      - security_groups                      = [] -> null
      - source_dest_check                    = true -> null
      - subnet_id                            = "subnet-0c60b127fa6e35de5" -> null
      - tags                                 = {
          - "Name" = "Server-C"
        } -> null
      - tags_all                             = {
          - "Name" = "Server-C"
        } -> null
      - tenancy                              = "default" -> null
      - user_data_replace_on_change          = false -> null
      - vpc_security_group_ids               = [
          - "sg-0cb51ba7dba1c93ea",
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
          - volume_id             = "vol-05cd91e6e2a2a61d3" -> null
          - volume_size           = 8 -> null
          - volume_type           = "gp3" -> null
            # (1 unchanged attribute hidden)
        }
    }

  # aws_internet_gateway.igw will be destroyed
  - resource "aws_internet_gateway" "igw" {
      - arn      = "arn:aws:ec2:ap-southeast-1:669745465514:internet-gateway/igw-0192bbe5a3160fd06" -> null
      - id       = "igw-0192bbe5a3160fd06" -> null
      - owner_id = "669745465514" -> null
      - tags     = {
          - "Name" = "Main IGW"
        } -> null
      - tags_all = {
          - "Name" = "Main IGW"
        } -> null
      - vpc_id   = "vpc-08ef5048dd424eed1" -> null
    }

  # aws_route.internet_access will be destroyed
  - resource "aws_route" "internet_access" {
      - destination_cidr_block      = "0.0.0.0/0" -> null
      - gateway_id                  = "igw-0192bbe5a3160fd06" -> null
      - id                          = "r-rtb-0516af31ad284e3e61080289494" -> null
      - origin                      = "CreateRoute" -> null
      - route_table_id              = "rtb-0516af31ad284e3e6" -> null
      - state                       = "active" -> null
        # (13 unchanged attributes hidden)
    }

  # aws_route_table.rt_a will be destroyed
  - resource "aws_route_table" "rt_a" {
      - arn              = "arn:aws:ec2:ap-southeast-1:669745465514:route-table/rtb-0516af31ad284e3e6" -> null
      - id               = "rtb-0516af31ad284e3e6" -> null
      - owner_id         = "669745465514" -> null
      - propagating_vgws = [] -> null
      - route            = [
          - {
              - cidr_block                 = "0.0.0.0/0"
              - gateway_id                 = "igw-0192bbe5a3160fd06"
                # (11 unchanged attributes hidden)
            },
          - {
              - cidr_block                 = "192.168.0.0/16"
              - vpc_peering_connection_id  = "pcx-0af3cf5276c550d93"
                # (11 unchanged attributes hidden)
            },
        ] -> null
      - tags             = {
          - "Name" = "Route Table VPC-A"
        } -> null
      - tags_all         = {
          - "Name" = "Route Table VPC-A"
        } -> null
      - vpc_id           = "vpc-08ef5048dd424eed1" -> null
    }

  # aws_route_table.rt_bc[0] will be destroyed
  - resource "aws_route_table" "rt_bc" {
      - arn              = "arn:aws:ec2:ap-southeast-1:669745465514:route-table/rtb-05963d51131240961" -> null
      - id               = "rtb-05963d51131240961" -> null
      - owner_id         = "669745465514" -> null
      - propagating_vgws = [] -> null
      - route            = [
          - {
              - cidr_block                 = "10.1.0.0/16"
              - vpc_peering_connection_id  = "pcx-0af3cf5276c550d93"
                # (11 unchanged attributes hidden)
            },
        ] -> null
      - tags             = {
          - "Name" = "Route Table VPC-B"
        } -> null
      - tags_all         = {
          - "Name" = "Route Table VPC-B"
        } -> null
      - vpc_id           = "vpc-08734d10537b6e439" -> null
    }

  # aws_route_table.rt_bc[1] will be destroyed
  - resource "aws_route_table" "rt_bc" {
      - arn              = "arn:aws:ec2:ap-southeast-1:669745465514:route-table/rtb-0378a7896d4d5cced" -> null
      - id               = "rtb-0378a7896d4d5cced" -> null
      - owner_id         = "669745465514" -> null
      - propagating_vgws = [] -> null
      - route            = [
          - {
              - cidr_block                 = "10.1.0.0/16"
              - vpc_peering_connection_id  = "pcx-0dba46795dcbc9e97"
                # (11 unchanged attributes hidden)
            },
        ] -> null
      - tags             = {
          - "Name" = "Route Table VPC-C"
        } -> null
      - tags_all         = {
          - "Name" = "Route Table VPC-C"
        } -> null
      - vpc_id           = "vpc-04dd1fc8878ebd4a0" -> null
    }

  # aws_route_table_association.rta_a will be destroyed
  - resource "aws_route_table_association" "rta_a" {
      - id             = "rtbassoc-0721a5244f7caac95" -> null
      - route_table_id = "rtb-0516af31ad284e3e6" -> null
      - subnet_id      = "subnet-0bfac2eccf96780ed" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_route_table_association.rta_bc[0] will be destroyed
  - resource "aws_route_table_association" "rta_bc" {
      - id             = "rtbassoc-047cb69ad1d23861f" -> null
      - route_table_id = "rtb-05963d51131240961" -> null
      - subnet_id      = "subnet-048b1ac196e579fbc" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_route_table_association.rta_bc[1] will be destroyed
  - resource "aws_route_table_association" "rta_bc" {
      - id             = "rtbassoc-067de8b590bf388d2" -> null
      - route_table_id = "rtb-0378a7896d4d5cced" -> null
      - subnet_id      = "subnet-0c60b127fa6e35de5" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_security_group.security_groups["a"] will be destroyed
  - resource "aws_security_group" "security_groups" {
      - arn                    = "arn:aws:ec2:ap-southeast-1:669745465514:security-group/sg-0d23cf1b7294c512e" -> null
      - description            = "Allow ICMP traffic" -> null
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
      - id                     = "sg-0d23cf1b7294c512e" -> null
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
        ] -> null
      - name                   = "Allow ICMP VPC-A" -> null
      - owner_id               = "669745465514" -> null
      - revoke_rules_on_delete = false -> null
      - tags                   = {
          - "Name" = "Allow ICMP traffic VPC-A"
        } -> null
      - tags_all               = {
          - "Name" = "Allow ICMP traffic VPC-A"
        } -> null
      - vpc_id                 = "vpc-08ef5048dd424eed1" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_security_group.security_groups["b"] will be destroyed
  - resource "aws_security_group" "security_groups" {
      - arn                    = "arn:aws:ec2:ap-southeast-1:669745465514:security-group/sg-0cc99e0b418b40fe5" -> null
      - description            = "Allow ICMP traffic" -> null
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
      - id                     = "sg-0cc99e0b418b40fe5" -> null
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
        ] -> null
      - name                   = "Allow ICMP VPC-B" -> null
      - owner_id               = "669745465514" -> null
      - revoke_rules_on_delete = false -> null
      - tags                   = {
          - "Name" = "Allow ICMP traffic VPC-B"
        } -> null
      - tags_all               = {
          - "Name" = "Allow ICMP traffic VPC-B"
        } -> null
      - vpc_id                 = "vpc-08734d10537b6e439" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_security_group.security_groups["c"] will be destroyed
  - resource "aws_security_group" "security_groups" {
      - arn                    = "arn:aws:ec2:ap-southeast-1:669745465514:security-group/sg-0cb51ba7dba1c93ea" -> null
      - description            = "Allow ICMP traffic" -> null
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
      - id                     = "sg-0cb51ba7dba1c93ea" -> null
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
        ] -> null
      - name                   = "Allow ICMP VPC-C" -> null
      - owner_id               = "669745465514" -> null
      - revoke_rules_on_delete = false -> null
      - tags                   = {
          - "Name" = "Allow ICMP traffic VPC-C"
        } -> null
      - tags_all               = {
          - "Name" = "Allow ICMP traffic VPC-C"
        } -> null
      - vpc_id                 = "vpc-04dd1fc8878ebd4a0" -> null
        # (1 unchanged attribute hidden)
    }

  # aws_subnet.subnets["a"] will be destroyed
  - resource "aws_subnet" "subnets" {
      - arn                                            = "arn:aws:ec2:ap-southeast-1:669745465514:subnet/subnet-0bfac2eccf96780ed" -> null
      - assign_ipv6_address_on_creation                = false -> null
      - availability_zone                              = "ap-southeast-1b" -> null
      - availability_zone_id                           = "apse1-az1" -> null
      - cidr_block                                     = "10.1.1.0/24" -> null
      - enable_dns64                                   = false -> null
      - enable_lni_at_device_index                     = 0 -> null
      - enable_resource_name_dns_a_record_on_launch    = false -> null
      - enable_resource_name_dns_aaaa_record_on_launch = false -> null
      - id                                             = "subnet-0bfac2eccf96780ed" -> null
      - ipv6_native                                    = false -> null
      - map_customer_owned_ip_on_launch                = false -> null
      - map_public_ip_on_launch                        = false -> null
      - owner_id                                       = "669745465514" -> null
      - private_dns_hostname_type_on_launch            = "ip-name" -> null
      - tags                                           = {
          - "Name" = "Subnet-A"
        } -> null
      - tags_all                                       = {
          - "Name" = "Subnet-A"
        } -> null
      - vpc_id                                         = "vpc-08ef5048dd424eed1" -> null
        # (4 unchanged attributes hidden)
    }

  # aws_subnet.subnets["b"] will be destroyed
  - resource "aws_subnet" "subnets" {
      - arn                                            = "arn:aws:ec2:ap-southeast-1:669745465514:subnet/subnet-048b1ac196e579fbc" -> null
      - assign_ipv6_address_on_creation                = false -> null
      - availability_zone                              = "ap-southeast-1b" -> null
      - availability_zone_id                           = "apse1-az1" -> null
      - cidr_block                                     = "192.168.1.0/24" -> null
      - enable_dns64                                   = false -> null
      - enable_lni_at_device_index                     = 0 -> null
      - enable_resource_name_dns_a_record_on_launch    = false -> null
      - enable_resource_name_dns_aaaa_record_on_launch = false -> null
      - id                                             = "subnet-048b1ac196e579fbc" -> null
      - ipv6_native                                    = false -> null
      - map_customer_owned_ip_on_launch                = false -> null
      - map_public_ip_on_launch                        = false -> null
      - owner_id                                       = "669745465514" -> null
      - private_dns_hostname_type_on_launch            = "ip-name" -> null
      - tags                                           = {
          - "Name" = "Subnet-B"
        } -> null
      - tags_all                                       = {
          - "Name" = "Subnet-B"
        } -> null
      - vpc_id                                         = "vpc-08734d10537b6e439" -> null
        # (4 unchanged attributes hidden)
    }

  # aws_subnet.subnets["c"] will be destroyed
  - resource "aws_subnet" "subnets" {
      - arn                                            = "arn:aws:ec2:ap-southeast-1:669745465514:subnet/subnet-0c60b127fa6e35de5" -> null
      - assign_ipv6_address_on_creation                = false -> null
      - availability_zone                              = "ap-southeast-1c" -> null
      - availability_zone_id                           = "apse1-az3" -> null
      - cidr_block                                     = "192.168.2.0/24" -> null
      - enable_dns64                                   = false -> null
      - enable_lni_at_device_index                     = 0 -> null
      - enable_resource_name_dns_a_record_on_launch    = false -> null
      - enable_resource_name_dns_aaaa_record_on_launch = false -> null
      - id                                             = "subnet-0c60b127fa6e35de5" -> null
      - ipv6_native                                    = false -> null
      - map_customer_owned_ip_on_launch                = false -> null
      - map_public_ip_on_launch                        = false -> null
      - owner_id                                       = "669745465514" -> null
      - private_dns_hostname_type_on_launch            = "ip-name" -> null
      - tags                                           = {
          - "Name" = "Subnet-C"
        } -> null
      - tags_all                                       = {
          - "Name" = "Subnet-C"
        } -> null
      - vpc_id                                         = "vpc-04dd1fc8878ebd4a0" -> null
        # (4 unchanged attributes hidden)
    }

  # aws_vpc.vpcs["a"] will be destroyed
  - resource "aws_vpc" "vpcs" {
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:vpc/vpc-08ef5048dd424eed1" -> null
      - assign_generated_ipv6_cidr_block     = false -> null
      - cidr_block                           = "10.1.0.0/16" -> null
      - default_network_acl_id               = "acl-0df98719eae7a545b" -> null
      - default_route_table_id               = "rtb-0586a8dd33fa804fb" -> null
      - default_security_group_id            = "sg-07abe146366afc665" -> null
      - dhcp_options_id                      = "dopt-06b97e6ae44d1358c" -> null
      - enable_dns_hostnames                 = true -> null
      - enable_dns_support                   = true -> null
      - enable_network_address_usage_metrics = false -> null
      - id                                   = "vpc-08ef5048dd424eed1" -> null
      - instance_tenancy                     = "default" -> null
      - ipv6_netmask_length                  = 0 -> null
      - main_route_table_id                  = "rtb-0586a8dd33fa804fb" -> null
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
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:vpc/vpc-08734d10537b6e439" -> null
      - assign_generated_ipv6_cidr_block     = false -> null
      - cidr_block                           = "192.168.0.0/16" -> null
      - default_network_acl_id               = "acl-0904eadfe4b0b2103" -> null
      - default_route_table_id               = "rtb-0ddee3fc3d9041697" -> null
      - default_security_group_id            = "sg-0e87345e0560ba73b" -> null
      - dhcp_options_id                      = "dopt-06b97e6ae44d1358c" -> null
      - enable_dns_hostnames                 = true -> null
      - enable_dns_support                   = true -> null
      - enable_network_address_usage_metrics = false -> null
      - id                                   = "vpc-08734d10537b6e439" -> null
      - instance_tenancy                     = "default" -> null
      - ipv6_netmask_length                  = 0 -> null
      - main_route_table_id                  = "rtb-0ddee3fc3d9041697" -> null
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
      - arn                                  = "arn:aws:ec2:ap-southeast-1:669745465514:vpc/vpc-04dd1fc8878ebd4a0" -> null
      - assign_generated_ipv6_cidr_block     = false -> null
      - cidr_block                           = "192.168.0.0/16" -> null
      - default_network_acl_id               = "acl-01e07e5ff38ac890d" -> null
      - default_route_table_id               = "rtb-0697383d6635d7509" -> null
      - default_security_group_id            = "sg-03d0084f81d1110cc" -> null
      - dhcp_options_id                      = "dopt-06b97e6ae44d1358c" -> null
      - enable_dns_hostnames                 = true -> null
      - enable_dns_support                   = true -> null
      - enable_network_address_usage_metrics = false -> null
      - id                                   = "vpc-04dd1fc8878ebd4a0" -> null
      - instance_tenancy                     = "default" -> null
      - ipv6_netmask_length                  = 0 -> null
      - main_route_table_id                  = "rtb-0697383d6635d7509" -> null
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
      - id            = "pcx-0af3cf5276c550d93" -> null
      - peer_owner_id = "669745465514" -> null
      - peer_region   = "ap-southeast-1" -> null
      - peer_vpc_id   = "vpc-08734d10537b6e439" -> null
      - tags          = {
          - "Name" = "VPC-A to VPC-B Peering "
        } -> null
      - tags_all      = {
          - "Name" = "VPC-A to VPC-B Peering "
        } -> null
      - vpc_id        = "vpc-08ef5048dd424eed1" -> null

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
      - id            = "pcx-0dba46795dcbc9e97" -> null
      - peer_owner_id = "669745465514" -> null
      - peer_region   = "ap-southeast-1" -> null
      - peer_vpc_id   = "vpc-04dd1fc8878ebd4a0" -> null
      - tags          = {
          - "Name" = "VPC-A to VPC-C Peering "
        } -> null
      - tags_all      = {
          - "Name" = "VPC-A to VPC-C Peering "
        } -> null
      - vpc_id        = "vpc-08ef5048dd424eed1" -> null

      - accepter {
          - allow_remote_vpc_dns_resolution = false -> null
        }

      - requester {
          - allow_remote_vpc_dns_resolution = false -> null
        }
    }

Plan: 0 to add, 0 to change, 26 to destroy.

Changes to Outputs:
  - test_instructions = <<-EOT
        1. SSH into Server-AB or Server-AC using their public IPs.
           Server-AB Public IP: 13.215.208.255
           Server-AC Public IP: 54.169.164.2
        
        2. From Server-AB, try to ping Server-B:
           Server-B Private IP: 192.168.1.7
        
        3. To test connectivity with Server-C:
           a. Go to the AWS VPC Console
           b. Find the route table for VPC-A
           c. Edit the route for 192.168.0.0/16
           d. Change the target to the peering connection with VPC-C
        
        4. After changing the route, from Server-AC, try to ping Server-C:
           Server-C Private IP: 192.168.2.34
        
        5. Remember to switch the route back to the peering connection with VPC-B if you want to test connectivity with Server-B again.
    EOT -> null
aws_route_table_association.rta_bc[1]: Destroying... [id=rtbassoc-067de8b590bf388d2]
aws_route_table_association.rta_bc[0]: Destroying... [id=rtbassoc-047cb69ad1d23861f]
aws_route_table_association.rta_a: Destroying... [id=rtbassoc-0721a5244f7caac95]
aws_instance.servers["c"]: Destroying... [id=i-0a0b12a99b902dfcd]
aws_instance.servers["ab"]: Destroying... [id=i-08523984a6c049465]
aws_iam_role_policy_attachment.ssm_policy: Destroying... [id=SSM-Role-20240904043854484000000001]
aws_instance.servers["ac"]: Destroying... [id=i-0ec016c966441ba3d]
aws_route.internet_access: Destroying... [id=r-rtb-0516af31ad284e3e61080289494]
aws_instance.servers["b"]: Destroying... [id=i-03ccd22fa08caffd7]
aws_route_table_association.rta_bc[0]: Destruction complete after 1s
aws_route_table_association.rta_a: Destruction complete after 1s
aws_route_table_association.rta_bc[1]: Destruction complete after 1s
aws_route_table.rt_bc[1]: Destroying... [id=rtb-0378a7896d4d5cced]
aws_route_table.rt_bc[0]: Destroying... [id=rtb-05963d51131240961]
aws_route.internet_access: Destruction complete after 1s
aws_internet_gateway.igw: Destroying... [id=igw-0192bbe5a3160fd06]
aws_route_table.rt_a: Destroying... [id=rtb-0516af31ad284e3e6]
aws_route_table.rt_bc[1]: Destruction complete after 0s
aws_route_table.rt_bc[0]: Destruction complete after 0s
aws_route_table.rt_a: Destruction complete after 0s
aws_vpc_peering_connection.peering[1]: Destroying... [id=pcx-0dba46795dcbc9e97]
aws_iam_role_policy_attachment.ssm_policy: Destruction complete after 1s
aws_vpc_peering_connection.peering[0]: Destroying... [id=pcx-0af3cf5276c550d93]
aws_vpc_peering_connection.peering[1]: Destruction complete after 1s
aws_vpc_peering_connection.peering[0]: Destruction complete after 1s
aws_instance.servers["b"]: Still destroying... [id=i-03ccd22fa08caffd7, 10s elapsed]
aws_instance.servers["c"]: Still destroying... [id=i-0a0b12a99b902dfcd, 10s elapsed]
aws_instance.servers["ac"]: Still destroying... [id=i-0ec016c966441ba3d, 10s elapsed]
aws_instance.servers["ab"]: Still destroying... [id=i-08523984a6c049465, 10s elapsed]
aws_internet_gateway.igw: Still destroying... [id=igw-0192bbe5a3160fd06, 10s elapsed]
aws_instance.servers["b"]: Still destroying... [id=i-03ccd22fa08caffd7, 20s elapsed]
aws_instance.servers["ac"]: Still destroying... [id=i-0ec016c966441ba3d, 20s elapsed]
aws_instance.servers["ab"]: Still destroying... [id=i-08523984a6c049465, 20s elapsed]
aws_instance.servers["c"]: Still destroying... [id=i-0a0b12a99b902dfcd, 20s elapsed]
aws_internet_gateway.igw: Still destroying... [id=igw-0192bbe5a3160fd06, 20s elapsed]
aws_instance.servers["c"]: Still destroying... [id=i-0a0b12a99b902dfcd, 30s elapsed]
aws_instance.servers["ac"]: Still destroying... [id=i-0ec016c966441ba3d, 30s elapsed]
aws_instance.servers["ab"]: Still destroying... [id=i-08523984a6c049465, 30s elapsed]
aws_instance.servers["b"]: Still destroying... [id=i-03ccd22fa08caffd7, 30s elapsed]
aws_internet_gateway.igw: Still destroying... [id=igw-0192bbe5a3160fd06, 30s elapsed]
aws_internet_gateway.igw: Destruction complete after 37s
aws_instance.servers["ab"]: Still destroying... [id=i-08523984a6c049465, 40s elapsed]
aws_instance.servers["c"]: Still destroying... [id=i-0a0b12a99b902dfcd, 40s elapsed]
aws_instance.servers["b"]: Still destroying... [id=i-03ccd22fa08caffd7, 40s elapsed]
aws_instance.servers["ac"]: Still destroying... [id=i-0ec016c966441ba3d, 40s elapsed]
aws_instance.servers["ac"]: Destruction complete after 41s
aws_instance.servers["ab"]: Destruction complete after 41s
aws_instance.servers["b"]: Destruction complete after 41s
aws_instance.servers["c"]: Still destroying... [id=i-0a0b12a99b902dfcd, 50s elapsed]
aws_instance.servers["c"]: Still destroying... [id=i-0a0b12a99b902dfcd, 1m0s elapsed]
aws_instance.servers["c"]: Destruction complete after 1m1s
aws_iam_instance_profile.ssm_profile: Destroying... [id=SSM-Instance-Profile]
aws_security_group.security_groups["a"]: Destroying... [id=sg-0d23cf1b7294c512e]
aws_subnet.subnets["b"]: Destroying... [id=subnet-048b1ac196e579fbc]
aws_subnet.subnets["a"]: Destroying... [id=subnet-0bfac2eccf96780ed]
aws_security_group.security_groups["b"]: Destroying... [id=sg-0cc99e0b418b40fe5]
aws_security_group.security_groups["c"]: Destroying... [id=sg-0cb51ba7dba1c93ea]
aws_subnet.subnets["c"]: Destroying... [id=subnet-0c60b127fa6e35de5]
aws_subnet.subnets["a"]: Destruction complete after 1s
aws_subnet.subnets["c"]: Destruction complete after 1s
aws_subnet.subnets["b"]: Destruction complete after 1s
aws_security_group.security_groups["a"]: Destruction complete after 1s
aws_security_group.security_groups["b"]: Destruction complete after 1s
aws_security_group.security_groups["c"]: Destruction complete after 1s
aws_vpc.vpcs["b"]: Destroying... [id=vpc-08734d10537b6e439]
aws_vpc.vpcs["c"]: Destroying... [id=vpc-04dd1fc8878ebd4a0]
aws_vpc.vpcs["a"]: Destroying... [id=vpc-08ef5048dd424eed1]
aws_vpc.vpcs["a"]: Destruction complete after 0s
aws_vpc.vpcs["c"]: Destruction complete after 0s
aws_vpc.vpcs["b"]: Destruction complete after 0s
aws_iam_instance_profile.ssm_profile: Destruction complete after 2s
aws_iam_role.ssm_role: Destroying... [id=SSM-Role]
aws_iam_role.ssm_role: Destruction complete after 1s

Destroy complete! Resources: 26 destroyed.
vagrant@cloud-native-box:~/hands-on-terraform/aws-vpc-peering-with-terraform/case01$ 
```
