# CloudWatch Lab: Monitor an EC2 Instance

## Objective

Use Amazon CloudWatch to review metrics, build a dashboard, configure an alarm, and explore logs. This lab introduces how monitoring helps you notice performance and availability issues and troubleshoot them.

## How the pieces fit together

- **Metrics** are time-based measurements, such as EC2 CPU utilization.
- **Dashboards** display selected metrics in one place.
- **Alarms** evaluate metrics against a condition and can change state or trigger an action.
- **Logs** are event records collected from applications and services.
- **Amazon SNS** can deliver alarm notifications, for example by email.

## Before you begin

- Choose the AWS Region where your EC2 instance is running; CloudWatch resources and metrics are regional.
- Have a running EC2 instance to monitor.
- Basic EC2 metrics, including CPU utilization, network traffic, and status checks, are published to CloudWatch automatically. Detailed monitoring provides more frequent metric data and may incur additional charges.
- Memory usage and filesystem/disk-space metrics are not included in the standard EC2 metrics. To collect these, install and configure the CloudWatch agent.
- EC2 operating-system and application logs are not automatically available in CloudWatch Logs. Configure the CloudWatch agent or the relevant AWS service integration to publish them.

## Names and tags for this lab

Use these example values, or choose your own:

- Dashboard: `lab07-aws-overview`
- Alarm: `alarm-lab07-ec2-high-cpu`
- SNS topic: `sns-lab07-alerts`
- Tags:
  - `Name` = `lab07-cloudwatch`
  - `Project` = `aws-zero-to-hero`
  - `Environment` = `dev`
  - `Owner` = `your-name`
  - `Purpose` = `monitoring-practice`

Consistent names and tags make resources easier to identify, manage, and clean up.

## Step-by-step practice

### 1. Open CloudWatch

1. Sign in to the AWS Console.
2. Select the same Region as your EC2 instance.
3. Search for and open **CloudWatch**.

### 2. Review EC2 metrics

1. In CloudWatch, open **Metrics** and find the **EC2** metrics (the console may label this **All metrics**).
2. Select **Per-Instance Metrics** and choose your instance.
3. Review metrics such as:
   - `CPUUtilization`
   - `NetworkIn` and `NetworkOut`
   - `StatusCheckFailed`, `StatusCheckFailed_Instance`, and `StatusCheckFailed_System`

Standard EC2 metrics do not include memory utilization or filesystem usage. Those require the CloudWatch agent and appropriate configuration.

### 3. Create a dashboard

1. Open **Dashboards** and choose **Create dashboard**.
2. Name it `lab07-aws-overview`.
3. Add metric widgets for your instance, such as CPU utilization, status checks, and network traffic.
4. Save the dashboard.

Dashboards help you view selected signals together; they do not themselves alert you when a metric crosses a threshold.

### 4. Create a CPU alarm

1. In CloudWatch, open **Alarms** and choose **Create alarm**.
2. Select the EC2 `CPUUtilization` metric for your instance.
3. For a simple practice alarm, set the condition to **CPU utilization greater than 60%**.
4. Set the metric period to **1 minute** and configure the alarm to trigger when the condition is met for **5 consecutive evaluation periods**. This means the value is above the threshold for five one-minute periods.
5. Set missing data handling deliberately. For a basic lab, you can leave the default, but understand that missing data is not the same as zero CPU usage.
6. Name the alarm `alarm-lab07-ec2-high-cpu` and create it.

Choose a threshold that fits the workload. A short-lived CPU spike may not indicate a problem, so production alarms often use thresholds and evaluation windows based on service needs.

### 5. Optionally add an SNS notification

1. Create an SNS topic named `sns-lab07-alerts`.
2. Add an email subscription using an address you can access.
3. Confirm the subscription using the confirmation message sent by SNS; notifications will not arrive until the subscription is confirmed.
4. When creating or editing the alarm, configure the SNS topic as an alarm action for the **In alarm** state.

Alarm actions run when the alarm enters the configured state. Avoid sending test notifications to an address or endpoint you do not control.

### 6. Explore CloudWatch Logs

1. Open **Logs → Log groups** in CloudWatch.
2. Inspect log groups that have already been created for your AWS services.
3. If you want EC2 operating-system or application logs, install and configure the CloudWatch agent with the required permissions and log-file configuration.
4. Review log streams and set a retention period appropriate for the lab.

A log group is a collection of log streams. A stream contains log events from a particular source. Unlike standard EC2 metrics, instance log files must be configured for collection.

### 7. Test and verify

1. Open the alarm and check its current state and metric graph. A new alarm may show **Insufficient data** until it has enough metric datapoints.
2. If you choose to generate CPU load, do so only on an instance you own or are authorized to use, and stop the workload after the test.
3. Confirm the metric graph changes and observe whether the alarm state changes after the configured evaluation periods.
4. If configured, confirm that the SNS subscription receives the alarm notification.
5. Check that the dashboard displays the metrics you selected.

## Common issues

- **No instance metrics:** Confirm the selected Region and instance ID. Allow time for metric datapoints to arrive and verify the instance is running.
- **Memory or disk-space metrics are missing:** Install and configure the CloudWatch agent; these are not standard EC2 metrics.
- **No EC2 log groups appear:** Configure the CloudWatch agent or another log-publishing integration. Logs are not automatically collected from an EC2 operating system.
- **Alarm stays in Insufficient data:** Check that the metric is receiving datapoints, that the instance is running, and that the alarm's missing-data behavior is appropriate.
- **No email notification:** Confirm the SNS email subscription and verify the alarm has an action configured for the state it entered.

## Cost and security notes

- CloudWatch charges can apply to custom metrics, detailed monitoring, dashboards, alarms, log ingestion, storage, and queries. Check current AWS pricing for your Region and usage.
- Set log retention instead of keeping practice logs indefinitely.
- Use least-privilege IAM permissions for CloudWatch and the CloudWatch agent.
- Restrict access to dashboards, alarms, and logs to people who need it.
- Keep alarm thresholds and notifications useful to avoid unnecessary alert noise.

## Cleanup

After the lab, remove resources you no longer need:

- Delete the practice alarm and dashboard.
- Delete the SNS topic and subscription if they were created only for this lab.
- Remove or shorten retention for practice log groups as appropriate.
- If you installed the CloudWatch agent only for practice, uninstall it or remove its configuration if no longer needed.
- Stop or terminate any test EC2 instance you created, taking care not to remove resources you still use.

## Check your understanding

- What is the difference between a metric and a log?
- Which EC2 metrics are available by default, and what requires the CloudWatch agent?
- How does an alarm's evaluation period affect when it changes state?
- What must be done before an SNS email subscription can receive notifications?
- Why should log retention and IAM permissions be configured deliberately?

## Reflection

Write a short summary of what you learned about observability. Which metric or log would be most useful for troubleshooting a real application, and why?