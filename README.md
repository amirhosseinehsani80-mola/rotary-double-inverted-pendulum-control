# Rotary Double Inverted Pendulum – Advanced Control Project

This repository contains MATLAB and Simulink implementations developed for the advanced control of a rotary double inverted pendulum. The project focuses on modeling, linearization, stability analysis, controller design, robustness evaluation, disturbance rejection, and observer development. The complete system analysis and all methodology are documented in the accompanying report.

<img width="773" height="797" alt="image" src="https://github.com/user-attachments/assets/311ab713-d56f-4056-a543-264541993472" />


## Overview

The rotary double inverted pendulum is an unstable and highly nonlinear system commonly used as a benchmark for testing advanced control algorithms. It consists of a rotary arm driven by a motor and two pendulum links attached in series. The objective of the project is to stabilize the pendulums in the upright position and track selected reference signals using state-space control techniques.

## Dynamic Modeling

The nonlinear equations of motion were derived using the Euler–Lagrange method. Expressions for the kinetic and potential energies of the rotary arm and both pendulums were formulated, and MATLAB symbolic tools were used to compute the equations and reduce their complexity. The model is fully parameterized using the physical values listed in the report.

## Linearization and State-Space Form

The nonlinear model was linearized around the upright equilibrium using a Taylor series expansion. The resulting linear system was converted into a state-space representation with six state variables: the three angles of the rotary arm and pendulums and their corresponding angular velocities. Stability analysis of the linear model shows that the system has unstable eigenvalues, as expected.

The system was verified to be both controllable and observable.

## State Feedback Control
<img width="731" height="599" alt="image" src="https://github.com/user-attachments/assets/e89ee0ff-3272-48bf-b871-033ea44f07bf" />

Two controllers were designed using pole placement: one with slow desired poles and one with fast desired poles.  
- The slow controller provides stable convergence with limited overshoot.  
- The fast controller achieves rapid settling but demands significantly higher control effort and exhibits larger overshoot.

The comparison shows that faster poles do not necessarily produce better overall performance due to actuator limitations and sensitivity to overshoot.

## Reference Tracking with Integrator
<img width="834" height="563" alt="image" src="https://github.com/user-attachments/assets/1db8dcef-88cf-4544-b6be-0638d1a2421c" />

To eliminate steady-state error in tracking, the system was augmented with an integrator. A stair-shaped reference signal was used to test the controller. The state feedback with integrator successfully tracks the reference while stabilizing the pendulum angles. The design balances responsiveness with the need to prevent destabilizing overshoots in this inherently unstable system.

## Robustness Analysis

The system was tested under parameter variations of approximately −10%. The controller continued to track the reference without performance degradation. This demonstrates that the linear state feedback controller is robust against moderate modeling uncertainties.

## Disturbance Rejection

An impulse-like disturbance was added to the control input. The controller successfully rejected the disturbance and returned the system to stable tracking behavior. This confirms the resilience of the control design under sudden external inputs.

## Full-Order Observer

A full-order state observer was designed for the augmented system. The estimated states converged to the true states, enabling continued closed-loop control even without direct access to all states. Higher observer gains were required to achieve fast convergence.

## Reduced-Order Observer
<img width="1453" height="818" alt="image" src="https://github.com/user-attachments/assets/c21f0f0f-b9bb-4ca2-ac42-3ead536c6d08" />

A reduced-order observer was developed to estimate only the three key angular states. This observer converged faster and more accurately than the full-order observer and demonstrated improved performance in tracking tasks due to its lower complexity.

## Multi-Reference Tracking

An extended control structure was created to track a sinusoidal reference for the rotary arm angle while holding one pendulum angle at a desired step value and driving the second pendulum angle to zero. The experiments show that, due to the single actuator and the strong coupling between pendulum states, only the rotary arm can reliably track a non-zero reference. The pendulum angles can be regulated to zero, but they cannot independently track additional reference signals without destabilizing the system.

## Conclusion

This project demonstrates the challenges and capabilities of controlling a complex nonlinear system such as the rotary double inverted pendulum. Through nonlinear modeling, linearization, controller design, robustness testing, and observer development, a comprehensive control framework was developed. The results show that state feedback can successfully stabilize the system and track references, observers can accurately reconstruct system states, and the controller maintains performance under disturbances and parameter variations. However, independent tracking of multiple pendulum angles is not feasible with a single actuator, and regulation remains the only achievable objective for those states.
