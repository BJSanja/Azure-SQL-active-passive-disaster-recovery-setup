<img width="467" height="368" alt="archi" src="https://github.com/user-attachments/assets/4275964d-1cfc-4bf4-bdaa-b3a61b8269bc" />


## Select the database replication strategy

### Azure SQL Database

Recommended for many transactional business applications using SQL Server-compatible services.
- Use an auto-failover group across two regional logical servers.
- Connect applications through the stable read-write listener.
- Use the read-only listener for suitable read workloads.
- Enable zone redundancy where supported and justified.
