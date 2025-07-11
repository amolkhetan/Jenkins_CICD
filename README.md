# Jenkins CI CD pipeline for flask application



## 🚀 Flask CI/CD Pipeline with Jenkins

This repository contains a simple Python Flask web application integrated with a Jenkins CI/CD pipeline. The pipeline automates **build**, **test**, **deploy**, and **Slack notifications** on every GitHub push.

---

## 🛠️ Tech Stack

- **Flask** – Python micro web framework
- **Pytest** – Unit testing framework
- **Jenkins** – Automation server for CI/CD
- **Slack Webhook** – Notification system

---


## 🔁 Jenkins CI/CD Workflow

### 🎯 Trigger
- Automatically triggered when code is pushed to the `main` branch via GitHub Webhook.

### 📋 Pipeline Stages

| Stage   | Description                                  |
|---------|----------------------------------------------|
| Build   | Creates virtual environment, installs deps   |
| Test    | Runs unit tests using pytest                 |
| Deploy  | Starts Flask app if tests pass               |
| Notify  | Sends status to Slack channel                |

---

<img width="400" height="570" alt="Jenkins_Build_Test_Deploy" src="https://github.com/user-attachments/assets/43a0fed0-7b8a-4208-a79e-ae50768904f7" />

---

<img width="800" height="610" alt="image" src="https://github.com/user-attachments/assets/64e54747-bb57-46cf-b92a-2fa55de565cc" />


---

## Notification

<img width="593" height="93" alt="Screenshot from 2025-07-11 14-04-23" src="https://github.com/user-attachments/assets/72e04dcf-c423-41e1-a7b7-381922bcf545" />


## 📂 Project Structure

<img width="462" height="165" alt="image" src="https://github.com/user-attachments/assets/39147e84-75fd-424f-a139-5426bec27af4" />


## Polling Log
```
This page captures the polling log that triggered this build.

Started on Jul 11, 2025, 7:44:24 AM
Started by event from 140.82.115.12 ⇒ http://jenkins.munisekar.com:8080/github-webhook/ on Fri Jul 11 07:44:24 UTC 2025
Using strategy: Default
[poll] Last Built Revision: Revision b46fe2f4fc71bd696a5d36020dac05aaffc25ce5 (refs/remotes/origin/main)
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
No credentials specified
 > git --version # timeout=10
 > git --version # 'git version 2.39.5'
 > git ls-remote -h -- https://github.com/munisekar-py/Jenkins_CICD.git # timeout=10
Found 1 remote heads on https://github.com/munisekar-py/Jenkins_CICD.git
[poll] Latest remote head revision on refs/heads/main is: 7f6c43a90752d969fdabbe3d782ff33739969297
Done. Took 0.38 sec
Changes found

```
---

## License

[MIT](https://choosealicense.com/licenses/mit/)
