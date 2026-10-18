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

