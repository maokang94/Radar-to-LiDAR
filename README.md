# Radar-to-LiDAR

**Dense Radar-to-LiDAR Point Cloud Generation via Stratified Gaussian Encoding and Offset-Aware Conditional Diffusion**

From sparse radar returns to structured 3D point clouds. This repository presents qualitative results of our radar-conditioned diffusion method, using stratified Gaussian encoding (SSG) and offset-aware alignment (ODA).

**[Continuous demos](#continuous-point-cloud-comparisons) · [Download 3D samples](#downloadable-3d-point-clouds) · [Visualization details](#visualization-protocol)**

![Radar input, generated point cloud and LiDAR reference in a Dual Radar tunnel scene](assets/dual_tunnel.png)

## Continuous point-cloud comparisons

Each animation shows **40 consecutive saved predictions**, with the corresponding radar input and LiDAR reference. Read every comparison from left to right: **Input radar → Generated point cloud → LiDAR GT**. All panels use the same view and height colors.

### Dual Radar · Tunnel

Reconstructed tunnel-side structures and nearby objects, viewed from above.

![Continuous tunnel comparison on Dual Radar](assets/dual_tunnel.gif)

Frames `006480–006519` · SSG + ODA, two height strata.

### Dual Radar · Urban road

Roadside geometry and scene objects over a continuous urban-road segment.

![Continuous urban-road comparison on Dual Radar](assets/dual_urban.gif)

Frames `007120–007159` · SSG + ODA, two height strata.

### View-of-Delft · Urban scene

Generation from the calibrated five-frame accumulated radar input.

![Continuous urban-scene comparison on VoD](assets/vod_urban.gif)

Frames `04720–04759` · SSG + ODA, one height stratum.

These are selected qualitative clips, not an exhaustive benchmark. Frame order is preserved without dropping intermediate frames. Playback is set to **6.25 displayed frames/s** for presentation; it is **not** a measurement of inference speed or the original sensor timing. Generation errors and temporal variation remain visible.

## Downloadable 3D point clouds

**[Download all nine generated PLY samples](samples/generated_samples.zip)** and open them in CloudCompare, MeshLab, or another PLY-compatible viewer. These are model predictions, not encoded/decoded LiDAR reconstructions.

| Scene | Generated sample frame IDs | Preview |
| :--- | :--- | :--- |
| Dual Radar — Tunnel | [006480](samples/dual_tunnel_006480.ply), [006500](samples/dual_tunnel_006500.ply), [006519](samples/dual_tunnel_006519.ply) | [PNG](assets/dual_tunnel.png) |
| Dual Radar — Urban road | [007120](samples/dual_urban_007120.ply), [007140](samples/dual_urban_007140.ply), [007159](samples/dual_urban_007159.ply) | [PNG](assets/dual_urban.png) |
| VoD — Urban scene | [04720](samples/vod_urban_04720.ply), [04740](samples/vod_urban_04740.ply), [04759](samples/vod_urban_04759.ply) | [PNG](assets/vod_urban.png) |

All PLY files contain the **full saved prediction**, not only the region displayed in the animation. Coordinates are in **metres**, with **x forward, y left, z up**, in the frame-local LiDAR coordinate system. RGB encodes height; it is not camera color or measured reflectivity. PLY coordinates are stored to five decimal places. No raw radar/LiDAR datasets, annotations, or camera images are included in this release.

## Visualization protocol

- Fixed bird's-eye view: forward is up; the common display region is **0–48 m forward, ±18 m lateral, −2.5–3.5 m height**.
- Radar measurements are transformed into the corresponding LiDAR frame using the dataset's per-frame calibration. The Dual Radar input combines Arbe and ARS548; VoD uses its provided five-frame radar accumulation.
- Reference LiDAR uses the existing ground-removed evaluation cache. Ground removal is applied to the reference only; generated predictions are not ground-filtered or adjusted using GT.
- Every point inside the shared display region is rendered: no GT-distance filtering, confidence-based pruning, or point-count matching. Height colors and point-marker size are identical across methods. Overlapping points can occupy the same image pixel.
- The downloadable generated clouds retain their native point counts. See the [provenance manifest](showcase_manifest.json) for frame IDs, source-relative paths, SHA-256 hashes, displayed/native point counts, and export hashes.

The clips compare **sensor input, generated output, and reference geometry**, not competing generation methods. The selected clips alone do not establish aggregate accuracy, temporal consistency, or real-time operation.

## Release contents

This is a **visual showcase and generated-sample release**: three animated comparisons, static previews, nine generated 3D clouds, and a provenance manifest. Model source code, training data, and model weights are not included in this release.

## Datasets and acknowledgements

We acknowledge the authors of [Dual Radar](https://github.com/adept-thu/Dual-Radar) and [View-of-Delft](https://github.com/tudelft-iv/view-of-delft-dataset). Please obtain the original datasets from their official distributors and follow their respective terms. See [DATA_NOTICE.md](DATA_NOTICE.md) for attribution and reuse notes.
