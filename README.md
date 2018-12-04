# vpc
Templates for VPC management

# 3tier_parameters

"This template defines the network parameters for a new 3 tier VPC with 2 public, private, and database private subnets"

Parameters:
"AvailabilityZones" -  List of Availability Zones to use for the subnets in the VPC (Region agnostic);
"PrivateSubnet1CIDR" - CIDR block for private subnet 1 located in Availability Zone 1;
"PrivateSubnet2CIDR" - CIDR block for private subnet 2 located in Availability Zone 2;
"PublicSubnet1CIDR" -  CIDR block for public subnet 1 located in Availability Zone 1;
"PublicSubnet2CIDR" -  CIDR block for private subnet 2 located in Availability Zone 2;
"DBSubnet1CIDR" -      CIDR block for database subnet 1 located in Availability Zone 1;
"DBSubnet1CIDR" -      CIDR block for database subnet 2 located in Availability Zone 2;
"VPCCIDR" -            CIDR Block for the VPC

Resources:
VPC;
2 Private Subnets;
2 Public Subnets;
2 Database Subnets;
1 RDS Subnet Group;
1 Public Route Table associated with both Public Subnets;
1 Internet Gateway attached to the VPC created and associated with the Public Route Table;

NACLs:
IMPORTANT - NO NACLs ALLOW EPHEMERAL PORTS; 
Database Subnets - Allowed Inbound and Outbound on port 3306 with both Private Subnets;
Private Subnets -  Allowed Inbound and Outbound on port 3306 with both Database Subnets; 
                   Allowed Inbound and Outbound on ports 80,443,22,389 with both Public Subnets;
Public Subnets -   Allowed Inbound and Outbound on ports 80, 443 with both 0.0.0.0/0;
                   Allowed Inbound and Outbound on ports 80,443,22,389 with both Private Subnets;
