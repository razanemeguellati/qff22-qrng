# Quantum Random Generation Challenge

<p float="middle" style="pointer-events:none;">
  <img align="middle" src="https://qiskit-fall-fest-algiers.wtmalgiers.org/_next/static/media/QiskitHero.94cd5459.png" width="26%"/>
  <picture>
  <img align="middle" width="54%"/>
  </picture>
  <img align="middle" src="logos/bleu_back_white_text_zoomed.png" width="18%"/>
  
</p>

This challenge is proposed by [Constantine Quantum Technologies](https://cqtech.org/) for the [Qiskit Fall Fest 2022 at Algiers](https://qiskit-fall-fest-algiers.wtmalgiers.org/) organized by [Women Techmakers Algiers](https://www.linkedin.com/company/wtm-algiers/) & [GDG Algiers](https://www.gdgalgiers.com/)

## Introduction

Random number generation is an essential subroutine for many algorithms and applications. There has been a lot of [progress to develop algorithms to generate random numbers on a classical computers (what is known as Pseudo-Random Number Generation)](https://towardsdatascience.com/where-does-python-get-its-random-numbers-from-81dece23b712). But as Von Neumann, said:

> Anyone who considers arithmetical methods of producing random digits is, of course, in a state of sin.

The reason for that is that the random numbers generated through arithmetic methods are reproducible and have repeating patterns and this is undesirable for many critical applications like cryptography. Ideally, we would like to build a random number generator which outputs unbiased bitstrings, unpredictable, and with high rate.

- **Unbiased**: the probability to have a `0` in the bitstring is equal to the probability to have a `1`, and the probability to have any sequence of bits is equal to the probability to have any other sequence of bits that has the same length.

- **Unpredictable**: if someone knows the algorithm/circuit used to generate the random numbers and also has access to other information like the `seed`, he should be unable to generate the same bitstring as you.

- **High rate**: the algorithm/circuit is able to output a large number of random bits.

## Tasks

For this challenge, you are asked to:

1. Write a paragraph to explain how can you use a quantum system/concept to generate a random bitstring.
generating a random bitstring using quantum concepts : 

so to generate a random number we can use qubits , a large number of qubits 
that we initialise in a superposition state , as an addition we use a normal python list
or a classicalregister and put the quantum register and the classical register ( or the 
list) in one single quantum circuit 
and then we measure the state of the qubit and put the result in an index of that classical 
register each time . 

2. Implement the ideas that you came up with in the above paragraph by coding a quantum circuit in Qiskit and execute it on a simulator `qasm_simulator`.

#Question2: 
#we can use 5 bits to test 
#decalring a quantum register with one bit 
qreg = QuantumRegister(1)
#decalring a classical register 
creg = ClassicalRegister(5)
qc = QuantumCircuit(qreg, creg)

qc.h(0)

qc.measure(0, 0) #measuring the first qubit and putting it in the first case of the classical register 
qc.measure(0, 1) 
qc.measure(0, 2) 
qc.measure(0, 3) 
qc.measure(0, 4) 
 
def execute(circuit, shots):

    backend = Aer.get_backend("qasm_simulator")

    results = backend.run(transpile(circuit, backend), shots = shots).result()
    return results.get_counts()


res=execute(qc, shots = 10)
print(res)
qc.draw()
#end of solution 
3. Try to execute your circuit on a fake noisy backend. What do you observe? Compare the results you got from the simulator and from the fake noisy backend (you can use a metric called `entropy`). Try to explain the difference?

4. Try to come up with a list of ideas to improve the results that you got in task (3)?
Q4:
to improve the results we can :
1-use a lot of qubits at once in the quantum register
2-use a loop and generate the result of multiple qubits
3-concatinate a small number of random result and get a bigger number 

5. Implement one (or more :)) of the ideas that you came up with in task (4) and try to improve the results of task (3).

6. Execute your circuit on a IBMQ real quantum-device.

**Notes**:

- **A bitstring**: is a sequence (list/array/string/...) of `0` and `1` e.g: `011010`.

- We expect the paragraphs in the tasks (1) and (4) to be detailed enough to show that you are understanding what you are doing and why you are doing it.

- Save the bitstrings generated in tasks (2), (3), (5), and (6) on the hard drive.

- The ideas of task (4) can be classical or quantum.

- If you implemented multiple ideas in task (5), try to compare them and see which one works best and try to explain why.

Have fun and we look forward to your submission :D !
