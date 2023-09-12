## Hands-On Sessions

### Session 1 - Introduction to AWS (60-70min)
#### AWS Console
- How to Access AWS Environments (AWS Console, API, SDK)
- Navigating the AWS Console
	- Regions
	- Services selection
- [Documentation](https://docs.aws.amazon.com/index.html)
	- Service Quotas

#### Networking
- [Networking Concept (Intro to VPC's)](https://docs.aws.amazon.com/vpc/)
- Default VPC
- [Components (VPC,  Availability Zones, CIDR ranges, Security Groups, Route Tables, IGW, NAT-GW)](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)
- [Examples](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-examples-intro.html)
- [Build a VPC](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-getting-started.html)

#### Compute
- [Compute options (EC2, Containers, Serverless)](https://aws.amazon.com/products/compute/)
- [Intro to EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)
- [EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/)
- Start EC2 instance and install a webserver:
	- Save Private Key

```
#!/bin/bash
yum update -y
yum install -y httpd.x86_64
systemctl start httpd.service
systemctl enable httpd.service
echo "Hello World from $(hostname -f)" > /var/www/html/index.html

```

- Configure ALB and target group inkl. health check to /index.html
- Deploy second instance


### Session 2 - Introduction to AWS (60min)
#### EC2, Auto-Scaling, Load Balancing
- Create an EC2 launch template (explain User Data section)
- Create an Auto Scaling Group + ALB + Target Group via the ASG dialog
- Do tests on shutting down instances

#### S3 static website hosting
- [Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html)

Bucket Policy:
```
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "PublicReadGetObject",
			"Effect": "Allow",
			"Principal": "*",
			"Action": "s3:GetObject",
			"Resource": "<bucketarn>/*"
		}
	]
}
```

### Session 3 - Serverless translation service (60min)

#### Sources
[GitHub Repository](https://github.com/cvolkmer/translate-example-s3)

#### Access to AWS Environment
https://dashboard.eventengine.run
