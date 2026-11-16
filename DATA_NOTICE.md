# Data and asset notice

The visualizations contain model-generated predictions and rendered comparisons against sensor measurements from the following third-party datasets:

- **Dual Radar**, Zhang et al., *Dual Radar: A Multi-modal Dataset with Dual 4D Radar for Autonomous Driving*. [Official project](https://github.com/adept-thu/Dual-Radar) · [Paper](https://arxiv.org/abs/2310.07602).
- **View-of-Delft**, Palffy et al., *Multi-Class Road User Detection With 3+1D Radar in the View-of-Delft Dataset*, IEEE Robotics and Automation Letters, 2022. [Official development kit](https://github.com/tudelft-iv/view-of-delft-dataset) · [Dataset access](https://viewofdelft-dataset.tudelft.nl/).

Raw radar/LiDAR binaries, original full-resolution camera image files, human annotations and model checkpoints are not redistributed here. The paper-model videos contain resized camera views embedded in four-column research comparisons, alongside rendered sensor measurements and model predictions. These derived illustrations are not a replacement for the original datasets and do not grant a license to the underlying sensor content.

Dataset ownership and applicable third-party terms remain with their respective rights holders. This repository does not grant a blanket license to the underlying datasets or waive their access/research-use conditions. Consult the dataset distributors before reuse or redistribution, particularly for commercial purposes.

Scene selection is qualitative. The files are not an independent test benchmark, and playback speed is not a runtime claim. The current paper-model demonstration uses 180 frames with the original DDPM schedule and manuscript learned decoder; its hashes and display protocol are in `paper_ddpm1000_manifest.json`. The older `showcase_manifest.json` is retained as historical provenance only.
