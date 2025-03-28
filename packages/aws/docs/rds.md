# Amazon RDS

The Amazon RDS integration allows you to monitor [Amazon Relational Database Service (Amazon RDS)](https://aws.amazon.com/rds)—a collection of cloud database services.

Use the Amazon RDS integration to collect metrics related to your Amazon databases. Then visualize that data in Kibana, create alerts to notify you if something goes wrong, and reference the metrics when troubleshooting an issue.

For example, you could use this integration to track the latency and throughput on your databases. Then create an alert that posts a message in Slack if your write latency spikes.

**IMPORTANT: Extra AWS charges on API requests will be generated by this integration. Check [API Requests](https://www.elastic.co/docs/current/integrations/aws#api-requests) for more details.**

## Data streams

The Amazon RDS integration collects one type of data: metrics.

**Metrics** give you insight into the state of Amazon RDS.
Metrics collected by the Amazon RDS integration include database dimensions, the lag between database instances, and more. See more details in the [Metrics reference](#metrics-reference).

## Requirements

You need Elasticsearch for storing and searching your data and Kibana for visualizing and managing it.
You can use our hosted Elasticsearch Service on Elastic Cloud, which is recommended, or self-manage the Elastic Stack on your own hardware.

Before using any AWS integration you will need:

* **AWS Credentials** to connect with your AWS account.
* **AWS Permissions** to make sure the user you're using to connect has permission to share the relevant data.

For more details about these requirements, please take a look at the [AWS integration documentation](https://docs.elastic.co/integrations/aws#requirements).

## Setup

Use this integration if you only need to collect data from the Amazon RDS service.

If you want to collect data from two or more AWS services, consider using the **AWS** integration.
When you configure the AWS integration, you can collect data from as many AWS services as you'd like.

For step-by-step instructions on how to set up an integration, see the
[Getting started](https://www.elastic.co/guide/en/starting-with-the-elasticsearch-platform-and-its-solutions/current/getting-started-observability.html) guide.

## Metrics reference

An example event for `rds` looks as following:

```json
{
    "@timestamp": "2022-06-03T15:28:00.000Z",
    "agent": {
        "ephemeral_id": "c4161c81-1e2e-4e8b-a0be-15940cc13226",
        "id": "90bfb41e-b925-420f-973e-9c1115297278",
        "name": "docker-fleet-agent",
        "type": "metricbeat",
        "version": "8.2.0"
    },
    "aws": {
        "cloudwatch": {
            "namespace": "AWS/RDS"
        },
        "dimensions": {
            "DatabaseClass": "db.r5.large"
        },
        "rds": {
            "aurora_bin_log_replica_lag": 0,
            "aurora_replica": {
                "lag": {
                    "ms": 19.47
                },
                "lag_max": {
                    "ms": 19.469999313354492
                },
                "lag_min": {
                    "ms": 19.469999313354492
                }
            },
            "aurora_volume_left_total": {
                "bytes": 70007366615040
            },
            "cache_hit_ratio": {
                "buffer": 100,
                "result_set": 0
            },
            "database_connections": 0,
            "deadlocks": 0,
            "engine_uptime": {
                "sec": 53016926.5
            },
            "free_local_storage": {
                "bytes": 28622428160
            },
            "freeable_memory": {
                "bytes": 4705378304
            },
            "latency": {
                "commit": 3.536983333333333,
                "ddl": 0,
                "delete": 0,
                "dml": 0.09705000000000001,
                "insert": 0.09705000000000001,
                "read": 0,
                "select": 0.2412933510638298,
                "update": 0,
                "write": 0.0006218917818574514
            },
            "login_failures": 0,
            "metrics": {
                "AbortedClients": {
                    "avg": 0
                },
                "Aurora_pq_request_attempted": {
                    "avg": 0
                },
                "Aurora_pq_request_executed": {
                    "avg": 0
                },
                "Aurora_pq_request_failed": {
                    "avg": 0
                },
                "Aurora_pq_request_in_progress": {
                    "avg": 0
                },
                "Aurora_pq_request_not_chosen": {
                    "avg": 0
                },
                "Aurora_pq_request_not_chosen_below_min_rows": {
                    "avg": 0
                },
                "Aurora_pq_request_not_chosen_few_pages_outside_buffer_pool": {
                    "avg": 0
                },
                "Aurora_pq_request_not_chosen_long_trx": {
                    "avg": 0
                },
                "Aurora_pq_request_not_chosen_pq_high_buffer_pool_pct": {
                    "avg": 0
                },
                "Aurora_pq_request_not_chosen_small_table": {
                    "avg": 0
                },
                "Aurora_pq_request_not_chosen_unsupported_access": {
                    "avg": 0
                },
                "Aurora_pq_request_throttled": {
                    "avg": 0
                },
                "ConnectionAttempts": {
                    "avg": 0
                },
                "NumBinaryLogFiles": {
                    "avg": 0
                },
                "RollbackSegmentHistoryListLength": {
                    "avg": 53
                },
                "RowLockTime": {
                    "avg": 0
                },
                "StorageNetworkReceiveThroughput": {
                    "avg": 7104.272100353031
                },
                "StorageNetworkThroughput": {
                    "avg": 22950.537520958267
                },
                "StorageNetworkTransmitThroughput": {
                    "avg": 15846.26542060524
                },
                "SumBinaryLogSize": {
                    "avg": 0
                }
            },
            "queries": 7.737700770575286,
            "swap_usage": {
                "bytes": 0
            },
            "throughput": {
                "commit": 0.2500125006250313,
                "ddl": 0,
                "delete": 0,
                "dml": 0.2500125006250313,
                "insert": 0.2500125006250313,
                "network": 1.404177703397091,
                "network_receive": 0.7020888516985455,
                "network_transmit": 0.7020888516985455,
                "select": 2.9051419389878808,
                "update": 0
            },
            "transactions": {
                "active": 0,
                "blocked": 0
            }
        }
    },
    "cloud": {
        "account": {
            "id": "123456789",
            "name": "elastic-beats"
        },
        "provider": "aws",
        "region": "eu-west-1"
    },
    "data_stream": {
        "dataset": "aws.rds",
        "namespace": "default",
        "type": "metrics"
    },
    "ecs": {
        "version": "8.11.0"
    },
    "elastic_agent": {
        "id": "90bfb41e-b925-420f-973e-9c1115297278",
        "snapshot": false,
        "version": "8.2.0"
    },
    "event": {
        "agent_id_status": "verified",
        "dataset": "aws.rds",
        "duration": 12570787900,
        "ingested": "2022-06-03T15:28:44Z",
        "module": "aws"
    },
    "metricset": {
        "name": "cloudwatch",
        "period": 60000
    },
    "service": {
        "type": "aws"
    }
}
```

**ECS Field Reference**

Please refer to the following [document](https://www.elastic.co/guide/en/ecs/current/ecs-field-reference.html) for detailed information on ECS fields.

**Exported fields**

| Field | Description | Type | Metric Type |
|---|---|---|---|
| @timestamp | Event timestamp. | date |  |
| agent.id | Unique identifier of this agent (if one exists). Example: For Beats this would be beat.id. | keyword |  |
| aws.cloudwatch.namespace | The namespace specified when query cloudwatch api. | keyword |  |
| aws.dimensions.DBClusterIdentifier | This dimension filters the data that you request for a specific Amazon Aurora DB cluster. | keyword |  |
| aws.dimensions.DBInstanceIdentifier | This dimension filters the data that you request for a specific DB instance. | keyword |  |
| aws.dimensions.DatabaseClass | This dimension filters the data that you request for all instances in a database class. | keyword |  |
| aws.dimensions.EngineName | This dimension filters the data that you request for the identified engine name only. | keyword |  |
| aws.dimensions.Role | This dimension filters the data that you request by instance role (WRITER/READER). | keyword |  |
| aws.dimensions.SourceRegion | This dimension filters the data that you request for the specified region only. | keyword |  |
| aws.metrics_names_fingerprint | Autogenerated ID representing the fingerprint of the list of metrics names.  Applicable only for [Amazon Data Firehose integration](https://www.elastic.co/docs/current/integrations/awsfirehose). | keyword |  |
| aws.rds.aurora_bin_log_replica_lag | The amount of time a replica DB cluster running on Aurora with MySQL compatibility lags behind the source DB cluster. | long | gauge |
| aws.rds.aurora_global_db.data_transfer.bytes | In an Aurora Global Database, the amount of redo log data transferred from the master AWS Region to a secondary AWS Region. | long | gauge |
| aws.rds.aurora_global_db.replicated_write_io.bytes | In an Aurora Global Database, the number of write I/O operations replicated from the primary AWS Region to the cluster volume in a secondary AWS Region. | long | gauge |
| aws.rds.aurora_global_db.replication_lag.ms | For an Aurora Global Database, the amount of lag when replicating updates from the primary AWS Region, in milliseconds. | long | gauge |
| aws.rds.aurora_replica.lag.ms | For an Aurora Replica, the amount of lag when replicating updates from the primary instance, in milliseconds. | long | gauge |
| aws.rds.aurora_replica.lag_max.ms | The maximum amount of lag between the primary instance and each Aurora DB instance in the DB cluster, in milliseconds. | long | gauge |
| aws.rds.aurora_replica.lag_min.ms | The minimum amount of lag between the primary instance and each Aurora DB instance in the DB cluster, in milliseconds. | long | gauge |
| aws.rds.aurora_volume_left_total.bytes | The remaining available space for the cluster volume, measured in bytes. | long | gauge |
| aws.rds.backtrack_change_records.creation_rate | The number of backtrack change records created over five minutes for your DB cluster. | long | gauge |
| aws.rds.backtrack_change_records.stored | The actual number of backtrack change records used by your DB cluster. | long | gauge |
| aws.rds.backtrack_window.actual | The difference between the target backtrack window and the actual backtrack window. | long | gauge |
| aws.rds.backtrack_window.alert | The number of times that the actual backtrack window is smaller than the target backtrack window for a given period of time. | long | gauge |
| aws.rds.backup_storage_billed_total.bytes | The total amount of backup storage in bytes for which you are billed for a given Aurora DB cluster. | long | gauge |
| aws.rds.cache_hit_ratio.buffer | The percentage of requests that are served by the buffer cache. | long | gauge |
| aws.rds.cache_hit_ratio.result_set | The percentage of requests that are served by the Resultset cache. | long | gauge |
| aws.rds.cpu.credit_balance | The number of earned CPU credits that an instance has accrued since it was launched or started. | long | gauge |
| aws.rds.cpu.credit_usage | The number of CPU credits spent by the instance for CPU utilization. | long | gauge |
| aws.rds.cpu.total.pct | The percentage of CPU utilization. | scaled_float | gauge |
| aws.rds.database_connections | The number of database connections in use. | long | gauge |
| aws.rds.db_instance.arn | Amazon Resource Name(ARN) for each rds. | keyword |  |
| aws.rds.db_instance.class | Contains the name of the compute and memory capacity class of the DB instance. | keyword |  |
| aws.rds.db_instance.db_cluster_identifier | This identifier is the unique key that identifies a DB cluster specifically for Amazon Aurora DB cluster. | keyword |  |
| aws.rds.db_instance.engine_name | Each DB instance runs a DB engine, like MySQL, MariaDB, PostgreSQL and etc. | keyword |  |
| aws.rds.db_instance.identifier | Contains a user-supplied database identifier. This identifier is the unique key that identifies a DB instance. | keyword |  |
| aws.rds.db_instance.role | DB roles like WRITER or READER, specifically for Amazon Aurora DB cluster. | keyword |  |
| aws.rds.db_instance.status | Specifies the current state of this database. | keyword |  |
| aws.rds.deadlocks | The average number of deadlocks in the database per second. | long | gauge |
| aws.rds.disk_queue_depth | The number of outstanding IOs (read/write requests) waiting to access the disk. | float | gauge |
| aws.rds.disk_usage.bin_log.bytes | The amount of disk space occupied by binary logs on the master. Applies to MySQL read replicas. | long | gauge |
| aws.rds.disk_usage.replication_slot.mb | The disk space used by replication slot files. Applies to PostgreSQL. | long | gauge |
| aws.rds.disk_usage.transaction_logs.mb | The disk space used by transaction logs. Applies to PostgreSQL. | long | gauge |
| aws.rds.engine_uptime.sec | The amount of time that the instance has been running, in seconds. | long | counter |
| aws.rds.failed_sql_server_agent_jobs | The number of failed SQL Server Agent jobs during the last minute. | long | gauge |
| aws.rds.free_local_storage.bytes | The amount of storage available for temporary tables and logs, in bytes. | long | gauge |
| aws.rds.free_storage.bytes | The amount of available storage space. | long | gauge |
| aws.rds.freeable_memory.bytes | The amount of available random access memory. | long | gauge |
| aws.rds.latency.commit | The amount of latency for commit operations, in milliseconds. | float | gauge |
| aws.rds.latency.ddl | The amount of latency for data definition language (DDL) requests, in milliseconds. | float | gauge |
| aws.rds.latency.delete | The amount of latency for delete queries, in milliseconds. | float | gauge |
| aws.rds.latency.dml | The amount of latency for inserts, updates, and deletes, in milliseconds. | float | gauge |
| aws.rds.latency.insert | The amount of latency for insert queries, in milliseconds. | float | gauge |
| aws.rds.latency.read | The average amount of time taken per disk I/O operation. | float | gauge |
| aws.rds.latency.select | The amount of latency for select queries, in milliseconds. | float | gauge |
| aws.rds.latency.update | The amount of latency for update queries, in milliseconds. | float | gauge |
| aws.rds.latency.write | The average amount of time taken per disk I/O operation. | float | gauge |
| aws.rds.login_failures | The average number of failed login attempts per second. | long | gauge |
| aws.rds.maximum_used_transaction_ids | The maximum transaction ID that has been used. Applies to PostgreSQL. | long | counter |
| aws.rds.metrics.\*.\* | Metrics that returned from Cloudwatch API query. | double |  |
| aws.rds.oldest_replication_slot_lag.mb | The lagging size of the replica lagging the most in terms of WAL data received. Applies to PostgreSQL. | long | gauge |
| aws.rds.queries | The average number of queries executed per second. | long | gauge |
| aws.rds.rds_to_aurora_postgresql_replica_lag.sec | The amount of lag in seconds when replicating updates from the primary RDS PostgreSQL instance to other nodes in the cluster. | long | gauge |
| aws.rds.read_io.ops_per_sec | The average number of disk read I/O operations per second. | float | gauge |
| aws.rds.replica_lag.sec | The amount of time a Read Replica DB instance lags behind the source DB instance. Applies to MySQL, MariaDB, and PostgreSQL Read Replicas. | long | gauge |
| aws.rds.storage_used.backup_retention_period.bytes | The total amount of backup storage in bytes used to support the point-in-time restore feature within the Aurora DB cluster's backup retention window. | long | gauge |
| aws.rds.storage_used.snapshot.bytes | The total amount of backup storage in bytes consumed by all Aurora snapshots for an Aurora DB cluster outside its backup retention window. | long | gauge |
| aws.rds.swap_usage.bytes | The amount of swap space used on the DB instance. This metric is not available for SQL Server. | long | gauge |
| aws.rds.throughput.commit | The average number of commit operations per second. | float | gauge |
| aws.rds.throughput.ddl | The average number of DDL requests per second. | float | gauge |
| aws.rds.throughput.delete | The average number of delete queries per second. | float | gauge |
| aws.rds.throughput.dml | The average number of inserts, updates, and deletes per second. | float | gauge |
| aws.rds.throughput.insert | The average number of insert queries per second. | float | gauge |
| aws.rds.throughput.network | The amount of network throughput both received from and transmitted to clients by each instance in the Aurora MySQL DB cluster, in bytes per second. | float | gauge |
| aws.rds.throughput.network_receive | The incoming (Receive) network traffic on the DB instance, including both customer database traffic and Amazon RDS traffic used for monitoring and replication. | float | gauge |
| aws.rds.throughput.network_transmit | The outgoing (Transmit) network traffic on the DB instance, including both customer database traffic and Amazon RDS traffic used for monitoring and replication. | float | gauge |
| aws.rds.throughput.read | The average amount of time taken per disk I/O operation. | float | gauge |
| aws.rds.throughput.select | The average number of select queries per second. | float | gauge |
| aws.rds.throughput.update | The average number of update queries per second. | float | gauge |
| aws.rds.throughput.write | The average number of bytes written to disk per second. | float | gauge |
| aws.rds.transaction_logs_generation | The disk space used by transaction logs. Applies to PostgreSQL. | long | gauge |
| aws.rds.transactions.active | The average number of current transactions executing on an Aurora database instance per second. | long | gauge |
| aws.rds.transactions.blocked | The average number of transactions in the database that are blocked per second. | long | gauge |
| aws.rds.volume.read.iops | The number of billed read I/O operations from a cluster volume, reported at 5-minute intervals. | long | gauge |
| aws.rds.volume.write.iops | The number of write disk I/O operations to the cluster volume, reported at 5-minute intervals. | long | gauge |
| aws.rds.volume_used.bytes | The amount of storage used by your Aurora DB instance, in bytes. | long | gauge |
| aws.rds.write_io.ops_per_sec | The average number of disk write I/O operations per second. | float | gauge |
| aws.tags | Tag key value pairs from aws resources. | flattened |  |
| cloud.account.id | The cloud account or organization id used to identify different entities in a multi-tenant environment. Examples: AWS account id, Google Cloud ORG Id, or other unique identifier. | keyword |  |
| cloud.image.id | Image ID for the cloud instance. | keyword |  |
| cloud.region | Region in which this host, resource, or service is located. | keyword |  |
| data_stream.dataset | Data stream dataset. | constant_keyword |  |
| data_stream.namespace | Data stream namespace. | constant_keyword |  |
| data_stream.type | Data stream type. | constant_keyword |  |
| event.module | Event module | constant_keyword |  |
| host.containerized | If the host is a container. | boolean |  |
| host.os.build | OS build information. | keyword |  |
| host.os.codename | OS codename, if any. | keyword |  |
