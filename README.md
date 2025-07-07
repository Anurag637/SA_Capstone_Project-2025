# 🅿️ SmartPark: Dynamic Pricing Engine for Urban Parking

![Real-Time AI](https://img.shields.io/badge/Real--Time-AI_Engine-ff69b4)
![Pathway](https://img.shields.io/badge/Powered_By-Pathway-01a8fe)
![Built from Scratch](https://img.shields.io/badge/Algorithms-From_Scratch-orange)
![Summer Analytics](https://img.shields.io/badge/Summer_Analytics-2025-9cf)

<div align="center">
  <img src="docs/system_flow.gif" alt="Animated System Flow" width="600">
  <p><em>Real-time price adjustment visualization</em></p>
</div>
# 🅿️ Dynamic Pricing for Urban Parking Lots  
**Summer Analytics 2025 Capstone Project**  
Hosted by Consulting & Analytics Club × Pathway

---

## 🚀 Introduction

This project implements a real-time intelligent pricing engine for urban parking lots using live-streamed data.  
The system dynamically updates prices based on current occupancy, demand signals, and competitive conditions.

All processing is done using:
- 🐍 Python 3.10
- 🧮 Numpy & Pandas
- 📡 Pathway for real-time streaming
- 📊 Bokeh & Panel for interactive dashboards

---

## 🧠 Models Implemented

### ✅ Model 1: Baseline Linear Pricing  
Simple, interpretable, and occupancy-driven  
Formula:  
Price_t+1 = Price_t + α × (Occupancy / Capacity)



### ✅ Model 2: Demand-Based Pricing  
Includes:
- Occupancy ratio
- Queue length
- Traffic congestion
- Special day flag
- Vehicle type weights

Formula:  
Demand = α(Occupancy/Capacity) + βQueue - γTraffic + δEvent + εVehicleWeight
Price = BasePrice × (1 + λ × NormalizedDemand)



### ✅ Model 3: Competitive Pricing  
Adds spatial awareness and market intelligence:
- Computes haversine distance to nearby lots
- Adjusts price relative to competitor average within 0.5 km

Logic:
- Nearby lots cheaper → lower price
- Nearby lots full or expensive → raise price

---

## 📈 Core Data Pipeline

%%{init: {'theme': 'neutral', 'themeVariables': { 'primaryColor': '#ffdfd3'}}}%%
flowchart TD
    A[Parking Logs\nCSV/API] --> B{Data Preprocessor}
    B --> C[Historical Patterns]
    B --> D[Real-Time Stream]
    C --> E[Model Training]
    D --> F[Pathway Engine]
    E --> G[Pricing Models]
    F --> G
    G --> H[Price Optimizer]
    H --> I[Visualization Dashboard]
    H --> J[Parking Signs API]
    H --> K[Mobile Notifications]

%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#d4f1f9'}}}%%
graph TD
    subgraph Input Layer
        A[Current Occupancy]
        B[Queue Length]
        C[Traffic Data]
        D[Event Calendar]
    end

    subgraph Pricing Models
        E[Linear Base Price\n+15% per 20% occupancy]
        F[Demand-Based\nExponential curve]
        G[Competitive\nMarket-aware adjustment]
    end

    subgraph Output Layer
        H[Weighted Consensus Price]
        I[Surge Flag]
        J[Alternative Lot Suggestions]
    end

    A --> E
    B --> F
    C --> G
    D --> F
    E --> H
    F --> H
    G --> H
    H --> I
    G --> J

pie
    title Technology Distribution
    "Python 3.10" : 35
    "Pathway" : 25
    "Pandas/Numpy" : 20
    "Bokeh" : 15
    "Custom C Extensions" : 5
