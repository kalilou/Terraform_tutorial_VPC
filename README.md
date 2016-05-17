### Create a basic VPC with terraform from HashiCorp
 

This example depicts a creation of a basic AWS VPC
Resources created:
* VPC 
* Subnets (one public and two privates)
* Routes 
* Route tables 
* Elastic IP (EIP)
* NAT Gateway 
* Route table association


#### Basic VPC 
AWS VPC stands for Virtual Private Cloud which basically provides a way to structure your own network the way you want in AWS. 
Before we dive in let's define some basic VPC concepts:

* CIDR - Classless Intern-Domain Routing 
Let's choose the address ranges which will be `172.31.0.0/16` in binary number give us `1010 1100.1111 0000.0000 0000.0000 0000` 
the slash 16 (/16) indicates that the first 16 bits will be fixed and represents the network and the rest 16 bits will represents the hosts. 
You can also choose any CIDR for your VPC which can be for example 10.0.0.0/16.
So with the /16 you will have 64 000 addresses. Nice 

So the terraform syntax for creating the VPC will look like the following:
```
resource "aws_vpc" "vpc_tuto" {
  cidr_block = "172.31.0.0/16"
  enable_dns_support = true
  enable_dns_hostnames = true
  tags = {
    Name = "TestVPC"
  }
}
```

* `resource` is a terraform notation. 
* `aws_vpc` resource name representing the AWS VPC resource. 
* `vpc_tuto` is a name given to the resource VPC which can be used later on the get thing like vpc_id or main_route_table_id
* `cidr_block` is the address ranges given for your VPC 
* `enable_dns_support` enable or disable DNS support in the VPC. (Default to true if not specified)
* `enable_dns_hostnames` enable or disable DNS hostnames in the VPC. (Default to false if not specified)
* `tags` used to tag your VPC with a name

#### Subnets 
In this tutorial we have setup three subnets, one public and two private subnets, what this means is that the public 
subnet can be accessible from the internet and the private subnets cannot be accessible from the internet, and this involves 
setting up and configuring the nat gateway, the internet gateway, the routes and the route tables. You can also apply some security groups (SG) and/or ACL to your VPC which 
are not covered in this tutorial. 

So the terraform syntax for creating the subnets will look like the following:
```
resource "aws_subnet" "subnet_eu_west_1a" {
  vpc_id                  = "${aws_vpc.vpc_tuto.id}"
  cidr_block              = "172.31.1.0/24"
  map_public_ip_on_launch = true
  availability_zone = "eu-west-1a"
  tags = {
  	Name =  "Subnet az 1a"
  }
}

```

* `resource` is a terraform notation. 
* `aws_subnet` resource name representing the AWS Subnet resource. 
* `subnet_eu_west_1a` is a name given to the resource subnet which can be used later on the get thing like subnet_id 
* `cidr_block` is the address ranges given for your subnet `172.31.1.0/24`  the first 24 bits will be fixed which result into having 251 IP addresses
* `map_public_ip_on_launch` enables public IP mapping which means any ec2 instance created in this subnet will have a public IP, for private subnet this field will be omitted 
* `availability_zone` Specify in which availability zone the subnet will be created
* `tags` used to tag your subnet with a name

#### Internet Gateway 
`coming soon` 

#### Nat Gateway 
`coming soon` 

#### Route 
`coming soon` 

#### Route Table 
`coming soon`

#### Elastic IP (EIP)
`coming soon` 

#### Route Table Assciation 
`coming soon `



