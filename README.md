# 🔥 University of Newcastle — Fire Management System
### Requirements Analysis & System Design

![Status](https://img.shields.io/badge/status-submitted-brightgreen)
![Course](https://img.shields.io/badge/course-INFO6030-blue)
![University](https://img.shields.io/badge/university-University%20of%20Newcastle-yellow)
![Artefacts](https://img.shields.io/badge/artefacts-UML%20%7C%20Business%20Rules%20%7C%20Domain%20Model-orange)

---

## 📌 About the Project

A complete **requirements analysis and UML system design** for the University of Newcastle's new Fire Management System (FMS) hub — a safety-critical, 24/7 online platform allowing Infrastructure and Facilities Services (IFS) to monitor, command, and audit fire detection, suppression, compartmentation, and evacuation systems across all campus buildings.

The FMS operates on a **hub-and-spoke model**: a central hub managed by IFS connects to local Fire Indicator Panels (FIPs) in every registered building — enabling remote monitoring, command dispatch, configuration updates, and comprehensive audit logging.

---

## 🏗️ System Architecture

```
┌──────────────────────────────────────────────────────────┐
│                    FMS Central Hub                        │
│           (IFS — Infrastructure & Facilities Services)    │
├─────────────────┬──────────────────┬─────────────────────┤
│  Asset Mgmt     │   User Mgmt      │   Event Management  │
├─────────────────┼──────────────────┼─────────────────────┤
│  Operation Mgmt │   Reporting      │   FIP Management    │
└─────────────────┴──────────────────┴─────────────────────┘
         │   Hub ↔ FIP via fibre / IP (FMS network)   │
    ┌──────────┐      ┌──────────┐      ┌──────────┐
    │  FIP — A │      │  FIP — B │      │  FIP — N │
    │ Building │      │ Building │      │ Building │
    └──────────┘      └──────────┘      └──────────┘
         │                  │                  │
  [Sensors · Alarms · Suppression · Evacuation · Fire Doors]
```

---

## 📋 Deliverables

| # | Artefact | Detail |
|---|----------|--------|
| 1 | **Business Rules** | 60+ rules across WHS, ethical/security/privacy, and legislation |
| 2 | **Use Case Diagrams** | 6 subsystems · 35+ use cases |
| 3 | **Full Use Case Descriptions** | 5 detailed descriptions — scenario, pre/post-conditions, flow of events, alternative flows, exceptions |
| 4 | **Activity Diagrams** | 5 swimlane diagrams with start/end nodes, one per use case |
| 5 | **Domain Class Diagram** | 10 classes, analyst-view, with attributes and multiplicities |
| 6 | **Team Management** | 4 meeting minutes · MS Project Gantt chart · MS Teams activity report · Pre-action plan |

---

## 🗂️ Six Subsystems

| Subsystem | Use Cases | Key Actors |
|---|---|---|
| Asset Management | 7 | Asset Manager, Fire Response Team |
| User Management | 7 | System Administrator, Users |
| Event Management | 6 | System Administrator, Fire Response Team |
| Operation Management | 7 | Operation Manager |
| Reporting | 9 | Operation Manager, Asset Manager, System Administrator, Report Manager |
| FIP Management | 7 | System Administrator, FIP Technician, Fire Response System |

---

## 📊 System Diagrams

> **How to add diagrams:** Open your submitted PDF, screenshot or export each diagram as PNG, save them in an `images/` folder in this repo. The images will render automatically below.

### Use Case Diagram — All Subsystems
![Use case diagram](images/use-case-overview.png)

### Generate Incident Report — Activity Diagram
![Activity diagram - incident report](images/activity-incident-report.png)

### Monitor FIP Status — Activity Diagram
![Activity diagram - FIP status](images/activity-fip-status.png)

### Domain Class Diagram
![Domain class diagram](images/domain-class-diagram.png)

---

## 📐 Domain Classes

| Class | Key Attributes |
|---|---|
| `User` | userId · userName · userType |
| `CentralSystem` | administratorId · administratorName · status · dataStorageId · reportList |
| `FIP` | fipId · location · status |
| `Building` | buildingId · buildingName · location |
| `Zone` | zoneId · zoneName · zoneType |
| `Sensor` | sensorId · sensorType · sensorStatus · location · zoneId |
| `Alarm` | alarmId · status · level · location · sensorId |
| `Report` | reportId · reportType · reportContent · level · managerId |
| `SubSystem` | systemId · systemName · systemType · systemStatus |
| `Data` | dataStorageId · length · size · isFull · isEmpty · dataType |

**Key relationships:**
- `CentralSystem` (1..1) → `User` (0..*)
- `CentralSystem` (1..1) → `SubSystem` (0..*)
- `Building` (1..1) → `Zone` (0..*)
- `Zone` (1..1) → `Sensor` (1..1)
- `Sensor` (1..1) → `Alarm` (1..*)
- `Building` (1..1) → `FIP` (0..*)

---

## 📏 Business Rules Coverage

### Work Health & Safety (10+)
- Compliance with Work Health and Safety Regulation 2017 (SafeWork NSW)
- Mandatory emergency evacuation procedures and regular fire drills
- PPE requirements for all personnel engaged in hazardous activities
- Immediate reporting and investigation of all workplace incidents
- Periodic health monitoring for staff exposed to hazardous conditions
- First aid facilities and certified personnel maintained on-site
- ISO 45001 — Crisis Management Plans covering fire and emergency scenarios

### Ethical, Security & Privacy (14)
- Australian Privacy Principles — no disclosure of personal occupant data
- ISO/IEC 27001 — cybersecurity measures, encrypted transmission hub ↔ FIP
- NIST Cybersecurity Framework — access limited to authorised personnel only
- OWASP Top Ten — command protection, preventing unauthorised FMS commands
- Ethical use of facial recognition and dual-gait biometric systems
- Incident Response Plan modelled on NIST Incident Response Guide
- Weekly system audits and regular risk assessments
- Emergency override actions documented for full accountability

### Legislation & Standards (22)
- NSW Fire and Rescue Act 1989
- Environmental Planning and Assessment Act 1979 (Sections 109R, 124)
- AS 1851 — Maintenance of fire protection systems and equipment
- AS 1670.1 — Fire detection, warning, control and intercom systems
- National Construction Code Vol. 1 — Sections C (fire resistance) and E (detection/suppression)
- Privacy Act 1988 (Cth) — Part IIIA, Section 14
- NSW Fire Brigades Regulation 2014 — Part 3, Section 18
- ISO 45001:2018 — Clauses 8.2 and 9.1 (emergency preparedness)
- Building Code of Australia — fire safety construction standards

---

## 📁 Repository Structure

```
📁 uon-fire-management-system/
├── 📄 README.md
├── 📁 images/
│   ├── use-case-overview.png          ← Export from report p.23–29
│   ├── activity-incident-report.png   ← Export from report p.46
│   ├── activity-fip-status.png        ← Export from report p.48
│   └── domain-class-diagram.png       ← Export from report p.53
├── 📁 report/
│   └── Wednesday_1pm_Group_3.pdf      ← Full submitted report
└── 📁 diagrams/
    ├── use-cases/
    ├── activity-diagrams/
    └── domain-model/
```

---

## 🔑 Key System Requirements

| # | Requirement |
|---|-------------|
| 1 | Manager needs all information at fingertips for real-time decision-making |
| 2 | Safety-critical — failure could directly result in loss of life |
| 3 | Multiple report types: periodic (monthly), on-demand, and after-action |
| 4 | Records must be secure — role-based access control enforced throughout |
| 5 | Live 24/7 system — high reliability and uptime non-negotiable |
| 6 | Mobile-accessible — IFS staff can issue commands from anywhere on campus |

---

## 🛠️ Tools & Methods

| Tool | Usage |
|---|---|
| UML | Use case, activity, and domain class diagrams |
| MS Project | Gantt chart with task owners, dependencies, and deadlines |
| MS Teams | Collaboration, meeting records, activity reporting |
| Australian Standards | AS 1851, AS 1670.1, NCC |
| NSW Legislation | Fire and Rescue Act, EPA Act, Privacy Act |
| International Standards | ISO/IEC 27001, ISO 45001, NIST, OWASP |

---

## 📚 References & Standards

- [NSW Fire and Rescue Act 1989](https://legislation.nsw.gov.au/view/html/inforce/current/act-1989-192)
- [Environmental Planning and Assessment Regulation 2021](https://legislation.nsw.gov.au/view/html/inforce/current/sl-2021-0689#pt.10)
- [UON Fire Services Guiding Principles v1.3](https://www.newcastle.edu.au/__data/assets/pdf_file/0010/937639/UON-Fire-Services-Guiding-PrinciplesV1.3.pdf)
- Australian Standard AS 1851 — Maintenance of fire protection systems
- Australian Standard AS 1670.1 — Fire detection, warning & control systems
- National Construction Code (NCC) — Volume One, Sections C & E
- ISO 45001:2018 — Occupational Health and Safety Management Systems
- Privacy Act 1988 (Cth) — Australian Privacy Principles

---

## 📄 Full Report

**[📥 View Full Report (PDF)](./report/Wednesday_1pm_Group_3.pdf)**

---

## ⏱️ Project Timeline

| Date | Milestone |
|---|---|
| 26 May 2024 | Project kickoff — scope understood, tasks divided, research begun |
| 05 Jun 2024 | Integration meeting — sections combined, use case list agreed |
| 12 Jun 2024 | Full-team review — use case descriptions finalised, diagrams allocated |
| 19 Jun 2024 | Final assembly — report compiled, Gantt verified, conclusion written |
| 21 Jun 2024 | ✅ Submitted via Canvas |

---

*INFO6030 Systems Analysis and Design · University of Newcastle · T2 2024*
