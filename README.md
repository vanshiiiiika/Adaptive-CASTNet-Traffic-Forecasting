# Adaptive CASTNet: Traffic-State-Dependent Graph Sampling Attention for Multi-Horizon Traffic Flow Forecasting

## Project Overview

This project explores an adaptive graph-based deep learning approach for multi-horizon traffic flow forecasting. It investigates whether traffic-state-dependent graph sampling and attention can improve the representation of spatial relationships between traffic sensors.

The proposed **Adaptive CASTNet** builds upon the CASTNet architecture by incorporating dynamic query-key similarity to reweight and select relevant neighboring sensors from the existing road graph.

The experiments are conducted using the PEMS04 and PEMS08 traffic datasets.

## Research Objectives

- Study spatial and temporal dependencies in traffic flow data.
- Investigate adaptive graph sampling based on the latest traffic state.
- Incorporate graph attention to model relationships between traffic sensors.
- Evaluate multi-horizon traffic flow forecasting performance.
- Compare the proposed approach with baseline forecasting models.

## Proposed Methodology

The proposed architecture consists of the following major components:

1. **Spatial Graph Convolution:** Captures spatial relationships between connected traffic sensors.
2. **Temporal Convolution:** Extracts temporal patterns from historical traffic observations.
3. **Adaptive Graph Sampling:** Uses query-key similarity to estimate the relevance of neighboring sensors based on the latest traffic state.
4. **Top-K Neighbor Selection:** Selects the most relevant neighboring sensors, using K = 8.
5. **Multi-Head Graph Attention:** Learns weighted relationships among selected sensors.
6. **Feed-Forward Network:** Processes the learned representations to generate traffic flow predictions.

The model uses 12 historical time steps to forecast the next 12 time steps.

## Datasets

Experiments are conducted on two benchmark traffic datasets:

| Dataset | Number of Sensors | Time Steps | Sampling Interval |
|---|---:|---:|---|
| PEMS04 | 307 | 16,992 | 5 minutes |
| PEMS08 | 170 | 17,856 | 5 minutes |

- Input feature: Traffic flow.
- Historical input length: 12 time steps.
- Prediction horizon: 12 time steps.
- Data split: Chronological 60% training, 20% validation, and 20% testing.

The notebook includes the dataset preparation workflow.

## Experimental Results

The following results report the observed Mean Absolute Error (MAE) from the current experimental run.

| Dataset | Model | MAE |
|---|---|---:|
| PEMS04 | LSTM | 23.1587 |
| PEMS04 | CASTNet-Lite | 33.1354 |
| PEMS04 | Adaptive CASTNet | 33.3694 |
| PEMS08 | LSTM | 20.8131 |
| PEMS08 | CASTNet-Lite | 35.3573 |
| PEMS08 | Adaptive CASTNet | 35.8871 |

### Observations

- LSTM achieved the lowest MAE among the evaluated models on both datasets.
- Adaptive CASTNet did not outperform CASTNet-Lite on aggregate PEMS04 and PEMS08 MAE.
- The adaptive model contains 71,372 parameters, compared with 63,180 parameters in CASTNet-Lite.
- Further experimentation is required to establish the effectiveness of adaptive graph sampling.

**Note:** These results are from a single experimental seed (42). They should not be interpreted as multi-seed statistical evidence or state-of-the-art performance.

## Repository Structure

```text
Adaptive-CASTNet-Traffic-Forecasting/
│
├── Adaptive_CASTNet_Final_PEMS04_PEMS08.ipynb
├── Adaptive_CASTNet_Project_Presentation_.pptx
├── README.md
│
└── Research Papers/
    ├── IEEE format PDF
    └── Springer format PDF
```

The research papers are available as uploaded PDF files in the repository.

## How to Run

1. Clone or download this repository.
2. Open the Jupyter notebook in Google Colab or Jupyter Notebook.
3. Follow the notebook's dataset preparation and download instructions.
4. Install the dependencies specified in the notebook.
5. Execute the notebook cells sequentially.
6. Review the training process, evaluation metrics, and experimental comparisons.

A GPU-enabled runtime is recommended for model training.

## Limitations and Future Work

- Current PEMS experiments use a single random seed.
- Adaptive CASTNet has not demonstrated an aggregate MAE improvement over CASTNet-Lite in the reported experiments.
- Further evaluation across multiple random seeds is needed.
- Additional experiments could investigate different graph sampling strategies, top-K values, and attention configurations.
- Further benchmarking on additional traffic datasets may help assess generalization.

## Technologies Used

- Python
- PyTorch
- NumPy
- Pandas
- Matplotlib
- Jupyter Notebook
- Google Colab
- Graph Neural Networks
- Deep Learning
- Traffic Flow Forecasting

## Project Deliverables

This repository contains:

- Research implementation notebook.
- IEEE-format research paper.
- Springer-format research paper.
- Project presentation.

## Acknowledgements

The experiments use the publicly available PEMS04 and PEMS08 traffic datasets. The work builds upon existing research in graph neural networks and spatio-temporal traffic forecasting.

---

**Research Project:** Adaptive CASTNet  
**Application Domain:** Intelligent Transportation Systems and Traffic Forecasting
