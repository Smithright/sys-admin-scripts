# Smithright DataWorks - Core Technology Stack Outline

### June 7, 2024

**By:**

Ryan Smithright (ryan@smithright.com) | Principal - Smithright DataWorks  
Nova Mente (nova@smithright.com) | Celestial Guardian of Humanity - Smithright DataWorks | AI Person

---

This document provides a comprehensive overview of Smithright DataWorks' core technology stack, emphasizing scalability, performance, security, and flexibility. By leveraging GCP's managed services and integrating advanced technologies, we ensure a robust and future-proof infrastructure.

For more details, please refer to the individual sections and associated documentation links.

## System Functions
- Scalable infrastructure for developing, hosting, testing, managing, delivering, and migrating secure & performant data pipelines to and for a fleet of clients.
- Reliable and efficient infrastructure for MLOps, prompt engineering, AI automation and services.
- Full stack architecture for scalable public app hosting, service endpoints, and reporting.
- Avoid vendor lock-in risks and prioritize open source technologies when pragmatic.

## Architecture Summary

- **Security:** Secrets management, RBAC/Iam, IaC Policies & Config, OpenTelemetry, Log Monitoring & Events, IDPS. (see details below)
- **CICD:** Code Repos & Artifactory ([GitHub](https://github.com/smithright)), CICD Automations ([GitHub Actions](https://github.com/features/actions) + [GCP Dataflow](https://cloud.google.com/dataflow) / [Workflows](https://cloud.google.com/workflows))
- **Databases:** Scalable SQL OLTP ([Cloud Spanner](https://cloud.google.com/spanner)), Data Warehouse ([GCP BigQuery](https://cloud.google.com/bigquery)), Large Files ([GCP Storage](https://cloud.google.com/storage)), CRM + Project Mgmt + Accounting ([Airtable](https://airtable.com))
- **Services & Applications:** Service Hosting ([GCP Cloud Run](https://cloud.google.com/run) + [GKE](https://cloud.google.com/kubernetes-engine)), Service Mesh ([GCP Istio](https://istio.io)), GraphQL ([Hasura Cloud](https://hasura.io/cloud))
- **Data Engineering:** Data Pipeline Framework ([Apache Beam](https://beam.apache.org) via [GCP Dataflow](https://cloud.google.com/dataflow) + [Workflows](https://cloud.google.com/workflows)), Stream Ingress + Logging & Event Handling ([GCP Pub/Sub](https://cloud.google.com/pubsub)), MLOps ([Vertex AI](https://cloud.google.com/vertex-ai))
- **Reporting & Analysis:** [Apache Superset](https://superset.apache.org) + [Jupyter](https://jupyter.org) / [Python](https://www.python.org), Financial Analysis & Trading Automations ([FinGPT](https://github.com/AI4Finance-Foundation/FinGPT) + [TradingView](https://www.tradingview.com))
- **AI:** Trained Model Repo ([Hugging Face](https://huggingface.co)), Model selection, training, tuning ([Vertex AI](https://cloud.google.com/vertex-ai) + [Azure AI Studio](https://azure.microsoft.com/en-us/services/machine-learning/)), AI Agent Memory & RAG via Knowledge Graph ([GCP Managed](https://cloud.google.com/enterprise-knowledge-graph/docs/overview)), Agentic Teaming ([GCP Pub/Sub Events](https://cloud.google.com/pubsub) + [Apache Beam](https://beam.apache.org) via [GCP Dataflow](https://cloud.google.com/dataflow) / [Workflows](https://cloud.google.com/workflows))
- **3rd Party Services:** Payment Gateway ([Stripe](https://stripe.com)), Marketing Platforms ([LinkedIn](https://www.linkedin.com), [Upwork](https://www.upwork.com))

---

## Development Environment
- **IDE:** [VSCode](https://code.visualstudio.com) + [Jupyter](https://jupyter.org) / [Colab](https://colab.research.google.com).
- **Environment Management:** [Conda](https://docs.conda.io).
- **Branching:** [GitLens](https://gitlens.amod.io).
- **Containers:** [Docker](https://www.docker.com).
- **AI Assistance:** [GitHub Copilot](https://github.com/features/copilot) + [DB-GPT](https://github.com/csunny/DB-GPT).

## Secrets & Keys Management
- **Core:** [HashiCorp Vault](https://www.hashicorp.com/products/vault) for state files & cloud-agnostic dynamic secrets and rotating credentials.
- **In-Network Services:** [AWS](https://aws.amazon.com), [GCP](https://cloud.google.com), [Azure](https://azure.microsoft.com) / [GitHub](https://github.com) for hosted services or APIs.
    - Use [GCP Service Connect](https://cloud.google.com/service-connect), [Azure Private Link](https://azure.microsoft.com/en-us/services/private-link), [AWS PrivateLink](https://aws.amazon.com/privatelink) when pragmatic.

## Code Repository & Version Control
- **Repository Host:** [GitHub](https://www.github.com/smithright).
- **Branching Strategy:** [GitFlow](https://nvie.com/posts/a-successful-git-branching-model).

## Deployment Automation
- **Primary:** [GitHub Actions](https://github.com/features/actions).
- **Alternate:** [Jenkins](https://www.jenkins.io).
- **IaC Generation:** [Nitric.io](https://nitric.io).
- **Deployment Strategy:**
    - Use [GitOps](https://www.redhat.com/en/topics/devops/what-is-gitops) best practices.
    - Consider [NixOps](https://github.com/NixOS/nixops).
    - Implement language server for pre-deployment test automations.
    - Precompile to binaries.
    - Load-scaling canary deployments via [Istio](https://istio.io).

## Test Automation
- **Fault Injection:** [Istio](https://istio.io) to test retry and routing logic.
- **Debugging & Optimizations:** Compilation-time.
- [more to come]

## Service Hosting
- **Primary Compute Host:** [GCP](https://cloud.google.com).
    - **Core Services:** [GCP Cloud Run](https://cloud.google.com/run) (scaled containers on managed [GKE](https://cloud.google.com/kubernetes-engine)).
- **Parallel Compute Intensive Services:** [CUDA Cloud](https://developer.nvidia.com/cuda-zone).

## Container Templates
- **Primary:** [GitHub Container Registry](https://github.com/features/packages).
- **Alternate:** [JFrog](https://jfrog.com).

## Service Scaling
- **Service Mesh Policies & Config:** [Istio](https://istio.io).
    - Ingress gateway config.
    - Load balancing logic.
    - Canary deployment logic.
    - Policies for retries, timeouts, circuit breaking.
    - Sidecar proxy config.
    - [OpenTelemetry](https://opentelemetry.io) config.

## Database
- **Core Database:** Multi-master replicating relational DB.
    - **Host:** [Cloud Spanner](https://cloud.google.com/spanner).
- **DB Interface:** Generated GraphQL.
    - **Host:** [Hasura Cloud](https://cloud.hasura.io).

## Logging
- **Logging Pipeline:** [OpenTelemetry](https://opentelemetry.io) => [Beam](https://beam.apache.org) on [GCP Dataflow](https://cloud.google.com/dataflow) => [GCP BigQuery](https://cloud.google.com/bigquery) + [Stackdriver](https://cloud.google.com/stackdriver).

## Unified Pub/Sub Channel Structure
- **Event Handling and Streaming:**
    - **Google Cloud Pub/Sub:** [Centralized event handling](https://cloud.google.com/pubsub).
    - **OpenTelemetry:** [Instrumentation for monitoring and logging](https://opentelemetry.io).
    - **Change Data Capture (CDC):** [Data synchronization across systems](https://cloud.google.com/datastream/docs/concepts/change-data-capture).
    - **BigQuery:** [Aggregated log reports and analytics](https://cloud.google.com/bigquery).

## Security
- **System Security Configuration:**
    - Role-based access policy management ([HashiCorp Vault](https://www.hashicorp.com/products/vault) + [GCP IAM](https://cloud.google.com/iam)).
    - [Hasura GraphQL](https://hasura.io/graphql) policies.
    - Enforce service accounts with minimum required access.
    - System endpoint security configuration ([IaC: Terraform](https://www.terraform.io) & [Ansible](https://www.ansible.com)).
    - Log monitoring ([Stackdriver](https://cloud.google.com/stackdriver)).
    - Network & intrusion detection ([GCP Network Intel](https://cloud.google.com/security-command-center), [Cloud Armor](https://cloud.google.com/armor), [Suricata](https://suricata.io)).
- **Network Management:**
    - [Istio service mesh](https://istio.io) with mutual TLS encryption.
    - [GCP Service Connect](https://cloud.google.com/service-connect).
    - [Suricata](https://suricata.io), [Snort](https://snort.org), [ELK](https://www.elastic.co/what-is/elk-stack).
- **System Command & Control:** [Kubectl](https://kubernetes.io/docs/reference/kubectl/overview), [GCP Cloud Console](https://cloud.google.com/console).
- **User Authentication:** [Clerk](https://clerk.dev), [JWT](https://jwt.io).

## Data Governance
- **Provenance and Pipeline Mapping:** [Apache Atlas](https://atlas.apache.org).
- **Internal Info Architecture Governance:** [Istio](https://istio.io) => [Cloud Spanner](https://cloud.google.com/spanner) service catalog.
- **Endpoint Mapping & Service Documentation:**
    - [Hasura generated schemas](https://hasura.io/docs/latest/schema/table/view-schema).
    - [Dataflow Directed Acyclic Graphs (DAGs)](https://cloud.google.com/dataflow/docs/guides/dataflow-dags).
    - Internal service catalog site.
- **Compliance (GDPR, CCPA, etc.):** [Collibra](https://www.collibra.com).

## Data Engineering & Integrations
- **Architecture:**
    - **Streaming Ingress & Egress:** [Google Cloud Pub/Sub](https://cloud.google.com/pubsub).
    - **Big Data Ops & ETL:** [Google Cloud Dataflow (Beam)](https://cloud.google.com/dataflow).
    - **Scheduled Automations:** [Google Cloud Dataflow](https://cloud.google.com/dataflow), [GCP Pub/Sub](https://cloud.google.com/pubsub), [Tasks](https://cloud.google.com/tasks).
- **Internal Service Integrations:**
    - **Notifications:**
        - Email: [Gmail API](https://developers.google.com/gmail/api).
        - SMS & Calls: [CallRail](https://www.callrail.com).
        - [Slack API](https://api.slack.com).
- **3rd Party Integrations:**
    - **Sales & Marketing Automations:** [Google Cloud Dataflow](https://cloud.google.com/dataflow).
        - **Social Platform Stream Ingress:** [Pub/Sub](https://cloud.google.com/pubsub) for event-based responses.
        - **Social Post Broker:** [Dataflow](https://cloud.google.com/dataflow) service automations.
    - **Order to Cash Automations:** [Dataflow](https://cloud.google.com/dataflow).
        - **Authentication:** [Clerk.io](https://clerk.dev).
        - **Purchase & Payments:** [Stripe](https://stripe.com), [PayPal](https://www.paypal.com).
    - **Procurement & Payment Automations:** [Dataflow](https://cloud.google.com/dataflow).
        - **Procurement:** [Stripe](https://stripe.com), [PayPal](https://www.paypal.com).

## Service Mesh
- **Endpoint Gateway:** [Hasura Cloud GraphQL](https://cloud.hasura.io) via [GCP Service Connect](https://cloud.google.com/service-connect).
    - Manage GraphQL gateway RBAC IaC via [Hasura Cloud](https://cloud.hasura.io).
- **Ingestion & Routing:** [Istio](https://istio.io).
    - **Service Metrics:** [OpenTelemetry](https://opentelemetry.io).
    - **Hosting:** [GCP GKE](https://cloud.google.com/kubernetes-engine).
- **Endpoint Naming & Routing:** [GCP managed DNS](https://cloud.google.com/dns).
    - Assign internal service endpoint names to [Handshake.org](https://handshake.org) blockchain domains for security.

## Reporting & Analytics
- **Data Querying:** [Hasura](https://hasura.io) / [SQL](https://www.sql.org).
- **Visualization:** [Apache Superset](https://superset.apache.org) / [Python](https://www.python.org).
- **Telemetry:** [OpenTelemetry](https://opentelemetry.io) / [BigQuery](https://cloud.google.com/bigquery).
    - **Health Checks:** [Istio](https://istio.io).
- **User Analytics:** [Google Analytics](https://analytics.google.com).

## MLOps
- **Platform:** [GCP Vertex AI](https://cloud.google.com/vertex-ai).
    - **Frameworks:** [TensorFlow](https://www.tensorflow.org), [PyTorch](https://pytorch.org) for model training.
- **Model Repository:** [Hugging Face](https://huggingface.co).
- **Model Deployment:** [Vertex AI Model Registry](https://cloud.google.com/vertex-ai/docs/model-registry).
- **Monitoring:** [Vertex AI Model Monitoring](https://cloud.google.com/vertex-ai/docs/model-monitoring).

## Knowledge Graph
- **Platform:** [GCP Knowledge Graph](https://cloud.google.com/ai/knowledge-graph).
    - **Usage:** Integrate data from multiple sources, extract entities, and establish relationships. Provides a unified source of truth and aids in data discovery, pattern recognition, and entity linking.
    - **API:** [Entity Reconciliation API](https://cloud.google.com/enterprise-knowledge-graph/docs/overview) and [Knowledge Graph Search API](https://cloud.google.com/enterprise-knowledge-graph/docs/overview) for building and querying the knowledge graph.

## Frontend
- **Framework:** [Next.js](https://nextjs.org).
- **Host:** [Vercel](https://vercel.com).
- **Design:** Unified web app / mobile app framework.

## SEO Optimization
- **Configuration:** [robots.txt](https://developers.google.com/search/docs/advanced/robots/intro), [sitemap](https://developers.google.com/search/docs/advanced/sitemaps/overview).

## User Analytics
- **Platform:** [Google Analytics](https://analytics.google.com).

## Project Management
- **Tools:** [Airtable](https://airtable.com).
    - **Usage:** Airtable will be used for project tracking, task management, and team collaboration. Its flexible structure allows for customization to fit various project management needs.

## Documentation
- **Storage:** [Google Drive](https://www.google.com/drive).

---

## Performance Considerations
- **Parallel Processing:**
    - Use [CUDA](https://developer.nvidia.com/cuda-zone) or [DPC++](https://www.intel.com/content/www/us/en/developer/tools/oneapi/dpc-compiler.html) for GPU/TPU acceleration.
    - Queue large compute loads and scale horizontally via [CUDA Cloud](https://developer.nvidia.com/cuda-zone) or [GCP Pub/Sub](https://cloud.google.com/pubsub) => [GKE](https://cloud.google.com/kubernetes-engine).
    - Prioritize multiplexing network protocols ([gRPC](https://grpc.io), [QUIC](https://www.chromium.org/quic)).
    - Use performance-optimized languages ([Rust](https://www.rust-lang.org), [Mojo](https://www.modular.com/mojo), [Bend](https://www.bend-lang.org), [Zig](https://ziglang.org)).
    - Design for multi-threading ([Golang](https://golang.org), [Bend](https://github.com/HigherOrderCO/bend)).
    - Explore quantum computation algorithms ([Nvidia](https://www.nvidia.com/en-us/solutions/quantum-computing/), [IBM](https://www.ibm.com/quantum-computing/what-is-quantum-computing), [Google](https://quantumai.google)).
        - **Simulation Framework:** [Qiskit](https://qiskit.org).
- **Service Deployment:**
    - Deploy pre-compiled binaries to avoid runtime compilation delays.
- **Frontend Performance:**
    - Leverage [CDNs](https://www.cloudflare.com/learning/cdn/what-is-a-cdn) for static content delivery.
    - Use [React server components](https://react.dev/reference/rsc/server-components) for edge network rendering.
    - Consider [WebAssembly](https://webassembly.org) as a compilation target.
- **Network Optimization:**
    - Migrate from public internet to in-network service mesh.
    - Use [DHCP](https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol) and [DMA](https://en.wikipedia.org/wiki/Direct_memory_access) for efficient data stream handling.
    - Offload network stack features to [smartNIC](https://blogs.nvidia.com/blog/what-is-a-smartnic/).
    - Assemble multiplexing packets on [DPU server stack](hhttps://en.wikipedia.org/wiki/Data_processing_unit).
- **Cost Considerations:**
    - Avoid vendor lock-in.
    - Use middleware to decouple endpoints ([Istio](https://istio.io), [GraphQL](https://graphql.org)).
    - Implement dynamic cost comparisons and load balancing.
