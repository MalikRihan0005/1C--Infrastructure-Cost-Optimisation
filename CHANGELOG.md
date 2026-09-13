# Changelog

All notable changes, architectural decisions, analytical models, policy assets, and validation milestones for the LendFlow Technologies Infrastructure Cost Optimisation & FinOps Framework are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [Unreleased] - 2026-09-13

### Stage 1: FinOps Foundations & Dataset Familiarisation (Day 1)
- **Added:** Git repository initialisation and standardized enterprise directory hierarchy (`docs/`, `analysis/`, `dashboards/`, `policies/`, `presentation/`, `daily-logs/`, `data/`).
- **Added:** High-fidelity simulated datasets in `data/` covering all 8 specified FinOps telemetry domains:
  - `monthly_cost_summary.csv`
  - `daily_cost_detail.csv`
  - `instance_utilisation.csv`
  - `storage_inventory.csv`
  - `data_transfer_log.csv`
  - `reserved_instance_coverage.csv`
  - `tag_compliance_report.csv`
  - `cost_anomaly_events.csv`
- **Added:** `analysis/billing-analysis.xlsx` detailing 12-month billing trends ($50,000 to $180,000), Month-over-Month growth rates, budget variance (+89.5% overrun), and Pareto spend distribution.
- **Added:** FinOps Lifecycle Framework (Inform → Optimise → Operate) and AWS Well-Architected Cost Optimisation principles.
- **Added:** Stakeholder Priority Matrix aligning Priya Menon (CFO), Arjun Deshmukh (CTO), Ravi Krishnan (VP Eng), Meera Iyer (Compliance), Sanjay Patel (Data Eng), and Anita Sharma (Product).
- **Added:** `daily-logs/day-01.md` log detailing baseline discoveries and exploratory data analysis.
