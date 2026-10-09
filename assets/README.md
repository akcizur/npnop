# Generated warrior GLB

The GitHub Pages workflow generates `assets/warrior.glb` from the compact procedural builder in `tools/warrior_builder.py.gz` before uploading the static site.

To generate locally:

```sh
python -m pip install numpy trimesh
gzip -dc tools/warrior_builder.py.gz > /tmp/warrior_builder.py
python /tmp/warrior_builder.py assets/warrior.glb
```

The generated GLB includes a 17-joint skin and seven animation clips: `Idle`, `Walk`, `Run`, `Jump`, `Attack`, `KnockDown` and `GetUp`. The asset is procedural and reference-inspired; it is not the exported Tripo3D page model.
