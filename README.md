## 📘 What Is VPC Peering?
A VPC peering connection allows two VPCs to communicate as if they are part of the same private network, using only private IP addresses. The data remains on the AWS global network, never traverses the public internet, and doesn’t rely on Internet Gateways, VPNs, or separate hardware 

Peering supports intra-account, inter-account, and inter-region setups, as long as the CIDR blocks don’t overlap 


## ✅ Benefits of VPC Peering

No single point of failure or bottleneck; peering leverages native infrastructure 

Minimal cost: Free for AZ-local traffic; cross-AZ/region data transfers incur minimal fees 
DEV Community

## 🛠️ How to Set It Up (Same Account, Same Region)
## 1. Create VPCs
Use the console or CLI to create your two VPCs (e.g., AjaVPC and IbmVPC) with separate non-overlapping CIDRs, such as 10.0.0.0/16 and 192.168.0.0/16 

## 2. Establish Peering Connection:

Navigate to VPC → Peering Connections → Create Peering Connection, choose the Requester (AjaVPC) and Accepter (IbmVPC), then click Create. The request status will be Pending 
Amazon Web Services, Inc.

## 3. Accept the Request:

Go to the Peering Connections list, select the request, then choose Actions → Accept Request 

## 4. Update Route Tables:

In each VPC’s route table, add a route for the other VPC’s CIDR via the peering connection (e.g., 192.168.0.0/16 → pcx-xxxx and vice versa) 
DEV Community
.

## 5. Adjust Security Groups:

Ensure both EC2 instances’ Security Groups allow Inbound ICMP (ping) and SSH from the peer VPC’s CIDR block 
Medium.

## 6. Test Connectivity:

## SSH into EC2-A and run:

```
ping 192.168.1.100  # EC2-B's private IP
```
## Screenshots:

You should receive ping replies if everything’s configured properly
