"# CSCI6212-Project1" 
# Asymptotic Analysis Simulation

This project simulates and times an algorithm with a theoretical running time of approximately  
\(T(n) \propto n^{2/3}\log n\). The Python script measures the runtime for different input sizes `n`  
and compares it with the theoretical estimates.

## Overview

The code defines a function `simulate(n)` that mimics the structure of the algorithm:

- Outer loop doubles `j` each iteration.
- Inner loop increments `k` by `step = n^(1/3) * log n`.
- Inside the inner loop you would normally perform constant-time work such as `Sum += a[k]*b[k]`.

A timing loop calls `simulate(n)` for a range of `n` values and prints the measured times.

## Code

```python
import math, time

def simulate(n):
    """Simulate the algorithm for a given input size n."""
    j = 2
    step = n**(1/3) * math.log(n)  # step = n^(1/3) * log n
    while j < n:
        k = j
        while k < n:
            # simulate the constant-time work (Sum += a[k]*b[k])
            k += step
        j *= 2

# Timing loop to run experiments:
n_values = [400, 800, 1000, 1600, 3200, 6400, 12800, 25600]
for n in n_values:
    start = time.time()
    simulate(n)
    end = time.time()
    print(f"n={n}, time={end - start:.6f}s")
Usage
Save the code to a file, e.g. simulate.py.

Run it with Python 3:

bash
Copy code
python simulate.py
It will print output like:

lua
Copy code
n=400, time=0.000013s
n=800, time=0.000013s
...
Data Analysis
Collect the printed times for each n.

Compare them with theoretical times 


Normalization (Optional)
To compute normalized times inside the loop:

python
Copy code
norm = (end - start) / ((n**(2/3))*math.log(n))
print(f"n={n}, time={end-start:.6f}s, normalized={norm:.6e}")
This helps verify that the measured runtime divided by the theoretical growth stays roughly constant.
