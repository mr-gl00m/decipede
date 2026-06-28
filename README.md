# DECIPEDE_LAB
![DECIPEDE_LAB](decipede.png)

3D neuroevolution of a segmented crawler, in a single HTML file. A chain of hinge-jointed body segments with articulated legs learns to walk forward; gait emerges from evolved neural weights, not animation.

**Subject:** `myriapoda-ignis-digitalis` · **v0.2**

## Try it

It's one self-contained page. Two runtime dependencies (`three@0.160.0` and `cannon-es@0.20.0`) load from CDN via an importmap, so it needs an internet connection but no install and no build step.

* **Hosted:** open the GitHub Pages URL (Settings → Pages → deploy from branch).
* **Local:** because it's an ES-module page, a raw `file://` double-click is blocked in most browsers. Serve it instead:

  ```bash
  python -m http.server 8000
  # then open http://localhost:8000/decipede-evolve-3d.html
  ```

## What it does

Each creature is a chain of rigid segments joined by yaw-bending hinge motors, with 4-segment articulated legs (coxa → femur → tibia → tarsus) per side, simulated in cannon-es. A small neural network per creature drives the joint motors. A genetic algorithm evolves the weights across generations.

Fitness is **forward displacement**: flat track, no obstacles, no checkpoints. Pure distance, so the population is selected purely on how far it learned to crawl. (The checkpoint-bonus path exists in the code for a later obstacle mode; training mode keeps it off for clean gait-learning.)

## Controls

* **Run / Pause / Skip Gen / Reset**: evolution control
* **Population / Mutation Rate / Sim Speed / Segments**: live sliders (Segments rebuilds the body plan)
* **Training Mode**: flat-track pure-distance fitness (on by default)
* **Export ★ / Import**: download or load the current best brain as JSON
* **Load Auto / Clear Auto**: reseed from, or wipe, the autosaved champion (`localStorage`)
* **Camera**: follow / free / top

The fitness-per-generation graph and a live gen/run overlay sit on the right.

## Layout

```
proj_decipede/
├── decipede-evolve-3d.html   ← the whole app
├── decipede.png              ← banner
└── archive/
    ├── centipede-evolve.html ← the 2D predecessor
    └── *.json                ← an early exported champion brain
```

## License

MIT. See [LICENSE](LICENSE).
