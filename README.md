# NPnop — Third-Person Controller Web Sandbox

A GitHub Pages-ready WebGL 2 port inspired by MaximeCrp/third-person-controller-boilerplate.

## v2.0 baseline

This repository implements the attached PRD v2.0 as a lightweight single-file web runtime:

- Three.js 0.160 WebGL 2 runtime
- procedural sky, IBL, bloom and exponential fog
- procedural grid floor + rotated OBB obstacles
- kinematic capsule controller with gravity, jump and wall sliding
- camera-relative WASD / arrow movement
- decoupled visual rotation
- spring-arm camera collision and pitch clamp
- keyboard + mouse, dynamic touch joystick + look pad, Gamepad API
- procedural Web Audio steps / jump / landing
- trauma camera shake and sprint FOV
- SVG radar
- live Inspector sliders
- GDScript exporter
- single-file distribution in index.html

## Run locally

No build step is required.

    python3 -m http.server 8000

Open http://localhost:8000.

## GitHub Pages

The repository is static and can also be deployed automatically by .github/workflows/pages.yml.
GitHub Pages must be enabled for the repository; the connector can write the workflow but cannot change repository Pages settings here.

## Controls

Desktop: WASD / arrows, Shift sprint, Space jump, F kick, K knock down, G get up, R reset, mouse/pointer lock camera.

Touch: dynamic left joystick for movement, right look pad for camera, action buttons on the right.

Gamepad: standard axes; A/Cross jump; RT/LB/RB/L3 sprint.

## Architecture

Scene → World → Player Root → Visuals + Camera Mount → Camera

Collision uses capsule-vs-rotated-OBB tests with iterative minimum-translation resolution.

## Asset policy

The runtime character and materials are procedural. The original Godot project and its Mixamo asset remain the reference only; this repo does not redistribute that GLB.