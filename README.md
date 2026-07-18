# Flight Ops GUI

A desktop front end for the same flight-routing and safety-scoring system
behind [SkAI](https://github.com/AryaanPe/SkAI---Flight-route-optimizer),
the flight route optimizer built for the Datathon 2.0 hackathon (hosted by
Analytika), where it reached the final round out of 300+ teams.

That project scores airport safety from weather data and reroutes around
unsafe stops with Dijkstra's algorithm. This repo wraps the same logic
(`RouteOptimization.py`, `SafetyLevel.py`) in a Tkinter desktop app, and
adds a second model: `ServiceStatus.py`, a Random Forest that predicts an
aircraft's maintenance status from days since servicing, warranty status,
and days since purchase, so the interface can flag operational risk
alongside weather risk.

## Setup

```bash
pip install -r requirements.txt
python UI_MAIN.py
```

## Files

| File | Purpose |
|---|---|
| `UI_MAIN.py` | Tkinter application: loads the trained models and data, builds the graph, and renders the interface. |
| `RouteOptimization.py` | Builds the city graph from flight-duration data and finds the optimized route with Dijkstra's algorithm. |
| `SafetyLevel.py` | Trains an MLP classifier that scores airport weather safety. |
| `ServiceStatus.py` | Trains a Random Forest that predicts aircraft maintenance status. |
| `*.csv` | Flight, city, and weather data the models train and run on. |
