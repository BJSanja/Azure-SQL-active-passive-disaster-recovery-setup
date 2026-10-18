# Deployment Steps — Azure Portal Only

This guide is a repeatable outline for setting up the active-passive Azure SQL Database project. Portal labels can change. Adapt the steps to our subscription and record actual resource names privately; publish only sanitized details.

## 1. Create or select the primary SQL logical server and database
<img width="953" height="281" alt="resource group" src="https://github.com/user-attachments/assets/ed31334a-4f4f-4c18-b2ae-66d366651763" />
<img width="947" height="322" alt="sql server" src="https://github.com/user-attachments/assets/cba7edda-e55b-4867-be6c-029c8c16193b" />
<img width="950" height="312" alt="sql DB" src="https://github.com/user-attachments/assets/5d285a04-a370-4e43-a083-53883897c01e" />

## 2. Create or select the secondary SQL logical server

## 3. Configure geo-replication / failover group
<img width="701" height="355" alt="sql geo replication" src="https://github.com/user-attachments/assets/fbf31a5c-af86-46c1-bec4-485196a55d7d" />
<img width="707" height="331" alt="sql geo replication 2" src="https://github.com/user-attachments/assets/34747adb-624b-4caf-92d9-5c59f19f38f6" />
<img width="932" height="448" alt="fail-over group" src="https://github.com/user-attachments/assets/dabf37f2-c62f-447d-ae87-52e6dfbeeb59" />

## 4. Record the listener endpoint

## 5. Validate database access before failover

<img width="933" height="379" alt="backup 3" src="https://github.com/user-attachments/assets/4013fd56-a12a-4180-a5f1-9d0a4ce92a35" />
<img width="431" height="301" alt="backup" src="https://github.com/user-attachments/assets/31dee021-37f6-42bd-b442-725e6388063a" />

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

