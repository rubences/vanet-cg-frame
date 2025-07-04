# VANET CG+Frame Reasoning Framework

**Framework for distributed, real-time reasoning in Vehicular Ad-Hoc Networks (VANETs) using integrated conceptual graphs and frame-based knowledge representation.**

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## 📖 Description

This repository implements a novel middleware that couples:
- **Conceptual Graphs (CGs):** Bipartite graphs modeling inter-entity relations (e.g., `send`, `located_in`, `propagate`).
- **Frame-Based Schemas:** Modular frames for vehicles and messages with dynamic slots (position, speed, TTL) and procedural attachments (e.g., `update_position()`, `decrement_ttl()`).

It provides:
- A **reasoning engine** (Horn-clause solver) embedded in each simulated vehicle.
- **NS-3.35** simulation scripts (IEEE 802.11p) for urban VANET scenarios.
- **Python** scripts for data processing and figure generation.
- Configuration files for simulation parameters and CG rule sets.

## 📂 Repository Structure

- **vanet-cg-frame/**  
  Top-level project directory  

  - **ns3/**  
    NS-3.35 simulation scenarios and configuration  
    - `scratch/`  
      Custom simulation scripts (e.g., `vanet_cg_frame.cc`)  
    - `wscript`  
      Build configuration for Waf  
    - `helpers/`  
      Utility modules (mobility models, MAC tweaks)  

  - **reasoning/**  
    Core reasoning engine implementation  
    - `cg_constructor.py`  
      Builds conceptual graph from frame data  
    - `frame_manager.py`  
      Manages frame instances and procedural attachments  
    - `horn_solver.py`  
      Lightweight Horn-clause forward-chaining solver  
    - `utils.py`  
      Shared data structures, serialization, logging  

  - **data/**  
    Simulation outputs and trace files  
    - `delivery_ratio.csv`  
      Aggregated delivery ratio results  
    - `latency.csv`  
      End-to-end latency measurements  
    - `raw_traces/`  
      Per-run NS-3 trace logs  

  - **analysis/**  
    Data processing and visualization  
    - `plot_delivery.py`  
      Generates Delivery Ratio vs. TTL chart  
    - `plot_latency.py`  
      Generates Latency vs. TTL chart  
    - `plot_scalability.py`  
      Generates density-impact figures  
    - `notebooks/`  
      Optional Jupyter analyses and tutorials  

  - **docs/**  
    Manuscript and supplementary materials  
    - `manuscript.tex`  
      LaTeX source for the article  
    - `figures/`  
      TikZ diagrams and PDF plots  
    - `bibliography.bib`  
      BibTeX references  

  - `LICENSE`  
    MIT license file  
  - `README.md`  
    Project overview and usage instructions  




## ⚙️ Requirements

- **NS-3.35** with IEEE 802.11p module
- **Python 3.8+** with:
  - `numpy`
  - `pandas`
  - `matplotlib`
- **LaTeX** distribution for manuscript compilation

## 🚀 Installation & Usage

1. **Clone the repository**
   ```bash
   git clone https://github.com/rubences/vanet-cg-frame.git
   cd vanet-cg-frame


2. **Run NS-3 simulations**

   ```bash
   cd ns3
   ./waf build
   ./waf --run scratch/vanet_cg_frame --simulationTime=300
   ```

3. **Process results & generate figures**

   ```bash
   cd analysis
   python plot_delivery.py ../data/delivery_ratio.csv
   python plot_latency.py ../data/latency.csv
   ```

4. **Compile the manuscript**

   ```bash
   cd docs
   pdflatex manuscript.tex
   bibtex manuscript
   pdflatex manuscript.tex
   pdflatex manuscript.tex
   ```

## 📝 Contribution

Contributions are welcome! Please open an issue or submit a pull request with your enhancements, bug fixes, or new simulation scenarios.

## 📜 License

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.


