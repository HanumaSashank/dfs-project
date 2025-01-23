# Distributed File System
## Overview
This project implements a Distributed File System (DFS) designed to manage files across interconnected servers with features like scalability, fault tolerance, high availability and disconnection management. The system allows seamless file operations (create, delete, read, write, etc.) and supports efficient synchronization and replication strategies.
## Key features
- **Fault Tolerance:** Ensures data redundancy by creating primary and replica copies on separate servers.
- **Location Transparency:** The system abstracts file locations, enabling uniform access regardless of storage locations
- **Automatic Failover:** Backup servers for the DB server and active servers are always on. Nodes automatically connect to backup servers in case of primary server failures.
- **Modular Architecture:** Composed of Active Server, DB Server, Lock Server, and multiple File Servers for efficient task distribution.
- **Replication:** Replicated copies of files ensure consistency and availability.\
- **Fair Locking Mechanism:** Provides orderly and conflict-free write access using FIFO principles.
- **Scalability:** Accommodates additional servers and clients without compromising performance.
## System Components
1. Active Server
   - Orchestrates communication between clients and file servers.
   - Maintains a dynamic list of available servers through heartbeat messages.
   - Directs clients to appropriate file servers for operations.
2. DB Server
   - Acts as a centralized repository for metadata, tracking file primary and replica locations.
   - Facilitates access to primary and replica copies of files for various operations.
3. Lock Server
   - Ensures orderly write operations(FIFO principle) through a fair locking mechanism.
   - Handles client requests for exclusive write access, avoiding conflicts.
4. Backup Servers
   - Always-on backups for the DB and Active Servers.
   - Automatically take over when the primary servers fail, ensuring uninterrupted connectivity and operations.
5. File Servers
   - Store primary and replica copies of files.
   - Perform file operations like read, write, and delete.
   - Communicate with the DB Server for metadata and synchronization details.
## Supported File Operations
 - **Create:** Generate new files with initial attributes and metadata.
 - **Read:** Retrieve data from files using primary or replica copies.
 - **Write:** Append or modify file content while maintaining consistency across replicas.
 - **Delete:** Remove primary and replica copies from the system.
 - **Seek:** Reposition file pointers for efficient data access.
 - **List Files:** View all currently available files in the whole distributed file system.
## Technology Stack
 - **Programming Language:** Python
 - **Libraries Used:** > socket, time, csv, os, shutil, random, collections
 - **Architecture:** Client-Server
## Architecture Diagram
![image](https://github.com/user-attachments/assets/eabbb3c5-47ae-49fb-bb4c-d51e1945fb06)
## Scalability and Performance
 - Gradual response time increment with more clients; decreased response time with additional servers.
 - Efficient workload distribution, with support for increased client and server counts.
## Future Work
 - Enhanced Backup System: Extend backup capabilities to all nodes for complete failover support.
 - Optimized Performance: Investigate anomaly patterns in response times to improve system robustness under heavy workloads.
## How to run the system
 - First, run the Lock_server.py, Db_server.py, Active_server.py (use different terminals for different programs)
 - Then run all the corresponding Fileservers server1.py, server2.py and server3.py (in 3 different terminals)
 - Now run the new_client.py program
 - As soon as you run the client program the client will be automatically connected to one of the active servers as shown below:
   ![image](https://github.com/user-attachments/assets/3a5125dd-5991-49dc-a83d-284afea9b176)
 - Now based on your requirement give the file operations and can **check working of all normal file operations**(8 operations including “LIST”), **replication** (can check file creation and updating in the parent directory of the replica server), **Locking Mechanism** (similarly like above create multiple client instances by running the new_client.py program in different terminals) and **Node failure** as well. For testing node failures make sure you are running backup_ Db_server.py, backup_Active_server.py as well\
**Note:** Make sure you’ve created all the required empty directories for every server in your local for smooth start.

