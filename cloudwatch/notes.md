# CloudWatch Lab

## Objective

Use Amazon CloudWatch to monitor AWS resources, review metrics and logs, create dashboards, and configure alarms that show how operational visibility supports secure and reliable workload management.

## Why this matters

Monitoring is a core operational skill in AWS. Without CloudWatch, it is difficult to know whether a system is failing, slow, over-utilized, or behaving unexpectedly. This lab teaches the habit of observing the health of services before issues become outages.

## Before you begin

Before reviewing metrics, make sure:

- you have a running EC2 instance or other AWS service to monitor
- CloudWatch is enabled for the resource
- you have a small test workload to generate metrics
- you understand the region where the service is running

## What you need to update in AWS

When creating the monitoring setup, update these values:

- Dashboard name: `lab07-aws-overview`
- Alarm name: `alarm-lab07-ec2-high-cpu`
- SNS topic name: `sns-lab07-alerts`
- Tags:
  - Name = `lab07-cloudwatch`
  - Project = `aws-zero-to-hero`
  - Environment = `dev`
  - Owner = `your-name`
  - Purpose = `monitoring-practice`

Why this matters:
- dashboards make operational health easier to see
- alarms enable early response to issues
- tags help you manage cost and cleanup
- naming conventions reduce confusion when you have multiple alarms and dashboards

## Step-by-step instructions

### Step 1: Open CloudWatch

1. Open the AWS Console.
2. Search for CloudWatch.
3. Open the CloudWatch dashboard and metrics section.

### Step 2: Review EC2 metrics

Select a running EC2 instance and review:

- CPU utilization
- network traffic
- status checks
- disk activity if applicable

This shows how AWS exposes resource health through metrics.

### Step 3: Create a dashboard

1. Go to Dashboards.
2. Click Create dashboard.
3. Name it `lab07-aws-overview`.
4. Add widgets for:
   - CPU utilization
   - status checks
   - network in/out
5. Save the dashboard.

This makes operations easier to visualize at a glance.

### Step 4: Create a CloudWatch alarm

Configure an alarm for CPU utilization:

- metric: CPU utilization
- threshold: above 60% for 5 minutes
- alarm name: `alarm-lab07-ec2-high-cpu`
- action: optional SNS notification

This teaches the idea of proactive alerting before an issue becomes critical.

### Step 5: Add SNS notifications

If you use an alarm notification:

1. create an SNS topic
2. subscribe your email or a simple endpoint
3. attach the topic to the alarm

This demonstrates how CloudWatch can notify a human or downstream service when a threshold is breached.

### Step 6: Review logs

1. Open CloudWatch Logs.
2. Inspect log groups for EC2, Lambda, or other services.
3. Check log streams and retention policy.

This shows the difference between system metrics and detailed operational logging.

### Step 7: Test the alarm behavior

Trigger a CPU spike or run a workload that increases processor use.

Then review:

- the metric graph
- alarm status
- any SNS notification
- the dashboard changes

This confirms that monitoring works in real time.

## Key concepts to remember

- Metric: a numerical signal such as CPU or network activity
- Alarm: threshold-based alerting mechanism
- Dashboard: a visual summary of metrics
- Log group: collection of log streams
- SNS: message delivery service for alerts

## Common mistakes to avoid

- setting thresholds too low and creating noisy alerts
- ignoring cost implications of long log retention
- creating dashboards without meaningful widgets
- not testing the alarm after creation

## Cost and security notes

- log retention can increase cost over time
- keep alarm thresholds practical
- avoid unnecessary notifications
- secure access to CloudWatch logs and alarm configuration

## Cleanup

After the lab:

- delete unused alarms
- remove unnecessary SNS topics
- delete dashboards you no longer need
- reduce log retention or remove old logs if not required

## Check your understanding

Answer these in your notes:

- Why is monitoring important in AWS?
- What is the difference between CloudWatch metrics and logs?
- When should you create an alarm instead of just checking a dashboard?
- How does CloudWatch support reliability and troubleshooting?
- Why do cost and retention settings matter for log data?

## Reflection

Write a short summary:

- What did this lab teach you about observability?
- Which monitoring signal seems most useful in real systems?
- Why is monitoring one of the biggest differences between a beginner setup and a production environment?
