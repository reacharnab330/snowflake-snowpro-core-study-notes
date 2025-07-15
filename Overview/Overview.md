# Overview #

## The Snowflake Platform ##
> Snowflake is a cloud native data platform delivered as a service
* purpose built for the cloud
* no management of hardware, updates and patches
* automatic optimizations (partitioning)

### Snowflake Releases ###
* Snowflake releases new features **_weekly_**
* The deployments happen transparently in the background; users experience no downtime or disruption of service, and are always assured of running on the most-recent release with access to the latest features.

### Data Platform Workloads ###
* Data Warehouse
  * Structured and relational data
  * ANSI standard SQL
  * ACID compliant transactions
  * Data stored in databases, schemas and tables
* Data Lake
  * Separation and scalability of storage and compute
  * Schema does not need to be defined up front
  * Native processing of semi-structured data formats
* Data Engineering
  * Data ingestion
    * batch: `COPY INTO`
    * streaming: Snowpipe
  * Separate compute clusters for different workloads
  * Tasks and Streams for data pipelines
  * Security features:
    * all data encrypted at rest and in transit
    * row-based access control
    * column-level masking
    * Multi-Factor Authentication
* Data Science
  * Centralized storage removes data management roadblocks
  * Partner ecosystem data science tools can integrate natively with Snowflake
    * Amazon SageMaker
    * DataRobot
    * Dataiku
* Data Exchange
  * Secure data sharing between accounts in the same cloud provider region
  * Data Marketplace
  * Data Exchange
  * BI with Snowflake partner ecosystem tools
* Data Applications
  * Connectors and drivers
  * UDFs and Stored Procedures
  * External UDFs (AWS Lambda or Azure Functions)
  * Snowpark

## Connecting to Snowflake
* Snowsight: Snowflake web interface/console
* SnowSQL: The Snowflake CLI client
* ODBC: client, requires a Snowflake driver
* JDBC: client, requires a Snowflake driver
* SDK (Node, Python, Kafka, Spark, Go…)

## Features ##
* ANSI SQL compliant OLAP data warehouse
* Multi-cluster, shared data architecture
* Self-tuning and self-healing
* Pay only for what you use: storage and compute
* Compute (Virtual Warehouses) can be
  * `Scaled Up/Down` by resizing the warehouse on the fly to accommodate complex, heavy workloads
  * `Scaled Out` by using multi-cluster Warehouses allowing Snowflake to automatically spin up additional compute clusters to handle large concurrent query workloads
  * Automatically suspended and resumed to accommodate periods of inactivity
* Time Travel (see below for more info)
* Fail-Safe (see below for more info)
* Live data sharing
  * Private 1:1 and 1:many data sharing
  * Public data marketplaces
  * Secure private data exchanges
* Multi-cloud: AWS, Azure, GCP
* Zero-Copy Cloning
  * Objects that can be cloned: Databases, Schemas and Tables
  * Only metadata is copied
  * Once an object is cloned, the individual copies evolve separately and their storage increases only by the amount of data that was modified in each copy.

### Time Travel ###
* Allows access to previous versions of the data - the data in its state at a point of time in the past
* A minimum of Enterprise edition required for time travel longer than 1 day, up to 90 days
* The period of time travel can be set by database, schema or table
* Three sql extensions -> undrop, at, before. Before does not include the statement id supplied in the query, it considers the state before that query was applied.
* Time travel along with cloning can restore and object from a past date
* standard edition can set DATA_RETENTION_TIME_IN_DAYS value either 0 or 1
* If DATA_RETENTION_TIME_IN_DAYS parameter was set on all levels, the child object takes precedence
* Default DATA_RETENTION_TIME_IN_DAYS is set to 1 day for account, database, schema and table objects
* Minimum value for DATA_RETENTION_TIME_IN_DAYS is zero, means time travel is turned off. Maximum value is 90
* For temporary and transient objects across all editions of Snowflake, the max retention period can either be set to zero or one.
* If a table, schema or database already exists with the name of the dropped object, which is being restored, an error will be returned
* To check which objects have been dropped, you can use a SHOW OBJECT HISTORY command

### Fail-Safe ###
* A data backup feature
* Snowflake admins can recover and restore data up to 7 days after the Time Travel period expires (not configurable)
* Accessible only by contacting Snowflake support administrators
* Only available for permanent tables
* Fail-Safe incurs additional storage costs for the extra 7 days of data retention

## Free Trial ##
You can apply for a 30-day free trial at the following link https://signup.snowflake.com/. Trying out the Enterprise edition is recommended.
