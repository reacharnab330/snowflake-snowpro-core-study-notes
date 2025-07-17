# Stages #

1. Stages form a crucial step in the data movement process. They're an area to temporarily hold raw data files either before being loaded into a table or after being unloaded from a table.
2. Stages are of two types viz external and internal
3. Internal stages can be of 3 types , user stage, table stage , named stage. External stage can be of one time i.e. named stage
4. User stage cannot be altered or dropped. Automatically created. Can only be accessed by user. Accessed with the following command (ls @~)
5. Table stage can be accessed by many user but only attached to one specific table. Automatically created. Accessed with the following command (ls @%Table_Name)
6. Named stages are user created securable database objects.  Accessed with the following command (ls @Stage_Name). 
7. Uncompressed files are automatically compressed using GZIP when loaded into an internal stage, unless explicitly set not to. Stage files are automatically encrypted using 128 bit keys.
8. To get a file into an internal stage from your local machine, use the PUT command from local client
9. An external stage is referenced in the same way as a named internal stage. An @ character is followed by the external stage name.
10. A storage integration object encapsulates all the required information to authenticate and gain access to a private external storage service to perform actions like reading, writing and deleting, typically using a generated identity entity such as a role in AWS. It can be applied across stages and is recommended to avoid having to explicitly set sensitive information for each stage definition.


