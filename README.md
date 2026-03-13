# Deploy candy-store from GitHub repo on EC2

## Goal

Deploy a Node.js application from GitHub to an Amazon EC2 cloud server.

## Technologies Used

* **EC2** – Cloud virtual machine
* **GitHub** – Code hosting platform
* **Node.js** – JavaScript runtime environment
* **Git** – Version control system

---

# Deployment Steps

## 1️ Launch EC2 Instance

Launch an EC2 instance from the AWS console.

**EC2 = Elastic Compute Cloud**

Purpose:
Creates a virtual server in the cloud where the application will run.

---

## 2️ Configure Security Group

Allow these ports:

| Port | Purpose                    |
| ---- | -------------------------- |
| 22   | SSH (remote server access) |
| 80   | HTTP (web traffic)         |
| 3000 | Node.js application        |

---

## 3️ Open WSL Terminal

Move to the folder containing the EC2 key:

```
cd Downloads
```

---

## 4️ Connect to EC2 Server

```
ssh -i ec2.pem ec2-user@51.21.171.67
```

or

```
ssh -i "ec2.pem" ec2-user@ec2-51-21-171-67.eu-north-1.compute.amazonaws.com
```

Explanation:

* **SSH = Secure Shell**
* Creates a secure connection between your local computer and the EC2 server
* `-i ec2.pem` → private key authentication

---

## 5️⃣ Update System Packages

```
sudo yum update -y
```

Explanation:

* **sudo** → run command as administrator
* **yum** → package manager for Amazon Linux

Purpose: update server packages and security patches.

---

## 6️⃣ Install Git

```
sudo yum install git -y
```

Git allows the server to download code from GitHub.

---

## 7️⃣ Install Node.js

```
sudo yum install nodejs -y
```

Node.js runs JavaScript applications on the server.

---

## 8️⃣ Install Required Library

```
sudo yum install libatomic -y
```

Fixes errors like:

```
libatomic.so.1 missing
```

---

## 9️⃣ Verify Installation

```
node -v
npm -v
```

* `node -v` → Node.js version
* `npm -v` → Node Package Manager version

---

## 🔟 Clone GitHub Repository

```
git clone https://github.com/surajyadav29/candy-store.git
```

This downloads the project from GitHub and creates a folder:

```
candy-store
```

---

## 1️⃣1️⃣ Move Into Project Folder

```
cd candy-store
```

---

## 1️⃣2️⃣ Install Project Dependencies

```
npm install
```

**npm = Node Package Manager**

Reads the `package.json` file and installs dependencies like:

* express
* cors
* dotenv

Installed inside:

```
node_modules
```

---

## 1️⃣3️⃣ Start Application Server

```
node app.js
```

This runs the Node.js application.

Example inside app.js:

```
app.listen(3000)
```

Meaning the application runs on **port 3000**.

---

## 1️⃣4️⃣ Open Application

Open in browser:

```
http://51.21.171.67:3000
```

* `51.21.171.67` → EC2 public IP
* `3000` → application port

---

# Updating the Project

## Important Rule

| Situation                 | Command     |
| ------------------------- | ----------- |
| First deployment          | `git clone` |
| Updating existing project | `git pull`  |

---

# Deployment Workflow

### First Deployment

```
Local Computer
     │
git push
     ▼
GitHub
     │
git clone
     ▼
EC2 Server
```

---

### Updating Application

```
Local Computer
     │
git push
     ▼
GitHub
     │
git pull
     ▼
EC2 Server
```

---

# Update Code From Local Computer

```
cd "C:\Users\AJAY YADAV\OneDrive\Desktop\Documents\Ajay\Projects\candy-store"

git status
git add .
git commit -m "Updated candy store project"
git push origin main
```

Explanation:

* `git status` → check changed files
* `git add .` → stage files
* `git commit` → save changes
* `git push` → upload to GitHub

---

# Update the Project on EC2

Connect to EC2:

```
ssh -i "C:\Users\AJAY YADAV\Downloads\ec2.pem" ec2-user@16.170.232.31
```

Move to project folder:

```
cd candy-store
```

Pull latest code:

```
git pull origin main
```

Internally runs:

```
git fetch
git merge
```

Install dependencies if needed:

```
npm install
```

Restart application:

```
node app.js
```

---

# Open Application

```
http://EC2_PUBLIC_IP:3000
```
