# RPA Automation — Ticket Integration Platform

## Related Projects

🔒 Private Repository: `https://github.com/EveMurta/MS_Power_Automate_Integracao_JIRA-ASSIST`

## 📌 Overview

This automation integrates a ticketing platform with Microsoft Power Platform and a desktop automation flow (RPA). The solution automates the monitoring, collection, routing, and assisted processing of technical tickets from specific operational groups.

The workflow performs:

* Periodic ticket monitoring through REST API integration
* Identification of new incidents and reopened tickets
* Storage of information in a collaborative online spreadsheet
* Conditional execution of a desktop robot for assisted processing

The architecture combines cloud automation and desktop automation to reduce manual operational effort and accelerate service response time.

---

## 🎯 Objectives

* Automate technical ticket monitoring
* Eliminate manual verification of operational queues
* Maintain a centralized incident database
* Trigger desktop automations on demand
* Reduce response time and operational rework

---

## 🛠 Technologies Used

* Power Automate / Azure Logic Apps
* REST API Integration
* Excel Online (Business)
* Power Automate Desktop (RPA)
* Microsoft Power Platform
* Cloud and Desktop Automation

---

## 🔄 Process Flow

```text id="c7r9ka"
Scheduled Trigger
    ↓
REST API Request
    ↓
Iterates through returned incidents
    ↓
Validates whether the incident already exists
    ├── No → Creates new record
    │        Triggers desktop automation
    └── Yes → Checks for reopening
             ├── Reopened today → New record
             └── Otherwise → Ignore
    ↓
Executes desktop flow
```

---

## 📂 Storage Structure

The automation uses an online spreadsheet as the operational queue.

### Fields Used

| Field             | Description                       |
| ----------------- | --------------------------------- |
| Store ID          | Unit identifier                   |
| Requester         | Person responsible for the ticket |
| Summary           | Incident title                    |
| Queue             | Operational group                 |
| Incident          | Ticket code                       |
| Description       | Ticket details                    |
| Processing Status | Processing indicator              |
| Contact           | Contact information               |
| Status            | Current situation                 |
| Date/Time         | Insertion timestamp               |

---

## ⚙️ Environment Configuration

### Parameters

| Parameter      | Description                              |
| -------------- | ---------------------------------------- |
| Execution Mode | Defines assisted or unattended execution |

### Integrations

* Online spreadsheet connection
* Desktop automation connection
* REST API integration

---

## 🧩 Main Components

### Cloud Flow

| Component         | Function                             |
| ----------------- | ------------------------------------ |
| Scheduled Trigger | Runs periodically                    |
| API Request       | Retrieves incidents                  |
| Record Validation | Checks whether the ticket exists     |
| Conditional Rules | Handles new incidents and reopenings |
| RPA Trigger       | Executes desktop automation          |

### Desktop Flow

Responsible for:

* Processing pending incidents
* Executing assisted operational tasks
* Updating records
* Finalizing processing

---

## 📊 Business Rules

### Ticket Selection

* Only active incidents are processed
* Specific operational queues are monitored
* Tickets are sorted by creation date

### Processing Logic

| Situation                  | Action                                 |
| -------------------------- | -------------------------------------- |
| New incident               | Creates record and triggers automation |
| Reopened incident          | Creates new processing                 |
| Already processed incident | Ignores                                |

---

## 🚨 Error Handling

Current implementation:

* The flow is interrupted if a dependency fails
* There is no retry policy or automatic notification

Possible future improvements:

* Automatic retry
* Operational alerts
* Structured logs
* Observability

---

## 🔧 Dependencies

* API access permissions
* Spreadsheet access permissions
* Configured RPA environment
* Power Platform licensing
* Installed desktop automation agent

---

## 🖥 Infrastructure Requirements

* Windows environment
* Power Automate Desktop installed
* Published desktop flows
* Proper execution permissions

---

## 👥 Teams Involved

* Cloud Automation Team
* RPA Team
* Operations Team
* Information Security Team

---

## 📄 License

Internal corporate use only.
