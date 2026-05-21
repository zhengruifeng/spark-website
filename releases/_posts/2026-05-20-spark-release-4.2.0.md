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
- [[SPARK-55139]](https://issues.apache.org/jira/browse/SPARK-55139) Support Pandas 3 (47 commits)
- [[SPARK-51658]](https://issues.apache.org/jira/browse/SPARK-51658) SPIP: Add geospatial types in Spark (40 commits)
- [[SPARK-55760]](https://issues.apache.org/jira/browse/SPARK-55760) Spark Web UI Modernization (40 commits)
- [[SPARK-55555]](https://issues.apache.org/jira/browse/SPARK-55555) Support heterogeneous K8s executor management (21 commits)
- [[SPARK-53484]](https://issues.apache.org/jira/browse/SPARK-53484) SPIP: JDBC Driver for Spark Connect (19 commits)
- [[SPARK-51727]](https://issues.apache.org/jira/browse/SPARK-51727) SPIP: Declarative Pipelines (19 commits)
- [[SPARK-54955]](https://issues.apache.org/jira/browse/SPARK-54955) Pandas UDF with PyArrow Backend (15 commits)
- [[SPARK-56603]](https://issues.apache.org/jira/browse/SPARK-56603) Improve K8s Resource Manager API (14 commits)
- [[SPARK-55227]](https://issues.apache.org/jira/browse/SPARK-55227) RDD API compatibility (13 commits)
- [[SPARK-54274]](https://issues.apache.org/jira/browse/SPARK-54274) Support `MERGE INTO` Schema Evolution (12 commits)
- [[SPARK-51167]](https://issues.apache.org/jira/browse/SPARK-51167) Build and Run Spark on Java 25 (12 commits)
- [[SPARK-55668]](https://issues.apache.org/jira/browse/SPARK-55668) Change Data Capture (CDC) Support (12 commits)
- [[SPARK-54357]](https://issues.apache.org/jira/browse/SPARK-54357) Improve SparkConnect usability and performance (11 commits)
- [[SPARK-54016]](https://issues.apache.org/jira/browse/SPARK-54016) Improve K8s support in Spark 4.1.0 (8 commits)
- [[SPARK-46156]](https://issues.apache.org/jira/browse/SPARK-46156) Add missing parameters for Pandas API on Spark (8 commits)
- [[SPARK-55722]](https://issues.apache.org/jira/browse/SPARK-55722) Optimize Vectorized Data Loading (8 commits)
- [[SPARK-55400]](https://issues.apache.org/jira/browse/SPARK-55400) Reduce K8s control plane overhead (6 commits)
- [[SPARK-54249]](https://issues.apache.org/jira/browse/SPARK-54249) Improve Spark Event Log, History Server, and Web UI (5 commits)

### Spark Core
- **Build and Run Spark on Java 25** ([[SPARK-51167]](https://issues.apache.org/jira/browse/SPARK-51167))
  - [[SPARK-55809]](https://issues.apache.org/jira/browse/SPARK-55809) Re-implements `Utils.getHeapHistogram` to use `DiagnosticCommandMBean` in-process instead of spawning `jmap` as a subprocess.
  - [[SPARK-53226]](https://issues.apache.org/jira/browse/SPARK-53226) Make ClosureCleaner work with Java22+
  - [[SPARK-55679]](https://issues.apache.org/jira/browse/SPARK-55679) Fix dectecting `sun.io.serialization.extendedDebugInfo` on Java 25
  - [[SPARK-55686]](https://issues.apache.org/jira/browse/SPARK-55686) SizeEstimator takes care of Compact Object Headers
- **Improve Spark History Server Scalability** ([[SPARK-56287]](https://issues.apache.org/jira/browse/SPARK-56287))
  - [[SPARK-55793]](https://issues.apache.org/jira/browse/SPARK-55793) Adds support for configuring Spark History Server to monitor event logs from multiple directories (comma-separated in `spark.history.fs.logDirectory`), optionally naming each source via `spark.history.fs.logDirectory.names`, and updates the History UI to show and filter by a new “Log Source” column (with the event log directory section collapsing when multiple sources are set).
  - [[SPARK-56234]](https://issues.apache.org/jira/browse/SPARK-56234) Adds a new config `spark.history.fs.update.scanDisabledPathPatterns` that allows disabling periodic log directory scanning by path pattern in SHS.
  - [[SPARK-56044]](https://issues.apache.org/jira/browse/SPARK-56044) HistoryServerDiskManager does not delete app store on release when app is not in active map
  - [[SPARK-56278]](https://issues.apache.org/jira/browse/SPARK-56278) Populate accurate metadata immediately during on-demand loading in SHS
- **DAGScheduler Stability/Performance improvements** ([[SPARK-56494]](https://issues.apache.org/jira/browse/SPARK-56494))
- **Improve Web Security** ([[SPARK-55556]](https://issues.apache.org/jira/browse/SPARK-55556))
  - [[SPARK-55252]](https://issues.apache.org/jira/browse/SPARK-55252) Improve `HttpSecurityFilter` to add `Content-Security-Policy` header
  - [[SPARK-56528]](https://issues.apache.org/jira/browse/SPARK-56528) Make Jetty SniHostCheck configurable
- **Support heterogeneous K8s executor management** ([[SPARK-55555]](https://issues.apache.org/jira/browse/SPARK-55555))
  - [[SPARK-55359]](https://issues.apache.org/jira/browse/SPARK-55359) Promote `TaskResourceRequest` to `Stable`
  - [[SPARK-55757]](https://issues.apache.org/jira/browse/SPARK-55757) Improve `spark.task.cpus` validation
- [[SPARK-51165]](https://issues.apache.org/jira/browse/SPARK-51165) Proposes enabling `spark.master.rest.enabled` by default in Apache Spark 4.1.0.
- [[SPARK-53807]](https://issues.apache.org/jira/browse/SPARK-53807) Addresses race condition issues between `unlock` and `releaseAllLocksForTask` methods in the `BlockInfoManager` class.
- [[SPARK-54170]](https://issues.apache.org/jira/browse/SPARK-54170) Use StructuredLogging message in Scala side
- [[SPARK-54219]](https://issues.apache.org/jira/browse/SPARK-54219) Introduces support for a new configuration `spark.cleaner.referenceTracking.blocking.timeout`.
- [[SPARK-54312]](https://issues.apache.org/jira/browse/SPARK-54312) Addresses an issue in the Apache Spark standalone worker where tasks for sending heartbeats and cleaning the work directory were scheduled multiple times if the worker registered multiple times due to heartbeat timeouts or disconnection from the master.
- [[SPARK-54313]](https://issues.apache.org/jira/browse/SPARK-54313) Introduces a `--extra-properties-file` option in `spark-submit` to support configuration layering, allowing users to specify multiple properties files.
- [[SPARK-54556]](https://issues.apache.org/jira/browse/SPARK-54556) Addresses handling shuffle checksum mismatches by rolling back and resubmitting succeeding shuffle map stages.
- [[SPARK-54808]](https://issues.apache.org/jira/browse/SPARK-54808) Extends the qualified naming ability to session temporary views, allowing users to explicitly disambiguate between a session temporary view and a persisted view.
- [[SPARK-54830]](https://issues.apache.org/jira/browse/SPARK-54830) Enables the checksum-based indeterminate shuffle retry feature by default.
- [[SPARK-55051]](https://issues.apache.org/jira/browse/SPARK-55051) Updates `JavaUtils.byteStringAs` to accept IEC binary unit suffixes like `Ki`, `KiB`, `Mi`, `MiB`, `Gi`, `GiB`, `Ti`, `TiB`, and `Pi`, `PiB` when parsing byte-size configuration values.
- [[SPARK-55964]](https://issues.apache.org/jira/browse/SPARK-55964) Adds a SQL config allowing users to choose whether functions in persisted schemas with name collisions against BUILTIN or SESSION are shadowed by builtin functions when partially qualified (e.g., `builtin.foo()`).
- [[SPARK-55991]](https://issues.apache.org/jira/browse/SPARK-55991) Fixes SQL parameter substitution to correctly handle Unicode supplementary characters (e.g., emojis) so the SQL text isn’t corrupted during marker replacement.
- [[SPARK-56279]](https://issues.apache.org/jira/browse/SPARK-56279) Modifies `MessageEncoder` to emit the header `ByteBuf` and `FileRegion` as separate objects for `FileSegmentManagedBuffer`, enabling native transports (EPOLL/KQUEUE) to use optimized `sendfile()`/`splice()` zero-copy paths instead of falling back to user-space copy via `FileRegion.transferTo()`.
- [[SPARK-56298]](https://issues.apache.org/jira/browse/SPARK-56298) Changes the default of `spark.master.rest.virtualThread.enabled` from `false` to `true`.
- [[SPARK-56302]](https://issues.apache.org/jira/browse/SPARK-56302) Eagerly nulls intermediate objects during task result serialization in `Executor.TaskRunner.run()` to reduce peak heap memory usage.
- [[SPARK-56330]](https://issues.apache.org/jira/browse/SPARK-56330) Adds a new `TaskInterruptListener` DeveloperApi interface that fires immediately when a task is interrupted via `markInterrupted`, enabling push-style reactions to task cancellation.
- [[SPARK-56491]](https://issues.apache.org/jira/browse/SPARK-56491) Adds a `getAllAsJavaMap` method to the `SparkConf` trait that returns `java.util.Map[String, String]`.
- [[SPARK-56501]](https://issues.apache.org/jira/browse/SPARK-56501) Introduces the `SET PATH` command with structured session state on `CatalogManager`, gated by the new master switch `spark.sql.path.enabled` (default `false`).

### SQL Foundation
- **Refactor Scala/SQL Tests** ([[SPARK-54819]](https://issues.apache.org/jira/browse/SPARK-54819))
- **Improve JDBC example and test coverage** ([[SPARK-55581]](https://issues.apache.org/jira/browse/SPARK-55581))
- **Support `MERGE INTO` Schema Evolution** ([[SPARK-54274]](https://issues.apache.org/jira/browse/SPARK-54274))
  - [[SPARK-53482]](https://issues.apache.org/jira/browse/SPARK-53482) Enhances the MERGE INTO functionality to support scenarios where the source dataset has fewer nested fields than the target.
  - [[SPARK-54621]](https://issues.apache.org/jira/browse/SPARK-54621) Modifies the behavior of the 'struct coercion' feature for the MERGE INTO operation in Spark SQL.
  - [[SPARK-54172]](https://issues.apache.org/jira/browse/SPARK-54172) Merge Into Schema Evolution should only add referenced columns
  - [[SPARK-54289]](https://issues.apache.org/jira/browse/SPARK-54289) Allow MERGE INTO to preserve existing struct fields for UPDATE SET * when source struct has less nested fields than target struct
  - [[SPARK-54496]](https://issues.apache.org/jira/browse/SPARK-54496) Fix Merge Into Schema Evolution for Dataframe API
  - [[SPARK-54525]](https://issues.apache.org/jira/browse/SPARK-54525) Disable nested struct coercion in MERGE INTO under a config
  - [[SPARK-54578]](https://issues.apache.org/jira/browse/SPARK-54578) Perform Code Cleanup on `AssignmentUtils`
  - [[SPARK-54595]](https://issues.apache.org/jira/browse/SPARK-54595) Keep existing behavior of MERGE INTO without SCHEMA EVOLUTION clause
  - [[SPARK-56054]](https://issues.apache.org/jira/browse/SPARK-56054) Fix aliased nested fields ignored for schema evolution in MERGE
  - [[SPARK-56472]](https://issues.apache.org/jira/browse/SPARK-56472) Fix MERGE schema evolution with WHEN MATCHED THEN DELETE
- **Optimize Vectorized Data Loading** ([[SPARK-55722]](https://issues.apache.org/jira/browse/SPARK-55722))
  - [[SPARK-55517]](https://issues.apache.org/jira/browse/SPARK-55517) Optimize `VectorizedPlainValuesReader.readBytes()` with direct array access for heap buffers
  - [[SPARK-55652]](https://issues.apache.org/jira/browse/SPARK-55652) Optimize `VectorizedPlainValuesReader.readShorts()` with direct array access for heap buffers
  - [[SPARK-55683]](https://issues.apache.org/jira/browse/SPARK-55683) Optimize `VectorizedPlainValuesReader.readUnsignedLongs`
  - [[SPARK-55739]](https://issues.apache.org/jira/browse/SPARK-55739) Optimize `OnHeapColumnVector.putIntsLittleEndian/putLongsLittleEndian` using `Platform.copyMemory` on little-endian platforms
  - [[SPARK-55885]](https://issues.apache.org/jira/browse/SPARK-55885) Optimize vectorized Parquet boolean reading with lookup-table expansion and batch buffer reads
  - [[SPARK-55962]](https://issues.apache.org/jira/browse/SPARK-55962) Use `getShort` instead of `getInt` casting in `putShortsFromIntsLittleEndian` on Little Endian platforms
  - [[SPARK-56438]](https://issues.apache.org/jira/browse/SPARK-56438) Optimize `VectorizedPlainValuesReader.readBinary` for direct ByteBuffer by eliminating intermediate bytecopy
  - [[SPARK-56522]](https://issues.apache.org/jira/browse/SPARK-56522) Batch PACKED null/non-null runs in `VectorizedRleValuesReader`
- **Change Data Capture (CDC) Support** ([[SPARK-55668]](https://issues.apache.org/jira/browse/SPARK-55668))
  - [[SPARK-55948]](https://issues.apache.org/jira/browse/SPARK-55948) Introduces the DSv2 Change Data Capture framework with new connector interfaces (`Changelog`, `ChangelogInfo`, `ChangelogRange`), analyzer resolution rules, and SQL `CHANGES` clause syntax (`SELECT * FROM table CHANGES FROM VERSION 1 TO VERSION 5`).
  - [[SPARK-55952]](https://issues.apache.org/jira/browse/SPARK-55952) Re-applies the `ResolveChangelogTable` analyzer rule from `881957a4` (which was reverted in `fe6051a`) along with the missing `ProtoToParsedPlanTestSuite` fixtures that caused the original revert.
  - [[SPARK-55953]](https://issues.apache.org/jira/browse/SPARK-55953) Adds the `netChanges` deduplication mode to `ResolveChangelogTable` for batch CDC reads, completing the per-SPIP net-change post-processing capability.
  - [[SPARK-56686]](https://issues.apache.org/jira/browse/SPARK-56686) Implements row-level CDC post-processing (carry-over removal, update detection) for DSv2 streaming reads, which previously rejected all post-processing with a blanket `STREAMING_POST_PROCESSING_NOT_SUPPORTED` error.
  - [[SPARK-56687]](https://issues.apache.org/jira/browse/SPARK-56687) Completes the DSv2 CDC streaming post-processing surface by implementing `deduplicationMode = netChanges` for streaming reads.
  - [[SPARK-55951]](https://issues.apache.org/jira/browse/SPARK-55951) **[User-facing for connector developers]** Adds `ChangelogTable.validateSchema` which fail-fast checks at relation construction time that the connector schema contains the required CDC metadata columns (`_change_type` as `StringType`, `_commit_version` of connector-defined type, `_commit_timestamp` as `TimestampType`) and that `rowId()` returns a non-empty array when a capability requires row identity.
  - [[SPARK-56711]](https://issues.apache.org/jira/browse/SPARK-56711) Restrict CDC `_commit_version` column to LongType or StringType
- **SPIP: Constraints in DSv2** ([[SPARK-51207]](https://issues.apache.org/jira/browse/SPARK-51207))
  - [[SPARK-51695]](https://issues.apache.org/jira/browse/SPARK-51695) Introduces parser changes to support ANSI SQL-compatible table constraints in Apache Spark, including CHECK, UNIQUE, PRIMARY KEY, and FOREIGN KEY constraints.
  - [[SPARK-51771]](https://issues.apache.org/jira/browse/SPARK-51771) Introduces DSv2 APIs for ALTER TABLE ADD/DROP CONSTRAINT, adding AddConstraint and DropConstraint as per the specified SPIP document.
  - [[SPARK-51834]](https://issues.apache.org/jira/browse/SPARK-51834) Introduces support for end-to-end table constraint management, allowing users to create, replace, and alter DSV2 tables with constraints.
  - [[SPARK-55694]](https://issues.apache.org/jira/browse/SPARK-55694) Block constraint clauses (PRIMARY KEY, UNIQUE, CHECK, FOREIGN KEY) from being parsed in CREATE TABLE AS SELECT and REPLACE TABLE AS SELECT, since they’re unsupported and were previously accepted but silently ignored.
  - [[SPARK-52439]](https://issues.apache.org/jira/browse/SPARK-52439) Support check constraint with null value
- **SPIP: Add geospatial types in Spark** ([[SPARK-51658]](https://issues.apache.org/jira/browse/SPARK-51658))
  - [[SPARK-56771]](https://issues.apache.org/jira/browse/SPARK-56771) Flips the geospatial-support SQL config default to enabled in Spark 4.2, so geospatial types and ST functions (delivered under SPARK-51658) are available out of the box.
  - [[SPARK-54243]](https://issues.apache.org/jira/browse/SPARK-54243) Introduce type coercion support for GEOGRAPHY data types
  - [[SPARK-55174]](https://issues.apache.org/jira/browse/SPARK-55174) Move `Geo*ClientSuite` from `sql/core` to `sql/api` module
  - [[SPARK-56813]](https://issues.apache.org/jira/browse/SPARK-56813) Refine the documentation for geospatial types and functions
- **Spark Web UI Modernization** ([[SPARK-55760]](https://issues.apache.org/jira/browse/SPARK-55760))
  - [[SPARK-56792]](https://issues.apache.org/jira/browse/SPARK-56792) Adds pan and zoom controls to the SQL execution plan visualization on the SQL tab's execution detail page, wrapping the dagre-d3 SVG in a fixed-height viewport with a d3.zoom() behavior on an inner zoom-layer, a floating toolbar with -/percent/+ buttons, and +/-/0 keyboard shortcuts.
  - [[SPARK-56799]](https://issues.apache.org/jira/browse/SPARK-56799) Adds an in-graph node search to the SQL execution detail page next to the SPARK-56792 zoom toolbar: a magnifying-glass button (or `/` keyboard shortcut) opens a compact search input with a match counter and prev/next buttons, performing case-insensitive substring matches against operator names.
  - [[SPARK-56020]](https://issues.apache.org/jira/browse/SPARK-56020) Improve `GroupPartitions` Spark UI
  - [[SPARK-56587]](https://issues.apache.org/jira/browse/SPARK-56587) Modifies the DSv2 write physical execs (`AppendDataExec`, `OverwriteByExpressionExec`, `OverwritePartitionsDynamicExec`, `ReplaceDataExec`, `WriteDeltaExec`) to accept and store the destination `tableName`, and updates `nodeName` in the base `V2ExistingTableWriteExec` trait to include it.
- **Sql Scripting support for Spark SQL** ([[SPARK-48338]](https://issues.apache.org/jira/browse/SPARK-48338))
  - [[SPARK-54558]](https://issues.apache.org/jira/browse/SPARK-54558) Fix Internal Exception when Exception Handlers with no BEGIN/END are used
  - [[SPARK-55005]](https://issues.apache.org/jira/browse/SPARK-55005) Fix CONTINUE HANDLER to continue loop execution after handling exceptions in loop body
  - [[SPARK-55119]](https://issues.apache.org/jira/browse/SPARK-55119) Fix Continue Handler: prevent INTERNAL_ERROR and incorrect conditional statements interruption
- **Build and Run Spark on Java 25** ([[SPARK-51167]](https://issues.apache.org/jira/browse/SPARK-51167))
  - [[SPARK-53327]](https://issues.apache.org/jira/browse/SPARK-53327) Workaround datasketches-memory Java 25 support
  - [[SPARK-55682]](https://issues.apache.org/jira/browse/SPARK-55682) ServiceLoader returned iterator may throw `NoClassDefFoundError` on `hasNext()`
  - [[SPARK-55714]](https://issues.apache.org/jira/browse/SPARK-55714) JDK might throw ArithmeticException without message
- **Align DSv2 commands to DSv1 implementation** ([[SPARK-33392]](https://issues.apache.org/jira/browse/SPARK-33392))
  - [[SPARK-33902]](https://issues.apache.org/jira/browse/SPARK-33902) Adds V2 catalog support for `CREATE TABLE LIKE`, enabling N-part names (e.g., `catalog.namespace.table`) and V2 catalog targets.
  - [[SPARK-39660]](https://issues.apache.org/jira/browse/SPARK-39660) Implements `DESCRIBE [EXTENDED] TABLE <v2_table> PARTITION (...)` for V2 tables that implement `SupportsPartitionManagement`, bringing parity with V1/Hive (previously the command threw unconditionally).
  - [[SPARK-49543]](https://issues.apache.org/jira/browse/SPARK-49543) Adds `SHOW COLLATIONS` SQL command with optional `LIKE` pattern filtering, consistent with MySQL and Spark's `SHOW` command family.
- **Improve `Variant` data type support** ([[SPARK-52857]](https://issues.apache.org/jira/browse/SPARK-52857))
  - [[SPARK-54306]](https://issues.apache.org/jira/browse/SPARK-54306) Updates the parquet writer to annotate variant columns with the Parquet variant logical type annotation.
  - [[SPARK-54099]](https://issues.apache.org/jira/browse/SPARK-54099) XML variant parser should fall back to string on decimal parsing errors
- **SPIP: JDBC Driver for Spark Connect** ([[SPARK-53484]](https://issues.apache.org/jira/browse/SPARK-53484))
  - [[SPARK-54303]](https://issues.apache.org/jira/browse/SPARK-54303) Canonicalize error condition MISSING_CATALOG_ABILITY
  - [[SPARK-54638]](https://issues.apache.org/jira/browse/SPARK-54638) Reuse statement instances if possible in `SparkConnectJdbcDataTypeSuite`
- **SPIP: Add the TIME data type** ([[SPARK-51162]](https://issues.apache.org/jira/browse/SPARK-51162))
  - [[SPARK-54609]](https://issues.apache.org/jira/browse/SPARK-54609) Disable TIME type by default
  - [[SPARK-56152]](https://issues.apache.org/jira/browse/SPARK-56152) Enable implicit cast from STRING to TIME type
- **RDD API compatibility** ([[SPARK-55227]](https://issues.apache.org/jira/browse/SPARK-55227))
  - [[SPARK-55385]](https://issues.apache.org/jira/browse/SPARK-55385) Mitigate the recomputation in `zipWithIndex`
  - [[SPARK-55395]](https://issues.apache.org/jira/browse/SPARK-55395) Disable RDD cache in `DataFrame.zipWithIndex`
- **Search path support** ([[SPARK-54806]](https://issues.apache.org/jira/browse/SPARK-54806))
  - [[SPARK-54807]](https://issues.apache.org/jira/browse/SPARK-54807) Lets you explicitly qualify and reference built-in, session (temporary), and extension functions using namespaces like `builtin`/`system.builtin`, `session`/`system.session`, and `extension`/`system.extension`, while cleaning up function-resolution APIs, registering these qualified names so they can co-exist, and fixing a bug where session functions with the same name could incorrectly co-exist as both table and scalar functions.
  - [[SPARK-56639]](https://issues.apache.org/jira/browse/SPARK-56639) Wires frozen SQL `PATH` semantics into analysis for persisted views and SQL functions (scalar and table).
- **SPIP: Row-level operations in Data Source V2** ([[SPARK-35801]](https://issues.apache.org/jira/browse/SPARK-35801))
  - [[SPARK-53652]](https://issues.apache.org/jira/browse/SPARK-53652) Codegen for MergeRowExec
  - [[SPARK-56524]](https://issues.apache.org/jira/browse/SPARK-56524) Add operation metrics for UPDATE queries in DSv2
- [[SPARK-31561]](https://issues.apache.org/jira/browse/SPARK-31561) Adds the SQL `QUALIFY` clause to Spark SQL, allowing queries like `SELECT a, ROW_NUMBER() OVER (...) AS rn FROM t QUALIFY rn = 1` to filter on window-function results without an extra subquery or CTE.
- [[SPARK-36082]](https://issues.apache.org/jira/browse/SPARK-36082) Restricts the single-column null-aware anti-join broadcast-hash optimization (which builds the right side as a broadcast hash relation) to cases where the right side actually fits within the broadcast threshold; previously the planner picked it unconditionally once the logical pattern matched, even on right sides above the broadcast threshold.
- [[SPARK-44065]](https://issues.apache.org/jira/browse/SPARK-44065) Extends `OptimizeSkewedJoin` to split skewed partitions of `BroadcastHashJoin` stream plans when `localShuffleReader` is disabled.
- [[SPARK-44571]](https://issues.apache.org/jira/browse/SPARK-44571) Enhances the query optimization process by extending the existing `MergeScalarSubqueries` rule to also merge non-grouping aggregate subplans that return a single row.
- [[SPARK-46830]](https://issues.apache.org/jira/browse/SPARK-46830) Fix collation strength for parameter markers in EXECUTE IMMEDIATE
- [[SPARK-47672]](https://issues.apache.org/jira/browse/SPARK-47672) Updates Spark SQL’s filter pushdown optimizer to avoid pushing filters past projections when doing so would likely cause expensive expressions (e.g., UDFs) to be evaluated twice, improving performance while keeping query results unchanged.
- [[SPARK-51518]](https://issues.apache.org/jira/browse/SPARK-51518) Introduces support for using `|` as an alternative to `|>` for the SQL pipe operator token in Spark.
- [[SPARK-51712]](https://issues.apache.org/jira/browse/SPARK-51712) Reverts previous approaches and makes `spark.catalog.listTables()` return the list of tables even when there is an exception during table resolution, consistent with `SHOW TABLES` behavior.
- [[SPARK-52326]](https://issues.apache.org/jira/browse/SPARK-52326) Introduces partition-related events for external catalog operations such as create, drop, alter, and rename.
- [[SPARK-52407]](https://issues.apache.org/jira/browse/SPARK-52407) Introduces support for Theta Sketches in Spark SQL by adding seven new functions.
- [[SPARK-52729]](https://issues.apache.org/jira/browse/SPARK-52729) Exposes a DSv2 API for metadata-only tables, `CREATE VIEW`, and `ALTER VIEW ...
- [[SPARK-52857]](https://issues.apache.org/jira/browse/SPARK-52857) Adds a new SQL expression `is_valid_variant(v)` that returns `true` if the variant is well-formed and `false` if it is malformed, instead of throwing `MALFORMED_VARIANT` like other variant expressions.
- [[SPARK-53469]](https://issues.apache.org/jira/browse/SPARK-53469) Enables shuffle cleanup in the Thrift server by honoring the existing configuration `spark.sql.classic.shuffleDependency.fileCleanup.enabled`.
- [[SPARK-53573]](https://issues.apache.org/jira/browse/SPARK-53573) Proposes expanding the IDENTIFIER() clause to be usable in all places identifiers can appear in SQL.
- [[SPARK-53991]](https://issues.apache.org/jira/browse/SPARK-53991) Introduces SQL support for KLL quantile sketches in Apache Spark, leveraging the Apache DataSketches library.
- [[SPARK-54022]](https://issues.apache.org/jira/browse/SPARK-54022) Ensures that DSv2 table resolution is aware of cached tables to prevent silent cache misses.
- [[SPARK-54119]](https://issues.apache.org/jira/browse/SPARK-54119) Extends metric-view DDL support to DSv2 catalogs by routing `CREATE VIEW ...
- [[SPARK-54134]](https://issues.apache.org/jira/browse/SPARK-54134) Optimizes memory usage for Arrow in Spark by compressing Arrow IPC data during serialization, addressing OOM issues encountered in PySpark when loading data with `toArrow` or `toPandas`.
- [[SPARK-54157]](https://issues.apache.org/jira/browse/SPARK-54157) Addresses an issue with refreshing DSv2 tables in Spark's Dataset API.
- [[SPARK-54179]](https://issues.apache.org/jira/browse/SPARK-54179) Adds native Spark SQL support for Apache DataSketches Tuple sketches, introducing 18 new SQL functions (including 6 aggregates) to build, inspect, and perform union/intersection/difference operations on tuple sketches for approximate distinct counting with associated summary values.
- [[SPARK-54199]](https://issues.apache.org/jira/browse/SPARK-54199) Adds DataFrame API support for the KLL quantile sketch functions in Apache Spark, allowing users to utilize these functions through both Scala and Python DataFrame APIs.
- [[SPARK-54220]](https://issues.apache.org/jira/browse/SPARK-54220) Introduces support for handling NullType columns in Parquet files by utilizing the `UNKNOWN` logical type annotation.
- [[SPARK-54226]](https://issues.apache.org/jira/browse/SPARK-54226) Extends Arrow compression to Pandas UDFs to optimize memory usage, building on a previous feature added for `toArrow` and `toPandas`.
- [[SPARK-54275]](https://issues.apache.org/jira/browse/SPARK-54275) Clean up  unused code from `pipeline` module
- [[SPARK-54292]](https://issues.apache.org/jira/browse/SPARK-54292) Enhances the SQL pipe operator syntax by allowing aggregate functions and `GROUP BY` in `|> SELECT` pipe operators, similar to their previous usage in `|> AGGREGATE` operators.
- [[SPARK-54354]](https://issues.apache.org/jira/browse/SPARK-54354) Fixes an issue where Spark hangs instead of throwing an OutOfMemoryError (OOM) when there isn't enough JVM heap memory for a broadcast hashed relation.
- [[SPARK-54405]](https://issues.apache.org/jira/browse/SPARK-54405) Introduces functionality for creating and querying metric views in Apache Spark.
- [[SPARK-54682]](https://issues.apache.org/jira/browse/SPARK-54682) Enhances the DESCRIBE PROCEDURE command in Apache Spark SQL to display detailed parameter information for V2 procedures, including parameter mode, name, data type, default values, and comments.
- [[SPARK-54713]](https://issues.apache.org/jira/browse/SPARK-54713) Introduces vector distance and similarity functions to Spark SQL.
- [[SPARK-54718]](https://issues.apache.org/jira/browse/SPARK-54718) Introduces a new implementation of CTERelationRef.newInstance() to preserve attribute names, ensuring a more predictable output schema.
- [[SPARK-54720]](https://issues.apache.org/jira/browse/SPARK-54720) Introduces a new version of `SparkSession.emptyDataFrame` that accepts a schema, simplifying the creation of an empty DataFrame with a specified schema in Scala.
- [[SPARK-54735]](https://issues.apache.org/jira/browse/SPARK-54735) Addresses a bug where user-defined comments on view columns with schema evolution enabled are overwritten by comments from the underlying table after executing a query.
- [[SPARK-54753]](https://issues.apache.org/jira/browse/SPARK-54753) Addresses a memory leak issue with the ArtifactManager in Spark.
- [[SPARK-54759]](https://issues.apache.org/jira/browse/SPARK-54759) Adds SQL Standard CURSOR support to Spark SQL Scripting, introducing `DECLARE CURSOR AS`, `OPEN ...
- [[SPARK-54760]](https://issues.apache.org/jira/browse/SPARK-54760) DelegatingCatalogExtension as session catalog supports both V1 and V2 functions
- [[SPARK-54785]](https://issues.apache.org/jira/browse/SPARK-54785) Introduces new SQL aggregate functions for merging multiple binary KLL sketch representations: `kll_merge_agg_bigint`, `kll_merge_agg_float`, and `kll_merge_agg_double`.
- [[SPARK-54803]](https://issues.apache.org/jira/browse/SPARK-54803) Adds support for the `BY NAME` parameter to `INSERT INTO ...
- [[SPARK-54812]](https://issues.apache.org/jira/browse/SPARK-54812) Prevents Spark SQL command result DataFrames (e.g., `CREATE TABLE`, `SHOW TABLES`) from being re-executed when `resultDf.cache()` is called by skipping caching for all `Command` results, avoiding unintended side effects or errors and stopping `SHOW` results from refreshing via `cache()`.
- [[SPARK-54830]](https://issues.apache.org/jira/browse/SPARK-54830) Enables the checksum-based indeterminate shuffle retry feature by default.
- [[SPARK-54840]](https://issues.apache.org/jira/browse/SPARK-54840) Optimizes ORC serialization performance by pre-allocating `OrcList` with the exact size needed, avoiding dynamic resizing and reducing the overhead of repeated array resizing and element copying.
- [[SPARK-54852]](https://issues.apache.org/jira/browse/SPARK-54852) Addresses a bug where a `NOT IN` subquery returns incorrect results with collated tables.
- [[SPARK-54854]](https://issues.apache.org/jira/browse/SPARK-54854) Introduces a UUIDv7 `queryId` to SparkListenerSQLExecutionStart for better global uniqueness and time-ordering in SQL execution events.
- [[SPARK-54864]](https://issues.apache.org/jira/browse/SPARK-54864) Add rCTE nodes to NormalizePlan
- [[SPARK-54870]](https://issues.apache.org/jira/browse/SPARK-54870) Adds collation support for char/varchar data types and extends the feature to CTAS (Create Table As Select) and RTAS (Replace Table As Select) commands, introducing a new feature for handling string collation in these contexts.
- [[SPARK-54878]](https://issues.apache.org/jira/browse/SPARK-54878) Adds a `sortKeys` option (default `false`) to the `to_json` function that sorts JSON object keys alphabetically when enabled.
- [[SPARK-54971]](https://issues.apache.org/jira/browse/SPARK-54971) Introduces a new SQL syntax, `WITH SCHEMA EVOLUTION`, for the `INSERT` command.
- [[SPARK-55019]](https://issues.apache.org/jira/browse/SPARK-55019) Modifies the semantics of the DROP TABLE command to allow it to operate on views.
- [[SPARK-55030]](https://issues.apache.org/jira/browse/SPARK-55030) Adds two new Spark SQL functions, `vector_norm` and `vector_normalize`, to compute Lp norms and unit-length normalization for `ARRAY<FLOAT>` vectors (defaulting to L2 and supporting L1/L2/∞ degrees).
- [[SPARK-55031]](https://issues.apache.org/jira/browse/SPARK-55031) Adds two new Spark SQL aggregate functions, `vector_sum` and `vector_avg`, to compute element-wise sum and average over grouped `ARRAY<FLOAT>` vectors, with validation for consistent vector dimensions and skipping NULL/invalid vectors.
- [[SPARK-55044]](https://issues.apache.org/jira/browse/SPARK-55044) Keep the metadata in toArrowSchema/fromArrowSchema
- [[SPARK-55064]](https://issues.apache.org/jira/browse/SPARK-55064) Improve indeterminate shuffle retry correctness at the query level by tracking all jobs within the same query execution, identifying succeeding stages via shuffle IDs, aborting completed/running succeeding result stages, and rolling back/resubmitting succeeding shuffle map stages while cleaning up stale shuffle outputs.
- [[SPARK-55155]](https://issues.apache.org/jira/browse/SPARK-55155) Extends the SQL `SET CATALOG` statement to accept foldable SQL expressions (and resolve session variables directly), enabling dynamically computed catalog names without needing to wrap them in `IDENTIFIER()`.
- [[SPARK-55250]](https://issues.apache.org/jira/browse/SPARK-55250) Reduces unnecessary Hive client RPCs during `CREATE NAMESPACE [IF NOT EXISTS] foo.bar` by removing an extra `catalog.databaseExists` check in `CreateNamespaceExec`, cutting Hive client calls from 3 to 1 for better performance.
- [[SPARK-55256]](https://issues.apache.org/jira/browse/SPARK-55256) Adds SQL support for `IGNORE NULLS` / `RESPECT NULLS` clauses on the `array_agg` and `collect_list` aggregate functions, allowing users to explicitly control whether nulls are excluded (default) or preserved in the resulting array.
- [[SPARK-55322]](https://issues.apache.org/jira/browse/SPARK-55322) Add a new 3-argument overload for the SQL aggregate functions `max_by(expr, ord, k)` and `min_by(expr, ord, k)` so they can return an array of the top/bottom *k* values (excluding NULL ordering keys) instead of a single value.
- [[SPARK-55341]](https://issues.apache.org/jira/browse/SPARK-55341) Adds an internal SQL feature flag `spark.sql.artifact.cacheStorageLevel` to let cached artifact blocks use `DISK_ONLY` when enabled (to reduce memory pressure) while keeping the default `MEMORY_AND_DISK_SER` behavior when disabled.
- [[SPARK-55356]](https://issues.apache.org/jira/browse/SPARK-55356) Adds optional `AS alias` support for the SQL `PIVOT` clause (T-SQL/BigQuery-style), letting the pivoted result be referenced by name (e.g., `alias.column`) within the same query block to disambiguate columns.
- [[SPARK-55453]](https://issues.apache.org/jira/browse/SPARK-55453) Fixes Spark SQL `LIKE` handling so patterns containing supplementary Unicode characters (e.g., emojis, code points above U+FFFF) are processed and matched correctly.
- [[SPARK-55528]](https://issues.apache.org/jira/browse/SPARK-55528) Adds default collation support for SQL UDFs so they can inherit schema-level collations or specify a `DEFAULT COLLATION` in `CREATE FUNCTION`, applying it to uncollated `STRING` parameters/return types and string literals (while explicit collations still take precedence).
- [[SPARK-55533]](https://issues.apache.org/jira/browse/SPARK-55533) Add SQL support for `IGNORE NULLS` / `RESPECT NULLS` clauses to `collect_set`, matching `collect_list` behavior so users can explicitly skip nulls or include a null in the collected set.
- [[SPARK-55558]](https://issues.apache.org/jira/browse/SPARK-55558) Adds support for union/intersection/difference set operations between DataSketches TupleSketch and ThetaSketch by introducing six new Spark SQL functions: `tuple_union_theta_{double,integer}`, `tuple_intersection_theta_{double,integer}`, and `tuple_difference_theta_{double,integer}`.
- [[SPARK-55596]](https://issues.apache.org/jira/browse/SPARK-55596) Enhances partition filtering for DataSource V2 SQL data sources by leveraging available partition statistics.
- [[SPARK-55631]](https://issues.apache.org/jira/browse/SPARK-55631) ALTER TABLE commands now invalidate the cache for DataSource V2 tables so cached data reflects table changes.
- [[SPARK-55689]](https://issues.apache.org/jira/browse/SPARK-55689) Adds a new `withSchemaEvolution()` method to the `DataFrameWriter` and `DataFrameWriterV2` APIs, mirroring the existing `MergeIntoWriter.withSchemaEvolution()`.
- [[SPARK-55690]](https://issues.apache.org/jira/browse/SPARK-55690) Adds schema evolution support for DataSource V2 INSERT operations (AppendData, OverwriteByExpression, OverwritePartitionsDynamic) so that, when a table declares `AUTOMATIC_SCHEMA_EVOLUTION`, Spark can detect new columns or nested fields in the INSERT source and automatically alter the target table schema (respecting INSERT by-name vs by-position resolution).
- [[SPARK-55702]](https://issues.apache.org/jira/browse/SPARK-55702) Spark SQL now supports the `FILTER (WHERE ...)` clause on aggregate functions used in window expressions, so these queries run successfully instead of failing with an `AnalysisException`.
- [[SPARK-55716]](https://issues.apache.org/jira/browse/SPARK-55716) Adds an opt-in setting (`spark.sql.fileSource.insert.enforceNotNull`) to enforce NOT NULL constraints on inserts into V1 file-based data source tables by preserving catalog nullability, injecting null checks during insertion, and fixing column metadata (`IS_NULLABLE`) to reflect actual nullability.
- [[SPARK-55855]](https://issues.apache.org/jira/browse/SPARK-55855) Adds the public Java interfaces (`TransactionInfo`, `Transaction`, `TransactionalCatalogPlugin`) and the Spark-side machinery (pre-analysis transaction initiation, a `TransactionAwareCatalogManager` that intercepts catalog lookups, `TransactionalExec` callback injection at planning, commit at `V2ExistingTableWriteExec`, and idempotent abort/close wrapped around every QE operation) that DSv2 connectors need for transactional DML.
- [[SPARK-55857]](https://issues.apache.org/jira/browse/SPARK-55857) Propagates `spark.sql.files.ignoreMissingFiles` into Parquet and ORC schema inference (`mergeSchema`) so files that vanish between listing and footer/schema reads are skipped instead of failing with `FileNotFoundException`.
- [[SPARK-55928]](https://issues.apache.org/jira/browse/SPARK-55928) Adds a `ConfigBindingPolicy` framework that requires new Spark SQL configs to declare whether their values are session-propagated, persisted at view/UDF creation time, or not applicable, replaces the hardcoded retained-analysis allowlist with a dynamic policy-based lookup in the Analyzer, annotates the previously allowlisted configs with the appropriate policy, and introduces a test to enforce that future configs declare a binding policy (with an exceptions list for existing configs).
- [[SPARK-55978]](https://issues.apache.org/jira/browse/SPARK-55978) Adds ANSI SQL `TABLESAMPLE SYSTEM` block sampling alongside the existing BERNOULLI row sampling, with grammar accepting an optional SYSTEM/BERNOULLI qualifier (both non-reserved keywords; default Bernoulli for backward compatibility).
- [[SPARK-55995]](https://issues.apache.org/jira/browse/SPARK-55995) Adds support for the SQL type syntax `TIMESTAMP WITH LOCAL TIME ZONE` to represent `TimestampType`, complementing `TIMESTAMP WITHOUT TIME ZONE` for `TimestampNTZType`.
- [[SPARK-56001]](https://issues.apache.org/jira/browse/SPARK-56001) Introduces two new SQL syntaxes: `INSERT INTO ...
- [[SPARK-56019]](https://issues.apache.org/jira/browse/SPARK-56019) Registers a `TaskInterruptListener` on JDBC read and write paths to close the connection when a task is killed.
- [[SPARK-56031]](https://issues.apache.org/jira/browse/SPARK-56031) Fixes `NATURAL JOIN` to use `conf.resolver` instead of case-sensitive `Seq.intersect` when computing common column names, respecting `spark.sql.caseSensitive`.
- [[SPARK-56032]](https://issues.apache.org/jira/browse/SPARK-56032) Adds subexpression elimination (CSE) support to `FilterExec.doConsume` in the whole-stage codegen path, following the pattern established by `ProjectExec` and `HashAggregateExec`.
- [[SPARK-56034]](https://issues.apache.org/jira/browse/SPARK-56034) Adds a new optimizer rule `PushDownJoinThroughUnion` that pushes broadcast joins through Union, transforming `Join(Union(c1, c2, ...), right)` into `Union(Join(c1, right), Join(c2, right), ...)` when the right side is broadcastable.
- [[SPARK-56045]](https://issues.apache.org/jira/browse/SPARK-56045) Introduces `spark.sql.parquet.reader.respectUnknownTypeAnnotation.enabled` to control behavior when reading Parquet files with `UNKNOWN` logical type annotation.
- [[SPARK-56046]](https://issues.apache.org/jira/browse/SPARK-56046) Adds a `resultType()` method to SPJ `Reducer` to return the correct type of reduced partition keys.
- [[SPARK-56047]](https://issues.apache.org/jira/browse/SPARK-56047) Extends `UnionEstimation` to propagate `distinctCount` column statistics through Union, enabling downstream operators like `AggregateEstimation` and `JoinEstimation` to produce accurate CBO estimates.
- [[SPARK-56089]](https://issues.apache.org/jira/browse/SPARK-56089) Replaces the naive `log(x + sqrt(x^2 ± 1))` formula in `Asinh` and `Acosh` with the full fdlibm algorithm used by OpenJDK, glibc, Python, PostgreSQL, and DuckDB.
- [[SPARK-56182]](https://issues.apache.org/jira/browse/SPARK-56182) Extends `KeyedShuffleSpec` to support storage-partitioned joins where one side uses an identity transform (`AttributeReference`) and the other uses an arbitrary `TransformExpression` (e.g., bucket).
- [[SPARK-56251]](https://issues.apache.org/jira/browse/SPARK-56251) Adds a default `fetchSize` of 1000 for the PostgreSQL JDBC dialect to prevent loading entire tables into memory.
- [[SPARK-56346]](https://issues.apache.org/jira/browse/SPARK-56346) Extends `OptimizeMetadataOnlyDeleteFromTable` with a second-pass fallback that converts partition-column filters to `PartitionPredicate`s when standard V2 filter translation fails.
- [[SPARK-56395]](https://issues.apache.org/jira/browse/SPARK-56395) First of two PRs implementing `NEAREST BY` top-K ranking joins.
- [[SPARK-56412]](https://issues.apache.org/jira/browse/SPARK-56412) Adds the engine-side foundation for the language-agnostic UDF framework (SPIP SPARK-55278) under a new `udf/worker/core` module.
- [[SPARK-56489]](https://issues.apache.org/jira/browse/SPARK-56489) Adds the `CURRENT_PATH()` builtin function returning the current SQL resolution search path as a comma-separated string of qualified schema names (e.g.
- [[SPARK-56509]](https://issues.apache.org/jira/browse/SPARK-56509) Introduces `LastAttemptAccumulator`, a trait mixable into any `AccumulatorV2` subclass that tracks per-(stageId, stageAttemptId, taskAttemptNumber) partial values and aggregates only values from the latest attempt of each partition — solving the long-standing problem that regular accumulators sum across all task attempts (so e.g.
- [[SPARK-56520]](https://issues.apache.org/jira/browse/SPARK-56520) Persists the effective SQL resolution path at CREATE-time for views and SQL functions when `spark.sql.path.enabled` is true (stored as JSON in `view.resolutionPath`/`function.resolutionPath` properties), and surfaces it in `DESCRIBE EXTENDED`/`DESCRIBE FORMATTED` (as `SQL Path`) and `DESCRIBE ...
- [[SPARK-56521]](https://issues.apache.org/jira/browse/SPARK-56521) Extends `PartitionPredicate` support in DSv2 from static pushdown into runtime filters (DPP and scalar subqueries).
- [[SPARK-56551]](https://issues.apache.org/jira/browse/SPARK-56551) Adds `numDeletedRows` and `numCopiedRows` operation metrics for DSv2 DELETE queries, computed in `WritingSparkTask`, to give users better visibility into what a DELETE actually did.
- [[SPARK-56594]](https://issues.apache.org/jira/browse/SPARK-56594) Adds a new scalar SQL function `time_bucket(bucket_size, ts[, origin])` that aligns a timestamp to the start of a fixed-size half-open bucket `[start, start + bucket_size)`.
- [[SPARK-56598]](https://issues.apache.org/jira/browse/SPARK-56598) Custom metrics support for TruncatableTable
- [[SPARK-56605]](https://issues.apache.org/jira/browse/SPARK-56605) Wires the resolution engine to use the live SQL `PATH` for unqualified table, function, and variable lookup (when `spark.sql.path.enabled = true`), via a new `sqlResolutionPathEntries` on `CatalogManager` that replaces the legacy `resolutionSearchPath`.
- [[SPARK-56647]](https://issues.apache.org/jira/browse/SPARK-56647) Optimize storage of SparkSQL Last Attempt Metrics
- [[SPARK-56677]](https://issues.apache.org/jira/browse/SPARK-56677) Extends `PlanMerger` to propagate filter conditions through `Join` nodes when merging similar subplans, so two scalar subqueries that share a join but differ only in a filter on one side can now be merged into a single scan with the second subquery's result derived via an aggregate `FILTER` clause.
- [[SPARK-56680]](https://issues.apache.org/jira/browse/SPARK-56680) DSv2 INSERT and Insert-Only MERGE Metrics

### Spark Connect
- **SPIP: JDBC Driver for Spark Connect** ([[SPARK-53484]](https://issues.apache.org/jira/browse/SPARK-53484))
  - [[SPARK-54014]](https://issues.apache.org/jira/browse/SPARK-54014) Support max rows for SparkConnectStatement
  - [[SPARK-54108]](https://issues.apache.org/jira/browse/SPARK-54108) Revise execute* methods of SparkConnectStatement
  - [[SPARK-54111]](https://issues.apache.org/jira/browse/SPARK-54111) Support getCatalogs for SparkConnectDatabaseMetaData
  - [[SPARK-54112]](https://issues.apache.org/jira/browse/SPARK-54112) Support getSchemas for SparkConnectDatabaseMetaData
  - [[SPARK-54113]](https://issues.apache.org/jira/browse/SPARK-54113) Support getTables for SparkConnectDatabaseMetaData
  - [[SPARK-54114]](https://issues.apache.org/jira/browse/SPARK-54114) Support getColumns for SparkConnectDatabaseMetaData
  - [[SPARK-54205]](https://issues.apache.org/jira/browse/SPARK-54205) Supports Decimal type data in SparkConnectResultSet
  - [[SPARK-54206]](https://issues.apache.org/jira/browse/SPARK-54206) Support BINARY type data in SparkConnectResultSet
  - [[SPARK-54207]](https://issues.apache.org/jira/browse/SPARK-54207) Supports Date type data in SparkConnectResultSet
  - [[SPARK-54208]](https://issues.apache.org/jira/browse/SPARK-54208) Support TIME type in SparkConnectResultSet
  - [[SPARK-54209]](https://issues.apache.org/jira/browse/SPARK-54209) Support TIMESTAMP type in SparkConnectResultSet
  - [[SPARK-54270]](https://issues.apache.org/jira/browse/SPARK-54270) SparkConnectResultSet get* methods should call checkOpen and check index boundary
  - [[SPARK-54537]](https://issues.apache.org/jira/browse/SPARK-54537) Fix SparkConnectDatabaseMetaData getSchemas/getTables on catalogs missing namespace capbalitity
  - [[SPARK-54540]](https://issues.apache.org/jira/browse/SPARK-54540) Couples of minor fix for Connect JDBC driver
- **Improve SparkConnect usability and performance** ([[SPARK-54357]](https://issues.apache.org/jira/browse/SPARK-54357))
  - [[SPARK-53525]](https://issues.apache.org/jira/browse/SPARK-53525) Addresses stability issues in Spark Connect by introducing chunking for large Arrow batches in `ExecutePlanResponse`.
  - [[SPARK-53917]](https://issues.apache.org/jira/browse/SPARK-53917) Addresses the limitations in handling large local relations in Spark Connect by proposing changes to the data serialization and transfer process.
  - [[SPARK-54194]](https://issues.apache.org/jira/browse/SPARK-54194) Implements compression for unresolved proto plans in Spark Connect to improve stability and address issues with oversized messages that exceed gRPC message limits.
  - [[SPARK-54696]](https://issues.apache.org/jira/browse/SPARK-54696) Addresses a memory leak issue in Spark Connect LocalRelations by cleaning up ArrowBuffers.
  - [[SPARK-54128]](https://issues.apache.org/jira/browse/SPARK-54128) Convert IllegalArgumentException to SparkException with proper error classes in Spark Connect server
  - [[SPARK-54294]](https://issues.apache.org/jira/browse/SPARK-54294) Normalize Connect server printed IP address
  - [[SPARK-54355]](https://issues.apache.org/jira/browse/SPARK-54355) Make `spark.connect.session.planCompression.defaultAlgorithm` to support `NONE`
- **RDD API compatibility** ([[SPARK-55227]](https://issues.apache.org/jira/browse/SPARK-55227))
  - [[SPARK-55089]](https://issues.apache.org/jira/browse/SPARK-55089) Fixes Spark Connect’s `Dataset.toJSON` to produce the same output schema as classic Spark.
  - [[SPARK-55090]](https://issues.apache.org/jira/browse/SPARK-55090) Adds support for `DataFrame.toJSON` in the Spark Connect Python client.
  - [[SPARK-55228]](https://issues.apache.org/jira/browse/SPARK-55228) Adds `Dataset.zipWithIndex()` and `Dataset.zipWithIndex(indexColName: String)` to the Spark SQL Connect Scala API.
  - [[SPARK-56253]](https://issues.apache.org/jira/browse/SPARK-56253) Allows `spark.read.json()` to accept a DataFrame as input (first column must be StringType), providing a Connect-compatible alternative to `sc.parallelize()` for parsing in-memory JSON text.
  - [[SPARK-56254]](https://issues.apache.org/jira/browse/SPARK-56254) Adds DataFrame input support to `spark.read.xml()`, completing the DataFrame input support across all text-based readers (JSON, CSV, XML).
  - [[SPARK-56255]](https://issues.apache.org/jira/browse/SPARK-56255) Adds support for passing a DataFrame containing CSV strings directly to `spark.read.csv()`, following the same pattern established for `spark.read.json()`.
- **Fix broken tests in Spark Connect 4.0 client <> master server** ([[SPARK-54477]](https://issues.apache.org/jira/browse/SPARK-54477))
- **SPIP: Declarative Pipelines** ([[SPARK-51727]](https://issues.apache.org/jira/browse/SPARK-51727))
  - [[SPARK-54369]](https://issues.apache.org/jira/browse/SPARK-54369) Fix `PythonPipelineSuite` flakiness via `Set` instead of `Seq`
  - [[SPARK-54375]](https://issues.apache.org/jira/browse/SPARK-54375) Add `assume` to cases in `PythonPipelineSuite` to skip tests when PyConnect dependencies is not available
- **Change Data Capture (CDC) Support** ([[SPARK-55668]](https://issues.apache.org/jira/browse/SPARK-55668))
  - [[SPARK-55949]](https://issues.apache.org/jira/browse/SPARK-55949) Adds the DataFrame API (`spark.read.changes("table")`) and Spark Connect support for CDC queries, complementing the SQL `CHANGES` clause.
  - [[SPARK-55950]](https://issues.apache.org/jira/browse/SPARK-55950) Adds `changes()` method to PySpark `DataFrameReader` and `DataStreamReader` for both classic and Spark Connect modes, exposing the CDC (Change Data Capture) API to Python users for batch and streaming reads.
- [[SPARK-54213]](https://issues.apache.org/jira/browse/SPARK-54213) Removes support for Python 3.9 from Spark Connect as it has reached end-of-life on 2025-10-31 and Apache Spark 4.1.0 has already dropped support for it.
- [[SPARK-54314]](https://issues.apache.org/jira/browse/SPARK-54314) Adds an opt-in Spark Connect client feature (via `SPARK_CONNECT_DEBUG_CLIENT_CALL_STACK`) to send the client application’s call-site details (function, file, line) with actions so the server can log/attribute them for easier debugging and performance troubleshooting.
- [[SPARK-54446]](https://issues.apache.org/jira/browse/SPARK-54446) Enables FPGrowth to support the local filesystem using the Arrow file format, allowing FPGrowth to function with local filesystem data.
- [[SPARK-54706]](https://issues.apache.org/jira/browse/SPARK-54706) Enables the DistributedLDAModel to work with the local file system in Spark's connect module, which is necessary to support this model on connect.
- [[SPARK-55047]](https://issues.apache.org/jira/browse/SPARK-55047) Adds a client-side check for `spark.sql.session.localRelationSizeLimit` when Spark Connect serializes local relations, preventing oversized relations from being uploaded as artifacts.
- [[SPARK-55104]](https://issues.apache.org/jira/browse/SPARK-55104) Adds Spark Connect support for `DataStreamReader.name()` in Scala and Python, enabling users to assign validated source names (ASCII letters/digits/underscores) to streaming sources for API parity with classic Spark.
- [[SPARK-55179]](https://issues.apache.org/jira/browse/SPARK-55179) For PySpark Connect, make `df.col_name` skip eager column-name validation (like `df["col_name"]`), so invalid attribute columns such as `df.abc`/`df._abc` return a `Column` and only fail later during analysis or execution.
- [[SPARK-55239]](https://issues.apache.org/jira/browse/SPARK-55239) Enable launching `SparkConnectServer` in YARN cluster deploy mode, leveraging existing support to discover the server location on the cluster.
- [[SPARK-55264]](https://issues.apache.org/jira/browse/SPARK-55264) Adds a new `ExecuteOutput` command to the Spark Connect pipelines protobuf so clients can directly execute multiple flows that write to an output.
- [[SPARK-55278]](https://issues.apache.org/jira/browse/SPARK-55278) Introduces the foundational module structure and core abstractions for a language-agnostic UDF worker framework.
- [[SPARK-55314]](https://issues.apache.org/jira/browse/SPARK-55314) Spark Connect now propagates observed-metrics collection failures back to the client (via new error fields in `ExecutePlanResponse.ObservedMetrics`) so that `Observation.get` raises the underlying exception instead of silently returning empty metrics.
- [[SPARK-55606]](https://issues.apache.org/jira/browse/SPARK-55606) Implements the server-side Spark Connect GetStatus API by tracking execution termination details across active/inactive operations, using those caches to report status, and adding a plugin interface to handle custom proto extensions.
- [[SPARK-55691]](https://issues.apache.org/jira/browse/SPARK-55691) Adds an experimental Spark Connect client implementation of the GetStatus API, including new client methods to request operation statuses and accompanying mocked-service and end-to-end tests for real operation lifecycles.
- [[SPARK-55887]](https://issues.apache.org/jira/browse/SPARK-55887) Updates Spark Connect’s `SparkConnectPlanExecution` to run `CollectLimitExec` and `CollectTailExec` via `executeCollect()` (instead of `execute()`), enabling the existing optimized `executeTake()`/`executeTail()` behavior so `head()`/`take()`/`tail()` avoid scanning all partitions.
- [[SPARK-56226]](https://issues.apache.org/jira/browse/SPARK-56226) Catch analysis errors before `InternalFrame.__init__` in `.loc`
- [[SPARK-56284]](https://issues.apache.org/jira/browse/SPARK-56284) Introduces protobuf definitions for the UDF worker specification (SPIP SPARK-55278): `common.proto` for shared types and `worker_spec.proto` for the specification.
- [[SPARK-56322]](https://issues.apache.org/jira/browse/SPARK-56322) Fixes a `TypeError` when self-joining a DataFrame that has `.observe()` metrics.
- [[SPARK-56395]](https://issues.apache.org/jira/browse/SPARK-56395) First of two PRs implementing `NEAREST BY` top-K ranking joins.
- [[SPARK-56614]](https://issues.apache.org/jira/browse/SPARK-56614) Adds an internal SQL config `spark.sql.analyzer.strictDataFrameColumnResolution` (default `true`) that controls how `UnresolvedAttribute`s carrying a `PLAN_ID_TAG` (Spark Connect DataFrame columns) are resolved in `ColumnResolutionHelper`.

### PySpark
- **Monitor behaviour changes from upstream** ([[SPARK-54936]](https://issues.apache.org/jira/browse/SPARK-54936))
- **Micro-benchmark PySpark Eval Types** ([[SPARK-55724]](https://issues.apache.org/jira/browse/SPARK-55724))
- **Refactor PythonEvalType processing logic** ([[SPARK-55388]](https://issues.apache.org/jira/browse/SPARK-55388))
- **Pandas UDF with PyArrow Backend** ([[SPARK-54955]](https://issues.apache.org/jira/browse/SPARK-54955))
  - [[SPARK-55462]](https://issues.apache.org/jira/browse/SPARK-55462) Support `UserDefinedType` in `convert_numpy` for the Arrow-to-Pandas conversion flow.
  - [[SPARK-54965]](https://issues.apache.org/jira/browse/SPARK-54965) Factor out legacy pa.Array -> pd.Series converter
  - [[SPARK-54969]](https://issues.apache.org/jira/browse/SPARK-54969) Implement new arrow->pandas conversion
  - [[SPARK-55036]](https://issues.apache.org/jira/browse/SPARK-55036) Add `ArrowTimestampConversion` for arrow timezone handling
  - [[SPARK-55088]](https://issues.apache.org/jira/browse/SPARK-55088) Keep the metadata in to/from_arrow_type/schema
  - [[SPARK-55186]](https://issues.apache.org/jira/browse/SPARK-55186) Make ArrowArrayToPandasConversion.convert_legacy able to return pd.DataFrame
  - [[SPARK-55333]](https://issues.apache.org/jira/browse/SPARK-55333) Enable `DateType` and `TimeType`  in `convert_numpy`
  - [[SPARK-55334]](https://issues.apache.org/jira/browse/SPARK-55334) Enable `TimestampType` and `TimestampNTZType` in `convert_numpy`
  - [[SPARK-55365]](https://issues.apache.org/jira/browse/SPARK-55365) Generalize the utils for arrow array conversion
  - [[SPARK-55366]](https://issues.apache.org/jira/browse/SPARK-55366) Remove `errorOnDuplicatedFieldNames` from Python UDFs
  - [[SPARK-55424]](https://issues.apache.org/jira/browse/SPARK-55424) Explicitly pass the series name in `convert_numpy`
  - [[SPARK-55464]](https://issues.apache.org/jira/browse/SPARK-55464) Support GeographyType in convert_numpy
  - [[SPARK-55465]](https://issues.apache.org/jira/browse/SPARK-55465) Support GeometryType in convert_numpy
- **Polish type annotations for pyspark** ([[SPARK-56223]](https://issues.apache.org/jira/browse/SPARK-56223))
- **Refactor PySpark Serializers** ([[SPARK-55384]](https://issues.apache.org/jira/browse/SPARK-55384))
- **Upgrade mypy to latest version** ([[SPARK-54953]](https://issues.apache.org/jira/browse/SPARK-54953))
  - [[SPARK-54954]](https://issues.apache.org/jira/browse/SPARK-54954) Fix remote related type hints in util.py
  - [[SPARK-54991]](https://issues.apache.org/jira/browse/SPARK-54991) Correct type hint for streaming/listener.py
  - [[SPARK-55355]](https://issues.apache.org/jira/browse/SPARK-55355) Upgrade mypy version to the latest
  - [[SPARK-55364]](https://issues.apache.org/jira/browse/SPARK-55364) Make SupportsIAdd and SupportsOrdering protocol more reasonable
- **Improve test coverage on pyspark** ([[SPARK-54453]](https://issues.apache.org/jira/browse/SPARK-54453))
- **Python worker logging infrastructure** ([[SPARK-53754]](https://issues.apache.org/jira/browse/SPARK-53754))
  - [[SPARK-54123]](https://issues.apache.org/jira/browse/SPARK-54123) Add timezone to make the timestamp an absolute time
  - [[SPARK-54229]](https://issues.apache.org/jira/browse/SPARK-54229) Make PySparkLogger in UDFs store one log entry per log function call
  - [[SPARK-54323]](https://issues.apache.org/jira/browse/SPARK-54323) Change the way to access logs to TVF instead of system view
- **Extract Arrow batch transformers from serializers for better composability** ([[SPARK-55159]](https://issues.apache.org/jira/browse/SPARK-55159))
  - [[SPARK-55168]](https://issues.apache.org/jira/browse/SPARK-55168) Use ArrowBatchTransformer.flatten_struct in GroupArrowUDFSerializer
  - [[SPARK-55169]](https://issues.apache.org/jira/browse/SPARK-55169) Use ArrowBatchTransformer.flatten_struct in ArrowStreamArrowUDTFSerializer
  - [[SPARK-55336]](https://issues.apache.org/jira/browse/SPARK-55336) Let createDF use create_batch logic for decoupling
- **RDD API compatibility** ([[SPARK-55227]](https://issues.apache.org/jira/browse/SPARK-55227))
  - [[SPARK-55229]](https://issues.apache.org/jira/browse/SPARK-55229) Adds the `DataFrame.zipWithIndex` API to PySpark Classic, matching the functionality previously available in Scala.
  - [[SPARK-56256]](https://issues.apache.org/jira/browse/SPARK-56256) Adds `SparkSession.emptyDataFrame(schema)` API that creates an empty DataFrame with a specified schema.
  - [[SPARK-55249]](https://issues.apache.org/jira/browse/SPARK-55249) Add an (opt-in, config-gated) option for PySpark `DataFrame.toJSON` to return a DataFrame instead of using older RDD-based APIs.
- **Support Python 3.14** ([[SPARK-54286]](https://issues.apache.org/jira/browse/SPARK-54286))
  - [[SPARK-54287]](https://issues.apache.org/jira/browse/SPARK-54287) Adds support for Python 3.14 in the `pyspark-client` and `pyspark-connect` components of Apache Spark 4.1.0.
  - [[SPARK-54068]](https://issues.apache.org/jira/browse/SPARK-54068) Fix `to_feather` to support PyArrow 22.0.0
- **Improve lint on PySpark** ([[SPARK-54543]](https://issues.apache.org/jira/browse/SPARK-54543))
  - [[SPARK-54544]](https://issues.apache.org/jira/browse/SPARK-54544) Enable flake8 F811 check
  - [[SPARK-54632]](https://issues.apache.org/jira/browse/SPARK-54632) Add the option to use ruff for lint
- **Support Pandas 3** ([[SPARK-55139]](https://issues.apache.org/jira/browse/SPARK-55139))
  - [[SPARK-55730]](https://issues.apache.org/jira/browse/SPARK-55730) Not make timezone lower case
  - [[SPARK-56310]](https://issues.apache.org/jira/browse/SPARK-56310) Handle pandas 3 dtype in DataFrame.toPandas
- [[SPARK-49793]](https://issues.apache.org/jira/browse/SPARK-49793) Reenable test_caching for predict_batch_udf
- [[SPARK-50111]](https://issues.apache.org/jira/browse/SPARK-50111) Adds `subplots` and `layout` kwargs to `plot_pie` for pandas-on-Spark DataFrames with the Plotly backend, rendering each column as a separate pie chart in a multi-subplot figure.
- [[SPARK-51966]](https://issues.apache.org/jira/browse/SPARK-51966) Replaces `select.select()` with `select.poll()` on POSIX systems to overcome the limitation of `select()` on glibc based Linux systems, which can only monitor file descriptor numbers less than `FD_SETSIZE` (1024).
- [[SPARK-52837]](https://issues.apache.org/jira/browse/SPARK-52837) Add `versionadded` to `TimeType` doc
- [[SPARK-53448]](https://issues.apache.org/jira/browse/SPARK-53448) Conversion of a pyspark DataFrame with a Variant column to pandas fails with an error
- [[SPARK-53614]](https://issues.apache.org/jira/browse/SPARK-53614) Introduces support for the `Iterator[pandas.DataFrame]` API in `groupBy().applyInPandas()` to allow batch-by-batch processing of grouped data.
- [[SPARK-53615]](https://issues.apache.org/jira/browse/SPARK-53615) Introduces an iterator API for Arrow grouped aggregation UDFs in PySpark.
- [[SPARK-53616]](https://issues.apache.org/jira/browse/SPARK-53616) Introduces an iterator API for pandas grouped aggregation UDFs, allowing batch-by-batch processing to improve memory efficiency.
- [[SPARK-54194]](https://issues.apache.org/jira/browse/SPARK-54194) Implements compression for unresolved proto plans in Spark Connect to improve stability and address issues with oversized messages that exceed gRPC message limits.
- [[SPARK-54340]](https://issues.apache.org/jira/browse/SPARK-54340) Introduces a script that allows developers to use viztracer for profiling PySpark daemons and workers without modifying the source code.
- [[SPARK-54555]](https://issues.apache.org/jira/browse/SPARK-54555) Enables Arrow-optimized Python UDFs and Arrow-based PySpark IPC by default in Spark 4.2.0.
- [[SPARK-54572]](https://issues.apache.org/jira/browse/SPARK-54572) Introduces a script and supporting files to enable native debugging in VSCode for PySpark code, including driver code, UDFs, workers, and daemons, enhancing the debugging experience.
- [[SPARK-54617]](https://issues.apache.org/jira/browse/SPARK-54617) Allows Arrow grouped iter aggregate UDFs to be registered and used in SQL queries, expanding their usage beyond just the DataFrame API.
- [[SPARK-54631]](https://issues.apache.org/jira/browse/SPARK-54631) Adds profiler support for Arrow Grouped Iter Aggregate UDFs by including the `SQL_GROUPED_AGG_ARROW_ITER_UDF` in the profiler warning list.
- [[SPARK-54640]](https://issues.apache.org/jira/browse/SPARK-54640) Replaces `select.select` with `select.poll` in `worker.py` for UNIX systems to address a known limitation where `select.select` fails to work with file descriptors greater than 1024, which can occur on systems under heavy load.
- [[SPARK-54722]](https://issues.apache.org/jira/browse/SPARK-54722) Introduces `SQL_GROUPED_AGG_PANDAS_ITER_UDF` support in `UDFRegistration.register()`, allowing Pandas Grouped Iter Aggregate UDFs to be used in SQL.
- [[SPARK-54738]](https://issues.apache.org/jira/browse/SPARK-54738) Adds profiler support for Pandas Grouped Iter Aggregate UDFs in PySpark.
- [[SPARK-54849]](https://issues.apache.org/jira/browse/SPARK-54849) Upgrades the minimum version of `pyarrow` to 18.0.0 to address a security issue and benefit from the removal of the numpy dependency, simplifying dependency management.
- [[SPARK-54925]](https://issues.apache.org/jira/browse/SPARK-54925) Introduces an optional capability to dump thread info for all PySpark processes, which can be used for debugging purposes, particularly when tests hang.
- [[SPARK-54962]](https://issues.apache.org/jira/browse/SPARK-54962) Addresses a correctness issue in Pandas UDF related to handling nullable integer columns.
- [[SPARK-55055]](https://issues.apache.org/jira/browse/SPARK-55055) Adds support for `SparkSession.Builder.create()` in PySpark Classic so users can always create a new `SparkSession` with the builder’s configs without mutating any existing session (matching Connect behavior).
- [[SPARK-55096]](https://issues.apache.org/jira/browse/SPARK-55096) Updates the pandas minimum required version in `connect/setup.py` to match the Spark 4.1 dependency bump to pandas 2.2.0.
- [[SPARK-55142]](https://issues.apache.org/jira/browse/SPARK-55142) Apply Python 3.12 for PySpark Tests in PR build
- [[SPARK-55161]](https://issues.apache.org/jira/browse/SPARK-55161) Enables perf/memory profiling for Python data sources via the new `pyspark.sql.pyspark.dataSource.profiler` configuration, and notes that the existing UDF profiler config will no longer log Python data source read/write operations.
- [[SPARK-55459]](https://issues.apache.org/jira/browse/SPARK-55459) Optimizes PySpark’s `wrap_grouped_map_pandas_udf` to eliminate a costly double-`concat` pattern, fixing a ~3× `applyInPandas` performance regression for large-group, few-column workloads by switching to a single per-column concatenation approach.
- [[SPARK-55507]](https://issues.apache.org/jira/browse/SPARK-55507) Add None check for field.metadata in is_geometry and is_geography
- [[SPARK-55610]](https://issues.apache.org/jira/browse/SPARK-55610) Adds `getExecutorInfos()` to `StatusTracker` in PySpark (non-connect), exposing executor details like host, port, cache size, running tasks, and storage memory that were previously only available in Scala.
- [[SPARK-55788]](https://issues.apache.org/jira/browse/SPARK-55788) Makes Pandas UDFs consistently use Pandas’ integer `ExtensionDtype` (instead of varying based on batch nullability), controlled by the new config `spark.sql.execution.pythonUDF.pandas.preferIntExtensionDtype`.
- [[SPARK-56056]](https://issues.apache.org/jira/browse/SPARK-56056) Adds viztracer profiling support for simpler workers, complementing the existing daemon worker profiling in `run-with-viztracer`.
- [[SPARK-56186]](https://issues.apache.org/jira/browse/SPARK-56186) Removes PyPy support from PySpark, cleaning up PyPy-specific code paths and conditional logic.
- [[SPARK-56221]](https://issues.apache.org/jira/browse/SPARK-56221) Adds feature parity between `spark.catalog.*` API and DDL commands, including new methods: `listCachedTables()`, `dropTable`/`dropView`, `createDatabase`/`dropDatabase`, `listPartitions`, `listViews`, `getTableProperties`, `getCreateTableString`, `truncateTable`, `analyzeTable`, and the new `SHOW CACHED TABLES` SQL command.
- [[SPARK-56463]](https://issues.apache.org/jira/browse/SPARK-56463) Disallows unpickling of User Defined Types (UDTs) for security purposes.
- [[SPARK-56518]](https://issues.apache.org/jira/browse/SPARK-56518) Adds the `current_path()` function to PySpark to match the JVM-side `CURRENT_PATH()` added in SPARK-56489.
- [[SPARK-56768]](https://issues.apache.org/jira/browse/SPARK-56768) Share SBT compile artifact across pyspark CI jobs

### Pandas API on Spark
- **Support Pandas 3** ([[SPARK-55139]](https://issues.apache.org/jira/browse/SPARK-55139))
  - [[SPARK-55156]](https://issues.apache.org/jira/browse/SPARK-55156) Add `include_groups` support to pandas-on-Spark `groupby.apply`, aligning defaults with the installed pandas version (pandas 2 defaults `True` with optional `False` for pandas 3–like behavior; pandas 3 defaults `False` and rejects `True` with an exception).
  - [[SPARK-55244]](https://issues.apache.org/jira/browse/SPARK-55244) For pandas 3, Spark now always uses `np.nan` as the default missing value when creating pandas `StringDtype` string columns.
  - [[SPARK-55296]](https://issues.apache.org/jira/browse/SPARK-55296) Adds support for pandas 3 Copy-on-Write (CoW) mode in Spark’s pandas API, updating behavior to align with pandas 3 semantics when modifying DataFrames/Series views.
  - [[SPARK-55297]](https://issues.apache.org/jira/browse/SPARK-55297) Add a restore method for `timedelta` to preserve/restore the original `timedelta` dtype (similar to the prior datetime restore change) when using pandas 3.
  - [[SPARK-55345]](https://issues.apache.org/jira/browse/SPARK-55345) Makes `TimedeltaIndex` raise an error when users pass the deprecated `unit` or `closed` parameters, aligning behavior with pandas 3.
  - [[SPARK-55376]](https://issues.apache.org/jira/browse/SPARK-55376) Updates pandas-on-Spark `groupby` functions to align with pandas 3 by requiring the `numeric_only` argument to be strictly boolean (rejecting non-boolean values like `None`).
  - [[SPARK-55490]](https://issues.apache.org/jira/browse/SPARK-55490) Update PySpark pandas-on-Spark to match pandas 3 behavior so `groupby(..., as_index=False)` includes grouping keys even when the grouping comes from an external object not present as a DataFrame column.
  - [[SPARK-55648]](https://issues.apache.org/jira/browse/SPARK-55648) Updates Spark pandas API behavior to handle the removal of the `axis` keyword in `groupby` under pandas 3, avoiding the unexpected keyword argument error and aligning behavior with pandas 3.
  - [[SPARK-55867]](https://issues.apache.org/jira/browse/SPARK-55867) Fixes pandas-on-Spark `StringMethods` to work correctly with pandas 3, updating behaviors of methods like `findall`, `match`, `rsplit`, and `split` to better align with pandas 3.
  - [[SPARK-55896]](https://issues.apache.org/jira/browse/SPARK-55896) Updates the pandas-on-Spark implementation to use NumPy functions instead of Python builtins and fixes `groupby().apply()` behavior to align more closely with pandas 3.
  - [[SPARK-55901]](https://issues.apache.org/jira/browse/SPARK-55901) Make `Series.replace()` raise an error when called with no arguments, aligning PySpark pandas behavior with pandas 3.
  - [[SPARK-56016]](https://issues.apache.org/jira/browse/SPARK-56016) Updates pandas-on-Spark `concat` so that when concatenating mixed `DataFrame`/`Series` row-wise with `ignore_index=True`, it preserves the `Series` name as the output column on pandas 3.0+ (while keeping pandas 2.x behavior), and refines the related namespace test using `subTest` to make failing cases easier to pinpoint.
  - [[SPARK-56219]](https://issues.apache.org/jira/browse/SPARK-56219) Aligns pandas-on-Spark `GroupBy.idxmax` and `GroupBy.idxmin` `skipna=False` behavior with pandas 2/3 version-specific semantics.
  - [[SPARK-55700]](https://issues.apache.org/jira/browse/SPARK-55700) Follow-up to use positional access (`.iloc[0]`) when squeezing a single-element Series.
  - [[SPARK-56060]](https://issues.apache.org/jira/browse/SPARK-56060) Updates `DataFrame.describe()` and related tests to handle the pandas 3 `astype(str)` behavior change on null values for empty timestamp-containing frames.
  - [[SPARK-56080]](https://issues.apache.org/jira/browse/SPARK-56080) Updates `Series.argmax` and `Series.argmin` to match pandas 3.0 behavior for NA handling.
  - [[SPARK-56081]](https://issues.apache.org/jira/browse/SPARK-56081) Updates pandas-on-Spark `idxmax` and `idxmin` behavior to follow pandas 3 semantics for NA value handling.
  - [[SPARK-56113]](https://issues.apache.org/jira/browse/SPARK-56113) Updates string restoration in `string_ops.py` so string columns are restored with the pandas dtype carried in the internal field when converting back to pandas in pandas 3 environments.
  - [[SPARK-56118]](https://issues.apache.org/jira/browse/SPARK-56118) Aligns pandas-on-Spark `GroupBy.quantile` bool-dtype behavior with pandas 3.0.
  - [[SPARK-56122]](https://issues.apache.org/jira/browse/SPARK-56122) Updates `Series.cov` to use pandas' `is_numeric_dtype` instead of `np.issubdtype(..., np.number)` for dtype validation, aligning with pandas 3.
  - [[SPARK-56167]](https://issues.apache.org/jira/browse/SPARK-56167) Updates pandas-on-Spark `astype` paths to match pandas 3 behavior for the default string dtype.
  - [[SPARK-56168]](https://issues.apache.org/jira/browse/SPARK-56168) Relaxes diff-frame groupby length test assertions for pandas 3 compatibility.
  - [[SPARK-56187]](https://issues.apache.org/jira/browse/SPARK-56187) Updates `Series.argsort()` to follow pandas 3 behavior for null value ordering.
  - [[SPARK-56188]](https://issues.apache.org/jira/browse/SPARK-56188) Updates `Series.map` for pandas 3 when the mapper is an empty plain `dict`.
  - [[SPARK-56245]](https://issues.apache.org/jira/browse/SPARK-56245) Fixes `DataFrame.eval` with `inplace=True` on pandas 3 by making a writable copy of the pandas batch frame before calling `pdf.eval(..., inplace=True)`.
  - [[SPARK-55140]](https://issues.apache.org/jira/browse/SPARK-55140) Do not map builtin functions to numpy version for pandas 3
  - [[SPARK-55154]](https://issues.apache.org/jira/browse/SPARK-55154) Remove fastpath to pd.Series for pandas 3
  - [[SPARK-55225]](https://issues.apache.org/jira/browse/SPARK-55225) Restore to the original dtype for Datetime
  - [[SPARK-55226]](https://issues.apache.org/jira/browse/SPARK-55226) Recognize datetime and timedelta with units other than
  - [[SPARK-55403]](https://issues.apache.org/jira/browse/SPARK-55403) Fix `no attribute 'draw'` error in the plot tests with pandas 3
  - [[SPARK-55408]](https://issues.apache.org/jira/browse/SPARK-55408) Handle unexpected keyword argument errors related to datetime with pandas 3
  - [[SPARK-55409]](https://issues.apache.org/jira/browse/SPARK-55409) Handle an unexpected keyword argument error from read_excel with pandas 3
  - [[SPARK-55472]](https://issues.apache.org/jira/browse/SPARK-55472) Raise `AttributeError` from methods removed in pandas 3
  - [[SPARK-55625]](https://issues.apache.org/jira/browse/SPARK-55625) Fix StringOps to make `str` dtype work properly
  - [[SPARK-55843]](https://issues.apache.org/jira/browse/SPARK-55843) Handle the unit of datetime64 and timedelta64 dtypes
  - [[SPARK-55946]](https://issues.apache.org/jira/browse/SPARK-55946) Set up __pandas_priority__ so mixed binary ops dispatch correctly to pandas-on-Spark
  - [[SPARK-55989]](https://issues.apache.org/jira/browse/SPARK-55989) Preserve non-int64 index dtypes in `restore_index`
- **Add missing parameters for Pandas API on Spark** ([[SPARK-46156]](https://issues.apache.org/jira/browse/SPARK-46156))
  - [[SPARK-46162]](https://issues.apache.org/jira/browse/SPARK-46162) Add support for the `axis` argument (including `axis=1`) in `pandas.DataFrame.nunique`.
  - [[SPARK-46163]](https://issues.apache.org/jira/browse/SPARK-46163) Adds the missing `filter_func` and `errors` parameters to the PySpark `DataFrame.update` API.
  - [[SPARK-46165]](https://issues.apache.org/jira/browse/SPARK-46165) Adds support for the missing `axis=1` parameter in the pandas API on Spark implementation of `pandas.DataFrame.any`.
  - [[SPARK-46167]](https://issues.apache.org/jira/browse/SPARK-46167) Adds support for the `axis` parameter in `DataFrame.rank`, completing the previously missing API behavior.
  - [[SPARK-46168]](https://issues.apache.org/jira/browse/SPARK-46168) Adds support for an `axis` argument to the `idxmax` API.
  - [[SPARK-46166]](https://issues.apache.org/jira/browse/SPARK-46166) Implements support for the `axis=1` parameter in the `pandas.DataFrame.any` function, allowing it to operate along columns.
- [[SPARK-47996]](https://issues.apache.org/jira/browse/SPARK-47996) Adds support for `"cross"` merges in Spark’s pandas API by allowing `"cross"` as the `how` parameter in `merge`.
- [[SPARK-47997]](https://issues.apache.org/jira/browse/SPARK-47997) Adds the `errors` parameter to pandas-on-Spark `DataFrame.drop` and `Series.drop` to match the pandas API.
- [[SPARK-54337]](https://issues.apache.org/jira/browse/SPARK-54337) Introduces support for the PyCapsule protocol in PySpark, allowing for seamless data interchange between Spark and other Python libraries like Polars and DuckDB.
- [[SPARK-55662]](https://issues.apache.org/jira/browse/SPARK-55662) Adds `axis=1` support for `DataFrame.idxmin`, aligning its behavior with the existing `idxmax(axis=1)` implementation.

### Structured Streaming
- [[SPARK-38498]](https://issues.apache.org/jira/browse/SPARK-38498) Introduces support for adding customized `StreamingListener` to `StreamingContext` through configuration, allowing users to specify listeners using `spark.streaming.extraListeners`.
- [[SPARK-54063]](https://issues.apache.org/jira/browse/SPARK-54063) Adds the functionality for the StateStoreProvider to force the creation of a snapshot during a commit when it detects lag in snapshot creation due to too many changelogs.
- [[SPARK-54106]](https://issues.apache.org/jira/browse/SPARK-54106) Reintroduces a state store row checksum implementation to detect and prevent data corruption at the row level for both HDFS and RocksDB state stores.
- [[SPARK-54121]](https://issues.apache.org/jira/browse/SPARK-54121) Introduces an automatic snapshot repair mechanism for the state store in the Structured Streaming component of Apache Spark.
- [[SPARK-54346]](https://issues.apache.org/jira/browse/SPARK-54346) Introduces an API for offline repartitioning of streaming state, though it is not yet exposed as it is still in development.
- [[SPARK-54388]](https://issues.apache.org/jira/browse/SPARK-54388) Introduces a new StatePartitionReader, StatePartitionReaderAllColumnFamilies, which supports offline repartition by scanning raw bytes for all column families in a state store.
- [[SPARK-54411]](https://issues.apache.org/jira/browse/SPARK-54411) Introduces a Repartition Writer that supports operations with multiple column families, such as TransformWithState, including support for List, Map, and Value state variables, as well as event time timers, processing time timers, and TTLs.
- [[SPARK-54419]](https://issues.apache.org/jira/browse/SPARK-54419) Enhances the StatePartitionAllColumnFamiliesReader to support operators with multiple column families, such as TransformWithState and Stream Stream Join V3.
- [[SPARK-54420]](https://issues.apache.org/jira/browse/SPARK-54420) Introduces the StatePartitionAllColumnFamiliesWriter for offline repartitioning.
- [[SPARK-54423]](https://issues.apache.org/jira/browse/SPARK-54423) Introduces the OffsetMap format to key source progress by source name rather than ordinal in the logical plan.
- [[SPARK-54443]](https://issues.apache.org/jira/browse/SPARK-54443) Integrates the PartitionKeyExtractor into the StatePartitionAllColumnFamiliesReader, allowing it to return the actual partition key and schema instead of the entire key value.
- [[SPARK-54583]](https://issues.apache.org/jira/browse/SPARK-54583) Introduces a configuration option to enable the use of OffsetMap by decoupling OffsetSeqMetadata versioning from OffsetLog versioning.
- [[SPARK-54590]](https://issues.apache.org/jira/browse/SPARK-54590) Adds Checkpoint V2 support to state repartitioning and the State Rewriter by returning and propagating checkpoint IDs after state writes complete.
- [[SPARK-54660]](https://issues.apache.org/jira/browse/SPARK-54660) Introduces an RTM trigger to PySpark, enabling PySpark queries to run in RTM mode.
- [[SPARK-54675]](https://issues.apache.org/jira/browse/SPARK-54675) Introduces a new configuration parameter, `spark.sql.streaming.stateStore.maintenanceForceShutdownTimeout`, which allows users to configure the timeout for forceful shutdown operations in the StateStore maintenance thread pool.
- [[SPARK-54907]](https://issues.apache.org/jira/browse/SPARK-54907) Introduces the `NameStreamingSources` analyzer rule and necessary infrastructure to support streaming source evolution in Apache Spark.
- [[SPARK-54924]](https://issues.apache.org/jira/browse/SPARK-54924) Introduces a State Rewriter for stateful streaming queries in Apache Spark.
- [[SPARK-54984]](https://issues.apache.org/jira/browse/SPARK-54984) Integrates the Repartition runner with the State rewriter to enable the end-to-end execution of offline state repartitioning, as introduced in a previous PR.
- [[SPARK-55013]](https://issues.apache.org/jira/browse/SPARK-55013) Introduces SQL parser support for the streaming source naming infrastructure, enabling SQL-based streaming queries to be compatible with source evolution.
- [[SPARK-55039]](https://issues.apache.org/jira/browse/SPARK-55039) Adds SQL support for naming streaming sources via an `IDENTIFIED BY` clause, e.g.
- [[SPARK-55054]](https://issues.apache.org/jira/browse/SPARK-55054) Extends the SQL `IDENTIFIED BY` clause to streaming table-valued functions (TVFs), aligning them with existing support for naming streaming tables.
- [[SPARK-55057]](https://issues.apache.org/jira/browse/SPARK-55057) Adds infrastructure for *named* structured streaming sources and a resolution pipeline that carries those names through analysis, enabling stable checkpoint paths and safer query evolution when sources are added/removed/reordered.
- [[SPARK-55058]](https://issues.apache.org/jira/browse/SPARK-55058) Adds validation for Structured Streaming checkpoints to detect missing metadata when offset/commit logs are present and fail fast with a new `MISSING_METADATA_FILE` error instead of restarting with a new query ID that can cause exactly-once sinks to duplicate data.
- [[SPARK-55121]](https://issues.apache.org/jira/browse/SPARK-55121) Adds a new `.name()` method to Classic PySpark `DataStreamReader` so users can assign a stable, validated source name for streaming reads, which is recorded in checkpoint metadata and helps keep checkpoint locations stable as sources evolve.
- [[SPARK-55123]](https://issues.apache.org/jira/browse/SPARK-55123) Adds a new `SequentialUnionOffset` (an `OffsetV2`) for Structured Streaming to track sequential union source progress in backfill-to-live scenarios, using stable name-based source tracking with validation and JSON serialization/deserialization support.
- [[SPARK-55129]](https://issues.apache.org/jira/browse/SPARK-55129) Introduces new UnsafeRow key state encoders that treat event-time timestamps as a first-class part of the serialized key (either as a prefix or postfix) to enable efficient prefix/range scans and reduce serialization/deserialization overhead compared to combining two UnsafeRows.
- [[SPARK-55144]](https://issues.apache.org/jira/browse/SPARK-55144) Implements a new event-time-aware state format (with a primary store plus a timestamp/key secondary index) for stream-stream join to avoid full state scans during eviction and unmatched-row handling, making eviction cost proportional to rows actually evicted.
- [[SPARK-55145]](https://issues.apache.org/jira/browse/SPARK-55145) Adds Avro support for `TimestampAsPrefixKeyStateEncoder` and `TimestampAsPostfixKeyStateEncoder`, resolving a TODO from the initial implementation.
- [[SPARK-55146]](https://issues.apache.org/jira/browse/SPARK-55146) Introduce an offline state repartition API and a checkpoint manager in PySpark to support offline state repartitioning.
- [[SPARK-55304]](https://issues.apache.org/jira/browse/SPARK-55304) Adds admission control and `Trigger.AvailableNow` support to the Python Data Source streaming reader API by updating `DataSourceStreamReader.latestOffset` to accept `(start, limit: ReadLimit)`, introducing optional `getDefaultReadLimit` and `reportLatestOffset` hooks plus built-in `ReadLimit` types, and adding a `SupportsTriggerAvailableNow` mix-in interface for sources to implement `prepareForTriggerAvailableNow`.
- [[SPARK-55601]](https://issues.apache.org/jira/browse/SPARK-55601) Derive `streamingSourceIdentifyingName` lazily from the `DataSource` instead of passing it through `StreamingRelation` constructors, and use the names from `StreamingRelation`/`StreamingRelationV2` in `MicroBatchExecution` to key the `OffsetMap` by source name during query execution.
- [[SPARK-55628]](https://issues.apache.org/jira/browse/SPARK-55628) Integrates stream-stream join state format V4 (timestamp-based indexing with a secondary index) into the operator by enabling version selection via config, gating it behind `spark.sql.streaming.join.stateFormatV4.enabled`, routing V4 through the VCF path with schema version 3, and updating checkpoint routing, watermark units, encoder-spec deserialization, and schema/column-family handling to support V4 correctly.
- [[SPARK-55728]](https://issues.apache.org/jira/browse/SPARK-55728) Introduces `spark.sql.streaming.stateStore.fileChecksumThreadPoolSize` config (default: 4) to control threads used by `ChecksumCheckpointFileManager`.
- [[SPARK-55729]](https://issues.apache.org/jira/browse/SPARK-55729) Enables the state data source reader to read state with the new V4 format for stream-stream joins.
- [[SPARK-55751]](https://issues.apache.org/jira/browse/SPARK-55751) Adds `rocksdbNumLoadedFromDfs` metric tracking how many `load()` operations fetched state from remote (cloud/DFS) storage vs.
- [[SPARK-55973]](https://issues.apache.org/jira/browse/SPARK-55973) Optimizes stream-stream **LeftSemi** joins by processing the right side before the left and by eagerly evicting matched left-side state (instead of waiting for the watermark), reducing unnecessary state-store retention and improving related metrics.
- [[SPARK-55999]](https://issues.apache.org/jira/browse/SPARK-55999) Changes the default of `forceSnapshotUploadOnLag` from `false` to `true`, allowing state store to upload snapshots in the query execution thread when the maintenance thread is lagging.
- [[SPARK-56216]](https://issues.apache.org/jira/browse/SPARK-56216) Adds auto-repair snapshot support to the checkpoint V2 (state store checkpoint IDs) load path.
- [[SPARK-56384]](https://issues.apache.org/jira/browse/SPARK-56384) Supports stream-stream non-outer join (Inner/LeftSemi) in Update output mode.
- [[SPARK-56700]](https://issues.apache.org/jira/browse/SPARK-56700) Removes the `private[sql]` modifier from `DataStreamReader.name(sourceName)` and adds it as a public abstract API on the `DataStreamReader` base class — now an `Experimental` public API available to all users.

### MLlib
- [[SPARK-41916]](https://issues.apache.org/jira/browse/SPARK-41916) Updates the Torch distributor to support multiple torchrun processes per task when the number of GPUs per task (`task.gpu.amount`) is greater than 1, which is a common use case.

### SparkR
- [[SPARK-56831]](https://issues.apache.org/jira/browse/SPARK-56831) Share SBT precompile artifact with sparkr CI job

### Declarative Pipelines
- **SPIP: Declarative Pipelines** ([[SPARK-51727]](https://issues.apache.org/jira/browse/SPARK-51727))
  - [[SPARK-52463]](https://issues.apache.org/jira/browse/SPARK-52463) Introduces support for the `cluster_by` argument in Python Pipelines APIs, specifically within the `table` and `materialized_view` decorators.
  - [[SPARK-54020]](https://issues.apache.org/jira/browse/SPARK-54020) Introduces support for using `spark.sql(...)` within query functions in Spark Declarative Pipelines.
  - [[SPARK-54191]](https://issues.apache.org/jira/browse/SPARK-54191) Adds a new feature to the Defineflow Proto by introducing the 'once' option, which supports creating one-time back-fill flows.
  - [[SPARK-54231]](https://issues.apache.org/jira/browse/SPARK-54231) Fill gaps in SDP docs
  - [[SPARK-54280]](https://issues.apache.org/jira/browse/SPARK-54280) Require pipeline checkpoint storage dir to be absolute path
  - [[SPARK-54356]](https://issues.apache.org/jira/browse/SPARK-54356) Fix EndToEndAPISuite caused by missing storage root schema
  - [[SPARK-54358]](https://issues.apache.org/jira/browse/SPARK-54358) Checkpoint dirs collide when streaming tables in different schemas have same name
  - [[SPARK-54376]](https://issues.apache.org/jira/browse/SPARK-54376) Mark most pipeline configuration options as internal
  - [[SPARK-54418]](https://issues.apache.org/jira/browse/SPARK-54418) Fix error messages and code formatting
  - [[SPARK-54435]](https://issues.apache.org/jira/browse/SPARK-54435) spark-pipelines init should avoid overwriting existing directory
  - [[SPARK-54440]](https://issues.apache.org/jira/browse/SPARK-54440) Give default pipeline spec file more idiomatic name, `spark-pipeline.yml`
  - [[SPARK-54452]](https://issues.apache.org/jira/browse/SPARK-54452) Fix empty response from SparkConnect server for `spark.sql(...)` inside FlowFunction
  - [[SPARK-54562]](https://issues.apache.org/jira/browse/SPARK-54562) Block eager analysis / execution inside flow function from the server side
  - [[SPARK-55945]](https://issues.apache.org/jira/browse/SPARK-55945) Support structured identifiers for flows in SDP eager analysis protos
- [[SPARK-7008]](https://issues.apache.org/jira/browse/SPARK-7008) Make `org.apache.spark.sql.pipelines` internal package and make `EstimatorUtils` private

### Geospatial
- **SPIP: Add geospatial types in Spark** ([[SPARK-51658]](https://issues.apache.org/jira/browse/SPARK-51658))
  - [[SPARK-56682]](https://issues.apache.org/jira/browse/SPARK-56682) Extends the `st_asbinary` geospatial WKB writer to accept an optional second argument specifying endianness for the output bytes (`st_asbinary(geo[, endianness])`), wired through SQL, Scala, and PySpark surfaces.
  - [[SPARK-54079]](https://issues.apache.org/jira/browse/SPARK-54079) Introduces a foundational framework in Catalyst for handling spatial data using ST expressions.
  - [[SPARK-54101]](https://issues.apache.org/jira/browse/SPARK-54101) Introduces a framework to add ST geospatial functions in the Scala API, starting with basic WKB read/write functions.
  - [[SPARK-54110]](https://issues.apache.org/jira/browse/SPARK-54110) Introduces type encoders for Geography and Geometry types in Spark.
  - [[SPARK-54142]](https://issues.apache.org/jira/browse/SPARK-54142) Implements the `st_srid` function in both Scala and PySpark, expanding API support for the `ST_Srid` expression.
  - [[SPARK-54151]](https://issues.apache.org/jira/browse/SPARK-54151) Introduces a framework for adding spatial (ST) functions in PySpark, starting with basic WKB read/write capabilities.
  - [[SPARK-54160]](https://issues.apache.org/jira/browse/SPARK-54160) Implements the `ST_SetSrid` expression in Spark SQL, allowing users to set the SRID (Spatial Reference System Identifier) for `GEOGRAPHY` or `GEOMETRY` values.
  - [[SPARK-54162]](https://issues.apache.org/jira/browse/SPARK-54162) Enables explicit casting from GeographyType to GeometryType in Apache Spark SQL, provided they share the same SRID, thus facilitating geospatial data handling.
  - [[SPARK-54175]](https://issues.apache.org/jira/browse/SPARK-54175) Introduces `Geography` and `Geometry` types to the Spark Connect protocol to enable support for geospatial data types.
  - [[SPARK-54176]](https://issues.apache.org/jira/browse/SPARK-54176) Introduces `GeographyType` and `GeometryType` data types to PySpark Connect, along with classes to represent `Geography` and `Geometry` values in Python.
  - [[SPARK-54166]](https://issues.apache.org/jira/browse/SPARK-54166) Introduce type encoders for geospatial types in PySpark
  - [[SPARK-54169]](https://issues.apache.org/jira/browse/SPARK-54169) Introduce Geography and Geometry types in Arrow writer
  - [[SPARK-54201]](https://issues.apache.org/jira/browse/SPARK-54201) Allow casting from GeographyType(srid) to GeographyType(ANY)
  - [[SPARK-54202]](https://issues.apache.org/jira/browse/SPARK-54202) Allow casting from GeometryType(srid) to GeometryType(ANY)
  - [[SPARK-54232]](https://issues.apache.org/jira/browse/SPARK-54232) Enable Arrow serialization for Geography and Geometry types
  - [[SPARK-54244]](https://issues.apache.org/jira/browse/SPARK-54244) Introduce type coercion support for GEOMETRY data types
  - [[SPARK-54253]](https://issues.apache.org/jira/browse/SPARK-54253) Add a guarding config for geospatial support
  - [[SPARK-54399]](https://issues.apache.org/jira/browse/SPARK-54399) Implement the st_setsrid function in Scala and PySpark
  - [[SPARK-55238]](https://issues.apache.org/jira/browse/SPARK-55238) Move Geo SRS mapping logic from `main/scala` to `main/java`
  - [[SPARK-55253]](https://issues.apache.org/jira/browse/SPARK-55253) Remove nonansi golden files for ST functions
  - [[SPARK-55259]](https://issues.apache.org/jira/browse/SPARK-55259) Implement Parquet schema conversion for Geo types
  - [[SPARK-55260]](https://issues.apache.org/jira/browse/SPARK-55260) Implement Parquet write support for Geo types
  - [[SPARK-55261]](https://issues.apache.org/jira/browse/SPARK-55261) Implement Parquet read support for Geo types
  - [[SPARK-55262]](https://issues.apache.org/jira/browse/SPARK-55262) Block Geo types in all file based data sources except Parquet
  - [[SPARK-55295]](https://issues.apache.org/jira/browse/SPARK-55295) Extend the ST_GeomFromWKB function to take an optional SRID value
  - [[SPARK-55339]](https://issues.apache.org/jira/browse/SPARK-55339) Implement WKT writer support for Geo objects
  - [[SPARK-55449]](https://issues.apache.org/jira/browse/SPARK-55449) Enable WKB parsing and writing for Geography
  - [[SPARK-55530]](https://issues.apache.org/jira/browse/SPARK-55530) Support Geo result sets in Hive and Thrift server
  - [[SPARK-55539]](https://issues.apache.org/jira/browse/SPARK-55539) Allow casting from GeographyType to GeometryType
  - [[SPARK-55541]](https://issues.apache.org/jira/browse/SPARK-55541) Support Geometry and Geography in catalyst type converters
  - [[SPARK-55638]](https://issues.apache.org/jira/browse/SPARK-55638) Refactor WKT serialization in GeometryModel
  - [[SPARK-55640]](https://issues.apache.org/jira/browse/SPARK-55640) Propagate WKB parsing errors for Geometry and Geography
  - [[SPARK-55790]](https://issues.apache.org/jira/browse/SPARK-55790) Build a complete SRS registry using PROJ 9.7.1 data

### Web UI
- **Spark Web UI Modernization** ([[SPARK-55760]](https://issues.apache.org/jira/browse/SPARK-55760))
  - [[SPARK-55785]](https://issues.apache.org/jira/browse/SPARK-55785) Updates the SQL execution detail page’s plan visualization to use compact operator/cluster labels and adds a clickable right-side details panel that shows structured metrics (including cluster and child-operator metrics) on demand.
  - [[SPARK-55835]](https://issues.apache.org/jira/browse/SPARK-55835) Updates the Spark UI Environment page to show a “Default Value” column and visually highlight (and optionally filter) Spark configuration entries whose values differ from their registered defaults.
  - [[SPARK-55877]](https://issues.apache.org/jira/browse/SPARK-55877) Adds a Unified/Split toggle to the SQL execution detail page’s Plan Details for AQE queries, enabling a side-by-side Initial vs Final plan comparison, while non-AQE queries continue to show the plan text without the toggle.
  - [[SPARK-55878]](https://issues.apache.org/jira/browse/SPARK-55878) Adds a Job Timeline (vis-timeline Gantt chart) to the SQL execution detail page showing job start/end times with colored bars (green=succeeded, red=failed, blue=running).
  - [[SPARK-55880]](https://issues.apache.org/jira/browse/SPARK-55880) Stage IDs shown in the SQL plan visualization metric detail side panel (when “Show Stage ID and Task ID” is enabled) are now clickable links that take you directly to the corresponding stage detail page.
  - [[SPARK-55881]](https://issues.apache.org/jira/browse/SPARK-55881) Extends Spark’s SQL execution REST API (`/api/v1/applications/{appId}/sql/`) to include three additional response fields—`queryId`, `errorMessage`, and `rootExecutionId`—that were previously only available internally.
  - [[SPARK-55961]](https://issues.apache.org/jira/browse/SPARK-55961) Makes the SQL plan visualization’s detail side panel collapsible so the graph uses full page width by default, automatically showing the panel when a node is clicked and letting users close it via an × button to return to full-width view.
  - [[SPARK-55971]](https://issues.apache.org/jira/browse/SPARK-55971) Adds an “Associated Jobs (N)” collapsible, sortable jobs table to the SQL execution detail page (replacing the old comma-separated job ID links) and updates progress bar labels across the UI to show concise “(N killed)” text while keeping truncated kill reasons in tooltips.
  - [[SPARK-56002]](https://issues.apache.org/jira/browse/SPARK-56002) Enables sorting in the SQL plan visualization side-panel metrics table by making column headers clickable so users can order metrics by name or value.
  - [[SPARK-56140]](https://issues.apache.org/jira/browse/SPARK-56140) Switches the SQL tab from client-side DataTables to server-side pagination with a new `/sql/sqlTable` endpoint, supporting sorting, search, and length menu options (20/50/100/All).
  - [[SPARK-55839]](https://issues.apache.org/jira/browse/SPARK-55839) Adds an "Export" button to the Spark Properties section of the Environment page that downloads the current configuration as a `spark-defaults.conf` formatted file, useful for reproducing environments.
  - [[SPARK-56048]](https://issues.apache.org/jira/browse/SPARK-56048) Adds "Copy Plan" and "Share Link" buttons next to the Download button on the SQL execution detail page, enabling quick clipboard copy of the physical plan text and URL sharing.
  - [[SPARK-56049]](https://issues.apache.org/jira/browse/SPARK-56049) Adds a search input to the SQL plan visualization side panel that filters metrics by name in real-time, making it easier to find specific metrics in complex query plans.
  - [[SPARK-55764]](https://issues.apache.org/jira/browse/SPARK-55764) Use delegated event listener for Bootstrap 5 Tooltip lazy initialization
  - [[SPARK-55766]](https://issues.apache.org/jira/browse/SPARK-55766) Support dark mode with Bootstrap 5 theme toggle
  - [[SPARK-55767]](https://issues.apache.org/jira/browse/SPARK-55767) Use Bootstrap 5 Offcanvas for executor detail panels
  - [[SPARK-55768]](https://issues.apache.org/jira/browse/SPARK-55768) Improve responsive layout with table-responsive wrappers and viz overflow
  - [[SPARK-55771]](https://issues.apache.org/jira/browse/SPARK-55771) Modernize progress bars using Bootstrap 5 Progress component
  - [[SPARK-55776]](https://issues.apache.org/jira/browse/SPARK-55776) Fix data-title to data-bs-title for timeline tooltips after Bootstrap 5 upgrade
  - [[SPARK-55779]](https://issues.apache.org/jira/browse/SPARK-55779) Add tooltip helper utilities for Spark Web UI
  - [[SPARK-55784]](https://issues.apache.org/jira/browse/SPARK-55784) Add Bootstrap 5 table-hover class for row highlight on mouseover
  - [[SPARK-55810]](https://issues.apache.org/jira/browse/SPARK-55810) Fix missing spacing between table and pagination controls in Jobs and Stages page
  - [[SPARK-55834]](https://issues.apache.org/jira/browse/SPARK-55834) Use Bootstrap 5 nav-tabs for Environment page sections
  - [[SPARK-55837]](https://issues.apache.org/jira/browse/SPARK-55837) Render Environment page tables client-side via REST API
  - [[SPARK-55863]](https://issues.apache.org/jira/browse/SPARK-55863) Move Application-level information from Job Tab to footer
  - [[SPARK-55875]](https://issues.apache.org/jira/browse/SPARK-55875) Switch SQL tab query listing to client-side DataTables
  - [[SPARK-55927]](https://issues.apache.org/jira/browse/SPARK-55927) Remove `jquery.mustache.js`
  - [[SPARK-55985]](https://issues.apache.org/jira/browse/SPARK-55985) Remove `jquery.blockUI.min.js`
  - [[SPARK-56143]](https://issues.apache.org/jira/browse/SPARK-56143) Remove `jquery.cookies`
  - [[SPARK-56239]](https://issues.apache.org/jira/browse/SPARK-56239) Fix SQL tab DataTables: API default limit, date format, and appId resolution
  - [[SPARK-56259]](https://issues.apache.org/jira/browse/SPARK-56259) Fix SHS application list table header/data column mismatch
  - [[SPARK-56331]](https://issues.apache.org/jira/browse/SPARK-56331) Truncate long node labels in SQL plan visualization
  - [[SPARK-56354]](https://issues.apache.org/jira/browse/SPARK-56354) Lazy-load vis-timeline resources only on pages that use timeline views
  - [[SPARK-56809]](https://issues.apache.org/jira/browse/SPARK-56809) Show SQL description and metadata on the execution detail page
  - [[SPARK-56811]](https://issues.apache.org/jira/browse/SPARK-56811) Restore sub-execution grouping on the SQL tab listing
- **Improve Spark Event Log, History Server, and Web UI** ([[SPARK-54249]](https://issues.apache.org/jira/browse/SPARK-54249))
  - [[SPARK-53337]](https://issues.apache.org/jira/browse/SPARK-53337) XSS: Ensure the application name in historypage get escaped
  - [[SPARK-54115]](https://issues.apache.org/jira/browse/SPARK-54115) Escalate display ordering priority of connect server operation threads in thread dump page
  - [[SPARK-54320]](https://issues.apache.org/jira/browse/SPARK-54320) Fix Job DAG overlapping
  - [[SPARK-54594]](https://issues.apache.org/jira/browse/SPARK-54594) Skip duplicated edges starting from subqueries in plan dot
  - [[SPARK-54624]](https://issues.apache.org/jira/browse/SPARK-54624) Ensure user name in historypage get escaped
- [[SPARK-54877]](https://issues.apache.org/jira/browse/SPARK-54877) Introduces a new configuration option `spark.ui.showErrorStacks` that allows users to control the display of stack traces on the UI error page.
- [[SPARK-55008]](https://issues.apache.org/jira/browse/SPARK-55008) Updates the Spark SQL UI to display the queryId, which is a globally unique and time-ordered UUIDv7.
- [[SPARK-55522]](https://issues.apache.org/jira/browse/SPARK-55522) Allow inline scripts, event handlers and styles in Spark UI with Content-Security-Policy

### Deployment
- **Support heterogeneous K8s executor management** ([[SPARK-55555]](https://issues.apache.org/jira/browse/SPARK-55555))
  - [[SPARK-55496]](https://issues.apache.org/jira/browse/SPARK-55496) Spark on Kubernetes now allows reusing existing executor PVCs that have been expanded to a larger capacity than originally requested, instead of ignoring them during PVC reuse.
  - [[SPARK-55639]](https://issues.apache.org/jira/browse/SPARK-55639) Adds support for “recovery-mode” Kubernetes executors so that when the driver detects executor OOM failures it can launch replacement executors configured to run only a single task per JVM, with a config (`spark.kubernetes.allocation.recoveryMode.enabled`) to enable/disable the feature.
  - [[SPARK-54780]](https://issues.apache.org/jira/browse/SPARK-54780) Updates the Kubernetes documentation in Apache Spark to recommend using K8s v1.33 or newer for the upcoming Spark 4.2.0 release.
  - [[SPARK-55075]](https://issues.apache.org/jira/browse/SPARK-55075) Adds tracking of Kubernetes executor pod creation failures via `ExecutorFailureTracker` so Spark can stop retrying once maximum executor failures are reached.
  - [[SPARK-55431]](https://issues.apache.org/jira/browse/SPARK-55431) Set Kubernetes executor pods’ container `resizePolicy` explicitly to `NotRequired` to align with Spark’s `restartPolicy=Never` behavior as in-place pod resize becomes stable in newer Kubernetes versions.
  - [[SPARK-55432]](https://issues.apache.org/jira/browse/SPARK-55432) Adds support for the built-in Kubernetes in-place vertical scaling plugin `ExecutorResizePlugin` for Spark executors.
  - [[SPARK-54422]](https://issues.apache.org/jira/browse/SPARK-54422) Increase `spark.kubernetes.allocation.batch.size` to 20
  - [[SPARK-55134]](https://issues.apache.org/jira/browse/SPARK-55134) Fix `BasicExecutorFeatureStep` to throw `IllegalArgumentException` for executor cpu misconfigs
  - [[SPARK-55342]](https://issues.apache.org/jira/browse/SPARK-55342) Fix `ExecutorPodsLifecycleEventHandler` to `ExecutorPodsLifecycleManager`
  - [[SPARK-55485]](https://issues.apache.org/jira/browse/SPARK-55485) Add `Constants.POD_DELETION_COST` for reuse
  - [[SPARK-55649]](https://issues.apache.org/jira/browse/SPARK-55649) Promote `Kubernetes(Driver|Executor)?FeatureConfigStep` traits to `Stable`
  - [[SPARK-55704]](https://issues.apache.org/jira/browse/SPARK-55704) Add `Constants.DEFAULT_PVC_ACCESS_MODE` for reuse
  - [[SPARK-56622]](https://issues.apache.org/jira/browse/SPARK-56622) Update K8s IT CI to use K8s 1.36
  - [[SPARK-56670]](https://issues.apache.org/jira/browse/SPARK-56670) Restrict `ExecutorResizePlugin` to `direct` pods allocator
  - [[SPARK-56684]](https://issues.apache.org/jira/browse/SPARK-56684) Expose `KubernetesClusterSchedulerBackend.kubernetesClient` to `k8s` package
  - [[SPARK-56689]](https://issues.apache.org/jira/browse/SPARK-56689) Improve `ExecutorResizePlugin` to reuse `KubernetesClusterSchedulerBackend.kubernetesClient`
  - [[SPARK-56693]](https://issues.apache.org/jira/browse/SPARK-56693) Support built-in K8s `ExecutorPVCResizePlugin`
  - [[SPARK-56699]](https://issues.apache.org/jira/browse/SPARK-56699) Default `ExecutorPVCResizePlugin` interval to `5min` in 5-minute units
  - [[SPARK-56702]](https://issues.apache.org/jira/browse/SPARK-56702) Restrict `ExecutorPVCResizePlugin` to `direct` pods allocator
- **Improve K8s Resource Manager API** ([[SPARK-56603]](https://issues.apache.org/jira/browse/SPARK-56603))
  - [[SPARK-56163]](https://issues.apache.org/jira/browse/SPARK-56163) Move `uploadFileToHadoopCompatibleFS` to `Utils`
  - [[SPARK-56300]](https://issues.apache.org/jira/browse/SPARK-56300) Add Java-friendly factory method to `KubernetesDriverSpec`
  - [[SPARK-56303]](https://issues.apache.org/jira/browse/SPARK-56303) Add Java-friendly factory methods to `JavaMainAppResource`
  - [[SPARK-56490]](https://issues.apache.org/jira/browse/SPARK-56490) Add Java-friendly `KubernetesConf.createDriverConf`
  - [[SPARK-56574]](https://issues.apache.org/jira/browse/SPARK-56574) Add Java-friendly `KubernetesDriverSpec.getSystemPropertiesAsJavaMap`
  - [[SPARK-56590]](https://issues.apache.org/jira/browse/SPARK-56590) Add Java-friendly getters for driver resources of `KubernetesDriverSpec`
  - [[SPARK-56600]](https://issues.apache.org/jira/browse/SPARK-56600) Promote `SparkPod` to `Stable`
  - [[SPARK-56601]](https://issues.apache.org/jira/browse/SPARK-56601) Promote `KubernetesClientUtils` to `Stable`
  - [[SPARK-56602]](https://issues.apache.org/jira/browse/SPARK-56602) Promote `KubernetesVolumeUtils` to `Stable`
  - [[SPARK-56604]](https://issues.apache.org/jira/browse/SPARK-56604) Promote `KubernetesDriverBuilder` to `Stable`
  - [[SPARK-56623]](https://issues.apache.org/jira/browse/SPARK-56623) Promote `KubernetesDriverSpec` to `Stable`
  - [[SPARK-56624]](https://issues.apache.org/jira/browse/SPARK-56624) Promote `KubernetesUtils` to `Stable`
  - [[SPARK-56736]](https://issues.apache.org/jira/browse/SPARK-56736) Add `sparkVersion` method to `KubernetesConf` abstract class
- **Improve K8s support in Spark 4.1.0** ([[SPARK-54016]](https://issues.apache.org/jira/browse/SPARK-54016))
  - [[SPARK-53944]](https://issues.apache.org/jira/browse/SPARK-53944) Adds support for using the Spark Driver pod IP instead of the Spark Driver's Kubernetes Service for Spark Executors, aiming to bypass Kubernetes DNS issues.
  - [[SPARK-52334]](https://issues.apache.org/jira/browse/SPARK-52334) update all files, jars, and pyFiles to reference the working directory after they are downloaded
  - [[SPARK-54184]](https://issues.apache.org/jira/browse/SPARK-54184) Support `spark.kubernetes.executor.deletedExecutorsCacheTimeout`
  - [[SPARK-54188]](https://issues.apache.org/jira/browse/SPARK-54188) Improve `ExecutorPodsWatchSnapshotSource` to watch only active executors
  - [[SPARK-54189]](https://issues.apache.org/jira/browse/SPARK-54189) Remove `spark.kubernetes.pyspark.pythonVersion`
  - [[SPARK-54197]](https://issues.apache.org/jira/browse/SPARK-54197) Improve `ExecutorsPodsLifecycleManager` not to request to delete if `deletionTimestamp` exists
  - [[SPARK-54198]](https://issues.apache.org/jira/browse/SPARK-54198) Delete Kubernetes executor pods only once per event processing interval
- **Reduce K8s control plane overhead** ([[SPARK-55400]](https://issues.apache.org/jira/browse/SPARK-55400))
  - [[SPARK-55370]](https://issues.apache.org/jira/browse/SPARK-55370) Improve `annotateExecutorDeletionCost` to use `patch` instead of `edit` API
  - [[SPARK-55377]](https://issues.apache.org/jira/browse/SPARK-55377) Improve `labelDecommissioningExecs` to use `patch` instead of `edit` API
  - [[SPARK-55399]](https://issues.apache.org/jira/browse/SPARK-55399) Improve `KubernetesDriverEndpoint` to use `patch` instead of `edit` API
  - [[SPARK-55410]](https://issues.apache.org/jira/browse/SPARK-55410) Improve `SparkKubernetesDiagnosticsSetter` to use `patch` instead of `edit` API
  - [[SPARK-55603]](https://issues.apache.org/jira/browse/SPARK-55603) Improve `removeExecutorFromK8s` to use `patch` instead of `edit` API
  - [[SPARK-56793]](https://issues.apache.org/jira/browse/SPARK-56793) Avoid cluster-wide LIST in executor pods polling
- [[SPARK-54553]](https://issues.apache.org/jira/browse/SPARK-54553) Introduces a new configuration option, `spark.kubernetes.scheduler.volcano.podGroupTemplateJson`, for Spark on Kubernetes with the Volcano scheduler.
- [[SPARK-54916]](https://issues.apache.org/jira/browse/SPARK-54916) Enables the `volcano` profile by default in Apache Spark 4.2.0.
- [[SPARK-55653]](https://issues.apache.org/jira/browse/SPARK-55653) Adds Kubernetes `NetworkPolicy` support for Spark executor pods, restricting access to only pods with the same Spark application ID unless the feature is explicitly excluded via configuration.
- [[SPARK-55831]](https://issues.apache.org/jira/browse/SPARK-55831) Adds a new YARN client-mode config `spark.yarn.am.defaultJavaOptions` that, when set, is prepended to `spark.yarn.am.extraJavaOptions` for the YARN ApplicationMaster.
- [[SPARK-56834]](https://issues.apache.org/jira/browse/SPARK-56834) Use Java `25-jre` instead of `21-jre` image in K8s Dockerfile

### Connectors
- [[SPARK-55062]](https://issues.apache.org/jira/browse/SPARK-55062) Adds optional support for proto2 extension fields in Spark’s `from_protobuf` and `to_protobuf` (when using a file descriptor set), controlled by the `spark.sql.function.protobufExtensions.enabled` config so extension fields are retained instead of dropped.

### Build and Infrastructure
- **Upgrade Ubuntu to 24.04 in CI** ([[SPARK-55482]](https://issues.apache.org/jira/browse/SPARK-55482))
- **Maintain Project Infra for Spark 4.1.0** ([[SPARK-54268]](https://issues.apache.org/jira/browse/SPARK-54268))
- **Apache Spark 4.1.0 Dependency Audit and Cleanup** ([[SPARK-54284]](https://issues.apache.org/jira/browse/SPARK-54284))
- **Improve Maven/SBT build** ([[SPARK-54359]](https://issues.apache.org/jira/browse/SPARK-54359))
  - [[SPARK-54190]](https://issues.apache.org/jira/browse/SPARK-54190) Simplifies Guava dependency management by using a unified version throughout Spark, reducing complexity and package size.
  - [[SPARK-54049]](https://issues.apache.org/jira/browse/SPARK-54049) Shade com.google.thirdparty package to fix Guava class conflicts in spark 4.0
  - [[SPARK-54127]](https://issues.apache.org/jira/browse/SPARK-54127) Fix sbt inconsistent shading package
  - [[SPARK-54242]](https://issues.apache.org/jira/browse/SPARK-54242) Skip `Checkstyle` if `NOLINT_ON_COMPILE` is true
- **Build and Run Spark on Java 25** ([[SPARK-51167]](https://issues.apache.org/jira/browse/SPARK-51167))
  - [[SPARK-55670]](https://issues.apache.org/jira/browse/SPARK-55670) Add `-Dio.netty.noUnsafe=false` to enable Java 25 support
  - [[SPARK-55678]](https://issues.apache.org/jira/browse/SPARK-55678) Add daily test for Java 25
  - [[SPARK-55712]](https://issues.apache.org/jira/browse/SPARK-55712) Allow run benchmark with JDK 25
- **SPIP: Add llms.txt files to Spark Documentation** ([[SPARK-53528]](https://issues.apache.org/jira/browse/SPARK-53528))
  - [[SPARK-53666]](https://issues.apache.org/jira/browse/SPARK-53666) Use absolute output path for `generate-llms-txt.py`
  - [[SPARK-54368]](https://issues.apache.org/jira/browse/SPARK-54368) Remove `generate-llms-txt.py` from `release-build.sh`
- **Support Python 3.14** ([[SPARK-54286]](https://issues.apache.org/jira/browse/SPARK-54286))
  - [[SPARK-54245]](https://issues.apache.org/jira/browse/SPARK-54245) Install `mlflow` at Python 3.14 Docker image
  - [[SPARK-54288]](https://issues.apache.org/jira/browse/SPARK-54288) Add a daily Python 3.14 CI for branch-4.1
- **Drop Python 3.9 Support** ([[SPARK-54262]](https://issues.apache.org/jira/browse/SPARK-54262))
  - [[SPARK-54263]](https://issues.apache.org/jira/browse/SPARK-54263) Fix `run-in-container` script to use Python 3.11 instead of 3.9
  - [[SPARK-54277]](https://issues.apache.org/jira/browse/SPARK-54277) Make `dev/run-tests` to ban `Python 3.9` and older versions
- **Remove pre-built test JAR and class files from the repository** ([[SPARK-56352]](https://issues.apache.org/jira/browse/SPARK-56352))
  - [[SPARK-56471]](https://issues.apache.org/jira/browse/SPARK-56471) Remove release-time binary deletion workaround and CI JAR/class checks
  - [[SPARK-56556]](https://issues.apache.org/jira/browse/SPARK-56556) Reject `.jar` and `.class` files in CI
- [[SPARK-47086]](https://issues.apache.org/jira/browse/SPARK-47086) Upgrades Jetty to 12.1.5, Jersey to 3.1.11, and Servlet to 6.0 in Apache Spark's build, core, and web UI components.
- [[SPARK-54177]](https://issues.apache.org/jira/browse/SPARK-54177) Upgrades gRPC to version 1.76 and protobuf to 6.33, addressing dependency issues and shading leaks in the `spark-connect` jar.
- [[SPARK-54524]](https://issues.apache.org/jira/browse/SPARK-54524) Fix Connect JDBC driver dependencies
- [[SPARK-54597]](https://issues.apache.org/jira/browse/SPARK-54597) Upgrades the `lz4-java` library to version 1.10.0, transitioning to a new repository for continued support and maintenance.
- [[SPARK-54830]](https://issues.apache.org/jira/browse/SPARK-54830) Enables the checksum-based indeterminate shuffle retry feature by default.
- [[SPARK-55193]](https://issues.apache.org/jira/browse/SPARK-55193) Use `CompressionHandler` as a replacement for the deprecated `GzipHandler` in `JettyUtils`
- [[SPARK-55547]](https://issues.apache.org/jira/browse/SPARK-55547) Enable the GitHub Issues feature for the Apache Spark repository.
- [[SPARK-55829]](https://issues.apache.org/jira/browse/SPARK-55829) Skip PySpark/SparkR/TPC-DS CI for static-resource-only changes
- [[SPARK-56209]](https://issues.apache.org/jira/browse/SPARK-56209) Upgrades `io.vertx` dependencies from 4.5.24 to 4.5.26 by declaring them as direct dependencies with exclusion from `kubernetes-client` transitive resolution.

### Other
- [[SPARK-53666]](https://issues.apache.org/jira/browse/SPARK-53666) Add script to generate llms.txt file for Spark main website

### Version upgrade of Java and Scala libraries

| Library Name | Version Change |
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
| gcs-connector | hadoop3-2.2.28 -> REMOVED |
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

Last but not least, this release would not have been possible without the following contributors: AbinayaJayaprakasam, Adam Binford, Adithya Ajith, Aditya Nambiar, Akash Nayar, Alex Khakhlyuk, Alexis Schlomer, Allison Wang, Amanda Liu, Anastasiia Terenteva, Andreas Chatzistergiou, Angerszhuuuu, Anshul Baliga, Anton Lykov, Anton Okolnychyi, Antonio Blanco, Anupam Yadav, Ashrith Bandla, Asif, Babatunde Micheal Okutubo, Biruk Tesfaye, Bjørn Jørgensen, Bo Zhang, Bobby Wang, Boyang Jerry Peng, Brooks Walls, Burak Yavuz, Canadian Data Guy, Celeste Horgan, Chang Chen, Chao Sun, Chen Wang, Cheng Pan, Chhida, Chirag Singh, Chloe Xia, Chris Boumalhab, ChuckLin2025, CuiYanxiang, DB Tsai, DS, Daniel Tenedorio, David, David Milicevic, David Tagatac, Deninelu, Devin Petersohn, Dhruv, Dilip Biswal, Dima Fedoriaka, Dmytro Fedoriaka, Dongjoon Hyun, Dylan Wong, Dzeri96, Eren Avsarogullari, Eric Marnadi, Eric Yang, Eugen, Fangchen Li, Felipe Pessoto, Felix, Filip Davidovic, Fu Chen, Garland Zhang, Gengliang Wang, Gera Shegalov, Gurpreet Nanda, Haiyang Sun, Harsh Motwani, Helios He, Herman van Hovell, Holden Karau, Hongze Zhang, Huanli Wang, Hyukjin Kwon, Ivan Sadikov, Jacek Laskowski, Jacky Wang, James Willis, Jason Teoh, Jerry Zheng, JiaKe, Jiaan Geng, Jiang Xingbo, Jim Halfpenny, Jiwon Park, Johan Lasperas, John Xu, John Zhuge, Jon Mio, Jonathan Chang, Joon Ro, Judyzzz, Juliusz Sompolski, Jungtaek Lim, Junyu Chen, KAZUYUKI TANIMURA, Karthik Prabhakar, Karuppayya, Kavpreet Grewal, Kelvin Jiang, Kent Yao, Kiyeon Jeon, Kousuke Saruta, Kris Mok, Kristin Cowalcijk, Leon Windheuser, Liang-Chi Hsieh, Linhong Liu, Livia Zhu, Luca Canali, Manu Zhang, Marcin Wojtyczka, Marco Gaido, Mark Jarvin, Mark Molinaro, Marko Ilić, Martin Grund, Matt Zhang, Mihailo Aleksic, Mihailo Timotic, Mikhail NIkoliukin, Milan Dankovic, Mingliang Zhu, Nicholas Chew, Nikolina Vraneš, Nishanth28, Pablo Langa, Parth Chandra, Pavle Martinovic, Petar Nikić, Peter Toth, Pranav Dev, Pratham Manja, Qiegang Long, Rahul Sharma, Rishbha, Rito Takeuchi, Robert Dillitz, Ruifeng Zheng, Sahil Kumar Singh, Sandro Sp, Sandy Ryza, Serge Rielau, Shilong Duan, Shrirang Mhalgi, Shuai Lu, Shubhambhusate, Shujing Yang, Simola Nayak, Siying Dong, Stanley Yao, Stefan Kandic, Stefan Savić, Steven Tran, Stevo Mitric, Sven Weber, Szehon Ho, Takuya UESHIN, Tengfei Huang, Thang Long Vu, Tian Gao, Tim Lee, TongWei, Uros Bojanic, Uros Stankovic, VINDHYA G BHAT, Vinod KC, Vlad Rozov, Vladan Vasić, Vladimir Golubev, WHJian, Wei Liu, WeichenXu, Wenchen Fan, Wojciech Szlachta, Xi Lyu, Xiang Li, Xianming Lei, Xianzhe Ma, Xiaonan Yang, Xiaoxuan, Xin Huang, Xinyi, YangJie, Yash Botadra, Yicong Huang, Yihong He, Yuchen Liu, Yuchuan Huang, Yuming Wang, Yuyuan Tang, Zequn Lin, Zero Qu, Zerui Bao, Zhen Wang, Zifei Feng, Ziya Mukhtarov, Zoey, Zouxxyy, aleksandr-chernousov-db, cafri.sun, chenhao-db, cookiedough77, cty, cxzl25, donaldchai, eddiebkheet, efaracci018, ganeshas-db, gaoyajun02, holyvolcano, huangxiaoping, jbharadw-oai, jdavidroberts, kepler62f, lepan, marko-sisovic-db, naveenp2708, nyaapa, qindongliang, raksoras, richardc-db, ruanwenjun, tugce-applied, victors-oai, wuyi, xihuan_mstr, yamayuki-hub, yyanyy.
