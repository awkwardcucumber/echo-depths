# ECHO DEPTHS — Spec-Driven Build Plan

Version: Draft 1
Project Type: Multiplayer-only co-op horror / tension game
Engine: Unity
Target Platform for v0.1: Windows PC via Steam Early Access / first public build
Players: 2–4
Primary Input Gimmick: Microphone loudness controls world revelation through echolocation-like pulses

---

# 1. Project Summary

## 1.1 High Concept

ECHO DEPTHS is a multiplayer underwater co-op game where players are effectively blind and must use their real microphone input to reveal the environment around them. Speaking, humming, tapping, or making noise generates temporary echo-vision pulses that expose nearby geometry and threats. However, sound also increases a shared noise meter and attracts enemies.

The game loop is based on tension between:

- [ ] needing sound to navigate and coordinate
- [ ] needing silence to survive
- [ ] reviving teammates by locating their voice in darkness
- [ ] progressing through submerged map sections by activating sound beacon devices that provide dim persistent visibility zones

## 1.2 Core Pitch

You can only see by making noise, but noise attracts monsters.

## 1.3 Design Goals

- [ ] Create a mechanic-first game with a clear one-sentence hook
- [ ] Produce strong co-op moments, blame moments, and panic moments
- [ ] Keep the MVP narrow enough to validate fun quickly
- [ ] Build in a spec-driven way so AI can generate and maintain subsystems reliably
- [ ] Reach a stable, marketable v0.1 Steam build without overcommitting to content

## 1.4 Non-Goals for Initial Release

- [ ] No solo mode in v0.1
- [ ] No modding support in v0.1
- [ ] No advanced anticheat beyond basic sanity checks in v0.1
- [ ] No full voice recognition system in v0.1
- [ ] No large campaign in v0.1
- [ ] No user-generated maps in v0.1

---

# 2. Product Vision

## 2.1 Player Fantasy

Players are vulnerable deep-sea creatures or divers navigating a dark underwater environment using sound to perceive the world. They feel disoriented, dependent on each other, and never fully safe.

## 2.2 Emotional Targets

- [ ] tension
- [ ] uncertainty
- [ ] relief when beacons activate
- [ ] panic when the noise meter spikes
- [ ] distrust when false voices play
- [ ] chaos when reviving teammates under pressure

## 2.3 Content Pillars

1. Sound as sight
2. Sound as threat
3. Team communication as both solution and danger
4. Sections of darkness progressively reclaimed with beacon devices
5. Enemy deception through mimicry and false signals

---

# 3. Scope Boundaries

## 3.1 MVP / Vertical Slice Scope

The MVP must prove the core loop is fun with 2 players and technically viable.

MVP includes:

- [ ] local/offline prototype first
- [ ] one small test map with 1–2 sections
- [ ] microphone loudness detection
- [ ] sound pulse reveal mechanic
- [ ] temporary visibility fade
- [ ] one enemy type attracted to sound
- [ ] shared noise meter
- [ ] one sound beacon objective
- [ ] downed state and voice-based revive
- [ ] basic multiplayer for 2 players minimum

MVP excludes:

- [ ] mimic voices
- [ ] multiple enemy types
- [ ] advanced cosmetics
- [ ] achievements
- [ ] rich Steam integration
- [ ] progression beyond one run
- [ ] difficulty system
- [ ] matchmaking
- [ ] advanced shaders if simple reveal works first

## 3.2 v0.1 Scope

v0.1 is the first public Steam build and should feel cohesive, replayable, and representative.

v0.1 includes:

- [ ] 2–4 player online co-op
- [ ] 1 full playable map with multiple sections
- [ ] 2–3 objectives / beacon phases
- [ ] 2 enemy behaviors or enemy variants
- [ ] revive system
- [ ] shared noise meter
- [ ] dim beacon safe-ish zones
- [ ] voice mimic / false help audio system if stable
- [ ] Steam invites and rich presence
- [ ] basic settings, audio controls, and key usability features
- [ ] basic difficulty progression or selectable difficulty

v0.1 excludes unless ahead of schedule:

- [ ] full campaign
- [ ] large meta progression
- [ ] mod support
- [ ] extensive accessibility suite beyond essential controls and subtitles where relevant
- [ ] anticheat beyond practical host-authoritative and validation measures

---

# 4. Development Method

## 4.1 Spec-Driven Workflow

Each feature must be developed through a mini-spec before implementation.

Every feature spec should include:

- [ ] feature name
- [ ] problem statement
- [ ] player-facing behavior
- [ ] designer constraints
- [ ] technical approach
- [ ] inputs
- [ ] outputs
- [ ] edge cases
- [ ] acceptance criteria
- [ ] test cases
- [ ] dependencies
- [ ] risks

## 4.2 AI-Assisted Development Rules

Use AI to generate code, tests, scaffolding, refactors, and documentation, but not to make final design decisions.

AI is allowed to:

- [ ] scaffold Unity C# scripts
- [ ] draft networking messages and synchronization code
- [ ] build editor tooling
- [ ] generate test harnesses
- [ ] refactor subsystems to cleaner patterns
- [ ] generate documentation and checklists

AI is not allowed to decide without review:

- [ ] final architecture changes
- [ ] feature scope expansion
- [ ] gameplay tuning values
- [ ] network authority model changes
- [ ] release criteria

## 4.3 Branching / Delivery Model

Recommended Git branches:

- [ ] `main` — always stable
- [ ] `develop` — integration branch
- [ ] `feature/<system-name>` — one feature at a time
- [ ] `release/v0.1` — stabilization branch before public build
- [ ] `hotfix/<issue>` — urgent bug fix

Recommended cadence:

- [ ] write spec
- [ ] implement in feature branch
- [ ] validate against acceptance criteria
- [ ] merge to develop
- [ ] regression test
- [ ] merge to main when stable

---

# 5. Technical Stack

## 5.1 Engine

- [ ] Unity

## 5.2 Source Control

- [ ] Git
- [ ] GitHub or equivalent remote repository

## 5.3 Networking

Choose one networking solution early and do not swap casually mid-project.

Selection criteria:

- [ ] good Unity support
- [ ] stable host-client model
- [ ] event sync simplicity
- [ ] practical Steam integration path

Minimum requirement:

- [ ] sync transforms
- [ ] sync gameplay events
- [ ] sync enemy states
- [ ] sync objective states
- [ ] sync player state transitions

## 5.4 Platform Services

- [ ] Steamworks integration for invites and rich presence

## 5.5 Audio / Voice

For gameplay:

- [ ] use microphone amplitude / loudness, not full speech-to-text

For optional voice chat:

- [ ] separate system decision, not required for core gameplay prototype

Important design note:

- [ ] raw mic audio should not be used as the core synchronized gameplay payload
- [ ] sync derived gameplay events instead, such as sound intensity and source position

---

# 6. Folder and Project Structure

Recommended Unity folder structure:

```text
Assets/
  Art/
    Materials/
    Models/
    VFX/
  Audio/
    Ambience/
    UI/
    SFX/
    VoiceMimic/
  Prefabs/
    Characters/
    Enemies/
    Objectives/
    Environment/
    UI/
  Scenes/
    Bootstrap/
    Prototype/
    Multiplayer/
    Release/
  Scripts/
    Core/
    Audio/
    Input/
    Player/
    Enemy/
    World/
    Objectives/
    Networking/
    UI/
    Steam/
    Editor/
    Tests/
  ScriptableObjects/
    Enemies/
    Audio/
    Difficulty/
    World/
  Shaders/
  Settings/
```

---

# 7. Milestone Overview

## Milestone 0 — Foundation

Goal: establish repo, project standards, and build discipline.

Deliverables:

- [ ] Unity project created
- [ ] repo initialized
- [ ] branch rules documented
- [ ] naming conventions documented
- [ ] coding standards documented
- [ ] issue tracker categories created
- [ ] basic folder structure created
- [ ] bootstrap scene created
- [ ] logging and debug utilities added

Exit criteria:

- [ ] clean project opens on at least one development machine
- [ ] project builds locally
- [ ] basic play mode works with no compile errors

## Milestone 1 — Offline Prototype

Goal: prove sound-to-vision feels good in a local single-player test environment.

Deliverables:

- [ ] player movement controller
- [ ] local mic loudness reader
- [ ] sound pulse reveal mechanic
- [ ] temporary object reveal / fade
- [ ] simple test arena
- [ ] debug UI for mic volume and reveal radius

Exit criteria:

- [ ] speaking into mic reveals nearby geometry
- [ ] louder sounds increase reveal radius
- [ ] revealed objects fade back to darkness predictably
- [ ] system runs without major stutter

## Milestone 2 — Core Threat Loop

Goal: prove tension by adding danger to sound.

Deliverables:

- [ ] shared noise meter logic, initially local
- [ ] one enemy type attracted to sound source
- [ ] enemy pathing toward emitted sound event
- [ ] player damage / downed state
- [ ] revive by sound concept in local prototype

Exit criteria:

- [ ] players can cause danger through repeated noise
- [ ] enemy reaches sound source reliably
- [ ] downed player emits recoverable audio source
- [ ] local loop is fun enough to test repeatedly

## Milestone 3 — Objective Prototype

Goal: prove the map progression loop with a beacon objective.

Deliverables:

- [ ] one beacon device prefab
- [ ] beacon activation interaction
- [ ] beacon emits dim persistent visibility zone
- [ ] section completion state
- [ ] next section unlock trigger

Exit criteria:

- [ ] player can find and activate beacon
- [ ] beacon changes local visibility state
- [ ] section progression is clear and understandable

## Milestone 4 — Multiplayer Foundation

Goal: transform the prototype into a networked co-op test.

Deliverables:

- [ ] lobby / host / join flow
- [ ] 2-player network session
- [ ] synchronized player positions
- [ ] synchronized sound events
- [ ] synchronized enemy behavior
- [ ] synchronized downed / revive state
- [ ] synchronized beacon activation

Exit criteria:

- [ ] two players can join and complete one run
- [ ] network state remains coherent for core events
- [ ] host migration decision documented even if not supported

## Milestone 5 — Vertical Slice

Goal: produce a polished 10–15 minute representative session.

Deliverables:

- [ ] one complete small map
- [ ] one enemy behavior fully tuned
- [ ] one complete objective chain
- [ ] tuned noise meter
- [ ] tuned revive loop
- [ ] basic audio design
- [ ] placeholder art direction locked
- [ ] first external playtest build

Exit criteria:

- [ ] external testers understand the game without direct developer explanation
- [ ] at least one memorable co-op panic moment occurs consistently
- [ ] bugs are manageable and reproducible

## Milestone 6 — Pre-Release Expansion

Goal: add enough content and features for a credible first Steam build.

Deliverables:

- [ ] full v0.1 content target
- [ ] second enemy behavior or variant
- [ ] voice mimic / false help sounds if stable
- [ ] settings menu
- [ ] session recovery behavior defined
- [ ] Steam integration
- [ ] onboarding / tutorialization layer

Exit criteria:

- [ ] game is enjoyable for multiple sessions
- [ ] platform features work reliably
- [ ] first-release quality bar is met

## Milestone 7 — v0.1 Release Candidate

Goal: stabilize and ship.

Deliverables:

- [ ] bug fixing pass
- [ ] performance pass
- [ ] crash triage pass
- [ ] usability pass
- [ ] store assets and description draft
- [ ] final release checklist

Exit criteria:

- [ ] no known critical blockers
- [ ] no progression blockers in intended play path
- [ ] no major desync in common network conditions
- [ ] build accepted as releasable

---

# 8. Detailed Phase Plan

# Phase A — Foundation

## A.1 Repository Setup Spec

### Objective

Create a project environment that supports disciplined iteration and AI-assisted development.

### Tasks

- [ ] initialize Unity project
- [ ] initialize Git repo
- [ ] add `.gitignore` suitable for Unity
- [ ] define code style rules
- [ ] define naming conventions
- [ ] create `Docs/` directory in repo
- [ ] add `README.md`
- [ ] create issue templates
- [ ] create milestone board

### Acceptance Criteria

- [ ] project clones cleanly
- [ ] no generated junk tracked unnecessarily
- [ ] developer onboarding steps documented

## A.2 Documentation Pack

Create initial docs:

- [ ] product brief
- [ ] build plan
- [ ] coding guidelines
- [ ] folder structure guidelines
- [ ] feature spec template
- [ ] testing checklist template
- [ ] bug report template

### Acceptance Criteria

- [ ] every new feature can be attached to a clear spec and test plan

---

# Phase B — Offline Prototype

## B.1 Feature Spec: Player Movement

### Goal

Allow local navigation in a dark underwater test arena.

### Requirements

- [ ] movement must feel slow and deliberate
- [ ] support keyboard and mouse
- [ ] include collision
- [ ] include a simple camera rig

### Acceptance Criteria

- [ ] player can traverse test environment reliably
- [ ] no major clipping through geometry

## B.2 Feature Spec: Microphone Input Reader

### Goal

Capture microphone loudness in real time and expose normalized output for gameplay systems.

### Inputs

- [ ] default selected microphone device

### Outputs

- [ ] `CurrentVolumeNormalized` from 0–1
- [ ] optional smoothed volume
- [ ] event on threshold crossing

### Constraints

- [ ] do not depend on speech recognition
- [ ] support noisy consumer microphones reasonably
- [ ] support calibration controls later

### Acceptance Criteria

- [ ] mic signal updates every frame or near-frame
- [ ] silence stays near floor value
- [ ] louder sound increases value predictably

## B.3 Feature Spec: Echo Pulse Visualizer

### Goal

Convert mic loudness into a radial reveal pulse.

### Behavior

- [ ] sound triggers a pulse centered at player position
- [ ] pulse radius scales with normalized volume
- [ ] objects within pulse become visible temporarily
- [ ] visibility fades back out

### MVP Implementation Guidance

Use simple material/emission toggles or renderer visibility before building custom shaders.

### Acceptance Criteria

- [ ] reveal timing feels readable
- [ ] louder sounds reveal more area
- [ ] fade timing is consistent

## B.4 Feature Spec: World Reveal Targets

### Goal

Tag world objects as revealable and control their visibility state.

### Requirements

- [ ] environmental objects can subscribe to pulse events
- [ ] reveal state should include fade timer
- [ ] debugging view should allow always-on visibility

### Acceptance Criteria

- [ ] designer can mark objects as revealable without code changes

## B.5 Offline Prototype Test Cases

- [ ] whisper into mic → small reveal radius
- [ ] speak normally → medium reveal radius
- [ ] clap / loud sound → large reveal radius
- [ ] stop making sound → world fades out
- [ ] movement while dark remains possible but risky

### Prototype Review Questions

- [ ] does revealing the world feel inherently satisfying?
- [ ] is the fade too fast or too slow?
- [ ] is darkness readable or only frustrating?
- [ ] is the mechanic fun before adding enemies?

---

# Phase C — Core Threat Loop

## C.1 Feature Spec: Noise Event System

### Goal

Create a reusable gameplay event generated whenever a player makes sound.

### Event Data

- [ ] source actor id
- [ ] world position
- [ ] intensity
- [ ] timestamp
- [ ] reveal radius
- [ ] threat contribution

### Acceptance Criteria

- [ ] enemy AI and UI systems can subscribe to the same event source

## C.2 Feature Spec: Shared Noise Meter

### Goal

Translate team sound into global tension.

### Behavior

- [ ] meter fills based on aggregate sound events
- [ ] louder / repeated sounds fill faster
- [ ] meter decays over time
- [ ] thresholds change enemy aggression

### Design Constraints

- [ ] meter should not punish necessary small communication too hard
- [ ] meter should sharply punish panic noise bursts

### Acceptance Criteria

- [ ] meter is visible in debug UI
- [ ] thresholds trigger predictable state changes

## C.3 Feature Spec: Enemy Type 01 — Sound Hunter

### Goal

Create one simple enemy behavior that validates the danger loop.

### Behavior States

- [ ] idle / patrol
- [ ] investigate sound
- [ ] pursue target area
- [ ] attack if player reached
- [ ] disengage if signal lost

### Inputs

- [ ] sound events
- [ ] line-of-sight optional later
- [ ] beacon zones optional influence later

### Acceptance Criteria

- [ ] enemy reliably reacts to sound events
- [ ] enemy pressure increases as player sound increases

## C.4 Feature Spec: Damage / Downed State

### Goal

Keep players in session after being attacked and create a revive loop.

### Behavior

- [ ] attacked player enters downed state, not immediate death
- [ ] downed player mobility reduced or disabled
- [ ] downed player is not visually obvious in darkness

### Acceptance Criteria

- [ ] downed state transitions correctly
- [ ] player cannot continue normal play until revived or eliminated

## C.5 Feature Spec: Revive by Sound

### Goal

Make reviving a teammate require locating them through sound.

### Behavior

- [ ] downed players must emit sound to become locatable
- [ ] teammates follow voice / sound source to revive
- [ ] revive takes a short interaction window

### Acceptance Criteria

- [ ] revive produces tension under enemy pressure
- [ ] downed player remains engaged and active

## C.6 Review Questions

- [ ] does sound now feel dangerous enough?
- [ ] do players naturally blame each other for bad noise choices?
- [ ] is revive a fun panic moment?

---

# Phase D — Objective and Progression Loop

## D.1 Feature Spec: Section Manager

### Goal

Divide the map into progression chunks with local state.

### Responsibilities

- [ ] track current section state
- [ ] lock/unlock progression
- [ ] spawn / enable local threats
- [ ] register beacon completion

### Acceptance Criteria

- [ ] section transitions are deterministic
- [ ] designers can configure section order and dependencies

## D.2 Feature Spec: Sound Beacon Device

### Goal

Introduce a map objective that creates a dim persistent visibility zone.

### Behavior

- [ ] beacon exists in dark section
- [ ] players reach beacon and activate it via interaction and/or sound contribution
- [ ] beacon powers up over time or in stages
- [ ] once active, beacon emits localized low-level light / visibility pulse

### Design Constraints

- [ ] beacon should reduce stress but not remove the need for sound entirely
- [ ] beacon zone should be strategically meaningful

### Acceptance Criteria

- [ ] activating beacon feels rewarding
- [ ] local visibility around beacon is persistently improved

## D.3 Feature Spec: Section Completion

### Goal

Advance players through the map.

### Behavior

- [ ] each section contains one main objective
- [ ] once complete, path to next section opens
- [ ] run ends after final objective and extraction or final state

### Acceptance Criteria

- [ ] run progression is understandable without developer explanation

## D.4 Review Questions

- [ ] does beacon activation provide a good rhythm break?
- [ ] is progress visible enough to sustain a full run?
- [ ] does the map feel too safe once a beacon is active?

---

# Phase E — Multiplayer Foundation

## E.1 Networking Authority Model Spec

### Goal

Define ownership and synchronization boundaries before large-scale implementation.

### Recommended Model

- [ ] host-authoritative for enemy state, objectives, and progression
- [ ] clients authoritative for local input capture only
- [ ] gameplay sound events are transmitted as derived values

### Sync Categories

1. player transform and state
2. sound events
3. enemy state
4. objective state
5. revive interactions
6. UI-relevant global state

### Acceptance Criteria

- [ ] authority model documented and consistently applied

## E.2 Feature Spec: Lobby / Session Flow

### Goal

Allow players to host and join co-op sessions.

### Requirements

- [ ] create lobby
- [ ] invite friend
- [ ] join lobby
- [ ] load gameplay scene together
- [ ] return to lobby or main menu cleanly

### Acceptance Criteria

- [ ] two players can start a run reliably

## E.3 Feature Spec: Networked Sound Events

### Goal

Ensure remote players' sound actions affect the game world consistently.

### Important Decision

Transmit:

- [ ] player id
- [ ] world position
- [ ] sound intensity
- [ ] reveal radius
- [ ] timestamp / sequence id

Do not transmit:

- [ ] full raw microphone audio for gameplay logic

### Acceptance Criteria

- [ ] remote player sound triggers enemy response and reveal logic consistently for all clients

## E.4 Feature Spec: Networked Enemy State

### Goal

Keep enemy behavior coherent across clients.

### Acceptance Criteria

- [ ] enemies do not jitter heavily
- [ ] attack / hit outcomes are consistent
- [ ] downed transitions are consistent

## E.5 Feature Spec: Networked Objectives

### Goal

Ensure beacon activation and section progression stay authoritative and replicated.

### Acceptance Criteria

- [ ] objective state never diverges between clients in normal play

## E.6 Multiplayer Test Matrix

Test at minimum:

- [ ] host + 1 client
- [ ] host + 2 clients
- [ ] reconnect behavior defined if not supported
- [ ] lobby cancellation
- [ ] failed join path
- [ ] scene load synchronization
- [ ] revive during enemy chase
- [ ] simultaneous sound spikes from multiple players

---

# Phase F — Vertical Slice Polish

## F.1 Audio Pass 01

### Goals

- [ ] underwater ambience
- [ ] enemy approach cues
- [ ] beacon hum
- [ ] tension ramp for high noise meter
- [ ] clearer revive locator sounds

### Acceptance Criteria

- [ ] players can use audio for decision making, not just atmosphere

## F.2 Visual Pass 01

### Goals

- [ ] replace purely debug visuals with consistent style
- [ ] establish wireframe / edge / glow language
- [ ] improve readability of revealed objects

### Acceptance Criteria

- [ ] screenshots communicate the hook clearly

## F.3 UI Pass 01

### Required UI

- [ ] lobby state
- [ ] connection state
- [ ] shared noise meter
- [ ] downed state indicator
- [ ] revive feedback
- [ ] beacon status
- [ ] settings menu

### Acceptance Criteria

- [ ] players understand the state of the run without voice explanation from the developer

## F.4 Tuning Pass 01

Tune:

- [ ] reveal radius mapping curve
  n- noise meter fill / decay
- [ ] enemy move speed
- [ ] attack window
- [ ] revive duration
- [ ] beacon activation time
- [ ] fade duration

### Acceptance Criteria

- [ ] the game produces tension without constant unwinnable spirals

---

# Phase G — v0.1 Expansion

## G.1 Enemy Variant 02 or Behavior Variant

Possible options:

- [ ] lurker that waits for repeated sounds
- [ ] charger that attacks on high noise threshold
- [ ] mimic-focused threat that manipulates team communication

### Acceptance Criteria

- [ ] new threat changes player behavior meaningfully

## G.2 Voice Mimic / False Help System

### Goal

Introduce distrust and deception.

### Behavior Options

- [ ] record short clips from player voice chat / input session locally
- [ ] play them back from enemy positions or dark corners
- [ ] trigger generic help calls and movement bait sounds

### Constraints

- [ ] must be readable enough to feel deceptive, not random nonsense
- [ ] must not overfire and become annoying

### Acceptance Criteria

- [ ] at least some testers are fooled by the system
- [ ] system creates memorable moments without breaking clarity entirely

## G.3 Difficulty Modes

Three difficulties maximum for v0.1 if implemented.

Suggested structure:

- [ ] Normal
- [ ] Hard
- [ ] Abyssal

Difficulty knobs:

- [ ] noise decay rate
- [ ] enemy speed
- [ ] beacon activation demands
- [ ] revive time
- [ ] false audio frequency

### Acceptance Criteria

- [ ] higher difficulties feel like meaningful escalation, not only bigger health numbers

## G.4 Steam Integration

Required for v0.1:

- [ ] rich presence
- [ ] invite friends
- [ ] basic ownership / launch testing
- [ ] overlay validation

### Acceptance Criteria

- [ ] players can invite friends and join sessions through Steam reliably

## G.5 Basic Release Operations

- [ ] crash logging strategy
- [ ] save / config persistence
- [ ] version string in UI
- [ ] build pipeline checklist

---

# 9. Feature Dependency Graph

## Core Dependency Order

1. player movement
2. microphone reader
3. sound event system
4. revealable environment
5. reveal pulse visualizer
6. shared noise meter
7. enemy reaction
8. downed state
9. revive logic
10. beacon objective
11. section progression
12. networking
13. Steam integration
14. mimic system
15. difficulty modes

Rule:
Do not build later features before earlier dependencies are stable.

---

# 10. Per-System Technical Notes

## 10.1 Microphone Input

- [ ] implement smoothing to avoid flicker
- [ ] provide calibration values in settings eventually
- [ ] support push-to-calibrate or sample-baseline function
- [ ] expose debug graphs in editor

## 10.2 Reveal System

Initial implementation can be gameplay-correct rather than beautiful.

Stages:

1. debug spheres and object toggles
2. emissive material flashes
3. proper shader-based outlines / wiremesh pulses

## 10.3 Enemy AI

Avoid overengineering early.

Start with:

- [ ] state machine
- [ ] navigation target = latest loudest sound event
- [ ] attack if close enough

Do not start with:

- [ ] behavior trees
- [ ] complex planner AI

## 10.4 Networking

- [ ] host-authoritative for enemy and objective truth
- [ ] clients submit sound events
- [ ] use sequence ids or timestamps to avoid event confusion
- [ ] keep data payloads small

## 10.5 Steam

Integrate late enough that it does not block prototype iteration, but early enough that v0.1 platform features are not rushed.

Recommended timing:

- [ ] after vertical slice, before content lock

---

# 11. Testing Strategy

## 11.1 Test Categories

- [ ] unit-level utility tests where practical
- [ ] gameplay functional tests
- [ ] network sync tests
- [ ] regression tests after merges
- [ ] session-length playtests

## 11.2 Core Functional Test List

### Mic and Reveal

- [ ] different volume levels map to expected reveal radii
- [ ] silence does not falsely trigger reveals
- [ ] reveal fade works for multiple objects simultaneously

### Noise Meter

- [ ] single small sounds produce low fill
- [ ] repeated loud sounds spike meter significantly
- [ ] meter decays over time when silent

### Enemy

- [ ] enemy moves to sound origin
- [ ] enemy reprioritizes louder recent sound when appropriate
- [ ] enemy attack transitions down player correctly

### Revive

- [ ] downed player can still emit locator sound
- [ ] teammate can locate and revive successfully
- [ ] revive fails correctly if interrupted

### Beacon

- [ ] beacon can be activated once requirements met
- [ ] beacon zone visibility persists
- [ ] section completion unlocks next section

### Multiplayer

- [ ] remote sound events affect shared world state
- [ ] remote revive state is visible and correct
- [ ] objective state remains synchronized
- [ ] one player disconnect path handled gracefully or explicitly unsupported

## 11.3 Playtest Questions

After each external playtest ask:

- [ ] what did you think the goal was?
- [ ] what caused your death most often?
- [ ] was making sound fun or stressful or both?
- [ ] did reviving teammates feel satisfying?
- [ ] did beacon activation feel rewarding?
- [ ] what moment would you clip and share?

---

# 12. Content Plan for v0.1

## 12.1 Map Target

One complete polished map.

Suggested structure:

- [ ] Intro section: learn echo and movement
- [ ] Threat section: first sound hunter encounter
- [ ] Recovery section: first beacon activation
- [ ] Pressure section: revive under threat
- [ ] Final section: higher complexity + extraction

## 12.2 Enemy Target

Minimum:

- [ ] 1 core enemy, well tuned

Preferred:

- [ ] 2nd variant or behavior modifier for diversity

## 12.3 Objective Target

- [ ] 2–3 beacon activations across a run
- [ ] one culminating final sequence

## 12.4 Session Length Target

15–30 minutes for v0.1 run target, depending on team coordination and difficulty

---

# 13. Release Criteria for v0.1

The game is ready for a first Steam build when:

- [ ] a full match can be completed end-to-end reliably
- [ ] core loop is understood by new players within the first few minutes
- [ ] at least 2–4 external playtest groups have confirmed fun / tension / replay interest
- [ ] no critical progression blockers remain
- [ ] no common hard crash remains unresolved
- [ ] lobby and invite flow works reliably enough for friends to join without developer intervention
- [ ] settings allow microphone selection / volume tuning if required by implementation
- [ ] store page messaging accurately reflects the actual experience

---

# 14. Risks and Mitigations

## Risk 1: The mic mechanic is novel but not fun long-term

Mitigation:

- [ ] validate early with the smallest playable loop
- [ ] cut content expansion until the loop is repeatedly enjoyable

## Risk 2: Consumer microphones are noisy and inconsistent

Mitigation:

- [ ] add smoothing, thresholds, and calibration support
- [ ] test on multiple hardware setups early

## Risk 3: Multiplayer complexity overwhelms progress

Mitigation:

- [ ] prototype offline first
- [ ] network derived sound events, not raw audio gameplay state
- [ ] keep host-authoritative model simple

## Risk 4: Darkness becomes frustrating rather than tense

Mitigation:

- [ ] tune fade carefully
- [ ] use beacon zones for relief
- [ ] ensure silhouettes and important props are readable when revealed

## Risk 5: Mimic system becomes confusing noise spam

Mitigation:

- [ ] add sparingly
- [ ] make its triggers readable and intentional
- [ ] playtest deception frequency

## Risk 6: Steam features are left too late

Mitigation:

- [ ] integrate after vertical slice, before final stabilization

---

# 15. Production Checklist by Stage

## Stage 0 Checklist

- [ ] Unity project created
- [ ] Repo initialized
- [ ] Folder structure created
- [ ] Build doc committed
- [ ] Feature spec template committed

## Stage 1 Checklist

- [ ] Player movement works
- [ ] Mic reader works
- [ ] Reveal pulse works
- [ ] Reveal fade works
- [ ] Debug UI works

## Stage 2 Checklist

- [ ] Noise events implemented
- [ ] Shared noise meter implemented
- [ ] Enemy reacts to sound
- [ ] Downed state implemented
- [ ] Revive by sound implemented

## Stage 3 Checklist

- [ ] Beacon object implemented
- [ ] Beacon zone visibility implemented
- [ ] Section completion implemented
- [ ] One full offline run possible

## Stage 4 Checklist

- [ ] Lobby flow implemented
- [ ] 2-player networking stable
- [ ] Sound events synchronized
- [ ] Enemy synchronized
- [ ] Revive synchronized
- [ ] Beacon synchronized

## Stage 5 Checklist

- [ ] Vertical slice map complete
- [ ] Audio pass complete
- [ ] UI pass complete
- [ ] External playtest complete
- [ ] Top issues triaged

## Stage 6 Checklist

- [ ] v0.1 content complete
- [ ] Steam presence implemented
- [ ] Invite flow works
- [ ] Voice mimic implemented or explicitly cut
- [ ] Difficulty system implemented or explicitly cut

## Stage 7 Checklist

- [ ] Major bugs resolved
- [ ] Performance pass complete
- [ ] Release notes drafted
- [ ] Store copy drafted
- [ ] v0.1 build approved

---

# 16. Suggested Initial Backlog

## Epic 1: Core Perception

- [ ] mic input reader
- [ ] volume normalization
- [ ] sound event emitter
- [ ] revealable object component
- [ ] reveal pulse manager
- [ ] debug HUD

## Epic 2: Threat

- [ ] noise meter
- [ ] enemy state machine
- [ ] sound target navigation
- [ ] player damage and downed state
- [ ] revive logic

## Epic 3: Progression

- [ ] section manager
- [ ] beacon objective
- [ ] section unlock gates
- [ ] end-of-run flow

## Epic 4: Multiplayer

- [ ] host / join flow
- [ ] session scene loading
- [ ] player sync
- [ ] sound event sync
- [ ] enemy sync
- [ ] objective sync

## Epic 5: Presentation

- [ ] visual style pass
- [ ] audio style pass
- [ ] UI pass
- [ ] settings menu

## Epic 6: Platform

- [ ] Steam integration
- [ ] rich presence
- [ ] invites
- [ ] basic release pipeline

---

# 17. How to Hand This to an AI

When asking an AI to implement a feature, include:

1. the relevant section of this build plan
2. the feature spec for that system
3. the current architecture constraints
4. the exact Unity version and packages in use
5. whether the code is offline-only or network-aware
6. acceptance criteria

Example prompt pattern:

```text
You are helping implement a Unity feature for ECHO DEPTHS.
Context:
- Multiplayer underwater co-op game
- Sound reveals world, sound attracts enemies
- We are currently in Phase B offline prototype
- Need a microphone loudness reader only, no networking

Requirements:
- Capture current microphone loudness
- Normalize to 0–1
- Provide optional smoothing
- Expose current value in Update
- Fire event when above threshold

Constraints:
- Unity C#
- No speech recognition
- Clean, production-leaning code
- Separate responsibilities cleanly

Deliver:
- script(s)
- explanation of setup in Unity Inspector
- any caveats
- test checklist
```

---

# 18. Immediate Next Action Plan

Do these first, in order:

1. create repo and docs structure
2. create Unity project and folder structure
3. implement player movement
4. implement microphone loudness reader
5. implement debug reveal pulse
6. build one simple test room with primitive geometry
7. test whether sound-to-vision is satisfying before building anything else

Do not move to enemies or networking until step 7 is genuinely positive.

---

# 19. Final Rule Set

Project rules:

- [ ] protect the core hook above all else
- [ ] validate fun before adding content
- [ ] prototype ugly, then polish later
- [ ] network events, not raw gameplay audio data
- [ ] keep v0.1 smaller than your ambition wants
- [ ] every system must support the one-sentence pitch
- [ ] when in doubt, cut scope

If a proposed feature does not improve one of these, it should be deferred:

- [ ] sound as vision
- [ ] sound as danger
- [ ] co-op panic and coordination
- [ ] memorable multiplayer moments

