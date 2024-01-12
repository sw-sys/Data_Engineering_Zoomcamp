# Week 1: Introduction & Prerequisites

Tech: Docker, Postgres, Google Cloud Platform (GCP), Terraform

---

### **Focus**: Week 1 is dedicated to setting up the key tools and technologies you’ll be using throughout the course.

[Slides](https://www.slideshare.net/AlexeyGrigorev/data-engineering-zoomcamp-introduction)

[Videos](https://dezoomcamp.streamlit.app/~/+/Week_1_Introduction_&_Prerequisites)

- Local Part: Learn to package your application and its dependencies with Docker and run a fully functioning database using PostgreSQL.
- Cloud Part: Discover Google Cloud Platform and Terraform, focusing on automating the setup and management of your cloud architecture.

---
To do:
- [x] [Watch Intro video]

**Video Notes:**

Staff (2023, might have changed):
- Organisers - Alexey, Ankush, Sejal
- Previous participants - Kalise, Jeff
- Teaching assistants - Michael, Irem, Luis

Set up:
- [x] [Watch tool set-up video](https://www.youtube.com/watch?v=XOSUt8Ih3zA&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

**Video Notes:**
- Docker networks: a way for containers to communicate.
- Run postgress and pgadmin using Docker for NY dataset

Docker:
- [ ] [Intro to Docker](https://www.youtube.com/watch?v=EYNwNlOrpr0&t=5s)

**Video Notes:**
- Data pipeline is a fancy name for process that inputs data, transforms it, outputs more data e.g. csv > Python transfomation > table in postgres
- Docker - one computer can host many containers holding OS, libraries, ELTs. this means you can run db's in complete isolation/avoid conflict similar to envs. 
- Advantages of Docker = fast reproducability, can run local experiments testing (to ensure behaviour consistant/integration tests), integration, running pipelines in the cloud by porting image/serverless, can use in conjunction with Spark.
- 

- [ ] [Ingesting NY Taxi Data to Postgres](https://youtu.be/2JM-ziJt0WI)
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