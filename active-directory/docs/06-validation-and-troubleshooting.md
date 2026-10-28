# Validation and troubleshooting

[Back to overview](../README.md)

## DNS and connectivity incident — retained from the original notes

**Symptom:** The first Windows 11 client displayed “No Internet” during setup.

**Checks recorded:** The client initially listed both the domain controller and router as DNS servers. An AD SRV lookup successfully returned `win2k25-dc01.labshandson.lan`:

```cmd
nslookup -type=SRV _ldap._tcp.dc._msdcs.labshandson.lan 192.168.1.11
```

A `ping 1.1.1.1` attempt timed out. DNS and gateway settings were investigated with ChatGPT's help. Connectivity appeared to return, and the client joined the domain.

**Conclusion:** AD discovery worked at the time of the lookup. The exact setting change that restored apparent connectivity was not recorded, so the root cause remains unconfirmed. A failed ping alone does not identify it, and domain join does not establish internet access.

**Next check:** Record `ipconfig /all`, the final gateway/DNS settings, an external DNS lookup and a browser or HTTPS connectivity result. Domain clients should use DNS servers that resolve the AD domain; external resolution should be handled through the AD DNS design rather than assuming the router knows the AD zone.

## Evidence and remaining checks

| Test | Current result | Next evidence to capture |
| --- | --- | --- |
| Domain discovery | Successful SRV response recorded in original notes | Current command output |
| Three client accounts | Visible in ADUC | Client-side domain and secure-channel checks |
| OU organisation | Hierarchy and workstation placement visible | Optional object export |
| Group membership | Administration workflow recorded | Saved membership tabs, group scopes and resource access test |
| Account state / sign-in | Client welcome screen and desktop recorded | Disabled rejection, enabled success, `whoami`, logon server |
| Two controllers | Two GC entries visible | Inventory and DNS health output |
| Object replication | `svc_sql` visible on each controller | Matching GUID, bidirectional change test and replication diagnostics |
| Sites/subnets | Three associations visible | Exact labels, client site discovery, site-link export |
| Internet connectivity | Apparent recovery recorded; root cause unknown | Final configuration and repeatable connectivity checks |
| Server health | Some dashboard alerts visible in captures | Review relevant service/event details and record findings |

## Suggested client checks

Run these in the lab and save the actual results; no results have been invented here.

```cmd
hostname
whoami
whoami /upn
echo %LOGONSERVER%
ipconfig /all
nltest /dsgetsite
nltest /dsgetdc:labshandson.lan
```

From PowerShell on a domain member client:

```powershell
Test-ComputerSecureChannel -Verbose
```

Record the machine, timestamp, expected outcome, actual outcome and evidence file for each test. Review exported outputs for credentials or unrelated personal data before adding them to the public repository.
