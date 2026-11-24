<p align="center">
  <img src="docs/images/banner-light.png" alt="Fintestix: Check financial models before they make decisions. Beside the title, the Threshold Lab on the ULB credit card fraud dataset shows the selected threshold 0.990 with 80 fraud cases caught, 18 missed and 2 false alarms.">
</p>

<p align="center">
  <img src="https://img.shields.io/github/last-commit/renaissancenath/Finetestix?color=0B5D4B&label=last%20commit" alt="Last commit">
  <img src="https://img.shields.io/badge/license-all%20rights%20reserved-0B5D4B" alt="All rights reserved">
  <br>
  <img src="https://img.shields.io/badge/Python_3.12-0B5D4B?logo=python&logoColor=white" alt="Python 3.12">
  <img src="https://img.shields.io/badge/FastAPI-0B5D4B?logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/PostgreSQL_16-0B5D4B?logo=postgresql&logoColor=white" alt="PostgreSQL 16">
  <img src="https://img.shields.io/badge/SQLAlchemy_2-0B5D4B?logo=sqlalchemy&logoColor=white" alt="SQLAlchemy 2">
  <img src="https://img.shields.io/badge/scikit--learn-0B5D4B?logo=scikitlearn&logoColor=white" alt="scikit-learn">
  <img src="https://img.shields.io/badge/LightGBM_%C2%B7_XGBoost-0B5D4B" alt="LightGBM and XGBoost">
  <img src="https://img.shields.io/badge/pandas-0B5D4B?logo=pandas&logoColor=white" alt="pandas">
  <img src="https://img.shields.io/badge/Jupyter-0B5D4B?logo=jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/React_18-0B5D4B?logo=react&logoColor=white" alt="React 18">
  <img src="https://img.shields.io/badge/TypeScript-0B5D4B?logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Tailwind-0B5D4B?logo=tailwindcss&logoColor=white" alt="Tailwind CSS">
  <img src="https://img.shields.io/badge/Playwright-0B5D4B?logo=playwright&logoColor=white" alt="Playwright">
  <img src="https://img.shields.io/badge/Docker-0B5D4B?logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/GitHub_Actions-0B5D4B?logo=githubactions&logoColor=white" alt="GitHub Actions">
</p>

<p align="center">
  <b>Fintestix checks financial datasets, models and decision rules, and shows the evidence behind every finding.</b><br>
  <a href="#see-it">See it</a> ·
  <a href="#how-it-works">How it works</a> ·
  <a href="#architecture">Architecture</a> ·
  <a href="#measured-results">Results</a> ·
  <a href="#engineering">Engineering</a>
</p>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/images/at-a-glance-dark.png">
  <img src="docs/images/at-a-glance-light.png" alt="At a glance: 81.6% of fraud caught at 97.6% precision on the full ULB dataset; PR-AUC 0.886; 99 of 100 planted defects found with 0 false alarms; 152 automated tests; metrics match scikit-learn to 6 decimals; $0 running cost.">
</picture>

<p align="center"><img src="docs/images/walkthrough.gif" width="880" alt="Recorded from the running app: landing page, sign in, data upload with column mapping, data health findings, model performance, the Threshold Lab moving with the keyboard, fault findings, rule test results and a change simulation."></p>

## The problem

A fraud model can score 99.8% accuracy while catching almost no fraud, because fraud is 0.17% of transactions. Columns that are only known after the outcome make models look better than they are. Business rules quietly conflict. **Fintestix tests all of this on your data and shows the proof for every finding.**

## See it

<table>
<tr>
<th width="50%">Threshold Lab</th>
<th width="50%">Model performance</th>
</tr>
<tr>
<td><img src="docs/images/threshold-lab.png" alt="Threshold Lab: precision, recall and F1 by threshold with the selected line and a readout of missed fraud, false alarms and alert volume"></td>
<td><img src="docs/images/performance.png" alt="Performance page: PR-AUC 0.886, ROC-AUC 0.979, precision and recall with prevalence stated next to every rate"></td>
</tr>
<tr>
<td>Move the threshold and see missed fraud, false alarms and alert volume before choosing.</td>
<td>Every rate is shown with the prevalence it depends on. Metrics that cannot be computed say so.</td>
</tr>
<tr>
<th>Fault Checker</th>
<th>Decision rules against an independent oracle</th>
</tr>
<tr>
<td><img src="docs/images/faults.png" alt="Fault Checker findings grouped by stage, each with severity, confidence and a link to its evidence"></td>
<td><img src="docs/images/rule-results.png" alt="Rule test results: pass rate 98.1%, 10 missed fires found at a planted boundary error, boundary coverage 4 of 4 requirements"></td>
</tr>
<tr>
<td>Leakage is confirmed by retraining without the column, not guessed.</td>
<td>Expected decisions come from the written requirements, never from the rule code.</td>
</tr>
<tr>
<th>Change simulator</th>
<th>Sign-up with an emailed code</th>
</tr>
<tr>
<td><img src="docs/images/simulate.png" alt="Change simulator listing what got worse first, then original, simulated and difference for every metric"></td>
<td><img src="docs/images/signup-code.png" alt="Sign-up page asking for the 6-digit code sent by email, with a link to send a new code"></td>
</tr>
<tr>
<td>Try a threshold, rule, feature or model change without touching the original.</td>
<td>A 6-digit code confirms the email before the first sign-in. Free plan included.</td>
</tr>
</table>

## How it works

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/images/how-it-works-dark.png">
  <img src="docs/images/how-it-works-light.png" alt="Ten steps: upload with SHA-256 checks, map columns, configure the task, data health, train or upload a model, Threshold Lab, Fault Checker, rules against an oracle, simulate a change, and a sealed receipt with an Excel report.">
</picture>

## Architecture

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/images/architecture-dark.png">
  <img src="docs/images/architecture-light.png" alt="The browser talks to one FastAPI service with middleware, auth, routers, plans, a run queue in PostgreSQL and workers that scale out. Data lives in PostgreSQL 16 and object storage; GlitchTip and SMTP are attached.">
</picture>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/images/inside-the-backend-dark.png">
  <img src="docs/images/inside-the-backend-light.png" alt="A training run in ten steps: middleware, session, CSRF and limits, project membership, validation, queue with audit, worker claim with SKIP LOCKED, child process with limits, engines, and a sealed result.">
</picture>

<table>
<tr>
<td width="50%"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/images/data-model-dark.png"><img src="docs/images/data-model-light.png" alt="Data model: 24 PostgreSQL tables grouped into accounts, data, runs and results, append-only receipts and audit log, and operations."></picture></td>
<td width="50%"><picture><source media="(prefers-color-scheme: dark)" srcset="docs/images/security-dark.png"><img src="docs/images/security-light.png" alt="Security layers: browser, edge and API, identity and data, and files, models and results, plus supply chain and change control."></picture></td>
</tr>
</table>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/images/delivery-dark.png">
  <img src="docs/images/delivery-light.png" alt="From commit to users: pull request, quality gate, migration guard, engineer review; production errors flow back through a triage job to a GitHub issue and a fix pull request.">
</picture>

## Measured results

Full ULB credit card fraud dataset: 284,807 real transactions, stratified test split of 56,962, prevalence 0.172%. The test split is never used for training or tuning. Full write-up: [docs/RESULTS.md](docs/RESULTS.md).

| Model | PR-AUC | ROC-AUC | Best F1 | Fraud caught | Alerts that are fraud |
|---|---:|---:|---:|---:|---:|
| Logistic regression | 0.718 | 0.971 | 0.703 | 84.7% | 60.1% |
| Random forest | 0.862 | 0.966 | 0.868 | 83.7% | 90.1% |
| XGBoost | 0.881 | 0.975 | 0.871 | 82.7% | 92.0% |
| **LightGBM** | **0.886** | **0.979** | **0.889** | 81.6% | **97.6%** |

<p align="center"><img src="docs/images/pr-curves.png" width="680" alt="Precision-recall curves for the four models on the ULB test split; LightGBM is highest with PR-AUC 0.886; the prevalence line sits at 0.0017."></p>

Accuracy is 99.96% for LightGBM, but a model that flags nothing already scores 99.83%, so the app leads with PR-AUC, recall and precision. On German Credit (1,000 applicants) accuracy is 74 to 75% against a 70% baseline, which is typical for that dataset.

The Fault Checker found **99 of 100** defects planted in copies of real data (leakage, train-test contamination, flipped labels, numbers stored as text, bad thresholds, broken prediction files, rule misfires) with **0 false alarms** on the clean data.

## Engineering

<details>
<summary><b>Stack, security, tests and CI</b></summary>

| Area | What's in place |
|---|---|
| **Backend** | FastAPI, Pydantic v2, SQLAlchemy 2, Alembic, PostgreSQL 16. Business logic in plain services with no web framework imports |
| **Machine learning** | pandas, scikit-learn, XGBoost, LightGBM, imbalanced-learn. Preprocessing fit on training data only; stratified, temporal and group splits; tuning on training folds only; every metric checked against scikit-learn |
| **Jobs** | Run queue in PostgreSQL with `SKIP LOCKED`; each run in its own process with memory and CPU limits, heartbeat and cancel; more workers can be added without code changes |
| **Frontend** | React 18, strict TypeScript, Vite, Tailwind on design tokens, Radix primitives, Recharts with a table view for every chart. Light and dark themes meet WCAG 2.2 AA |
| **Auth** | Argon2id passwords, server-side sessions with hashed tokens, CSRF tokens, lockout, rate limits, 6-digit email code at sign-up, optional authenticator 2FA |
| **Security** | Strict CSP, project membership on every query, magic-byte upload checks, zip-bomb guard, no pickle or code execution, rules interpreted from JSON, append-only receipts and audit log, least-privilege database roles |
| **Plans** | Free and Pro plans with limits enforced on the server |
| **Tests** | 97 backend tests on PostgreSQL (auth, CSRF on every route, cross-project access, database grants, uploads, metrics, rules, defects), 53 frontend tests including colour contrast for every token pair, 2 browser end-to-end runs with accessibility checks at 375, 768 and 1280 px |
| **CI on every pull request** | Lint, types, tests with coverage gates, Bandit, Semgrep, pip-audit, npm audit, gitleaks, licence check, API breaking-change check, Docker build, browser walkthroughs |
| **Safe migrations** | Destructive SQL fails CI unless it names a recorded approval and the pull request carries an approval label; the app's database role cannot drop or truncate |
| **Production errors** | GlitchTip with personal data scrubbed; a triage job groups errors and in-app bug reports into GitHub issues |

Write-ups: [Architecture](docs/ARCHITECTURE.md) · [Security](docs/SECURITY.md) · [Results](docs/RESULTS.md) · [API reference](docs/api/openapi.json)

</details>

## Honest limitations

- Results are on historical public datasets. Fintestix is not connected to any bank and makes no compliance claims.
- IEEE-CIS and Home Credit allow only non-commercial use; Fintestix never ships those files, users upload data they are allowed to use.
- The free hosting tier sleeps when idle, so the first request after a quiet period is slow.
- Online payment for the Pro plan is planned; for now an admin upgrades accounts.

## About the source code

This repository is the public overview of Fintestix. The source code (backend, analysis engines, web app, tests, notebooks and CI) is in a private repository. If you are reviewing my work for a role, open an issue or message me through my GitHub profile and I will give you read access or walk you through the code.

## Licence

All rights reserved. The text, diagrams and screenshots here may be viewed on GitHub; any other use needs written permission. See [LICENSE](LICENSE).
