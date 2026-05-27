#network #aws #vpc #peering #transit_gateway 

1. Use traceroute dns to find which hops are dead.
2. Network Analyzer, check the AWS setup logic only to detect the blocker hop.
3. AWS Flow logs
4. nc -vz to check if the port is opened, blocked
5. nslookup to check the DNS resolver

### VPC peering
1. Create a VPC peering request to another VPC X on another account. Do not need RAM
2. Accept request
3. Update the destination CIDR on the current account routable to point to the VPC X.

### Route tables
1. CIDR, IP, IP Prefix
2. Destination: NAT, igx, vpc-id, transit-gw-attachment-id

### Transit gateway
1. Central account to create a HUB, transit gateway, have the id. Use RAM to share this resources to account A & B
2. Account A: VPC A, create transit gw attachment request for VPC A to the central transit gateway
3. Account B: VPC B, create transit gw attachment request for VPC B to the central transit gateway
4. Central account: Approve requests, and propagate the CIRD of VPC A (subnets), and CIRD of the VPC B.
5. To access VPC B from account A. Update the account A route table to have 
   VPC B CIRD - Destination: transit gateway id
6. To response from account B. Update the account B route table to have 
   VPC A CIRD - Destination: transit gateway id
7. Security group/ NACL / VPC Lattice for the one way communication