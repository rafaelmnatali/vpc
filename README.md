# vpc
Templates for VPC management

# 3tier_parameters

"This template defines the network parameters for a new 3 tier VPC with 2 public, private, and database private subnets"

It requests input for: Availability Zone and the CIDRs that are going to be used.
NACLs and Security Groups don't allow ephemeral ports. 
Ports allowed: 80, 443 (Public); 22,389,80,443 (Private), 3306 (Database)


