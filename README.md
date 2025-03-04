# Machine Learning Based Quanutm Circuit Optimisation
## Training RandomForestClassifier on TKET quantum circuits to reccomend optimisation passes

## Overview

This project trains a machine learning model to predict the optimal TKET optimization pass for unoptimized quantum circuits, aiming to minimize gate counts. The process starts with generating random circuits in Qiskit, converting them to TKET format, and extracting features like qubit count and gate tallies. These features train a Random Forest Classifier to select the best optimisation pass based on gate reduction.

- **Dataset**: 48 circuits with 2-5 qubits and depths 1-4, generated and left unoptimized. Data set could be increased in size - I chose to begin with a small dataset to focus on building the ML-pipeline before scaling up.
- **Features**: Seven metrics, including connectivity and CNOT counts, drive predictions. 
- **Passes**: Three TKET optimizations are tested per circuit: CliffordSimp, FullPeepholeOptimise, and PauliSimp.
- **Train-Test Split**: The training data is split 80-20 training to test data.
- **Training and Evaluation**: The odel is trained and achieves 90% on the test data.
- **Application**: Correctly predicts CliffordSimp for a sample 4-qubit circuit, demonstrating ability to accuratley predict the correct optimisation pass for individual circuits (up to 90%).

The jupyter notebook file is well documented, so please view tket-ML-optimisation.ipynb to see descriptions and commented code in more detail.
