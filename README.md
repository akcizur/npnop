# NPnop — Third-Person Controller Web Sandbox

A GitHub Pages-ready Three.js third-person web sandbox inspired by [MaximeCrp/third-person-controller-boilerplate](https://github.com/MaximeCrp/third-person-controller-boilerplate).

## Runtime

- Three.js 0.160 WebGL runtime loaded from a CDN
- Procedural world, sky, fog, grid floor, collision obstacles, radar and camera presets
- Kinematic capsule collision, jump, gravity, sprint, camera-relative movement and pointer-lock camera
- Keyboard, Gamepad API and dual touch controls (move joystick + look pad)
- A stylized procedural warrior fallback so the game remains playable without the external model file
- Optional rigged GLB character import, animation clip matching and basic bone-driven movement when compatible bone names are available
- Single-file game runtime in `index.html`; no bundler or npm install is required

## Run locally

```sh
python3 -m http.server 8000
```

Open http://localhost:8000. Opening `index.html` as a `file://` URL is not recommended because browser module and asset loading rules vary.

## GitHub Pages

The static project deploys through `.github/workflows/pages.yml`. Enable GitHub Pages with **GitHub Actions** as the build and deployment source in the repository settings.

## Warrior model

On startup, the game tries to load `assets/warrior.glb`. If the file is absent, the procedural warrior fallback remains visible and fully controllable. The landing overlay also has **Load Warrior GLB**, which loads a local `.glb` into the current browser session without uploading it to GitHub.

To include the model in the published site:

1. Export the warrior from Tripo3D as a **rigged GLB**. For best bone-name compatibility, use a Mixamo-compatible humanoid rig if that option is offered.
2. Place the exported file at `assets/warrior.glb`.
3. Commit the GLB to this repository and push to `main`. The Pages workflow publishes the file with the game.
4. Keep only animation clips that you have permission to distribute. Clip names are matched against common labels such as `idle`, `walk`, `run`, `jump`, `attack`/`kick`, `death`/`knockdown` and `getup`.

The loader normalizes model height to approximately 1.82 m and applies a 180° Y rotation so the character faces the game controller's forward direction. If the exported model faces backward, change `root.rotation.y=Math.PI` in `normaliseWarriorRoot()`.

**Important:** the screenshots and the Tripo model page are not the 3D asset itself. This repository does not yet contain a copy of the model binary; an exported `.glb` needs to be added before GitHub Pages can render this exact character automatically. Check the model's usage and redistribution permissions before committing it.

## Controls

Desktop: WASD / arrows, Shift sprint, Space jump, F kick, K knock down, G get up, R reset; click the scene for pointer lock.

Touch: dynamic left joystick for movement, right-side look pad for camera, action buttons on the right.

Gamepad: analog left stick, A/Cross jump, RT/LB/RB/L3 sprint.

## License and assets

The controller code is a static web implementation. Third-party packages load from their CDNs and retain their own licenses. Do not commit proprietary models or expiring/private download URLs unless their licenses permit redistribution.
