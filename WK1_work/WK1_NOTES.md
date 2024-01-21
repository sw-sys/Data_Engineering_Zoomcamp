# Week 1: Introduction & Prerequisites

Tech: Docker, Postgres, Google Cloud Platform (GCP), Terraform

---

### **Focus**: Week 1 is dedicated to setting up the key tools and technologies you’ll be using throughout the course.

[Slides](https://www.slideshare.net/AlexeyGrigorev/data-engineering-zoomcamp-introduction)

[Videos](https://dezoomcamp.streamlit.app/~/+/Week_1_Introduction_&_Prerequisites)

- Local Part: Learn to package your application and its dependencies with Docker and run a fully functioning database using PostgreSQL.
- Cloud Part: Discover Google Cloud Platform and Terraform, focusing on automating the setup and management of your cloud architecture.

---

### Week 1: Introduction
**Tools:** Docker / SQL
**Start date:** 15 January 2024
**Homework due:** 25 January 2024
**Duration:** 2 weeks

---

To do:
- [x] [Watch Intro video]

**Video Notes:**

Staff Course instructors 2024: 
- Alexey Grigorev (Various)
- Victoria Perez Mola (week 4)
- Michael Shoemaker (terraform)
- Matt Palmer (2 - Data engineer - book 'Understanding ETL')
- Luis Oliverira - Data & Analytics Engieneer (Github codespaces, Docker, DQL, DBT)
- Sejal Vaidya (Data and ML engineer - Platform Infrastructure and Data Ingestion)
- Irem Erturk (IaC and stream processing with Python)

Set up:
- [x] [Watch tool set-up video](https://www.youtube.com/watch?v=XOSUt8Ih3zA&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

**Video Notes:**
- Docker networks: a way for containers to communicate.
- Run postgress and pgadmin using Docker for NY dataset

Docker:
- [x] [Intro to Docker](https://www.youtube.com/watch?v=EYNwNlOrpr0&t=5s)

**Video Notes:**
- Data pipeline is a fancy name for process that inputs data, transforms it, outputs more data e.g. csv > Python transfomation > table in postgres
- Docker - one computer can host many containers holding OS, libraries, ELTs. this means you can run db's in complete isolation/avoid conflict similar to envs. 
- Advantages of Docker = fast reproducability, can run local experiments testing (to ensure behaviour consistant/integration tests), integration, running pipelines in the cloud by porting image/serverless, can use in conjunction with Spark.
- It's possible to set up a container (e.g. python:3.9) but use a dockerfile to config what to do automatically e.g. FROM container, RUN a pip install, specify a WORKDIR, use ENTRYPOINT
- use sys & argv to pass the file [0] then arguments [1] like dates
- can use variables specified as args to return status updates

- [x] [Ingesting NY Taxi Data to Postgres](https://youtu.be/2JM-ziJt0WI)

[NYC taxi dataset](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)

**Video Notes about terminal:**
- running ubuntu, can use 'jupyter notebooks', 'less' to examine csv, 
- problems with pgcli (can't pip install)
- don't need to unzip .gz files
- What are .gz files? A type of compression created using gnu zip software, common on unix based systems
- use wslview . to go to file dir
- take the first one hundred rows - head -n 100 yellow_tripdata.csv > yellow_head.csv
- wc -l filename.csv command counts lines
- view the data dictionary to see what each field is
- Q. Why the heck are terminals so complex? Why are there so many and why all different syntax? Which to use for what? 
- Bash for pgcli seems to work
- pgcli commands to test conn - \dt & SELECT 1;
- WSL just need pgadmin, pgcli is not the way to do this

- [ ] [Connecting pgAdmin and Postgres](https://youtu.be/hCAIVe9N0ow)
- [ ] [Putting the ingestion script into Docker](https://youtu.be/B1WwATwf-vY)
- [ ] [Running Postgres and pgAdmin with Docker-Compose](https://youtu.be/hKI6PkPhpa0)
- [ ] [SQL refresher](https://youtu.be/QEcps_iskgg)

Intro to GCP:
- [ ] Introduction to GCP (Google Cloud Platform)
- [ ] Introduction to Terraform Concepts & GCP Pre-Requisites
- [ ] Workshop: Creating GCP Infrastructure with Terraform
- [ ] Setting up the environment on cloud VM

Homework:
- [ ] [Week 1 homework](https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/cohorts/2024)