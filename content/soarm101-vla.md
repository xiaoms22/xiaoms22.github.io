![SO-ARM101 pipeline](/assets/projects/so101-pipeline.svg)

## Goal

This is my main embodied AI project. I built a real-robot pickup-and-putdown loop around SO-ARM101: teleoperation data collection, dataset organization, policy training, inference integration, rollout evaluation, and failure analysis.

The key value is that the work connects LeRobot/OpenPI, ACT, Diffusion Policy, SmolVLA, and pi0/pi0.5 to a physical robot task instead of staying only at paper reading or offline code execution.

## Hardware and Data

- Platform: SO-ARM101 leader/follower arm setup.
- Task: pickup, transport, and putdown.
- Data: 99 episodes, about 28k frames.
- Logged signals: camera observations, joint states, actions, task stages, and success/failure notes.

## Model Routes

- **ACT:** action chunking for low-frequency control; I focused on chunk length, motion smoothness, and accumulated error.
- **Diffusion Policy:** action-sequence modeling through diffusion; I focused on sampling steps, inference latency, and real-robot stability.
- **SmolVLA:** visual/language-conditioned action prediction; I focused on instruction format, action interface, and deployment cost.
- **pi0/pi0.5:** deployment validation and small-sample evaluation on SO-ARM101, not from-scratch foundation-model training.

## Deployment Loop

![SO-ARM101 rollout](/assets/projects/so101-rollout-01.svg)

The main engineering issues were:

1. Dataset schema and training configuration consistency.
2. Correct action normalization and denormalization.
3. Matching relative actions with robot coordinate conventions.
4. Matching action chunking with the robot control frequency.
5. Inference latency, abnormal actions, and safe stop behavior.

## Evaluation

The public claim is intentionally bounded: I completed the SO-ARM101 data-training-deployment loop; ACT, Diffusion Policy, and SmolVLA have rollout evidence; pi0/pi0.5 completed small-sample pickup/putdown deployment validation. The small-sample result validates the deployment pipeline, not open-world generalization.

## Failure Analysis

The main real-robot failure sources are:

- Camera-view or object-initial-position shift.
- Incorrect normalization or relative-action convention.
- Inference latency causing state-action mismatch.
- Gripper timing, grasp pose, or putdown height instability.
- Limited data coverage under unseen conditions.

## Next Experiments

- Expand left / center / right initial positions.
- Add object, lighting, camera-view, and language-paraphrase variations.
- Track stage pass rate instead of only final success rate.
- Compare failure types across ACT, Diffusion Policy, SmolVLA, and pi0/pi0.5.
- Use failure examples to guide the next data collection and tuning round.

## Boundary

This project demonstrates real-robot data, training, deployment, evaluation, and failure-analysis ability. It should not be read as from-scratch training of a general-purpose embodied foundation model.
