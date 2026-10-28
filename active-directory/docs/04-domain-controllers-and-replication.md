# Domain controllers and replication

[Back to overview](../README.md)

## Two-controller configuration

![Both domain controllers listed as global catalogs](../evidence/screenshots/03-two-domain-controllers.png)

Two controller objects are present, and both show `GC` in the DC Type column. This establishes the configuration shown in AD Users and Computers. A second controller provides a basis for redundancy, but actual failover and DNS availability still require testing.

## Object visibility comparison

The `svc_sql` object appears in the same ServiceAccounts OU when the console is connected to DC01 and DC02.

| DC01 | DC02 |
| --- | --- |
| ![svc_sql on DC01](../evidence/screenshots/04-service-account-dc01.png) | ![svc_sql on DC02](../evidence/screenshots/05-service-account-dc02.png) |

This is consistent with directory replication. Matching names alone do not measure convergence time or prove every directory partition and replication direction is healthy. Comparing the object's GUID and metadata, and recording replication diagnostics, would strengthen the result.

## Next verification

Run from the lab with the appropriate AD tools and permissions; these commands are proposed checks, not recorded outputs:

```powershell
Get-ADDomainController -Filter * |
    Select-Object HostName, IPv4Address, Site, IsGlobalCatalog
Get-ADUser svc_sql -Server WIN2K25-DC01 -Properties ObjectGUID,Description |
    Select-Object SamAccountName,ObjectGUID,Description
Get-ADUser svc_sql -Server WIN2K25-DC02 -Properties ObjectGUID,Description |
    Select-Object SamAccountName,ObjectGUID,Description
repadmin /replsummary
repadmin /showrepl
```

Record timestamps, replication failures if any, and the last successful replication for each partner. A controlled test can change a harmless description on DC01 and observe it on DC02, then repeat in the opposite direction. Record the initial value and restore it afterwards.

The original two-controller screenshot still shows the default site name. The later Sites and Services screenshot places both controllers under the head-office site, reflecting the lab's progression.

Reference: [Microsoft: Active Directory replication concepts](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/replication/active-directory-replication-concepts).
