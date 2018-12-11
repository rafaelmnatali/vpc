### vpc
Templates for VPC management

### 3tier_parameters

"This template defines the network parameters for a new 3 tier VPC with 2 public, private, and database private subnets"

Template requests input for: Availability Zone, CIDRs, and Database Port Number.

NACLs allow ephemeral ports. 
Ports allowed: 80, 443 (Public); 22,389,80,443 (Private), (Database as inputed in the parameter)


