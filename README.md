# CloudFormation Big-IP LAMPv7








The default values in this CloudFormation template were designed to work in AWS Region Singapore (ap-southeast-1).
The reason of that is because the adapted LAMPv7 VM is only imported to AWS Region Singapore, so the adapted LAMPv7 AMI exists only in AWS Region Singapore.
To make this template works in any other AWS Regions, the adapted LAMPv7 AMI must exist in the targeted region and be accessible by the targeted account, before the execution of this template.
Which can be achieved by re-importing the adapted LAMPv7 VM, or by copying the adapted LAMPv7 AMI in Singapore to the targeted AWS Region.
Once the adapted LAMPv7 AMI exist in the targeted AWS Region, the AMI ID of the adapted LAMPv7 need to be indicated properly (i.e. not using the default value) during execution of this template.

The Big-IP AMI should be available in most (if not ALL) of AWS Regions as part of F5 Networks effort to sell usage of their product in AWS.
Only the correct AMI ID of Big-IP within the targeted AWS Region is needed, which should not be difficult to find.
Just a note that this CloudFormation template were tested with Big-IP version 15.0.1 build 0.0.11.
You will also need a valid F5 Big-IP License to execute this template.

This template creates:
1. One F5's LAMPv7 instance which had been adapted to AWS environment in certain extend.
2. One F5's Big-IP instance, license the instance, configure the networking part, and potentially also configure the services with the AS3 Declaration URL.

The whole template require around 30 minutes to fully completed. Although the CloudFormation stack itself stated it has completed, the instances themselves need much more time to self-configure.

The diagram below depicts the Logical Network Diagram built by this CloudFormation template.
![Logical Network Diagram](Figures/LogicalNetworkDiagram.png)

This CloudFormation template is design for building Demo/Testing environment only. It was NOT designed to be used for Live/Commercial environment!

The output part of the CloudFormation template is only 100% valid in the case of AS3 Declaration URL is using the default value.
Otherwise they're only partially valid (i.e. only management IPs/URLs are valid, while services' like Static Web Server, DVWA and Hackazon IPs/URLs are entirely dependent on AS3 Declaration URL).
Refer to ![AS3](AS3-Simple-LTM/) as one example of AS3 Declaration.


