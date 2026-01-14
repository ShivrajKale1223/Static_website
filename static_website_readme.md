# Static Website Deployment on AWS EC2 using NGINX

This README explains how to deploy a static website on an AWS EC2 instance using Amazon Linux 2023 and NGINX. It also includes screenshots demonstrating each step.



##  Step 1: Launch EC2 Instance
- Choose **Amazon Linux 2023** AMI.
- Use a **t3.micro** instance.
- Create or use an existing key pair.
- Enable inbound rules for **HTTP (80)** and **SSH (22)**.

### Screenshot
EC2 Instance Summary
![alt text][def]



##  Step 2: Connect to EC2 via SSH
```bash
ssh -i "north-v-key.pem" ec2-user@44.213.71.152
```

### Screenshot
SSH Connected
![alt text](<Screenshot 2025-11-24 143336.png>)


##  Step 3: Install NGINX
```bash
sudo dnf install nginx -y
sudo systemctl start nginx
sudo systemctl status nginx
```

### Screenshot
NGINX Installation
![alt text](<Screenshot 2025-11-24 143824.png>)
NGINX Running
![alt text](<Screenshot 2025-11-24 144329.png>)



##  Step 4: Upload Website Files to EC2 Using SCP
```bash
scp -i "north-v-key.pem" -r templatemo_602_graph_page/ ec2-user@44.213.71.152.compute-1.amazonaws.com:/home/ec2-user/
```

### Screenshot
File Upload via SCP
![alt text](<Screenshot 2025-11-24 151458.png>)



##  Step 5: Move Files to NGINX Web Directory
```bash
sudo cp -r templatemo_602_graph_page/* /usr/share/nginx/html/
```

### Screenshot
Copying Files
![alt text](<Screenshot 2025-11-24 152259.png>)



##  Step 6: Access the Website
Open browser:
```
http://44.213.71.152
```

### Screenshot
Website Working
![alt text](<Screenshot 2025-11-24 153219.png>)

---

## 🎉 Deployment Complete!
We have successfully deployed a static website using AWS EC2 + NGINX.



##  Project Structure
```
/your_website
│── index.html
│── styles.css
│── script.js
```

---

##  Notes
- Ensure correct permissions when copying files.
- Restart NGINX if you update files:
```bash
sudo systemctl restart nginx
```

---

##  Author
This documentation was auto‑generated to assist in AWS static website deployment.




[def]: <Screenshot 2025-11-24 142041.png>
