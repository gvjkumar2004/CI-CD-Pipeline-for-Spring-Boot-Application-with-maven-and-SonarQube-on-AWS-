# CI/CD Pipeline for Spring Boot Application

## Overview
Automated CI/CD pipeline for a Spring Boot application using Jenkins, Maven, SonarQube, and AWS EC2.

## Prerequisites
- **Jenkins Server:**
  - Java 17 installed
  - Plugins: Git, Maven, SSH, SonarQube
  
- **Deployment Server (AWS EC2):**
  - Java 17 installed
  - SSH access configured

- **SonarQube:**
  - Running on port 9000
  - Access token generated

## Pipeline Steps
1. **Checkout Code:** Jenkins pulls code from GitHub.
2. **Build:** Compiles and packages the application using Maven.
3. **Code Quality:** SonarQube scans the code.
4. **Deploy:** Copies the JAR file to the EC2 instance and runs it.

## Setup Instructions
1. **Jenkins:**
   - Install necessary plugins.
   - Configure SonarQube server in Jenkins.

2. **Deployment Server:**
   - Ensure Java 17 and SSH are set up.

3. **SonarQube:**
   - Generate a token and configure Jenkins for code analysis.

## Execution
Run the Jenkins pipeline to automate the deployment of your Spring Boot application.
