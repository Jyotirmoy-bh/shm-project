# Simple Harmonic Motion: Analytical and Numerical Study

A Jupyter notebook that studies simple harmonic motion (SHM) in Python:
the exact solution, numerical solutions using Euler-type methods,
energy conservation, and the effect of damping.

## The physics

The equation of motion for a mass on a spring is

    d²x/dt² = -ω² x

With ω = 1, the exact solution is x(t) = A cos(t + φ).
To solve it numerically, I split it into two first-order equations:

    dx/dt = v
    dv/dt = -ω² x

**Explicit Euler** updates both using the old values:

    x[i+1] = x[i] + v[i]·dt
    v[i+1] = v[i] - ω² x[i]·dt

**Symplectic Euler** updates v first, then uses the new v for x:

    v[i+1] = v[i] - ω² x[i]·dt
    x[i+1] = x[i] + v[i+1]·dt

## What's in the notebook

- Derivation of the SHM equation
- Sine and cosine solutions, and how the parameters change them
- Explicit Euler implementation and comparison with the exact solution
- Velocity and energy plots
- Damped oscillator, trying different damping values `b`
- A reusable `simulate()` function with `omega`, `T` and `method` as parameters
- Energy comparison of explicit and symplectic Euler

## Key finding

Explicit Euler does not conserve energy. For ω = 1, each step multiplies
the total energy E = ½v² + ½ω²x² by (1 + dt²), so E grows exponentially.
With dt = 0.01 and T = 50, the energy rises from 0.50 to about 0.82,
which matches the predicted 0.5·(1 + dt²)^N ≈ 0.5·e^0.5.

Symplectic Euler differs only in updating v first and then using the new v
to update x. Its energy oscillates within about 1% of the exact value
and does not drift. Same cost per step, much better long-term behaviour.
