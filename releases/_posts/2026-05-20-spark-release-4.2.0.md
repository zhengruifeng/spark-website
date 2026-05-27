---
layout: post
title: Spark Release 4.2.0
categories: []
tags: []
status: publish
type: post
published: true
meta:
  _edit_last: '4'
  _wpas_done_all: '1'
---

Apache Spark 4.2.0 is the second release of the 4.x line. The release advances several long-running SPIPs (geospatial types, Constraints in DSv2, Declarative Pipelines, JDBC driver for Spark Connect), modernizes the Spark Web UI, lands first-class Change Data Capture (CDC) support in DSv2, brings Pandas 3 compatibility to Pandas API on Spark, and adds Java 25 build support.

To download Apache Spark 4.2.0, visit the <a href="{{site.baseurl}}/downloads.html">downloads</a> page.

You can consult JIRA for the <a href="https://issues.apache.org/jira/issues/?jql=project%20%3D%20SPARK%20AND%20fixVersion%20%3D%204.2.0">detailed changes</a>.

### Highlights
- [[SPARK-55760]](https://issues.apache.org/jira/browse/SPARK-55760) Spark Web UI Modernization (37 commits)
- [[SPARK-55555]](https://issues.apache.org/jira/browse/SPARK-55555) Support heterogeneous K8s executor management (18 commits)
- [[SPARK-51658]](https://issues.apache.org/jira/browse/SPARK-51658) SPIP: Add geospatial types in Spark (15 commits)
- [[SPARK-56603]](https://issues.apache.org/jira/browse/SPARK-56603) Improve K8s Resource Manager API (14 commits)
- [[SPARK-51167]](https://issues.apache.org/jira/browse/SPARK-51167) Build and Run Spark on Java 25 (10 commits)
- [[SPARK-55668]](https://issues.apache.org/jira/browse/SPARK-55668) Change Data Capture (CDC) Support (10 commits)
- [[SPARK-56249]](https://issues.apache.org/jira/browse/SPARK-56249) Auto CDC support (9 commits)
- [[SPARK-55400]](https://issues.apache.org/jira/browse/SPARK-55400) Reduce K8s control plane overhead (6 commits)
- [[SPARK-55556]](https://issues.apache.org/jira/browse/SPARK-55556) Improve Web Security (5 commits)
- [[SPARK-56287]](https://issues.apache.org/jira/browse/SPARK-56287) Improve Spark History Server Scalability (4 commits)
- [[SPARK-54119]](https://issues.apache.org/jira/browse/SPARK-54119) Metrics & semantic modeling in Spark (3 commits)
- [[SPARK-56395]](https://issues.apache.org/jira/browse/SPARK-56395) SPIP: NEAREST BY Top-K Ranking Join

### Spark Core
- **Improve Spark History Server Scalability** ([[SPARK-56287]](https://issues.apache.org/jira/browse/SPARK-56287))
  - [[SPARK-55793]](https://issues.apache.org/jira/browse/SPARK-55793) Support multiple log directories in SHS
  - [[SPARK-56234]](https://issues.apache.org/jira/browse/SPARK-56234) Support disabling log directory scanning by path pattern in SHS
  - [[SPARK-56044]](https://issues.apache.org/jira/browse/SPARK-56044) HistoryServerDiskManager does not delete app store on release when app is not in active map
  - [[SPARK-56278]](https://issues.apache.org/jira/browse/SPARK-56278) Populate accurate metadata immediately during on-demand loading in SHS
- **DAGScheduler Stability/Performance improvements** ([[SPARK-56494]](https://issues.apache.org/jira/browse/SPARK-56494))
- **SPIP: Declarative Pipelines** ([[SPARK-51727]](https://issues.apache.org/jira/browse/SPARK-51727))
  - [[SPARK-54562]](https://issues.apache.org/jira/browse/SPARK-54562) Block eager analysis / execution inside flow function from server side rather than client side
  - [[SPARK-55945]](https://issues.apache.org/jira/browse/SPARK-55945) Support structured identifiers for flows in SDP eager analysis protos
- **Sql Scripting support for Spark SQL** ([[SPARK-48338]](https://issues.apache.org/jira/browse/SPARK-48338))
  - [[SPARK-55005]](https://issues.apache.org/jira/browse/SPARK-55005) CONTINUE handler not working properly when exception occurs inside loops
  - [[SPARK-55119]](https://issues.apache.org/jira/browse/SPARK-55119) CONTINUE handler should not interrupt conditional if exception thrown by previous statement
- [[SPARK-46830]](https://issues.apache.org/jira/browse/SPARK-46830) Introducing collation concept into Spark
- [[SPARK-53807]](https://issues.apache.org/jira/browse/SPARK-53807) Fix a race condition issue between `unlock` and `releaseAllLocksForTask` in `BlockInfoManager for write locks
- [[SPARK-54219]](https://issues.apache.org/jira/browse/SPARK-54219) Driver can't create thread causing ContextCleaner stuck and stuck stop process
- [[SPARK-55051]](https://issues.apache.org/jira/browse/SPARK-55051) Byte string accepts KiB, MiB, GiB, TiB, PiB
- [[SPARK-55064]](https://issues.apache.org/jira/browse/SPARK-55064) Query level indeterminate shuffle retry
- [[SPARK-55528]](https://issues.apache.org/jira/browse/SPARK-55528) Default collation support for SQL UDFs
- [[SPARK-56279]](https://issues.apache.org/jira/browse/SPARK-56279) Enable zero-copy sendfile for FileRegion in native Netty transports
- [[SPARK-56298]](https://issues.apache.org/jira/browse/SPARK-56298) Enable `spark.master.rest.virtualThread.enabled` by default
- [[SPARK-56302]](https://issues.apache.org/jira/browse/SPARK-56302) Free memories as soon as possible to reduce memory pressure handling large task results
- [[SPARK-56330]](https://issues.apache.org/jira/browse/SPARK-56330) Add TaskInterruptListener to TaskContext for interrupt notifications

### SQL Foundation
- **SPIP: Add geospatial types in Spark** ([[SPARK-51658]](https://issues.apache.org/jira/browse/SPARK-51658))
  - [[SPARK-55238]](https://issues.apache.org/jira/browse/SPARK-55238) Move the SRS mapping Java classes to sql/api/src/main/java
  - [[SPARK-55259]](https://issues.apache.org/jira/browse/SPARK-55259) Implement Parquet schema conversion for Geo types
  - [[SPARK-55260]](https://issues.apache.org/jira/browse/SPARK-55260) Implement Parquet write support for Geo types
  - [[SPARK-55261]](https://issues.apache.org/jira/browse/SPARK-55261) Implement Parquet read support for Geo types
  - [[SPARK-55262]](https://issues.apache.org/jira/browse/SPARK-55262) Block Geo types in all file based data sources except Parquet
  - [[SPARK-55295]](https://issues.apache.org/jira/browse/SPARK-55295) Extend the ST_GeomFromWKB function to take an optional SRID value
  - [[SPARK-55339]](https://issues.apache.org/jira/browse/SPARK-55339) Implement WKT writer for Geo objects
  - [[SPARK-55449]](https://issues.apache.org/jira/browse/SPARK-55449) Enable WKB parsing and writing for Geography
  - [[SPARK-55530]](https://issues.apache.org/jira/browse/SPARK-55530) Support Geo result sets in Hive and Thrift server
  - [[SPARK-55539]](https://issues.apache.org/jira/browse/SPARK-55539) Allow casting from GeometryType to GeographyType
  - [[SPARK-55541]](https://issues.apache.org/jira/browse/SPARK-55541) Support Geometry and Geography in catalyst type converters
  - [[SPARK-55640]](https://issues.apache.org/jira/browse/SPARK-55640) Propagate WKB parsing errors for Geometry and Geography
  - [[SPARK-55790]](https://issues.apache.org/jira/browse/SPARK-55790) Build a complete SRS registry using PROJ 9.7.1 data
  - [[SPARK-56682]](https://issues.apache.org/jira/browse/SPARK-56682) Extend the ST_AsBinary function to take an optional endianness
  - [[SPARK-56771]](https://issues.apache.org/jira/browse/SPARK-56771) Enable `spark.sql.geospatial.enabled` by default
- **Improve JDBC example and test coverage** ([[SPARK-55581]](https://issues.apache.org/jira/browse/SPARK-55581))
- **Change Data Capture (CDC) Support** ([[SPARK-55668]](https://issues.apache.org/jira/browse/SPARK-55668))
  - [[SPARK-55948]](https://issues.apache.org/jira/browse/SPARK-55948) Add DSv2 CDC connector API, analyzer resolution, and SQL CHANGES clause
  - [[SPARK-55949]](https://issues.apache.org/jira/browse/SPARK-55949) Add DataFrame API and Spark Connect support for CDC queries
  - [[SPARK-55950]](https://issues.apache.org/jira/browse/SPARK-55950) Add PySpark API support for CDC queries
  - [[SPARK-55952]](https://issues.apache.org/jira/browse/SPARK-55952) Post Process for CDC batch query: drop carry-overs
  - [[SPARK-55953]](https://issues.apache.org/jira/browse/SPARK-55953) Post Process for CDC batch query: compute update
  - [[SPARK-56686]](https://issues.apache.org/jira/browse/SPARK-56686) Post Process for CDC streaming query: drop carry-overs and compute updates
  - [[SPARK-56687]](https://issues.apache.org/jira/browse/SPARK-56687) Post Process for CDC streaming query: compute net changes
  - [[SPARK-55951]](https://issues.apache.org/jira/browse/SPARK-55951) The schema of ChangeLog must contain _change_type/_commit_version/_commit_timestamp
  - [[SPARK-56711]](https://issues.apache.org/jira/browse/SPARK-56711) CDC: Restricting data type of _commit_version to Long / String
- **Search path support** ([[SPARK-54806]](https://issues.apache.org/jira/browse/SPARK-54806))
  - [[SPARK-54807]](https://issues.apache.org/jira/browse/SPARK-54807) Support SYSTEM.BUILTIN and SYSTEM.SESSION for function resolution
  - [[SPARK-54808]](https://issues.apache.org/jira/browse/SPARK-54808) Support SYSTEM.SESSION for temporary view resolution
  - [[SPARK-56639]](https://issues.apache.org/jira/browse/SPARK-56639) Frozen PATH semantics
  - [[SPARK-56939]](https://issues.apache.org/jira/browse/SPARK-56939) Resolve deadlock between USE and function lookup
- **Align DSv2 commands to DSv1 implementation** ([[SPARK-33392]](https://issues.apache.org/jira/browse/SPARK-33392))
  - [[SPARK-33902]](https://issues.apache.org/jira/browse/SPARK-33902) CREATE TABLE LIKE FOR V2
  - [[SPARK-39660]](https://issues.apache.org/jira/browse/SPARK-39660) Support v2 DESCRIBE TABLE .. PARTITION
  - [[SPARK-49543]](https://issues.apache.org/jira/browse/SPARK-49543) Support v2 SHOW COLLATIONS
- **SPIP: NEAREST BY Top-K Ranking Join** ([[SPARK-56395]](https://issues.apache.org/jira/browse/SPARK-56395))
- **Metrics & semantic modeling in Spark** ([[SPARK-54119]](https://issues.apache.org/jira/browse/SPARK-54119))
  - [[SPARK-54405]](https://issues.apache.org/jira/browse/SPARK-54405) Query metric view with dimensions and measures
  - [[SPARK-54403]](https://issues.apache.org/jira/browse/SPARK-54403) YAML parser to read metric view definition
- **Support `MERGE INTO` Schema Evolution** ([[SPARK-54274]](https://issues.apache.org/jira/browse/SPARK-54274))
  - [[SPARK-54621]](https://issues.apache.org/jira/browse/SPARK-54621) Merge Into Update Set * preserve nested fields if coerceNestedTypes is enabled
  - [[SPARK-56472]](https://issues.apache.org/jira/browse/SPARK-56472) Fix MERGE schema evolution with WHEN MATCHED THEN DELETE
- **SPIP: Row-level operations in Data Source V2** ([[SPARK-35801]](https://issues.apache.org/jira/browse/SPARK-35801))
  - [[SPARK-53652]](https://issues.apache.org/jira/browse/SPARK-53652) Codegen For MergeRowExec
  - [[SPARK-56524]](https://issues.apache.org/jira/browse/SPARK-56524) UPDATE Operation Metrics
- [[SPARK-31561]](https://issues.apache.org/jira/browse/SPARK-31561) Add QUALIFY Clause
- [[SPARK-43752]](https://issues.apache.org/jira/browse/SPARK-43752) default column value should support v2 write commands
- [[SPARK-44571]](https://issues.apache.org/jira/browse/SPARK-44571) Eliminate the Join by combine multiple Aggregates
- [[SPARK-47672]](https://issues.apache.org/jira/browse/SPARK-47672) Avoid double evaluation of non-trivial projected elements from filter pushdown
- [[SPARK-51518]](https://issues.apache.org/jira/browse/SPARK-51518) Support | as an alternative to |> for the operator pipe token
- [[SPARK-51712]](https://issues.apache.org/jira/browse/SPARK-51712) Swallow non-fatal Throwables when resolving tables in spark.catalog.listTables()
- [[SPARK-52729]](https://issues.apache.org/jira/browse/SPARK-52729) Add MetadataOnlyTable and CREATE/ALTER VIEW support for DS v2 catalogs
- [[SPARK-54063]](https://issues.apache.org/jira/browse/SPARK-54063) Trigger snapshot generation for next batch when lag is detected
- [[SPARK-54106]](https://issues.apache.org/jira/browse/SPARK-54106) State Store Row Checksum implementation
- [[SPARK-54179]](https://issues.apache.org/jira/browse/SPARK-54179) Add Native Support for Apache Tuple Sketches
- [[SPARK-54292]](https://issues.apache.org/jira/browse/SPARK-54292) Support aggregation in |> SELECT operators
- [[SPARK-54411]](https://issues.apache.org/jira/browse/SPARK-54411) [SS] Introduce Writer for Repartition - support multiple column families
- [[SPARK-54419]](https://issues.apache.org/jira/browse/SPARK-54419) Support State Reader for Multi-col-family operator
- [[SPARK-54420]](https://issues.apache.org/jira/browse/SPARK-54420) Introduce State Writer for offline repartitioning - support single column family
- [[SPARK-54446]](https://issues.apache.org/jira/browse/SPARK-54446) FPGrowth supports local filesystem
- [[SPARK-54675]](https://issues.apache.org/jira/browse/SPARK-54675) Add configurable force shutdown timeout for StateStore maintenance thread pool
- [[SPARK-54682]](https://issues.apache.org/jira/browse/SPARK-54682) Improve DescribeProcedureCommand
- [[SPARK-54713]](https://issues.apache.org/jira/browse/SPARK-54713) Add support for vector similarity/distance functions
- [[SPARK-54718]](https://issues.apache.org/jira/browse/SPARK-54718) Preserve attributes names during CTE newInstance()
- [[SPARK-54720]](https://issues.apache.org/jira/browse/SPARK-54720) Create an empty DataFrame with a schema
- [[SPARK-54735]](https://issues.apache.org/jira/browse/SPARK-54735) Properly preserve column comments in view with SCHEMA EVOLUTION
- [[SPARK-54759]](https://issues.apache.org/jira/browse/SPARK-54759) Support for cursors in SQL Scripting
- [[SPARK-54760]](https://issues.apache.org/jira/browse/SPARK-54760) DelegatingCatalogExtension supports both V1 and V2 functions
- [[SPARK-54803]](https://issues.apache.org/jira/browse/SPARK-54803) Support BY NAME with INSERT INTO ... REPLACE WHERE
- [[SPARK-54812]](https://issues.apache.org/jira/browse/SPARK-54812) Make executable commands not execute on resultDf.cache()
- [[SPARK-54840]](https://issues.apache.org/jira/browse/SPARK-54840) OrcList Pre-allocation
- [[SPARK-54854]](https://issues.apache.org/jira/browse/SPARK-54854) Add queryId (UUIDv7) to SQL Execution Events
- [[SPARK-54864]](https://issues.apache.org/jira/browse/SPARK-54864) Add plan normalization for recursive CTEs
- [[SPARK-54870]](https://issues.apache.org/jira/browse/SPARK-54870) collation support for char/varchar and CTAS/RTAS
- [[SPARK-54971]](https://issues.apache.org/jira/browse/SPARK-54971) Recognizing the existence of the SQL Syntax WITH SCHEMA EVOLUTION for SQL INSERT statements in the Parser
- [[SPARK-55019]](https://issues.apache.org/jira/browse/SPARK-55019) Allow DROP TABLE to drop VIEW
- [[SPARK-55030]](https://issues.apache.org/jira/browse/SPARK-55030) Add support for vector_norm, vector_normalize functions
- [[SPARK-55031]](https://issues.apache.org/jira/browse/SPARK-55031) Add support for vector_sum, vector_avg functions
- [[SPARK-55256]](https://issues.apache.org/jira/browse/SPARK-55256) [SQL] Support IGNORE NULLS / RESPECT NULLS for array_agg and collect_list
- [[SPARK-55304]](https://issues.apache.org/jira/browse/SPARK-55304) Introduce Admission Control and Trigger.AvailableNow into Python Data Source - reader
- [[SPARK-55322]](https://issues.apache.org/jira/browse/SPARK-55322) Add Overload for MaxBy / MinBy with k > 1
- [[SPARK-55356]](https://issues.apache.org/jira/browse/SPARK-55356) Support alias in Spark SQL PIVOT
- [[SPARK-55453]](https://issues.apache.org/jira/browse/SPARK-55453) LIKE returns wrong results for emoji
- [[SPARK-55533]](https://issues.apache.org/jira/browse/SPARK-55533) Support IGNORE NULLS / RESPECT NULLS for collect_set
- [[SPARK-55558]](https://issues.apache.org/jira/browse/SPARK-55558) Add Support for Tuple/Theta Set Operations
- [[SPARK-55596]](https://issues.apache.org/jira/browse/SPARK-55596) DSV2 Enhanced Partition Stats Filtering
- [[SPARK-55601]](https://issues.apache.org/jira/browse/SPARK-55601) Hook StreamingSourceIdentifyingName into MicrobatchExecution for source naming
- [[SPARK-55631]](https://issues.apache.org/jira/browse/SPARK-55631) ALTER TABLE should invalidate cache
- [[SPARK-55689]](https://issues.apache.org/jira/browse/SPARK-55689) Support schema evolution in DSv2 INSERTs
- [[SPARK-55690]](https://issues.apache.org/jira/browse/SPARK-55690) Implement schema evolution for DSv2 AppendData, OverwriteByExpression, OverwritePartitionsDynamic
- [[SPARK-55702]](https://issues.apache.org/jira/browse/SPARK-55702) Support filter predicate in window aggregate functions
- [[SPARK-55729]](https://issues.apache.org/jira/browse/SPARK-55729) Support state format v4 of stream-stream join in state data source (reader)
- [[SPARK-55855]](https://issues.apache.org/jira/browse/SPARK-55855) Add foundations for the DSv2 Transaction API
- [[SPARK-55857]](https://issues.apache.org/jira/browse/SPARK-55857) [SQL] Support ignoreMissingFiles when inferring schema during schema evolution
- [[SPARK-55964]](https://issues.apache.org/jira/browse/SPARK-55964) By default, prevent shadowing of system schemas
- [[SPARK-55995]](https://issues.apache.org/jira/browse/SPARK-55995) Support TIMESTAMP WITH LOCAL TIME ZONE in SQL syntax
- [[SPARK-55999]](https://issues.apache.org/jira/browse/SPARK-55999) Enable `spark.sql.streaming.stateStore.forceSnapshotUploadOnLag` by default
- [[SPARK-56001]](https://issues.apache.org/jira/browse/SPARK-56001) Recognizing the existence of the SQL Syntax REPLACE ON/USING for SQL INSERT statements in the Parser
- [[SPARK-56045]](https://issues.apache.org/jira/browse/SPARK-56045) Parquet UNKNOWN Type Regression at Spark 4.1
- [[SPARK-56046]](https://issues.apache.org/jira/browse/SPARK-56046) Typed SPJ partition key reducers
- [[SPARK-56152]](https://issues.apache.org/jira/browse/SPARK-56152) Support implicit cast from string to time
- [[SPARK-56182]](https://issues.apache.org/jira/browse/SPARK-56182) Allow SPJ reducing identity to other transforms
- [[SPARK-56221]](https://issues.apache.org/jira/browse/SPARK-56221) Feature parity between spark.catalog.* vs DDL commands
- [[SPARK-56251]](https://issues.apache.org/jira/browse/SPARK-56251) Avoid loading all data to memory by default for PostgresSQL jdbc connector
- [[SPARK-56384]](https://issues.apache.org/jira/browse/SPARK-56384) Support Update mode in Stream-Stream Non-Outer Join
- [[SPARK-56489]](https://issues.apache.org/jira/browse/SPARK-56489) Support for PATH syntax
- [[SPARK-56501]](https://issues.apache.org/jira/browse/SPARK-56501) SET PATH syntax
- [[SPARK-56509]](https://issues.apache.org/jira/browse/SPARK-56509) SparkSQL Last Attempt Metrics
- [[SPARK-56520]](https://issues.apache.org/jira/browse/SPARK-56520) Persist PATH for VIEWs, FUNCTIONS, expose with DESCRIBE
- [[SPARK-56521]](https://issues.apache.org/jira/browse/SPARK-56521) Support PartitionPredicate in runtime filters
- [[SPARK-56522]](https://issues.apache.org/jira/browse/SPARK-56522) Batch PACKED null/non-null runs in VectorizedRleValuesReader
- [[SPARK-56551]](https://issues.apache.org/jira/browse/SPARK-56551) DSv2 DELETE Operation Metrics
- [[SPARK-56594]](https://issues.apache.org/jira/browse/SPARK-56594) Add time_bucket scalar function for interval-based timestamp bucketing
- [[SPARK-56598]](https://issues.apache.org/jira/browse/SPARK-56598) Custom metrics support for TruncatableTable
- [[SPARK-56605]](https://issues.apache.org/jira/browse/SPARK-56605) Wire resolution engine to use SQL PATH for table, function, and variable lookup
- [[SPARK-56677]](https://issues.apache.org/jira/browse/SPARK-56677) Propagate filter conditions through Join nodes in PlanMerger
- [[SPARK-56680]](https://issues.apache.org/jira/browse/SPARK-56680) DSv2 INSERT Operation Metrics

### Spark Connect
- **Pandas UDF with PyArrow Backend** ([[SPARK-54955]](https://issues.apache.org/jira/browse/SPARK-54955))
  - [[SPARK-55462]](https://issues.apache.org/jira/browse/SPARK-55462) Support UserDefinedType in convert_numpy
  - [[SPARK-54965]](https://issues.apache.org/jira/browse/SPARK-54965) Factor out legacy pa.Array -> pd.Series (np-backed) converter
  - [[SPARK-54969]](https://issues.apache.org/jira/browse/SPARK-54969) Implement new arrow->pandas conversion
  - [[SPARK-55036]](https://issues.apache.org/jira/browse/SPARK-55036) Add ArrowTimeStampConversion for arrow timezone handling
  - [[SPARK-55044]](https://issues.apache.org/jira/browse/SPARK-55044) Keep the metadata in toArrowSchema/fromArrowSchema
  - [[SPARK-55088]](https://issues.apache.org/jira/browse/SPARK-55088) Keep the metadata in to/from_arrow_type/schema
  - [[SPARK-55186]](https://issues.apache.org/jira/browse/SPARK-55186) Make ArrowArrayToPandasConversion.convert_legacy able to return pd.DataFrame
  - [[SPARK-55333]](https://issues.apache.org/jira/browse/SPARK-55333) Revisit date_as_object in arrow->pandas conversion
  - [[SPARK-55334]](https://issues.apache.org/jira/browse/SPARK-55334) Enable TimestampType and TimestampNTZType in convert_numpy
  - [[SPARK-55365]](https://issues.apache.org/jira/browse/SPARK-55365) Generalize the utils for arrow array conversion
  - [[SPARK-55366]](https://issues.apache.org/jira/browse/SPARK-55366) Remove `errorOnDuplicatedFieldNames` from Python UDFs
  - [[SPARK-55424]](https://issues.apache.org/jira/browse/SPARK-55424) Explicitly pass the series name in convert_numpy
  - [[SPARK-55464]](https://issues.apache.org/jira/browse/SPARK-55464) Support GeographyType in convert_numpy
  - [[SPARK-55465]](https://issues.apache.org/jira/browse/SPARK-55465) Support GeometryType in convert_numpy
- **RDD API compatibility** ([[SPARK-55227]](https://issues.apache.org/jira/browse/SPARK-55227))
  - [[SPARK-55089]](https://issues.apache.org/jira/browse/SPARK-55089) Correct the output schema of toJSON
  - [[SPARK-55090]](https://issues.apache.org/jira/browse/SPARK-55090) Implement DataFrame.toJSON in Python Client
  - [[SPARK-55228]](https://issues.apache.org/jira/browse/SPARK-55228) Implement Dataset.zipWithIndex in Scala API
  - [[SPARK-55229]](https://issues.apache.org/jira/browse/SPARK-55229) Implement DataFrame.zipWithIndex in PySpark Classic
  - [[SPARK-56253]](https://issues.apache.org/jira/browse/SPARK-56253) Make spark.read.json accept DataFrame input
  - [[SPARK-56254]](https://issues.apache.org/jira/browse/SPARK-56254) Make spark.read.xml accept DataFrame input
  - [[SPARK-56255]](https://issues.apache.org/jira/browse/SPARK-56255) Make spark.read.csv accept DataFrame input
  - [[SPARK-56256]](https://issues.apache.org/jira/browse/SPARK-56256) Implement SparkSession.emptyDataFrame in Python
  - [[SPARK-55249]](https://issues.apache.org/jira/browse/SPARK-55249) Make DataFrame.toJSON able to return dataframe
  - [[SPARK-55385]](https://issues.apache.org/jira/browse/SPARK-55385) Mitigate the recomputation in zipWithIndex
  - [[SPARK-55395]](https://issues.apache.org/jira/browse/SPARK-55395) Disable RDD cache in DataFrame.zipWithIndex
- **Fix broken tests in Spark Connect 4.0 client <> master server** ([[SPARK-54477]](https://issues.apache.org/jira/browse/SPARK-54477))
- **SPIP: Language-agnostic UDF Protocol for Spark** ([[SPARK-55278]](https://issues.apache.org/jira/browse/SPARK-55278))
  - [[SPARK-56284]](https://issues.apache.org/jira/browse/SPARK-56284) Key worker abstraction for language-agnostic UDF protocol
  - [[SPARK-56412]](https://issues.apache.org/jira/browse/SPARK-56412) Implement WorkerDispatcher for direct worker that are spawned as local processes
- [[SPARK-50111]](https://issues.apache.org/jira/browse/SPARK-50111) PySpark and PS Plotting Improvement
- [[SPARK-54314]](https://issues.apache.org/jira/browse/SPARK-54314) Improve Server-Side debuggability in Spark Connect by capturing client application's file name and line numbers in PySpark
- [[SPARK-55047]](https://issues.apache.org/jira/browse/SPARK-55047) [CONNECT] Add client-side limit for local relation size
- [[SPARK-55606]](https://issues.apache.org/jira/browse/SPARK-55606) [CONNECT] Server-side implementation of GetStatus API
- [[SPARK-55691]](https://issues.apache.org/jira/browse/SPARK-55691) [CONNECT] Client-side implementation of GetStatus API

### PySpark
- **Support Pandas 3** ([[SPARK-55139]](https://issues.apache.org/jira/browse/SPARK-55139))
  - [[SPARK-55156]](https://issues.apache.org/jira/browse/SPARK-55156) deal with include_groups for groupby.apply
  - [[SPARK-55244]](https://issues.apache.org/jira/browse/SPARK-55244) Use np.nan as default for string type in pandas 3
  - [[SPARK-55296]](https://issues.apache.org/jira/browse/SPARK-55296) Support CoW mode for pyspark.pandas
  - [[SPARK-55297]](https://issues.apache.org/jira/browse/SPARK-55297) Restore unit for timedelta dtype
  - [[SPARK-55345]](https://issues.apache.org/jira/browse/SPARK-55345) Timedelta does not take unit and closed anymore
  - [[SPARK-55376]](https://issues.apache.org/jira/browse/SPARK-55376) Make numeric_only argument in groupby functions accept only boolean with pandas 3
  - [[SPARK-55490]](https://issues.apache.org/jira/browse/SPARK-55490) Make groupby(as_index=False) include a grouping that is not in the DataFrame with pandas 3
  - [[SPARK-55648]](https://issues.apache.org/jira/browse/SPARK-55648) Handle an unexpected keyword argument error `groupby(axis)` with pandas 3
  - [[SPARK-55867]](https://issues.apache.org/jira/browse/SPARK-55867) Fix StringMethods
  - [[SPARK-55896]](https://issues.apache.org/jira/browse/SPARK-55896) Use numpy functions instead of builtins
  - [[SPARK-55901]](https://issues.apache.org/jira/browse/SPARK-55901) Raise an error from Series.replace() with no arguments
  - [[SPARK-56016]](https://issues.apache.org/jira/browse/SPARK-56016) Preserve named Series columns in concat with ignore_index on pandas 3
  - [[SPARK-56219]](https://issues.apache.org/jira/browse/SPARK-56219) Align groupby idxmax and idxmin skipna=False behavior with pandas 2/3
  - [[SPARK-56245]](https://issues.apache.org/jira/browse/SPARK-56245) Fix DataFrame.eval inplace assignment on pandas 3
  - [[SPARK-55140]](https://issues.apache.org/jira/browse/SPARK-55140) Do not convert builtin functions for pandas 3 anymore
  - [[SPARK-55154]](https://issues.apache.org/jira/browse/SPARK-55154) Remove fastpath to pd.Series
  - [[SPARK-55225]](https://issues.apache.org/jira/browse/SPARK-55225) Fix timestamp unit issue for pandas 3
  - [[SPARK-55226]](https://issues.apache.org/jira/browse/SPARK-55226) Recognize timestamp units other than [ns]
  - [[SPARK-55403]](https://issues.apache.org/jira/browse/SPARK-55403) Fix no attribute 'draw' error in the plot tests with pandas 3
  - [[SPARK-55408]](https://issues.apache.org/jira/browse/SPARK-55408) Handle unexpected keyword argument errors related to datetime with pandas 3
  - [[SPARK-55409]](https://issues.apache.org/jira/browse/SPARK-55409) Handle an unexpected keyword argument error from read_excel with pandas 3
  - [[SPARK-55472]](https://issues.apache.org/jira/browse/SPARK-55472) Raise AttributeError from methods removed in pandas 3
  - [[SPARK-55625]](https://issues.apache.org/jira/browse/SPARK-55625) Fix StringOps to make `str` dtype work properly
  - [[SPARK-55700]](https://issues.apache.org/jira/browse/SPARK-55700) Fix handling integer keys on Series with non-integer index
  - [[SPARK-55730]](https://issues.apache.org/jira/browse/SPARK-55730) Not make timezone lower case
  - [[SPARK-55843]](https://issues.apache.org/jira/browse/SPARK-55843) Handle the unit of datetime64 and timedelta64 dtypes
  - [[SPARK-55946]](https://issues.apache.org/jira/browse/SPARK-55946) Set up __pandas_priority__ so mixed binary ops dispatch correctly to pandas-on-Spark
  - [[SPARK-55989]](https://issues.apache.org/jira/browse/SPARK-55989) Preserve non-int64 index dtypes in `restore_index`
  - [[SPARK-56060]](https://issues.apache.org/jira/browse/SPARK-56060) Handle pandas 3 null string conversion in describe() for empty timestamp frames
  - [[SPARK-56080]](https://issues.apache.org/jira/browse/SPARK-56080) Align Series.argmax/argmin with pandas 3.0 NA handling
  - [[SPARK-56081]](https://issues.apache.org/jira/browse/SPARK-56081) Align idxmax and idxmin NA handling with pandas 3
  - [[SPARK-56113]](https://issues.apache.org/jira/browse/SPARK-56113) Improve pandas 3 string restoration in pandas-on-Spark
  - [[SPARK-56118]](https://issues.apache.org/jira/browse/SPARK-56118) Match pandas 3.0 bool handling in GroupBy.quantile
  - [[SPARK-56122]](https://issues.apache.org/jira/browse/SPARK-56122) Use pandas-aware numeric dtype check in Series.cov
  - [[SPARK-56167]](https://issues.apache.org/jira/browse/SPARK-56167) Align astype with pandas 3 default string behavior
  - [[SPARK-56187]](https://issues.apache.org/jira/browse/SPARK-56187) Fix Series.argsort null ordering for pandas 3
  - [[SPARK-56188]](https://issues.apache.org/jira/browse/SPARK-56188) Align Series.map({}) with pandas 3 empty-dict behavior
  - [[SPARK-56226]](https://issues.apache.org/jira/browse/SPARK-56226) Catch analysis errors before `InternalFrame.__init__` in `.loc`
  - [[SPARK-56310]](https://issues.apache.org/jira/browse/SPARK-56310) Handle pandas 3 string dtype in DataFrame.toPandas
- **Monitor behaviour changes from upstream** ([[SPARK-54936]](https://issues.apache.org/jira/browse/SPARK-54936))
- **Micro-benchmark PySpark Eval Types** ([[SPARK-55724]](https://issues.apache.org/jira/browse/SPARK-55724))
- **Refactor PythonEvalType processing logic** ([[SPARK-55388]](https://issues.apache.org/jira/browse/SPARK-55388))
- **Polish type annotations for pyspark** ([[SPARK-56223]](https://issues.apache.org/jira/browse/SPARK-56223))
- **Refactor PySpark Serializers** ([[SPARK-55384]](https://issues.apache.org/jira/browse/SPARK-55384))
- **Improve lint on PySpark** ([[SPARK-54543]](https://issues.apache.org/jira/browse/SPARK-54543))
- **Python worker logging infrastructure** ([[SPARK-53754]](https://issues.apache.org/jira/browse/SPARK-53754))
- **Improve test coverage on pyspark** ([[SPARK-54453]](https://issues.apache.org/jira/browse/SPARK-54453))
- **Extract Arrow batch transformers from serializers for better composability** ([[SPARK-55159]](https://issues.apache.org/jira/browse/SPARK-55159))
  - [[SPARK-55168]](https://issues.apache.org/jira/browse/SPARK-55168) Refactor GroupArrowUDFSerializer to use ArrowBatchTransformer.flatten_struct
  - [[SPARK-55169]](https://issues.apache.org/jira/browse/SPARK-55169) Refactor ArrowStreamArrowUDTFSerializer to use ArrowBatchTransformer.flatten_struct
  - [[SPARK-55336]](https://issues.apache.org/jira/browse/SPARK-55336) Factor out ArrowStreamPandasSerializer._create_batch logic for createDataFrame
- [[SPARK-53615]](https://issues.apache.org/jira/browse/SPARK-53615) Introduce iterator API for arrow grouped agg UDF
- [[SPARK-53616]](https://issues.apache.org/jira/browse/SPARK-53616) Introduce iterator API for pandas grouped agg UDF
- [[SPARK-54337]](https://issues.apache.org/jira/browse/SPARK-54337) Expose __dataframe__ interchange protocol on pyspark RDD, SQL DataFrame, and pandas DataFrame APIs
- [[SPARK-54555]](https://issues.apache.org/jira/browse/SPARK-54555) Enable Arrow-optimized Python UDFs by default
- [[SPARK-54617]](https://issues.apache.org/jira/browse/SPARK-54617) Register Arrow Grouped Iter Aggregate UDF for SQL usage
- [[SPARK-54631]](https://issues.apache.org/jira/browse/SPARK-54631) Add profiler support for Arrow Grouped Iter Aggregate UDF
- [[SPARK-54722]](https://issues.apache.org/jira/browse/SPARK-54722) Register Pandas Grouped Iter Aggregate UDF for SQL usage
- [[SPARK-54738]](https://issues.apache.org/jira/browse/SPARK-54738) Add profiler support for Pandas Grouped Iter Aggregate UDF
- [[SPARK-54925]](https://issues.apache.org/jira/browse/SPARK-54925) Add the capability in pyspark to dump thread info from all processes
- [[SPARK-55055]](https://issues.apache.org/jira/browse/SPARK-55055) Support SparkSession.Builder.create for PySpark Classic #53820
- [[SPARK-55096]](https://issues.apache.org/jira/browse/SPARK-55096) Update pandas minimum version in `connect/setup.py`
- [[SPARK-55161]](https://issues.apache.org/jira/browse/SPARK-55161) Support profilers on python data source
- [[SPARK-55179]](https://issues.apache.org/jira/browse/SPARK-55179) Skip eager column name validation in df.col_name
- [[SPARK-55610]](https://issues.apache.org/jira/browse/SPARK-55610) Introduce getExecutorInfos to SparkStatusTracker in PySpark
- [[SPARK-55788]](https://issues.apache.org/jira/browse/SPARK-55788) Support ExtensionDType for integers in Pandas UDF
- [[SPARK-56322]](https://issues.apache.org/jira/browse/SPARK-56322) [CONNECT][PYTHON] Self-joining an observed DataFrame raises TypeError in observations property
- [[SPARK-56463]](https://issues.apache.org/jira/browse/SPARK-56463) Disallow unpickling UDT
- [[SPARK-56518]](https://issues.apache.org/jira/browse/SPARK-56518) Add current_path to PySpark functions
- [[SPARK-56614]](https://issues.apache.org/jira/browse/SPARK-56614) Add config for strict DataFrame column resolution

#### Pandas API on Spark
- **Add missing parameters for Pandas API on Spark** ([[SPARK-46156]](https://issues.apache.org/jira/browse/SPARK-46156))
  - [[SPARK-46162]](https://issues.apache.org/jira/browse/SPARK-46162) Improve axis parameter for DataFrame.nunique to support columns
  - [[SPARK-46163]](https://issues.apache.org/jira/browse/SPARK-46163) Add filter_func and errors parameter for DataFrame.update
  - [[SPARK-46165]](https://issues.apache.org/jira/browse/SPARK-46165) Improve axis parameter for DataFrame.all to support columns
  - [[SPARK-46167]](https://issues.apache.org/jira/browse/SPARK-46167) Add axis, pct and na_option parameter to DataFrame.rank
  - [[SPARK-46168]](https://issues.apache.org/jira/browse/SPARK-46168) Add axis parameter to DataFrame idxmax
  - [[SPARK-46166]](https://issues.apache.org/jira/browse/SPARK-46166) Add axis and skipna parameters to DataFrame.any
- [[SPARK-55662]](https://issues.apache.org/jira/browse/SPARK-55662) pyspark.pandas.DataFrame.idxmin axis implementation

### Structured Streaming
- **Enabling addition, removal and reordering of streaming sources** ([[SPARK-54909]](https://issues.apache.org/jira/browse/SPARK-54909))
  - [[SPARK-55039]](https://issues.apache.org/jira/browse/SPARK-55039) Add IDENTIFIED BY syntax for naming streaming sources
  - [[SPARK-55054]](https://issues.apache.org/jira/browse/SPARK-55054) Add IDENTIFIED BY support for streaming table-valued functions
  - [[SPARK-55057]](https://issues.apache.org/jira/browse/SPARK-55057) Add streaming source naming infrastructure and resolution pipeline
  - [[SPARK-55104]](https://issues.apache.org/jira/browse/SPARK-55104) Add Spark Connect support for DataStreamReader.name()
  - [[SPARK-55121]](https://issues.apache.org/jira/browse/SPARK-55121) Add DataStreamReader.name() to Classic PySpark
  - [[SPARK-54907]](https://issues.apache.org/jira/browse/SPARK-54907) Introduce NameStreamingSources analyzer rule for streaming source evolution
  - [[SPARK-55013]](https://issues.apache.org/jira/browse/SPARK-55013) Add SQL parser support for streaming source naming infrastructure
  - [[SPARK-54910]](https://issues.apache.org/jira/browse/SPARK-54910) Add streamingSourceIdentifyingName field to StreamingRelationV2
  - [[SPARK-55029]](https://issues.apache.org/jira/browse/SPARK-55029) Propagate streaming source identifying name through resolution pipeline
- **Structured Streaming - Offline State Repartitioning** ([[SPARK-54345]](https://issues.apache.org/jira/browse/SPARK-54345))
  - [[SPARK-54346]](https://issues.apache.org/jira/browse/SPARK-54346) Introduce repartition API and repartition runner
  - [[SPARK-54388]](https://issues.apache.org/jira/browse/SPARK-54388) State Reader - repartition dataframe format (with read support for single column family stores e.g. agg, dedup etc.)
  - [[SPARK-54443]](https://issues.apache.org/jira/browse/SPARK-54443) Partition key extraction for all streaming stateful operators
  - [[SPARK-54924]](https://issues.apache.org/jira/browse/SPARK-54924) State Rewriter to Read + transform + Write
  - [[SPARK-54984]](https://issues.apache.org/jira/browse/SPARK-54984) State Repartition execution and integrate with State Rewriter
  - [[SPARK-55146]](https://issues.apache.org/jira/browse/SPARK-55146) State repartition pyspark API
  - [[SPARK-54365]](https://issues.apache.org/jira/browse/SPARK-54365) Test repartition for Agg, Dedup, session window, FMGWS
  - [[SPARK-55111]](https://issues.apache.org/jira/browse/SPARK-55111) Failed repartitioning detection on query restart
- **Allow seamless and sequential source switching for streaming queries** ([[SPARK-55122]](https://issues.apache.org/jira/browse/SPARK-55122))
  - [[SPARK-55123]](https://issues.apache.org/jira/browse/SPARK-55123) Add SequentialUnionOffset for tracking sequential source processing
  - [[SPARK-55317]](https://issues.apache.org/jira/browse/SPARK-55317) Introduce the SequentialUnion Logical Node
  - [[SPARK-55471]](https://issues.apache.org/jira/browse/SPARK-55471) Adding optimizer support for Sequential Union
- [[SPARK-54121]](https://issues.apache.org/jira/browse/SPARK-54121) Automatic Snapshot Repair for State store
- [[SPARK-54423]](https://issues.apache.org/jira/browse/SPARK-54423) Create the OffsetMap to enable tracking of streaming progress via name
- [[SPARK-54583]](https://issues.apache.org/jira/browse/SPARK-54583) Add SQLConf to enable use of OffsetMap
- [[SPARK-54590]](https://issues.apache.org/jira/browse/SPARK-54590) State Writer supports checkpoint V2
- [[SPARK-54660]](https://issues.apache.org/jira/browse/SPARK-54660) Add RTM trigger to python and tests
- [[SPARK-55058]](https://issues.apache.org/jira/browse/SPARK-55058) Throw an error if the /metadata file is not present, but offset or commit directories are non-empty
- [[SPARK-55129]](https://issues.apache.org/jira/browse/SPARK-55129) Introduce State Store API and key encoders for event-time as a first class
- [[SPARK-55145]](https://issues.apache.org/jira/browse/SPARK-55145) Reflect the new RocksDB key encoders in SPARK-55129 to Avro
- [[SPARK-55628]](https://issues.apache.org/jira/browse/SPARK-55628) Integrate state format version 4 state manager to stream-stream join operator
- [[SPARK-55728]](https://issues.apache.org/jira/browse/SPARK-55728) Introduce RocksDB conf for file checksum threadpool size
- [[SPARK-55751]](https://issues.apache.org/jira/browse/SPARK-55751) Add metrics on how often state stores are loaded from cloud storage
- [[SPARK-56216]](https://issues.apache.org/jira/browse/SPARK-56216) Integrate checkpoint V2 with auto-repair snapshot

### MLlib
- [[SPARK-41916]](https://issues.apache.org/jira/browse/SPARK-41916) Address General Fixes
- [[SPARK-54706]](https://issues.apache.org/jira/browse/SPARK-54706) Make DistributedLDAModel work with local file system

### Declarative Pipelines
- **Auto CDC support** ([[SPARK-56249]](https://issues.apache.org/jira/browse/SPARK-56249))
  - [[SPARK-56650]](https://issues.apache.org/jira/browse/SPARK-56650) Add AutoCDC connect APIs
  - [[SPARK-56651]](https://issues.apache.org/jira/browse/SPARK-56651) Add AutoCDC Python API
  - [[SPARK-56838]](https://issues.apache.org/jira/browse/SPARK-56838) Introduce AutoCDC parameters dataclass
  - [[SPARK-56856]](https://issues.apache.org/jira/browse/SPARK-56856) Implement SCD1 Batch Processor; Microbatch Deduplication
  - [[SPARK-56870]](https://issues.apache.org/jira/browse/SPARK-56870) Implement SCD1 Batch Processor; Extend Microbatch with CDC Metadata
  - [[SPARK-56882]](https://issues.apache.org/jira/browse/SPARK-56882) Implement SCD1 Batch Processor; Target Column Projection
  - [[SPARK-56953]](https://issues.apache.org/jira/browse/SPARK-56953) Implement SCD1 Batch Processor; foreachBatch Callback
  - [[SPARK-56956]](https://issues.apache.org/jira/browse/SPARK-56956) AutoCDC Flow Execution; Introduce AutoCDC Flow Dataclasses

### Web UI
- **Spark Web UI Modernization** ([[SPARK-55760]](https://issues.apache.org/jira/browse/SPARK-55760))
  - [[SPARK-55785]](https://issues.apache.org/jira/browse/SPARK-55785) Compact SQL plan visualization nodes with detail side panel
  - [[SPARK-55835]](https://issues.apache.org/jira/browse/SPARK-55835) Highlight non-default Spark configuration values on Environment page
  - [[SPARK-55877]](https://issues.apache.org/jira/browse/SPARK-55877) Support side-by-side SQL plan comparison
  - [[SPARK-55878]](https://issues.apache.org/jira/browse/SPARK-55878) Add query timeline visualization to SQL tab
  - [[SPARK-55880]](https://issues.apache.org/jira/browse/SPARK-55880) Link SQL plan nodes to corresponding stage/job pages
  - [[SPARK-55881]](https://issues.apache.org/jira/browse/SPARK-55881) Add missing fields to SQL execution REST API (queryId, errorMessage, subExecutionIds)
  - [[SPARK-55961]](https://issues.apache.org/jira/browse/SPARK-55961) Make SQL plan viz side panel collapsible to avoid overlapping with the plan graph
  - [[SPARK-55971]](https://issues.apache.org/jira/browse/SPARK-55971) Add Jobs table section to SQL execution detail page
  - [[SPARK-56002]](https://issues.apache.org/jira/browse/SPARK-56002) Make SQL plan visualization metrics table sortable
  - [[SPARK-56140]](https://issues.apache.org/jira/browse/SPARK-56140) Add server-side pagination for SQL tab query listing
  - [[SPARK-55764]](https://issues.apache.org/jira/browse/SPARK-55764) Use delegated event listener for Bootstrap 5 Tooltip lazy initialization
  - [[SPARK-55766]](https://issues.apache.org/jira/browse/SPARK-55766) Support dark mode using Bootstrap 5 CSS custom properties
  - [[SPARK-55767]](https://issues.apache.org/jira/browse/SPARK-55767) Use Bootstrap 5 Offcanvas for detail panels on Environment/Executor pages
  - [[SPARK-55768]](https://issues.apache.org/jira/browse/SPARK-55768) Improve responsive layout for executor/storage tables and DAG visualizations
  - [[SPARK-55771]](https://issues.apache.org/jira/browse/SPARK-55771) Modernize progress bars using Bootstrap 5 Progress component
  - [[SPARK-55776]](https://issues.apache.org/jira/browse/SPARK-55776) Fix data-title to data-bs-title for timeline tooltips after Bootstrap 5 upgrade
  - [[SPARK-55779]](https://issues.apache.org/jira/browse/SPARK-55779) Add Scala helper for inline tooltip markup in Spark UI pages
  - [[SPARK-55784]](https://issues.apache.org/jira/browse/SPARK-55784) Add table-hover class for interactive table row highlighting
  - [[SPARK-55834]](https://issues.apache.org/jira/browse/SPARK-55834) Use tabbed layout for Environment page sections
  - [[SPARK-55837]](https://issues.apache.org/jira/browse/SPARK-55837) Render Environment page tables client-side via REST API
  - [[SPARK-55839]](https://issues.apache.org/jira/browse/SPARK-55839) Add export config button to Environment page
  - [[SPARK-55863]](https://issues.apache.org/jira/browse/SPARK-55863) Add footer to Spark Web UI with user, version, and uptime
  - [[SPARK-55875]](https://issues.apache.org/jira/browse/SPARK-55875) Switch SQL tab query listing to client-side DataTables
  - [[SPARK-55927]](https://issues.apache.org/jira/browse/SPARK-55927) Remove `jquery.mustache.js`
  - [[SPARK-55985]](https://issues.apache.org/jira/browse/SPARK-55985) Remove `jquery.blockUI.min.js`
  - [[SPARK-56020]](https://issues.apache.org/jira/browse/SPARK-56020) Improve GroupPartitions Explain Extended
  - [[SPARK-56048]](https://issues.apache.org/jira/browse/SPARK-56048) Add copy plan text and share link buttons to SQL execution detail page
  - [[SPARK-56049]](https://issues.apache.org/jira/browse/SPARK-56049) Add search/filter for metrics in SQL plan visualization side panel
  - [[SPARK-56143]](https://issues.apache.org/jira/browse/SPARK-56143) Remove `jquery.cookies`
  - [[SPARK-56239]](https://issues.apache.org/jira/browse/SPARK-56239) Fix SQL tab client-side DataTables: default API limit, date format, and appId resolution
  - [[SPARK-56259]](https://issues.apache.org/jira/browse/SPARK-56259) Fix SHS application list table header/data column mismatch
  - [[SPARK-56331]](https://issues.apache.org/jira/browse/SPARK-56331) Truncate long node labels in SQL plan visualization
  - [[SPARK-56587]](https://issues.apache.org/jira/browse/SPARK-56587) Show table name in WriteDelta UI node
  - [[SPARK-56792]](https://issues.apache.org/jira/browse/SPARK-56792) Support pan and zoom for SQL plan visualization
  - [[SPARK-56799]](https://issues.apache.org/jira/browse/SPARK-56799) Search and highlight nodes in SQL plan visualization
  - [[SPARK-56809]](https://issues.apache.org/jira/browse/SPARK-56809) Show description on SQL execution detail page
  - [[SPARK-56811]](https://issues.apache.org/jira/browse/SPARK-56811) Restore sub-execution grouping on SQL tab listing
- [[SPARK-54877]](https://issues.apache.org/jira/browse/SPARK-54877) Make display stacktrace on UI error page configurable
- [[SPARK-55008]](https://issues.apache.org/jira/browse/SPARK-55008) Display Query ID in Spark UI

### Deployment
- **Support heterogeneous K8s executor management** ([[SPARK-55555]](https://issues.apache.org/jira/browse/SPARK-55555))
  - [[SPARK-55496]](https://issues.apache.org/jira/browse/SPARK-55496) Support reuse of scaled PVCs
  - [[SPARK-55639]](https://issues.apache.org/jira/browse/SPARK-55639) Support Recovery-mode K8s Executor
  - [[SPARK-55075]](https://issues.apache.org/jira/browse/SPARK-55075) Track executor pod creation errors with ExecutorFailureTracker
  - [[SPARK-55431]](https://issues.apache.org/jira/browse/SPARK-55431) Set `resizePolicy` to `NotRequired` explicitly for executor pods
  - [[SPARK-55432]](https://issues.apache.org/jira/browse/SPARK-55432) Support built-in K8s `ExecutorResizePlugin`
  - [[SPARK-54422]](https://issues.apache.org/jira/browse/SPARK-54422) Increase `spark.kubernetes.allocation.batch.size` to 20
  - [[SPARK-55134]](https://issues.apache.org/jira/browse/SPARK-55134) If the executor’s resource request is greater than its limit, the driver is expected to exit
  - [[SPARK-55359]](https://issues.apache.org/jira/browse/SPARK-55359) Promote `TaskResourceRequest` to `Stable`
  - [[SPARK-55485]](https://issues.apache.org/jira/browse/SPARK-55485) Add `Constants.POD_DELETION_COST` for reuse
  - [[SPARK-55649]](https://issues.apache.org/jira/browse/SPARK-55649) Promote `Kubernetes(Driver|Executor)?FeatureConfigStep` traits to `Stable`
  - [[SPARK-55704]](https://issues.apache.org/jira/browse/SPARK-55704) Add `Constants.DEFAULT_PVC_ACCESS_MODE ` for reuse
  - [[SPARK-55757]](https://issues.apache.org/jira/browse/SPARK-55757) Improve `spark.task.cpus` validation
  - [[SPARK-56670]](https://issues.apache.org/jira/browse/SPARK-56670) Restrict `ExecutorResizePlugin` to `direct` pods allocator
  - [[SPARK-56684]](https://issues.apache.org/jira/browse/SPARK-56684) Expose `KubernetesClusterSchedulerBackend.kubernetesClient` to `k8s` package
  - [[SPARK-56689]](https://issues.apache.org/jira/browse/SPARK-56689) Improve `ExecutorResizePlugin` to reuse `KubernetesClusterSchedulerBackend.kubernetesClient`
  - [[SPARK-56693]](https://issues.apache.org/jira/browse/SPARK-56693) Support built-in K8s `ExecutorPVCResizePlugin`
  - [[SPARK-56699]](https://issues.apache.org/jira/browse/SPARK-56699) Default ExecutorPVCResizePlugin interval to 5min in 5-minute units
  - [[SPARK-56702]](https://issues.apache.org/jira/browse/SPARK-56702) Restrict `ExecutorPVCResizePlugin` to `direct` pods allocator
- **Improve K8s Resource Manager API** ([[SPARK-56603]](https://issues.apache.org/jira/browse/SPARK-56603))
  - [[SPARK-56491]](https://issues.apache.org/jira/browse/SPARK-56491) Add `ReadOnlySparkConf.getAllAsJavaMap`
  - [[SPARK-56163]](https://issues.apache.org/jira/browse/SPARK-56163) Move `uploadFileToHadoopCompatibleFS` to Utils
  - [[SPARK-56300]](https://issues.apache.org/jira/browse/SPARK-56300) Add Java-friendly factory method to `KubernetesDriverSpec`
  - [[SPARK-56303]](https://issues.apache.org/jira/browse/SPARK-56303) Add Java-friendly factory methods to `JavaMainAppResource`
  - [[SPARK-56490]](https://issues.apache.org/jira/browse/SPARK-56490) Add Java-friendly `KubernetesConf.createDriverConf`
  - [[SPARK-56574]](https://issues.apache.org/jira/browse/SPARK-56574) Add Java-friendly `KubernetesDriverSpec.getSystemPropertiesAsJavaMap`
  - [[SPARK-56590]](https://issues.apache.org/jira/browse/SPARK-56590) Add Java-friendly getters for driver resources of KubernetesDriverSpec
  - [[SPARK-56600]](https://issues.apache.org/jira/browse/SPARK-56600) Promote `SparkPod` to `Stable`
  - [[SPARK-56601]](https://issues.apache.org/jira/browse/SPARK-56601) Promote `KubernetesClientUtils` to `Stable`
  - [[SPARK-56602]](https://issues.apache.org/jira/browse/SPARK-56602) Promote `KubernetesVolumeUtils` to `Stable`
  - [[SPARK-56604]](https://issues.apache.org/jira/browse/SPARK-56604) Promote `KubernetesDriverBuilder` to `Stable`
  - [[SPARK-56623]](https://issues.apache.org/jira/browse/SPARK-56623) Promote `KubernetesDriverSpec` to `Stable`
  - [[SPARK-56624]](https://issues.apache.org/jira/browse/SPARK-56624) Promote `KubernetesUtils` to `Stable`
  - [[SPARK-56736]](https://issues.apache.org/jira/browse/SPARK-56736) Add `sparkVersion` method to KubernetesConf abstract class
- **Reduce K8s control plane overhead** ([[SPARK-55400]](https://issues.apache.org/jira/browse/SPARK-55400))
  - [[SPARK-55370]](https://issues.apache.org/jira/browse/SPARK-55370) Improve `annotateExecutorDeletionCost` to use `patch` instead of `edit` API
  - [[SPARK-55377]](https://issues.apache.org/jira/browse/SPARK-55377) Improve `labelDecommissioningExecs` to use `patch` instead of `edit` API
  - [[SPARK-55399]](https://issues.apache.org/jira/browse/SPARK-55399) Improve `KubernetesDriverEndpoint` to use `patch` instead of `edit` API
  - [[SPARK-55410]](https://issues.apache.org/jira/browse/SPARK-55410) Improve `SparkKubernetesDiagnosticsSetter` to use `patch` instead of `edit` API
  - [[SPARK-55603]](https://issues.apache.org/jira/browse/SPARK-55603) Improve `removeExecutorFromK8s` to use `patch` instead of `edit` API
  - [[SPARK-56793]](https://issues.apache.org/jira/browse/SPARK-56793) Avoid cluster-wide LIST in executor pods polling
- **Improve Web Security** ([[SPARK-55556]](https://issues.apache.org/jira/browse/SPARK-55556))
  - [[SPARK-55653]](https://issues.apache.org/jira/browse/SPARK-55653) Support `NetworkPolicy` for Spark executor pods
  - [[SPARK-55193]](https://issues.apache.org/jira/browse/SPARK-55193) Use CompressionHandler as a replacement for the deprecated GzipHandler in JettyUtils
  - [[SPARK-55252]](https://issues.apache.org/jira/browse/SPARK-55252) Improve `HttpSecurityFilter` to add `Content-Security-Policy` header
  - [[SPARK-55522]](https://issues.apache.org/jira/browse/SPARK-55522) Web UI has been broken since Content-Security-Policy was introduced
  - [[SPARK-56528]](https://issues.apache.org/jira/browse/SPARK-56528) Make Jetty SniHostCheck configurable
- [[SPARK-54553]](https://issues.apache.org/jira/browse/SPARK-54553) Supports receiving podgroup JSON format configurations when using Volcano
- [[SPARK-54916]](https://issues.apache.org/jira/browse/SPARK-54916) Enable `volcano` profile by default

### Connectors
- [[SPARK-53469]](https://issues.apache.org/jira/browse/SPARK-53469) Ability to cleanup shuffle generated from SQL executed in thrift server
- [[SPARK-55928]](https://issues.apache.org/jira/browse/SPARK-55928) New linter for config effectiveness in views, UDFs and procedures

### Build and Infrastructure
- **Build and Run Spark on Java 25** ([[SPARK-51167]](https://issues.apache.org/jira/browse/SPARK-51167))
  - [[SPARK-55809]](https://issues.apache.org/jira/browse/SPARK-55809) HeapHistogram stuck on JDK 25
  - [[SPARK-53226]](https://issues.apache.org/jira/browse/SPARK-53226) Spark-Shell run fails with Java 22 ~ 25
  - [[SPARK-53327]](https://issues.apache.org/jira/browse/SPARK-53327) Datasketches does not support Java 25
  - [[SPARK-55670]](https://issues.apache.org/jira/browse/SPARK-55670) Add `-Dio.netty.noUnsafe=false` to enable Arrow Java 25 support
  - [[SPARK-55678]](https://issues.apache.org/jira/browse/SPARK-55678) Add daily test for Java 25
  - [[SPARK-55679]](https://issues.apache.org/jira/browse/SPARK-55679) Fix dectecting `sun.io.serialization.extendedDebugInfo` on Java 25
  - [[SPARK-55682]](https://issues.apache.org/jira/browse/SPARK-55682) ServiceLoader returned iterator may throw NoClassDefFoundError on hasNext()
  - [[SPARK-55686]](https://issues.apache.org/jira/browse/SPARK-55686) SizeEstimator takes care of Compact Object Headers
  - [[SPARK-55714]](https://issues.apache.org/jira/browse/SPARK-55714) JDK 25 might throw ArithmeticException without message
  - [[SPARK-56834]](https://issues.apache.org/jira/browse/SPARK-56834) Use Java `25-jre` instead of `21-jre` image in K8s Dockerfile
- **Remove pre-built test JAR and class files from the repository** ([[SPARK-56352]](https://issues.apache.org/jira/browse/SPARK-56352))
- **Share compile artifact across CI jobs** ([[SPARK-56830]](https://issues.apache.org/jira/browse/SPARK-56830))

### Version upgrade of Java and Scala libraries

| Library Name                     | Version Change      |
| :------------------------------- | :------------------ |
| HdrHistogram | -> 2.1.12 (NEW) |
| RoaringBitmap | 1.3.0 -> 1.6.10 |
| aircompressor | 2.0.2 -> 2.0.3 |
| aliyun-java-core | -> 0.2.11-beta (NEW) |
| aliyun-sdk-oss | 3.13.2 -> 3.18.1 |
| analyticsaccelerator-s3 | 1.3.0 -> 1.3.1 |
| arpack | 3.0.4 -> 3.2.0 |
| arrow-compression | 18.3.0 -> 19.0.0 |
| arrow-format | 18.3.0 -> 19.0.0 |
| arrow-memory-core | 18.3.0 -> 19.0.0 |
| arrow-memory-netty | 18.3.0 -> 19.0.0 |
| arrow-memory-netty-buffer-patch | 18.3.0 -> 19.0.0 |
| arrow-vector | 18.3.0 -> 19.0.0 |
| blas | 3.0.4 -> 3.2.0 |
| bundle | 2.29.52 -> 2.35.4 |
| commons-cli | 1.10.0 -> 1.11.0 |
| commons-codec | 1.19.0 -> 1.22.0 |
| commons-io | 2.21.0 -> 2.22.0 |
| commons-lang3 | 3.19.0 -> 3.20.0 |
| commons-text | 1.14.0 -> 1.15.0 |
| compress-lzf | 1.1.2 -> 1.2.0 |
| dom4j | -> 2.1.4 (NEW) |
| gson | 2.11.0 -> 2.13.2 |
| guava | 33.4.8-jre -> 33.6.0-jre |
| hadoop-aliyun | 3.4.2 -> 3.5.0 |
| hadoop-annotations | 3.4.2 -> 3.5.0 |
| hadoop-aws | 3.4.2 -> 3.5.0 |
| hadoop-azure | 3.4.2 -> 3.5.0 |
| hadoop-azure-datalake | 3.4.2 -> 3.5.0 |
| hadoop-client-api | 3.4.2 -> 3.5.0 |
| hadoop-client-runtime | 3.4.2 -> 3.5.0 |
| hadoop-cloud-storage | 3.4.2 -> 3.5.0 |
| hadoop-gcp | -> 3.5.0 (NEW) |
| hadoop-huaweicloud | 3.4.2 -> 3.5.0 |
| hadoop-shaded-guava | 1.4.0 -> 1.5.0 |
| icu4j | 77.1 -> 78.3 |
| jackson-annotations | 2.20 -> 2.21 |
| jackson-core | 2.20.0 -> 2.21.2 |
| jackson-databind | 2.20.0 -> 2.21.2 |
| jackson-dataformat-cbor | 2.20.0 -> 2.21.2 |
| jackson-dataformat-yaml | 2.20.0 -> 2.21.2 |
| jackson-datatype-jsr310 | 2.20.0 -> 2.21.2 |
| jackson-module-scala_2.13 | 2.20.0 -> 2.21.2 |
| jakarta.activation-api | 2.1.3 -> 2.1.4 |
| jakarta.servlet-api | 5.0.0 -> 6.0.0 |
| jakarta.ws.rs-api | 3.0.0 -> 3.1.0 |
| jakarta.xml.bind-api | 4.0.2 -> 4.0.5 |
| java-trace-api | -> 0.2.11-beta (NEW) |
| jaxb-core | 4.0.5 -> 4.0.6 |
| jaxb-runtime | 4.0.5 -> 4.0.6 |
| jdom2 | 2.0.6 -> 2.0.6.1 |
| jersey-client | 3.0.18 -> 3.1.11 |
| jersey-common | 3.0.18 -> 3.1.11 |
| jersey-container-servlet | 3.0.18 -> 3.1.11 |
| jersey-container-servlet-core | 3.0.18 -> 3.1.11 |
| jersey-hk2 | 3.0.18 -> 3.1.11 |
| jersey-server | 3.0.18 -> 3.1.11 |
| jetty-util | 11.0.26 -> REMOVED |
| jetty-util-ajax | 11.0.26 -> REMOVED |
| jjwt-api | 0.12.6 -> 0.13.0 |
| jjwt-impl | 0.12.6 -> 0.13.0 |
| jjwt-jackson | 0.12.6 -> 0.13.0 |
| joda-time | 2.14.0 -> 2.14.1 |
| kubernetes-client | 7.4.0 -> 7.6.1 |
| kubernetes-client-api | 7.4.0 -> 7.6.1 |
| kubernetes-httpclient-vertx | 7.4.0 -> 7.6.1 |
| kubernetes-model-admissionregistration | 7.4.0 -> 7.6.1 |
| kubernetes-model-apiextensions | 7.4.0 -> 7.6.1 |
| kubernetes-model-apps | 7.4.0 -> 7.6.1 |
| kubernetes-model-autoscaling | 7.4.0 -> 7.6.1 |
| kubernetes-model-batch | 7.4.0 -> 7.6.1 |
| kubernetes-model-certificates | 7.4.0 -> 7.6.1 |
| kubernetes-model-common | 7.4.0 -> 7.6.1 |
| kubernetes-model-coordination | 7.4.0 -> 7.6.1 |
| kubernetes-model-core | 7.4.0 -> 7.6.1 |
| kubernetes-model-discovery | 7.4.0 -> 7.6.1 |
| kubernetes-model-events | 7.4.0 -> 7.6.1 |
| kubernetes-model-extensions | 7.4.0 -> 7.6.1 |
| kubernetes-model-flowcontrol | 7.4.0 -> 7.6.1 |
| kubernetes-model-gatewayapi | 7.4.0 -> 7.6.1 |
| kubernetes-model-metrics | 7.4.0 -> 7.6.1 |
| kubernetes-model-networking | 7.4.0 -> 7.6.1 |
| kubernetes-model-node | 7.4.0 -> 7.6.1 |
| kubernetes-model-policy | 7.4.0 -> 7.6.1 |
| kubernetes-model-rbac | 7.4.0 -> 7.6.1 |
| kubernetes-model-resource | 7.4.0 -> 7.6.1 |
| kubernetes-model-scheduling | 7.4.0 -> 7.6.1 |
| kubernetes-model-storageclass | 7.4.0 -> 7.6.1 |
| lapack | 3.0.4 -> 3.2.0 |
| log4j-1.2-api | 2.24.3 -> 2.25.4 |
| log4j-api | 2.24.3 -> 2.25.4 |
| log4j-core | 2.24.3 -> 2.25.4 |
| log4j-layout-template-json | 2.24.3 -> 2.25.4 |
| log4j-slf4j2-impl | 2.24.3 -> 2.25.4 |
| lz4-java | 1.8.0 -> 1.11.0 |
| netty-all | 4.2.7.Final -> 4.2.13.Final |
| netty-buffer | 4.2.7.Final -> 4.2.13.Final |
| netty-codec | 4.2.7.Final -> 4.2.13.Final |
| netty-codec-base | 4.2.7.Final -> 4.2.13.Final |
| netty-codec-classes-quic | 4.2.7.Final -> REMOVED |
| netty-codec-compression | 4.2.7.Final -> 4.2.13.Final |
| netty-codec-dns | 4.2.7.Final -> 4.2.13.Final |
| netty-codec-http | 4.2.7.Final -> 4.2.13.Final |
| netty-codec-http2 | 4.2.7.Final -> 4.2.13.Final |
| netty-codec-http3 | 4.2.7.Final -> REMOVED |
| netty-codec-marshalling | 4.2.7.Final -> REMOVED |
| netty-codec-native-quic | 4.2.7.Final -> REMOVED |
| netty-codec-protobuf | 4.2.7.Final -> REMOVED |
| netty-codec-socks | 4.2.7.Final -> 4.2.13.Final |
| netty-common | 4.2.7.Final -> 4.2.13.Final |
| netty-handler | 4.2.7.Final -> 4.2.13.Final |
| netty-handler-proxy | 4.2.7.Final -> 4.2.13.Final |
| netty-resolver | 4.2.7.Final -> 4.2.13.Final |
| netty-resolver-dns | 4.2.7.Final -> 4.2.13.Final |
| netty-tcnative-boringssl-static | 2.0.74.Final -> 2.0.76.Final |
| netty-tcnative-classes | 2.0.74.Final -> 2.0.76.Final |
| netty-transport | 4.2.7.Final -> 4.2.13.Final |
| netty-transport-classes-epoll | 4.2.7.Final -> 4.2.13.Final |
| netty-transport-classes-io_uring | 4.2.7.Final -> REMOVED |
| netty-transport-classes-kqueue | 4.2.7.Final -> 4.2.13.Final |
| netty-transport-native-epoll | 4.2.7.Final -> 4.2.13.Final |
| netty-transport-native-io_uring | 4.2.7.Final -> REMOVED |
| netty-transport-native-kqueue | 4.2.7.Final -> 4.2.13.Final |
| netty-transport-native-unix-common | 4.2.7.Final -> 4.2.13.Final |
| objenesis | 3.4 -> 3.5 |
| opentelemetry-api | -> 1.49.0 (NEW) |
| opentelemetry-context | -> 1.49.0 (NEW) |
| orc-core | 2.2.1 -> 2.3.0 |
| orc-mapreduce | 2.2.1 -> 2.3.0 |
| orc-shims | 2.2.1 -> 2.3.0 |
| parquet-column | 1.16.0 -> 1.17.0 |
| parquet-common | 1.16.0 -> 1.17.0 |
| parquet-encoding | 1.16.0 -> 1.17.0 |
| parquet-format-structures | 1.16.0 -> 1.17.0 |
| parquet-hadoop | 1.16.0 -> 1.17.0 |
| parquet-jackson | 1.16.0 -> 1.17.0 |
| reactive-streams | -> 1.0.3 (NEW) |
| scala-compiler | 2.13.17 -> 2.13.18 |
| scala-library | 2.13.17 -> 2.13.18 |
| scala-reflect | 2.13.17 -> 2.13.18 |
| snakeyaml | 2.4 -> 2.5 |
| snakeyaml-engine | 2.10 -> 3.0.1 |
| tink | 1.16.0 -> 1.20.0 |
| vertx-auth-common | 4.5.14 -> 4.5.26 |
| vertx-core | 4.5.14 -> 4.5.26 |
| vertx-uri-template | -> 4.5.26 (NEW) |
| vertx-web-client | 4.5.14 -> 4.5.26 |
| vertx-web-common | 4.5.14 -> 4.5.26 |
| volcano-client | -> 7.6.1 (NEW) |
| volcano-model | -> 7.6.1 (NEW) |
| xbean-asm9-shaded | 4.28 -> 4.30 |
| xz | 1.10 -> 1.12 |
| zjsonpatch | 7.4.0 -> 7.6.1 |
| zookeeper | 3.9.4 -> 3.9.5 |
| zookeeper-jute | 3.9.4 -> 3.9.5 |
| zstd-jni | 1.5.7-6 -> 1.5.7-7 |

### Credits

Last but not least, this release would not have been possible without the following contributors: AbinayaJayaprakasam, Adam Binford, Adithya Ajith, Aditya Nambiar, Akash Nayar, Albert Sugranyes, Aleksandr Chernousov, Alex Khakhlyuk, Alexis Schlomer, Allison Wang, Amanda Liu, Anastasiia Terenteva, Anastasiia Terenteva, Andreas Chatzistergiou, Andreas Neumann, Angerszhuuuu, AnishMahto, Anshul Baliga, antban, Anton Lykov, Anton Okolnychyi, Antonio Blanco, Anupam Yadav, ashrithb, Asif Hussain Shahid, Attila Zsolt Piros, beliefer, Biruk Tesfaye, Bjørn Jørgensen, Bo Zhang, Bobby Wang, Brooks Walls, Burak Yavuz, cafri.sun, Celeste Horgan, Chang chen, Chao Sun, Chen Wang, Cheng Pan, Chenhao Li, Chirag Singh, Chris Boumalhab, ChuckLin2025, cty123, cuiyanxiang, Daniel Tenedorio, David Milicevic, David Roberts, David Tagatac, David Young, DB Tsai, DenineLu, Devin Petersohn, DhruvArya, Dilip Biswal, Dmytro Fedoriaka, Dmytro Fedoriaka, donaldchai, Dongjoon Hyun, Dylan Wong, Eddie Bkheet, Emilie Faracci, Eren Avsarogullari, Eric Yang, ericm-db, EugenYushin, Fangchen Li, fanyue-xia, Felipe Fujiy Pessoto, Felix, Filip Darmanovic, Filip Davidovic, Fu Chen, Ganesha S, gaoyajun02, Garland Zhang, Gengliang Wang, Gera Shegalov, Gurpreet Nanda, Haiyang Sun, haoyangeng-db, Harsh Motwani, Helios He, Herman van Hövell, Holden Karau, holyvolcano, Hongze Zhang, huangxiaoping, huanliwang-db, Hyukjin Kwon, ibenchhida, ilicmarkodb, Ivan Sadikov, Jacek Laskowski, Jacky Wang, Jahnavi Nelavelli, jameswillis, Jarek Potiuk, jbharadw-oai, Jerry Peng, Jerry Zheng, Jessie Luo, Jia Teoh, Jim Halfpenny, Jitesh Soni, Jiwon Park, Johan Lasperas, John Xu, John Zhuge, Jon Mio, Joon Ro, judy, Juliusz Sompolski, Juliusz Sompolski, Jungtaek Lim, Junyu Chen, Karthik Prabhakar, Karuppayya Rajendran, Kavpreet Grewal, Kazuyuki Tanimura, Ke Jia, Kelvin Jiang, Kent Yao, kepler62f, Kiyeon Jeon, Kousuke Saruta, Kris Mok, Kristin Cowalcijk, Leon Windheuser, lepan, Liang-Chi Hsieh, Linhong Liu, Livia Zhu, Luca Canali, manuzhang, Marcin Wojtyczka, Marco Gaido, mariaselvam.nishanth, Mark Jarvin, Mark Molinaro, Marko Sisovic, Martin Grund, Matt Zhang, micheal-o, Mihailo Timotic, mihailoale-db, Mikhail Nikoliukin, Milan Dankovic, Naveen Kumar Puppala, Nicholas Chew, Nikolina Vraneš, nyaapa, Pablo Langa, Parth Chandra, pavle-martinovic_data, Petar Nikić, Peter Toth, pranavdev022, Pratham Manja, Pratham Manja, Puneet Dixit, Qiegang Long, qindongliang, Rahul Sharma, Richard Chen, RishbhaJain, Rito Takeuchi, Robert Dillitz, ruanwenjun, Ruifeng Zheng, sahilkumarsingh, Sandro Sp, Sandy Ryza, Serge Rielau, Shilong Duan, Shrirang Mhalgi, Shuai Lu, Shubhambhusate, Shujing Yang, Simola Nayak, Siying Dong, st-tran, Stanley Yao, Stefan Kandic, Stefan Savić, Stevo Mitric, susheel-aroskar, Sven Weber, sychen, Szehon Ho, Takuya Ueshin, tangrizzly, Tengfei Huang, Thang Long VU, Tian Gao, Tim Lee, TongWei1105, tugce-applied, Ubuntu, Uros Bojanic, Uros Stankovic, Victor Sunderland, VINDHYA G BHAT, vinodkc, Vlad Rozov, Vladan Vasić, Vladimir Golubev, Wei Liu, Weichen Xu, Wenchen Fan, wforget, WHJian, Wojciech Szlachta, Xi Lyu, Xiang Li, Xiang LI, Xianming Lei, xianzhe-databricks, Xiaonan Yang, Xiaoxuan Li, xihuan_mstr, Xin Huang, Xingbo Jiang, Xinyi Yu, yamayuki-hub, Yan Yan, yangjie01, Yash Botadra, yhuang-db, Yi Wu, Yicong-Huang, Yihong He, Yuchen Liu, Yuheng Chang, Yuming Wang, Zequn Lin, zeruibao, zhidongqu-db, zifeif2, Ziya Mukhtarov, zml1206, Zoey Han, zouxxyy
