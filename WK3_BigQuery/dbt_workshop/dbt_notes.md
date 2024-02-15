# Dlt workshop

### Resources
- [dlt notebook](https://colab.research.google.com/drive/1kLyD3AL-tYf_HqCXYnA3ZLwHGpzbLmoj#scrollTo=3RGdjQnN7J8A&forceEdit=true&sandboxMode=true)

- [ ] [Form for submitting the homework:](https://courses.datatalks.club/de-zoomcamp-2024/homework/workshop1)

### Data ingestion with dlt

- [ ] [Workshop page and homework:](https://github.com/DataTalksClub/data-engineering-zoomcamp/blob/main/cohorts/2024/workshops/dlt.md)

**Video notes:**

- the workshop will focus on building robust, scalable, self maintaining pipelines with built-in governance (in other words, best practice applied)

- What is dlt? 

A library that automates data ingestion (loading, schema mgt, data type detection, scalability, self healing, scalable extraction...)

- How do dlt and mage differ?

Mage is an orchestrator. You can run dlt pipelines in mage to get the both of best worlds.

- What is self healing? 

"In the context of data engineering, self-healing refers to the ability of a data pipeline to automatically recover from failures or errors, ensuring pipeline reliability. This is achieved through the implementation of mechanisms that detect and address issues without human intervention, thereby maintaining the continuous and proper functioning of the pipeline. Self-healing design patterns are essential for building robust and resilient data pipelines, and they typically involve the use of automated alerts, prevention of error scenarios, and simple recovery steps to minimize the support burden on the development team" https://www.perplexity.ai/search/What-is-self-HihtlSarRL2xmRjlvy_WiA?s=c

- What is data ingestion? 

Process of extracting data from a producer, transporting it to an environment where it can be prepared, normalising and sometimes cleaning, and adding metadata.

- Data lake is a consequence of this process. In it will be structured data with explicit schema (like parquet, avro or table in a db) or weakly typed and without explicit schema (csv or json)

- Csv is just like a layout, it doesn't have the metadata layer that loaded data has

- What is a schema? 

"specifies format and structure of data within a doc or data store, defining the allowed keys, their data types and any constrainers or relationships." https://github.com/DataTalksClub/data-engineering-zoomcamp/blob/main/cohorts/2024/workshops/dlt_resources/data_ingestion_workshop.md

## What does a data engineer do?
- ensure data flows from source systems to analytical destinations
- build, run, fix pipelines
- ensure data quality, integrity, implement effective data goverance, refine data architecture to meet the evolving needs of the organisation
- beyond the mechanics, they need to strategically mgt and enhance throughout the data lifecycle e.g. retention policies for private data (GDPR?)
- You should go learn about incremental extraction (pulling only the data you want)

## How can we extract the data?

- you will be extracting data from apis (web) or from dbs.
- When extracting, consider the hardware limits:
1. manage memory - you could run out of ram or disk space on cloud, so stream the data by event or chunk e.g. steam data between buffers like API to local file, webhooks to event queues, from event queue (Kafka, SQS) to Bucket (events being an occurance e.g. a completed taxi trip)
- build a generator (see https://github.com/DataTalksClub/data-engineering-zoomcamp/blob/main/cohorts/2024/workshops/dlt_resources/data_ingestion_workshop.md) so instead of listing all the items, waiting for script to finish running we can 
2. network limits - can't control but can repeat requests
3. source api limits e.g. requests per second, rate limitations

## How to normalise, clean, add metadata such as schema and types
- a lot of this is automated with dlt

## Incremental loading:
- Vital for fast, cost effective data refreshes.
- just load new values and update old ones which have changed