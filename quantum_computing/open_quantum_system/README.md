## Evolution of Bell states in Amplitude Damping(AD) and Generalized Amplitude Damping(GAD) channel

### Overview 
   We have 2 qubit entangled states $$|\psi^-\rangle$$, shared between Alice and Bob.
   Compute fidelity, concurrence and other metrics when Alice evolved under below channels with different time and Gamma values.

   | Alice | Bob |
|-------|-----|
| AD    | AD  |
| AD    | GAD |
| GAD   | AD  |
| GAD   | GAD |


## Quantum Terms and Definitions

### Qubit
A **qubit** is the fundamental unit of quantum information, analogous to a bit in classical computing. Unlike a classical bit that can be either 0 or 1, a qubit can exist in a **superposition** of both 0 and 1 simultaneously, represented as a linear combination of these states.

### Superposition
**Superposition** refers to the quantum property where a qubit exists in a combination of multiple states at once. If a qubit is in a superposition, it can be described as a weighted combination of the basis states |0⟩ and |1⟩ until it is measured, collapsing into one of the states.

### Entanglement
**Entanglement** is a quantum phenomenon where two or more qubits become interconnected such that the state of one qubit is dependent on the state of the other(s), even when they are separated by large distances. Measuring one entangled qubit instantaneously affects the state of the other, regardless of the distance between them.

### Bell States
**Bell states** are specific maximally entangled quantum states of two qubits. There are four Bell states, which form the basis of two-qubit systems. They are key to many quantum algorithms and protocols, including quantum teleportation and superdense coding. The Bell states are:
- |Φ+⟩ = (|00⟩ + |11⟩) / √2
- |Φ−⟩ = (|00⟩ − |11⟩) / √2
- |Ψ+⟩ = (|01⟩ + |10⟩) / √2
- |Ψ−⟩ = (|01⟩ − |10⟩) / √2



### Fidelity
**Fidelity** is a measure of how close two quantum states are to each other. It is commonly used to assess the accuracy of quantum operations or the similarity between an ideal state and an experimental state. Fidelity values range from 0 to 1, where 1 indicates that the states are identical.

### Concurrence
**Concurrence** is a measure of quantum entanglement used primarily for two-qubit systems. It quantifies the degree of entanglement between qubits, with a value ranging from 0 (no entanglement) to 1 (maximum entanglement). Concurrence is especially useful for evaluating mixed quantum states.

### Open Quantum Systems
An **open quantum system** refers to a quantum system that interacts with an external environment, causing it to experience decoherence or loss of information. Unlike closed quantum systems, open systems cannot be described by a pure quantum state due to the influence of external factors.

### Amplitude Damping (AD) Channel
The **Amplitude Damping (AD) channel** models the loss of energy from a quantum system to its environment. It is typically used to describe spontaneous emission, where a qubit in the excited state |1⟩ decays to the ground state |0⟩, releasing energy.

- **Use case**: The AD channel describes real-world scenarios such as the decay of an excited atom (|1⟩) to a lower energy state (|0⟩) through the emission of a photon.
- **Effect on a qubit**: A qubit starting in the |1⟩ state may decay to the |0⟩ state with some probability determined by the damping factor \(\gamma\). Over time, the qubit tends to relax to the ground state |0⟩.
  
In this channel, there is no mechanism for the qubit to gain energy from the environment, so it only models energy loss.


## Kraus Operators for Amplitude Damping (AD) Channel

The Amplitude Damping (AD) channel models the energy loss in a quantum system, such as a qubit relaxing from an excited state |1⟩ to a ground state |0⟩. The Kraus operators for this channel are:

     $$ **K₀**: 
      
      K_0 = \begin{pmatrix}
      1 & 0 \\
      0 & \sqrt{1 - \gamma}
      \end{pmatrix}
      $$
     
  This operator corresponds to no decay, with probability \(1 - \gamma\).

      - **K₁**: 
        \[
        K_1 = \begin{pmatrix}
        0 & \sqrt{\gamma} \\
        0 & 0
        \end{pmatrix}
        \]
  
  This operator corresponds to the decay from state |1⟩ to state |0⟩, with probability \(\gamma\), where \(\gamma\) is the damping parameter.

### Generalized Amplitude Damping (GAD) Channel
The **Generalized Amplitude Damping (GAD) channel** is an extension of the AD channel, modeling systems in a thermal environment. It accounts for both energy loss and energy absorption. In this model, a qubit can decay from |1⟩ to |0⟩ (as in the AD channel), or be excited from |0⟩ to |1⟩ due to interactions with thermal energy.

- **Use case**: The GAD channel represents more realistic scenarios where a quantum system can exchange energy with a thermal environment. For example, an atom can absorb heat and become excited, or emit energy and relax.
- **Effect on a qubit**: The GAD channel accounts for both energy loss (decay from |1⟩ to |0⟩) and energy absorption (excitation from |0⟩ to |1⟩), depending on the temperature of the environment. The parameter \(p\) represents the thermal equilibrium, balancing decay and absorption.


## Kraus Operators for Generalized Amplitude Damping (GAD) Channel

The Generalized Amplitude Damping (GAD) channel extends the AD channel to a thermal environment, where the system can not only decay but also absorb energy. The Kraus operators for this channel are:

      - **K₀**:
        \[
        K_0 = \sqrt{p} \begin{pmatrix}
        1 & 0 \\
        0 & \sqrt{1 - \gamma}
        \end{pmatrix}
        \]

  This corresponds to no decay with probability \(p\) and relaxation probability \(1 - \gamma\).

      - **K₁**:
        \[
        K_1 = \sqrt{p} \begin{pmatrix}
        0 & \sqrt{\gamma} \\
        0 & 0
        \end{pmatrix}
        \]

  This corresponds to decay from state |1⟩ to state |0⟩ with probability \(\gamma\), scaled by \(p\).

      - **K₂**:
        \[
        K_2 = \sqrt{1 - p} \begin{pmatrix}
        \sqrt{1 - \gamma} & 0 \\
        0 & 1
        \end{pmatrix}
        \]

  This operator models no absorption with probability \(1 - p\) and decay probability \(1 - \gamma\).

      - **K₃**:
        \[
        K_3 = \sqrt{1 - p} \begin{pmatrix}
        0 & 0 \\
        \sqrt{\gamma} & 0
        \end{pmatrix}
        \]

  This operator models absorption of energy from state |0⟩ to state |1⟩, with probability \(\gamma\), scaled by \(1 - p\).

### Parameters:
- \(\gamma\): Damping factor representing energy loss.
- \(p\): Thermal equilibrium parameter representing the balance between decay and absorption in a thermal environment.
