# AWS Cloud Engineering - Hands-On Projects

Self-study labs and projects. Hands-on Amazon Web Services in a personal AWS account, documented step by step.

## Purpose

This repository is my working record of learning AWS by doing. Every lab I complete is written up as a repeatable guide, so that anyone, including future me, can follow it from a blank AWS account to a verified result. Writing each lab down forces me to understand it well enough to explain it, and the commit history shows the learning happening over time.

Each module folder contains:

- A README with the goal, prerequisites, numbered steps, a verification checklist, and cleanup instructions
- Screenshots with account details redacted
- Notes on mistakes, fixes, and what I would do differently next time

## About Me

I work in IT technical support and have more than three years of experience troubleshooting problems, supporting users, and working to service expectations in a shift-based environment. I am building cloud engineering skills alongside my job through a structured six-month cloud operations program (CloudThat) and online courses.

My foundations so far:

- **Linux administration:** hands-on practice on Rocky Linux and Ubuntu virtual machines, documented in my [Linux-Admin](https://github.com/Irbaz22/Linux-Admin) repository
- **Python and SQL:** core syntax, plus MySQL schema design and queries
- **Cloud and security fundamentals:** now being turned into real AWS practice in this repository

## Career Goal

I want to move from IT support into a cloud role, starting as a **Junior Cloud Support Engineer or Cloud Engineer** working with AWS. My plan:

1. Learn the core AWS services through hands-on labs: IAM, VPC networking, EC2, storage, and load balancing
2. Earn the **AWS Certified Solutions Architect - Associate** certification
3. Build projects that show real troubleshooting and operations skills, not just console clicks
4. Add automation on top: Linux scripting, Python, and later infrastructure as code

This repository is the evidence trail for that plan.

## Modules

| Module | Topic | Status |
|--------|-------|--------|
| [1](./01-IAM-and-Security) | IAM & Security Best Practices | 🔄 In Progress |
| [2](./02-VPC-Load-Balancers-and-Routing) | VPC, Load Balancers & Routing | ⏳ Pending |
| [3](./03-EC2-and-Auto-Scaling) | EC2 & Auto Scaling | ⏳ Pending |
| [4](./04-Storage-S3-EBS-EFS) | Storage: S3, EBS & EFS | ⏳ Pending |
| [5](./05-Global-Infrastructure) | Global Infrastructure | ⏳ Pending |
| [6](./06-Capstone-Project) | Capstone Project | ⏳ Pending |

## Environment

- Cloud: Amazon Web Services, personal account
- Tools: AWS Management Console (AWS CLI added as the labs progress)
- Course: CloudThat and Online

## Repository Structure

```
AWS-Cloud/
├── README.md
├── 01-IAM-and-Security/
│   ├── README.md
│   └── screenshots/
├── 02-VPC-Load-Balancers-and-Routing/
├── 03-EC2-and-Auto-Scaling/
├── 04-Storage-S3-EBS-EFS/
├── 05-Global-Infrastructure/
└── 06-Capstone-Project/
```

## Security and Cost Practices

- No credentials, access keys, or downloaded credential files are ever committed to this repository
- Account IDs and aliases are redacted in screenshots
- The root user is used for initial setup only; all lab work happens under an IAM user with MFA enabled
- Every lab ends with a cleanup section so that practice resources do not generate surprise charges

## Connect

- Blog: [arbaz.in](https://arbaz.in)
- LinkedIn: [linkedin.com/in/arbaz22](https://www.linkedin.com/in/arbaz22/)
- Linux labs: [Linux-Admin](https://github.com/Irbaz22/Linux-Admin)

*This repository is a work in progress and is updated as each module is completed.*
