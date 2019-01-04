### vpc
Templates for VPC management

### 3tier_parameters

This template creates the network segmentation of Public, Private, and Database subnet in two Availability Zones in a new VPC along with the Network Access Lists (NACLs) and Security Groups for the resources that will be provisioned in each subnet. This is a standard configuration that could be changed accordingly to applications’ requirements, but always keeping the ‘least privilege access’ premisse. 

Firstly, the template requests the input of the information required for the network creation. Here is a brief explanation of each one:

Availability Zones: From the drop-down list selects 2 AZs where the network will be configured
VPCCIDR: IP address block for the entire VPC; default: 10.0.0.0/16
DBPortNumber: Number of the port to connect to the database 
xSubnetxCIDR:  IP address block for each subnet; it must not overlap each other

Secondly, the template configures the NACLs for each subnet. NACLs can spread across AZs therefore, the subnets share the same NACL. 
This is the first line of defense against unwanted connections to provisioned resources.

For the Public Subnet it only allows connection on ports 80, 443, and ephemeral ports. 
In the Private Subnet it accepts traffic from the Public Subnet for ports 80, 443, 22, and 389 (these last two are configured now already considering a Bastion Host or a VPN connection in the future). 
It also allow communication with the Database Subnet (port 3306 in this example). At last, the Database Subnet only communicates with the Private Subnet.

In addition to the NACLs, the template also creates an Internet Gateway and associate it with the Route Table in the Public Subnet allowing traffic from and to the Internet 
for the subnet. As to the Private Subnets the Route Table only allow local traffic.

Finally, the template creates Security Groups for public resources, Linux and Windows private servers, and for the database. 
The objective is to allow access to the resources in the same ports that are configured in the NACLs.


