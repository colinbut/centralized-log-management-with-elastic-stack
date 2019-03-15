# Setup Elastic Stack

## Preface

This project of mines demonstrates how to setup and configure the Elastic Stack for a project. Note that I'm only going to showcase the most minimalistic options of configurations. 

elastic.co has in-depth tutorial & guides as part of their documentation along with reference examples shipped with each of their products to help you do the most advanced setup.

## The Elastic Stack

What is the elastic stack? The Elastic Stack is the new name for the list of products offered by elastic.co

Previously this was commonly known as the ELK Stack (because it ONLY contained ElasticSearch-Logstash-Kibana). But now it has outgrown that to contain more software products most noticeably Beats (which consist of many individual components), APM (Application Performance Monitoring), Elastic on the Cloud offering and a few more. 

The rationale behind calling it the Elastic Stack is simply because their stack has now many products and not just ElasticSearch, Logstash, and Kibana.

## Stack overview

Here's a brief overview of what each product of the stack does. I'm probably not going to do it justice myself or I might be a tad incorrect so please head over to elastic.co official site to get an explanation of what each product is.

| Product | Description |
| Elasticsearch | A highly available Search Engine |
| Logstash | |
| Kibana | A visualization tool that views the elasticsearch's data |
| Filebeat | A lightweight log shipper |
| Metricbeat | A lightweight metric data shipper |

## Setup

### Download 
Download all the services below from elastic.co site's download pages of each of their products.
Unpack all the services into their own distinct binary directories.

### 1 ElasticSearch

ElasticSearch is the search engine which contains indices of data ingested from various sources and it is the core of the Elastic Stack. It is at the heart of everything. So the first thing is to start this service up.

Minimal configuration needed and so can fallback to all defaults.

```bash
/bin/elasticsearch
```

by default, ElasticSearch runs on port 9200. So mines was running on localhost therefore - http://localhost:9200

### 2 Logstash

Logstash is a transformation pipeline. You feed in input data and you can filter it by doing a serious of transformations on that data fed in finally outputting back to the connecting sink. In case of the Elastic Stack (and previous the ELK stack) this would be Elastic Search the search engine.

This is optional. Tradtionally this was somewhat mandatory as it was one of the main services that made up the previous ELK stack.

```bash
/bin/logstash -f logstash-conf.conf
```

Logstash default runs on port 5044.

logstash-conf.conf:

```
input {
  stdin {}
  beats {
    port => 5044
  }
}

output {
  stdout {}
  elasticsearch {
    hosts => ["http://localhost:9200"]
    index => "%{[@metadata][beat]}-%{[@metadata][version]}-%{+YYYY.MM.dd}"
  }
}
```

In above I configured stdin & stdout plugins for input & output respectively simply for as a means of sanity test to ensure Logstash is up and running and appears fine to me. 

### Filebeat

```bash
/bin/filebeat
```

### Metricbeat

### Kibana

```bash
/bin/kibana
```

Finally, the visualization tool of the Elastic Stack allowing you to "see" the data ingested for analysis. 

With Kibana you can use it as a centralized logging tool where you can see all your logs for all your applications in one place.
You can also create various dashboards of different types of graphs of your log data.

