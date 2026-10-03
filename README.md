# 🚚 SwiftShip Tracker

A Salesforce-based parcel tracking and delivery management system that allows users to book and track parcels, retrieve delivery details using a Parcel ID, and get conversational tracking responses through Salesforce Agentforce.

The solution combines **Salesforce Custom Objects, Auto-Launched Flow, Prompt Builder and Agentforce** to reduce manual parcel-status queries and keep parcel, sender, receiver and delivery information connected.

---

## 🎥 Project Overview

SwiftShip Tracker is designed to simplify parcel tracking by allowing a user to provide a **Parcel ID** and receive the parcel's current status, weight and estimated delivery date through an Agentforce conversational interface.

The system uses:

- Salesforce Developer Edition
- Four custom objects
- Auto-Launched Flow
- Prompt Builder
- Agentforce
- Permission Set for access control

---

---

## 🎥 Project Resources

- 🎬 **Demo Video:** [Watch Project Demo](https://drive.google.com/file/d/1oUVUV6_sL6Sbdm-4bWtOZdf6efneG4TV/view?usp=drivesdk)
- 📄 **Project Documentation:** [View Project Documentation](https://drive.google.com/file/d/1D4J_KbpKXCK922qDYsJhvqmf-2aYqG8C/view?usp=drivesdk)

---

## 👥 Team Details

**Team ID:** SWTID-2026-5349  
**Team Size:** 4

| Name | Role | NM ID | Register No. |
|------|------|-------|--------------|
| Hobika Mn | Team Leader | `89F5F40E81CE63E884A4DB81C938D3B3` | 821923243020 |
| Gowmidha C | Team Member | `688286753926f6e9617403cd0b902680` | 821923243020 |
| Kanimozhi M | Team Member | `4AAA164C0B9DE728DD2472E65FD42986` | 821923243024 |
| Abinaya M | Team Member | `6f9d6750fa91b79b26d451dc2ec83578` | 821923243002 |

**College:** [College Name]  
**College Code:** [College Code]  
**City:** [City]

---

## 📌 Problem Statement

Parcel booking and tracking often requires customers to contact support or switch between multiple applications. This can result in:

- Repeated "where is my parcel?" queries
- Delays in getting delivery information
- Scattered parcel, sender, receiver and delivery records
- Additional workload for support teams
- Difficulty accessing parcel information quickly

SwiftShip Tracker moves the core tracking process into Salesforce and provides a conversational way to retrieve parcel information using a Parcel ID.

---

## 🎯 Project Goals

The system aims to:

- Create and manage parcel records
- Link parcels with sender, receiver and delivery details
- Track parcel status throughout delivery
- Retrieve parcel information using a Parcel ID
- Display tracking information in a fixed, readable format
- Provide conversational parcel tracking through Agentforce
- Control access through a Salesforce Permission Set
- Reduce manual parcel-status searches and repeated support queries

---

## 🚀 Key Features

### 🔹 Parcel Management

Four custom Salesforce objects store the main information required by the system:

- Parcel
- Delivery
- Sender
- Receiver

These records are connected through lookup relationships.

### 🔹 Parcel Status Tracking

The parcel status is maintained using a Picklist with the following values:

| Status | Meaning |
|--------|---------|
| 📦 Booked | Parcel has been booked |
| 🚚 In Transit | Parcel is moving through the delivery process |
| 🛵 Out for Delivery | Parcel is currently out for delivery |
| ✅ Delivered | Parcel has been delivered |

### 🔹 Parcel ID Based Tracking

Users can provide a unique **Parcel ID**, such as `P-002`, to retrieve the corresponding parcel details.

The system returns:

- Parcel Name
- Parcel ID
- Status
- Weight
- Estimated Delivery Date

### 🔹 Auto-Launched Flow

The **Parcel Updates** Flow is an Auto-Launched Flow with no direct trigger. Agentforce invokes it as an action.

The Flow:

1. Receives the Parcel ID.
2. Searches the Parcel object.
3. Retrieves the matching parcel record.
4. Executes the Prompt Builder template.
5. Stores the generated response.
6. Returns the formatted result to Agentforce.

### 🔹 Prompt Builder

The **Retrieve Parcel Details** Prompt Template formats the parcel information into a fixed and readable response.

It uses Salesforce record fields as resources so that the response is grounded in the stored parcel data.

### 🔹 Agentforce Conversational Tracking

The **SwiftShip Tracker** Agentforce agent provides conversational parcel tracking.

It contains:

- **Agent:** SwiftShip Tracker
- **Subagent:** Parcel Tracker
- **Action:** Parcel Details
- **Flow:** Parcel Updates

The user can simply provide a Parcel ID and request parcel information.

### 🔹 Permission-Based Access

The **Swift Ship** Permission Set controls access to the required Salesforce objects and Flow.

The permission set provides the Einstein Agent user with access to:

- Parcel
- Delivery
- Sender
- Receiver
- Parcel Updates Flow

### 🔹 Reports and Field History Support

The four custom objects have:

- Allow Reports enabled
- Track Activities enabled
- Track Field History enabled
- Deployment Status: Deployed

---

## 🔄 Parcel Journey

```text
Customer
   │
   ▼
Book Parcel
   │
   ▼
Parcel Record Created
   │
   ▼
Link Sender / Receiver / Delivery
   │
   ▼
Status Updates
(Booked → In Transit → Out for Delivery → Delivered)
   │
   ▼
User Provides Parcel ID
   │
   ▼
SwiftShip Tracker Agent
   │
   ▼
Parcel Tracker Subagent
   │
   ▼
Parcel Details Action
   │
   ▼
Parcel Updates Flow
   │
   ▼
Get Parcel Records
   │
   ▼
Retrieve Parcel Details Prompt
   │
   ▼
Formatted Tracking Response
```

---

## 🏗️ System Architecture

```text
                         USER
                           │
                           ▼
                 SwiftShip Tracker
                    Agentforce Agent
                           │
                           ▼
                  Parcel Tracker
                     Subagent
                           │
                           ▼
                   Parcel Details
                       Action
                           │
                           ▼
                 Parcel Updates Flow
                  (Auto-Launched)
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
       Get Parcel Records        Prompt Builder
              │                  Retrieve Parcel
              │                     Details
              └────────────┬────────────┘
                           ▼
                  Formatted Output
                           │
                           ▼
             Status / Weight / Delivery Date
```

---

## ⚙️ Technology Stack

### Salesforce Platform

- Salesforce Developer Edition
- Custom Objects
- Lookup Relationships
- Auto-Launched Flow
- Flow Builder
- Prompt Builder
- Agentforce
- Permission Sets
- Field History Tracking
- Reports

### AI Layer

- Salesforce Agentforce
- Prompt Builder
- Agentforce Subagent
- Flow-based Agent Action

---

## 🗂️ Data Model

The project uses four custom Salesforce objects.

| Object | API Name | Purpose |
|--------|----------|---------|
| **Parcel** | `parcel__c` | Stores core parcel details |
| **Delivery** | `Delivery__c` | Stores delivery information |
| **Sender** | `sender__c` | Stores sender information |
| **Receiver** | `Receiver__c` | Stores receiver information |

### Parcel Object

| Field | Type | Description |
|------|------|-------------|
| Parcel ID | Auto Number | Unique parcel identifier |
| Status | Picklist | Booked, In Transit, Out for Delivery, Delivered |
| Weight | Number | Parcel weight |
| Estimate Delivery Date | Date | Expected delivery date |
| Sender | Lookup | Links parcel to sender |

### Delivery Object

| Field | Type | Description |
|------|------|-------------|
| Current Location | Geolocation | Current parcel location |
| Estimate Delivery Date | Date | Expected delivery date |
| Parcel | Lookup | Links delivery to parcel |
| Sender | Lookup | Links delivery to sender |

### Sender Object

| Field | Type | Description |
|------|------|-------------|
| Sender Address | Geolocation | Sender location |
| Sender Contact | Phone | Sender contact number |
| Sender Email | Email | Sender email address |

### Receiver Object

| Field | Type | Description |
|------|------|-------------|
| Receiver Address | Geolocation | Receiver location |
| Receiver Contact | Phone | Receiver contact number |
| Receiver Email | Email | Receiver email address |
| Receiver | Lookup | Relationship field |

---

## 🔗 Object Relationships

```text
                 ┌──────────────┐
                 │    Parcel    │
                 │ parcel__c    │
                 └──────┬───────┘
                        │
                        │ Lookup
                        ▼
                 ┌──────────────┐
                 │   Delivery   │
                 │ Delivery__c  │
                 └──────┬───────┘
                        │
             ┌──────────┴──────────┐
             ▼                     ▼
      ┌──────────────┐      ┌──────────────┐
      │    Sender    │      │   Receiver   │
      │  sender__c   │      │ Receiver__c  │
      └──────────────┘      └──────────────┘
```

---

## 🔁 Flow Logic

### Flow Name

**Parcel Updates**

### Flow Type

**Auto-Launched Flow**

### Input

`Ids` — Text input containing the Parcel ID.

Example:

```text
P-002
```

### Output

`Output` — Text output containing the formatted parcel tracking details.

### Flow Components

| Element | Function |
|---------|----------|
| Start | Starts the Auto-Launched Flow |
| Get Parcel Records | Finds the parcel using Parcel ID |
| Parcel Updates Action | Runs the Retrieve Parcel Details Prompt Template |
| Assignment Outputs | Stores the response |
| End | Returns the output to Agentforce |

---

## 🤖 Agentforce Setup

| Property | Configuration |
|----------|---------------|
| Agent | SwiftShip Tracker |
| Agent Type | Agentforce Service Agent |
| Version | Version 1 |
| Status | Active |
| Subagent | Parcel Tracker |
| Action | Parcel Details |
| Action Type | Flow |
| Flow | Parcel Updates |
| Input | Parcel ID |
| Output | Parcel details text |

### Agent Instruction

When the user asks for parcel details and provides a Parcel ID, the Parcel Tracker subagent retrieves the parcel information through the Parcel Details action and displays the returned parcel information.

---

## 🔐 Security and Access

The project uses the **Swift Ship Permission Set** for access control.

The permission set provides the Einstein Agent user with:

- Read access
- Create access
- Edit access
- Required object access
- Access to the Parcel Updates Flow

Objects covered:

- Parcel
- Delivery
- Sender
- Receiver

---

## 🧪 Testing

Testing was performed using **Flow Builder Debug** and the **Agentforce Builder Preview** with sample Parcel ID `P-002`.

| Test ID | Test | Expected Result | Actual Result | Status |
|---------|------|-----------------|---------------|--------|
| TC-01 | Flow Debug Run | Flow completes without error | Completed in 5.23 seconds | ✅ Pass |
| TC-02 | Parcel ID `P-002` tracking request | Agent returns parcel details | Sandwood, P-002, Out for Delivery, weight 5, estimated delivery 09/26/2026 | ✅ Pass |
| TC-03 | Agent trace view | Request routes to Parcel Tracker and Parcel Details action | Correct subagent/action transition with grounded output | ✅ Pass |

---

## 📊 Project Metrics

| Metric | Value |
|--------|-------|
| Team Members | 4 |
| Story Points | 42 |
| Sprints | 6 |
| Custom Objects | 4 |
| Auto-Launched Flows | 1 |
| Agentforce Agents | 1 |
| Prompt Templates | 1 |
| Permission Sets | 1 |

---

## 📅 Agile Plan

The project was divided into **6 sprints** with a total of **42 story points**.

| Sprint | User Story | Points | Owner |
|--------|------------|--------|-------|
| 1 | Configure Salesforce Developer Environment | 3 | Hobika Mn |
| 2 | Create four custom objects and tabs | 5 | Gowmidha C |
| 2 | Create fields and relationships | 5 | Kanimozhi M |
| 3 | Build Retrieve Parcel Details Prompt Template | 5 | Abinaya M |
| 3 | Build Auto-Launched Flow - Parcel Updates | 5 | Hobika Mn |
| 4 | Create Agentforce agent, subagent and action | 8 | Gowmidha C |
| 4 | Permission set and Flow access | 3 | Kanimozhi M |
| 5 | Test Flow and Agentforce with sample parcels | 5 | Abinaya M |
| 6 | Documentation and final review | 3 | Hobika Mn |

### Sprint Distribution

```text
Sprint 1  ███           3 points
Sprint 2  ██████████   10 points
Sprint 3  ███████████  11 points
Sprint 4  ███████████  11 points
Sprint 5  █████          5 points
Sprint 6  ███            3 points
```

**Total:** 42 story points  
**Average velocity:** approximately 7.0 points per sprint

---

## 🛠️ Build Process

### Step 1 — Salesforce Environment

Create and configure a Salesforce Developer Edition org.

### Step 2 — Custom Objects

Create:

- Parcel
- Delivery
- Sender
- Receiver

Enable required reporting, search/activity and field-history capabilities.

### Step 3 — Custom Tabs

Create custom object tabs for:

- Parcels
- Deliveries
- Senders
- Receivers

### Step 4 — Fields and Relationships

Configure the fields and lookup relationships described in the Data Model section.

### Step 5 — Prompt Builder

Create:

**Retrieve Parcel Details**

Map the required Parcel fields into the prompt template and activate it.

### Step 6 — Auto-Launched Flow

Create and activate:

**Parcel Updates**

Configure:

```text
Start
  ↓
Get Parcel Records
  ↓
Parcel Updates Action
  ↓
Assignment Outputs
  ↓
End
```

### Step 7 — Agentforce

Configure:

```text
SwiftShip Tracker
       ↓
Parcel Tracker
       ↓
Parcel Details
       ↓
Parcel Updates Flow
```

Activate the agent after configuring the required permissions.

### Step 8 — Permissions

Assign the **Swift Ship** Permission Set to the required Einstein Agent user and provide Flow access.

### Step 9 — Testing

Test the Flow and Agentforce agent using valid Parcel IDs such as `P-002`.

---

## 📁 Repository Structure

```text
SwiftShip-Tracker/
│
├── README.md
│
├── docs/
│   ├── SwiftShip_Tracker_Project_Documentation.pdf
│   └── screenshots/
│
└── force-app/
    └── main/
        └── default/
            ├── objects/
            │   ├── parcel__c/
            │   ├── Delivery__c/
            │   ├── sender__c/
            │   └── Receiver__c/
            │
            ├── flows/
            │   └── Parcel_Updates.flow-meta.xml
            │
            ├── permissionsets/
            │   └── Swift_Ship.permissionset-meta.xml
            │
            └── tabs/
```

---

## ⚠️ Current Limitations

The current implementation has the following limitations:

- Agentforce currently focuses on parcel status/details retrieval.
- Parcel booking and status updates are performed directly in Salesforce.
- Email notifications are planned but not implemented.
- Experience Cloud customer portal is planned but not implemented.
- Dashboards are planned but not implemented.
- Parcel weight is displayed without a unit.
- Testing was performed only in a Salesforce Developer Edition org.
- No separate Sandbox/UAT stage was used.
- Invalid or missing Parcel IDs do not yet have a custom fault message.

---

## 🔮 Future Enhancements

### 📧 Notifications

Send email notifications to senders and receivers whenever the parcel status changes.

### 🌐 Customer Portal

Build a self-service parcel tracking portal using Salesforce Experience Cloud.

### 🤖 Agent Actions

Allow Agentforce to:

- Book parcels
- Update delivery status
- Perform additional parcel operations

### 📊 Analytics

Add Salesforce Reports and Dashboards for:

- Parcel volume
- Delivery performance
- Status trends
- Delivery timelines

### 📍 Richer Tracking Information

Display:

- Weight with measurement units
- Current delivery location
- Additional delivery information

### 🛡️ Fault Handling

Add a dedicated Flow fault path to return a clear message when the provided Parcel ID does not exist.

---

## 📈 Solution Benefits

SwiftShip Tracker provides:

- Faster parcel-status retrieval
- Reduced repetitive support queries
- Centralized parcel information
- Connected sender, receiver and delivery records
- Conversational tracking through Agentforce
- Reusable Flow-based automation
- Prompt-based response formatting
- Permission-controlled access
- A scalable Salesforce-based architecture

---

## 🧩 Core Salesforce Components

| Component | Name |
|-----------|------|
| Custom Object | `parcel__c` |
| Custom Object | `Delivery__c` |
| Custom Object | `sender__c` |
| Custom Object | `Receiver__c` |
| Flow | `Parcel Updates` |
| Prompt Template | `Retrieve Parcel Details` |
| Agent | `SwiftShip Tracker` |
| Subagent | `Parcel Tracker` |
| Agent Action | `Parcel Details` |
| Permission Set | `Swift Ship` |

---

## 🏫 Institution

**[College Name]**  
**[City]**  
**College Code:** [College Code]

---

## 👨‍💻 Team

### Hobika Mn
**Team Leader**  
NM ID: `89F5F40E81CE63E884A4DB81C938D3B3`

### Gowmidha C
**Team Member**  
NM ID: `688286753926f6e9617403cd0b902680`

### Kanimozhi M
**Team Member**  
NM ID: `4AAA164C0B9DE728DD2472E65FD42986`

### Abinaya M
**Team Member**  
NM ID: `6f9d6750fa91b79b26d451dc2ec83578`

---

## 📄 Project Documentation

The complete project documentation contains the project requirements, architecture, data model, Flow logic, Agentforce configuration, build process, testing results, Agile plan, limitations and future roadmap.

---

## ⭐ Project Summary

**SwiftShip Tracker** combines Salesforce data, Flow automation, Prompt Builder and Agentforce to provide Parcel ID-based conversational tracking.

```text
Parcel ID
   ↓
Agentforce
   ↓
Parcel Tracker
   ↓
Parcel Details Action
   ↓
Parcel Updates Flow
   ↓
Salesforce Records
   ↓
Prompt Builder
   ↓
Tracking Response
```

**Built with Salesforce + Flow + Prompt Builder + Agentforce.**
