# RTDADM Midterm Project
## Real-Time Data Collection and Stream Processing System

**Student:** Galymzhan Tamirlan Galymzhanuly | ID: 240542 | Group: BDA-2407  
**Course:** Real-Time Data Analysis and Decision Making (RTDADM)  
**University:** Astana IT University, 2026–2027  
**GitHub Repository:** [https://github.com/mtake-da/Midterm_RTDADM](https://github.com/mtake-da/Midterm_RTDADM)

---

## What This Project Does

I built a real-time stream processing system that monitors a classroom (Room C1.3.101 at AITU) using simulated IoT sensor data. The system processes one record per minute, cleans missing values online, computes rolling statistics, and raises alerts when something goes wrong.

I reused the same classroom dataset from Assignment 2 as the starting point and extended it into a full 60-minute lecture simulation.

## Project Files

| File | Description |
|------|-------------|
| `Midterm_Project.ipynb` | **Main notebook** — run this to see everything |
| `stream_generator.py` | Generates the 60-minute sensor stream |
| `stream_processor.py` | Incremental stream processing engine |
| `report.tex` | Technical report (LaTeX source) |
| `report.pdf` | Compiled PDF report |
| `stream_dashboard.png` | Output dashboard figure |
| `build_notebook.py` | Script to regenerate the notebook from scratch |

## How to Run

```bash
# Run the notebook in Jupyter
jupyter notebook Midterm_Project.ipynb

# Or just regenerate everything
python3 build_notebook.py
```

## Stream Phases

The 60-minute stream has these phases:
- **10:00–10:11** — Assignment 2 baseline data (real records)
- **10:12–10:25** — Stable lecture period
- **10:26–10:35** — Ventilation failure → CO₂ spikes
- **10:36–10:45** — Overheating → temperature crosses 24°C
- **10:46–10:50** — Electrical surge → power above 6 kW
- **10:51–10:59** — Lecture ends, students leave

## Anomaly Types Detected

| Alert | Condition |
|-------|-----------|
| SENSOR_DROPOUT | Missing sensor value (imputed) |
| CO2_HIGH | CO₂ > 1000 ppm |
| CO2_CRITICAL | CO₂ > 1200 ppm |
| OVERHEATING | Temperature > 24°C |
| UNDERHEATING | Temperature < 20°C |
| POWER_SURGE | Power > 6.0 kW |
| RAPID_OCC_CHANGE | Occupancy changes ≥ 6 persons/min |
