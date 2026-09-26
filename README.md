# Grover's Algorithm — Quantum Search Demo

A hands-on implementation of Grover's Search Algorithm using Qiskit, built while learning the fundamentals of quantum computing (qubits, superposition, and quantum simulators) from scratch.

## What this does

Given a "secret number" hidden among 8 possibilities (3 qubits = 2³ states), this notebook builds a quantum circuit that finds it with much higher probability than classical random guessing — demonstrating the core idea behind Grover's algorithm: a quadratic speedup for unstructured search problems.

Classically, finding one item among 8 unsorted possibilities takes ~4 checks on average. Grover's algorithm finds it in roughly √8 ≈ 3 steps by using superposition, an "oracle" to mark the answer, and a "diffuser" to amplify its probability — repeated the optimal number of rounds.

## How it works (high level)

1. **Superposition** — all 8 possibilities start with equal probability (via Hadamard gates)
2. **Oracle** — secretly flips the sign of the correct answer's amplitude, without revealing it
3. **Diffuser** — reflects all amplitudes around their average, amplifying the marked answer and shrinking the rest
4. **Repeat** — oracle + diffuser are repeated an optimal number of times (calculated via `(π/4)√N`)
5. **Measure** — collapse the qubits and observe the result; the secret number appears with high probability (~90%+ for this 3-qubit example)

## Tech used

- **Python**
- **Qiskit** — quantum circuit construction
- **Qiskit Aer** — local quantum simulator (runs on CPU, mimics real QPU behavior)
- **Google Colab** — development environment

## Note on QPUs vs. simulation

This runs on a **local simulator**, not real quantum hardware. Grover's algorithm is designed to give a genuine speed advantage on real quantum processors (QPUs), but simulating it locally lets you build, test, and understand the exact same logic without needing (limited, often paid) real QPU access. At small scales like this one, the simulator does the same computation classically would — the real advantage only shows up at much larger qubit counts.

## Running it

Open the notebook in Google Colab and run the cells in order:

!pip install qiskit qiskit-aer pylatexenc -q

Then build the circuit, define your secret number, and run — the final cell outputs a histogram showing the secret number dominating the measurement results.

## What I learned

- How qubits differ from classical bits (superposition vs. definite states)
- Why the oracle alone doesn't help — it's the oracle **and** diffuser together that create the probability boost
- Why there's an optimal number of algorithm rounds, and why over-rotating past that point actually decreases your success probability
- The practical difference between simulating a quantum algorithm and running it on real quantum hardware
