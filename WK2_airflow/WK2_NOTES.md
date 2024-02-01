# Week 2: Workflow Orchestration

- What is workflow orchestration? automating and managing complex processes   like mgt of people, systems and data end-to-end, enabling the creation, deployment and monitoring of tasks (like ETL)
-ETL - extraction, transformation and loading of data
- What is data ingestion? the process of importing large, diverse data files from multiple sources in to a single storage medium, such as a datawarehouse or lake
- What is data modeling? organising data to make it easier to understand, manage and access in a specific context. Techniques include dimensional modeling, entity-relationship modeling and data vault modeling.
- What is data warehousing? The process of designing a central repo to integrate data from one or more disparate sources.

## Tech: officially Mage.AI, Google Cloud Storage (GCS)
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
[x] [What is orchestration?](https://www.youtube.com/watch?v=Li8-MWHhTbo&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

**Video notes:**
- "Orchestration is the process of dependency management, facilitated by automation" It manages, schedules, triggers, monitors and allocates resources.
- A good orchestrator manages a lot of different functions - workflow mgt, automation, errors, recovery, monitors, alerts, resource optimisation, observability is key (inc debugging data pipelines, as well as compliance/auditing)
- What is an Orchestration Pipeline? The process of automating the movement of data from source to storage by configuring multiple pipeliene tasks in to one single workflow. Data orchestration tools automate the process of bringing data togehter from multiple sources, standardising it, and preparing it for data analysis.
- What is a [DAG]?(https://en.wikipedia.org/wiki/Directed_acyclic_graph) A Directed Acyclic Graph. It's a visual representation of the flow (and dependencies) of tasks in a data pipeline. It is made up of nodes (tasks) and directed edges (representing dependencies between tasks). Tasks are executed in a specific order without forming a loop.

[x] If not covered above, [What are data lakes?](https://www.youtube.com/watch?v=W3Zm6rjOq70&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

**Video notes:**
- What is a data lake? A repo that holds lots of data from many sources (structured or not). Ingest the data as quick;y as possible and make it accessible to analysts. It will have metadata for faster access. It will be secure and can scale. The hardware should be cheap as you're storing masses of data. Companies value data and want to grab and store it all. It avoids data loss before it's value is realised. 
- Data lake vs warehouse - the differences are that data lake is unstructured, the target users are data scientists, massive amounts of data daily. It's all about stremaing and real time analystics. However the warehouse is usually structured, the users are business analysts, the data size is smaller, it focuses on batch processing data.
- ETL (Export transform load) - ETL is used for small amounts of data, usually in a data warehouse. There will be a well defined schema, defined relationships and the data is written to it.
- vs ELT (Export load and transform) - used for large amounts of data, usually in a data lake. Based on schema on read, where the data is written and the schema is defined later.
- Barriers of Data lakes - can become data swamps (unuseful) very quickly, there is no versioning, schemas are incompatible for the same data without versioning, datasets can become useless, without metadata it's hard for a user to figure out what is the usefulness of the data for the project. Joining different datasets can also be challenging - there may not be a foreign key.
- Cloud providers - GCP has cloud storage, in AWS it's S3, in Azure, it's Azure blob.

## Mage 
[Docs here](https://docs.mage.ai/introduction/overview) [Slack here](https://www.mage.ai/chat)

[x] 2.2.2a - [What is Mage?](https://www.youtube.com/watch?v=AicKRcK3pa4&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video notes:**
- An Open source pipeline tool that allows yout to orchestrate, transform and integrate your data.
- Mage concepts include: 
- Projects - holds multiple pipelines
- Pipelines - DAGs or data workflows, made up of blocks
- Blocks - make up a transformation, written in Python, SQL or R. Blocks can be sensors (trigger on events), conditionals (branching and elif logic), dynamics (can create dynamic childnre) or webhooks (for addiitonal functionality), data integration, unified pipelines (pass data around), multi-user envs, templating
- Load, Transform, Export - this is usually what the blocks are doing, LTE'ing data
- Build, edit and share data pipelines with others including in a GUI or VS Code
- Engineering best practices built in - in-line testing & debugging, full observability (inc build in support for dbt models, streaming etc), DRY principles (Don't Repeat Yourself) so no more spaghetti DAGs with dup funcs and weird imports
- You can write the blocks and even less technical people can implement with the GUI
- Designed to reduce set up, config, all the admin that's working but not producing any output
- Projects > pipelines (DAGS, YAML files) > blocks (py or sql files which direct the work, orchestrated by Mage)
- Anatomy of a block (imports, decorator, function(needs df), assertion)

[x] 2.2.2b - [Configuring Mage](https://www.youtube.com/watch?v=tNiV7Wp08XE?list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video notes:**
- Run image, docker compose up then go to http://localhost:6789/ to see Mage
- [x] [Getting started repo](https://github.com/mage-ai/mage-zoomcamp)

[x] 2.2.2c - [A Simple Pipeline](https://www.youtube.com/watch?v=stI-gg4QBnI&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video notes:**
- Collecting data from an API
- At the top of mage is the project name
- go to left menu > 'pipelines' page
- click the name of the pipeline to enter, then to edit go to left menu 'edit pipeline'
- Run the action, similar to Jupyter
Scroll to last block, select the 3 dot icon and choose 'Execute with all upstream blocks'

[x] 2.2.3a - [Configuring Postgres](https://www.youtube.com/watch?v=pmhI-ezd3BE&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video notes:**
- There's a local postgres in a Docker image we built so config it
- Can see the pg creds (all db creds) in mage by going to Menu > Files > io_config.yaml
- Within the io_config.yaml we have profiles (the default is 'default' but you can create more and call them anything you want e.g. 'dev')
- it's possible to pull in env vars using jinja e.g. "{{ env_var('POSTGRES_DBNAME') }}"
- create the pipeline, then the block and you can define the profile inside the new block
- you can test a pg connection by creating a 'Data loader' SQL block, select raw SQL and SELECT 1;

[x] 2.2.3b - [Writing an ETL Pipeline](https://www.youtube.com/watch?v=Maidfe7oKLs&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video notes:**
- start a new pipeline, add a new data loader block, choose Python > API
- add URL [Taxi Dataset](https://github.com/DataTalksClub/nyc-tlc-data/releases/download/yellow/yellow_tripdata_2021-01.csv.gz)
- no need to use 'requests' lib or to unzip csv files with pandas
- However, we do need to map datatypes as when dealing with large datasets it helps reduce memory consumption
- If the data types change (or are wrong) the pipeline will fail. This is useful as it notifies you, you're not getting what you're expecting.
- to pass the pd you need to use the return keyword
- then you can add a 'Transformer' block (Python > generic)
- It's possible to use the @test decorator to verify outputs
- once everything has been transformed, create a 'Data exporter' block, choose "Python > Postgres"
- after naming, defin the schema_name, table_name, config_profile is dev etc
- to check if connection successful, can create a SQL data loader, use 'dev' profile, raw SQL and SELECT * FROM ny_taxi.yellow_cab_data LIMIT 10 to return first ten results from pg

- [Sample loading block](https://github.com/mage-ai/mage-zoomcamp/blob/solutions/magic-zoomcamp/data_loaders/load_nyc_taxi_data.py)

[ ] [Set up GCP](https://github.com/DataTalksClub/data-engineering-zoomcamp/blob/main/01-docker-terraform/1_terraform_gcp/2_gcp_overview.md)

[ ] [2.2.4a Config GCP](https://www.youtube.com/watch?v=00LP360iYvE&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video notes:**

[ ] [2.2.4b Writing an ETL Pipeline](https://www.youtube.com/watch?v=w0XmcASRUnc&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video notes:**

## ETL: GCS to BigQuery
[ ] [2.2.5a - Writing an ETL Pipeline](https://www.youtube.com/watch?v=JKp_uzM-XsM)
**Video notes:**

[ ] [2.2.6a - Parameterized Execution](https://www.youtube.com/watch?v=H0hWjWxB-rg&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video notes:**

[ ] [2.2.6b - Backfills](https://www.youtube.com/watch?v=ZoeC6Ag5gQc&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video notes:**

RESOURCES:
- [Mage Variables Overview](https://docs.mage.ai/development/variables/overview)
- [Mage Runtime Variables](https://docs.mage.ai/getting-started/runtime-variable)

## Deployment (optional)

- [ ] [See 2.2.7](https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/02-workflow-orchestration#229---%EF%B8%8F-homework)
**Video notes:**

## Airflow

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
- Create a new pipeline 'green_taxi_etl`
- add a data block, url = `https://github.com/DataTalksClub/nyc-tlc-data/releases/tag/green/download`
- set data types - ones from video are fine 
- return the df e.g. return pd.read_csv(url, sep=",", compression="gzip", dtype=taxi_dtypes)
- add a transform block (e.g. python generic)
- add a data exporter block (e.g. Python > postgres)
- for pg need to define schema_name, table_name, config profile dev etc
- add a data loader block to see SQL > postgress conn