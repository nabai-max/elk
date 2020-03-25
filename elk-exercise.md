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

repeat ... next command ... etc
