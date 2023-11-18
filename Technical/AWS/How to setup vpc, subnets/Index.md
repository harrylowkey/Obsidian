---
tag: aws
---
![Untitled](Example%20diagram.png)

Region: us-west-1

VPC Range 172.20.0.0/16

4 subnets: 2 pub sub, 2 priv sub

2 zones: us-west-1a, us-west-1b

172.20.1.0/24    => pub-sub1 [us-west-1a]

172.20.2.0/24    => pub-sub-2 [us-west-1b]

172.20.3.0/24    => priv-sub-1 [us-west-1a]

172.20.4.0/24    => priv-sub-2 [us-west-1b]

1 Internet GW

2 NAT Gateway

1 EIP

2 Route Tables : 1 Pub Sub RT, 1 Pub Sub RT

1 Bastion host in Pub subnet

NACL

1 more VPC => VPC Peering

https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html

https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/enable-access-logs.html

[https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/QuickStartEC2Instance.html](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/QuickStartEC2Instance.html)

[Build specification reference for CodeBuild - AWS CodeBuild (amazon.com)](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html)