# Week 3: Data Warehouse

## Tech: BigQuery

---

### Focus: Week 3 focuses on efficient data management.

- Learn to use Google’s BigQuery for effective data management.
- Study data storage techniques like partitioning and clustering, and understand their differences.

---

- WK3 DTC [Repo](https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/03-data-warehouse)

To do:
 
- [x] Watch [Data Warehouse and BigQuery](https://www.youtube.com/watch?v=jrHljAoD6nM&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video Notes:**
- OLAP - OnLine Analytical Process - hold lots of data, designed to find insights. Periodically refresh data. Denormalised (less joins increases speed of querying). 
- OLTP - OnLine Transaction Processing - SQL backend. Fast but small updates. Normalised data for efficiency. 
- Data warehouse - what is it? An OLAP solution used for analysis. It holds raw data, meta data and summary data.
- BigQuery - what is it? A serveless data warehouse. It's easy to scale. Has built in feature for ML, geospacial analysis and BI. Stores data seperate from the compute engine which analyses the data = cost win.
- Go in to settings to disable "cached" data to get more consistant results.
- Gives access to public data (search in explorer)
- It's possible to 'explore data' using data studio
- Cost - around 1 TB of data processing was $5 in 2022. Can also prerequest slots (100 = $1000 dollars a month 0r 200TB data processing)
- Partitioning - can be done on creation date so only data processed is based on date. This saves money. e.g. PARTITIONED BY DATE(tpep_pickup_datetime)
- Partitions and clusters - It's possible to cluster within partitions and increase performance e.g. CLUSTER BY VendorID
- Best practices - 
- Internals - 
- ML in BQ -

- [ ] Watch [Partioning and Clustering](https://youtu.be/-CqXf7vhhDs&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video Notes:**

- if your dataset is less than 1GB, you won't see any improvements from partitioning or clustering the data on query performance
- However it will add cost because metadata

#### PARTITIONING 

There are different types of partioning:

1. time-unit column: unit can be hourly, daily, weekly, monthly
2. Ingestion time (_PARTITIONTIME):
3. Integer range partitioning:

- You can partition for volume e.g. if you medium sized you might partition by day but if you have massive volumes you might process based on an hourly time range
- there is a limit on the number of partitions in Big Query (4000 - if doing hourly partitions you should have a 'expire partitioning' strategy)
- 'expire partitioning' strategy:

#### CLUSTERING

- Column order matters - the sort order of the data is set by column organisation - so it will sort first on the most left column, then move across to the right most column
- You cna specify up to 4 clustering cols in Google Bigquery but they must be 'top level' and non-repeating columns
- You can choose between these types for clustering columns: date, bool, geography, int64, numeric, bignumeric, string, timestamp, datetime

#### Partitioning vs Clustering



- [ ] Watch [BigQuery Best Practices](https://www.youtube.com/watch?v=k81mLJVX08w&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video Notes:**

- [ ] Watch [Internals of Big Query](https://www.youtube.com/watch?v=eduHi1inM4s&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video Notes:**

## Advanced topics
- [ ] Watch [BigQuery Machine Learning](https://www.youtube.com/watch?v=B-WtpB0PuG4&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video Notes:**

- [ ] Watch [SQL for ML in BigQuery](https://github.com/DataTalksClub/data-engineering-zoomcamp/blob/main/03-data-warehouse/big_query_ml.sql)
**Video Notes:**

## Resources:
[BigQuery ML Tutorials](https://cloud.google.com/bigquery-ml/docs/tutorials)
[BigQuery ML Reference Parameter](https://cloud.google.com/bigquery-ml/docs/analytics-reference-patterns)
[Hyper Parameter tuning](https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-syntax-create-glm)
[Feature preprocessing](https://cloud.google.com/bigquery-ml/docs/reference/standard-sql/bigqueryml-syntax-preprocess-overview)

## Deploying an ML Model

- [ ] Watch [BigQuery Machine Learning Deployment](https://www.youtube.com/watch?v=BjARzEWaznU&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)
**Video Notes:**

- [ ] Watch [Steps to extract and deploy model with docker](https://github.com/DataTalksClub/data-engineering-zoomcamp/blob/main/03-data-warehouse/extract_model.md)
**Video Notes:**

## Homework

- [Details here](https://github.com/DataTalksClub/data-engineering-zoomcamp/blob/main/cohorts/2024/03-data-warehouse/homework.md)
- [Submit here](https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/cohorts/2024)