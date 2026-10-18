# Architecture — Azure SQL Active-Passive Disaster Recovery

## Purpose

This document describes a project architecture for Azure SQL Database disaster recovery across East Asia and Southeast Asia. The primary database handles normal read/write traffic; the geo-secondary is the recovery target.

Logical architecture
```text
                    Application / SQL client
                              |
                              v
                 Failover Group Read-Write
                        Listener DNS
                              |
                              v
                  Current primary SQL database
                         East Asia
                              |
                  Asynchronous geo-replication
                              |
                              v
                    Geo-secondary database
                         Southeast Asia
```
After a successful failover, the Southeast Asia database can become primary and the listener routes new connections to the current primary. Applications should use the failover-group read/write listener rather than hard-coding a regional server name.

## Components

| Component | Role |
|---|---|
| East Asia 2 SQL logical server | Original primary region |
| Primary Azure SQL database | Serves normal read/write workload |
| Southeast Asia SQL logical server | Recovery region |
| Geo-secondary database | Replicated recovery copy |
| Auto-Failover Group | Manages the relationship and listener endpoint |
| Read/write listener | Stable connection endpoint for applications |

## Failover behavior and caveats

* Geo-replication is asynchronous. A forced failover during a regional outage can result in data loss if recent changes have not replicated.
* A planned failover is a controlled role switch when the databases are synchronized; it is not the same as testing a real regional outage.
* Applications should implement connection retry/recovery behavior and use the listener endpoint.
* DNS caching and existing connection pools can affect how quickly clients reconnect after failover.
* Recovery time and recovery point objectives depend on workload, service configuration, and failure scenario.

## Network and security

The project uses SQL authentication and public endpoints with firewall access restricted to the administrator's client IP. The broad Allow Azure services and resources to access this server setting should remain disabled unless there is a deliberate, reviewed requirement to enable it.

