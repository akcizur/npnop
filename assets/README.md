# Warrior GLB asset

The runtime expects the exported character at:

`assets/warrior.glb`

This placeholder instructions file is intentionally committed in place of a 3D binary. Export the model from the linked Tripo3D project as a rigged GLB and add the file here when you have the export and redistribution rights.

Recommended checks:
- GLB contains mesh geometry and material/texture data.
- A humanoid skeleton and skin weights are present.
- Embedded clip names are preferably recognizable (`Idle`, `Walk`, `Run`, `Jump`, `Attack`, `GetUp`).
- Use Mixamo-compatible bone naming for the built-in procedural bone fallback.
- Keep the file reasonably small for mobile GitHub Pages users; compress or optimize it in Blender or another tool if needed.

The in-page **Load Warrior GLB** picker is useful for previewing the exported file before adding it to the repository. Loading a local file into the browser does not upload or commit it.
