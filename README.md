Distributed file system with pessimistic server replication, Locking Mechanism and Disconnection management.
How to run the system:
	1)First, run the Lock_server.py, Db_server.py, Active_server.py (use different terminals for different programs)
 	2)Then run all the corresponding Fileservers server1.py, server2.py and server3.py (in 3 different terminals)
	3)Now run the new_client.py program
	As soon as you run the client program the client will be automatically connected to one of the active servers as shown below:
 	![image](https://github.com/user-attachments/assets/3a5125dd-5991-49dc-a83d-284afea9b176)
	Now based on your requirement give the file operations and can check working of all normal file 
 	operations(8 operations including “LIST”), replication (can check file creation and updating in the parent directory of the replica server), 
	Locking Mechanism (similarly like above create multiple client instances by running the new_client.py program in different terminals) and Node failure as well.
 	For testing node failures make sure you are running backup_ Db_server.py, backup_Active_server.py as well
Note: Make sure you’ve created all the required empty directories for every server in your local for smooth start.
