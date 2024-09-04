# Exploring AWS VPC Peering with Terraform
![](./images/Exploring%20AWS%20VPC%20Peering%20with%20Terraform.png)

# Understanding Test Cases with Terraform

In this blog post, we'll walk through two test cases using Terraform to set up servers in a Virtual Private Cloud (VPC). We'll keep it simple and easy to follow!

## Test Case 1: Servers in the Same Subnet

In this scenario, we will place **Server-AB** and **Server-AC** in the same subnet within **VPC-A**.

### Steps to Set Up

1. **Go to the Directory**: Open your terminal and navigate to the `testcase1` directory.
2. **Initialize Terraform**: Run the command:
   ```bash
   terraform init
   ```
   This prepares Terraform to manage your infrastructure.
3. **Create the Infrastructure**: Run the command:
   ```bash
   terraform apply
   ```
   This command will create the servers and other resources defined in your Terraform configuration.

### Testing

After running the above commands, follow the instructions shown in the output. This will guide you on how to test the connectivity between the servers.

### Test Case 01 output
[Case01 Scenario Output](./case01/case01.md)

## Test Case 2: Servers in Different Subnets

In this scenario, **Server-AB** and **Server-AC** will be placed in different subnets within **VPC-A**.

### Steps to Set Up

1. **Go to the Directory**: Open your terminal and navigate to the `testcase2` directory.
2. **Initialize Terraform**: Run the command:
   ```bash
   terraform init
   ```
3. **Create the Infrastructure**: Run the command:
   ```bash
   terraform apply
   ```

### Testing

Again, follow the instructions provided in the output after applying the configuration to test the connectivity.

## Important Notes

- **Manual Route Changes**: For both test cases, you will need to manually change the route in VPC-A's route table when testing connectivity with **Server-C**.
- **Clean Up**: After finishing your tests, run the following command in each test case directory to avoid extra charges:
  ```bash
  terraform destroy
  ```

### Case 02 Scenario Output
[Case-02 Scenario Output](./case02/case02.md)
## Key Takeaways

Here are some important lessons learned from these test cases:

### 1. CIDR Block Conflict
- **Problem**: We initially set VPC-B and VPC-C with the same CIDR block (192.168.0.0/16), causing routing issues.
- **Solution**: We had to manually switch routes in VPC-A to test connectivity properly.

### 2. SSM Agent Issues
- **Problem**: The SSM agent (used for managing servers) wasn't connecting.
- **Solution**: We ensured that the servers had internet access or proper VPC endpoints set up.

### 3. Public IP Assignment
- We needed to assign public IPs only to **Server-AB** and **Server-AC**. This was done using the `associate_public_ip_address` setting in Terraform.

### 4. Managing Resources
- We faced challenges with resource dependencies in Terraform. We learned to use features like `count` and `for_each` to manage multiple similar resources more easily.

### 5. Manual Testing Steps
- Due to CIDR block conflicts, we had to adjust routes manually in the AWS console for testing, showing some limitations of using infrastructure-as-code.

By following these test cases, you can gain hands-on experience with Terraform and learn how to set up and troubleshoot server connectivity in a VPC. Happy testing!