# CISC 525 Module 10 Output of Exercise #5.

You must provide this output as a part of your homework assignment.
You must share this repository with me
For each command you run on Kibana's web console, make sure to provide the input and output of the
command as follows:

## Kibana Console

- command input: Checking the cluster health.

```http

GET /_cluster/health
```
- command output

```json

{
  "cluster_name" : "elasticsearch",
  "status" : "yellow",
  "timed_out" : false,
  "number_of_nodes" : 1,
  "number_of_data_nodes" : 1,
  "active_primary_shards" : 5,
  "active_shards" : 5,
  "relocating_shards" : 0,
  "initializing_shards" : 0,
  "unassigned_shards" : 4,
  "delayed_unassigned_shards" : 0,
  "number_of_pending_tasks" : 0,
  "number_of_in_flight_fetch" : 0,
  "task_max_waiting_in_queue_millis" : 0,
  "active_shards_percent_as_number" : 55.55555555555556
}
```

- alternative curl:
  
```bash

curl -XGET "http://localhost:9200/_cluster/health"
```

- command input: Listing the cluster's nodes.

```http

GET /_cat/nodes?v
```
- command output

```json

ip        heap.percent ram.percent cpu load_1m load_5m load_15m node.role master name
127.0.0.1           31          97   2    0.16    0.09     0.12 dilm      *      student-VirtualBox
```

- alternative curl:
  
```bash

curl -XGET "http://localhost:9200/_cat/indices?v"

```
- command input: Listing the cluster's indicess.

```http

GET /_cat/indices?v
```
- command output

```json

health status index                    uuid                   pri rep docs.count docs.deleted store.size pri.store.size
green  open   .kibana_task_manager_1   9D3oQE8zQ2-q0qM4XCMITg   1   0          2            1     26.9kb         26.9kb
green  open   .apm-agent-configuration DvPDzd-uRPWLOWR-FlVKbQ   1   0          0            0       283b           283b
green  open   .kibana_1                Tye9xrNRSNufstAaXD6HeA   1   0         22            1     20.3kb         20.3kb
yellow open   products                 6wNSB1ljTIaqNlnmtdQQkg   2   2          3            0      8.4kb          8.4kb
```

- alternative curl:
  
```bash

curl -XGET "http://localhost:9200/_cat/indices?v"

```


- command input: Updating a document

```http

POST /products/_doc
{
  "name": "Coffee Maker",
  "price": 64,
  "in_stock": 10
}
```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "IOUvEXEBqQw-X1IjiYSN",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 2
}
```

- curl command:

```bash

curl -XPOST "http://localhost:9200/products/_doc" -H 'Content-Type: application/json' -d'{  "name": "Coffee Maker",  "price": 64,  "in_stock": 10}'
```
- command input: Updating a document

```http

POST /products/_doc
{
  "name": "Coffee Maker",
  "price": 64,
  "in_stock": 10
}
```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "IOUvEXEBqQw-X1IjiYSN",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 2
}
```

- curl command:

```bash

curl -XPOST "http://localhost:9200/products/_doc" -H 'Content-Type: application/json' -d'{  "name": "Coffee Maker",  "price": 64,  "in_stock": 10}'
```
