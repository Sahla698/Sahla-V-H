# Sahla V H
### Helping Business build strategic data solutions
## Cloud Data Engineer 
### Technical Skills
• Languages/Scripting: Python, SQL, PySpark, Terraform.
• Public Cloud Platform: GCP, Azure.
• Data Integration Tools: Google Cloud Composer, Google Dataplex, Azure Data Factory, Databricks.
• RDBMS Tools: BigQuery, MS SQL Server, Azure Synapse SQL DW.
• Version Control & Delivery : Gitlab, Google Cloud build
• Visualization tool : Power BI
### Work Experience
**GCP Data Engineer - Ernst & Young (June 2023 - Current)**

Tech stack: Google Bigquery, Cloud Composer, Reltio, Python,SQL,Airflow.
• Transformed the data integration framework by designing dynamic ETL processes, accelerating initial data
load by 30% while ensuring 100% data accuracy across various source systems into Reltio-compliant formats
with BigQuery stored procedures and Composer pipelines.
• Optimized ETL data pipelines by enhancing query performance in BigQuery, resulting in a 23% improvement
in processing speed and a 15% reduction in data latency for downstream applications.
• Engineered high-performance Airflow DAGs, which reduced manual intervention by 60% and improved
data pipeline reliability, automating complex DML operations between BigQuery and GCS.
• Implemented a metadata-audit balancing and error routing framework across BigQuery that proac-
tively flagged and routed data quality issues, significantly boosting operational efficiency.
• Implemented advanced monitoring and alert mechanisms to track data loads and detect reconciliation issues
using Cloud Logging and monitoring services.

The goal of the project is to centralize mastered data in the Reltio cloud MDM platform, reducing duplication. The GCP pipeline efficiently transfers raw data from staging2 to staging3 within designated Big Query tables, streamlining the integration process.
![Solution architecture workflow](/assets/architecture.PNG)
A parameterized framework approach was followed to build the data pipeline for multiple source application from stage2 to stage3. Google Big Query, Cloud Composer, Cloud logging and monitoring, etc were the GCP services that are being mostly leveraged as part of the data pipeline built. The badge learning helped me to understand and improve my skills in these tools.

The end-to-end dataflow across the pipeline consists of Audit, Reconciliation, error routing and Alerting frameworks, which ensures fast, optimized and resilient data load. The source data has been distributed across different legacy applications. Different attributes associated to a Person or organization are distributed across different tables in the BQ staging2 dataset. Our aim was to bring the mastered records associated with Person and Organization affiliated with the client, into stage3 dataset, then into Reltio. The target entities in staging3 Big Query dataset will be resembling the Reltio MDM database. BQ stored procedures were used for loading, test record filtering, metadata handling and reconciliation purpose. GCP composer is used to orchestrate and implement the dependencies between various target entity pipelines. The insight that I have gained from the badge learning has strengthened my capability to handle all these tasks. 
Below are the specific aspects developed as part of the data pipeline:
1. Audit Framework
The audit framework consists of :
(i)	Master table which controls whole loading process by maintaining multiple checkpoints in loading process and helps to restart the load.
(ii)	Audit and statistics table that captures the run details at job level such as Table_Id, Job run id, etc.
2.Reconciliation Framework
This framework is to ensure that the data loaded into target is balanced with the source data. For technical reconciliation, the source and target record counts are balanced and updated in the Audit Balance table. Based on these counts, the reconciliation process determines whether a particular load is balanced or not and update the audit table accordingly. This ensures the data load is completed without any data loss between staging2 and staging 3.
3. Error routing/filtering
The invalid/test records from source are filtered at the source level based on the profiling results. These error records along with their source table name, unique identifiers are loaded into an Error log table. Only valid records are passed to the target entities.
4. BQ stored procedures 
All the above 3 frameworks are leveraged via BQ stored procedures. For each entity in the target dataset, there are 2 stored procedures, viz loading and reconciliation SPs.
Loading SP is responsible for source data processing, test data filtering, and updating the audit framework tables whereas Reconciliation SPs calculates the source and target record counts and update the audit balance table. 
5. Airflow DAGs – GCP Composer
Following Airflow DAGs were developed for the entire framework:
(i)	Load_stage3_tables: Is responsible for the orchestration of end-to-end data flow from source to target. Both loading and reconciliation stored procedures in Big Query are called subsequently in the Airflow Python callable function. For each entity like Person, Organization in stage3, there will be associated tasks for loading and reconciliation. The entire flow is organized based on the dependency between the loading process of each entity.
(ii)	Create_environment: The dynamic creation of stage2, stage3 environment is facilitated. In these DAG, each table and stored procedures are dynamically created using BQ client API being called via python functions.
(iii)	Dml_jobs: This DAG is used to run dml jobs such as table deletion, one-time inserts, etc through Big Query client API.
6. Alert Mechanism
For any entity load job failure, error message is being sent to GCP Cloud logging services from the DAG. Load based alerts has been created to pick the job failure from logging service. Then the alert policy creates an incident and send email notification. Incidents will auto close if not acknowledged within 7 days. Notification channels could be configured as per the need.


**Associate Analyst - Ernst & Young (April 2021 -June 2023)**
Tech stack: Pyspark, Databricks, PowerBI, Microsoft Azure , MS SQL, Google Dataplex,Dataproc, Terraform.
• Revolutionized data management in the Integrated Cloud Data Platform (ICDP) by engineering high-performance
data ingestion, data quality and transformation modules leveraging Databricks and Pyspark.
• Orchestrated the deployment of the Dremio application using AKS, optimizing data virtualization layers, and
empowering rapid data access for end-users.
• Engineered a comprehensive suite of data integration solutions in GCP Dataplex, including custom PySpark
jobs for data transformations and robust data governance features such as Dynamic Data Masking, Policy Tags,
and Column and Row Level Security.
• Automated the infrastructure setup for GCP Dataplex services using terraform leveraging Google Cloud Build
and Cloud source repository.

### EDUCATION
Bachelor of Technology, APJ Abdul Kalam Technical University (2016 - 2020)
Electrical & Electronics Engineering 
### CERTIFICATIONS & ACHIEVEMENTS
• Google Cloud Certified Associate Engineer
• Databricks certified: Data engineer Associate.
• Awarded EY Spot Award (twice) for outstanding performance and accelerated project delivery.
