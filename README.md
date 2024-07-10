# Quantum Walk Implementation in Qiskit

This repository contains an implementation of a quantum walk using Qiskit. The code defines functions to create and manipulate quantum circuits, specifically for implementing a quantum walk using multi-controlled X gates and unitary gates.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Functions](#functions)

## Installation

To use this code, you need to have Qiskit installed. You can install it using pip:

```bash
pip install qiskit
```

## Usage

You can use the provided functions to create quantum circuits that implement a quantum walk. Below is an example of how to use these functions:

```python
from qiskit import Aer, execute
from your_module_name import create_coin, circuit_initialized_qw_steps

# Create a quantum circuit for a quantum walk with specific parameters
num_qubits = 7
num_steps = 5
angle = 1
bitString = '000000'

circuit, coin = initialize_quantum_circuit(qubits=num_qubits, angle=angle, bitString=bitString)
circuit = circuit_initialized_qw_steps(num_qubits=num_qubits, num_steps=num_steps, angle=angle, bitString=bitString)

# Simulate the circuit
simulator = Aer.get_backend('aer_simulator')
result = execute(circuit, backend=simulator).result()

# Get the results
counts = result.get_counts(circuit)
print(counts)
```

## Functions

### `create_coin(angle=1)`

Creates a coin operator using a unitary gate.

**Parameters:**
- `angle` (float): The angle parameter for the coin operator.

**Returns:**
- `coin` (UnitaryGate): The coin operator.

### `incrementBlock(circuit)`

Adds the increment block to the quantum circuit.

**Parameters:**
- `circuit` (QuantumCircuit): The quantum circuit to which the increment block is added.

### `decrementBlock(circuit)`

Adds the decrement block to the quantum circuit.

**Parameters:**
- `circuit` (QuantumCircuit): The quantum circuit to which the decrement block is added.

### `initialize_quantum_circuit(qubits=2, angle=1, bitString='000000')`

Initializes a quantum circuit with a specific number of qubits, angle, and initial bit string.

**Parameters:**
- `qubits` (int): Number of qubits in the circuit.
- `angle` (float): Angle parameter for the coin operator.
- `bitString` (str): Initial bit string for the quantum register.

**Returns:**
- `circuit_base` (QuantumCircuit): The initialized quantum circuit.
- `coin` (UnitaryGate): The coin operator.

### `get_single_step(qubits, coin)`

Creates a single step of the quantum walk.

**Parameters:**
- `qubits` (int): Number of qubits in the circuit.
- `coin` (UnitaryGate): The coin operator.

**Returns:**
- `one_step_gate` (Instruction): The single step gate for the quantum walk.

### `circuit_initialized_qw_steps(num_qubits=7, num_steps=1, angle=1, bitString='000000')`

Creates a quantum walk circuit with a specified number of steps.

**Parameters:**
- `num_qubits` (int): Number of qubits in the circuit.
- `num_steps` (int): Number of steps in the quantum walk.
- `angle` (float): Angle parameter for the coin operator.
- `bitString` (str): Initial bit string for the quantum register.

**Returns:**
- `circuit` (QuantumCircuit): The quantum walk circuit.

### `list_of_index_proba(quasi_probs)`

Generates a list of indices and their corresponding probabilities from quasi-probabilities.

**Parameters:**
- `quasi_probs` (dict): Quasi-probabilities.

**Returns:**
- `list_of_index` (list): List of indices.
- `list_of_proba` (list): List of probabilities.

### `get_quasi_dist_in_executions(sampler, execution_number=10, angles=[-2, 2])`

Generates quasi-distributions for a series of executions with specified angles.

**Parameters:**
- `sampler` (Sampler): Qiskit sampler.
- `execution_number` (int): Number of executions.
- `angles` (list): List of angles.

**Returns:**
- `list_quasi_probs` (list): List of quasi-distributions.

### `get_quasi_dist_in_transformation(sampler, execution_number=10, angles=[-2, 2])`

Generates quasi-distributions for a series of executions with a transformation applied.

**Parameters:**
- `sampler` (Sampler): Qiskit sampler.
- `execution_number` (int): Number of executions.
- `angles` (list): List of angles.

**Returns:**
- `list_quasi_probs` (list): List of quasi-distributions.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
