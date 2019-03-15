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