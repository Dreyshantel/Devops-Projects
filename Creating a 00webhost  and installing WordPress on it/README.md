# Create an account on 00webhost  and installing WordPress on it. 

This project is a documentation guide on how to create an account on 000webhost and installing WordPress on it using an AWS EC2 instance. It involves several steps, below is a complete step-by-step guide to walk you through the process.
### Step 1: Creating an Account on 000webhost
1. **Visit 000Webhost**
   - Open your web browser and go to 000webhost.
2. **Sign up**
   -Click on the "Sign Up For Free" button.
   -Fill in the required details such as your name, email address, and password.
   -Alternatively, you can sign up using your Google or Facebook account.
![Screenshot (268)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/bfd153d1-891c-4cb2-9ba8-c68a65bb6607)

3. **Email Verification:**
   -Check your email inbox for a verification email from 000webhost. 
   -Click on the verification link to activate your account.
   -Part 2: Launching an AWS EC2 Instance

4. **Login to 000webhost:**
  - Once registered, log in to your 000webhost account using your credentials.
  - Set Up Your Website:

  - After logging in, you can set up your website by following the prompts provided by 000webhost.
  - You can choose to create a new website or migrate an existing one.

   ### Step 2: Launch AWS EC2 Instance

1. **Launch an ec2 instance**:

   - Sign in to AWS management console

   - Navigate to EC2 dashboard.

   - Click on "Launch instance" and choose Ubuntu Server 20.04 LTS as the operating system
   ![Screenshot (269)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/b1fc4cb9-645f-42d3-9272-aea8375f2201)


2. **Configure Instance Details:**

    - Choose instance type, network, subnet, and other required settings.

3.  **Add Storage**

    - Allocate storage space for according to your requirement

4.  **Add Tags:**

    - Optionally, add tags for better organization

5.  **Configure Security Group**

    - Create a new security group or use an existing one.
    - Allow inbound traffic on port 80 (HTTP), port 22 (SHH) from your IP address
![Screenshot (270)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/fdd69530-641c-42bd-a85d-687e98394bb8)

6. **Review and launch:**

  - Review the configuration and launch the instance.
    ![Screenshot (271)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/53003358-87fb-40e5-a11d-5cf1561d3e6a)
   
7. **Connect to Your EC2 Instance:**
    - SSH into Your Instance:
    - Once your instance is running, connect to it via SSH using a terminal or an SSH client.
      ![Screenshot (273)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/1df9440f-d300-4522-956c-2a651dc7e471)


### Step 3: Install Wordpress
1. **Update package repository**
   ```
   sudo apt update
   sudo apt upgrade
   ```
   ![Screenshot (276)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/f84004ea-4287-497b-b4c2-59e197918732)
   ![Screenshot (277)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/06a66036-edff-44ee-94a3-82c07a6d45c3)

2. **Install LAMP Stack (Linux, Apache, MySQL, PHP):**
   A lamp stack is an open source software stack commonly used in creating a web page. The lamp stack is known for it's flexibility, stability and cost effectiveness, making it the best choice in creating web pages. The acronym LAMP stands for:

- Linux: An operating system used to host the web server
- Apache: A web server softer which server the web pages to users browser
- MySQL: Relational database management system (RDBMS) used to store and manage data
- PHP: a server-side scripting language used to create a dynamic web pages

install lamp stack using the following command below:
```
sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql
```
![Screenshot (276)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/c3b55507-fec1-4191-8d89-98bb3a51047f)
![Screenshot (277)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/b73d022f-3e53-42b0-9157-1fa2e86ae1e3)

3. **Create MySQL Database and User:**
