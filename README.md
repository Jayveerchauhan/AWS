# 🚀 Launch and Connect to an AWS EC2 Instance

This guide walks you through the full process of launching an EC2 instance and connecting to it using both the AWS Console and SSH from your local system.

---

## 🧱 Step 1: Sign In to AWS Console

Go to [https://aws.amazon.com](https://aws.amazon.com) and log in to your AWS account.

(<img width="602" height="307" alt="Picture1" src="https://github.com/user-attachments/assets/f2ac3b18-3bdc-4dd9-bb4b-0a13c6cc04c4" />

---

## 🖥️ Step 2: Launch a New EC2 Instance

1. Navigate to **EC2 → Instances → Launch Instance**
2. Fill out:
   - **Name**: `MyUbuntuInstance`
   - **OS Image**: Choose Ubuntu 22.04 LTS
   - **Instance type**: `t2.micro` (Free Tier eligible)
   - **Key pair**: Create or select `.pem` key
   - **Network settings**: Allow SSH (port 22)

📸 ![Step 2 - Launch Instance](https://via.placeholder.com/800x400?text=Launch+Instance+Screen)

Click **Launch Instance** to start.

---

## 📡 Step 3: Verify Instance is Running

Once launched:
- Go to **Instances**
- Wait for `Instance state: Running`
- Copy the **Public IPv4 DNS** (you'll use this to connect via SSH)

📸 ![Step 3 - Instance Running](https://via.placeholder.com/800x400?text=Instance+Running)

---

## 🌐 Step 4: Connect Using EC2 Instance Connect (Browser SSH)

1. Select your instance → Click **Connect**
2. Choose **EC2 Instance Connect**
3. Click **Connect** to launch browser terminal

📸 ![Step 4 - EC2 Instance Connect](https://via.placeholder.com/800x400?text=Browser+SSH+Connection)

---

## 💻 Step 5: Connect Using SSH (from Terminal)

### ✅ A. Move `.pem` file to a safe location:

```bash
mv ~/Downloads/hellokey.pem ~/.ssh/
