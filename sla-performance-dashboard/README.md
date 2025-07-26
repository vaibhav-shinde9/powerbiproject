# 📊 SLA Performance Power BI Dashboard

This repository contains a Power BI dashboard designed to monitor and analyze **SLA (Service Level Agreement) Performance** across support operations. It includes interactive visuals, KPI cards, and slicers for effective SLA compliance tracking.

---

## 🔍 Dashboard Overview

![Dashboard Preview](overviewimgSLA.png)

## 📌 Key Features

- **KPI Metrics**:
  - 🧮 **Average CSAT Score**
  - 🎟️ **Total Tickets**
  - ⏱️ **SLA Compliance %**
  - 👥 **Total Agents**

- **Trend & Analysis**:
  - 📉 SLA Compliance % by Month (Line Chart)
  - 🧁 SLA Breach % (Donut Chart)
  - 📊 SLA % by Category and Month (Matrix Table)
  - 🪄 Ticket Count by Priority (Bar Chart)

- **Slicers for Filtering**:
  - Region
  - Priority
  - Category
  - Status

---

## 📁 Files Included

| File Name | Description |
|-----------|-------------|
| `Tickets.csv` | Raw ticket data including SLA timestamps, agents, and status |
| `SLA_definitions.csv` | SLA compliance rules by priority or category |
| `Agents.csv` | Agent-level metadata |
| `SLA_Dashboard.pbix` | Power BI project file |
| `Screenshot 2025-07-26 213419.png` | Dashboard preview image |
| `README.md` | Project documentation |

---

## 🧮 DAX Measures Used

```DAX
Total Tickets = COUNT(Tickets[TicketID])

SLA Compliance % = 
DIVIDE(
    COUNTROWS(FILTER(Tickets, Tickets[SLA Met] = "Yes")),
    COUNTROWS(Tickets)
)

Average CSAT Score = AVERAGE(Tickets[CSAT Score])

Total Agents = DISTINCTCOUNT(Agents[AgentName])

SLA Breach % = 
DIVIDE(
    COUNTROWS(FILTER(Tickets, Tickets[SLA Met] = "No")),
    COUNTROWS(Tickets)
)
