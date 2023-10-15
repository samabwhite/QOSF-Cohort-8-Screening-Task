
# Quantum Decomposition: QOSF Task 3 
This repository provides a detailed exploration into quantum gate decomposition, with a focus on the Toffoli (controlled-controlled-X) gate, CCCX gate, their optimizations, and further applications in the construction of multi-controlled-X gates.

*Thank you for considering my application!*

## The Problem 
Using the U and CX gates shown below, decompose the matrices to obtain CCX and CCCX gates. As a bonus, create a method for constructing any multi-controlled X gate.

## My Solution
You can find my fully documented solution in the **QOSF-Task3-Screening.ipynb** Jupyter Notebook. For convenience, my solution will be featured at the top of the file, while my process and research is featured towards the bottom. 

## My Approach
There are countless research papers that offer established solutions to all 3 of the problems in this task. My goal was not to copy their implementations, but to instead learn the process of decomposing a circuit. Below I feature some of the fundamental concepts that I used for my decomposition. 

### Toffoli (CCX) Decomposition
**Gate Depth:** 12  
**Ancilla:** 0

Decomposing the Toffoli gate felt like a recursive decomposition where I first needed to break down a 2-Control Unitary gate and then a 1-Control Unitary gate.

*First, we tackled the 2-Control Unitary gate by finding the square root of our unitary transformation (X), which will be our V.*

![image](https://i.stack.imgur.com/Pu2er.png)

*Next, to decompose further, we break our V down into an A, B, C, and alpha gate using ZYZ decomposition.*

![image2](https://miro.medium.com/v2/resize:fit:1400/1*d_I1vCjnGJfPMD9EnayzGA.png)

### CCCX Decomposition
**Gate Depth:** 33  
**Ancilla:** 1  

Decomposing the CCCX was simply an expansion of the previously decomposed Toffoli gate. We can use this algorithm to create any MCX gate with n-2 ancilla qubits where n is the number of control qubits. In this case it was 3 control qubits, 3 Toffoli gates, and 1 ancilla. 

![image3](https://i.stack.imgur.com/lSvZD.png)


### MCX Method (Bonus)
Taking inspiration from the previous CCCX Decomposition and the MCU Decomposition seen below, we can create an algorithm to create a form of both. This follows the same n-2 ancilla qubits. Since our unitary gate would be redundant, we can remove this as well as an excess ancilla.

![image4](https://i.stack.imgur.com/PtdeW.png)


## References
Barenco, A., Bennett, C. H., Cleve, R., DiVincenzo, D. P., Margolus, N., Shor, P., Sleator, T., Smolin, J. A., & Weinfurter, H. (1995). Elementary gates for quantum computation. Physical Review A, 52(5), 3457-3467. https://doi.org/10.1103/physreva.52.3457

Baker, J. M., Duckering, C., Hoover, A., & Chong, F. T. (2019). Decomposing Quantum Generalized Toffoli with an Arbitrary Number of Ancilla. arXiv preprint arXiv:1904.01671. https://arxiv.org/abs/1904.01671

Crooks, G. E. (2023). Gates, States, and Circuits: Notes on the circuit model of quantum computation (Tech. Note 014 v0.9.0 beta). https://threeplusone.com/gates
