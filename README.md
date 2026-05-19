# UDC-Large-Scale-CVRP

Implementation of a unified neural divide-and-conquer framework for solving large-scale Capacitated Vehicle Routing Problems (CVRP).

This repository focuses on scalable neural combinatorial optimization methods combining:

* Reinforcement Learning (RL)
* Graph Neural Networks (GNNs)
* Heatmap-based neural routing
* Divide-and-Conquer optimization
* Large-scale vehicle routing

---

## Updates

### 2024.11.25

Fixed a bug in the CVRP implementation caused by an unnecessary legality check during decoding, which previously resulted in extremely low efficiency.

Future updates will focus on cleaner implementations and better computational efficiency.

---

## Introduction

Recent neural combinatorial optimization solvers achieve strong performance on small-scale routing problems but often suffer from severe performance degradation on large-scale instances.

This project explores scalable routing optimization through a unified divide-and-conquer framework integrating:

1. Neural partitioning policies
2. Constructive routing solvers
3. Reinforcement learning
4. Graph neural networks
5. Heatmap-based optimization

The framework is designed for large-scale CVRP optimization.

---

## Framework Overview

The optimization pipeline follows a Divide-Conquer-Reunion (DCR) process.

### Dividing Stage

A lightweight Graph Neural Network generates a heatmap representation of the routing instance and constructs an initial global routing solution.

The dividing policy decomposes large-scale CVRP instances into multiple fixed-length sub-problems.

Main characteristics:

* Sparse graph construction
* Heatmap-based routing
* Global route approximation
* Neural partitioning

---

### Conquering Stage

Each sub-problem is independently optimized using a constructive neural routing solver.

The conquering stage focuses on:

* Local route refinement
* Capacity feasibility
* Sub-route optimization
* Solution quality improvement

---

### Reunion Stage

The reunion mechanism repairs poor boundary connections between adjacent sub-problems caused by sub-optimal decompositions.

This stage improves:

* Route continuity
* Boundary node connections
* Final routing quality
* Training stability

---

## Repository Structure

```text
udc-large-scale-co/
│
├── UDC/
│   ├── CVRP-AGNN-ICAM/
│   │   ├── CVRPEnv.py
│   │   ├── CVRPModel.py
│   │   ├── CVRPTester.py
│   │   ├── CVRPTesterlib.py
│   │   ├── CVRPTrainerPartition.py
│   │   ├── PartitionModel.py
│   │   ├── test_lib.py
│   │   ├── test_rrc.py
│   │   └── train_udc_n500_n1000.py
│   │
│   ├── utils/
│   │   └── utils.py
│   │
│   └── CVRPProblemDef.py
│
├── README.md
└── .gitignore
```

---

## Main Components

### CVRPModel.py

Implementation of the neural routing model for CVRP.

Includes:

* Encoder-decoder architecture
* Heatmap generation
* Neural routing policy
* Route construction

---

### PartitionModel.py

Implements the neural partitioning model used in the dividing stage.

Responsible for:

* Large-scale instance decomposition
* Sub-problem generation
* Route partitioning

---

### CVRPTrainerPartition.py

Training framework for reinforcement learning optimization.

Includes:

* Policy training
* Reward computation
* Divide-Conquer-Reunion optimization

---

### CVRPTester.py

Evaluation framework for trained models.

Responsible for:

* Benchmark testing
* Route validation
* Performance evaluation

---

### CVRPEnv.py

Environment definition for CVRP reinforcement learning training and evaluation.

---

### CVRPProblemDef.py

Problem generation and instance construction for CVRP datasets.

---

## Dependencies

Recommended environment:

```text
Python = 3.9
torch = 1.12.1
torch-geometric = 2.4.0
networkx = 2.6.3
numpy = 1.22.4
```

Install dependencies:

```bash
pip install torch numpy networkx torch-geometric
```

---

## Training

Train the model:

```bash
python UDC/CVRP-AGNN-ICAM/train_udc_n500_n1000.py
```

---

## Evaluation

Run evaluation:

```bash
python UDC/CVRP-AGNN-ICAM/CVRPTester.py
```

---

## Reproducibility

The framework uses O(N²) memory complexity during parallel GNN computations.

For extremely large routing instances, distance matrices and heatmaps may need to be stored on CPU memory.

Experimental results may vary due to:

* Random initialization
* Batch size differences
* GPU memory limitations

Reported large-scale experiments are conducted using NVIDIA RTX 3090 GPUs.

---

## Research Topics

This project involves:

* Neural Combinatorial Optimization
* Reinforcement Learning
* Graph Neural Networks
* Vehicle Routing Problems
* Large-scale Optimization
* Divide-and-Conquer Optimization

---

## Acknowledgements

Some implementations are inspired by:

* POMO
* MatNet
* GLOP

We sincerely thank the original authors for their excellent work.

---

## License

This project is intended for research and educational purposes.
