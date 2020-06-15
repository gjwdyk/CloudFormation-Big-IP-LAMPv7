# CloudFormation Big-IP LAMPv7








This repositry reflects a journey in learning (AWS' CF & F5's AS3) and re-making of F5 Demo environment (vLab section under https://downloads.f5.com/).

The default values in this CloudFormation template were designed to work in AWS Region Singapore (ap-southeast-1).
The reason of that is because the adapted LAMPv7 VM is only imported to AWS Region Singapore, so the adapted LAMPv7 AMI exists only in AWS Region Singapore.
To make this template works in any other AWS Regions, the adapted LAMPv7 AMI must exist in the targeted region and be accessible by the targeted account, before the execution of this template.
Which can be achieved by re-importing the adapted LAMPv7 VM, or by copying the adapted LAMPv7 AMI in Singapore to the targeted AWS Region.
Once the adapted LAMPv7 AMI exist in the targeted AWS Region, the AMI ID of the adapted LAMPv7 need to be indicated properly (i.e. not using the default value) during execution of this template.

The Big-IP AMI should be available in most (if not ALL) of AWS Regions as part of F5 Networks effort to sell usage of the product in AWS.
Only the correct AMI ID of Big-IP within the targeted AWS Region is needed, which should not be difficult to find.
Just a note that this CloudFormation template were tested with Big-IP version 15.0.1 build 0.0.11.
You will also need a valid F5 Big-IP License to execute this template.

This CloudFormation template is designed for building Demo/Testing environment only. It was NOT designed to be used for Live/Commercial environment!

The whole template require around 30 minutes to fully completed. Although the CloudFormation stack itself stated it has completed, the instances themselves need much more time to self-configure.

The diagram below depicts the Logical Network Diagram built by the following CloudFormation templates.
![Logical Network Diagram](Figures/LogicalNetworkDiagram.png)

The output part of the CloudFormation template is only 100% valid in the case of AS3 Declaration URL is using the default value.
Otherwise they're only partially valid (i.e. only management IPs/URLs are valid, while services' like Static Web Server, DVWA and Hackazon IPs/URLs are entirely dependent on AS3 Declaration being used).

Refer to [AS3-LTM-Simple](AS3-LTM-Simple/) as one example of AS3 Declaration.



***

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CloudFormation_Big-IP_LAMPv7_Original.json"><img align="right" src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/LaunchStackJigokuShoujo.png" width="140" height="22"/></a>

The [CloudFormation_Big-IP_LAMPv7.json](CloudFormation_Big-IP_LAMPv7.json) template creates:
1. One F5's LAMPv7 instance which had been adapted to AWS environment in certain extend.
2. One F5's Big-IP instance, license the instance, configure the networking part, and potentially also configure the services with the AS3 Declaration URL.

Default AS3 Declaration for [CloudFormation_Big-IP_LAMPv7.json](CloudFormation_Big-IP_LAMPv7.json) is [AS3-LTM-Simple](AS3-LTM-Simple/), but can be changed during the CloudFormation template deployment,
provided the replacement AS3 Declaration fits into the Big-IP environment provided by the [CloudFormation_Big-IP_LAMPv7.json](CloudFormation_Big-IP_LAMPv7.json) template.

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CloudFormation_Big-IP_LAMPv7.json"><img src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/JigokuShoujoLaunchStack.png" width="140" height="22"/></a>



***

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CloudFormation_Big-IP_LAMPv7_SSLOffLoad_Original.json"><img align="right" src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/LaunchStackJigokuShoujo.png" width="140" height="22"/></a>

The [CloudFormation_Big-IP_LAMPv7_SSLOffLoad.json](CloudFormation_Big-IP_LAMPv7_SSLOffLoad.json) template creates:
1. One F5's LAMPv7 instance which had been adapted to AWS environment in certain extend.
2. One F5's Big-IP instance, license the instance, configure the networking part, and potentially also configure the services with the AS3 Declaration URL.
3. Import the TLS Private Key and Certificate into the Big-IP, so the corresponding AS3 Declaration can use them to create SSL Profiles.

Default AS3 Declaration for [CloudFormation_Big-IP_LAMPv7_SSLOffLoad.json](CloudFormation_Big-IP_LAMPv7_SSLOffLoad.json) is [AS3-LTM-SSLOffLoad](AS3-LTM-SSLOffLoad/), but can be changed during the CloudFormation template deployment,
provided the replacement AS3 Declaration fits into the Big-IP environment provided by the [CloudFormation_Big-IP_LAMPv7_SSLOffLoad.json](CloudFormation_Big-IP_LAMPv7_SSLOffLoad.json) template.

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CloudFormation_Big-IP_LAMPv7_SSLOffLoad.json"><img src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/JigokuShoujoLaunchStack.png" width="140" height="22"/></a>



***

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_Big-IP_LAMP_SSLOffLoad_MailNotification_Original.json"><img align="right" src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/LaunchStackJigokuShoujo.png" width="140" height="22"/></a>

The [CF_Big-IP_LAMP_SSLOffLoad_MailNotification.json](CF_Big-IP_LAMP_SSLOffLoad_MailNotification.json) template creates:
1. One F5's LAMPv7 instance which had been adapted to AWS environment in certain extend.
2. One F5's Big-IP instance, license the instance, configure the networking part, and potentially also configure the services with the AS3 Declaration URL.
3. Import the TLS Private Key and Certificate into the Big-IP, so the corresponding AS3 Declaration can use them to create SSL Profiles.
4. Configure SSMTP and user_alert.conf to send email notification in case of an event. The example works with GMail's SMTP, and sending notification when a pool has no available member, and when the pool back to having a member available to handle the traffic.

Default AS3 Declaration for [CF_Big-IP_LAMP_SSLOffLoad_MailNotification.json](CF_Big-IP_LAMP_SSLOffLoad_MailNotification.json) is [AS3-LTM-SSLOffLoad](AS3-LTM-SSLOffLoad/), but can be changed during the CloudFormation template deployment,
provided the replacement AS3 Declaration fits into the Big-IP environment provided by the [CloudFormation_Big-IP_LAMPv7_SSLOffLoad.json](CloudFormation_Big-IP_LAMPv7_SSLOffLoad.json) template.

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_Big-IP_LAMP_SSLOffLoad_MailNotification.json"><img src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/JigokuShoujoLaunchStack.png" width="140" height="22"/></a>



***

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_BigIP_LAMP_SSLOffL_MailNotification_Lidsa_Original.json"><img align="right" src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/LaunchStackJigokuShoujo.png" width="140" height="22"/></a>

The [CF_BigIP_LAMP_SSLOffL_MailNotification_Lidsa.json](CF_BigIP_LAMP_SSLOffL_MailNotification_Lidsa.json) template creates:
1. One F5's LAMPv7 instance which had been adapted to AWS environment in certain extend.
2. One F5's Big-IP instance, license the instance, configure the networking part, and potentially also configure the services with the AS3 Declaration URL.
3. Import the TLS Private Key and Certificate into the Big-IP, so the corresponding AS3 Declaration can use them to create SSL Profiles.
4. Configure SSMTP and user_alert.conf to send email notification in case of an event. The example works with GMail's SMTP, and sending notification when a pool has no available member, and when the pool back to having a member available to handle the traffic.
5. Additional Lorem Ipsum Dolor Sit Amet mock-up field.

Default AS3 Declaration for [CF_BigIP_LAMP_SSLOffL_MailNotification_Lidsa.json](CF_BigIP_LAMP_SSLOffL_MailNotification_Lidsa.json) is [AS3-LTM-SSLOffLoad](AS3-LTM-SSLOffLoad/), but can be changed during the CloudFormation template deployment,
provided the replacement AS3 Declaration fits into the Big-IP environment provided by the [CF_BigIP_LAMP_SSLOffL_MailNotification_Lidsa.json](CF_BigIP_LAMP_SSLOffL_MailNotification_Lidsa.json) template.

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_BigIP_LAMP_SSLOffL_MailNotification_Lidsa.json"><img src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/JigokuShoujoLaunchStack.png" width="140" height="22"/></a>



***



# CloudFormation Big-IP LAMPv7 Windows-Server-2008-R2









Below onward Windows Server 2008 is added into the CF template, as well as a few changes done to the LAMPv7 image (which may affect the previous/above CF templates).

The same as previous, the Windows Server VM is only imported to AWS Region Singapore (ap-southeast-1), therefore the CF template works only in AWS Region Singapore (ap-southeast-1).
To make this template works in any other AWS Regions, the adapted LAMPv7 AMI and the adapted Windows Server AMI must exist in the targeted region and be accessible by the targeted account, before the execution of this template.
Which can be achieved by re-importing the adapted LAMPv7 VM and the adapted Windows Server VM, or by copying the adapted LAMPv7 AMI and the adapted Windows Server AMI in Singapore to the targeted AWS Region.

Once the adapted LAMPv7 AMI and the adapted Windows Server AMI exist in the targeted AWS Region, the AMI ID of the adapted LAMPv7 and the adapted Windows Server need to be indicated properly (i.e. not using the default value) during execution of this template.

The Big-IP AMI should be available in most (if not ALL) of AWS Regions as part of F5 Networks effort to sell usage of the product in AWS.
Only the correct AMI ID of Big-IP within the targeted AWS Region is needed, which should not be difficult to find.
Just a note that this CloudFormation template were tested with Big-IP version 15.0.1 build 0.0.11.
You will also need a valid F5 Big-IP License to execute this template.

This CloudFormation template is designed for building Demo/Testing environment only. It was NOT designed to be used for Live/Commercial environment!

The whole template require around 30 minutes to fully completed. Although the CloudFormation stack itself stated it has completed, the instances themselves need much more time to self-configure.

The diagram below depicts the Logical Network Diagram built by the following CloudFormation template(s).
![Logical Network Diagram with Windows Server](Figures/LogicalNetworkDiagramWindows.png)

The output part of the CloudFormation template is only 100% valid in the case of AS3 Declaration URL is using the default value.
Otherwise they're only partially valid (i.e. only management IPs/URLs are valid, while services' like Static Web Server, DVWA and Hackazon IPs/URLs are entirely dependent on AS3 Declaration being used).

Refer to [AS3-LTM-SSLOffLoad-NoOutBound](AS3-LTM-SSLOffLoad-NoOutBound/) as one example of AS3 Declaration.



***

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP_Win&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_BigIP_LAMP_Win_SSLOffL_eMail_Lidsa_Original.json"><img align="right" src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/LaunchStackJigokuShoujo.png" width="140" height="22"/></a>

The [CF_BigIP_LAMP_Win_SSLOffL_eMail_Lidsa.json](CF_BigIP_LAMP_Win_SSLOffL_eMail_Lidsa.json) template creates:
1. One F5's LAMPv7 instance which had been adapted to AWS environment in certain extend.
2. One F5's Windows Server 2008 R2 instance which had been adapted to AWS environment in certain extend.
3. One F5's Big-IP instance, license the instance, configure the networking part, and potentially also configure the services with the AS3 Declaration URL.
4. Import the TLS Private Key and Certificate into the Big-IP, so the corresponding AS3 Declaration can use them to create SSL Profiles.
5. Configure SSMTP and user_alert.conf to send email notification in case of an event. The example works with GMail's SMTP, and sending notification when a pool has no available member, and when the pool back to having a member available to handle the traffic.
6. Lorem Ipsum Dolor Sit Amet mock-up field.

Default AS3 Declaration for [CF_BigIP_LAMP_Win_SSLOffL_eMail_Lidsa.json](CF_BigIP_LAMP_Win_SSLOffL_eMail_Lidsa.json) is [AS3-LTM-SSLOffLoad-NoOutBound](AS3-LTM-SSLOffLoad-NoOutBound/), but can be changed during the CloudFormation template deployment,
provided the replacement AS3 Declaration fits into the Big-IP environment provided by the [CF_BigIP_LAMP_Win_SSLOffL_eMail_Lidsa.json](CF_BigIP_LAMP_Win_SSLOffL_eMail_Lidsa.json) template.

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP_Win&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_BigIP_LAMP_Win_SSLOffL_eMail_Lidsa.json"><img src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/JigokuShoujoLaunchStack.png" width="140" height="22"/></a>



***

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP_Win&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_Original.json"><img align="right" src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/LaunchStackJigokuShoujo.png" width="140" height="22"/></a>

The [CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20.json](CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20.json) template creates:
1. One F5's LAMPv7 instance which had been adapted to AWS environment in certain extend.
2. One F5's Windows Server 2008 R2 instance which had been adapted to AWS environment in certain extend.
3. One F5's Big-IP instance, license the instance, configure the networking part, and potentially also configure the services with the AS3 Declaration URL.
4. Import the TLS Private Key and Certificate into the Big-IP, so the corresponding AS3 Declaration can use them to create SSL Profiles.
5. Configure SSMTP and user_alert.conf to send email notification in case of an event. The example works with GMail's SMTP, and sending notification when a pool has no available member, and when the pool back to having a member available to handle the traffic.
6. Lorem Ipsum Dolor Sit Amet mock-up field.
7. Upgrade F5 Application Services 3 Extension from previous version 3.5.1-5 into version 3.20.0-3 .

Default AS3 Declaration for [CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20.json](CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20.json) is [AS3-LTM-SSLoL-AVR-NOutB](AS3-LTM-SSLoL-AVR-NOutB/), but can be changed during the CloudFormation template deployment,
provided the replacement AS3 Declaration fits into the Big-IP environment provided by the [CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20.json](CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20.json) template.

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP_LAMP_Win&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20.json"><img src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/JigokuShoujoLaunchStack.png" width="140" height="22"/></a>



***



To Do:

- [ ] Update existing AS3 with Pools from Windows Server ??? (should we do this or not?)
- [ ] Update Previous CF templates to use No OutBound versions of AS3 (and Update the corresponding Documentations)
- [ ] tmsh modify sys db ui.statistics.modulestatistics.localtraffic.persistencerecords value true
- [ ] Test Concept of Floating IP for High Availability. If 2 interfaces assigned same IP Address, will they be conflict? If not assigned, will they work?
- [ ] Default ASM Profiles
- [ ] APM (when applicable)



***


