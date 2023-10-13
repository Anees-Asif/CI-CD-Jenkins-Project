

1. **Launch an EC2 Instance:**
   You'll run Jenkins on an Amazon EC2 (Elastic Compute Cloud) instance. Follow these steps to create an EC2 instance:
   - Log in to the AWS Management Console.
   - Go to the EC2 Dashboard.
   - Click "Launch Instance."
   - Choose an Amazon Machine Image (AMI) that suits your needs. Consider using an Amazon Linux, Ubuntu, or a Jenkins-specific AMI.
   - Select an instance type based on your requirements. A t2.micro instance is a good starting point for small projects.
   - Configure instance details like the number of instances, VPC settings, and security groups.
   - Review and configure storage options if needed.
   - Add tags to your instance for easy identification.
   - Configure the security group to allow SSH (port 22) and HTTP (port 80) access.
   - Review your settings and launch the instance. You will need to create or select an existing key pair for SSH access.

2. **Connect to Your EC2 Instance:**
   - Use an SSH client to connect to your instance. You'll use the key pair you created during the instance launch.
   - The connection command may look like this:
     ```
     ssh -i your-key.pem ec2-user@your-instance-ip
     ```

3. **Install Jenkins:**
   On your EC2 instance, you need to install Jenkins. The exact commands may vary depending on your instance's operating system. For example, on Ubuntu, you can use the following commands:

   ```bash
   sudo apt update
   sudo apt install openjdk-11-jdk
   wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
   sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
   sudo apt update
   sudo apt install jenkins
   ```

   After installing Jenkins, start the Jenkins service:

   ```bash
   sudo systemctl start jenkins
   sudo systemctl enable jenkins
   ```

4. **Access Jenkins:**
   Jenkins is accessible through a web interface. Use your browser to access Jenkins by navigating to `http://your-instance-ip:8080` (replace `your-instance-ip` with your actual instance IP address). You'll need to retrieve the Jenkins unlock key from the server's log files to complete the initial setup. `sudo cat /var/lib/jenkins/secrets/initialAdminPassword`

5. **Admin account**

    You can either create an account or skip and log in as admin.


## Creating an environment

This is how we will configure our jenkins, but for this case we will use the suggested plugins as these are all we need.

## Creating pipeline.



