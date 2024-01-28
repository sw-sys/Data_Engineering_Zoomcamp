# Week 2: Workflow Orchestration

- What is workflow orchestration? automating and managing complex processes   like mgt of people, systems and data end-to-end, enabling the creation, deployment and monitoring of tasks (like ETL)
-ETL - extraction, transformation and loading of data
- What is data ingestion? the process of importing large, diverse data files from multiple sources in to a single storage medium, such as a datawarehouse or lake
- What is data modeling? organising data to make it easier to understand, manage and access in a specific context. Techniques include dimensional modeling, entity-relationship modeling and data vault modeling.
- What is data warehousing? The process of designing a central repo to integrate data from one or more disparate sources.

## Tech: officially Mage.AI, Google Cloud Storage (GCS) but I'm trying to use Airflow 
- [Mage week](https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/02-workflow-orchestration) 
- [Airflow week](https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/cohorts/2022/week_2_data_ingestion)

## Homework:
- WEEK 2 [HOMEWORK here](https://github.com/DataTalksClub/data-engineering-zoomcamp/blob/main/cohorts/2024/02-workflow-orchestration/homework.md)
---

### **Focus:** Week 2 is about task automation and coordination within complex data pipelines.

- Learn what Data Lakes are and how to set them up using GCS.
- Use Mage to connect multiple steps in the workflow into a single process.

---

To do:
- [x] [What is orchestration?](https://www.youtube.com/watch?v=Li8-MWHhTbo&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

**Video notes:**
- "Orchestration is the process of dependency management, facilitated by automation" It manages, schedules, triggers, monitors and allocates resources.
- A good orchestrator manages a lot of different functions - workflow mgt, automation, errors, recovery, monitors, alerts, resource optimisation, observability is key (inc debugging data pipelines, as well as compliance/auditing)

**QUESTIONS TO ANSWER**
- What is an Orchestration Pipeline? The process of automating the movement of data from source to storage by configuring multiple pipeliene tasks in to one single workflow. Data orchestration tools automate the process of bringing data togehter from multiple sources, standardising it, and preparing it for data analysis.
- What is a [DAG]?(https://en.wikipedia.org/wiki/Directed_acyclic_graph) A Directed Acyclic Graph. It's a visual representation of the flow (and dependencies) of tasks in a data pipeline. It is made up of nodes (tasks) and directed edges (representing dependencies between tasks). Tasks are executed in a specific order without forming a loop.

- [x] If not covered above, [What are data lakes?](https://www.youtube.com/watch?v=W3Zm6rjOq70&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

**Video notes:**
- What is a data lake? A repo that holds lots of data from many sources (structured or not). Ingest the data as quick;y as possible and make it accessible to analysts. It will have metadata for faster access. It will be secure and can scale. The hardware should be cheap as you're storing masses of data. Companies value data and want to grab and store it all. It avoids data loss before it's value is realised. 
- Data lake vs warehouse - the differences are that data lake is unstructured, the target users are data scientists, massive amounts of data daily. It's all about stremaing and real time analystics. However the warehouse is usually structured, the users are business analysts, the data size is smaller, it focuses on batch processing data.
- ETL (Export transform load) - ETL is used for small amounts of data, usually in a data warehouse. There will be a well defined schema, defined relationships and the data is written to it.
- vs ELT (Export load and transform) - used for large amounts of data, usually in a data lake. Based on schema on read, where the data is written and the schema is defined later.
- Barriers of Data lakes - can become data swamps (unuseful) very quickly, there is no versioning, schemas are incompatible for the same data without versioning, datasets can become useless, without metadata it's hard for a user to figure out what is the usefulness of the data for the project. Joining different datasets can also be challenging - there may not be a foreign key.
- Cloud providers - GCP has cloud storage, in AWS it's S3, in Azure, it's Azure blob.

- [ ] [Setting up Airflow locally with Docker-Compose](https://www.youtube.com/watch?v=lqDMzReAtrw&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

More information in the [airflow folder](https://github.com/DataTalksClub/data-engineering-zoomcamp/blob/main/cohorts/2022/week_2_data_ingestion/airflow)

**Video notes:**

- [ ] [Ingesting data to GCP with Airflow](https://www.youtube.com/watch?v=9ksX9REfL8w&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb&index=19)

**Video notes:**
- Extraction: Download and unpack the data
- Pre-processing: Convert this raw data to parquet
- Upload the parquet files to GCS
- Create an external table in BigQuery

- [ ] [Ingesting data to Local Postgres with Airflow](https://www.youtube.com/watch?v=s2U8MWJH5xA&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

**Video notes:**
- Converting the ingestion script for loading data to Postgres to Airflow DAG

- [ ] Transfer service (AWS -> GCP) - optional, needs AWS acc
- [Video 1](https://www.youtube.com/watch?v=rFOFTfD1uGk&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
- [Video 2](https://www.youtube.com/watch?v=VhmmbqpIzeI&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

**Video notes:**

- [ ] Homework