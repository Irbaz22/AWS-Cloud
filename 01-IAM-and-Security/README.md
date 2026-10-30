# AWS IAM Project: Admin User, Group and Safe Console Access

A hands-on Project that sets up the first thing every new AWS account needs: a day-to-day administrator identity, so the root user can be put away. It covers IAM users, groups, policy inheritance, an account alias, and signing in as two identities at once.

## What I built

- An **IAM user** with AWS Management Console access
- An **`admin` group** with the AWS managed policy `AdministratorAccess` attached
- The user added to the group, so permissions are inherited rather than attached directly
- An optional **tag** on the user to practise resource metadata
- An **account alias** that gives the account a readable sign-in URL
- Two simultaneous sessions, **root** and **IAM user**, using a private browser window and the console's multi-session support

## Architecture

```
AWS account
├── Root user                 setup only, not used day to day
└── IAM                       global service, no region
    ├── Group: admin          policy: AdministratorAccess
    │   └── User              inherits permissions from the group
    └── Account alias         https://<alias>.signin.aws.amazon.com/console
```

## Steps performed

1. Opened the IAM console and confirmed the service is global (the region selector shows Global).
2. Created an IAM user with console access, choosing the IAM user option rather than Identity Center.
3. Created the `admin` group, attached `AdministratorAccess`, and added the user to it.
4. Reviewed the user and added a tag.
5. Created an account alias and copied the new sign-in URL.
6. Signed in as the IAM user in a private window while keeping the root session open.
7. Turned on multi-session support and signed in to a second identity in the same browser.

## How I verified it

- **Groups → admin** lists one member and the `AdministratorAccess` policy.
- **Users → Permissions** shows `AdministratorAccess` coming from the group, confirming inheritance rather than a direct attachment.
- The console header shows the IAM user name for the IAM session and only the account ID for the root session.
- Both sessions stayed signed in side by side.

## Key takeaways

- IAM is a **global** service. Users and groups created here exist in every region.
- **Groups contain only users**, and a user can belong to several groups. Assigning policies to groups keeps permission management in one place.
- **Policies are JSON documents** describing allowed actions. The principle of **least privilege** means granting only what is needed. `policies/least-privilege-example.json` shows the shape of a narrow read-only policy for illustration; it was not attached in this Project.
- The **root user** should be used for initial setup only.
- Multi-session support, introduced in 2025, allows up to five simultaneous console sessions in one browser. Each session is isolated, and resources belong to the account they were created in.

## Security notes

- No credentials, account IDs or access keys are stored in this repository. The `.gitignore` excludes CSV credential downloads and common secret files.
- `AdministratorAccess` was used here because the Project sets up a personal admin identity. In a team environment, permissions should be scoped down.
- MFA should be enabled on both the root user and the admin user.
- AWS currently recommends IAM Identity Center for human users. The IAM user approach is used here to learn the underlying model.

## Repository structure

```
.
├── README.md
├── LICENSE
├── .gitignore
├── docs/
│   └── screenshots/                  evidence of each step
└── policies/
    └── least-privilege-example.json  illustrative policy, not applied
```

<!--
SCREENSHOTS: add your images to docs/screenshots/, then uncomment the block below.
Crop or blur account IDs before committing.

## Screenshots

![IAM dashboard showing Global region](docs/screenshots/01-iam-dashboard-global.png)
![admin group with AdministratorAccess](docs/screenshots/02-admin-group-policy.png)
![User permissions inherited from group](docs/screenshots/03-user-permissions-inherited.png)
![Account alias and sign-in URL](docs/screenshots/04-account-alias.png)
![Root and IAM user signed in side by side](docs/screenshots/05-two-sessions.png)
-->
## Screenshots

![IAM dashboard showing Global region](<img width="1108" height="616" alt="brave_AsQsMiEE4x" src="https://github.com/user-attachments/assets/84a6cb83-1a1b-4fac-9bf6-4ac246d99178" />)
![admin group with AdministratorAccess](<img width="2200" height="1599" alt="image" src="https://github.com/user-attachments/assets/bdf7f810-5e83-44a6-862c-71ff07cdd395" />
)
![User permissions inherited from group](<img width="1106" height="780" alt="brave_v1uharduhE" src="https://github.com/user-attachments/assets/1a62e579-c447-412a-8a94-f58aaab6e677" />
)
![Account alias and sign-in URL](docs/screenshots/04-account-alias.png)
![Root and IAM user signed in side by side](docs/screenshots/05-two-sessions.png)



## Author

Mohammed Arbaz Ahmed · [Blog](https://arbaz.in) · [GitHub](https://github.com/Irbaz22) · [LinkedIn](https://www.linkedin.com/in/arbaz22/)

Licensed under the MIT License.
