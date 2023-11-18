---
tag: aws
---
**VPC in a region**

![Untitled](Services%20diagram%20image.png)

- The VPC has one subnet in each of the Availability Zones in the Region
- EC2 instances in each subnet
- An internet gateway to allow communication between the resources in your VPC and the internet.

**VPC resources map**

![VPC diagram](VCP%20diagram%20image.png)

## Virtual networking environments

- IP address range
- Subnet
- Route tables
- Network gateways

## VPC use multiple layers of security:

- Security groups
- NACL - Network Access Control Lists: Help control access to EC2 instances in each subnet

## Features

- **Subnet**
    - A [subnet](https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html) is a range of IP addresses in your VPC. A subnet must reside in a single Availability Zone. After you add subnets, you can deploy AWS resources in your VPC.
- **IP Addressing**
- **Routing**
    - Use [route tables](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html) to determine where network traffic from your subnet or gateway is directed.
    
    A *route table* contains a set of rules, called routes, that are used to determine where network traffic from your VPC is directed. You can explicitly associate a subnet with a particular route table. Otherwise, the subnet is implicitly associated with the main route table.
    
    Each route in a route table specifies the range of IP addresses where you want the traffic to go (the destination) and the gateway, network interface, or connection through which to send the traffic (the target).
    
- **NAT**
    
    Allow instances in private subnet connect to internet throw NAT.
    
    NAT map multiple private IP address to **a single** publish IP address (can assign elastic IP to it) then connect it to the internet **through an internet gateway**
    
    - Alternatively, to allow an instance in your VPC to initiate outbound connections to the internet but prevent unsolicited inbound connections from the internet, you can use a network address translation (NAT) device. NAT maps multiple private IPv4 addresses to a single public IPv4 address. You can configure the NAT device with an Elastic IP address and connect it to the internet through an internet gateway. This makes it possible for an instance in a private subnet to connect to the internet through the NAT device, routing traffic from the instance to the internet gateway and any responses to the instance.
- **Gateways and endpoints**
    
    A [gateway](https://docs.aws.amazon.com/vpc/latest/userguide/extend-intro.html) connects your VPC to another network. For example, use an [internet gateway](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html) to connect your VPC to the internet. Use a [VPC endpoint](https://docs.aws.amazon.com/vpc/latest/privatelink/privatelink-access-aws-services.html) to connect to AWS services privately, without the use of an internet gateway or NAT device.
    
- **Flow Logs**
    - S3
    - CloudWatch
- **IP Address Manager (IPAM)**
- **Ingress Routing**
    - With this feature, you can route all incoming and outgoing traffic flowing to/from an [internet gateway](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html) or [virtual private gateway](https://docs.aws.amazon.com/vpn/latest/s2svpn/your-cgw.html) to a specific [Amazon EC2](https://aws.amazon.com/ec2/) instance’s [elastic network interface.](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html) Configure your [virtual private cloud](https://aws.amazon.com/vpc/) to send all traffic to a gateway or an [Amazon EC2](https://aws.amazon.com/ec2/) instance before it reaches your business workloads. Learn more about this feature [here.](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html#gateway-route-table)
- **Network Access Analyzer**
- **Network Access Control List**
    - A network access control list (network ACL) is an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets. You might set up network ACLs with rules similar to those of your security groups. Read about the differences between security groups and network ACLs [here](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html#VPC_Security_Comparison).
- **Network Manager**
- ****Reachability Analyzer****
- ****Security Groups****
    - Create security groups to act as a firewall for associated Amazon EC2 instances, controlling inbound and outbound traffic at the instance level. When you launch an instance, you can associate it with one or more security groups. If you don’t specify a group, the instance is automatically associated with the VPC’s default group. Each instance in your VPC can belong to a different set of groups. Learn more about security groups [here](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html).
- ****Traffic Mirroring****