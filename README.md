# CloudFormation Big-IP LAMPv7








This CloudFormation template only works in AWS Region Singapore (ap-southeast-1).
The reason of that is because the adapted LAMPv7 VM is only imported to AWS Region Singapore, so the adapted LAMPv7 AMI exists only in AWS Region Singapore.
To make this template works in any other AWS Regions, the adapted LAMPv7 AMI must exist in the targeted region and be accessible by the targeted account, before the execution of this template.
Which can be achieved by re-importing the adapted LAMPv7 VM, or by copying the adapted LAMPv7 AMI in Singapore to the targeted AWS Region.

The Big-IP AMI should be available in most (if not ALL) of AWS Regions (as part of F5 Networks effort to sell usage of their product in AWS).
Only the correct AMI ID of Big-IP within the targeted AWS Region is needed, which should not be difficult to find.
Just a note that this CloudFormation template were tested with Big-IP version 15.0.1 build 0.0.11.
You will also need a valid F5 Big-IP License to execute this template.

This template creates:
1. One F5's LAMPv7 instance which had been adapted to AWS environment in certain extend.
2. One F5's Big-IP instance












