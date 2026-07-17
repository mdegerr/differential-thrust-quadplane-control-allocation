# Feasibility-Aware Acceleration Control for a Differential-Thrust Quad-Plane

This repository presents a conceptual control architecture and reduced-order MATLAB proof-of-concept for a fixed-wing quad-plane configuration with four fixed rotors and no conventional control surfaces.

The main focus is actuator-feasible acceleration control: converting commanded acceleration objectives into rotor thrust commands while respecting physical rotor limits and preserving attitude/moment authority as much as possible.

## Project Scope

- Regime-spanning acceleration control concept for hover, transition, and cruise
- Differential-thrust force and moment generation
- Smooth lift-sharing between rotor-dominant and wing-dominant regimes
- Constrained control allocation under rotor saturation
- MATLAB-generated figures for allocation and feasibility explanation

This is a public, sanitized portfolio version. It does not include any company-specific case documents, proprietary platform data, or interview material.

## Core Idea

For a differential-thrust quad-plane, the same four rotors must generate both total force and body moments. When a commanded force/moment vector is infeasible, independent rotor clipping can unintentionally distort roll, pitch, or yaw moments.

Instead, the allocator can be written as a constrained optimization problem:

```text
T* = arg min ||Wu (B T - u_cmd)||^2 + rho ||T - T_trim||^2
subject to 0 <= Ti <= Tmax
```

where:

- `T` is the rotor thrust vector
- `B` is the mixing/control-effectiveness matrix
- `u_cmd` is the commanded force/moment vector
- `Wu` defines axis priorities under saturation
- `rho` regularizes the solution around trim thrust

## Repository Structure

```text
.
|-- README.md
|-- REFERENCES.md
|-- SANITIZATION_CHECKLIST.md
|-- scripts/
|   `-- generate_constrained_allocation_equation.m
`-- assets/
    `-- constrained_allocation_equation.png
```

## MATLAB Figure Generation

Run the MATLAB script from the repository root:

```matlab
run('scripts/generate_constrained_allocation_equation.m')
```

It generates the constrained allocation equation figure used in the technical presentation.

## Suggested Presentation File

After you sanitize the presentation, add it with a generic filename, for example:

```text
docs/quadplane_control_allocation_study.pdf
```

Do not upload the original case-study PDF or any company-specific document.

## Notes

This repository is intended as a technical portfolio project, not as a complete aircraft controller implementation. The MATLAB material is a reduced-order proof-of-concept focused on allocation logic and saturation behavior.

