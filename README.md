# Diamond — Mach 3, 0°, 80,000 ft

OpenFOAM Foundation 14, foamRun / shockFluid.

## Conditions

Geometric altitude: 24,384 m; geopotential altitude: 24,290.823 m.
US Standard Atmosphere layer 20–32 km: T = 220.940823 K,
p = 2801.546621 Pa, rho = 0.044173315 kg/m³.
Perfect gas, R = 287.05287 J/(kg K), gamma = 1.4.
Freestream velocity: (893.931421 0 0) m/s.

Atmosphere reference: https://ntrs.nasa.gov/api/citations/20050207438/downloads/20050207438.pdf

## Model

The STL cross-section has vertices (0,0), (0.1,0.01), (0.2,0),
(0.1,-0.01), in metres. Its span is 0.001 m.
The mesh is fitted exactly to these straight edges; no STL snapping is needed.
2-D, one spanwise cell with empty front/back patches; 24,000 cells.
Inviscid Euler approximation, slip wall, zero viscosity. This computes shocks
and pressure/wave drag, not skin friction, heat transfer or finite-span effects.
It is a preliminary calculation, without mesh independence or demonstrated
steady convergence. End time 0.004 s is an initial run length, not a convergence guarantee.

## Run

In this directory:

```bash
bash Allrun
```

The script saves progress in log.foamRun. In a second terminal:

```bash
tail -f log.foamRun
```

Open ParaView with `paraview --no-mpi`, then open diamond.foam and Apply.
For the mesh, select Surface With Edges and the +Z view.
For the solution, select the latest available time and colour by p or U magnitude.
A short startup check is recorded in log.startupCheck; it is not the completed analysis.
The main run resumes from the latest written time.
