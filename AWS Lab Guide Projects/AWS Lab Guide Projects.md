AWS Lab Guide Projects

AWS EC2 Lab Guide for Beginners

Focuses on AWS EC2 fundamentals, covering the steps to launch, configure, and manage instances. It also appeals directly to beginners and those seeking to gain hands-on experience with AWS compute resources, security, and performance.

Compute Resources and EC2

1. What is EC2?

Explain the purpose of Amazon EC2. Why is it considered an example of Infrastructure as a Service (IaaS)?

EC2 (Elastic Compute Cloud) is a web service provided by Amazon Web Services (AWS) that allows users to rent virtual computers, known as instances, in the cloud to run applications. It provides scalable computing power, meaning you can quickly scale up or down depending on your needs, whether you're hosting websites, running databases, processing data, or any other computational tasks.

Key features of EC2 include:

Scalability: You can scale up or down based on your computing needs, paying only for the resources you use.

Variety of Instance Types: EC2 offers a wide range of instance types that vary in CPU, memory, storage, and networking capabilities to fit specific use cases.

Elasticity: You can automatically adjust the number of instances you’re using through features like Auto Scaling, which adjusts capacity based on traffic demand.

Security: EC2 instances can be secured with firewalls, encryption, and access management controls to meet security requirements.

Pay-as-you-go Pricing: You only pay for the compute capacity you actually use, and pricing is based on the instance type and the duration of usage.

EC2 is often used to run applications, websites, big data processing, machine learning models, and more. It’s one of the core services in AWS, helping companies handle high-availability and highly scalable applications in the cloud.


Amazon EC2 (Elastic Compute Cloud) 

serves the primary purpose of providing scalable and flexible computing power in the cloud. It allows users to rent virtual servers (called instances) on-demand to run their applications, websites, databases, or any computational tasks without having to invest in or manage physical hardware. The core benefit of EC2 is its scalability, flexibility, and cost-effectiveness, allowing businesses to grow and adjust their infrastructure quickly according to their needs.

Purpose of Amazon EC2:

Scalable Computing Resources: 

EC2 allows users to quickly provision and scale virtual servers to handle varying amounts of traffic and workloads. Whether it's scaling up during peak demand or scaling down during low traffic periods, EC2 makes it easy to adjust your infrastructure in real time.

Cost Efficiency: 

Instead of investing in physical hardware, users pay only for the computing resources they use (i.e., the number of EC2 instances, their type, and how long they are running). This pay-as-you-go model helps reduce upfront capital expenses.

Global Availability: 

EC2 instances can be deployed in multiple geographic regions around the world. This helps to ensure high availability and redundancy for applications and services.

Flexibility:

EC2 offers a wide range of instance types with varying CPU, memory, storage, and networking configurations, enabling users to select the instance that best suits their specific workload.

Security and Control: 

Users have full control over their EC2 instances, including the ability to configure firewall rules, manage network access, and choose encryption options for securing data.

Why is EC2 considered Infrastructure as a Service (IaaS)?

Amazon EC2 is considered an example of Infrastructure as a Service (IaaS) because it provides users with basic infrastructure components, like compute power (virtual machines), networking, and storage, that are essential for running applications but without requiring them to own or manage the physical hardware.

In more detail:

Compute (Virtual Machines): EC2 provides virtual machines (or instances) with configurable CPU, memory, and storage. Users don’t need to worry about the underlying physical infrastructure, as AWS takes care of hardware maintenance, failure recovery, and resource management.

Networking and Connectivity: EC2 instances can be connected to other AWS services or the internet, offering networking flexibility. This includes features like Virtual Private Cloud (VPC) to define isolated network environments and security groups to control network access.

Storage: EC2 integrates with various AWS storage options (like Elastic Block Store (EBS) for persistent storage) that users can attach to their instances as needed.

Control and Customization: EC2 allows users to have complete control over the virtual machines, including choosing the operating system, configuring software, and managing the state of the instances.

Since IaaS focuses on delivering the fundamental building blocks of IT infrastructure in the cloud (compute, storage, networking), EC2 fits this model perfectly. Users are provided with the essential components to build and run their applications without the need to manage physical hardware or data centers.

2. Launch Your First EC2 Instance

Go to the AWS Management Console.

Search for EC2 and click on Instances.

![alt text](<AWS Lab Guide Projects IMAGES/EC2.png>)


![alt text](<AWS Lab Guide Projects IMAGES/STEP 1.png>)


Create New Key Pair

![alt text](<AWS Lab Guide Projects IMAGES/CREAT NEW KEY PAI.png>)

Launch Instance

![alt text](<AWS Lab Guide Projects IMAGES/INSTANCE LAUNCH.png>)



2.2 Step 2: Connect to the EC2 Instance

Once the instance is launched, go to the Instances section.

Select the instance you just launched.

Click Connect and follow the instructions to connect via SSH


![alt text](<AWS Lab Guide Projects IMAGES/connect  to EC2 instance.png>)


2.3 Step 3: Install a Web Server (Nginx)

After connecting via SSH, run the following commands to install Nginx:

![alt text](<AWS Lab Guide Projects IMAGES/install Ngix.png>)


3. Understanding Security Groups
Image

3.1 Step 1: Set Up Security Groups

![alt text](<AWS Lab Guide Projects IMAGES/SECURITY GROUPS.png>)


4. Elastic IPs
4.1 Step 1: Allocate and Assign an Elastic IP


Go to the EC2 dashboard and click on Elastic IPs under Network & Security.

Click Allocate Elastic IP Address and choose the default Amazon pool.

Click Allocate.

![alt text](<AWS Lab Guide Projects IMAGES/ELASTIC IP.png>)

After allocation, select the Elastic IP and click Actions → 

![alt text](<AWS Lab Guide Projects IMAGES/ALLOCAT ELASTIC IP.png>)


Associate Elastic IP Address.

![alt text](<AWS Lab Guide Projects IMAGES/ASSOCIATE EL2.png>)

Choose the EC2 instance you launched earlier from the 

![alt text](<AWS Lab Guide Projects IMAGES/EL.png>)

Instance dropdown.

Click Associate.

![alt text](<AWS Lab Guide Projects IMAGES/ELASTIC IP ALLOCATION SUCCESFUL.png>)

5. Stop, Start, and Terminate EC2 Instances

Explain the difference between stopping, starting, and terminating an EC2 instance. Perform each operation and observe the effects.

![alt text](<AWS Lab Guide Projects IMAGES/STOP START ISTANCE STATE .png>)


6. Performance Optimization of EC2 Instances

Outline steps that a junior DevOps engineer can take to identify and resolve performance issues on EC2 instances, 
focusing on monitoring, analysis, and optimization techniques


 1. Monitoring the Instance

Use these tools to gather real-time data:

Amazon CloudWatch: Set up monitoring for key metrics like CPU utilization, memory usage (with custom scripts), disk I/O, and network throughput.

EC2 Instance Status Checks: Monitor for hardware or network-level issues.

SSM Agent + Logs: Use AWS Systems Manager for remote shell access and centralized log collection.

Top/htop/iostat/netstat: Use these Linux tools to identify bottlenecks in compute, disk, or network.

📊 2. Analyzing Performance Metrics

Look for red flags:

High CPU: Check for runaway processes (top, ps aux --sort=-%cpu).

Memory Swapping: Indicates insufficient RAM; check with free -m or vmstat.

Disk I/O Waits: Use iostat or iotop to identify slow disks or heavy read/write apps.

Network Bottlenecks: Check iftop or CloudWatch’s NetworkIn/Out metrics.

⚙️ 3. Optimization Techniques

✅ Compute Tuning
Right-size the instance: Scale vertically (e.g., from t3.micro → t3.medium) if CPU or memory consistently spikes.

Use Auto Scaling: For horizontal scaling in stateless environments.

✅ Disk Optimization

Use EBS-optimized instances.

Upgrade to gp3 or io2 volumes for better IOPS.

Separate volumes for OS and data when applicable.

✅ Networking

Place instances in appropriate AZs/Subnets.

Enable enhanced networking (ENA/SR-IOV) for high-throughput needs.

✅ OS & App Tuning

Update system packages and kernel.

Configure Nginx, Apache, or DB servers with tuned parameters (worker_processes, buffer sizes, etc.).

Use caching (Redis, Memcached) to reduce load.

🧪 4. Automation & Follow-Up

Set CloudWatch Alarms to get notified before issues escalate.

Use AWS Trusted Advisor for performance recommendations.

Periodically audit with performance baselines and load testing tools (e.g., ApacheBench, locust.io).