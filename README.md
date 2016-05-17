### Basic AWS VPC with one public subnet and two private subnets


This example depicts a creation of a basic AWS VPC
Resources created:
* VPC 
* Subnets
* Routes 
* Route tables 
* Elastic IP (EIP)
* NAT Gateway 
* Route table association


#### Basic VPC 
AWS VPC stands for Virtual Private Cloud which basically provides a way to structure your own network the way you want in AWS. 
Before we dive in let's define some basic VPC basic concepts:

* CIDR - Classless Intern-Domain Routing 
Let's choose the address ranges which will be `172.31.0.0/16` in binary number give us `1010 1100.1111 0000.0000 0000.0000 0000` 
the slash 16 (/16) indicates that the first 16 bits will be fixed and represents the network and the rest 16 bits will represents the hosts. 
You can also choose any CIDR for your VPC which can be for example 10.0.0.0/16
So with the /16 will have 64 000 addresses. Nice 

So the terraform syntax for creation the VPC will look like the following:
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


[provisioners](https://www.terraform.io/docs/provisioners/) 
[Packer](http://www.packer.io).

