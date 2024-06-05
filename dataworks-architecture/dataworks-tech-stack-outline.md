# Smithright DataWorks - Core Technology Stack Outline

System Functions:
    - Scalable infrastructure for developing, hosting, testing, managing, delivering, and migrating secure & performant data pipelines to and for a fleet of clients.
    - Reliable and efficient infrastructure for MLops, prompt engineering, AI automation and services.
    - Full stack architecture for scalable public app hosting, service endpoints, and reporting.
    - Avoid vendor lockin risks, and prioritize open source technologies when pragmatic.

Architecture Summary:
    - Event-driven micro-service architecture, prioritizing security, reliability, scalability
    - GCP for Vertex AI, mlops, core service hosting, ingress & scaling
        - Azure for openai model tuning
    - DataBricks for big data ops
    - Kafka for streaming
    - Airflow for automations
    - Secrets mgmt + RBAC + IaC + Stackdriver + IDPS for security

---

Dev Env:
    vscode + jupyter/colab
        env's & libraries: conda
        branching: gitlens
        containers: docker
        copilot

Secrets & Keys Mgmt:
    Core: Hashicorp Vault
        dynamic secrets & rotating credentials
    In-network Services: AWS, GCP, Azure for in-network hosted services or API's

Code Repo & Version Control: Git
    Host: Github - https://www.github.com/smithright
    Branching Strategy: GitFlow

Deployment Automation:
    Primary: Github Actions
    Alt: Jenkins
    Deployment Strategy:
        - Use GitOps best practices 
        - NixOps?
        - Implement language server for pre-deployment test automations 
        - Precompile to binaries
        - Load-scaling canary deployments via Istio

Test Automation:
    Istio fault injection (to test retry & routing logic etc.)
    Compilation-time debugging & optimizations


Service Hosting:
    Primary Compute Host: GCP
        Primary Core Services: GCP Cloud Run (Scaled Containers on managed GKE)
    Parallel Compute Intensive Services: Cuda Cloud

Container Templates: 
    Primary: Github Container Registry
    Alt: Jfrog

Service Scaling
    Define & apply Istio service mesh policies & config via IaC:
        ingress gateway config
        load balancing logic
        canary deployment logic
        policies for retries, timeouts, circuit breaking
        other sidecar proxy config
        opentelemetry config


GKE
    Helm
    ArgoCD?
    Flux?

Core Database: Multi-master replicating relational DB
    Host: CRDB Cloud - https://www.cockroachlabs.com/docs/cockroachcloud/

DB Interface: Generated GraphQL
    Host: Hasura Cloud - https://cloud.hasura.io

Logging:
    OpenTelemetry
    GCP Stackdriver
    ELK Stack?
        Host: GCP Elastic Cloud?
        Log search: Elasticsearch
        Log ingestion & store: Logstash
        Log visualization: Kibana

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
            Stackdriver
            Carefully manage role-based access to logs
        Network & Intrusion detection 
            GCP Network Intel, Cloud Armor, Suricata
    Network Mgmt: 
        Istio service mesh
            mutual TLS encryption between services
            service ID & certificate mgmt 
        GCP Service Connect
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





Data Engineering & Integrations:
    Architecture
        Streaming ingress & egress:
            Kafka
                Hosting: Confluent Cloud - confluent.io
        Big data ops & ETL:
            Data Bricks
        Scheduled automations:
            Apache Airflow
            GCP Pub/sub, Tasks
    Internal Service Integrations
        Notifications
            email: gmail api
            SMS & calls: callrail
            Slack API
    3rd Party Integrations:
        Sales & Marketing Automations: Airflow
            Social platform stream ingress: 
                kafka => GCP pub/sub for event-based responses
            Social post broker: Airflow service automations
        Order to Cash Automations: Airflow
            Authentication: Clerk.io
            Purchase & payments: Stripe, Paypal 
        Procurement & Payment Automations: Airflow
            Procumement: Stripe, Paypal 






Service Mesh:
    Public Endpoint Documentation: ?
    Private Endpoint Documentation: 
    Ingestion & Routing: Istio
        Service Metrics: Prometheus
    Hosting: GCP GKE
    Endpoint naming & routing:
        GCP managed DNS
        assign internal service endpoint names to handshake.org blockchain domains on an owned tld (for simple naming and added security)

Reporting & Analytics
    Hasura / SQL
    PowerBI / Python
    GCP Stackdriver / Bigquery
    Google Analytics

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
        Queue large compute loads and scale horizontally via CUDA cloud or GCP pub/sub => GKE
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
            Use DHCP protocols & DMA to skip the kernel and post data streams directly to memory regions.
            Offload network stack features from the kernel to a smartNIC
            Assemble outgoing multiplexing packets with pre-compressed structures directly on a scalable DPU server stack.
            Migrate remote services inside a secure network to avoid encryption and data transfer overhead.

Compute cost considerations:

    Avoid cloud & vendor lockin

    Use middleware to decouple service endpoints from infrastructure e.g. Istio, graphql

    Consider dynamic service cost comparisons and load balancing across multiple clouds & service providers