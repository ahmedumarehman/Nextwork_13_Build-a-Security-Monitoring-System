<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Security Monitoring System

**Project Link:** [View Project](https://nextwork.ai/projects/a6948fcf-cdce-53e8-9037-892917ce7585)

**Author:** Ahmed Umar Rehman  
**Email:** ahmedumar475@gmail.com

---

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_reghtjy)

## Introducing Today's Project!

I'm doing this project to learn how to securely store secrets, track access using AWS CloudTrail, and create CloudWatch alarms with SNS email notifications to detect when someone accesses sensitive information.

### Tools and concepts

Services I used were AWS Secrets Manager, AWS CloudTrail, Amazon CloudWatch, Amazon SNS, and AWS IAM. Key concepts I learnt include secret management, API activity logging, CloudTrail trails, CloudWatch Logs, metric filters, alarms, SNS email notifications, IAM permissions, and monitoring and troubleshooting.

### Project reflection

This project took me approximately 1-2 hours. The most challenging part was configuring IAM permissions and troubleshooting CloudWatch metric filters, alarms, and SNS email notifications. It was most rewarding to understand how AWS services work together to record secret access, monitor suspicious activity, and send alerts through email.

## Create a Secret

Secrets Manager is an AWS service that securely stores sensitive information. You could use Secrets Manager to store database passwords, API keys, and other confidential credentials.

To set up for my project, I created a secret called TopSecretInfo that contains a dummy secret value for testing access monitoring.

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_o5p6q7r8)

## Set Up CloudTrail

CloudTrail is an AWS service that records activity in my AWS account. I set up a trail to track secret access events and store logs in an S3 bucket.

CloudTrail events include types like management events, data events, Insights events, and network activity events.

### Read vs Write Activity

Read API activity involves viewing data without changing it. Write API activity involves creating, modifying, or retrieving sensitive data. For this project, we need both enabled to monitor secret access events.

## Verifying CloudTrail

I retrieved the secret in two ways: First through the AWS Secrets Manager console. Second using AWS CLI in CloudShell.

To analyze my CloudTrail events, I visited CloudTrail Event History. I found a GetSecretValue event showing that my IAM user accessed the secret. This tells me that CloudTrail successfully records secret access activities for security monitoring.

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_s8t9u0v1)

## CloudWatch Metrics

CloudWatch Logs is an AWS service that stores and analyzes logs. It's important for monitoring because it helps detect specific events, troubleshoot issues, and trigger security alerts.

CloudTrail's Event History is useful for reviewing recent AWS account activity, while CloudWatch Logs are better for filtering events, monitoring specific activity, and triggering automated security alerts.

A CloudWatch metric is a measurement used to track specific activity. When setting up a metric, the metric value represents the amount recorded when the filter detects an event. The default value is used when no matching events are found during a time period.

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_a9b0c1d2)

## CloudWatch Alarm

A CloudWatch alarm is a monitoring feature that triggers an alert when a metric meets a specified condition. I set my CloudWatch alarm threshold to 1 so the alarm will trigger when at least one secret-access event is detected.

An SNS topic is a communication channel that distributes notifications to subscribers. My SNS topic is set up to send email notifications whenever the CloudWatch alarm detects secret-access activity.

AWS requires email confirmation because it needs to verify that the email address belongs to you. This helps prevent unauthorized subscriptions and ensures notifications are sent to the correct person.

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_fsdghstt)

## Troubleshooting Notification Errors

To test my monitoring system, I retrieved the secret value again using AWS Secrets Manager and checked CloudWatch for the alarm notification. The results were that I could verify the GetSecretValue event in CloudTrail, but I needed to check the metric filter, alarm state, and SNS email subscription to confirm that notifications were working correctly.

When troubleshooting the notification issues, I:

1. Checked CloudTrail Event History to confirm that `GetSecretValue` events were recorded.
2. Verified that CloudWatch Logs was enabled for my CloudTrail trail.
3. Checked that the metric filter was configured to detect secret access events.
4. Checked the CloudWatch alarm configuration and its threshold.
5. Verified that my SNS email subscription was confirmed and checked whether notifications were being delivered.

I initially didn't receive an email because the CloudWatch alarm, metric filter, or SNS email subscription was not fully configured or working correctly. The key solution was to troubleshoot the monitoring configuration, ensure the required IAM permissions were granted, and verify that the SNS email subscription was confirmed.

## Success!

To validate my monitoring system, I checked the CloudTrail events, CloudWatch metric filter, alarm status, and SNS email subscription. I received an email notification after confirming that the monitoring system was configured correctly.

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_ageraergearge)

## Comparing CloudWatch with CloudTrail Notifications

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/a6948fcf-cdce-53e8-9037-892917ce7585)*
