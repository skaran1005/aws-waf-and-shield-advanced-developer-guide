# AWS managed policies for AWS Firewall Manager<a name="fms-security-iam-awsmanpol"></a>





To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the `ViewOnlyAccess` AWS managed policy provides read\-only access to many AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.

## AWS managed policy: FMSServiceRolePolicy<a name="security-iam-awsmanpol-FMSServiceRolePolicy"></a>

This policy allows AWS Firewall Manager to manage AWS resources on your behalf in Firewall Manager and in integrated services\. This policy is attached to the service\-linked role `AWSServiceRoleForFMS`\. For more information about the service\-linked role, see [Using service\-linked roles for Firewall Manager](fms-using-service-linked-roles.md)\. 

For policy details, see the IAM console at [FMSServiceRolePolicy](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/FMSServiceRolePolicy$serviceLevelSummary)\.













## Firewall Manager updates to AWS managed policies<a name="fms-security-iam-awsmanpol-updates"></a>

View details about updates to AWS managed policies for Firewall Manager since this service began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the Firewall Manager document history page at [Document history](doc-history.md)\.




| Change | Description | Date | 
| --- | --- | --- | 
|  `FMSServiceRolePolicy` – New permissions for AWS Firewall Manager third\-party firewall policies  |  This change allows Firewall Manager to create and delete the Amazon EC2 VPC endpoints associated with a third\-party firewall policy\.  | March 30, 2022 | 
|  `FMSServiceRolePolicy` – New permissions for AWS Network Firewall policies  |  Added new permissions to support deployment of firewalls for Network Firewall policies\. The new permissions allow the retrieval of information about Availability Zones for accounts that are in scope of a policy\.   | February 16, 2022 | 
|  `FMSServiceRolePolicy` – New permissions for AWS Shield policies  |  Added new permissions to retrieve tags for AWS WAF regional and AWS WAF global resources\. Added AWS WAF regional permissions to retrieve web ACLs using a resource ARN\. Added permissions to support Shield automatic application layer DDoS mitigation\.   | January 07, 2022 | 
|  `FMSServiceRolePolicy` – New permissions for AWS Shield policies  |  Added new permission to retrieve tags for Elastic Load Balancing resources\.   | November 18, 2021 | 
|  `FMSServiceRolePolicy` – New permissions for security group and AWS Network Firewall policies  |  Added new permissions to enable centralized logging for AWS Network Firewall policies\. Additionally, read\-only Amazon EC2 permissions were added to support changes to the Config service that impact how AWS Firewall Manager queries resources for security group policies\.  | September 29, 2021 | 
|  `FMSServiceRolePolicy` – ARN formats for AWS WAF resources  |  Updated the `FMSServiceRolePolicy` to standardize the ARN formats for AWS WAF resources\. The updated ARN formats are `arn:aws:waf:*:*:*` and `arn:aws:waf-regional:*:*:*`\.  | August 12, 2021 | 
|  `FMSServiceRolePolicy` – Additional regions in China  |  AWS Firewall Manager has enabled `FMSServiceRolePolicy` for the BJS and ZHY regions in China\.  | August 12, 2021 | 
|  `FMSServiceRolePolicy` – Update to the existing policy  |  Added new permissions to allow AWS Firewall Manager to manage Amazon Route 53 Resolver DNS Firewall\. This change allows Firewall Manager to configure Amazon Route 53 Resolver DNS Firewall associations\. This permits you to use Firewall Manager to provide DNS Firewall protections for your VPCs throughout your organization in AWS Organizations\.  | March 17, 2021 | 
|  Firewall Manager started tracking changes  |  Firewall Manager started tracking changes for its AWS managed policies\.  | March 01, 2021 | 