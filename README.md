# ☁️ Azure Infrastructure Foundation - Hessler Logistik GmbH

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Last commit](https://img.shields.io/github/last-commit/rubak714/azure-iac-foundation)
![Stars](https://img.shields.io/github/stars/rubak714/azure-iac-foundation?style=social)
![Issues](https://img.shields.io/github/issues/rubak714/azure-iac-foundation)
![Built with Bicep](https://img.shields.io/badge/IaC-Azure%20Bicep-0078D4?logo=microsoftazure)
![AZ-104 Aligned](https://img.shields.io/badge/AZ--104-aligned-green)

---

> A lot of people are using AI to generate portfolios right now.
> I am doing something different.
> I am currently studying full time for AZ-104 and CompTIA Security+.
> This project is part of that preparation. I build it alongside my studies, step by step.
> Every command here I actually ran. Every bug documented here I actually hit.
> Every screenshot was taken by me from my own Azure account.
> This is not a generated walkthrough. This is me learning in public and proving it.

---

> **Status:** In progress. I am currently studying full time for **AZ-104 and CompTIA Security+**.
> I build this project in parallel with my studies, module by module.
> The commit history reflects the real pace of that work.

---

## ☁️ What is this project

**The company:** Hessler Logistik GmbH. Fictional. 30 people. Freight forwarding. Frankfurt.
They have been running on an old on-premises Windows Server for years and are now moving their first workloads to Azure.

**The role I am playing:** Junior cloud admin. Hired to set up the foundation before anyone else deploys anything.

**The problem:** Most tutorials skip this part. They jump straight to deploying VMs and databases because that is more exciting to watch. But skipping the foundation is exactly *what causes runaway costs, audit failures, and naming chaos six months later*.

**What I am doing instead:** Building the foundation first.

> Clean resource group structure. Naming convention. Mandatory tags. RBAC with least privilege. Azure Policy guardrails. All of it in **Bicep** so it deploys with one command, *not a hundred portal clicks*.
