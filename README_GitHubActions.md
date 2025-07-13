# CIC Pipeline for flask application
This repository contains a simple Python Flask web application deployment via GitHub Actions. The pipeline automates **build**, **test**, **deploy to Staging**, and **deploy to Production** on every GitHub push events.

---

## 🛠️ Tech Stack

- **Flask** – Python micro web framework
- **Pytest** – Unit testing framework

---


## 🔁 GitHub Workflow
Have built workflow file from Actions options to define the stages


### 📋 Pipeline Stages

| Stage   | Description                                  |
|---------|----------------------------------------------|
| Build   | Creates virtual environment, installs deps   |
| Test    | Runs unit tests using pytest                 |
| Deploy  | Deploy to Staging and Production             |

---

**Source Code Pipeline/Work Flow:**
Workflow defination is mentioned/defined in https://github.com/amolkhetan/Jenkins_CICD/blob/main/.github/workflows/main.yml

<img width="1905" height="710" alt="image" src="https://github.com/user-attachments/assets/281fdcc0-9b58-4c76-8e3e-53be65da4063" />


**Scretes**
<img width="1909" height="828" alt="image" src="https://github.com/user-attachments/assets/6ff0f7b5-861f-4690-8fb6-7bacaa2e95c1" />
