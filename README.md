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

Planned future updates include cleaner and more optimized implementations.

---

## Introduction

This repository contains implementations and experiments for large-scale CVRP based on a unified neural divide-and-conquer framework.

Recent neural combinatorial optimization solvers achieve strong performance on small-scale routing problems but often exhibit severe performance degradation when scaling to large-scale instances.

This project explores scalable routing optimization by integrating:

1. Neural dividing policies
2. Constructive conquering policies
3. Reinforcement learning
4. Graph neural networks
5. Heatmap-based routing strategies

The framework is inspired by recent advances in neural divide-and-conquer optimization for large-scale combinatorial optimization problems.

---

## Framework Overview

The optimization pipeline follows a Divide-Conquer-Reunion (DCR) process.

### 1. Dividing Stage

A lightweight Graph Neural Network (GNN) generates a heatmap representation of the routing instance and constructs an initial global solution.

The dividing policy decomposes large-scale CVRP instances into multiple fixed-length sub-problems.

Main characteristics:

* Sparse graph construction
* Heatmap-based neural policy
* Global route approximation
* Large-scale route partitioning

---

### 2. Conquering Stage

Each sub-problem is optimized independently using a constructive neural routing solver.

The conquering stage focuses on:

* Local route refinement
* Capacity feasibility
* Sub-route optimization
* Solution quality improvement

Optimized sub-solutions are merged into a complete routing solution.

---

### 3. Reunion Stage

The reunion mechanism repairs poor boundary connections between adjacent sub-problems caused by sub-optimal decompositions.

This additional optimization stage improves:

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
* Divide-Conquer-Reunion training pipeline

---

### CVRPTester.py

Evaluation framework for trained models.

Responsible for:

* Benchmark testing
* Route validation
* Performance evaluation

---

## Dependencies

Recommended environment:

```text
Python = 3.11
torch = 2.7.1
torch-geometric = 2.7.0
networkx = 3.4.2
numpy = 2.1.0
```

Install dependencies:

```bash
pip install torch numpy networkx torch-geometric
```

---

## Data & Pretrained Models

The framework is trained using reinforcement learning on randomly generated CVRP instances.

Problem generation examples are provided in:

```text
CVRPProblemDef.py
```

Pretrained models and benchmark datasets can be downloaded from:

https://drive.google.com/file/d/1lVWBPvxhHDd-ZLJNCorGJugi_Smrx8uh/view?usp=sharing

---

## Training

Train the model:

```bash
python train_udc_n500_n1000.py
```

---

## Evaluation

Run evaluation:

```bash
python CVRPTester.py
```

---

## Reproducibility

Download pretrained models and benchmark datasets to reproduce the experimental results.

Important notes:

* The framework uses O(N²) memory complexity during parallel GNN computations.
* Large-scale routing instances may require moving distance matrices or heatmaps to CPU memory.
* Experimental results may vary due to randomness and different batch sizes.

For randomly generated instances, reported results are obtained using maximum feasible batch sizes on a single NVIDIA RTX 3090 GPU.

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

## Future Work

Possible future improvements include:

* Better decomposition policies
* More memory-efficient GNN architectures
* Hybrid neural-exact optimization
* Multi-stage route refinement
* Distributed training
* Generalization to other routing problems

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
