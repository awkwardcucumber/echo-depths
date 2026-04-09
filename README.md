[README.md](https://github.com/user-attachments/files/26601891/README.md)
# ECHO DEPTHS

Multiplayer co-op underwater horror where players are effectively blind and must use microphone loudness to reveal the world. Sound helps navigation, but also increases danger.

## Core Pitch

You can only see by making noise, but noise attracts monsters.

## Project Status

Planning phase (spec-driven).

Primary planning document:
- `the_plan.md`

## v0.1 Target

- Platform: Windows PC
- Release channel: Steam Early Access / first public build
- Players: 2-4 online co-op

## Design Pillars

1. Sound as sight
2. Sound as threat
3. Team communication as both solution and danger
4. Darkness reclaimed through beacon objectives
5. Enemy deception through false signals

## Development Approach

This project is built spec-first.

Each feature should have a mini-spec with:
- feature name
- problem statement
- player-facing behavior
- designer constraints
- technical approach
- inputs and outputs
- edge cases
- acceptance criteria
- test cases
- dependencies
- risks

## Scope Discipline

Rules for early development:
- Validate fun before adding content
- Prototype ugly, polish later
- Keep v0.1 intentionally small
- Network derived gameplay events, not raw mic audio payloads

## Suggested Milestone Flow

1. Foundation
2. Offline Prototype
3. Core Threat Loop
4. Objective and Progression Loop
5. Multiplayer Foundation
6. Vertical Slice Polish
7. v0.1 Expansion
8. Release Candidate

## Immediate Next Actions

1. Create repo/docs structure
2. Create Unity project and folder structure
3. Implement player movement
4. Implement microphone loudness reader
5. Implement debug reveal pulse
6. Build one simple test room
7. Validate sound-to-vision fun before enemies/networking

## Proposed Repository Layout (Unity)

```text
Assets/
  Art/
  Audio/
  Prefabs/
  Scenes/
  Scripts/
  ScriptableObjects/
  Shaders/
  Settings/
Docs/
```

## Git Workflow (Recommended)

- `main`: always stable
- `develop`: integration branch
- `feature/<system-name>`: one feature at a time
- `release/v0.1`: stabilization branch
- `hotfix/<issue>`: urgent fixes

## Testing Focus

- Mic loudness to reveal mapping
- Shared noise meter behavior
- Enemy reaction to sound events
- Revive loop reliability
- Objective progression consistency
- Multiplayer synchronization for core events

## Notes

- Unity version and package versions should be pinned once project initialization begins.
- Steam integration should not block prototype iteration, but should land before final stabilization.
