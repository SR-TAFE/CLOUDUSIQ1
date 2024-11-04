# Auto Scaling Troubleshooting Exercise

## Overview
This exercise helps you develop problem-solving skills by investigating why auto scaling is not working in a given AWS infrastructure. You'll work with a CloudFormation template that deploys a web server with monitoring capabilities.

## Learning Objectives
- Understand AWS Auto Scaling components and dependencies
- Practice AWS infrastructure troubleshooting
- Analyze CloudWatch metrics and alarms
- Identify missing components in an AWS architecture

## Prerequisites
- AWS Account with appropriate permissions
- Basic understanding of AWS services (EC2, CloudWatch, Auto Scaling)
- AWS CLI configured locally
- An existing EC2 key pair in your AWS account

## Infrastructure Components
The template deploys:
- EC2 instance running a basic web server
- Security group allowing HTTP and SSH access
- CloudWatch alarm monitoring CPU utilization
- CloudWatch dashboard displaying metrics

## Problem Statement
The infrastructure is designed to automatically scale based on CPU utilization, but it's not working as expected. Your task is to identify why the auto scaling functionality is failing.

## Setup Instructions
1. Log into your AWS Console
2. Navigate to CloudFormation
3. Create new stack and upload the template
4. Provide parameters:
   - Instance Type (t2.micro or t2.small)
   - EC2 KeyPair name

## Troubleshooting Exercise

### Step 1: Review Current Configuration
1. Examine the CloudFormation template
2. List all components related to auto scaling
3. Document what you find and what's missing

### Step 2: Test CPU Alarm
1. SSH into the EC2 instance:
   ```bash
   ssh -i your-key.pem ec2-user@<instance-public-dns>
   ```

2. Generate CPU load:
   ```bash
   sudo stress --cpu 1 --timeout 600
   ```

3. Monitor the CloudWatch dashboard
4. Document the alarm behavior

### Step 3: Identify Missing Components
Look for these critical auto scaling components:
- [ ] Launch Template/Configuration
- [ ] Auto Scaling Group
- [ ] Scaling Policies
- [ ] Target Group (if using ALB)
- [ ] Integration between CloudWatch Alarm and Scaling Policy

## Solution Hints
1. The template only contains monitoring components
2. No auto scaling group is defined
3. CloudWatch alarm exists but has no scaling actions configured

## Expected Findings
Students should identify that the template:
1. Lacks an Auto Scaling Group definition
2. Missing scaling policies
3. Has no integration between the CloudWatch alarm and scaling actions
4. Requires additional components for a complete auto scaling solution

## Extension Activities
1. Modify the template to add missing components
2. Test the modified infrastructure
3. Document best practices for auto scaling configurations

## Additional Resources
- [AWS Auto Scaling Documentation](https://docs.aws.amazon.com/autoscaling/)
- [CloudWatch Alarms Documentation](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html)
- [Auto Scaling Best Practices](https://docs.aws.amazon.com/autoscaling/ec2/userguide/auto-scaling-best-practices.html)

## Support
For assistance, please:
1. Review AWS documentation
2. Check CloudWatch logs
3. Verify IAM permissions
4. Consult with your instructor

## Success Criteria
You've completed the exercise when you can:
1. Identify all missing components
2. Explain why auto scaling isn't working
3. Propose a solution to implement proper auto scaling
4. Document your findings and reasoning
