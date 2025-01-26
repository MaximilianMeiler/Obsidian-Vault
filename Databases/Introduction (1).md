Previous lecture: N/A


**Database**: A collection of correlated data managed by a DBMS and something we want to persist
- Properties - Persistent, Structured, Queryable

**DBMS** ("Database management system")
- Interacts with the user, applications, and the database to capture and analyze data
- Provides an *efficient*, *convenient*, *reliable*, *safe*, *multi-user* storage of and access to *massive* amounts of *persistent* data
- Architecture: ![[Pasted image 20250115091433.png]]

DDL (Database Definition Language) commands
- Alter the schema/structure of the database (table count, table name, col title, col variable types, etc)
- Called by database administrator
- Compiled, then sent to execution engine -> index manager
DML (Data Manipulation Language) commands
- Ask or modify stored data
- Can be called by the user or the application
- Compiled, then sent to execution engine -> index manager -> buffer manager (to cache certain data) <-> storage manager
- Transaction processing
	- Transaction: groups of commands that are run/completed together
	- Transaction manager communicates with a concurrency control to ensure atomicity (that either all or none of the transaction's commands are applied) and isolation (transaction execution order is unimportant)
		- Uses lock tables to ensure data is being handled between transactions in order
	- Transaction manager also communicates with the logging and recovery  manager, which stores logs in buffers for use by the buffer manager to ensure durability (consistency) in the event of a crash

Storage and buffer management
- The data resides in secondary storage, but must be in main memory to be operated on
- The storage manager controls where data is placed on the disk,  and the movement of data between the disk and main memory
- The buffer manager partitions main memory into buffers (page-sized?)

ACID
- Atomicity: all or nothing (no partial actions)
- Consistency: The DB must always be in a consistent state
- Isolation: Multi-user platform where users do not interfere with one another
- Database: Recovery from failures and misuse

Query Processor
- Query compiler
	- Parser - builds tree structure from query text
	- Preprocessor - semantic checks and tree transformations
	- Optimizer - transform query plan to best sequence of operations
- Execution engine
	- Executes the steps of the query plan

Levels of abstraction (3-tiers)
- View level: Users interact with the database, with different parts of the database shown to different users based on their permissions
- Conceptual level: Defines what data is stored in the database and how the data is related
- Physical level: Describes how the data is physically stored (indexing, compression, organization)

Data models (define data structure, operations, constraints)
- Free text
- Semi-structured (XML)
	- Captures data as a hierarchal structure of labeled values
- Relational (tables/spreadsheets)
	- Entities: things
	- Attributes: properties of entities
	- Relation: connects two or more sets of entities
- Graph data (nodes/edges)
	- 