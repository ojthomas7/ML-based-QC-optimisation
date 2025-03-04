# Machine Learning Based Quanutm Circuit Optimisation
## Training RandomForestClassifier on TKET quantum circuits to reccomend optimisation passes

## Overview

This project trains a machine learning model to predict the optimal TKET optimization pass for unoptimized quantum circuits, aiming to minimize gate counts. The process starts with generating random circuits in Qiskit, converting them to TKET format, and extracting features like qubit count and gate tallies. These features train a Random Forest Classifier to select the best pass—CliffordSimp, FullPeepholeOptimise, or PauliSimp—based on gate reduction. Key details include:

- **Dataset**: 48 circuits with 2-5 qubits and depths 1-4, generated and left unoptimized.
- **Features**: Seven metrics, including connectivity and CNOT counts, drive predictions.
- **Passes**: Three TKET optimizations are tested per circuit.
- **Accuracy**: Model achieves up to 100% on a 20% test set.
- **Application**: Correctly predicts CliffordSimp for a sample 4-qubit circuit.

## Implementation

The implementation uses Qiskit to generate 48 random circuits with qubit counts from 2 to 5 and depths from 1 to 4, each repeated three times for variety. These are transpiled into a TKET-compatible basis (Hadamard, CNOT, Rz, T gates) without optimization, then converted to TKET’s Circuit format. Features extracted include number of qubits, depth, counts of CNOT, Hadamard, Rz, and T gates, and a connectivity metric averaging qubit interactions via CNOT gates. A Random Forest Classifier, trained on 80% of this data, evaluates three TKET passes on each circuit, selecting the one with the largest gate reduction. Testing on the remaining 20% yields up to 100% accuracy, with connectivity (25.9%) and CNOT counts (21.4%) as top predictors. For a sample circuit with 4 qubits, 27 depth, and 6 CNOT gates, it accurately suggests CliffordSimp, streamlining optimization efforts.
