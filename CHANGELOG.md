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
