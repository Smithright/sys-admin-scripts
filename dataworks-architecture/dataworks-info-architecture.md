# Smithright DataWorks - Core Information Architecture Outline

    Hashicorp
        Secrets Vault
            RBAC:
                root system keys
                service account keys
                api keys
    Github
        Code
            Private repos
                Client code
                Terraform state config?
            Public repos
                Other scripts & internal code when pragmatic
        IaC
            Container templates
                Docker templates
                    Microservice container templates
                        Nix - security hardened base image
                        Alphine - security hardened base image
                    Role-based workstation VM images
                        Internal developer workstation VM
                        Client developer workstation VM
            Configuraton State Files
            Scripts
                Github Action Scripts
                    Test automations
                    Deployments
                Provisioning Scripts
                    New Client System Provisioning Script Stack
                        New client: Hosting & system requirements intake checklist
                        New client backend / data pipeline - Default provisioning scripts
                            New project folder with delivery templates
                            New airtable PM space
                            New private project code repo
                            New CRDB cloud cluster
                            New Hasura cloud account
                            New GCP project & RBAC
                            Istio - Dev service mesh
                            Istio - Test service mesh
                            Istio - Preprod service mesh
                            Istio - Prod service mesh
                            New Cloud Run service template
                                Airflow container
                                DataBricks container
                                Kafka container
                                OpenTelemetry container
                                PowerBI container
                        New client web app  - Default provisioning scripts
                            Clerk.io
                            Next.js
                            New CDN service account
                            Server component templates
                        New integration script templates
                            Payments
                                Stripe
                                Paypal

    Airtable
        CRM
            Companies
            People
                Sales pipeline
                    Opportunities & Leads
                        Engagement history
                    Contracts
                Clients
                Partners
        Project management
            Internal work scope
            Client work scope
        System catalog
            System admins & roles
            Cost projections
        Service catalog
            Istio service account ID
            Assigned endpoint domain names
            System admins & roles
            Cost projections

    Google
        Drive
            Internal
                Wiki
                Individual & Ad hoc
                Training
                Sales & marketing assets
                Design assets
                Delivery templates
                Archive & artifacts

            Client-facing
                Project collaboration spaces
                    work in progress
                    deliverables

        GCP
            RBAC/IAM
            Stackdriver => Unified Log Store
            Cloud Armor config
            Projects
                Default Service Architecture (for Internal & Client-facing services)
                    Cloud Run
                        Istio service mesh (separate meshes for dev, test, preprod, prod)
                            Custom Microservices
                            Airflow
                            DataBricks
                            Kafka
                            OpenTelemetry => Unified Log Store
                            PowerBI
                Internal & Managed Client Services
                    Unified log monitoring and event logic
                        GCP pub/sub?
                            Event Channels:
                                Production Outages
                                Network events
                                Errors
                             Event pattern triggers
                                Endpoint load surges
                                IDPS patterns
                                Service SLA failures
                        Emergency/Outage SMS & call service
                        Ticketing interface to Airtable
                    Data Engineering - Internal Services
                        System & Service Catalog Feeds
                            Istio service discovery & logs => GCP pub/sub => service change channels => queue updates to airtable catalogs for role-based review & approval
                        Service Catalog Site
                            Generated Service Directory Page (based on user permissions)
                                Generated service link graph
                                Uptime graphs
                            Generated Service Info Pages (conditional visibility and modules based on public/private authenticated permissions)
                                Service Roles
                                    Owner
                                    Other Stakeholders
                                Access
                                    GraphQL
                                        Service spec
                                            schema
                                            input params
                                            output format
                                        View current permissions summary
                                            Request access
                                Usage (RBAC limited)
                                    Log Query interface
                                    Live graphs
                                        Graph interface
                                Wiki.js
                        GCP DataFlow Ingress & Routing Streams
                            Airtable CDC 
                                => GCP pub/sub (for optional channel event logic)
                                => CRDB read-only views
                            Clerk.io => CRDB user data tables (read only)
                            Social media & marketing platform data (other than Google Analytics)
                                => GCP pub/sub (for optional channel event logic)
                                => CRDB read-only views
                        Data Pipeline latency & performance logs => unified log store
                            Internal service pipelines & interfaces
                            Performance testing for contracted software (pre-delivery)
                            Performance logs for client managed services/apps/systems
                        Social post broker - airflow service automations 
                            Articles
                                Linkedin
                                Medium
                                Site blog
                                google news
                                Site partners
                            Newsletter
                            Social News
                                Facebook
                                Instagram
                                X.com
                            PPC marketing platforms
                                Linkedin
                                Upwork
                                Google



                    Hosted PowerBI or Python dashboards with role-based access
                        
                        Core Dashboard Apps
                            Security & Infrastructure
                                Network Analytics
                                IDPS Analytics
                                Log Analytics
                            Service & Endpoint Analytics
                                Public Endpoint Usage Analytics
                                Internal Endpoint & Service Usage Analytics
                                Data Pipeline Latency Analytics
                                App Performance Analytics
                            App & User Analytics 
                                Company-owned Public Apps - Usage Analytics

                            Marketing Analytics
                            Sales Analytics

                            Cost Center Analytics
                                Fixed Cost 
                            P&L Analytics
                            HR
                                Recruiting Analytics
                                Individual Contributor Analytics
                                Team Analytics
                        RBAC for Core Data SQL Analysis
                            Role-based PowerBI or Jupyter Analysis Templates
                                GCP Stackdriver
                                    Unified Log Queries (ROOT ADMINS ONLY)
                                    Unified Log Queries (Sys Admin / Security Analyst - Case Restricted)
                                    Service User Analytics (per service)
                                CRDB Accounting Tables
                                    Finance & Accounting Queries (Controller)
                                    Finance & Accounting Queries (Analyst)
                                Google Analytics
                                    App User Analytics (per app)
                                

                                HR Table Queries (Director)
                                HR Table Queries (Analyst)
                        RBAC for Ad Hoc reports & dashboards
            Cloud Store (for large static assets)


    CRDB
        Internal Company Cluster
            Internal Service & Application Data
                Logs & auditing
                    CDC
                Accounting
                Data Engineering
                    Training data
                    Staging views

                Reporting
                Ad hoc table space
    
    Hasura
        GraphQL engine & endpoints
            RBAC policies 