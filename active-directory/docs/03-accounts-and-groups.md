# Accounts and groups

[Back to overview](../README.md)

## Recorded demonstrations

| Recording | Duration | What can be observed |
| --- | --- | --- |
| [Group membership administration](../evidence/videos/group-membership-administration.mp4) | About 59 seconds | Departmental user properties, security-group listings, group search and membership-selection dialogs |
| [Account administration and client sign-in](../evidence/videos/account-administration-and-client-sign-in.mp4) | About 2 minutes 7 seconds | User administration on DC01, a Windows client session, an `IT User01` welcome screen and a desktop at the end |

### Group administration

The first recording shows `IT User01` properties at approximately 00:05, a security-group listing around 00:13–00:23, and group-selection dialogs around 00:43–00:57. It records the membership administration workflow. Capture the saved **Member Of** and **Members** tabs next to make the final memberships unambiguous.

The OU layout separates `Global_Group` and `Domain_Local`. These are OU names; the actual scope of each security group must be checked in its properties. The intended access-management pattern for a future file-access exercise is:

```text
User account → departmental global group → resource domain-local group → permission
```

This is a design to validate with a resource and access tests. Group selection alone does not prove that NTFS/share permissions were assigned or that an unauthorised user was denied access.

### Account administration

The second recording was supplied as “Enabling Disabling account”. It shows the account/client exercise and a desktop at the end. A desktop and welcome screen alone do not establish whether authentication was online or cached, or prove both outcomes of a disable/enable test.

For a stronger demonstration, record the account's Enabled state before each attempt, a fresh client sign-in while the account is disabled, the rejection message, then re-enable the account and record a fresh successful sign-in. Also capture `whoami` and the authenticating logon server. Disabling an account is not proof that an already active desktop session was immediately terminated.

## Service-account organisation

The `svc_sql` user object is stored under `ServiceAccounts` and is visible on both controllers. This demonstrates directory organisation and object visibility. It does not establish SQL Server deployment, service logon rights, a configured service dependency or use of a managed service account.

## Why this matters in IT support

Clear object placement and verified group memberships make onboarding and access troubleshooting easier. Account-state changes are useful for access control, but the resulting sign-in behaviour needs to be tested and recorded separately.

Reference: [Microsoft: Active Directory security groups](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups).
