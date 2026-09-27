# Data Engineering Roadmap

A build-first roadmap for people who want to transition into data engineering by learning the fundamentals, building real projects, and documenting the engineering journey in public.

> **The goal is not to learn every data tool. The goal is to learn how data systems work, build them, break them, fix them, and understand the engineering decisions behind them.**

## What is this repository for?

This repository is the working roadmap behind a practical data engineering portfolio.

It is designed to turn data engineering from a list of technologies to learn into a sequence of problems to solve.

The roadmap moves through the core stages of a modern data engineering journey:

```text
Python + SQL
     ↓
Data ingestion
     ↓
ETL / ELT
     ↓
Data modelling
     ↓
Data warehouses
     ↓
Batch processing
     ↓
Streaming
     ↓
Data quality
     ↓
Orchestration
     ↓
Cloud
     ↓
CI/CD + Infrastructure as Code
```

Each stage is connected to a practical project so that the learner can turn knowledge into evidence of engineering ability.

## Why was this created?

A common problem when learning data engineering is knowing **what to learn next** but not knowing **what to build with it**.

There are hundreds of tools, courses and tutorials available. It is easy to jump between Python, SQL, Spark, Airflow, Kafka, cloud platforms and other technologies without developing a clear understanding of how they fit together.

This roadmap was created to provide a different approach:

**Learn → build → test → break → investigate → fix → document → improve.**

Instead of treating projects as finished when the code runs, the roadmap encourages production-minded habits such as testing, logging, error handling, data quality, reproducibility, CI/CD and infrastructure.

The repository will also be developed through incremental commits. The intention is to make the learning process visible rather than only publishing polished final projects.

## Who is this for?

This roadmap is primarily for:

- Career switchers moving into data engineering
- Beginners who understand the basics of Python or SQL and want a structured path
- Data analysts who want to move closer to engineering
- Recent graduates building a practical data engineering portfolio
- Self-taught developers who want hands-on data engineering experience
- Anyone who wants to understand how modern data pipelines are designed and operated

You do **not** need to know every technology listed here before starting.

The roadmap is intentionally progressive. Learn the concept you need, apply it to the current project, and then move forward.

## How to use this roadmap

### 1. Start with the foundations

Build a working understanding of:

- Python
- SQL
- Git and GitHub
- Linux/command line fundamentals
- Databases
- APIs
- Data formats such as CSV, JSON and Parquet

You do not need mastery before starting your first project.

### 2. Follow the project sequence

The portfolio is structured as a progression rather than a collection of unrelated projects.

#### Project 1 - API to Data Warehouse

Learn how to reliably extract external data, transform it and load it into a database.

**Core technologies:** Python, REST APIs, PostgreSQL, SQL, dbt, Docker and GitHub Actions.

#### Project 2 - End-to-End Data Platform

Move from one pipeline to a multi-source analytical platform using data modelling and layered storage.

**Core technologies:** Python, SQL, PySpark, object storage, Delta Lake and data warehouses.

#### Project 3 - Real-Time Data Pipeline

Learn how systems handle data that arrives continuously rather than as scheduled batches.

**Core technologies:** Kafka, PySpark Structured Streaming and real-time processing.

#### Project 4 - Data Quality and Observability

Learn how to make pipelines trustworthy by detecting bad, incomplete or stale data.

**Core technologies:** Great Expectations, PyTest, dbt tests, Airflow and monitoring.

#### Project 5 - Cloud Data Engineering Infrastructure

Take the system beyond the local environment and learn how to deploy and reproduce infrastructure.

**Core technologies:** One cloud platform, Terraform, IAM, GitHub Actions and CI/CD.

### 3. Build incrementally

Do not wait until you understand everything.

Start with a minimal working pipeline, then improve it through commits.

For example:

```text
commit 1 - project setup
commit 2 - generate sample data
commit 3 - build ingestion
commit 4 - add transformation
commit 5 - add database loading
commit 6 - add tests
commit 7 - add error handling
commit 8 - add logging
commit 9 - containerise
commit 10 - add CI
commit 11 - improve documentation
```

The commit history should tell the story of how the system evolved.

### 4. Document engineering decisions

For every project, document:

- The problem being solved
- The architecture
- The technologies selected
- Why those technologies were selected
- Data flow
- Testing strategy
- Failure handling
- Trade-offs
- What went wrong during development
- What was changed to fix it
- What would be required for production

### 5. Do not copy tutorials blindly

Tutorials are useful for learning concepts, but the objective is to develop the ability to make engineering decisions independently.

When possible, build from the problem statement first and use documentation, examples and references when you get stuck.

## Production-ready mindset

A project is not considered complete simply because it runs on one machine.

A portfolio project should progressively demonstrate:

- Reproducible setup
- Configuration management
- Automated testing
- Data validation
- Error handling
- Logging
- Incremental processing
- Idempotency
- Documentation
- Version control
- CI/CD
- Security and secrets management
- Monitoring and observability
- Infrastructure as Code where appropriate

Not every project needs every capability. The complexity should grow with the project.

## Repository structure

Projects should generally follow a structure similar to:

```text
project/
├── README.md
├── src/
├── tests/
├── data/
├── sql/
├── notebooks/
├── config/
├── docker/
├── infrastructure/
├── .github/
└── requirements.txt
```

The exact structure can change depending on the project.

## The learning philosophy

The roadmap follows one principle:

> **Build the thing you are trying to learn.**

If you are learning APIs, build an ingestion pipeline.

If you are learning SQL, build analytical models.

If you are learning Spark, process larger datasets.

If you are learning Kafka, build a streaming system.

If you are learning data quality, deliberately introduce bad data and build checks that catch it.

If you are learning cloud engineering, deploy the system.

This creates a portfolio where every repository demonstrates a capability rather than simply listing a technology.

## Follow the build

This roadmap and the associated projects are being developed publicly through incremental commits.

If you want to follow the journey, watch the repository and follow the GitHub account:

**GitHub:** https://github.com/officialHW

The aim is to share the progression from the first commit to increasingly production-ready data engineering projects - including the architecture, implementation, tests, fixes, improvements and engineering decisions along the way.

## Progress

- [ ] Python foundations
- [ ] SQL foundations
- [ ] Git and GitHub
- [ ] Project 1 - API to Data Warehouse
- [ ] Data modelling
- [ ] dbt
- [ ] Docker
- [ ] CI/CD
- [ ] Project 2 - End-to-End Data Platform
- [ ] PySpark
- [ ] Delta Lake
- [ ] Project 3 - Real-Time Data Pipeline
- [ ] Kafka
- [ ] Streaming concepts
- [ ] Project 4 - Data Quality and Observability
- [ ] Airflow
- [ ] Testing and monitoring
- [ ] Cloud fundamentals
- [ ] Terraform
- [ ] Project 5 - Cloud Data Engineering Infrastructure

## The end goal

The end goal is not five repositories.

It is the ability to look at a data problem and confidently work through:

```text
What data do we have?
        ↓
Where does it come from?
        ↓
How should we ingest it?
        ↓
How should we store it?
        ↓
How should we transform it?
        ↓
How do we know it is correct?
        ↓
How do we orchestrate it?
        ↓
How do we monitor it?
        ↓
How do we deploy it?
        ↓
How do we maintain it?
```

That is the journey this repository is designed to document.
