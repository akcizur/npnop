# NPnop — Third-Person Controller Web Sandbox

A GitHub Pages-ready Three.js third-person web sandbox inspired by [MaximeCrp/third-person-controller-boilerplate](https://github.com/MaximeCrp/third-person-controller-boilerplate).

## Runtime

- Three.js 0.160 WebGL runtime loaded from a CDN
- Procedural world, sky, fog, collision obstacles, radar and camera presets
- Kinematic capsule collision, jump, gravity, sprint and camera-relative movement
- Keyboard, Gamepad API and dual touch controls (move joystick + look pad)
- A custom stylized 3D warrior, automatically generated as a rigged GLB during Pages deployment
- 17-joint humanoid skeleton with Idle, Walk, Run, Jump, Attack, KnockDown and GetUp clips
- A procedural in-browser fallback and a **Load Warrior GLB** picker remain available
- Single-file game runtime in `index.html`

## Run locally

```sh
python3 -m http.server 8000
```

Open http://localhost:8000. To generate the bundled warrior locally, install Python 3.12+, NumPy and Trimesh, then run:

```sh
gzip -dc tools/warrior_builder.py.gz > /tmp/warrior_builder.py
python -m pip install numpy trimesh
python /tmp/warrior_builder.py assets/warrior.glb
```

## GitHub Pages

The `.github/workflows/pages.yml` workflow builds `assets/warrior.glb` and publishes it with the static game. No manually uploaded model is required for this generated character. Enable GitHub Pages with **GitHub Actions** as the deployment source in repository settings.

## Character model

The generated Ashen Warden is a stylized recreation inspired by the supplied references: bald head, long ash-grey beard, exposed muscular chest, torn charcoal robes, olive forearm wraps and aged belt charms. The model is generated locally in CI (not downloaded at runtime) and uses standard GLB/glTF 2.0 materials and animation clips.

This is an original procedural model, **not a downloaded copy of the Tripo3D model page**. The menu's **Load Warrior GLB** control can still preview a separately exported Tripo GLB in the current browser session. The game loader normalizes model height and applies a 180° Y rotation to align standard GLB forward (+Z) with the controller.

The model has 17 joints and per-part rigid weights, suitable for a stylized prototype. It is not a film-quality deformation rig; smooth shoulder/hip weight blending can be improved in Blender later.

## Controls

Desktop: WASD / arrows, Shift sprint, Space jump, F kick, K knock down, G get up, R reset; click the scene for pointer lock.

Touch: dynamic left joystick for movement, right-side look pad for camera, action buttons on the right.

Gamepad: analog left stick, A/Cross jump, RT/LB/RB/L3 sprint.

## Asset policy

The generated character is made from procedural geometry. Third-party packages load from their CDNs and retain their own licenses. Do not commit proprietary models or expiring/private download URLs unless their licenses permit redistribution.
