---
title: "Local Development Environment"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.2.2. </b> "
---

Install the following tools locally:

| Tool            | Purpose |
|-----------------|---------|
| AWS CLI v2      | AWS access and automation |
| Python 3.12     | Lambda runtime and ML training |
| Node.js ≥ 18    | React frontend |
| Git             | Version control |
| Postman         | API testing |
| VS Code/Pycharm | Editor |

#### Configure the AWS CLI

```bash
aws configure
```

Enter:

```text
AWS Access Key ID: <your key>
AWS Secret Access Key: <your secret>
Default region name: ap-southeast-1
Default output format: json
```

Verify:

```bash
aws s3 ls
```

#### Python virtual environment

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
pip install -r requirements.txt
```

