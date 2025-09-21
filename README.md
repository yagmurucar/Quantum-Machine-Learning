# Quantum-Machine-Learning
In the field of quantum machine learning, I created hybrid models by leveraging the documentation of **PennyLane** and **Qiskit**. I learned to integrate the training phases of classical models like **ResNet-18** with quantum circuits.

Quantum Machine Learning/ Qiskit or PannyLane

This is a file where I share simple examples for creating circuits in quantum machine learning. This file includes an example of creating a circuit using qiskit. ZZFeatureMap creates a four-qubit quantum circuit using a pre-built template. This circuit is used to transform classical data into quantum states. In short, it prepares the data encoding (feature mapping) circuit and shows us what it looks like.
feature_dimension=num_qubits: Specifies that the circuit will take 4 classical data features as input and encode them into 4 qubits.
reps=1: Specifies that the basic layer of the circuit (rotation and entanglement gates) will be repeated only once.
feature_map.decompose().draw(output="mpl", style="clifford", fold=20)
.decompose(): Decomposes a high-level template, such as ZZFeatureMap, into a sequence of more basic quantum gates, such as H, RZ, and CZ.


Another example was made using pannylane.


qml.BasisEmbedding takes a binary vector (consisting of 0s and 1s) and directly prepares it as a quantum ground state.
qml.AmplitudeEmbedding: This layer is used to encode continuous (floating-point) data into the amplitudes of the quantum state. This process ensures that the dimensionality of the data is set to 1, as required by quantum mechanics, with the parameter normalize=True.
qml.StronglyEntanglingLayers: This layer functions as a variational circuit (ansatz). It contains learnable parameters (weights) that the model will optimize during training, and gates that create entanglement between the qubits. Entanglement allows the model to capture complex relationships in the data.
qml.expval(qml.PauliZ(i)): This part receives the output of the circuit. expval stands for expectation value and calculates the average value obtained after a given measurement (in this case, Pauli-Z). These values ​​can be fed into a classical neural network as input and used for tasks such as classification.
diff_method="adjoint": This parameter specifies how gradients will be calculated. The adjoint method provides more efficient backpropagation, reducing memory usage, especially in circuits with many qubits and layers.
