# Changelog

All notable changes, architectural decisions, analytical models, policy assets, and validation milestones for the LendFlow Technologies Infrastructure Cost Optimisation & FinOps Framework are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [Unreleased] - 2026-09-13

### Stage 1: FinOps Foundations & Dataset Familiarisation (Day 1)
- **Added:** Git repository initialisation and standardized enterprise directory hierarchy (`docs/`, `analysis/`, `dashboards/`, `policies/`, `presentation/`, `daily-logs/`, `data/`).
- **Added:** High-fidelity simulated datasets in `data/` covering all 8 specified FinOps telemetry domains.
- **Added:** `analysis/billing-analysis.xlsx` detailing 12-month billing trends ($50,000 to $180,000) and Pareto distribution.
- **Added:** Stakeholder Priority Matrix and `daily-logs/day-01.md`.

### Stage 2: Compute & Database Analysis (Day 2)
- **Added:** Resource-level telemetry profiling of 41 EC2 compute instances and 12 database/caching clusters.
- **Identified:** 28 instances (68.3%) with sustained CPU <20%; immediate termination of 2 abandoned sandboxes ($1,042.56/mo waste).
- **Designed:** Automated non-production scheduling (9 AM - 7 PM weekdays) reducing non-prod compute hours by 69.4% ($8,200/mo savings).
- **Consolidated:** RDS reporting read-replica decommissioned in favor of S3/Athena lake ($1,411.20/mo savings); staging RDS converted to Single-AZ Graviton ($1,091.20/mo savings).
- **Built:** `analysis/savings-model.xlsx` featuring `Executive Summary`, `Compute Analysis`, and `Database Analysis` tabs.
- **Published:** `daily-logs/day-02.md`.

### Stage 3: Storage & Data Transfer Analysis (Day 3)
- **Added:** S3 lifecycle policy framework transitioning 145 TB of dormant KYC loan docs (>90d inactive) to Glacier Instant Retrieval ($1,850/mo savings) and audit logs to Glacier with WORM Object Lock ($1,250/mo savings).
- **Remediated:** 4 unattached orphan EBS volumes (7,500 GB) deleted ($750/mo savings); 32,000 GB of attached GP2 converted to GP3 ($650/mo savings); DLM 30d snapshot retention policy enforced ($1,000/mo savings).
- **Eliminated:** $7,560/mo in avoidable NAT Gateway data processing fees via AWS S3 Gateway VPC Endpoints.
- **Remediated:** Cross-AZ inter-service chatter via AZ-affinity topology-aware routing ($2,920/mo savings).
- **Appended:** `Storage Analysis` and `Data Transfer Analysis` tabs to `analysis/savings-model.xlsx`.
- **Published:** `daily-logs/day-03.md`.

### Stage 4: Reserved Capacity & Spot Strategy (Day 4)
- **Audited:** 0.0% baseline RI/SP coverage across all 65 compute instances and 12 database clusters.
- **Designed:** 1-Year Partial Upfront Compute Savings Plan ($18,000 upfront, 1.23-month payback) yielding $14,600/mo savings on steady-state production compute, plus $2,822.40/mo on RDS Reserved Instances.
- **Architected:** Diversified Spot Fleets across 12 independent capacity pools (capacity-optimized allocation) with 20% on-demand base for asynchronous batch OCR and ETL pipelines ($4,000/mo savings).
- **Modeled:** Spot interruption sensitivity across 5%, 10%, and 20% scenarios; verified sub-page S3 checkpointing keeps reprocessing overhead <$130/mo.
- **Published:** `docs/ri-spot-strategy.md` and appended `Commitment & Spot` tab to `analysis/savings-model.xlsx`.
- **Published:** `daily-logs/day-04.md`.

### Stage 5: Tagging & Cost Allocation Governance (Day 5)
- **Audited:** 58.2% baseline tag compliance in `data/tag_compliance_report.csv`, identifying $75,420.00/month in unallocated dark spend.
- **Designed:** Enterprise 10-tag mandatory taxonomy (`business_unit`, `product`, `environment`, `cost_centre`, `team`, `service`, `created_by`, `ttl`, `compliance_scope`, `data_classification`).
- **Engineered:** 4-layer governance model (Preventive, Detective, Corrective, Audit & Showback) and proportional shared-cost allocation math.
- **Authored:** `policies/scp-mandatory-tags.json` and `policies/config-rules.yaml`.
- **Published:** `docs/tagging-taxonomy.md` and `daily-logs/day-05.md`.

### Stage 6: Cost Anomaly Detection (Day 6)
- **Audited:** 10 historical anomaly incidents in `data/cost_anomaly_events.csv` generating $31,512.80 in waste with average MTTD of 156.6 hours (6.5 days).
- **Designed:** Hybrid 3-tier detection framework (Sub-hour CloudWatch proxy alarms, Lambda Modified Z-Score with salary-day surge awareness, and AWS ML Cost Anomaly Detection).
- **Established:** 4-tier severity matrix (P1 Critical through P4 Low) with SLAs, automated PagerDuty/Slack routing, and 5-step operational Anomaly Investigation Runbook.
- **Published:** `docs/anomaly-detection.md` and `daily-logs/day-06.md`.

### Stage 7: Consolidated Cost Audit & Savings Model (Day 7)
- **Synthesised:** Master AWS Cost Audit Report (`docs/cost-audit-report.md`) detailing baseline spend ($180,000/mo), gross waste ($70,850/mo), net savings waterfall ($64,250/mo), and 90-day realization timeline.
- **Engineered:** Catalog of 16 prioritized optimisation recommendations (`docs/optimisation-recommendations.md`) complete with technical solutions, compliance assessments, and Impact vs Effort matrix.
- **Reconciled:** Probabilistic scenario modeling in `analysis/savings-model.xlsx` (Expected: $64,250/mo; Best-Case: $71,800/mo; Worst-Case: $56,400/mo).
- **Published:** `docs/cost-audit-report.md`, `docs/optimisation-recommendations.md`, and `daily-logs/day-07.md`.

### Stage 8: Auto-Scaling Architecture (Day 8)
- **Architected:** Asymmetric auto-scaling framework (60s scale-out cooldown, 300s-600s scale-in cooldown, 60s ELB connection draining) across 6 core microservices.
- **Deployed:** Predictive and scheduled scaling for borrower salary-day spikes (1st and 15th of the month) pre-warming capacity to eliminate transaction drop-offs.
- **Implemented:** Scheduled scaling for development and staging fleets (9 AM - 7 PM weekdays, stopped on weekends) capturing $8,200.00/month in idle compute waste.
- **Authored:** `policies/auto-scaling-loan-api.json`, `policies/auto-scaling-batch-ocr.json`, and `policies/auto-scaling-scheduled-dev.json`.
- **Published:** `docs/auto-scaling-policies.md` and `daily-logs/day-08.md`.
