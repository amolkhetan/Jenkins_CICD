# CIC Pipeline for flask application
This repository contains a simple Python Flask web application integrated with a Jenkins CI/CD pipeline. The pipeline automates **build**, **test**, **deploy**, and **Slack notifications** on every GitHub push.

---

## 🛠️ Tech Stack

- **Flask** – Python micro web framework
- **Pytest** – Unit testing framework
- **Jenkins** – Automation server for CI/CD
- **Slack Webhook** – Notification system

---


## 🔁 Jenkins CI/CD Workflow
Using Multi branch pipeline for this. Webhooks can also be using for code commit scanning.
### 🎯 Trigger
- Automatically triggered when code is pushed to the `main` branch via GitHub Webhook.

### 📋 Pipeline Stages

| Stage   | Description                                  |
|---------|----------------------------------------------|
| Poll    | Scan Git Repo for commits                    |
| Build   | Creates virtual environment, installs deps   |
| Test    | Runs unit tests using pytest                 |
| Deploy  | Starts Flask app if tests pass               |
| Notify  | Sends status to Slack channel                |

---
**1.	Setup:**
   - Launch an EC2 machine
     <img width="1912" height="974" alt="image" src="https://github.com/user-attachments/assets/f7ba71ec-5a31-4806-bd6a-d040bdd2e974" />

   - Run Below commands to install jenkins on newly launch machine.

      sudo apt update
     #Java to be installed for Jenkins as it is java based application
     sudo apt install openjdk-17-jdk -y
     wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
     sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
     sudo apt update
     sudo apt install jenkins -y
     sudo systemctl start jenkins
     sudo systemctl enable Jenkins 

     sudo apt install python3-full python3-pip
     python3 -m venv /opt/jenkins_venv
     source /opt/jenkins_venv/bin/activate
     pip install -r requirements.txt

    <img width="1291" height="279" alt="image" src="https://github.com/user-attachments/assets/1f4ba731-09e8-4537-933b-4dfaf9f69288" />

    <img width="1918" height="937" alt="image" src="https://github.com/user-attachments/assets/0f54b065-f6e4-4ea4-b0dc-3626583c2d36" />

**Issues Faced: **
  1. java 11 didnt worked  - Used java 17
  2. python version not supported - used full version
  3. After install url was not accessible using publicip on 8080 --> enabled port 8080 in security inbound rule

<img width="1349" height="728" alt="image" src="https://github.com/user-attachments/assets/f4674878-31fb-4f1f-bdc7-44592bf33ad9" />
<img width="1680" height="944" alt="image" src="https://github.com/user-attachments/assets/9fc5750d-efce-4d3c-a5f5-0582a5d1d688" />
<img width="1919" height="599" alt="image" src="https://github.com/user-attachments/assets/f2b69c74-96ae-4213-ab5a-a867a08f284a" />

**2. Source Code:**
I forked my repo from one of my batchmate's git hub and there were no link given
<img width="1036" height="334" alt="image" src="https://github.com/user-attachments/assets/b8969f01-1f13-4f45-9ab3-0b2816d18605" />

**3. Jenkins Pipeline:**
Jenkins file is present in repo

<img width="1549" height="899" alt="image" src="https://github.com/user-attachments/assets/fa19dec2-2dd7-4d38-979f-556d7d4968d0" />

**4. Notification**
<img width="1843" height="397" alt="image" src="https://github.com/user-attachments/assets/9e0edbdc-6a56-4a71-8323-4018526c09fd" />




**5. 📂 Project Structure**
<img width="462" height="165" alt="image" src="https://github.com/user-attachments/assets/39147e84-75fd-424f-a139-5426bec27af4" />



**6. Polling Log**

<img width="1887" height="837" alt="image" src="https://github.com/user-attachments/assets/a01757ba-4d0f-4132-af77-25c063325be7" />

```

