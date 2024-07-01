# STATIC WEBSITE IMPLEMENTATION

## Overview
This guide helps you create and configure index.html, styles.css, and optionally script.js files using the Vim editor on AWS EC2 instance. After setting up your files, Apache is configured to serve your static website, which you can verify and access through a web browser.

### Components

* **Linux**: The operating system on which the stack runs. Linux is chosen for its stability, security, and widespread support.
* **Apache**: The web server software. It is known for its high performance, rich feature spirit, stability, simple configuration and low resources consumption



## Step 1- Preparing prerequisite

1. **Launch an ec2 instance**:

   - Sign in to AWS management console

   - Navigate to EC2 dashboard.

   - Click on "Launch instance" and choose Ubuntu Server 20.04 LTS as the operating system
![Screenshot (359)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/5dbae436-04f0-4461-ac28-02a454048271)

2. **Configure Instance Details:**

    - Choose instance type, network, subnet, and other required settings.

3.  **Add Storage**

    - Allocate storage space for according to your requirement

4.  **Add Tags:**

    - Optionally, add tags for better organization

5.  **Configure Security Group**

    - Create a new security group or use an existing one.
    - Allow inbound traffic on port 80 (HTTP, 433 (HTTPS), 22 (SHH) from your IP address
![Screenshot (374)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/d37ea158-3613-44e5-b463-7e4e3bcf321a)

6. **Review and launch:**

  - Review the configuration and launch the instance.

![Screenshot (361)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/99b9186c-e826-4993-86bb-8c2ce3d6b4c8)

7. **Connect to the Instance**

   - use Window terminal to connect to the instance via SSH.

8.  **Grant permission for the private key and SSH into the instance**

   `chmod 400 my-ec2-key.pem`

   `ssh -i "my_ec2-key.pem" 51-20-2-201.`

![Screenshot (362)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/c7f1c75a-91ce-47cc-a6b3-c030d7cf0b14)


### Step 2- INSTALLING APACHE2
1. **Update package repository**
```
sudo apt update
```
![Screenshot (363)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/d640c31f-ac22-4392-9e9a-23b02542591b)

2. **install Apache**
```
sudo apt install apache2
```
3. **Enable and verify that apacche2 is successfullly running as a service on the OS**
```
sudo systemctl enable apache2
sudo systemctl status apache2
```
If it is green and running, Apache2 is successfully installed
![Screenshot (364)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/7b12d61e-104c-4b32-bde0-922bec7b4676)
4. 4.The server is running and can be accessed locally in the ubuntu shell by running the command below:
```
curl http://localhost:80
OR
curl http://127.0.0.1:80
```
![Screenshot (365)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/b5352d8e-8f3b-4f7b-a9ea-5556e27883f4)


 ### Step 3-  Navigate to the Web Root Directory
 1. **Typically, Apache serves files from /var/www/html/. Navigate to this directory:**
```
cd /var/www/html/
```
2. **Create and Edit index.html with Vim**
   ```
   vim index.html
   ```
3. **Edit index.html file**
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Static Website</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Welcome to My Website</h1>
    </header>
    <main>
        <section>
            <h2>About Me</h2>
            <p>Hello, I'm oluwasegun, also known as Shantel.</p>
        </section>
        <section>
            <h2>HNG Internship</h2>
            <p>Check out the latest opportunities at the <a href="https://hng.tech" target="_blank">HNG Internship</a>.</p>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 oluwasegun. All rights reserved. Contact: Oluwasegun2557@gmail.com</p>
    </footer>
</body>
</html>
```
![image](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/6fa82947-a8aa-4940-854f-e5afd3373385)

4. **Create styles.css file**
```
vim styles.css
```
Edit anc copy the following code below into the css file.
```
/* Reset default browser styles */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* Basic styling */
body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    background-color: #f0f0f0;
    padding: 20px;
}

header {
    background-color: #333;
    color: #fff;
    padding: 10px 20px;
    text-align: center;
}

header h1 {
    font-size: 2em;
}

main {
    margin: 20px 0;
}

section {
    padding: 20px;
    background-color: #fff;
    margin-bottom: 20px;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

section h2 {
    color: #333;
    font-size: 1.5em;
    margin-bottom: 10px;
}

footer {
    text-align: center;
    padding: 10px 0;
    background-color: #333;
    color: #fff;
    position: fixed;
    width: 100%;
    bottom: 0;
}
```

![Screenshot (370)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/9bddf4a3-ae93-4b55-9c6d-6f516723dce0)

5. **1.5. Create and Edit script.js**
Create a new script.js file and open it with Vim
```
 vim script.js
```
copy and paste the code below into the script.js file:
```
// Display a welcome message in the console
console.log('Hello from Oni Oluwasegun Timileyin');

// Function to change the background color
function changeBackgroundColor() {
    const colors = ['#f0f0f0', '#c8e6c9', '#ffccbc', '#d1c4e9', '#ffeb3b'];
    const randomColor = colors[Math.floor(Math.random() * colors.length)];
    document.body.style.backgroundColor = randomColor;
}

// Add event listener to the button
document.getElementById('colorButton').addEventListener('click', changeBackgroundColor);

// Add event listener to the HNG section
document.getElementById('hng').addEventListener('click', function() {
    alert('You clicked on the HNG Internship section!');
});
```
![image](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/b8ac38cd-59db-4ae1-9bb4-b7102263a041)

6. **Configuring Apache to Serve Your Website**
   - start apache2 service
```
sudo systemctl start apache2
```
**Verify Apache status**
Check the status of Apache to ensure it's running without errors:
```
sudo systemctl status apache2
```
![Screenshot (372)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/2b0b3567-28ba-49a4-86aa-a54cbad78c0e)

### Accessing Your Website
Open a web browser and enter your EC2 instance's public IP address or domain name. You should see your static website rendered with the content you created.
![Screenshot (373)](https://github.com/Dreyshantel/Devops-Projects/assets/109143806/94d3441c-db6a-4fe3-b653-36a15888bb81)


Now we have successfully launch our static website on the internet using Apache2 web server and linux OS.
