# Smithright DataWorks - Core Architecture Outline

System Functions:
    - Scalable infrastructure for developing, hosting, testing, managing, delivering, and migrating secure & performant data pipelines to and for a fleet of clients.
    - Reliable and efficient infrastructure for MLops, prompt engineering, AI automation and services.
    - Full stack architecture for scalable public app hosting, service endpoints, and reporting
    - Avoid vendor lockin risks, and prioritize open source technologies when pragmatic

Architecture Summary:
    - Event-driven micro-service architecture, prioritizing security, reliability, scalability
    - GCP for Vertex AI, mlops, core service hosting, ingress & scaling
        - Azure for openai model tuning
    - DataBricks for data engineering & pipelines
    - Kafka for streaming
    - Airflow for automations

---

Code Repo & Version Control: Git
    Host: Github - https://www.github.com/smithright

Deployment Automation:
    Primary: Github Actions
    Alt: Jenkins

Service Hosting:
    Primary Compute Host: GCP
    Primary Core Services: GCP Cloud Run


Container Templates: 
    Primary: Github Container Registry
    Alt: Jfrog

Core Database: Multi-master replicating relational DB
    Host: CRDB Cloud - https://www.cockroachlabs.com/docs/cockroachcloud/

DB Interface: Generated GraphQL
    Host: Hasura Cloud - https://cloud.hasura.io

Logging:
    Log search: Elasticsearch
    Log ingestion: Logstash
    Log visualization: Kibana
    Host: GCP Elastic Cloud

Security:
    Secrets Mgmt:
        Core: Hashicorp Vault
        Alts: AWS, GCP, Azure for in-network hosted services or API's
    
     

Service Hosting: