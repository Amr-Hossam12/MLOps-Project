# Multi-Agent Financial Risk Assessment Engine
### Predictive Stability Analysis & Simulation Platform

**A distributed, autonomous multi-agent system designed to simulate financial scenarios, perform probabilistic risk analysis, and generate dynamic risk dashboards using a Data Lakehouse architecture.**

---

## 🏗️ System Architecture

![Multi-Agent Architecture Diagram](MLOps Architecture Diagram.png)

---

## 📖 Project Overview

This platform leverages a **Multi-Agent System (MAS)** to model complex financial ecosystems. Unlike traditional static risk models, this engine uses autonomous agents that interact with each other to simulate how liquidity, debt, operations, and market volatility intersect under stress.

The system features an **Active Feedback Loop** where user edits on the dashboard are vectorized and stored, allowing the agents to recalibrate and improve predictive accuracy over future simulations.

---

## 🚀 Key Components & Flow

### 1. 📂 Data Ingestion & Processing
The system begins with the user uploading raw files to a **Drive Storage Bucket**.
* **Data Ingestion Agent:** The central gatekeeper that detects file types and routes them to the correct processing pipeline.
    * **Tabular Pipeline:** Handles **CSV** and **Excel** files via parsing and schema mapping.
    * **Unstructured Pipeline:** Handles **PDFs** and **Images** (e.g., scanned receipts) via an OCR and Text Extraction pipeline.
* **Data Destination:** All processed data flows into the **Data Lakehouse**.

### 2. 🏛️ The Data Lakehouse
A unified storage architecture that supports diverse data needs:
* **Data Lake:** Stores raw, unstructured files.
* **Data Warehouse:** Holds structured business tables.
* **Vector Database:** Stores embeddings for semantic search and historical feedback.
* **Graph Database:** Maps relationships and cascading risks between entities.
* **Time-Series Database:** Stores historical metrics (cash flow, loads).
* **Cache Layer (Redis):** Ensures low-latency access for fast queries.

### 3. 🧠 The Multi-Agent Layer
The core simulation logic is driven by five specialized agents that receive inputs from the **Scenario Manager**:
1.  **Liquidity Agent:** Models cash flow and runway.
2.  **Debt Agent:** Simulates debt modeling and interest rate shocks.
3.  **Operations Agent:** Evaluates operational disruptions.
4.  **Market Agent:** Analyzes market volatility.
5.  **Counterparty Agent:** Assesses relationship risks.

*These agents feed their individual assessments into the **Simulation Engine**, which runs Monte Carlo and probabilistic modeling.*

### 4. ⚡ Scenario & External Data
* **Scenario Manager:** The entry point for simulation. It accepts user inputs (Scenario Description, Timeframe, Variables).
* **External Market APIs:** The Scenario Manager synchronously fetches on-demand market data (Stock Prices, Currency, Commodities) at the time of the request to ensure simulations use real-time market context.

### 5. 🔄 Feedback Loop
The system learns from interaction:
1.  **Risk Aggregator Agent:** Compiles simulation results into the **Interactive Dashboard**.
2.  **Feedback Agent:** When a user edits a result or provides feedback, this agent captures the input.
3.  **Recalibration:**
    * Updates the **Vector Database** with new embeddings.
    * Triggers a recalibration signal to the **Multi-Agent Layer** for future simulations.

---
