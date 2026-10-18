# Deployment Steps — Azure Portal Only

This guide is a repeatable outline for setting up the active-passive Azure SQL Database project. Portal labels can change. Adapt the steps to our subscription and record actual resource names privately; publish only sanitized details.

## 1. Create or select the primary SQL logical server and database
<img width="953" height="281" alt="resource group" src="https://github.com/user-attachments/assets/ed31334a-4f4f-4c18-b2ae-66d366651763" />


## 2. Create or select the secondary SQL logical server

## 3. Configure geo-replication / failover group

## 4. Record the listener endpoint

## 5. Validate database access before failover
Connect to the database using your SQL client.
Run a harmless validation query:
```sql
SELECT
    DB_NAME() AS database_name,
    SYSUTCDATETIME() AS checked_at_utc;
```

## 6. Perform a planned failover

## 7. Optional failback

Suggested filenames: `01-primary-overview.png`, `02-secondary-overview.png`, `03-failover-group-health.png`. Only include screenshots from your own Azure environment.

