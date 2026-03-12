# Candy Store – Node.js Deployment on AWS EC2
# Project Overview

This project demonstrates how to deploy a Node.js web application on AWS EC2.
The application serves a simple Candy Store website with static assets (HTML, CSS, images) and runs using a Node.js server.

The purpose of this project is to demonstrate cloud deployment skills required for AWS / DevOps roles.

# Tech Stack

Node.js
Express.js
Git
GitHub
AWS EC2
Linux (Amazon Linux)
npm

# AWS EC2 Setup

1. Launch an EC2 Instance

2️. Configure Security Group Ports

# Port and Purpose

1. 22 SSH Access, 
2. 80 HTTP,
3. 3000 Node.js Application.

# Deploy From Local Project → GitHub → EC2
# Step 1 – Open Terminal and Navigate to Project
cd "C:\Users\AJAY YADAV\OneDrive\Desktop\Documents\Ajay\Projects\candy-store"

# Step 2 – Initialize Git
git init
git add .
git commit -m "Initial commit of candy-store project"

# Step 3 – Connect Repository to GitHub
git remote add origin https://github.com/surajyadav29/candy-store1.git
git branch -M main
git push -u origin main

This uploads the project to GitHub.

# Step 4 – Connect to EC2 Server
ssh -i "C:\Users\AJAY YADAV\Downloads\ec2.pem" ec2-user@your-ec2-public-ip

# Step 5 – Install Required Software on 
sudo yum update -y
sudo yum install git -y
sudo yum install nodejs -y
sudo yum install libatomic -y

# Step 6 – Clone Repository on EC2
git clone https://github.com/surajyadav29/candy-store1.git
cd candy-store1

# Step 7 – Install Dependencies
npm install

This installs packages defined in package.json using npm.

# Step 8 – Start the Application
node app.js

Server will start on port 3000.

# Step 9 – Access the Application
Open in browser:

http://your-ec2-public-ip:3000

# Author

# Ajay Yadav
# Aspiring AWS / DevOps Engineer
