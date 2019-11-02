# AWS CloudFormation

`aws cloudformation create-stack`

`  --stack-name wjnet-va-prod-vpc`

`  --template-body file://templates/company-prod-01-vpc.yaml`

`  --parameters ParameterKey=AdminIp,ParameterValue=AdminIp`



# Bastion

ssh -i "devTeam.pem" ec2-user@ec2-18-206-152-248.compute-1.amazonaws.com

Test Results
- BastionSG worked.


# Notes

CloudFormation scripts here are designed to build a traditional EC2 VPN infrastructure.

Ideally, each of the JSON CloudFormation files are to be ran in sequence (ascending order).  Then when we destroy the infrastrucrure they should be ran backwards (descending order).

## CloufFormation JSON Notes

[JSON Find in Map](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-findinmap.html)

[VPC](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpc.html)


Public Subnet connected to a Public Router Table, connected to the VPN.

## CF File Strategy

1-vpn.json - This contains only what is needed to create a clean VPN.
2-vpn-public-subnet - This contains only what is needed to create a public subnet with firewall ACL
3-vpn-private-subnet - Same as 2, but private with NAT to Internet Gateway
4-vpn-linux-bastion - This is the Linux jumpbox, lives on Public subnet.