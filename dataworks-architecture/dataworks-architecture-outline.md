# Smithright DataWorks - Core Architecture Outline

System Functions:
    - Scalable infrastructure for developing, hosting, testing, managing, delivering, and migrating secure & performant data pipelines to and for a fleet of clients.
    - Reliable and efficient infrastructure for MLops, prompt engineering, AI automation and services.
    - Full stack architecture for scalable public app hosting, service endpoints, and reporting.
    - Avoid vendor lockin risks, and prioritize open source technologies when pragmatic.

Architecture Summary:
    - Event-driven micro-service architecture, prioritizing security, reliability, scalability
    - GCP for Vertex AI, mlops, core service hosting, ingress & scaling
        - Azure for openai model tuning
    - DataBricks for data engineering & pipelines
    - Kafka for streaming
    - Airflow for automations

---

Dev Env:
    vscode + jupyter/colab
        env's & libraries: conda
        branching: gitlens
        containers: docker
        copilot

Secrets & Keys Mgmt:
    Core: Hashicorp Vault
    In-network Services: AWS, GCP, Azure for in-network hosted services or API's

Code Repo & Version Control: Git
    Host: Github - https://www.github.com/smithright
    Branching Strategy: GitFlow

Deployment Automation:
    Primary: Github Actions
    Alt: Jenkins
    Deployment Strategy:
        - Implement language server for pre-deployment test automations and compilation-time debugging & optimizations
        - Precompile to binaries
        - Load-scaling canary deployments via Istio

Service Hosting:
    Primary Compute Host: GCP
        Primary Core Services: GCP Cloud Run (Scaled Containers on managed GKE)
    Parallel Compute Intensive Services: Cuda Cloud

Container Templates: 
    Primary: Github Container Registry
    Alt: Jfrog

Core Database: Multi-master replicating relational DB
    Host: CRDB Cloud - https://www.cockroachlabs.com/docs/cockroachcloud/

DB Interface: Generated GraphQL
    Host: Hasura Cloud - https://cloud.hasura.io

Logging:
    ELK Stack
        Log search: Elasticsearch
        Log ingestion: Logstash
        Log visualization: Kibana
    Host: GCP Elastic Cloud

Security:
    System Security Config:
        Role-based access policy mgmt
            Hashicorp Vault + GCP IAM
            Hasura GraphQL policies
            Enforce service accounts with minimum required access for all interfaces
        System endpoint security configuation
            IaC: Terraform & Ansible
                for:
                    CRDB
                    Hasura
                    Container repo
                        Network config
        Log monitoring
            Prometheus + Grafana
            Stackdriver
            Carefully manage role-based access to logs
        Network & Intrusion detection 
            GCP Network Intel, Cloud Armor, Suricata
    Network Mgmt: 
        Suricata
        Snort
        ELK
    System Command & Control: 
        Kubectl
        GCP cloud console
    User authentication:
        Clerk
        JWT

Data Governance:
    Provenance and pipeline mapping: 
        Apache Atlas
    Endpoint mapping & service documentation: 
        GCP Endpoints
        OpenAPI/Swagger
        Hasura
        Airflow Directed Acyclic Graphs (DAG's)
    Internal info architecture governance: 
        GCP Data Catalog
    Compliance (GDPR, CCPA, etc.)
        Collibra

Data Engineering:
    Streaming ingress & egress:
        Kafka
            Hosting: Confluent Cloud - confluent.io
    Big data ops:
        Data Bricks
    Scheduled automations:
        Apache Airflow
        GCP Pub/sub, Tasks

Service Mesh:
    Public Endpoint Documentation: ?
    Private Endpoint Documentation: 
    Ingestion & Routing: Istio
        Service Metrics: Prometheus
    Hosting: GCP GKE

MLops:
    GCP Vertex AI
        TensorFlow
        Model training
    Public model repo: huggingface

Frontend:
    Framework: Next.js
    Host: Vercel
    Use a unified web app / mobile app design framework

SEO Optimization:
    robots.txt
    site map

User Analytics:
    Google analytics

Project Mgmt:
    Jira
    Slack
    Google Calendar/Meet

Documentation:
    Files: Google Drive

---

Performance considerations:

    Leverage parallel processing whenever possible
        Use CUDA or DPC++ to leverage GPU's or TPU's for parallel loops, matrix math, or other tensor operations 
        Queue large compute loads and scale horizontally via CUDA cloud or GCP pub/sub
        Prioritize multi-plexing network protocols: grpc, quic
        Use languages & compilers that optimize compilation & memory allocation e.g. rust, mojo, bend, zig
        Use languages and design applications for performant multi-threading e.g. golang, bend
        Consider when quantum computation algorithms could increase performance
            Use Nvidia, IBM, or Google quantum server api's
            Qiskit for simulating quantum circuits

    Deploy services as pre-compiled binaries to avoid runtime compilation delays

    Front-end performance:
        Leverage CDN's for low-latency static content delivery
        Use React server components to render front-end components quickly on a nearby edge network server, and update only the component rather than refreshing the whole page.
        Consider leveraging webasm as a compilation target

    Migrate from serverless interfaces that must encrypt and call each other over the public internet to an in-network service mesh 

    For ultra high performance & low latency
        Dynamically measure and map latency and performance bottlenecks across pipelines and system interfaces, automate prioritized performance opportunity reports.
            Profiling: Perf, GCP Profiler
            Tracing: Jaeger, OpenTelemetry
            Dynamic Analysis: Valgrind, GDB
            Reports: Grafana
        Migrate performance-critical functions to field programmable gate arrays (FPGA's) nearest to key endpoints
        Optimize the network stack for edge compute & streaming
            Use DHCP protocols & DMA to skip the kernel and post data streams directly to memory regions
            Offload network stack features from the kernel to a smartNIC
            Assemble outgoing multiplexing packets with pre-compressed structures directly on a scalable DPU server stack
            Migrate remote services inside the network to avoid encryption and data transfer overhead

Compute cost considerations:

    Avoid cloud & vendor lockin

    Use middleware to decouple service endpoints from infrastructure e.g. Istio, graphql