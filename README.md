# PhyGONC 3D — Adaptive Robotic Control

**Physics-Guided Online Neural Control | 3D Stress-Test Demonstration**

PhyGONC 3D combines nominal rigid-body dynamics with online adaptive residual and bias compensation for computed-torque control of spatial 3-DOF robotic arms.

### Stress Test

**128 heterogeneous robots · 120 seconds · 5 random seeds**

The simulation evaluates tracking under:

- Time-varying mass and joint friction
- Nonlinear actuator dynamics and actuator-law switching
- External torque disturbance bursts
- Camera blackouts and noisy visual perception
- One-step actuation delay and rapid target changes
- Torque saturation limits

The controller uses stereo visual perception for target estimation, noisy joint encoders for continuous feedback, and online adaptation to compensate for modelling errors.

### Results

| Metric | Adaptive | Nonadaptive | Improvement |
|---|---:|---:|---:|
| Mean tip error | 0.1376 m | 0.3099 m | **55.6%** |
| Late-window tip error | 0.0848 m | 0.2940 m | **71.1%** |
| Tip RMSE | 0.2934 m | 0.4360 m | **32.7%** |
| Torque saturation | 1.97% | 1.94% | — |
| Visual joint error | 0.0186 rad | 0.0186 rad | — |

Results are means across five seeds (640 simulated robot runs per configuration). Late-window error is evaluated during the final three seconds of each waypoint interval.

### Demonstration

**3D robot motion, stereo camera views and tracking performance**

![PhyGONC 3D stress test](media/stress_test.gif)

**Stress-test diagnostics**

![Tracking diagnostics](media/tracking_diagnostics.png)

### Scope

These results demonstrate promising **simulation performance**, not real-world robotic validation. The comparison evaluates the combined effect of online residual and bias adaptation; individual component contributions require controlled ablation studies.

**Status:** Research prototype · Simulation demonstration · Full implementation not publicly released.