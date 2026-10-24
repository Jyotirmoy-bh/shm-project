# Simple Harmonic Motion: Analytical and Numerical Study

A Python-based study of simple harmonic motion (SHM) using analytical solutions and numerical simulations. This project explores the motion of an ideal oscillator, implements the Euler method, compares numerical results with the exact solution, and investigates the effects of damping.

## 1. The Physics

For an ideal mass-spring system, Newton's second law gives the equation of motion:

**Differential equation:**

`d²x/dt² = −ω²x`

Here, `x` is the displacement from equilibrium and `ω` is the angular frequency.

For `ω = 1`, the exact solution can be written as:

`x(t) = A cos(t + φ)`

where `A` is the amplitude and `φ` is the phase constant.

To solve the equation numerically, we rewrite it as two first-order differential equations:

```text
dx/dt = v
dv/dt = −x
```

## 2. Numerical Method: Euler's Method

Euler's method approximates the evolution of a system by updating its variables in small time steps.

For a time step `dt`, the updates are:

```python
x[i+1] = x[i] + v[i] * dt
v[i+1] = v[i] - x[i] * dt
```

The numerical solution can then be compared with the exact analytical solution to understand the accuracy and limitations of the method.

## 3. What's in the Notebook

- Derivation and exploration of the simple harmonic motion equation
- Sine and cosine solutions and the effects of changing their parameters
- Numerical simulation using Euler's method
- A reusable `simulate()` function
- Comparison between numerical and analytical solutions
- Position, velocity, and energy plots
- Damped oscillator simulations for different damping values

## 4. Key Observation

The standard Euler method does not conserve the total mechanical energy of an ideal harmonic oscillator.

For typical initial conditions, the numerical solution may show a gradual increase in amplitude and energy over time, even though the exact solution maintains constant amplitude and energy.

This behaviour arises from the numerical error introduced at each time step. The accumulated error depends on the time step and the duration of the simulation.

Comparing numerical results with the analytical solution helps illustrate why the choice of numerical integration method matters when simulating physical systems.

## 5. How to Run

### Requirements

- Python 3
- NumPy
- Matplotlib
- Jupyter Notebook

Install the required packages using:

```bash
pip install
