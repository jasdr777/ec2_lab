# AWS CloudFormation

CloudFormation scripts here are designed to build a traditional EC2 VPN infrastructure.

Ideally, each of the JSON CloudFormation files are to be ran in sequence (ascending order).  Then when we destroy the infrastrucrure they should be ran backwards (descending order).

1 [Create VPN](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpc.html)

2 Create Linux Server