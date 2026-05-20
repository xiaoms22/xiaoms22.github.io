![Dual-arm schema](/assets/projects/dual-arm-schema.svg)

## Goal

This project targets hazardous-material placement with dual-arm robots, aiming to replace risky manual operations. My contribution focuses on the teaching, data collection, imitation-learning interface, and training-validation pipeline.

## My Work

- Implemented and debugged ROS2 nodes and upper-computer functions.
- Designed a LeRobot-style data collection interface.
- Organized a state-action schema connecting visual observations, joint states, end-effector states, and actions.
- Built teaching flow, collection scripts, and model training validation.
- Turned the task into an iterative teaching -> data -> training -> deployment prototype.

## Data Pipeline

1. The upper-computer interface starts tasks and records state.
2. ROS2 nodes synchronize robot state and control interfaces.
3. Collection scripts save observations, states, actions, and task stages.
4. The LeRobot interface converts records into trainable format.
5. The trained model returns to the prototype loop for deployment validation.

## Value

This project shows how I reason about embodied algorithms under real application constraints: dual-arm synchronization, motion safety, state alignment, UI interaction, and downstream industrial evaluation.

## Boundary

The public claim is prototype pipeline and training validation, not final industrial delivery. No internal files, raw code, data, or partner materials are uploaded.
