# Smithright DataWorks - AI Architecture & Opportunities (all rights reserved)

DRAFT AI TECH STACK :

Enterprise Events Feed
    DB CDC + Service OpenTelemetry + 3rd party data feed ingestion + network telemetry + server telemetry + Workstation Telemetry? + comms feeds? + transaction & accounting feed & telemetry + agent telemetry => Unified GCP Pub/Sub Events Feed => RBAC-gated event channels => BigQuery
        
[AGI Reactor Components - Proprietary]

Agent Architecture
    Agent RBAC
    Langchain? / Dialogflow? / Nvidia NIM?
        Agent definitions
        Agent provisioning
        Agent logs

Prompt engineering
    Prompt library?
    Reasoning and planning flow scripts / DAG
    RAG logic for embedding retrieval & context

LLM's
    Controlled
        Ollama
            Qwen?
    API's
        Azure/OpenAI
        Claude

Training
    Data
        Local repos in Spanner/BigQuery
        Training data api's
    Fine-tuning
        Training module repo
        Training services

