# 🎫 Customer Support Ticket Priority Prediction & Automated Assignment System

A Salesforce-based intelligent customer support system that automatically analyzes support tickets, predicts their priority, creates urgent tasks, and assigns them to the appropriate support level using **Salesforce Flow and Agentforce**.

---

## 🎥 Project Resources

- 🎬 **Demo Video:** [Watch Project Demo](https://drive.google.com/file/d/1YJgDyH9_CWsXaU2An7mBlIr6Zu0FUrB7/view?usp=drive_link)
- 📄 **Project Documentation:** [View Project Documentation](https://drive.google.com/file/d/1IOgsbZxHDVmD93r_0Y6DI5PamSI0t0ew/view?usp=drive_link)

---

## 👥 Team Details

**Team ID:** `SWTID-2026-7679`  
**Team Size:** 4  
**College:** St. Joseph's College of Engineering and Technology, Thanjavur  
**College Code:** `8219`

| Name | Role | NMID |
|---|---|---|
| **Priyadharshini J** | Team Leader | `CB0E45A5610E3B7A80D4E9F2F74B93FA` |
| **Sushmitha ** | Team Member | `42C35A146C4BF81B09B4C6771D29B681` |
| **Srimathi R** | Team Member | `137C65A061B7F819292474B958E38893` |
| **Pushpa A** | Team Member | `42C35A146C4BF81B09B4C6771D29B681` |

---

## 📌 Project Overview

Support teams often spend time manually checking tickets, deciding which issues are urgent, and assigning them to the right support agent.

This project automates that process.

The system:

- Retrieves the latest support ticket for a customer Account
- Analyzes the ticket description
- Classifies the ticket as **High, Medium, or Low**
- Automatically creates an urgent task for High-priority tickets
- Assigns High-priority tickets to a **Senior Support Agent**
- Provides conversational access through **Agentforce**
- Performs an optional SLA breach-risk check

The complete solution is built using Salesforce, an Auto-Launched Flow, and an Agentforce subagent.

---

## 🚀 Key Features

### 🔹 Automatic Ticket Priority

Tickets are classified based on keywords in the ticket description:

| Priority | Keywords | Action |
|---|---|---|
| 🔴 **High** | `urgent`, `not working`, `failure` | Create urgent task + assign Senior Support Agent |
| 🟠 **Medium** | `issue`, `slow`, `delay` | Mark for handling shortly |
| 🟢 **Low** | None of the above | Queue for processing |

High-priority conditions are checked first, so if a ticket contains both High and Medium keywords, it is classified as **High**.

---

## 🤖 Agentforce Integration

The project uses an Agentforce subagent called:

**Support Ticket Priority Analysis**

The user only needs to provide an **Account Name**.

Agentforce then:

1. Retrieves the latest ticket.
2. Reads the ticket description.
3. Determines the priority.
4. Triggers the Salesforce Flow.
5. Creates an urgent task for High-priority tickets.
6. Assigns the appropriate support level.
7. Returns the result to the user.

The Agentforce action uses the Auto-Launched Flow as its backend automation.

---

## ⚙️ Technology Stack

- **Salesforce**
- **Salesforce Developer Edition**
- **Trailhead Playground**
- **Salesforce Flow**
- **Auto-Launched Flow**
- **Agentforce**
- **Custom Salesforce Object**
- **Account & Contact Records**
- **Task Management**

---

## 🏗️ Architecture

```text
                User
                  │
                  ▼
            Agentforce
                  │
                  ▼
     Support Ticket Priority
          Analysis Subagent
                  │
                  ▼
        Auto-Launched Flow
                  │
          ┌───────┴───────┐
          ▼               ▼
    Get Account       Get Latest Ticket
          │               │
          └───────┬───────┘
                  ▼
          Analyze Description
                  │
        ┌─────────┼─────────┐
        ▼         ▼         ▼
      HIGH      MEDIUM      LOW
        │         │          │
        ▼         ▼          ▼
  Create Task   Handle      Queue
  Senior Agent  Shortly    Processing
