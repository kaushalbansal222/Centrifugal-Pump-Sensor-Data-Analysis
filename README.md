# Centrifugal Pump Sensor Data Analysis

**Exploratory Data Analysis | Industrial IoT | Feature Selection for Predictive Maintenance**

This project analyzes **real industrial pump sensor data** to uncover actionable insights that improve **predictive maintenance, fault detection, and sensor reliability** in rotating machinery.
The work goes beyond visualizations — it **detects pump operating modes, identifies redundant sensors to reduce hardware costs, and selects high-impact features for vibration prediction models.**

---

## 🚀 Why This Project Matters

Industrial pumps are critical in manufacturing, power, and oil & gas.
Failures lead to:

* expensive downtime,
* safety risks,
* unnecessary sensor redundancy costs.

This EDA project demonstrates how **data analysis directly improves reliability and cost efficiency**.

---

## 🎯 Project Objectives

| Objective                                     | Description                                                     | Real-World Impact                                                         |
| --------------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------- |
| **Operating Mode Detection**                  | Identify discrete pump motor speed settings                     | Helps detect abnormal mode shifts → enables early failure detection       |
| **Redundant Sensor Identification**           | Detect sensors measuring the same physical signal               | Reduces hardware & maintenance costs; simplifies data pipelines           |
| **Feature Selection for Predictive Modeling** | Select optimal features to predict **radial bearing vibration** | Increases predictive model accuracy & prevents unnecessary data ingestion |

---

## 📂 Datasets Used

| Dataset             | Usage                              | 
| ------------------- | ---------------------------------- |
| Clean Pump Data     | Mode detection & feature selection |  
| Sensor Data         | Redundancy detection               | 

> The datasets include **RPM, pressures, temperatures, vibrations, flow rates, and multiple redundant sensor channels.**

---

## 🧠 Key Insights & Results

### 1️⃣ **Pump Operates at Distinct RPM Levels**

Using histogram peak detection + clustering:

* **Identified *3 distinct operating speed modes***
* Approximate speeds include: **~2800 RPM, ~3600 RPM, ~4400 RPM**

> **Impact:** Enables mode-based monitoring instead of continuous monitoring → reduces false alerts.

---

### 2️⃣ **Found Redundant Sensors**

* Discovered sensor groups with ≥ 0.95 correlation
* Example: **Sensor I, J, K track the same signal pattern**
* **One sensor pair exhibited strong inverse relationship** → ideal for fault cross-checks

> **Impact:**
>
> * Companies can safely **remove redundant sensors**, cutting cost
> * Improves **feature selection stability** for ML pipelines

---

### 3️⃣ **Feature Selection Reduced Dimensionality**

By combining:

* correlation matrix,
* mutual information scores,
* domain-based redundancy check,

**Features eliminated:**
`Cluster, Pump Shaft Speed,Heat Recovery System Header Mass Flow.1, Pump Thrust Bearing Temperature 1, Lube Oil Tank Temperature -0.044991, Heat Recovery System Header Mass Flow, Pump Journal 2 Bearing Temperature, Pump Thrust Bearing Temperature 2, Lube Oil Cooler Outlet Temperature, Motor Current Phases B, C, Pump Discharge Volumetric Flow, Pump Discharge Pressure, Pump Suction Pressures 1 & 2`

*Reason:* Null values, Low variance, perfect redundancy, or weak vibration relation.

**Final predictive features selected:**
`Pump Discharge Pressure (strongest hydraulic predictor), Pump Suction Strainer Differential Pressure (strong hydraulic predictor, less redundant), Motor Current Phase A (electrical load indicator), Pump Thrust Bearing Temperature 1 (mechanical load / bearing stress)`

*justified through measurable vibration influence and non-redundancy.*

> **Impact:**
>
> * Ensures **model interpretability**
> * Avoids multicollinearity
> * Reduces training cost in real-time monitoring systems

---

## 📊 Tools & Techniques

| Category   | Tools / Methods                                                                             |
| ---------- | ------------------------------------------------------------------------------------------- |
| Language   | Python                                                                                      |
| Libraries  | Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn                                            |
| Techniques | KDE plots, clustering, correlation heatmaps, sensor redundancy mapping, feature elimination |

---

## 🧩 What I Learned 

* Applied **EDA for predictive maintenance** — not generic analysis
* Selected features based on **sensor physics + statistics**, not intuition
* Understood **how to reduce costs with redundancy detection**
* Connected **EDA → ML feature engineering pipeline**

---
