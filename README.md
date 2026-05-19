# UDC-Large-Scale-CVRP

Implementation of a unified neural divide-and-conquer framework for solving large-scale Capacitated Vehicle Routing Problems (CVRP).

This repository focuses on scalable neural combinatorial optimization methods combining:

* Reinforcement Learning (RL)
* Graph Neural Networks (GNNs)
* Heatmap-based neural routing
* Divide-and-Conquer optimization
* Large-scale vehicle routing

---

# Introduction

Neural combinatorial optimization solvers achieve strong performance on small-scale routing problems but often suffer from significant performance degradation on large-scale instances.

This project explores a unified divide-and-conquer framework for large-scale CVRP. The framework combines:

1. A neural dividing policy for global route decomposition
2. A constructive neural conquering policy for local sub-problem optimization
3. A reunion mechanism for repairing sub-optimal decompositions

The framework is inspired by recent advances in large-scale neural combinatorial optimization.

---

# Problem Description

The Capacitated Vehicle Routing Problem (CVRP) is a classical NP-hard combinatorial optimization problem where:

* A fleet of vehicles starts from a depot
* Each customer has a demand
* Each vehicle has limited capacity
* Every customer must be visited exactly once
* The objective is to minimize total routing cost

Large-scale CVRP instances are particularly challenging due to increasing computational complexity and memory consumption.

---

# Framework Overview

The framework follows a Divide-Conquer-Reunion (DCR) optimization process.

## 1. Dividing Stage

A lightweight Graph Neural Network (GNN) generates a heatmap representation of the routing instance and produces an initial global routing solution.

The large-scale instance is decomposed into multiple fixed-length sub-problems.

Main characteristics:

* Sparse graph construction
* Heatmap-based neural policy
* Global route approximation
* Large-scale instance partitioning

---

## 2. Conquering Stage

Each sub-problem is independently optimized using a constructive neural solver.

The conquering stage focuses on:

* Local route refinement
* Capacity feasibility
* Sub-route optimization
* Solution quality improvement

Optimized sub-solutions are merged into a complete routing solution.

---

## 3. Reunion Stage

The reunion mechanism repairs poor boundary connections between adjacent sub-problems caused by sub-optimal decompositions.

This additional optimization stage improves:

* Route continuity
* Boundary node connections
* Final routing quality
* Training stability

---

# Repository Structure

```text
project/
│
├── data/                      # Benchmark datasets
├── models/                    # Saved models
├── results/                   # Experimental outputs
├── utils/                     # Utility functions
│
├── train.py                   # Training pipeline
├── test.py                    # Evaluation pipeline
├── Tester.py                  # Testing framework
├── Trainer.py                 # RL training framework
│
├── model.py                   # Neural architectures
├── GNN.py                     # Graph neural network
├── decoder.py                 # Constructive decoder
│
├── CVRPEnv.py                 # CVRP environment
├── CVRPProblemDef.py          # Problem generation
├── heatmap.py                 # Heatmap generation
│
└── README.md
```

---

# Dependencies

Recommended environment:

```text
Python 3.9
PyTorch >= 1.12
torch-geometric >= 2.4
NumPy
NetworkX
Matplotlib
```

Install dependencies:

```bash
pip install torch numpy networkx matplotlib torch-geometric
```

---

# Training

Train the neural solver:

```bash
python train.py
```

---

# Evaluation

Evaluate trained models:

```bash
python test.py
```

---

# Benchmark Instances

The framework supports experiments on:

* Large-scale CVRP instances
* Randomly generated routing datasets
* Synthetic benchmark instances

---

# Reinforcement Learning Framework

The framework adopts reinforcement learning for training both:

* Dividing policy
* Conquering policy

Training is based on:

* REINFORCE
* Heatmap-based routing policies
* Divide-Conquer-Reunion (DCR) optimization

---

# Features

* Unified divide-and-conquer framework
* RL-based routing optimization
* GNN-based decomposition
* Heatmap-based route generation
* Large-scale CVRP support
* Scalable neural optimization
* End-to-end training pipeline

---

# Research Topics

This project involves:

* Neural Combinatorial Optimization
* Reinforcement Learning
* Graph Neural Networks
* Vehicle Routing Problems
* Large-scale Optimization
* Divide-and-Conquer Optimization

---

# Future Work

Possible future improvements include:

* Better decomposition strategies
* Memory-efficient GNN architectures
* Hybrid neural-exact optimization
* Multi-stage route refinement
* Distributed training
* Generalization to other routing problems

---

# License

This project is intended for research and educational purposes.
