## Environment

- AWS Management Console (IAM)
- AWS Free Tier account, signed in as an IAM administrator user

## Scenario

I imagined a junior support engineer joining a team. They needed to view IAM users and groups to help with access tickets, but they should not be able to create or change anything. I also wanted to make sign-in stronger for the whole account.

## What I Learned First

- A policy is a JSON document. It has an Effect (Allow or Deny), an Action, a Resource, and sometimes a Principal and a Condition.
- Users get permissions from groups, from policies attached directly, and from inline policies. All of them add up.
- By default, a user can do nothing until a policy allows it.
- A password policy sets rules for IAM user passwords. MFA adds a second proof of identity.

## What I Did

1. Created a test IAM user with no permissions and signed in as that user. The IAM users page showed an access-denied error for the list-users action.
2. Created a group for support staff, attached a read-only IAM policy, and added the user. After that the user could view users and groups.
3. Tried to create a group as that user. It failed, because read-only access does not allow creating anything.
4. Opened the JSON of the read-only policy and read it. It allows actions that start with `Get` and `List` on all resources.
5. Built my own custom policy in the visual editor that allows only listing users and viewing one user. I attached it directly to the user and saw that the user now had permissions from two sources, the group and the direct policy.
6. Set a custom password policy with a minimum length, mixed character types, password expiry, and no password reuse.
7. Added an authenticator app as an MFA device for the test user, entered two consecutive codes, and then signed in again using a password and a code.
8. Cleaned up by removing the direct policy and the test group.

## Commands / Console Steps Used

- IAM, Users, Create user - created the test user.
- IAM, User groups, Create group - created the support group and attached a policy.
- IAM, Policies, JSON tab - read how a managed policy is written.
- IAM, Policies, Create policy - built a custom policy in the visual editor.
- IAM, Account settings, Password policy - set the password rules.
- IAM, Users, Security credentials, Assign MFA device - added the authenticator app.

## Results

- The user had no access before any policy and could view IAM after the group policy.
- The user could not create groups with read-only access.
- The user's permissions page showed the group policy and the direct policy as separate entries.
- The custom password policy saved, and MFA sign-in worked.

## Key Takeaways

- Access is denied by default, and permissions are added by policies.
- Group policies are easier to manage than direct ones, so I use groups first.
- `*` in a policy means "anything", so `Action: *` on `Resource: *` is full admin.
- Read-only access is a safe way to let someone look without being able to change.
- MFA protects an account even if the password is stolen. I did not add MFA to my root user, because losing the device would lock me out.

## Screenshots

<!--
Uncomment after adding real images. Blur account IDs, aliases, and QR codes.

![Access denied](screenshots/01-access-denied.png)
![Policy JSON](screenshots/02-policy-json.png)
![User permissions](screenshots/03-user-permissions.png)
![Password policy](screenshots/04-password-policy.png)
-->
