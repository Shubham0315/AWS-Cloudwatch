# AWS-Cloudwatch


- Amazon CloudWatch is a powerful monitoring and management service designed to provide actionable insights into AWS resources, applications, and services.
- It is service watching Cloud Activities just like gatekeeper for AWS Cloud. It watches EC2 creation, upload to S3 buckets, creating resources. We can find these activities logged with AWS Cloud Watch
- To keep eye what activities are down on our AWS Account
- It helps in monitoring, alerting, reporting and logging. Using these features of CloudWatch we can keep track of activities that are happening on our AWS Account

# Uses of AWS Cloudwatch

1. Monitoring
- We can implement monitoring using CloudWatch as its very imp for DevOps engineer. It plays important role in Infrastructure monitoring but still we can do app monitoring as well

2. Real Time Metrics
- It allows to get Real time metrics
- In using EC2, Metrics can be how many API request our app inside EC2 receive? or In last 30 mins CPU utilization/memory consumption on EC2?

3. Alarms
- We get alarming using CloudWatch. Metric and alarms are very closely associated
- If we collect metrics for CPU utilization, user will go to metrics dashboard and observes that. We are getting metrics, but we need to take actions on that if CPU is getting full. We need to take action on metrics outcome
- So cloudwatch, if our memory goes above some threshold, we can configure alarm such as to send email notification to us or send an alarm of consumption.
  * Thus both Metrics and Alarms are closely associated.

4. Log Insights
- CloudWatch also gives us log insights. Provides logs of which service is accessing other service
- Earlier we connected our EC2 with Code pipeline. If we go to cloud watch we can see our EC2 was trying to connect with one of the AWS service with timestamp

5. Custom metrics.
- CPU Utilization is custom metrics. Memory utilization is not. We need to send custom metrics to cloudwatch for memory. 

6. Cost Optimization
- To reduce cost of our AWS services and Account

7. Scaling Resources
- CloudWatch also helps in scaling
- If our CPU is above threshold, cloudwatch will inform auto scaling groups. If it goes above threshold, cloudwatch sends notification to  auto scaling groups and they will scale EC2 to next level


** Thus there are "default metrics" configured in cloud watch. If we ned to enhance CloudWatch, we can use "Custom Metrics"


# Practical Demo

- Top features of Cloudwatch are :- Logs, Metrics, Alarms, Dashboards, ServiceLens

1. Log Groups
- Go to Cloudwatch and go to Log Groups. Cloudwatch automatically creates groups for our logs based on our use of particular service
  e.g:- Earlier we created Code Build service. So it has created log group for that for code build logs.
- Here cloudwatch was observing the activities in code build service. So cloudwatch logged everything happening for that project.
- If we go to log stream, we can get how many times we've done changes and build.
  Even if we have deleted any project, we can come to cloudwatch and get information about success or errors.

<img width="959" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/0a9fcd61-2b24-4d1c-9c6c-cb6fb05b286d">

<img width="959" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/df691118-750c-488b-9e3e-bcd226272553">

2. Metrics
- It helps to collect information about AWS resources.
- If we go to "All Metrics", we get "N" default metrics (130 here) which is being tracked all the time on our account. It will collect all information of all services in use,

<img width="943" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/93751a67-b821-4d94-a09c-4aa22cf74c2a">

- If we go inside any of the metrics, we get the information about all the metrics inside a service

<img width="791" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/736f6345-aa90-43a6-ada2-623929090b69">

- If here we go inside EC2 and want to get CPU Utilization, we will click on the same and get insights.

** Now Create an EC2 Instance
- The script inside Custom_Metrics folder is to increase or decarease the CPU utilization of EC2 and to track metrics information on cloudwatch














