# MOHAMMED_ELGHANAM_SONARQUBE

Welcome to the **SonarQube Setup Guide**! This documentation will walk you through setting up and running **SonarQube** locally using Docker to analyze and monitor your project's code quality.

---

## 🚀 Prerequisites

Before starting, ensure you have the following:

- 🐳 **Docker** installed on your system.
- 🔌 Ensure port **9000** is available on your machine for SonarQube.

---

## 🛠 SonarQube Setup

### 1️⃣ Pull the SonarQube Image

First, pull the official **SonarQube** image from Docker Hub:

```bash
docker pull sonarqube
```

### 2️⃣ Run the SonarQube Container

Run the SonarQube container and expose it on port **9000**:

```bash
docker run -d --name sonarqube -p 9000:9000 sonarqube
```

Now, SonarQube is up and running! You can access the dashboard by visiting:

🌐 [http://localhost:9000](http://localhost:9000)

---

## 🔍 Scanning Your Project

### 3️⃣ Pull the Sonar Scanner CLI

To scan your project's source code, you need the **Sonar Scanner CLI**. Pull the Docker image for the scanner:

```bash
docker pull sonarsource/sonar-scanner-cli
```

### 4️⃣ Run Sonar Scanner

Run the Sonar Scanner from your project directory to analyze the code and send it to SonarQube:

```bash
docker run --rm \
  -e SONAR_SCANNER_OPTS="-Dsonar.host.url=http://localhost:9000" \
  -v "$(pwd):/usr/src" \
  sonarsource/sonar-scanner-cli
```

This will connect to the SonarQube instance running on your local machine.

---

## 📁 Configuration: `sonar-project.properties`

Ensure you have a `sonar-project.properties` file in the root of your project. This file configures the analysis settings for SonarQube. Here’s an example:

```properties
# Project identification
sonar.projectKey=your_project_key
sonar.projectName=Your Project Name
sonar.projectVersion=1.0

# Path to the source code
sonar.sources=./src

# Exclude test files and unnecessary assets
sonar.exclusions=**/test/**, **/*.spec.js

# SonarQube server URL
sonar.host.url=http://localhost:9000

# Language settings (for JavaScript, for example)
sonar.language=js
```

---

## ✅ Results

After running the scan, open your browser and navigate to:

🌐 [http://localhost:9000](http://localhost:9000)

From here, you can explore code metrics, bugs, vulnerabilities, and code smells!

---

By following these steps, you will have a fully operational SonarQube instance to continuously analyze and improve your project’s code quality.

---

💡 **Pro Tip**: Customize the `sonar-project.properties` file to fit your project's needs, excluding unnecessary files and directories from the scan.