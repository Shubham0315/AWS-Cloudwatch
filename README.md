# AWS-Cloudwatch


- Amazon CloudWatch is a powerful monitoring and management service designed to provide actionable insights into AWS resources, applications, and services.
- It is service watching Cloud Activities just like gatekeeper for AWS Cloud. It watches EC2 creation, upload to S3 buckets, creating resources. We can find these activities logged with AWS Cloud Watch
- To keep eye what activities are done on our AWS Account
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

- Login to EC2 and check the metrics of EC2 now

<img width="800" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/d1acc7a9-5969-4d67-86c4-d5df89415860">

- Suppose you want to check just CPU Utilization, we can select that metrics under EC2 and check usage. As we've only created the EC2, nothing will be there.

<img width="959" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/1b3f5916-10d0-4739-a6df-62d3e278bd32">

- Go back to EC2, select "Monitoring", we'll get all the information related to CloudWatch only

<img width="812" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/028dd442-ae2b-4b90-bf7e-a43e50003802">

If we expand the CPU Utilization there, we get below

<img width="945" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/466e8f3a-345b-4c1d-a679-5dccc78e75ce">

- By default, EC2 sends request to metrics every 5 mins. We can go to "Managed Detailed Monitoring" here and enable it so it will send matrics every one min.

<img width="832" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/e9c0db0e-f0d9-491e-b64c-24ae844f5761">

- Configure cpus_spike.py file into our EC2 terminal and run it
- Now if we check CPU Usage of metrics, we can see spike in it

<img width="959" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/0ab25d91-5e80-4229-97c9-0297c86ef091">

- We can select the metrics and go to "Graphed Metrics" to set Average, Minimum, Maximun. But in organizations, we do average metrics

<img width="908" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/d5279735-2638-442f-a326-54cfea00cc0c">


3. Alarms
- Now we got the required information about CPU but we need to act upon it. If we see issues, we as DevOps engineers need to report them.
- We can do them by setting alarms.
- We have now simulated the metrics. But now how to act on the metrics is work of alarm.
- We can set up alarm so that it notifies us if something goes wrong in critical systems.

- To create alarm, select metrics needed (EC2 here). Then specify metric and condition. Keep maximum of 1 min, cloudwatch will get metrics from EC2. Configure the conditions below (greater than). Then configure actions how we want to send notifications (create topic with name and email address). Topic means notification we're sending. Then setup the alarm

<img width="926" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/9422b316-644c-4622-8b81-35369fcfd304">

<img width="956" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/a4abe80f-e2e8-4b2a-9e1f-ac0e9049204d">

<img width="626" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/57e9e272-fae7-4c7b-a4b6-583b4c68c789">

<img width="959" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/9c381dee-5a65-42e6-bf81-24c0c1f504aa">

<img width="819" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/620f6f85-73e3-481e-8364-5a87de39c8ef">

- In this way alarm is created. But this alarm is not yet activated. We get insufficient data error like below.

<img width="959" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/f08f7140-327d-45e4-9b67-e98c8bafc836">

- This is due to we havent activated same from email address. We have to confirm the same from email which we got in inbox. After that we can see below.

 <img width="959" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/75018713-cdb9-4056-be24-1c8d106f261c">


- Now we've to trigger alarm from terminal. We have program for that is script. Run it again to get below

<img width="959" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/609f0a7b-d857-496c-80a1-84daf4ea974b">


























