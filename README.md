# IT Audit: User Access Control Analysis & Risk Dashboard

[![Power BI](https://img.shields.io/badge/Power_BI-Desktop-F2C811?logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![Microsoft Excel](https://img.shields.io/badge/Microsoft_Excel-Dataset-217346?logo=microsoftexcel&logoColor=white)](https://www.microsoft.com/excel)
[![DAX](https://img.shields.io/badge/Analytics-DAX-blue)](https://docs.microsoft.com/dax/)
[![Audit Domain](https://img.shields.io/badge/Domain-IT_Audit_%7C_GRC_%7C_SOX-navy)](https://en.wikipedia.org/wiki/Information_technology_audit)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An end-to-end IT Audit review evaluating **User Access Management (UAM)** and **Information Technology General Controls (ITGC)** across core enterprise systems. This project models an audit engagement that tests access provisioning, inactive account governance, and post-termination deprovisioning using risk scoring methodologies (5×5 Likelihood × Impact matrix) and interactive Power BI audit dashboards.

---

## 📌 Executive Summary & Business Problem

In enterprise environments, user access control failures represent one of the leading vectors for unauthorized transactions, data breaches, and regulatory non-compliance under frameworks such as **SOX (Sarbanes-Oxley Act - Section 404)** and **ISO 27001**. 

Organizations frequently struggle with:
1. **Orphaned and Inactive Accounts**: Employees who retain system access long after departing or stopping active use.
2. **Delayed Deprovisioning**: Communication lags between Human Resources (HR) and IT identity management teams.
3. **Privileged Access Sprawl**: Insufficient monitoring of elevated rights across high-impact business systems (ERP, SAP, CRM, HRIS).

This project performs an independent audit testing of **2,398 enterprise user accounts** to identify control exceptions, calculate risk exposure scores, and present management-ready reporting.

---

## 🎯 Audit Objectives & Scope

The audit evaluated whether identity and access governance controls operate effectively across the user lifecycle:

- **Provisioning Controls**: Verify that accounts are appropriately authorized and mapped to legitimate job functions.
- **Deprovisioning Controls (Termination)**: Validate that system access is revoked immediately upon employee termination.
- **Inactive Account Governance**: Identify dormant and never-logged-in accounts for timely deactivation.
- **Privileged Access Governance**: Ensure elevated privileges are restricted and subject to enhanced audit scrutiny.

### Enterprise Systems in Scope
- **ERP_System** (Enterprise Resource Planning - Core Financials)
- **SAP_System** (Supply Chain & Operations)
- **CRM_System** (Customer Relationship Management & Sales)
- **HR_System** (Human Resources Information System)

---

## 📊 Risk Scoring Methodology

To prioritize findings consistently, audit exceptions were evaluated using a standardized **5 × 5 Risk Matrix** combining **Impact** and **Likelihood**:

$$\text{Risk Score} = \text{Impact Score} \times \text{Likelihood Score}$$

Exceptions are classified into four risk categories:
- 🟢 **Low Risk**: Minor administrative anomalies with low exposure.
- 🟡 **Medium Risk**: Inactive accounts requiring scheduled deprovisioning.
- 🟠 **High Risk**: Control deficiencies with elevated exposure in standard systems.
- 🔴 **Critical Risk**: Unrevoked active access for terminated staff or elevated access in critical financial systems (ERP).

### Exception Definitions (Mini Glossary)
| Issue Type | Definition | Risk Severity |
| :--- | :--- | :--- |
| **Dormant Account** | Account inactive for an extended period without login, yet remaining active in the identity directory. | Medium / High |
| **Never Logged In** | Account provisioned but never utilized by the user since creation. | Low / Medium |
| **Post-Termination Access** | A former employee account that retained active access permissions past the effective termination date. | High / Critical |
| **Terminated but Active** | Employee marked as terminated in HR records whose system account status remains enabled. | Critical |
| **Privileged Access** | Accounts holding administrative or elevated permissions presenting severe blast radius if compromised. | High / Critical |

---

## 📈 Dashboard Walkthrough & Audit Evidence

The interactive Power BI report (`IT Audit.pbix`) is organized into four core analytical views:

### 1. Executive Risk Overview
Presents high-level metrics for executive leadership and the Audit Committee, summarizing total population exposure, risk level distribution, and primary issue drivers.

![Executive Risk Overview](./Executive%20Risk%20Overview.PNG)

*Key Insights Shown:*
- **Active Users & Total Employees With Access** across systems.
- **1,065 Total Exceptions Identified** across the reviewed population.
- **Dormant Accounts (42%)** represent the largest individual volume of control failures.
- **Termination-Related Exposure (36%)** represents the highest security and compliance vulnerability.
- **8% of the User Population** holds elevated/privileged access requiring targeted oversight.

---

### 2. Access Control Risk Analysis & Key Drivers
Drills into root causes, analyzing risk distribution by system type, access tier, and control failure mechanism.

![Access Control Analysis](./Access%20control%20Analysis.PNG)

*Key Insights Shown:*
- **ERP System Concentration**: The ERP system concentrates **85% of all High-Risk access violations**, representing a critical financial control weakness.
- **Standard User Drivers**: High-risk exposure is predominantly driven by standard accounts rather than administrators alone, indicating pervasive deprovisioning gaps rather than isolated admin errors.
- **Volume Breakdown**: Clear breakdown of exceptions by system (ERP, SAP, CRM, HRIS).

---

### 3. Detailed Findings & Audit Evidence
Provides auditable, line-by-line evidence supporting the testing results. Serves as working paper documentation for external auditors and remediation owners.

![Detailed Exceptions](./Detailed%20Exceptions.PNG)

*Key Insights Shown:*
- Granular record-level evidence: User ID, Account Status, Risk Category, Risk Score, Testing Result (Pass/Fail), Control Status, Hire Date, Termination Date, and Last Login Date.
- Real-time exception filtering by risk level: Critical, Medium, and Low.
- Actionable exception register facilitating direct dispatch to system administrators.

---

### 4. Risk Scoring Methodology & Treatment
Documents the underlying risk evaluation model, calculation guidelines, and treatment protocols for each exception class.

![Risk Scoring Methodology](./Risk%20scoring%20methodology.PNG)

*Key Insights Shown:*
- Transparent documentation of the 5×5 Impact × Likelihood scoring framework.
- Audit definitions and treatment strategies mapped directly to exception categories.

---

## 🚨 Key Audit Findings

From testing **2,398 user accounts**, a total of **1,065 access control exceptions** were identified (an overall exception rate of **44.4%**):

| Audit Finding Category | Record Count | % of Exceptions | Audit Observation |
| :--- | :---: | :---: | :--- |
| **Dormant Accounts** | **448** | **42.1%** | Accounts with extended inactivity remaining enabled; represents the highest volume issue. |
| **Never Logged In** | **228** | **21.4%** | Over-provisioned accounts created upon onboarding that were never utilized. |
| **Post-Termination Access** | **196** | **18.4%** | Terminated personnel retaining system access post-departure; severe compliance violation. |
| **Terminated but Active** | **193** | **18.1%** | Terminated in HR system but marked active in target application directories. |
| **Total Non-Compliant Accounts** | **1,065** | **100.0%** | **Comprehensive finding requiring prioritized remediation.** |

### Critical Governance Observations
1. **Severe Termination Deprovisioning Gaps**: A combined **389 accounts (36.5% of all exceptions)** involved terminated employees retaining system access or active status.
2. **ERP High-Risk Concentration**: **85% of high-risk violations** are concentrated within the ERP system, directly threatening financial reporting integrity (SOX ITGC scope).
3. **Privileged Account Exposure**: 8% of users hold elevated administrative privileges, several of which had dormant or unmonitored statuses.

---

## ⚠️ Risk Implications & SOX Impact

Failure to enforce stringent access controls exposes the organization to significant operational and regulatory risks:

- **Unauthorized Financial Transactions**: Delayed deprovisioning in the ERP system allows former or unmonitored users to post fraudulent or erroneous journal entries.
- **Data Exfiltration & Breaches**: Inactive and unrevoked accounts provide untracked entry points for malicious insiders or external attackers.
- **SOX 404 Material Weakness / Deficiency**: Ineffective user access deprovisioning and periodic reviews constitute an ITGC control failure, potentially resulting in adverse external audit findings.

---

## ✅ Audit Recommendations & Management Action Plan

| Priority | Remediation Recommendation | Responsible Owner | Target Timeline |
| :---: | :--- | :--- | :--- |
| 🔴 **P1** | **Immediate Revocation**: Immediately disable and revoke all 389 terminated employee accounts across ERP, SAP, CRM, and HR systems. | IT Identity Admin / System Owners | 24 - 48 Hours |
| 🔴 **P1** | **Automate Offboarding**: Establish automated API integrations between HR Information Systems (HRIS) and Active Directory/Identity Provider (IdP) for zero-delay deprovisioning. | IT Operations & HR Engineering | 30 Days |
| 🟠 **P2** | **Dormant Account Deactivation Policy**: Implement an automated policy disabling accounts inactive for >90 days and deprovisioning accounts never logged into after 30 days. | IT Security / GRC | 45 Days |
| 🟠 **P2** | **Periodic Access Reviews (PAR)**: Institute mandatory quarterly access recertification for business managers, prioritizing financial systems (ERP/SAP). | Internal Audit / Compliance | Quarterly |
| 🟡 **P3** | **Privileged Access Management (PAM)**: Deploy privileged session logging, multi-factor authentication (MFA), and just-in-time access for elevated ERP and SAP roles. | Information Security | 60 Days |

---

## 🛠️ Technology Stack & Prerequisites

- **Business Intelligence & Reporting**: [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/) (Report file: `IT Audit.pbix`)
- **Data Analysis Expressions (DAX)**: Custom measures for dynamic risk scoring, exception counting, and KPI aggregations
- **Data Source**: [Microsoft Excel](https://www.microsoft.com/excel) (`Access Management (HR Dataset).xlsx`)
- **Data Modeling**: Star/Tabular data model linking user attributes, system roles, risk matrices, and audit flags

*No additional programming runtimes (Python, Node.js, SQL databases) are required to view or interact with this project.*

---

## 📂 Repository Structure

```text
IT-Audit-User-Access-Control-Analysis/
│
├── IT Audit.pbix                         # Power BI dashboard report (4 interactive pages)
├── Access Management (HR Dataset).xlsx   # Cleaned audit testing dataset (2,398 records)
│
├── Access control Analysis.PNG           # Dashboard Page: Risk drivers and system breakdown
├── Detailed Exceptions.PNG               # Dashboard Page: Audit evidence and sample records
├── Executive Risk Overview.PNG           # Dashboard Page: Executive summary & high-level KPIs
├── Risk scoring methodology.PNG          # Dashboard Page: 5x5 matrix & glossary
│
├── README.md                             # Comprehensive audit report and documentation
└── .gitignore                            # Git ignore file for Excel/Power BI temporary files
```

---

## 📋 Dataset Schema & Data Dictionary

The audit testing dataset (`Access Management (HR Dataset).xlsx`) contains **2,398 records** across two worksheets (`Clean Audit Data` and `Sheet1`):

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `User_ID` | Text | Unique identifier assigned to the user account (e.g., `U001` - `U2398`). |
| `Employee_Name` | Text | Anonymized employee name. |
| `Department` | Text | Organizational department (Finance, IT, Sales, Procurement, Legal, etc.). |
| `Job_Title` | Text | Role title within the organization. |
| `System_Name` | Text | Target system evaluated (`ERP_System`, `SAP_System`, `CRM_System`, `HR_System`). |
| `Role_Name` | Text | System role assigned (e.g., `ERP_Admin`, `ERP_User`, `SAP_Admin`, etc.). |
| `Access_Level` | Text | Permissions tier assigned to the account (`Standard`, `Privileged`, etc.). |
| `Account_Status` | Text | Directory account status (`Active`, `Inactive`). |
| `Hire_Date` | Date | Employee onboarding / hire date. |
| `Termination_Date` | Date | Employee departure date (null for active employees). |
| `Last_Login_Date` | Date | Timestamp of most recent system authentication (null for never logged in). |
| `Manager` | Text | Reporting manager field. |
| `Privileged_Acess (Yes/No)` | Text | Binary flag indicating whether the role grants elevated administrative access. |
| `Audit_Flag` | Text | Audit testing result (`OK`, `Dormant Account`, `Never Logged In`, `Post-Termination Access`, `Terminated but Active`). |

---

## 🚀 How to Open and Review the Dashboard

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Jash275/IT-Audit-User-Access-Control-Analysis.git
   cd IT-Audit-User-Access-Control-Analysis
   ```
2. **Open the Power BI Report**:
   - Ensure [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/) is installed.
   - Double-click `IT Audit.pbix`.
3. **Interact with the Visuals**:
   - Use the slicers on each page to filter by Department, System, Access Level, and Risk Category.
   - Review audit evidence in the **Detailed Exceptions** tab.

---

## 💡 Key Audit & GRC Skills Demonstrated

- **IT General Controls (ITGC) Testing**: Practical application of access control testing methodologies.
- **Access Governance & Deprovisioning Review**: Identification of dormant accounts, orphaned identities, and delayed terminations.
- **Risk Assessment & Scoring**: Development of defensible 5×5 risk rating models aligned with internal control frameworks.
- **Data Storytelling & Executive Reporting**: Designing clean, executive-ready Power BI visuals bridging IT operations and audit leadership.
- **Audit Documentation & Working Papers**: Maintaining trace evidence connecting raw HR data to testing conclusions.

---

## ⚠️ Disclaimer

This repository utilizes synthetic and anonymized sample data curated specifically for demonstration and educational purposes. No confidential employee records, real credentials, or proprietary corporate data are included.
