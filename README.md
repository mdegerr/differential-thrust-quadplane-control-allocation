# Feasibility-Aware Acceleration Control for a Differential-Thrust Quad-Plane

This repository contains a technical presentation on acceleration control for a differential-thrust quad-plane UAV.

The presentation focuses on how a quad-plane with fixed rotors and no conventional control surfaces can track acceleration commands across hover, transition, and cruise while respecting actuator limits.

## Presentation

The presentation PDF is available here:

```text
docs/quadplane_control_allocation_study.pdf
```

## What The Presentation Covers

- Problem definition for a differential-thrust quad-plane
- Hover vs. cruise force and moment generation
- Static pitch stability considerations
- Differential-thrust authority limits with airspeed
- Cascaded acceleration, attitude, and rate control architecture
- INDI-based acceleration feedback concept
- Continuous blending through transition
- Control allocation under actuator saturation
- Saturation priority and graceful degradation
- MATLAB reduced-order proof-of-concept results
- Implementation path from simulation to flight testing

## Main Technical Idea

The key idea is that acceleration control for this platform is not only a tracking problem. It is also an actuator-feasibility problem.

When the requested force and moment vector is outside the rotor limits, simple rotor clipping can unintentionally distort roll, pitch, or yaw response. A feasibility-aware allocator instead searches for the best achievable force and moment response while keeping all rotor commands within physical limits.
