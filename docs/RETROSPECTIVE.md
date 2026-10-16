# Retrospective: 2019 Automated River Cleaner → 2026

An honest look back at my senior design project — what worked, what didn't,
and how each gap became a design decision in the current project.

## What we built (2019)

Drexel MEM-493, Group 32 (team of 5). The "Automated River Cleaner": a catamaran boat robot (styrofoam twin hulls, PVC frame, rotary sweeper collector, brushless propulsion, Arduino MEGA control) built for a real sponsor to clean bottles and plastic bags from a river near their factory. I served as project manager — owning schedule, quality control, and system integration across the mechanical, electrical, and software workstreams — and as the sole developer of the AI recognition module: TensorFlow object detection, model training through Raspberry Pi + Pi Camera deployment, all the way to the 100-test validation.

## What worked — highlights worth keeping

- Real hardware, real water. Not a simulation: stakeholder needs, decision matrices, FEA on hull designs, a built prototype, and river field tests (5 runs, 5 bottles collected within 90 seconds each).
- Wore two hats. Project manager leading 5 people (schedule, quality control, cross-discipline integration) while personally delivering the AI recognition module end to end — model, Pi deployment, and validation. Managing the project and building its hardest subsystem at the same time is the story.
- Early edge AI (2019). TensorFlow object detection on a $37 Raspberry Pi — 100 bottle-recognition tests at ~80% average confidence, before edge AI was fashionable.
- The economics closed. Final build $704 against a $1,000 budget; 5-year operating cost $2,235 vs ~$24,000 for manual labor. Engineers who can do the cost math get funded.

## What didn't — the honest gaps

1. 1.2 FPS. The Pi managed 1–1.5 FPS; our own report admits it was too slow for a 1.5 m/s river. Compute was the bottleneck, not the model.
2. The loop was never closed. Recognition worked; collection stayed on a human with a remote control. Senior design ran out of time before autonomy.
3. Mechanical reliability hacks. Belt slipping fixed with sandpaper for friction, bottles jamming between sweeper rods, exposed wiring, parallel batteries without diodes. It worked — but it wasn't robust.
4. Requirements cut by budget. GPS autopilot and solar charging were dropped for cost. Real engineering is about trade-offs, and we made them explicitly.

## What I'd do differently — the 2026 answers

2019 gap → 2026 answer (this repo):
- 1.2 FPS on Pi → YOLO + TensorRT on Jetson Orin NX, 30+ FPS
- Manual collection → 6DOF arm closes the grasp loop
- Fragile prototype → Staged R0-R3 roadmap with benchmarks at each gate
- No field data loop → Self-collected marine dataset (floating bottles, glare, waves)

## Lessons that stuck

Our final slide said it best: "Tolerance is KEY — always have a backup plan." Seven years later, the mission is the same. Only the silicon changed.
