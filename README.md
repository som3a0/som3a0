<div align="center">

# Ismael Khalifa

**Data Engineer — I build data systems people can trust**

<sub>Real-time pipelines · Medallion architecture · Dashboards engineered to agree with each other</sub>

<br>

![Status](https://img.shields.io/badge/STATUS-Open_to_Data_Engineering_roles-7E9A72?style=flat-square&labelColor=161310)
![Location](https://img.shields.io/badge/BASED_IN-Egypt-6F93A6?style=flat-square&labelColor=161310)
![DEPI](https://img.shields.io/badge/DEPI_2026-Microsoft_Data_Engineer_Track-C9A227?style=flat-square&labelColor=161310)

[Portfolio](https://som3a0.github.io/) · [LinkedIn](https://www.linkedin.com/in/ismael-khalifa/) · [Email](mailto:ismael.elsayed.khalifa@gmail.com)

</div>

<br>

Most GitHub profiles show a pipeline that moved data once, in a notebook, and it worked.
The project below is the version that has to keep working — validated at the door,
reconciled behind a single source of truth, and instrumented so a 3&nbsp;AM failure shows
up as a dashboard panel, not a phone call.

<br>

## Engineering Philosophy

| Principle | How it actually shows up |
|---|---|
| **One number, everywhere** | Every consumer — dashboard, API, chatbot — filters to `WHERE batch_id = MAX(batch_id)`. Averaging across snapshots was an early bug. It's now a rule, not a preference. |
| **Explain it, don't just score it** | Every alert carries a root cause (`GAS_LEAK`, `HIGH_TEMP`, `SMOKE_SPIKE`), computed once, server-side — never recomputed on the client. |
| **Design for the dependency that fails** | A 3-model AI fallback chain, then a fully deterministic, database-grounded reply. It degrades in personality, never in usefulness. |
| **Make the wrong architecture hard to build** | Two dashboard views are derived from **one** endpoint, not two — so an entire class of count-mismatch bugs can't exist, not just "shouldn't." |

<br>

## Featured Project

### Smart City Gas & Air Safety Monitoring Platform
`Feb – May 2026` · DEPI 2026 Graduation Project · [Source code →](https://github.com/som3a0/Smart-City-Gas-Air-Safety-Monitoring)

**The problem.** Gas leaks, LPG buildup, and air-quality risk in dense residential and
industrial areas are usually invisible until a person notices — a resident smells gas, a
neighbor calls a hotline, a crew responds after the fact. There's no continuous, city-scale
layer showing where risk is *accumulating* before it becomes an incident.

**What it does.** Simulates that missing layer across all 27 Egyptian governorates —
3,000 sensor nodes across 169 real zones, streaming through Kafka (3 partitions, keyed by
`house_id` for ordered, horizontally-scalable ingestion) into three **independent, isolated**
Spark Structured Streaming queries — Bronze, Silver, Gold — each with its own checkpoint, so
a failure in one can't corrupt another. Gold lands in SQL Server and is served through
Grafana, a custom React "Command Center," and **ARIA** — a bilingual (Arabic/English)
assistant grounded in the same live data.

<img src="./assets/architecture.svg" width="100%" alt="Architecture diagram: an IoT Simulator feeds Kafka, which fans out to three independent Spark Structured Streaming queries — Bronze, Silver, and Gold. Gold writes to SQL Server, which serves three parallel consumers — Grafana, a React Command Center, and the ARIA assistant."/>

**Decisions that mattered more than the tech stack:**

- **A single filter, enforced everywhere.** Early builds let each consumer decide how to read "current" data; numbers drifted between screens almost immediately. The fix was a rule, not a smarter query: every consumer reads `WHERE batch_id = MAX(batch_id)`, no exceptions.
- **AI resilience over AI cleverness.** ARIA tries three Gemini models in order and, if every model call fails, falls back to a fully deterministic, database-grounded reply — real numbers, no generation, every time.
- **Bronze never gets corrected.** Cleaning happens in Silver, never in Bronze. If a validation rule later turns out to be wrong, Bronze still holds the untouched original to replay from.
- **The build-arg that cost an afternoon.** The React frontend read its API URL from an env var that Vite bakes in at *build* time, not container start — so the right runtime value shipped with the wrong compiled URL anyway. Fixed by passing it as a Docker build `ARG` instead of a runtime `ENV`.

**Honestly measured:**

| Metric | Value |
|---|---|
| Sustained throughput | ~100 msg/sec (3,000 nodes, 30s interval, zero loss under normal load) |
| Gold-layer freshness | ≤30s, from a sensor event to a queryable SQL Server row |
| Cross-dashboard drift | 0 — enforced structurally by the `batch_id` invariant, not just tested for |
| Deployment | 9 containers, 1 command — `docker compose up -d` |

> **A note on the numbers above:** an earlier version of this README (and my CV) described
> this system at 100,000 simulated houses and sub-second latency. That didn't hold up against
> the actual shipped configuration, so both have been corrected here to the real, verified numbers.

<br>

## Tech Stack

**Languages**
![Python](https://img.shields.io/badge/Python-6F93A6?style=flat-square&logo=python&logoColor=161310&labelColor=161310)
![SQL](https://img.shields.io/badge/SQL-6F93A6?style=flat-square&labelColor=161310)
![C++](https://img.shields.io/badge/C%2B%2B-6F93A6?style=flat-square&logo=cplusplus&logoColor=161310&labelColor=161310)

**Streaming & Big Data**
![Kafka](https://img.shields.io/badge/Apache_Kafka-C9A227?style=flat-square&logo=apachekafka&logoColor=161310&labelColor=161310)
![Spark Structured Streaming](https://img.shields.io/badge/Spark_Structured_Streaming-C9A227?style=flat-square&labelColor=161310)
![Spark](https://img.shields.io/badge/Apache_Spark-6F93A6?style=flat-square&logo=apachespark&logoColor=161310&labelColor=161310)
![Hadoop](https://img.shields.io/badge/Hadoop_HDFS-6F93A6?style=flat-square&logo=apachehadoop&logoColor=161310&labelColor=161310)
![Hive](https://img.shields.io/badge/Hive-6F93A6?style=flat-square&logo=apachehive&logoColor=161310&labelColor=161310)

**Orchestration & Modeling**
![Airflow](https://img.shields.io/badge/Apache_Airflow-6F93A6?style=flat-square&logo=apacheairflow&logoColor=161310&labelColor=161310)
![SSIS](https://img.shields.io/badge/SSIS-6F93A6?style=flat-square&labelColor=161310)
![Star Schema](https://img.shields.io/badge/Star_Schema-6F93A6?style=flat-square&labelColor=161310)
![Snowflake Schema](https://img.shields.io/badge/Snowflake_Schema-6F93A6?style=flat-square&labelColor=161310)

**Databases & Warehousing**
![SQL Server](https://img.shields.io/badge/SQL_Server-6F93A6?style=flat-square&logo=microsoftsqlserver&logoColor=161310&labelColor=161310)
![MongoDB](https://img.shields.io/badge/MongoDB-6F93A6?style=flat-square&logo=mongodb&logoColor=161310&labelColor=161310)

**Backend, BI & Visualization**
![FastAPI](https://img.shields.io/badge/FastAPI-6F93A6?style=flat-square&logo=fastapi&logoColor=161310&labelColor=161310)
![Power BI](https://img.shields.io/badge/Power_BI-6F93A6?style=flat-square&logo=powerbi&logoColor=161310&labelColor=161310)
![Grafana](https://img.shields.io/badge/Grafana-6F93A6?style=flat-square&logo=grafana&logoColor=161310&labelColor=161310)
![React](https://img.shields.io/badge/React-6F93A6?style=flat-square&logo=react&logoColor=161310&labelColor=161310)

**Cloud, DevOps & AI**
![Azure](https://img.shields.io/badge/Azure_Data_Factory-6F93A6?style=flat-square&logo=microsoftazure&logoColor=161310&labelColor=161310)
![Docker](https://img.shields.io/badge/Docker-6F93A6?style=flat-square&logo=docker&logoColor=161310&labelColor=161310)
![Git](https://img.shields.io/badge/Git-6F93A6?style=flat-square&logo=git&logoColor=161310&labelColor=161310)
![Gemini](https://img.shields.io/badge/Google_Gemini_API-C9A227?style=flat-square&labelColor=161310)

<br>

## Other Projects

**Batch ETL Pipeline with Multi-Stage Validation** — coursework-scale — a Spark batch pipeline
rehearsing production patterns: schema validation, layered data-quality checks, and
orchestrated transformations built for idempotent re-runs.

**Enterprise Data Warehouse & BI Platform** — coursework-scale — a star-schema warehouse
consolidating multiple source systems via SSIS, surfaced through Power BI dashboards with
KPI scorecards and drill-through reporting.

*Neither has a public repo linked yet, so no invented metrics are attached to them here.*

<br>

## Currently

`BSc Computer Science` — Obour University *(2024–2028, in progress)*
`Microsoft Data Engineer Track` — Digital Egypt Pioneers Initiative, DEPI *(completed June 2026)*
`ECPC Competitor` — Arab Academy for Science, Technology & Maritime Transport *(ongoing)*

<br>

## GitHub Activity

<div align="center">

<img height="165" src="https://github-readme-stats.vercel.app/api?username=som3a0&show_icons=true&hide_border=true&bg_color=0A0908&title_color=C9A227&icon_color=6F93A6&text_color=ACA495&include_all_commits=true&count_private=true" alt="GitHub Stats"/>
<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=som3a0&layout=compact&hide_border=true&bg_color=0A0908&title_color=C9A227&text_color=ACA495&langs_count=6" alt="Top Languages"/>

</div>

<br>

## Contact

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-6F93A6?style=flat-square&logo=linkedin&logoColor=161310&labelColor=161310)](https://www.linkedin.com/in/ismael-khalifa/)
[![Email](https://img.shields.io/badge/Email-6F93A6?style=flat-square&logo=gmail&logoColor=161310&labelColor=161310)](mailto:ismael.elsayed.khalifa@gmail.com)
[![Portfolio](https://img.shields.io/badge/Portfolio-C9A227?style=flat-square&labelColor=161310)](https://som3a0.github.io/)

</div>
