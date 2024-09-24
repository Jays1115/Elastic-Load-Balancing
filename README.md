<h5>Directory</h5> 

<b>[Tech Portfolio Home](https://github.com/Jays1115/Jalen-Smith.git)</b> /
<b>[AWS Projects](https://github.com/Jays1115/AWS-Projects.git)</b>

# Elastic Load Balancing

<h2>Description</h2>
Scenario: a travel agency that recently held a promotional event. The event significantly increased web traffic, causing the agency's website to become overloaded and unable to handle the influx of requests, leading to timeouts. Additionally, the agency's EC2 instances, hosted on AWS in an Availability Zone, were affected by severe storms, which resulted in the website being offline for several hours.
<br/> <br/>
Solution: To manage traffic surges and maintain website uptime, create an Auto Scaling Group that adjusts the number of EC2 instances based on demand. Set up a Load Balancer to distribute incoming traffic evenly across these instances, and attach the Auto Scaling Group to it for seamless scalability. Implement Load Balancer Health Checks to ensure traffic is only directed to healthy instances, enhancing the reliability of your service.

<h2>Program walk-through:</h2>

<p align="center">
Navigated to the EC2 dashboard: <br/>
<img src="images/Screenshot 2024-09-24 at 8.52.15 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
I navigated to "Auto Scaling Groups" (ASG) using the left sidebar. Then, I selected the ASG named "TravelAgencyWebServers" and clicked on the "Instance Management" tab to view all the running instances in this ASG: <br/>
<img src="images/Screenshot 2024-09-24 at 8.55.54 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 8.59.44 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<h3 align="center">Creating the Load Balancer & Configuring Complimentary Settings</h3>

<p align="center">
Returned to the details tab of the Auto Scaling Group (ASG) and scrolled down to the section on Load Balancers. Here, I added an internet-facing application load balancer, which connects to three public subnets across three different availability zones. Additionally, I created a new target group: <br/>
<img src="images/Screenshot 2024-09-24 at 9.02.30 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.03.34 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.05.23 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.05.37 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.06.15 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Navigated to "Security Groups" via the left side bar to create a new security group for the load balancer: <br/>
<img src="images/Screenshot 2024-09-24 at 9.14.31 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
I configured the load balancer settings to allow inbound HTTP traffic from the internet and directed outbound traffic to the security group of the travel agency web server: <br/>
<img src="images/Screenshot 2024-09-24 at 9.17.54 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.18.43 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.20.13 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
I returned to "Security Group" through the left sidebar, selecting the TravelAgencyWebServer security group to modify its inbound rules. I deleted the existing rule and replaced it with a new rule that permits HTTP traffic from the recently created load balancer: <br/>
<img src="images/Screenshot 2024-09-24 at 9.22.11 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.22.43 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.23.16 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
I accessed the "Load Balancers" page through the left sidebar and clicked on the load balancer I had previously created: <br/>
<img src="images/Screenshot 2024-09-24 at 9.26.59 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.27.08 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
I scrolled down to locate the security tab for this load balancer and updated its security group to the Travel Agency LoadBalancer security group that I had created earlier: <br/>
<img src="images/Screenshot 2024-09-24 at 9.29.47 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.30.16 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.23.16 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
I copied the DNS name of the load balancer and pasted it into a new browser tab: <br/>
<img src="images/Screenshot 2024-09-24 at 9.38.50 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.39.18 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<h3 align="center">Configuring Health Checks</h3>

<p align="center">
I navigated to the target groups page, selected the "TravelAgencyWebServers" target group, and then clicked on the "health checks" tab: <br/>
<img src="images/Screenshot 2024-09-24 at 9.42.12 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.39.18 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Edits Applied to Health Check Setting:
- Changed Health Check Protocol to HTTP: Ensures compatibility with web applications.
- Reduced Healthy Threshold to 5: Speeds up routing to stable instances.
- Lowered Unhealthy Threshold to 2: Quickly removes failing instances.
- Shortened Health Check Interval to 5 Seconds: Allows faster detection of server issues. <br/>
<img src="images/Screenshot 2024-09-24 at 9.45.50 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.46.04 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.49.41 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<h3 align="center">Adding Subnets to the Auto Scaling Group & Testing </h3>

<p align="center">
Navigated to the Auto Scaling Groups and updated the network settings, adding the Private Subnet 1 from availability zone us-east-1a: <br/>
<img src="images/Screenshot 2024-09-24 at 9.51.39 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.52.16 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
I navigated back to the instances, then terminated the running instance. Changing the subnet alone does not trigger an automatic rebuild of instances within the Auto Scaling group. However, terminating the instance reduces the count below the group's minimum, prompting the Auto Scaling group to launch a new instance in the private subnet: <br/>
<img src="images/Screenshot 2024-09-24 at 9.54.44 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 9.55.51 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
New instance is automatically created: <br/>
<img src="images/Screenshot 2024-09-24 at 10.00.13 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
I navigated to the Auto Scaling Group (ASG), selected the "TravelAgencyWebServer" ASG, and then went to the "Activity" tab. From there, I scrolled down to view the activity history. This is another place that shows the new instance being created after the other was terminated: <br/>
<img src="images/Screenshot 2024-09-24 at 10.03.10 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
In the same ASG, I went to the "Details" tab, scrolled down to the network section, and added Private Subnet 2 from availability zone us-east-1b to the Auto Scaling Group (ASG): <br/>
<img src="images/Screenshot 2024-09-24 at 10.05.41 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 10.06.27 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
I went to the "Details" tab, scrolled down to the network section, and added Private Subnet 2 from availability zone us-east-1b to the Auto Scaling Group (ASG): <br/>
<img src="images/Screenshot 2024-09-24 at 10.05.41 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 10.06.27 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
I edited the group details to manually adjust the desired capacity. This allows for testing the Auto Scaling group’s behavior. Increasing the desired capacity, as long as it remains below the maximum limit, will trigger the launch of additional instances to meet the new desired capacity: <br/>
<img src="images/Screenshot 2024-09-24 at 10.08.46 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 10.09.07 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-24 at 10.12.07 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Added Private Subnet 3 from availability zone us-east-1c to the Auto Scaling Group (ASG) & changed the desired capacity to 3 (steps not shown, repeat of the above steps). More instances were created, 1 instance in each availability zone: <br/>
<img src="images/Screenshot 2024-09-24 at 10.26.19 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>
