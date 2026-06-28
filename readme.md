# 🤖 AI-Powered Invoice Processing Automation

<p align="center">

![UiPath](https://img.shields.io/badge/UiPath-RPA-orange)
![Document Understanding](https://img.shields.io/badge/AI-Document%20Understanding-blue)
![Event Driven](https://img.shields.io/badge/Architecture-Event--Driven-success)
![Action Center](https://img.shields.io/badge/Human--in--the--Loop-Action%20Center-purple)
![License](https://img.shields.io/badge/License-MIT-green)

</p>

An enterprise-grade **UiPath Intelligent Document Processing (IDP)** solution that automatically processes incoming invoice emails, extracts invoice information using **UiPath Document Understanding**, validates uncertain fields through **UiPath Action Center**, and consolidates all processed invoices into a centralized Excel report.

The project demonstrates enterprise automation practices including event-driven processing, reusable workflows, external configuration, automated Orchestrator initialization, structured logging, and human-in-the-loop validation.

---

# 📦 Repository Contents

```text
Data/
DocumentProcessing/
Documentation/
Framework/
QuickStart/
Main-AiInvoiceProcessing.xaml
Main-ActionCenter.xaml
GetMailInfo.xaml
README.md
LICENSE
```

---

# 🎥 Demonstration

Refer to Documentation/ to watch the demonstration video.

---

# 🚀 Features

* Event-driven invoice processing
* Gmail integration
* Automatic attachment download
* AI-powered invoice extraction
* Human validation with UiPath Action Center
* Automatic Excel reporting
* Automated Orchestrator environment initialization
* External configuration templates
* Modular workflow architecture
* Logging and exception handling

---

# 📊 Extracted Fields

The automation extracts information including:

- Supplier Name
- Billing Name
- Invoice Number
- Date
- Shipping Address
- Payment Terms
- Net Amount
- Shipping Charges
- Discount
- Total

---

# 🏗 Solution Architecture

```text
┌────────────────────┐
│ Gmail Mailbox    │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ New Invoice Email  │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ GetMailInfo.xaml   │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ Download Attachment│
└─────────┬──────────┘
          │
          ▼
┌──────────────────────────────┐
│ Main-ActionCenter.xaml       │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ Document Understanding AI    │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ Confidence Evaluation        │
└───────┬───────────┬──────────┘
        │           │
        ▼           ▼
 High Confidence  Low Confidence
        │           │
        ▼           ▼
   Continue   Action Center
        └──────┬──────┘
               ▼
┌──────────────────────────────┐
│ Build Result Dictionary      │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ AppendToExcelReport.xaml     │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ InvoicesReport.xlsx          │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ Log Results                  │
└──────────────────────────────┘
```

---

# ⚙️ Usage

## Prerequisites

Before running the solution, ensure that you have:

* UiPath Studio
* UiPath Orchestrator
* UiPath Document Understanding enabled
* UiPath Action Center configured
* Gmail Integration Service configured
* Required UiPath packages installed

---

## Initial Setup

This repository provides two configuration templates.

### Runtime Configuration

```text
Data/
Config.Template.xlsx
```

Contains runtime settings such as:

* Document Understanding API Key
* OCR configuration
* Queue names
* Asset names
* Report location

Copy the template and rename it to:

```text
Config.xlsx
```

Then update all placeholder values.

---

### Orchestrator Initialization

```text
QuickStart/
InitializeOrchestrator/
Data/
InitializeOrchestratorConfig.Template.xlsx
```

This configuration is used to automatically provision the UiPath Orchestrator environment.

It contains information such as:

* Folder Name
* Queue Name
* Storage Bucket Name
* Asset Names and values
* Task Catalog Names

Copy the template and rename it to:

```text
InitializeOrchestratorConfig.xlsx
```

Fill in the required values before executing the initialization workflow.

---

## QuickStart

The **QuickStart** module automates the initial setup of the UiPath Orchestrator environment.

### InitializeOrchestrator.xaml

Creates the required Orchestrator resources automatically:

* Assets
* Queues
* Storage Buckets
* Task Catalogs

---

### OrchestratorRequest_POST.xaml

Reusable workflow responsible for communicating with the UiPath Orchestrator REST API.

Used for:

* Creating Assets
* Creating Queues
* Creating Storage Buckets
* Creating Task Catalogs

---

## Deployment

1. Configure **InitializeOrchestratorConfig.xlsx**
2. Execute **InitializeOrchestrator.xaml**
3. Populate the generated Assets inside Orchestrator with the required values (for example, `DU_APIKey`, OCR credentials, endpoints, and other secure settings).
4. Configure **Config.xlsx** using the created Queue, Asset, and Storage Bucket names.
5. Execute **Main-AiInvoiceProcessing.xaml**

The solution is now ready to process incoming invoice emails.

---



# 🔒 Security

Sensitive information is intentionally excluded from this repository.

The following are **not** included:

* API Keys
* Production credentials
* Customer documents
* Production endpoints

Configuration templates are provided instead.

---

# 📄 License

Copyright © 2026 Mohamed Dhafer HADJ AMOR

This repository is provided for educational, demonstration, and portfolio purposes.

If you intend to reuse this project or any part of it in production, please ensure that you comply with all applicable licenses for UiPath components and third-party packages used by this solution.

---

# 📝 Notes

* This project is intended to demonstrate an enterprise Intelligent Document Processing solution developed with UiPath.
* Configuration templates are included to simplify deployment across different environments.
* Before executing the automation, initialize the UiPath Orchestrator environment using the **QuickStart** workflows.
* Populate all required Asset values after they have been created in Orchestrator.
* Replace all placeholder values in the provided configuration templates before execution.
* The repository uses anonymized sample documents only.

---

# 👤 Author

**Mohamed Dhafer HADJ AMOR**

Software Engineer • UiPath Certified Professional • Intelligent Automation Developer

Specializations:

* UiPath
* Intelligent Document Processing
* RPA
* Python Automation
* Low-Code Development
* Process Automation

**LinkedIn**

https://www.linkedin.com/in/mohamed-dhafer-hadj-amor-17a7b1176/