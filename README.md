# AWS-Cloudwatch


- It is a service watching activities on cloud. It is basically a gatekeeper for AWS cloud watching activities on cloud like creating EC2, uploading objects on S3, creating any resource. We can find these activities logged using cloudwatch.
- It is gatekeeper for AWS which helps in monitoring, alerting, logging and reporting.
- Amazon CloudWatch is a powerful monitoring and management service designed to provide actionable insights into AWS resources, applications, and services.
- It is service watching Cloud Activities just like gatekeeper for AWS Cloud. It watches EC2 creation, upload to S3 buckets, creating resources. We can find these activities logged with AWS Cloud Watch
- To keep eye what activities are done on our AWS Account
- It helps in monitoring, alerting, reporting and logging. Using these features of CloudWatch we can keep track of activities that are happening on our AWS Account


# Uses of AWS Cloudwatch

#1. Monitoring
- We can implement monitoring using CloudWatch as its very imp for DevOps engineer. It plays important role in Infrastructure monitoring but still we can do app monitoring as well

#2. Real Time Metrics
- It allows to get Real time metrics
- Cloudwatch helps in telling us what metrics we're getting for our AWS services
- While using EC2, Metrics can be :-
  - How many API request our app inside EC2 receive?
  - In last 30 mins CPU utilization/memory consumption on EC2?
- Metrics helps in understanding the utilization or details of AWS services.
- Metrics are easy way to communicate with users.

#3. Alarms
- Metrics and alarms are very closely associated
- If we collect metrics for CPU utilization, user will go to metrics dashboard and observes that conveying CPU utilization. We've collected metrics, but we need to take actions on that if CPU is getting full. We need to take action on metrics outcome. So our responsibility will not only be to collect the metrics but also take actions on metrics outcome
- So cloudwatch, if our memory goes above some threshold we've set, we can configure alarm such as to send email notification to us or send an alarm of consumption.
- Thus both Metrics and Alarms are closely associated.

#4. Logging
- CloudWatch also gives us log insights. Provides logs of a service accessing other service. Logging here happens automatically.
- Earlier we connected our EC2 with Code pipeline/deploy. If we go to cloudwatch and looks out for logs, we can see our EC2 was trying to connect with one of the AWS service with timestamp.

#5. Custom metrics.
- CPU Utilization is default metrics. By default Cloudwatch tracks CPU utilization for EC2 but it doesnt track memory utilization of EC2.
- Here we need to enhance cloudwatch by sending custom metrics to cloudwatch. Using this, we can track our application, its memory, etc.

#6. Cost Optimization
- The primary reason to switch to AWS is to reduce maintenance and enhance security. Another thing is cost optimization.
- To reduce cost of our AWS services and Account.

#7. Scaling Resources
- Cloudwatch doesnt directly perform cost optimization or scaling. But it can integrate with other services like lambda and help in reducing cloud cost.
- It also helps in identifying unused resources on our AWS account.
- CloudWatch also helps in scaling.
- If our CPU is above threshold, cloudwatch will inform auto scaling groups. If it goes above threshold, cloudwatch sends notification to auto scaling groups and they will scale EC2 to next level by increasing replicas of EC2.


** Thus there are "default metrics" configured in cloud watch. If we ned to enhance CloudWatch, we can use "Custom Metrics"

---------------------------------------------------------------------------------------------------------------------------------

# Practical Demo

- Top features of Cloudwatch are :- Logs, Metrics, Alarms, Dashboards, ServiceLens
- Cloudwatch dashboard :-

![image](https://github.com/user-attachments/assets/60f91a10-53bc-48e1-b747-aed2b13a7006)

Log Groups
-
- Go to Cloudwatch - Log Groups.
- Cloudwatch automatically creates groups for our logs based on our use of particular service
  - e.g:- Earlier we created Code Build service. So it has created log group for that for the activities in code build .
- Here cloudwatch was observing the activities in code build service tracking activities inside it. So cloudwatch logged everything happening for that project.
  - It gives info like how all the stages were performed for the pipeline, build service. Entire log of build process is available (just like jenkins)
- If we go to log stream, we can get how many times we've done changes and build.
- Even if we have deleted any project, we can come to cloudwatch and get information about success or errors.

![image](https://github.com/user-attachments/assets/3506e518-77f2-4738-bec7-19e8853a53a6)
![image](https://github.com/user-attachments/assets/5da6c32f-4463-4a5f-ad50-bab4041bc20c)
![image](https://github.com/user-attachments/assets/6fbc097f-6ee4-44b0-a0b5-5d861a65fef0)

- We can even check logs for specific time duration

![image](https://github.com/user-attachments/assets/73ec93aa-5d7e-40b8-b5ba-24334c0acb19)

- Here not only successful logs are recorded but also failed events are recorded.

![image](https://github.com/user-attachments/assets/304b30d9-d3fc-47a4-bb87-18c484c97393)

- It can also give you log insights (will see later)

![image](https://github.com/user-attachments/assets/d0571e50-1571-47e2-99db-8565bd2fadbe)

Metrics
-
- It helps to collect information about AWS resources like EC2 CPU, EC2 Disk usage. 
- If we go to "All Metrics", we get "N" default metrics (410 here) which is being tracked all the time on our account. It will collect all information of all services in use.
  - We can see how many metrics are associated with each service.

![image](https://github.com/user-attachments/assets/55efc5d4-56ff-4664-bee2-00f2008bc168)

- We can check every service's dashboard by clicking on metics link as below

<img width="959" alt="image" src="https://github.com/user-attachments/assets/dfa259ad-e440-47ca-9a16-be935fb5ca81" />

  - Here we can see all the deault dashboards created

![image](https://github.com/user-attachments/assets/dd738249-d18b-42f7-ab20-ecddba7c50d2)

- If we go inside any of the metrics, we get the information about all the metrics inside a service
  - If we've CPU utilization metrics, we can see how our EC2 was performing for specific time frame

![image](https://github.com/user-attachments/assets/4f96c709-0cd9-4083-9c25-49861f4aede8)

- If here we go inside EC2 and want to get CPU Utilization, we will click on the same and get insights.

** Now Create an EC2 Instance
- Launch one instance
- Write python application to vary the CPU and check the metrics
- The script inside Custom_Metrics folder is to increase or decarease the CPU utilization of EC2 and to track metrics information on cloudwatch (cpu_spike.py)

![image](https://github.com/user-attachments/assets/2e4f40cd-fe3d-401e-b922-d5bdb5c60912)

- Login to EC2 using UI and if we check "top" everything will be normal.

- Now go to cloudwatch and go to EC2 and check the metrics of EC2 now there will be nothing

<img width="800" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/d1acc7a9-5969-4d67-86c4-d5df89415860">

- Suppose you want to check just CPU Utilization, we can select that metrics under EC2 and check usage. As we've only created the EC2, nothing will be there.

<img width="959" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/1b3f5916-10d0-4739-a6df-62d3e278bd32">

- Go back to EC2, select "Monitoring", we'll get all the information related to CloudWatch only

![image](https://github.com/user-attachments/assets/d06aad6b-ad1a-420a-bd7f-817c120b65ac)

- If we expand the CPU Utilization there, we get below

![image](https://github.com/user-attachments/assets/c13d54a6-391e-450e-bfe1-c6759f189d67)

- By default, EC2 sends request to metrics every 5 mins. We can go to "Managed Detailed Monitoring" here and enable it so it will send matrics every one min.

<img width="959" alt="image" src="https://github.com/user-attachments/assets/68820bc3-90c2-4bfd-ac8c-30eace4bdd27" />

- Now we can check the metrics in AWS Cloudwatch console as well

- Configure cpus_spike.py file into our EC2 terminal and run it to increase spike of CPU
  - Command :- **python3 cpu_spike.py**
 
![image](https://github.com/user-attachments/assets/88ce1953-7364-490f-9090-d8ef54cea5fd)

- If we check CPU Utilization metrics inside EC2, and set time to 1 sec or so, we can see below spike

![image](https://github.com/user-attachments/assets/1368fe77-e6cc-4dd5-a463-e332e35b25c1)

- Now if we check CPU Usage of metrics, we can see spike in it. Search by instance ID and then CPUUtilization

![image](https://github.com/user-attachments/assets/52493ba5-0607-48ce-bc85-f6359be1346b)

- We can also get the iformation of metrics in pie chart, bar graph etc. To get more easier view.

![image](https://github.com/user-attachments/assets/3f578dba-792c-47db-af11-c355943b71ea)
![image](https://github.com/user-attachments/assets/071b8c99-e34f-4761-8475-81f1d7c8e668)


<img width="959" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/0ab25d91-5e80-4229-97c9-0297c86ef091">

- We can select the metrics and go to "Graphed Metrics" to set/check Average, Minimum, Maximun. But in organizations, we do average metrics.

<img width="908" alt="image" src="https://github.com/Shubham0315/AWS-Cloudwatch/assets/105341138/d5279735-2638-442f-a326-54cfea00cc0c">

- When we stop the spike file, CPU utilization comes to normal

Alarms
-
- Now we got the required information about CPU but we need to act upon it. If we see issues, we as DevOps engineers need to report them.
- We can do this by setting/configuring alarms.
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


























