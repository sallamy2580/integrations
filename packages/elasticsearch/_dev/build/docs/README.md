# Elasticsearch

The `elasticsearch` package collects metrics and logs of Elasticsearch.

## Compatibility

The `elasticsearch` package can monitor Elasticsearch 6.7.0 and later.

## Logs

NOTE: If you're running against Elasticsearch >= 7.0.0, configure the
`var.paths` setting to point to JSON logs. Otherwise, configure it
to point to plain text logs.

### Compatibility

The Elasticsearch package is compatible with logs from Elasticsearch 6.2 and newer.

### Audit

{{fields "audit"}}

### Deprecation

{{fields "deprecation"}}

### Garbage collection

{{fields "gc"}}

### Server

{{fields "server"}}

### Slowlog

{{fields "slowlog"}}

## Metrics

### Usage for Stack Monitoring

The `elasticsearch` package can be used to collect logs and metrics shown in our Stack Monitoring
UI in Kibana.

### Metric-specific configuration notes

Like other package, `elasticsearch` metrics collection accepts a `hosts` configuration setting.
This setting can contain a list of entries. The related `scope` setting determines how each entry in
the `hosts` list is interpreted by the module.

* If `scope` is set to `node` (default), each entry in the `hosts` list indicates a distinct node in an
  Elasticsearch cluster.
* If `scope` is set to `cluster`, each entry in the `hosts` list indicates a single endpoint for a distinct
  Elasticsearch cluster (for example, a load-balancing proxy fronting the cluster).

### Cross Cluster Replication

CCR It uses the Cross-Cluster Replication Stats API endpoint to fetch metrics about cross-cluster
replication from the Elasticsearch clusters that are participating in cross-cluster
replication.

If the Elasticsearch cluster does not have cross-cluster replication enabled, this package
will not collect metrics. A DEBUG log message about this will be emitted in the log.

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| elasticsearch.ccr.auto_follow.failed.follow_indices.count |  | long |
| elasticsearch.ccr.auto_follow.failed.remote_cluster_state_requests.count |  | long |
| elasticsearch.ccr.auto_follow.success.follow_indices.count |  | long |
| elasticsearch.ccr.bytes_read |  | long |
| elasticsearch.ccr.follower.aliases_version |  | long |
| elasticsearch.ccr.follower.global_checkpoint | Global checkpoint value on follower shard | long |
| elasticsearch.ccr.follower.index | Name of follower index | keyword |
| elasticsearch.ccr.follower.mapping_version |  | long |
| elasticsearch.ccr.follower.max_seq_no | Maximum sequence number of operation on the follower shard | long |
| elasticsearch.ccr.follower.operations.read.count |  | long |
| elasticsearch.ccr.follower.operations_written | Number of operations indexed (replicated) into the follower shard from the leader shard | long |
| elasticsearch.ccr.follower.settings_version |  | long |
| elasticsearch.ccr.follower.shard.number | Number of the shard within the index | long |
| elasticsearch.ccr.follower.time_since_last_read.ms | Time, in ms, since the follower last fetched from the leader | long |
| elasticsearch.ccr.last_requested_seq_no |  | long |
| elasticsearch.ccr.leader.global_checkpoint |  | long |
| elasticsearch.ccr.leader.index | Name of leader index | keyword |
| elasticsearch.ccr.leader.max_seq_no | Maximum sequence number of operation on the leader shard | long |
| elasticsearch.ccr.read_exceptions |  | nested |
| elasticsearch.ccr.remote_cluster |  | keyword |
| elasticsearch.ccr.requests.failed.read.count |  | long |
| elasticsearch.ccr.requests.failed.write.count |  | long |
| elasticsearch.ccr.requests.outstanding.read.count |  | long |
| elasticsearch.ccr.requests.outstanding.write.count |  | long |
| elasticsearch.ccr.requests.successful.read.count |  | long |
| elasticsearch.ccr.requests.successful.write.count |  | long |
| elasticsearch.ccr.shard_id |  | integer |
| elasticsearch.ccr.total_time.read.ms |  | long |
| elasticsearch.ccr.total_time.read.remote_exec.ms |  | long |
| elasticsearch.ccr.total_time.write.ms |  | long |
| elasticsearch.ccr.write_buffer.operation.count |  | long |
| elasticsearch.ccr.write_buffer.size.bytes |  | long |
| elasticsearch.cluster.id | Elasticsearch cluster id. | keyword |
| elasticsearch.cluster.name | Elasticsearch cluster name. | keyword |
| elasticsearch.cluster.state.id | Elasticsearch state id. | keyword |
| elasticsearch.node.id | Node ID | keyword |
| elasticsearch.node.master | Is the node the master node? | boolean |
| elasticsearch.node.mlockall | Is mlockall enabled on the node? | boolean |
| elasticsearch.node.name | Node name. | keyword |

### Cluster Stats

`cluster_stats` interrogates the 
{{ url "elasticsearch-cluster-stats" "Cluster Stats API endpoint" }}
to fetch information about the Elasticsearch cluster.

{{event "cluster_stats"}}

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| elasticsearch.cluster.id | Elasticsearch cluster id. | keyword |
| elasticsearch.cluster.name | Elasticsearch cluster name. | keyword |
| elasticsearch.cluster.state.id | Elasticsearch state id. | keyword |
| elasticsearch.cluster.stats.indices.docs.total | Total number of indices in cluster. | long |
| elasticsearch.cluster.stats.indices.fielddata.memory.bytes | Memory used for fielddata. | long |
| elasticsearch.cluster.stats.indices.shards.count | Total number of shards in cluster. | long |
| elasticsearch.cluster.stats.indices.shards.primaries | Total number of primary shards in cluster. | long |
| elasticsearch.cluster.stats.indices.store.size.bytes |  | long |
| elasticsearch.cluster.stats.indices.total |  | long |
| elasticsearch.cluster.stats.license.expiry_date_in_millis |  | long |
| elasticsearch.cluster.stats.license.status |  | keyword |
| elasticsearch.cluster.stats.license.type |  | keyword |
| elasticsearch.cluster.stats.nodes.count | Total number of nodes in cluster. | long |
| elasticsearch.cluster.stats.nodes.data |  | long |
| elasticsearch.cluster.stats.nodes.fs.available.bytes |  | long |
| elasticsearch.cluster.stats.nodes.fs.total.bytes |  | long |
| elasticsearch.cluster.stats.nodes.jvm.max_uptime.ms |  | long |
| elasticsearch.cluster.stats.nodes.jvm.memory.heap.max.bytes |  | long |
| elasticsearch.cluster.stats.nodes.jvm.memory.heap.used.bytes |  | long |
| elasticsearch.cluster.stats.nodes.master | Number of master-eligible nodes in cluster. | long |
| elasticsearch.cluster.stats.nodes.stats.data | Number of data nodes in cluster. | long |
| elasticsearch.cluster.stats.stack.apm.found |  | boolean |
| elasticsearch.cluster.stats.stack.xpack.ccr.available |  | boolean |
| elasticsearch.cluster.stats.stack.xpack.ccr.enabled |  | boolean |
| elasticsearch.cluster.stats.state.master_node |  | keyword |
| elasticsearch.cluster.stats.state.nodes_hash |  | keyword |
| elasticsearch.cluster.stats.state.state_uuid |  | keyword |
| elasticsearch.cluster.stats.state.version |  | keyword |
| elasticsearch.cluster.stats.status | Cluster status (green, yellow, red). | keyword |
| elasticsearch.cluster.stats.version |  | keyword |
| elasticsearch.node.id | Node ID | keyword |
| elasticsearch.node.master | Is the node the master node? | boolean |
| elasticsearch.node.mlockall | Is mlockall enabled on the node? | boolean |
| elasticsearch.node.name | Node name. | keyword |
| elasticsearch.version |  | keyword |

### Enrich

Enrch interrogates the {{ url "elasticsearch-enrich-stats-api" "Enrich Stats API" }}
endpoint to fetch information about Enrich coordinator nodesin the Elasticsearch cluster that are participating in 
ingest-time enrichment.

{{event "enrich"}}

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| elasticsearch.cluster.id | Elasticsearch cluster id. | keyword |
| elasticsearch.cluster.name | Elasticsearch cluster name. | keyword |
| elasticsearch.cluster.state.id | Elasticsearch state id. | keyword |
| elasticsearch.enrich.executed_searches.total | Number of search requests that enrich processors have executed since node startup. | long |
| elasticsearch.enrich.executing_policy.name |  | keyword |
| elasticsearch.enrich.executing_policy.task.action |  | keyword |
| elasticsearch.enrich.executing_policy.task.cancellable |  | boolean |
| elasticsearch.enrich.executing_policy.task.id |  | long |
| elasticsearch.enrich.executing_policy.task.parent_task_id |  | keyword |
| elasticsearch.enrich.executing_policy.task.task |  | keyword |
| elasticsearch.enrich.executing_policy.task.time.running.nano |  | long |
| elasticsearch.enrich.executing_policy.task.time.start.ms |  | long |
| elasticsearch.enrich.queue.size | Number of search requests in the queue. | long |
| elasticsearch.enrich.remote_requests.current | Current number of outstanding remote requests. | long |
| elasticsearch.enrich.remote_requests.total | Number of outstanding remote requests executed since node startup. | long |
| elasticsearch.node.id | Node ID | keyword |
| elasticsearch.node.master | Is the node the master node? | boolean |
| elasticsearch.node.mlockall | Is mlockall enabled on the node? | boolean |
| elasticsearch.node.name | Node name. | keyword |

### Index

{{event "index"}}

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Event timestamp. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| elasticsearch.cluster.id | Elasticsearch cluster id. | keyword |
| elasticsearch.cluster.name | Elasticsearch cluster name. | keyword |
| elasticsearch.cluster.state.id | Elasticsearch state id. | keyword |
| elasticsearch.index.created |  | long |
| elasticsearch.index.hidden |  | boolean |
| elasticsearch.index.name | Index name. | keyword |
| elasticsearch.index.primaries.docs.count |  | long |
| elasticsearch.index.primaries.docs.deleted |  | long |
| elasticsearch.index.primaries.indexing.index_time_in_millis |  | long |
| elasticsearch.index.primaries.indexing.index_total |  | long |
| elasticsearch.index.primaries.indexing.throttle_time_in_millis |  | long |
| elasticsearch.index.primaries.merges.total_size_in_bytes |  | long |
| elasticsearch.index.primaries.query_cache.hit_count |  | long |
| elasticsearch.index.primaries.query_cache.memory_size_in_bytes |  | long |
| elasticsearch.index.primaries.query_cache.miss_count |  | long |
| elasticsearch.index.primaries.refresh.external_total_time_in_millis |  | long |
| elasticsearch.index.primaries.refresh.total_time_in_millis |  | long |
| elasticsearch.index.primaries.request_cache.evictions |  | long |
| elasticsearch.index.primaries.request_cache.hit_count |  | long |
| elasticsearch.index.primaries.request_cache.memory_size_in_bytes |  | long |
| elasticsearch.index.primaries.request_cache.miss_count |  | long |
| elasticsearch.index.primaries.search.query_time_in_millis |  | long |
| elasticsearch.index.primaries.search.query_total |  | long |
| elasticsearch.index.primaries.segments.count |  | long |
| elasticsearch.index.primaries.segments.doc_values_memory_in_bytes |  | long |
| elasticsearch.index.primaries.segments.fixed_bit_set_memory_in_bytes |  | long |
| elasticsearch.index.primaries.segments.index_writer_memory_in_bytes |  | long |
| elasticsearch.index.primaries.segments.memory_in_bytes |  | long |
| elasticsearch.index.primaries.segments.norms_memory_in_bytes |  | long |
| elasticsearch.index.primaries.segments.points_memory_in_bytes |  | long |
| elasticsearch.index.primaries.segments.stored_fields_memory_in_bytes |  | long |
| elasticsearch.index.primaries.segments.term_vectors_memory_in_bytes |  | long |
| elasticsearch.index.primaries.segments.terms_memory_in_bytes |  | long |
| elasticsearch.index.primaries.segments.version_map_memory_in_bytes |  | long |
| elasticsearch.index.primaries.store.size_in_bytes |  | long |
| elasticsearch.index.shards.total |  | long |
| elasticsearch.index.status |  | keyword |
| elasticsearch.index.total.docs.count | Total number of documents in the index. | long |
| elasticsearch.index.total.docs.deleted | Total number of deleted documents in the index. | long |
| elasticsearch.index.total.fielddata.evictions |  | long |
| elasticsearch.index.total.fielddata.memory_size_in_bytes |  | long |
| elasticsearch.index.total.indexing.index_time_in_millis |  | long |
| elasticsearch.index.total.indexing.index_total |  | long |
| elasticsearch.index.total.indexing.throttle_time_in_millis |  | long |
| elasticsearch.index.total.merges.total_size_in_bytes |  | long |
| elasticsearch.index.total.query_cache.evictions |  | long |
| elasticsearch.index.total.query_cache.hit_count |  | long |
| elasticsearch.index.total.query_cache.memory_size_in_bytes |  | long |
| elasticsearch.index.total.query_cache.miss_count |  | long |
| elasticsearch.index.total.refresh.external_total_time_in_millis |  | long |
| elasticsearch.index.total.refresh.total_time_in_millis |  | long |
| elasticsearch.index.total.request_cache.evictions |  | long |
| elasticsearch.index.total.request_cache.hit_count |  | long |
| elasticsearch.index.total.request_cache.memory_size_in_bytes |  | long |
| elasticsearch.index.total.request_cache.miss_count |  | long |
| elasticsearch.index.total.search.query_time_in_millis |  | long |
| elasticsearch.index.total.search.query_total |  | long |
| elasticsearch.index.total.segments.count | Total number of index segments. | long |
| elasticsearch.index.total.segments.doc_values_memory_in_bytes |  | long |
| elasticsearch.index.total.segments.fixed_bit_set_memory_in_bytes |  | long |
| elasticsearch.index.total.segments.index_writer_memory_in_bytes |  | long |
| elasticsearch.index.total.segments.memory_in_bytes | Total number of memory used by the segments in bytes. | long |
| elasticsearch.index.total.segments.norms_memory_in_bytes |  | long |
| elasticsearch.index.total.segments.points_memory_in_bytes |  | long |
| elasticsearch.index.total.segments.stored_fields_memory_in_bytes |  | long |
| elasticsearch.index.total.segments.term_vectors_memory_in_bytes |  | long |
| elasticsearch.index.total.segments.terms_memory_in_bytes |  | long |
| elasticsearch.index.total.segments.version_map_memory_in_bytes |  | long |
| elasticsearch.index.total.store.size_in_bytes | Total size of the index in bytes. | long |
| elasticsearch.index.uuid |  | keyword |
| elasticsearch.node.id | Node ID | keyword |
| elasticsearch.node.master | Is the node the master node? | boolean |
| elasticsearch.node.mlockall | Is mlockall enabled on the node? | boolean |
| elasticsearch.node.name | Node name. | keyword |

### Index recovery

By default only data about indices which are under active recovery are fetched.
To gather data about all indices set `active_only: false`.

{{event "index_recovery"}}

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| elasticsearch.cluster.id | Elasticsearch cluster id. | keyword |
| elasticsearch.cluster.name | Elasticsearch cluster name. | keyword |
| elasticsearch.cluster.state.id | Elasticsearch state id. | keyword |
| elasticsearch.index.name |  | keyword |
| elasticsearch.index.recovery.id | Shard recovery id. | long |
| elasticsearch.index.recovery.index.files.percent |  | keyword |
| elasticsearch.index.recovery.index.files.recovered |  | long |
| elasticsearch.index.recovery.index.files.reused |  | long |
| elasticsearch.index.recovery.index.files.total |  | long |
| elasticsearch.index.recovery.index.size.recovered_in_bytes |  | long |
| elasticsearch.index.recovery.index.size.reused_in_bytes |  | long |
| elasticsearch.index.recovery.index.size.total_in_bytes |  | long |
| elasticsearch.index.recovery.name |  | keyword |
| elasticsearch.index.recovery.primary | True if primary shard. | boolean |
| elasticsearch.index.recovery.source.host | Source node host address (could be IP address or hostname). | keyword |
| elasticsearch.index.recovery.source.id | Source node id. | keyword |
| elasticsearch.index.recovery.source.name | Source node name. | keyword |
| elasticsearch.index.recovery.source.transport_address |  | keyword |
| elasticsearch.index.recovery.stage | Recovery stage. | keyword |
| elasticsearch.index.recovery.start_time.ms |  | long |
| elasticsearch.index.recovery.stop_time.ms |  | long |
| elasticsearch.index.recovery.target.host | Target node host address (could be IP address or hostname). | keyword |
| elasticsearch.index.recovery.target.id | Target node id. | keyword |
| elasticsearch.index.recovery.target.name | Target node name. | keyword |
| elasticsearch.index.recovery.target.transport_address |  | keyword |
| elasticsearch.index.recovery.total_time.ms |  | long |
| elasticsearch.index.recovery.translog.percent |  | keyword |
| elasticsearch.index.recovery.translog.total |  | long |
| elasticsearch.index.recovery.translog.total_on_start |  | long |
| elasticsearch.index.recovery.type | Shard recovery type. | keyword |
| elasticsearch.index.recovery.verify_index.check_index_time.ms |  | long |
| elasticsearch.index.recovery.verify_index.total_time.ms |  | long |
| elasticsearch.node.id | Node ID | keyword |
| elasticsearch.node.master | Is the node the master node? | boolean |
| elasticsearch.node.mlockall | Is mlockall enabled on the node? | boolean |
| elasticsearch.node.name | Node name. | keyword |
| version |  | long |

### Index summary

{{event "index_summary"}}

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| elasticsearch.cluster.id | Elasticsearch cluster id. | keyword |
| elasticsearch.cluster.name | Elasticsearch cluster name. | keyword |
| elasticsearch.cluster.state.id | Elasticsearch state id. | keyword |
| elasticsearch.index.summary.primaries.bulk.operations.count |  | long |
| elasticsearch.index.summary.primaries.bulk.size.bytes |  | long |
| elasticsearch.index.summary.primaries.bulk.time.avg.bytes |  | long |
| elasticsearch.index.summary.primaries.bulk.time.avg.ms |  | long |
| elasticsearch.index.summary.primaries.bulk.time.count.ms |  | long |
| elasticsearch.index.summary.primaries.docs.count | Total number of documents in the index. | long |
| elasticsearch.index.summary.primaries.docs.deleted | Total number of deleted documents in the index. | long |
| elasticsearch.index.summary.primaries.indexing.index.count |  | long |
| elasticsearch.index.summary.primaries.indexing.index.time.ms |  | long |
| elasticsearch.index.summary.primaries.search.query.count |  | long |
| elasticsearch.index.summary.primaries.search.query.time.ms |  | long |
| elasticsearch.index.summary.primaries.segments.count | Total number of index segments. | long |
| elasticsearch.index.summary.primaries.segments.memory.bytes | Total number of memory used by the segments in bytes. | long |
| elasticsearch.index.summary.primaries.store.size.bytes | Total size of the index in bytes. | long |
| elasticsearch.index.summary.total.bulk.operations.count |  | long |
| elasticsearch.index.summary.total.bulk.size.bytes |  | long |
| elasticsearch.index.summary.total.bulk.time.avg.bytes |  | long |
| elasticsearch.index.summary.total.bulk.time.avg.ms |  | long |
| elasticsearch.index.summary.total.docs.count | Total number of documents in the index. | long |
| elasticsearch.index.summary.total.docs.deleted | Total number of deleted documents in the index. | long |
| elasticsearch.index.summary.total.indexing.index.count |  | long |
| elasticsearch.index.summary.total.indexing.index.time.ms |  | long |
| elasticsearch.index.summary.total.indexing.is_throttled |  | boolean |
| elasticsearch.index.summary.total.indexing.throttle_time.ms |  | long |
| elasticsearch.index.summary.total.search.query.count |  | long |
| elasticsearch.index.summary.total.search.query.time.ms |  | long |
| elasticsearch.index.summary.total.segments.count | Total number of index segments. | long |
| elasticsearch.index.summary.total.segments.memory.bytes | Total number of memory used by the segments in bytes. | long |
| elasticsearch.index.summary.total.store.size.bytes | Total size of the index in bytes. | long |
| elasticsearch.node.id | Node ID | keyword |
| elasticsearch.node.master | Is the node the master node? | boolean |
| elasticsearch.node.mlockall | Is mlockall enabled on the node? | boolean |
| elasticsearch.node.name | Node name. | keyword |

### Machine Learning Jobs

If you have Machine Learning jobs, this data stream will interrogate the 
{{ url "elasticsearch-ml-apis" "Machine Learning Anomaly Detection API" }}
and  requires [Machine Learning](https://www.elastic.co/products/x-pack/machine-learning) to be enabled.

{{event "ml_job"}}

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| elasticsearch.cluster.id | Elasticsearch cluster id. | keyword |
| elasticsearch.cluster.name | Elasticsearch cluster name. | keyword |
| elasticsearch.cluster.state.id | Elasticsearch state id. | keyword |
| elasticsearch.ml.job.data.invalid_date.count | The number of records with either a missing date field or a date that could not be parsed. | long |
| elasticsearch.ml.job.data_counts.invalid_date_count |  | long |
| elasticsearch.ml.job.data_counts.processed_record_count | Processed data events. | long |
| elasticsearch.ml.job.forecasts_stats.total |  | long |
| elasticsearch.ml.job.id | Unique ml job id. | keyword |
| elasticsearch.ml.job.model_size.memory_status |  | keyword |
| elasticsearch.ml.job.state | Job state. | keyword |
| elasticsearch.node.id | Node ID | keyword |
| elasticsearch.node.master | Is the node the master node? | boolean |
| elasticsearch.node.mlockall | Is mlockall enabled on the node? | boolean |
| elasticsearch.node.name | Node name. | keyword |

### Node

`node` interrogates the
{{ url "elasticsearch-cluster-nodes-info" "Cluster API endpoint" }} of
Elasticsearch to get cluster nodes information. It only fetches the data from the `_local` node so it must
run on each Elasticsearch node.

{{event "node"}}

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| elasticsearch.cluster.id | Elasticsearch cluster id. | keyword |
| elasticsearch.cluster.name | Elasticsearch cluster name. | keyword |
| elasticsearch.cluster.state.id | Elasticsearch state id. | keyword |
| elasticsearch.node.id | Node ID | keyword |
| elasticsearch.node.jvm.memory.heap.init.bytes | Heap init used by the JVM in bytes. | long |
| elasticsearch.node.jvm.memory.heap.max.bytes | Heap max used by the JVM in bytes. | long |
| elasticsearch.node.jvm.memory.nonheap.init.bytes | Non-Heap init used by the JVM in bytes. | long |
| elasticsearch.node.jvm.memory.nonheap.max.bytes | Non-Heap max used by the JVM in bytes. | long |
| elasticsearch.node.jvm.version | JVM version. | keyword |
| elasticsearch.node.master | Is the node the master node? | boolean |
| elasticsearch.node.mlockall | Is mlockall enabled on the node? | boolean |
| elasticsearch.node.name | Node name. | keyword |
| elasticsearch.node.process.mlockall | If process locked in memory. | boolean |
| elasticsearch.node.version | Node version. | keyword |

### Node stats

`node_stats` interrogates the
{{ url "elasticsearch-cluster-nodes-stats" "Cluster API endpoint" }} of
Elasticsearch to get the cluster nodes statistics. The data received is only for the local node so the Agent has
to be run on each Elasticsearch node.

NOTE: The indices stats are node-specific. That means for example the total number of docs reported by all nodes together is not the total number of documents in all indices as there can also be replicas.

{{event "node_stats"}}

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| elasticsearch.cluster.id | Elasticsearch cluster id. | keyword |
| elasticsearch.cluster.name | Elasticsearch cluster name. | keyword |
| elasticsearch.cluster.state.id | Elasticsearch state id. | keyword |
| elasticsearch.node.id | Node ID | keyword |
| elasticsearch.node.master | Is the node the master node? | boolean |
| elasticsearch.node.mlockall | Is mlockall enabled on the node? | boolean |
| elasticsearch.node.name | Node name. | keyword |
| elasticsearch.node.stats.fs.io_stats.total.operations.count |  | long |
| elasticsearch.node.stats.fs.io_stats.total.read.operations.count |  | long |
| elasticsearch.node.stats.fs.io_stats.total.write.operations.count |  | long |
| elasticsearch.node.stats.fs.summary.available.bytes |  | long |
| elasticsearch.node.stats.fs.summary.free.bytes |  | long |
| elasticsearch.node.stats.fs.summary.total.bytes |  | long |
| elasticsearch.node.stats.fs.total.available_in_bytes |  | long |
| elasticsearch.node.stats.fs.total.total_in_bytes |  | long |
| elasticsearch.node.stats.indices.docs.count | Total number of existing documents. | long |
| elasticsearch.node.stats.indices.docs.deleted | Total number of deleted documents. | long |
| elasticsearch.node.stats.indices.fielddata.memory.bytes |  | long |
| elasticsearch.node.stats.indices.indexing.index_time.ms |  | long |
| elasticsearch.node.stats.indices.indexing.index_total.count |  | long |
| elasticsearch.node.stats.indices.indexing.throttle_time.ms |  | long |
| elasticsearch.node.stats.indices.query_cache.memory.bytes |  | long |
| elasticsearch.node.stats.indices.request_cache.memory.bytes |  | long |
| elasticsearch.node.stats.indices.search.query_time.ms |  | long |
| elasticsearch.node.stats.indices.search.query_total.count |  | long |
| elasticsearch.node.stats.indices.segments.count | Total number of segments. | long |
| elasticsearch.node.stats.indices.segments.doc_values.memory.bytes |  | long |
| elasticsearch.node.stats.indices.segments.fixed_bit_set.memory.bytes |  | long |
| elasticsearch.node.stats.indices.segments.index_writer.memory.bytes |  | long |
| elasticsearch.node.stats.indices.segments.memory.bytes | Total size of segments in bytes. | long |
| elasticsearch.node.stats.indices.segments.norms.memory.bytes |  | long |
| elasticsearch.node.stats.indices.segments.points.memory.bytes |  | long |
| elasticsearch.node.stats.indices.segments.stored_fields.memory.bytes |  | long |
| elasticsearch.node.stats.indices.segments.term_vectors.memory.bytes |  | long |
| elasticsearch.node.stats.indices.segments.terms.memory.bytes |  | long |
| elasticsearch.node.stats.indices.segments.version_map.memory.bytes |  | long |
| elasticsearch.node.stats.indices.store.size.bytes | Total size of the store in bytes. | long |
| elasticsearch.node.stats.jvm.gc.collectors.old.collection.count |  | long |
| elasticsearch.node.stats.jvm.gc.collectors.old.collection.ms |  | long |
| elasticsearch.node.stats.jvm.gc.collectors.young.collection.count |  | long |
| elasticsearch.node.stats.jvm.gc.collectors.young.collection.ms |  | long |
| elasticsearch.node.stats.jvm.mem.heap.max.bytes |  | long |
| elasticsearch.node.stats.jvm.mem.heap.used.bytes |  | long |
| elasticsearch.node.stats.jvm.mem.heap.used.pct |  | double |
| elasticsearch.node.stats.jvm.mem.pools.old.max.bytes | Max bytes. | long |
| elasticsearch.node.stats.jvm.mem.pools.old.peak.bytes | Peak bytes. | long |
| elasticsearch.node.stats.jvm.mem.pools.old.peak_max.bytes | Peak max bytes. | long |
| elasticsearch.node.stats.jvm.mem.pools.old.used.bytes | Used bytes. | long |
| elasticsearch.node.stats.jvm.mem.pools.survivor.max.bytes | Max bytes. | long |
| elasticsearch.node.stats.jvm.mem.pools.survivor.peak.bytes | Peak bytes. | long |
| elasticsearch.node.stats.jvm.mem.pools.survivor.peak_max.bytes | Peak max bytes. | long |
| elasticsearch.node.stats.jvm.mem.pools.survivor.used.bytes | Used bytes. | long |
| elasticsearch.node.stats.jvm.mem.pools.young.max.bytes | Max bytes. | long |
| elasticsearch.node.stats.jvm.mem.pools.young.peak.bytes | Peak bytes. | long |
| elasticsearch.node.stats.jvm.mem.pools.young.peak_max.bytes | Peak max bytes. | long |
| elasticsearch.node.stats.jvm.mem.pools.young.used.bytes | Used bytes. | long |
| elasticsearch.node.stats.os.cgroup.cpu.cfs.quota.us |  | long |
| elasticsearch.node.stats.os.cgroup.cpu.stat.elapsed_periods.count |  | long |
| elasticsearch.node.stats.os.cgroup.cpu.stat.time_throttled.ns |  | long |
| elasticsearch.node.stats.os.cgroup.cpu.stat.times_throttled.count |  | long |
| elasticsearch.node.stats.os.cgroup.cpuacct.usage.ns |  | long |
| elasticsearch.node.stats.os.cgroup.memory.control_group |  | keyword |
| elasticsearch.node.stats.os.cgroup.memory.limit.bytes |  | long |
| elasticsearch.node.stats.os.cgroup.memory.usage.bytes |  | long |
| elasticsearch.node.stats.os.cpu.load_avg.1m |  | half_float |
| elasticsearch.node.stats.process.cpu.pct |  | double |
| elasticsearch.node.stats.thread_pool.bulk.queue.count |  | long |
| elasticsearch.node.stats.thread_pool.bulk.rejected.count |  | long |
| elasticsearch.node.stats.thread_pool.get.queue.count |  | long |
| elasticsearch.node.stats.thread_pool.get.rejected.count |  | long |
| elasticsearch.node.stats.thread_pool.index.queue.count |  | long |
| elasticsearch.node.stats.thread_pool.index.rejected.count |  | long |
| elasticsearch.node.stats.thread_pool.search.queue.count |  | long |
| elasticsearch.node.stats.thread_pool.search.rejected.count |  | long |
| elasticsearch.node.stats.thread_pool.write.queue.count |  | long |
| elasticsearch.node.stats.thread_pool.write.rejected.count |  | long |

### Pending tasks

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| elasticsearch.cluster.id | Elasticsearch cluster id. | keyword |
| elasticsearch.cluster.name | Elasticsearch cluster name. | keyword |
| elasticsearch.cluster.pending_task.insert_order | Insert order | long |
| elasticsearch.cluster.pending_task.priority | Priority | keyword |
| elasticsearch.cluster.pending_task.source | Source. For example: put-mapping | keyword |
| elasticsearch.cluster.pending_task.time_in_queue.ms | Time in queue | long |
| elasticsearch.cluster.state.id | Elasticsearch state id. | keyword |
| elasticsearch.node.id | Node ID | keyword |
| elasticsearch.node.master | Is the node the master node? | boolean |
| elasticsearch.node.mlockall | Is mlockall enabled on the node? | boolean |
| elasticsearch.node.name | Node name. | keyword |

# Shard

`shard` interrogates the
{{ url "elasticsearch-cluster-state-6.2" "Cluster State API endpoint" }} to fetch
information about all shards.

{{event "shard"}}

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| elasticsearch.cluster.id | Elasticsearch cluster id. | keyword |
| elasticsearch.cluster.name | Elasticsearch cluster name. | keyword |
| elasticsearch.cluster.state.id | Elasticsearch state id. | keyword |
| elasticsearch.index.name |  | keyword |
| elasticsearch.node.id | Node ID | keyword |
| elasticsearch.node.master | Is the node the master node? | boolean |
| elasticsearch.node.mlockall | Is mlockall enabled on the node? | boolean |
| elasticsearch.node.name | Node name. | keyword |
| elasticsearch.shard.number | The number of this shard. | long |
| elasticsearch.shard.primary | True if this is the primary shard. | boolean |
| elasticsearch.shard.relocating_node.id | The node the shard was relocated from. It has the exact same value than relocating_node.name for compatibility purposes. | keyword |
| elasticsearch.shard.relocating_node.name | The node the shard was relocated from. | keyword |
| elasticsearch.shard.source_node.name |  | keyword |
| elasticsearch.shard.source_node.uuid |  | keyword |
| elasticsearch.shard.state | The state of this shard. | keyword |
