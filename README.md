# Rotary Double Inverted Pendulum — Advanced Control Implementation

This repository contains the full MATLAB & Simulink implementation of advanced control strategies for a **rotary double inverted pendulum** (Quanser DBPEN-ROT).  
The project covers everything from nonlinear modeling to observer design, and includes simulations, stability analysis, and reference tracking experiments.

---

## 📌 Project Overview

The rotary double inverted pendulum is a **highly nonlinear, unstable, multivariable system**, making it a classical benchmark for advanced control methods.  
This project includes:

- Nonlinear dynamic modeling using **Euler–Lagrange equations**
- MATLAB symbolic derivation for full system dynamics
- Linearization around the upright equilibrium using **Taylor series**
- Stability analysis (eigenvalues + Lyapunov test)
- **State-feedback control** (slow & fast pole placement)
- **Robustness and disturbance rejection** simulations
- **Full-order** and **reduced-order** observers
- Reference tracking:
  - Stair-shaped signal
  - Sinusoidal \( q \) reference
  - Constant \( \alpha \) reference
  - Regulation of \( \gamma \)

The work is based on the complete report included in this repository.

---

## 🧩 System Architecture

(*Insert your image here — drag & drop*)

---

## 🧮 Nonlinear Modeling

The nonlinear dynamic equations of motion were derived using the **Euler–Lagrange method** and validated in MATLAB.  
Symbolic computation was used to generate expressions for:

- Kinetic energy of all links  
- Potential energy  
- Complete Lagrangian  
- 3 coupled nonlinear differential equations  

(*Insert model diagram or math flowchart here*)

---

## 🔄 Linearization & State-Space Model

The system is linearized around the upright equilibrium.  
The linear model is expressed as:

\[
\dot{x} = Ax + Bu
\]

with 6 states:

- \( q, \alpha, \gamma \) (angles)  
- \( \dot{q}, \dot{\alpha}, \dot{\gamma} \) (angular velocities)

Controllability and observability are verified (both full rank).

(*Insert linearization figure or stability diagram here*)

---

## 🎛️ State-Feedback Controller

Two controller designs were implemented:

### **Slow Poles Controller**
- Stable, smooth response  
- Low overshoot  
- Lower control effort  

(*Insert slow poles step response image here*)

### **Fast Poles Controller**
- Very quick settling  
- High overshoot  
- Large control effort (not ideal for actuators)

(*Insert fast poles step response image here*)

---

## 📈 Reference Tracking with Integral Action

A stair-shaped reference for angle \( q \) is tracked using:

- Augmented state-space model  
- Integral action  
- State feedback controller  

(*Insert tracking figure here*)

The controller achieves zero steady-state error while maintaining pendulum stability.

---

## 🛡️ Robustness & Disturbance Rejection

The system is tested under:

- **−10% parameter variations**
- **Impulse-like external disturbance**

Results show the controller maintains tracking performance and stability.

(*Insert robustness and disturbance rejection plots here*)

---

## 👁️ Observer Design

Both observer types were designed and tested:

### **Full-Order Observer**
- Estimates all 7 augmented states  
- Slower than reduced observer  
- Requires higher gain tuning  

(*Insert full-order observer results*)

### **Reduced-Order Observer**
- Estimates only the angles \( q, \alpha, \gamma \)  
- Much faster convergence  
- Higher numerical stability  

(*Insert reduced-order observer plots here*)

---

## 🌊 Tracking Multiple References (q, α, γ)

The controller is extended to track:

- Sinusoidal reference for **q**
- Step reference for **α**
- Zero reference for **γ**

Several amplitudes and frequencies are tested.

(*Insert multi-reference tracking plots here*)

Final finding:

> With a single actuator, it is **impossible** for both pendulum angles (α, γ) to follow independent reference signals.  
> Only regulation to zero is feasible due to strong coupling and physical limitations.

---

## 📂 Repository Contents

