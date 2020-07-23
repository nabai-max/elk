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
- command input: Listing the cluster's indices.

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
- command input: Test search query.

```http

GET /.kibana/_search
{
  "query": {
    "match_all":{}
  }
}
```
- command output

```json

{
  "took" : 1,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 22,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "space:default",
        "_score" : 1.0,
        "_source" : {
          "space" : {
            "name" : "Default",
            "description" : "This is your default space!",
            "color" : "#00bfb3",
            "disabledFeatures" : [ ],
            "_reserved" : true
          },
          "type" : "space",
          "references" : [ ],
          "migrationVersion" : {
            "space" : "6.6.0"
          },
          "updated_at" : "2020-03-21T11:56:30.286Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "config:7.6.1",
        "_score" : 1.0,
        "_source" : {
          "config" : {
            "buildNum" : 29118
          },
          "type" : "config",
          "references" : [ ],
          "updated_at" : "2020-03-21T11:56:40.954Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "telemetry:telemetry",
        "_score" : 1.0,
        "_source" : {
          "telemetry" : {
            "userHasSeenNotice" : true
          },
          "type" : "telemetry",
          "references" : [ ],
          "updated_at" : "2020-03-21T11:56:59.847Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:Kibana_home:sampleDataConfirm",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 1
          },
          "type" : "ui-metric",
          "updated_at" : "2020-03-21T12:31:48.378Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "maps-telemetry:maps-telemetry",
        "_score" : 1.0,
        "_source" : {
          "maps-telemetry" : {
            "settings" : {
              "showMapVisualizationTypes" : false
            },
            "indexPatternsWithGeoFieldCount" : 0,
            "mapsTotalCount" : 0,
            "timeCaptured" : "2020-07-23T19:27:40.277Z",
            "attributesPerMap" : {
              "dataSourcesCount" : {
                "min" : 0,
                "max" : 0,
                "avg" : 0
              },
              "layersCount" : {
                "min" : 0,
                "max" : 0,
                "avg" : 0
              },
              "layerTypesCount" : { },
              "emsVectorLayersCount" : { }
            }
          },
          "type" : "maps-telemetry",
          "references" : [ ],
          "updated_at" : "2020-07-23T19:27:40.277Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:kibana-user_agent:Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 1
          },
          "type" : "ui-metric",
          "references" : [ ],
          "updated_at" : "2020-07-23T19:28:05.999Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:Kibana_home:welcomeScreenMount",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 3
          },
          "type" : "ui-metric",
          "updated_at" : "2020-07-23T19:28:05.999Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:Kibana_home:sampleDataDecline",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 2
          },
          "type" : "ui-metric",
          "updated_at" : "2020-07-23T19:28:05.999Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:console:DELETE_indices.delete",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 5
          },
          "type" : "ui-metric",
          "updated_at" : "2020-07-23T19:44:39.220Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:console:GET_cluster.health",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 10
          },
          "type" : "ui-metric",
          "updated_at" : "2020-07-23T19:44:39.220Z"
        }
      }
    ]
  }
}

```

- alternative curl:
  
```bash

curl -XGET "http://localhost:9200/.kibana/_search" -H 'Content-Type: application/json' -d'{  "query": {    "match_all":{}  }}'

```
- command input: Creating Index

```http

PUT /pages

```

- command output:

```json
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "pages"
}
```

- curl command:

```bash

curl -XPUT "http://localhost:9200/pages"
```

- command input: Deleting Index

```http

DELETE /pages

```

- command output:

```json
{
  "acknowledged" : true
}

```

- curl command:

```bash

curl -XDELETE "http://localhost:9200/pages"
```
- command input: Creating Index with setting

```http

PUT /products
{
  "settings": {
    "number_of_shards": 2,
    "number_of_replicas": 2
  }
}

```

- command output:

```json
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "products"
}

```

- curl command:

```bash
curl -XPUT "http://localhost:9200/products" -H 'Content-Type: application/json' -d'{  "settings": {    "number_of_shards": 2,    "number_of_replicas": 2  }}'
```
- command input: Indexing document with auto generated id

```http

POST /products/_doc
{
  "name":"Coffee Mkaer",
  "price":64,
  "in_stock":10
}

```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "ogVmfXMBBCvWdakeoGVb",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}

```

- curl command:

```bash
curl -XPOST "http://localhost:9200/products/_doc" -H 'Content-Type: application/json' -d'{  "name":"Coffee Mkaer",  "price":64,  "in_stock":10}'
```

- command input: Indexing document with customer id

```http

POST /products/_doc/100
{
  "name":"Toaster",
  "price":49,
  "in_stock":4
}

```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}


```

- curl command:

```bash
curl -XPOST "http://localhost:9200/products/_doc/100" -H 'Content-Type: application/json' -d'{  "name":"Toaster",  "price":49,  "in_stock":4}'
```

- command input: Retrieving documents by ID

```http

GET /products/_doc/100

```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 1,
  "_seq_no" : 0,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "name" : "Toaster",
    "price" : 49,
    "in_stock" : 4
  }
}
```

- curl command:

```bash
curl -XGET "http://localhost:9200/products/_doc/100"
```

- command input: Updating a document

```http

POST /products/_update/100
{
  "doc": {
    "in_stock":3 
  }
}
```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 2,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 1,
  "_primary_term" : 1
}
```

- curl command:

```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "doc": {    "in_stock":3    }}'
```
- command input: Scripted update (reducing the current value of in_stock by one)

```http

POST /products/_update/100
{
  "script": {
    "source":"ctx._source.in_stock--" 
  }
}
```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 3,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 2,
  "_primary_term" : 1
}
```

- curl command:

```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source":"ctx._source.in_stock--"   }}'
```

- command input: Scripted update (assigning an arbitrary value to of in_stock)

```http

POST /products/_update/100
{
  "script": {
    "source":"ctx._source.in_stock = 10" 
  }
}

```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 4,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 3,
  "_primary_term" : 1
}
```

- curl command:

```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source":"ctx._source.in_stock = 10"   }}'
```

- command input: Using parameters within scripts

```http

POST /products/_update/100
{
  "script": {
    "source":"ctx._source.in_stock -= params.quantity",
    "params": {
      "quantity": 4
    }
  }
}

```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 5,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 4,
  "_primary_term" : 1
}
```

- curl command:

```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source":"ctx._source.in_stock -= params.quantity",    "params": {      "quantity": 4    }  }}'
```

- command input: conditionally setting the operation to noop

```http

POST /products/_update/100
{
  "script": {
    "source":"""
    if (ctx._source.in_stock ==0) {
      ctx.op = 'noop';
    }
    
    ctx._source.in_stock--;
    """
  }
}

```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 6,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 5,
  "_primary_term" : 1
}
```

- curl command:

```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source":"\n    if (ctx._source.in_stock ==0) {\n      ctx.op = \"noop\";\n    }\n    \n    ctx._source.in_stock--;\n    "  }}'
```
- command input: conditionally update the field value

```http

POST /products/_update/100
{
  "script": {
    "source":"""
    if (ctx._source.in_stock >0) {
    ctx._source.in_stock--;
  }
  """
  }
}

```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 7,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 6,
  "_primary_term" : 1
}
```

- curl command:

```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source":"\n    if (ctx._source.in_stock >0) {\n    ctx._source.in_stock--;\n  }\n  "  }}'
```

- command input: conditionally delete a document

```http

POST /products/_update/100
{
  "script": {
    "source":"""
    if (ctx._source.in_stock <0) {
      ctx.op = 'delete';
    }
    
    ctx._source.in_stock--;
    """
  }
}

```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 8,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 7,
  "_primary_term" : 1
}

```

- curl command:

```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source":"\n    if (ctx._source.in_stock <0) {\n      ctx.op = \"delete\";\n    }\n    \n    ctx._source.in_stock--;\n    "  }}'

```

- command input: Upserts

```http

POST /products/_update/101
{
  "script": {
    "source": "SCRIPT"
  },
  "upsert":{
    "name": "Blender",
    "price": 399,
    "in_Stock": 5
  }
}

```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "101",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 8,
  "_primary_term" : 1
}
```

- curl command:

```bash
curl -XPOST "http://localhost:9200/products/_update/101" -H 'Content-Type: application/json' -d'{  "script": {    "source": "SCRIPT"  },  "upsert":{    "name": "Blender",    "price": 399,    "in_Stock": 5  }}'
```

- command input: Replacing Document

```http

PUT /products/_doc/100
{
  "name": "Toaster",
  "price": 79,
  "in_Stock": 4
}

```

- command output:

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 9,
  "result" : "updated",
  "_shards" : {
    "total" : 3,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 9,
  "_primary_term" : 1
}

```

- curl command:

```bash

curl -XPUT "http://localhost:9200/products/_doc/100" -H 'Content-Type: application/json' -d'{  "name": "Toaster",  "price": 79,  "in_Stock": 4}'
```










