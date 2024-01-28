# Week 2: Workflow Orchestration

- What is workflow orchestration? automating and managing complex processes   like mgt of people, systems and data end-to-end, enabling the creation, deployment and monitoring of tasks (like ETL)
-ETL - extraction, transformation and loading of data
- What is data ingestion? the process of importing large, diverse data files from multiple sources in to a single storage medium, such as a datawarehouse or lake

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
- [ ] [What is orchestration?](https://www.youtube.com/watch?v=Li8-MWHhTbo&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

**Video notes:**
What is an Orchestration Pipeline?
What is a DAG?

- [ ] If not covered above, [What are data lakes?](https://www.youtube.com/watch?v=W3Zm6rjOq70&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

**Video notes:**

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