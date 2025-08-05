# 🚀 Launching and SSH an EC2 Instance on AWS – Step-by-Step Guide

This guide explains how to launch a virtual server (EC2 instance) using the AWS Management Console.  
Perfect for beginners, using **Free Tier** eligible resources.

---

## 📌 Prerequisites

- An active AWS account → [Create AWS Account](https://portal.aws.amazon.com/billing/signup)
- Logged in as **Root user** or IAM user with EC2 permissions
- Basic knowledge of SSH and key pairs
  
- <img width="602" height="307" alt="Picture1" src="https://github.com/user-attachments/assets/1e6e5930-85ba-4235-9e06-80c74eee18f5" />


---

## ✅ Step 1: Open EC2 Dashboard

- Go to AWS Console → Services → Select **EC2**
- [Step 1 – EC2 Dashboard]
- <img width="602" height="275" alt="Picture2" src="https://github.com/user-attachments/assets/76430dad-5e8e-4a32-8f9d-95269fbd7b34" />


---

## ✅ Step 2: Click “Launch Instance”

Click the orange **Launch Instance** button to start the setup.
- [Step 2 – Launch Instance]
- <img width="602" height="278" alt="Picture3" src="https://github.com/user-attachments/assets/9388128a-c5d7-4f38-a4b8-1c2267879b44" />


---

## ✅ Step 3: Set Instance Name

Enter a name for your instance (e.g., `demo-server`) in the **Name and tags** section.
- [Step 3 – Set Name]
- <img width="602" height="260" alt="Picture4" src="https://github.com/user-attachments/assets/ec76818f-6264-4429-aa2d-3163ceec0116" />


---

## ✅ Step 4: Choose Amazon Machine Image (AMI)

Select an OS image. We are using:
- **Ubuntu Server 24.04 LTS (64-bit x86)**  
- Free tier eligible
- [Step 4 – Choose AMI]
- <img width="602" height="280" alt="Picture5" src="https://github.com/user-attachments/assets/1f95fc46-5c0f-432a-92fe-610f28ed8720" />


---

## ✅ Step 5: Choose Instance Type

Select:
- **t2.micro**
- 1 vCPU, 1 GiB RAM
- **Free tier eligible**
- [Step 5 – Instance Type]
- <img width="602" height="276" alt="Picture6" src="https://github.com/user-attachments/assets/354ca1ee-eeda-462c-afb4-739587ece2be" />


---

## ✅ Step 6: Create or Select Key Pair

Create a new key pair:
- Name: `hellokey`
- Type: RSA
- Format: `.pem` (for OpenSSH)

Download and save the file securely!
- [Step 6 – Key Pair]
- <img width="602" height="481" alt="Picture7" src="https://github.com/user-attachments/assets/bdf683fd-d7f1-4b7f-a870-091cb447bfe6" />
- <img width="602" height="273" alt="Picture8" src="https://github.com/user-attachments/assets/0f8b0d41-082c-4055-b0af-c32c417176bf" />



---

## ✅ Step 7: Configure Network & Firewall

- Enable auto-assign public IP
- Create a new security group
- Allow:
  - **SSH (22)** – from Anywhere
  - **HTTP (80)** – from Anywhere
  - **HTTPS (443)** – from Anywhere (optional)

> ⚠️ 0.0.0.0/0 allows access from all IPs. Use caution.
- [Step 7 – Network]
- <img width="602" height="276" alt="Picture9" src="https://github.com/user-attachments/assets/2c4d6413-2f0d-43dc-8900-295c9053d7f5" />


---

## ✅ Step 8: Configure Storage

- 8 GiB **gp3** EBS root volume
- Free tier eligible
- [Step 8 – Storage]
- <img width="602" height="279" alt="Picture10" src="https://github.com/user-attachments/assets/65cb4907-0e9c-4f05-a1a4-7e892d255549" />


---
## ✅ Step 9: Launch Your Instance

- Click **Launch Instance**  
- Instance will be created and launched  
  -[Step 9]
  - <img width="602" height="280" alt="Picture11" src="https://github.com/user-attachments/assets/04ef31bb-0370-4828-b079-8c69ed2f3b4e" />

---

## ✅ Step 10: Verify the Instance Is Running

- Go to **EC2 Dashboard → Instances**
- Check instance state is **Running** and has **Public IPv4 DNS**  
  -[Step 10]
  - <img width="602" height="277" alt="Picture12" src="https://github.com/user-attachments/assets/81cd984a-af66-4e03-a127-963a4f629f44" />
  -<img width="602" height="194" alt="Picture13" src="https://github.com/user-attachments/assets/35fcb2db-f246-4efb-849c-0556aa945d7a" />



---

## ✅ Step 11: Connect Using EC2 Instance Connect

- Click your instance → **Connect**  
- Choose EC2 Instance Connect  
- Username: `ubuntu`  
- Click **Connect**  
- [Step 11]
- <img width="602" height="265" alt="Picture14" src="https://github.com/user-attachments/assets/8838a731-fced-47ba-aba2-7d6186526502" />


---

## ✅ Step 12: Use the Terminal

You can now run commands in the instance:

```bash
# Check system info
uname -a

# Update packages
sudo apt update

# Create file
nano app.txt

# View file
cat app.txt
```
-<img width="602" height="279" alt="Picture15" src="https://github.com/user-attachments/assets/3148a889-c36b-45ea-9355-a38826122e7d" />
-<img width="602" height="274" alt="Picture16" src="https://github.com/user-attachments/assets/825d852f-e10f-462c-9d39-45e86791146a" />
-<img width="602" height="274" alt="Picture17" src="https://github.com/user-attachments/assets/d0a3e9f4-6aa1-4405-a953-2e832c8bbeb9" />

# 🔐 Connecting to EC2 via SSH
## ✅ Step 14: Connect to EC2 Instance via SSH (Local Terminal)

Instead of using EC2 Instance Connect (browser), you can also connect using your local terminal (Linux/Mac) or Git Bash (Windows).

### 🔧 Prerequisites

- You have downloaded the `.pem` file (key pair) when launching the instance (e.g., `hellokey.pem`)
- You have `chmod` set to restrict the key's permissions
- <img width="602" height="311" alt="Picture18" src="https://github.com/user-attachments/assets/e50afac8-fcf1-42d5-835b-0435aa15fee3" />

### 🔐 Set Key Permissions (Run Once):

```bash
chmod 400 hellokey.pem
```
🔗 SSH Command Format
```
ssh -i "hellokey.pem" ubuntu@<Public-IP>
```
- Replace <Public-IP> with the EC2 instance’s IPv4 Public IP
- Example:
```
ssh -i "hellokey.pem" ubuntu@13.233.177.4
```
- <img width="602" height="147" alt="Picture19" src="https://github.com/user-attachments/assets/bcdae74e-3227-4647-bfb8-dd7427a85679" />
## ✅ Step 15: Create & Read a File Inside EC2 (via SSH)
- Once inside your EC2 terminal:
  
# Create directory
```
mkdir jayveer
cd jayveer
```

# Create a text file
```
touch app.txt
```

# Write text to the file
```
echo "Hello this is Jayveer Chauhan" > app.txt
```

# Read the file
```
cat app.txt
```
## 🧼 Step 16: Terminate Your EC2 Instance
To avoid AWS charges, terminate the instance after use:

Go to EC2 → Instances

Select your instance

Click Instance State → Terminate

Confirm termination

📸 Terminate confirmation prompt:
- <img width="602" height="275" alt="Picture20" src="https://github.com/user-attachments/assets/58b67700-e341-4685-9c95-d4971b92a9e8" />

---

### ✅ Next Step:
Let me know if you'd like me to **generate a `README.md` file** containing all steps including:




