# Amazon Security Groups

## Lab Mission
Create security groups to govern ICMP and RDP access to AWS resources.

## Lab Duration
20–40 minutes

## Requirements
- AWS account
- Basic knowledge of AWS
- Working knowledge of the RDP tool

## Resources
- **Environment & Tools**
  - Web browser
  - RDP
- **Extra Links**
  - [AWS documentation](https://docs.aws.amazon.com/)


## Lab Task 1: Create an ICMP Security Group
In this task, you will modify the security group assigned to your instance to allow pings from your computer’s IP address only.

1. Go to [AWS](https://aws.amazon.com) and log in to your account.
2. Navigate to the **EC2 dashboard**.
3. In the EC2 dashboard, navigate to the running instances and start the instance by right-clicking it and selecting **Start instance**.

   > **Note:** Make sure the instance is running. (This may take a few minutes.)

4. In the search bar, type **security groups** and then select **Security groups**.
5. Click **Create security group**.
6. In the **Create security group** window, name the group and add a description. Then, in the **Type** dropdown menu, select `ICMP - IPv4`. Next, add `My IP` in the **Source** dropdown menu. Leave the description and tags empty. Click **Create security group** in the bottom-right corner.
7. Check the EC2 instance to make sure the security group was added. Go to the **Running instances** and select the server. Then go to the **Security** tab and look at the inbound rules.
8. Click the **Actions** dropdown at the top-right corner to modify the security groups. Then add in the newly created group for ICMP from your IP address. Make sure to add the security group and click **Save**.
9. Connect to the instance via RDP. Right-click on the instance and select **Connect**. In the window that appears, click **Get password** and upload the security key to get the password.


10. Click **Connect** in the Remote Desktop Connection window and insert the decrypted password to establish the connection. Click **Yes** when the unauthenticated connection warning appears. Leave the RDP connection open for the next task.

## Lab Task 2: Create an ICMPv4 Security Group
In this task, you will create a new security group with a rule to allow pinging the instance. Due to the default ping blocking configured in Windows Server 2016, it must be enabled in its firewall first.

1. Try to ping the instance from your host machine and notice it doesn’t get a response. The public IP of the instance can be viewed in the instances window.
2. While connected to the instance via RDP, search for **Windows Firewall with Advanced Security** and open it.
3. Navigate to **Inbound Rules** and click **New Rule...**.
4. In **Rule Type**, select **Custom**.
5. In **Program**, select **All programs**.
6. In **Protocol and Ports**, select the protocol type `ICMPv4`.
7. In **Scope**, don’t change any options.
8. In **Action**, don’t change any options.
9. In **Profile**, don’t change any options.
10. In **Name**, name the rule `ICMPv4 allow` and finish the configuration.
11. Try to ping the instance again and notice that the ping now goes through to the public IP.
12. Disconnect from the instance and stop it.
