# AWS IAM Hands-On Project: Admin User, Group, and Multi-Session Sign-In

A step-by-step Project that walks through the first thing every new AWS account needs: stop using the root user and set up a properly permissioned IAM user instead. It also covers account aliases and the console's multi-session support, so you can work in more than one identity or account from the same browser.

## What You Will Build

By the end of this Project you will have the following in a fresh AWS account:

```
AWS Account
├── Root user ............. used for setup only, then left alone
└── IAM
    ├── Group: admin ...... has the AdministratorAccess policy
    │   └── User .......... inherits permissions from the group
    └── Account alias ..... a friendlier sign-in URL
```

You will also sign in as the new user in a private window while the root session stays open, then repeat the idea in a single browser using multi-session support.

## Concepts Covered

- **IAM (Identity and Access Management):** the AWS service that controls who can sign in and what they can do. It is global, so there is no region to choose.
- **Root user:** the identity created with the account. It has unrestricted power and should be used only for initial setup.
- **Users and groups:** a user represents one person. A group holds users, never other groups. A user can be in no group or in several groups.
- **Policies:** JSON documents that describe permitted actions, attached to users or groups. Users inherit the policies of every group they belong to.
- **Least privilege:** grant only the permissions that are needed, and nothing more.
- **Multi-session support:** staying signed in to several accounts or identities in one browser.

## Prerequisites

- A personal AWS account that you can sign in to as the root user
- A modern browser that supports private or incognito windows
- A password manager, or another safe place to keep credentials

## Project Steps

### Part 1: Explore IAM and confirm you are the root user

1. Sign in to the AWS Management Console as the root user.
2. In the search bar, type **IAM** and open the IAM console. Ignore the security recommendations on the dashboard for now.
3. Look at the top-right corner. It reads **Global** and offers no region picker. This confirms IAM is a global service.
4. Open the account menu in the top-right corner. It shows only the account ID (`<ACCOUNT_ID>`), which is how you recognise a root session.

<!-- Screenshot suggestion: IAM dashboard with the Global Projectel visible. Redact the account ID. -->
<img width="941" height="329" alt="image" src="https://github.com/user-attachments/assets/c0e63ede-67a8-48e9-8028-7a8fa7802932" />

### Part 2: Create the user and the admin group

1. In the left menu, choose **IAM Users**, then **Create user**.
2. Enter a user name that identifies you, for example `<your-name>`.
3. Tick **Provide user access to the AWS Management Console**, then choose **I want to create an IAM user**.
   - IAM Identity Center is the recommended option for real organizations. An IAM user is simpler for learning and is what the certification exam expects you to know.
4. Set the password.
   - For another person: keep the auto-generated password and leave **User must create a new password at next sign-in** ticked.
   - For your own practice account: choose a custom password and untick that box.
5. Choose **Next**.
6. On the permissions step, choose to add the user to a group, then **Create group**.
   - Group name: `admin`
   - Policy: `AdministratorAccess`
7. Create the group, then select it on the permissions page and choose **Next**.
8. On the review page, confirm the user name and the group permissions. Optionally add a tag such as `Department = Engineering`. Tags are optional metadata that can be attached to most AWS resources.
9. Choose **Create user**.
10. The success page offers to email sign-in instructions or download a CSV file of credentials. If you download it, store it privately and never commit it to a repository.

<!-- Screenshot suggestion: the review page showing group permissions. -->
<img width="929" height="409" alt="image" src="https://github.com/user-attachments/assets/c067435b-00e9-4797-90f7-7f064d38cd43" />


### Part 3: Verify the permissions

1. Return to the **Users** list and confirm the new user is present.
2. Open **User groups**, then `admin`. You should see one user and the `AdministratorAccess` policy.
3. Open the user and view the **Permissions** tab. `AdministratorAccess` is listed as attached through the group `admin`. The user did not receive it directly; it was inherited. This is why permissions are managed at group level.

### Part 4: Create an account alias (optional)

1. On the IAM dashboard, find the **AWS Account** panel. It shows the account ID and the sign-in URL.
2. Next to **Account alias**, choose **Create** and enter a name. Aliases must be globally unique, so try another variation if yours is taken.
3. Copy the new sign-in URL, which now uses the alias instead of the account ID.

### Part 5: Sign in as the IAM user while staying signed in as root

1. Open a private (incognito) window.
   - Signing in as the IAM user in your normal window would replace the root session. The private window keeps the two sessions separate so both can be open side by side.
2. Paste the sign-in URL. If you land on the general sign-in page, choose **IAM user**, not root.
3. Enter the account ID or alias, the IAM user name, and the password.
4. Compare the top-right menu in each window:
   - Private window: shows the IAM user name and the account ID.
   - Normal window: shows only the account ID, which is the root session.

### Part 6: Try multi-session support (optional)

1. In the console, open the account menu in the top-right corner and turn on **multi-session support**.
2. In the same menu, choose **Add session**.
3. Sign in with another account ID, root user, or IAM user.
4. Each session shows its own account ID in the top right. Check it before making any change.
5. Optional proof that the sessions are separate:
   - In one session, go to **EC2 > Volumes** and create a 1 GiB EBS volume.
   - In the other session, open the same Volumes page. It is empty, because the volume belongs to a different account.

## Verification Checklist

- [ ] IAM console shows **Global** instead of a region
- [ ] User `<your-name>` exists and can sign in to the console
- [ ] Group `admin` exists with one member and the `AdministratorAccess` policy
- [ ] The user's Permissions tab shows the policy attached via the group
- [ ] The private window shows the IAM user and the normal window shows root
- [ ] Multi-session support lets you hold a second session in the same browser

## Cleanup

- If you created the test EBS volume in Part 6, delete it to avoid charges: **EC2 > Volumes**, select the volume, then **Actions > Delete volume**.
- IAM users and groups do not cost anything, so you can keep the admin user for later Projects.
- Make sure you still have working credentials for both the root user and the admin user. If both are lost, recovery means contacting AWS Support.

## Security Notes

- **Never commit credentials.** Do not add the downloaded credentials CSV, passwords, or access keys to this repository.
- **Redact before sharing.** Blur account IDs, aliases, and user names in screenshots before publishing them.
- **Turn on MFA** for both the root user and the admin user. This goes beyond the steps above but is a standard recommendation.
- **AdministratorAccess is for practice.** In a real team, create narrower groups and attach only the permissions each group needs.

## Key Takeaways

1. IAM is global: what you create applies in every region.
2. The root user is for setup. Daily work belongs to IAM users.
3. Attach policies to groups and put users in groups, so permissions are inherited and easy to manage.
4. Least privilege should be the default mindset, even in a practice account.
5. Multi-session support, or a private window, lets you compare identities side by side without logging out.

## Next Steps

- Create a second group with a narrower policy, such as read-only access, and compare what its members can do.
- Enable MFA on both identities.
- Move on to the next AWS foundation topics, starting with VPC networking.

## Author

Mohammed Arbaz Ahmed. Full write-ups and more Projects at [arbaz.in](https://arbaz.in).
