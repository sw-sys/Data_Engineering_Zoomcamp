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

- [x] [Connecting pgAdmin and Postgres](https://youtu.be/hCAIVe9N0ow)

- Not needed for WSL
- use this:

- [x] [Docker Module Walk-Through on WSL](https://www.youtube.com/watch?v=Mv4zFm2AwzQ)

**Video Notes about getting containers to connect:**
- pgadmin and postgres running in different containers
- created network called 'pg-network' so containers are able to see each other
- docs [docker network create](https://docs.docker.com/engine/reference/commandline/network_create/)
- pgadmin is connected to postgres 

- [x] [Putting the ingestion script into Docker](https://youtu.be/B1WwATwf-vY)

**Video Notes about Docker Compose:**
- instead of running containers for postgres and pgadmin, can run both at once using Compose
- once again [ ] [Docker Module Walk-Through on WSL](https://www.youtube.com/watch?v=Mv4zFm2AwzQ) more relevant
- need to create docker-compose.yml file
- ~~on wsl, env needs to be mapped not listed (: not =)~~ did not find to be true but could not use an .env file to hold the credentials

- [x] [Running Postgres and pgAdmin with Docker-Compose](https://youtu.be/hKI6PkPhpa0)
 - covered in WSL video

- [ ] [SQL refresher](https://youtu.be/QEcps_iskgg)

Intro to GCP:
- [x] Introduction to GCP (Google Cloud Platform)

**Video notes:**
- [Google Cloud Docs](https://cloud.google.com/docs)
- cloud computing service - hosts compute, storage, app devs that run on Google hardware
- We're covering infrastructure as a service (IaaS) for big data and storage and databases
- Create projects to manage your work
- to store data you create buckets

- [ ] [Local Setup for Terraform and GCP](https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/01-docker-terraform/1_terraform_gcp)

- [x] Introduction to Terraform Concepts & GCP Pre-Requisites

**Video notes:**
- What is Terraform? allows you to write instructions on how to build digital infrastructure (servers, networks, storage etc) then automatically creates it to your specifications.
- Terraform is infrastructure as code. Make resources with code files.
- Terraforming is shaping and creating conditions where you take a cloud platform like GCP, AWS and set up infrastructure where code can live and software can run using config files.
- Because it's a file, you can see everything, share the infrastructure, reproduce it from dev to production and helps keep things tidy/costs low as you can easily bring all the resources down.
- It does not manage or update code, deploy or update software, change immutable resources, can't manage resources outside the terraform config (e.g. kubernetes)
- Terraform runs on your local machine which uses a 'provider' to communicate with different services to bring up different infrastructure (on GCP, AWS, Azure)
- Providers are code that allows terraform to [manage resources on](https://registry.terraform.io/browse/providers)
- Key commands - init (get the providers), plan (what am I about to do?), apply (the code in the tf files), destroy (remove everything defined in the tf files)

- [x] Terraform Basics: Simple one file Terraform Deployment

**Video notes:**
- never upload your .json creds to github!
- 'terraform fmt' command will format the .tf file
- 'terraform plan'
- 'terraform apply' - provides an overview of values passed to funcs before running code to create infrastructure (search these in docs for more info)
- 'terraform destroy'- always do this, cut the cost
- credentials can be set and unset e.g. 'echo $GOOGLE_CRENTIALS' tells you where the location is, 'unset GOOGLE_CREDENTIALS' makes it blank again

- [x] Deployment with a Variables File

**Video notes:**
- 'terraform fmt' command will format the .tf file
- Check the docs e.g. ['bigquery dataset'](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/bigquery_dataset) then *'ctrl'* + *'f'* for 'required' to see how to configure the thingy
- Set your location to 'EU' (maybe?)
- it's also possible to create a 'variables.tf' file and declare variables in relation to the classes used e.g. gcs_storage_class or location. Apply these in the main .tf file using *func = var.nameofvar*
- credentials can also be set as a variable in the .tf file e.g. description = "My credentials" default = "./keys/my-creds.json" then call 'credentials = file(var.credentials)' in the main.tf

Homework:
- [ ] [Week 1 homework](https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/cohorts/2024)