# SA-Capstone
 Dynamic Pricing for Urban Parking Lots
# 📌 Dynamic Pricing for Urban Parking Lots

Capstone Project | Summer Analytics 2025

---

## 📖 Overview

This project addresses the inefficiencies caused by static pricing in urban parking lots. We developed a dynamic, real-time pricing engine that updates parking fees based on demand, queue length, traffic conditions, special events, and competitor pricing. The solution uses real-time data streaming and logic-based modeling to improve parking lot utilization.

---

## 🛠 Tech Stack Used

* **Python**
* **Pandas & NumPy** – For data manipulation and model logic
* **Pathway** – For real-time data ingestion, processing, and streaming
* **Bokeh + Panel** – For real-time data visualization
* **Google Colab** – Development environment
* **GitHub** – Version control and documentation

---

## 🧱 Architecture Diagram (Mermaid Syntax)

```mermaid
graph LR
    A[CSV Stream Input] -->|Streamed to Pathway| B[Pathway Ingestion Layer]
    B --> C[Model 1 Logic - Linear Pricing]
    B --> D[Model 2 Logic - Demand-Based Pricing]
    C --> E[Streaming Output Table]
    D --> E
    E --> F[Bokeh Visualizations via Panel]
    E --> G[CSV Export - parking_stream.csv]
```

---

## 🔄 Project Architecture and Workflow

1. **Data Streaming**: The dataset (CSV) is read using `Pathway` in streaming mode with one row per second simulation.

2. **Model 1 (Linear)**:

   * Computes price based on occupancy rate.
   * Formula: `Price = BasePrice + α * (Occupancy / Capacity)`
   * Serves as a baseline.

3. **Model 2 (Demand-Based)**:

   * Adds queue length, traffic, event-day, and vehicle-type impact.
   * Computes a normalized demand score.
   * Final price is scaled smoothly between 0.5x and 2x base price.

4. **Real-Time Windows**:

   * Daily tumbling windows used for smoothing fluctuations.
   * Aggregates occupancy for dynamic adjustments.

5. **Visualization**:

   * Bokeh plots are created in Panel.
   * Users can interactively view prices per lot and compare with competitors.

6. **Output**:

   * All processed results are streamed and saved to `parking_stream.csv`
