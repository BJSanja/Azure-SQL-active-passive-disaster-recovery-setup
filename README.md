# Azure-SQL-active-passive-disaster-recovery-setup
Azure SQL Database active-passive disaster recovery setup using geo-replication, failover groups, and planned failover validation through the Azure Portal.

> **Status:** 
This project documents an active-passive disaster recovery setup across two Azure regions. The primary database serves normal read/write traffic, while a geo-secondary database provides a recovery target.
>
## Architecture
```text
                  Application / SQL Client
                            |
                            v
                Failover Group Read-Write
                       Listener
                            |
                            v
                 Primary Azure SQL Database
                         East US 2
                            |
                     Geo-replication
                            |
                            v
                Secondary Azure SQL Database
                         Central US
```
The failover-group read/write listener is the stable application endpoint. After failover, it directs connections to the current primary. Applications should connect through the listener rather than hard-coding a regional server endpoint.

## Goals

* Configure a primary Azure SQL database and a secondary in another region.
* Configure and inspect the failover group.
* Identify the read/write listener endpoint.
* Perform a planned failover.
* Verify the new primary role and database connectivity.
* Document observations, limitations, and cleanup.

## Deployment Outline

* Create or select the primary SQL logical server and database in East US 2.
* Create or select a secondary SQL logical server in Central US.
* Configure cross-region geo-replication and the Auto-Failover Group.
* Confirm replication and failover-group health.
* Record the failover-group read/write listener endpoint (do not include credentials).
* Perform a planned failover through the Azure Portal.
* Verify which region is primary after the operation.
* Test database access through the listener.
* If appropriate, perform and document a controlled failback.

## Validation Checklist
* [x] Primary and secondary regions configured
* [x] Failover group created and health checked
* [x] Planned failover performed
* [x] New primary role verified
* [ ] Application connectivity tested through the read/write listener
* [x] Failback tested and documented




