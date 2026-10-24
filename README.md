# Simple Harmonic Motion: Analytical and Numerical Study

A Jupyter notebook that studies simple harmonic motion (SHM) in Python: first the exact solution, then a numerical solution using the Euler method, and finally the effect of damping.

## The Physics

The equation of motion for a mass on a spring is

\[
\frac{d^2x}{dt^2}=-\omega^2x
\]

With \(\omega=1\), the exact solution is \(x(t)=A\cos(t+\phi)\).

To solve it numerically, I split it into two first-order equations:

\[
\frac{dx}{dt}=v,\qquad \frac{dv}{dt}=-x
\]

The Euler method updates them step by step:

```python
x[i+1] = x[i] + v[i] * dt
v[i+1] = v[i] - x[i] * dt
```

## What's in the Notebook

- Derivation of the SHM equation
- Sine and cosine solutions, and how parameters change them
- Euler method implementation using a reusable `simulate()` function
- Comparison of the Euler result with the exact solution
- Velocity and energy plots
- Damped oscillator simulations with different damping values `b`

## Key Finding

The Euler method does not conserve energy. In the position-versus-time plot, the amplitude gradually grows even though the exact solution has constant amplitude. This is numerical error: each Euler step introduces a small error that accumulates over time. A smaller time step `dt` can reduce the error, but the standard Euler method still exhibits energy drift.

## How to Run

Install the required packages:

```bash
pip install numpy matplotlib jupyter
```

Then launch Jupyter Notebook:

```bash
jupyter notebook shmproject.ipynb
```

## Next Steps

- Implement symplectic Euler and RK4 and compare their energy behaviour
- Extend `simulate()` to accept `omega` and total simulation time as parameters
