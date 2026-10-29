# Context: 2-year ML/DS/DE career roadmap (Nov 2026 – 2028)

## About me
- ML engineer at the Institute of Ionosphere: burned-area prediction research
- BSc Data Science (IITU); MSc at KBTU (2026–2028)
- Goal: land an ML/DS/Data Engineering role at a big tech company
- Problem: empty GitHub, few own projects. Need shipped, end-to-end evidence.
- Budget: ~8–10 hrs/week alongside work and study

## How to work with me (learning mode)
My goal is to LEARN these skills, not to collect a repo someone else wrote.
I must be able to explain and rebuild every line in an interview.
- I write the core code myself: data pipelines, features, models, evaluation, API logic
- Before I start a task: explain the concept and the why, point to docs, and
  break it into small steps I can implement
- When I'm stuck: give hints first, then a partial snippet. Give a full
  solution only if I ask for it explicitly
- Review my code like a senior engineer: bugs, design, tests, naming
- You may write boilerplate when I ask (configs, CI YAML, Dockerfile skeletons),
  but walk me through every non-obvious line
- Never generate whole modules or the whole project unprompted
- Ask me questions that check my understanding (e.g. "why this metric?")
- I make the design decisions. You propose options with trade-offs.
- I write the README and docs myself. You review them.

## Conflict of interest
At the institute I work on burned-area / fire-spread prediction. Personal
projects must stay away from wildfire and burned-area topics and must not
use institute data, code or methods.

## ML lifecycle I want to learn by building
1. Problem framing (business metric, baseline)
2. Data pipelines (ingestion, cleaning, warehouse, quality tests)
3. Experimentation (tracked, reproducible runs)
4. Evaluation (offline metrics, slice checks, A/B or shadow)
5. Deployment (Docker, API/batch, CI/CD)
6. Monitoring (data/prediction drift, latency, cost)
7. Retraining loop

## Roadmap
**Phase 0: Foundations (Nov–Dec 2026)**
Git workflow (branches, PRs), Linux, Docker, SQL (CTEs, window functions),
Python as a package + pytest. Output: one clean repo with tests + Dockerfile.

**Phase 1: End-to-end ML system (Jan–Jun 2027)**
Almaty air quality: forecast PM2.5 24–48 h ahead per station/district
from open data (OpenAQ sensors + Open-Meteo weather). Baseline is persistence
and a seasonal profile. Metrics: MAE per horizon, recall on hazardous hours.
Slices: season (heating vs. non-heating), hour, station. The heating season
gives real drift, which makes monitoring and retraining meaningful.
- Scheduled hourly ingestion (Prefect or Airflow)
- DVC (data versioning) + MLflow (experiment tracking)
- FastAPI model service in Docker
- GitHub Actions CI/CD
- Evidently drift monitoring + retraining trigger
- Alerts when the forecast crosses a hazardous level
- Deployed on home lab server or cloud free tier
Guide: DataTalksClub MLOps Zoomcamp

**Phase 2: Data engineering + cloud (Jul–Dec 2027)**
Batch pipeline into a warehouse (Postgres/BigQuery) + dbt + orchestration
+ data quality tests; Spark/Kafka if justified. One cloud (AWS or GCP),
maybe a cert, Kubernetes basics. Pick lane (MLE / DE / DS) by mid-2027.
Guide: DataTalksClub Data Engineering Zoomcamp

**Phase 3: System design, LLM project, applications (2028)**
LLM/RAG project with evals + serving; clean up thesis repo (lung-cancer CT
detection) with reproducible training. Interview prep: DSA, ML system design,
behavioral stories. Apply for internships in autumn 2027 for summer 2028.

## Reading
- Designing Machine Learning Systems (Chip Huyen)
- Made With ML (Goku Mohandas)
- Designing Data-Intensive Applications (Martin Kleppmann)

## Rules
- Push something to GitHub every week
- Every project: README with problem, architecture diagram, how to run, lessons learned
- Depth over count: 3 deployed + monitored systems > 15 notebooks

## Current step
Switch the project from burned area to Almaty air quality:
1. Rename the local repo and the GitHub repo (e.g. `almaty-air-quality`, private for now)
2. Explore OpenAQ: which stations/sensors exist in Almaty, their history and gaps
3. I write the one-page README myself (problem, data sources, baseline and
   metrics, target architecture), and Claude reviews it