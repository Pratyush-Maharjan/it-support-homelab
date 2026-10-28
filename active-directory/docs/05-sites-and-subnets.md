# Sites and subnets

[Back to overview](../README.md)

![Configured sites and subnet associations](../evidence/screenshots/06-sites-and-subnets.png)

## Configuration shown

| Subnet object | Location shown | Controllers visible |
| --- | --- | --- |
| `192.168.1.0/24` | Head office — Sydney | `WIN2K25-DC01`, `WIN2K25-DC02` |
| `192.168.10.0/24` | Branch office — Melbourne | None shown |
| `192.168.20.0/24` | Remote office — Perth | None shown |

The head-office label is visible as `LHO-HeadOffice_Sydney`. The branch and remote labels are partially clipped in the screenshot; the location descriptions above summarise their visible names. Export the site/subnet objects to record the exact full labels.

## What the design represents

Sites describe network locations, while subnet objects associate IP ranges with those locations. This gives AD a basis for site-aware domain-controller discovery and replication topology. OUs serve a different purpose: organising directory objects for administration.

Creating site and subnet objects does not create IP networks, routers, VPNs or firewall paths. The current screenshot shows both controllers at head office. It therefore demonstrates configuration of the location model, with branch connectivity and inter-site replication still to be implemented and tested.

## Follow-up validation

```powershell
Get-ADReplicationSite -Filter * | Select-Object Name
Get-ADReplicationSubnet -Filter * | Select-Object Name,Site
Get-ADReplicationSiteLink -Filter * |
    Select-Object Name,Cost,ReplicationFrequencyInMinutes,SitesIncluded
```

On a domain client, run `nltest /dsgetsite` and record its IP address with the result. After a branch network is implemented, confirm routing and DC placement before interpreting replication timing. Site-link costs and schedules are not visible in the supplied evidence.

Reference: [Microsoft: Active Directory replication concepts](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/replication/active-directory-replication-concepts).
