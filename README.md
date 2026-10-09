# Predicting and Quantifying Lysosome Organisation in PhTau-Aggregate Cells

Computational analysis for investigating lysosome abundance, morphology, and spatial organisation in cells expressing phosphorylated Tau (PhTau). This repository contains notebooks and workflows for image preprocessing, image-to-image translation, and point-based spatial analysis.

## Project overview

This project evaluates computational approaches for detecting and characterising lysosome patterns associated with Tau pathology. The experimental model uses H4 neuroglioma cells with doxycycline-inducible Tau P301L/S320F expression. Induced cells are analysed 120 hours after doxycycline treatment alongside untreated controls, with analyses also distinguishing PhTau-positive and PhTau-negative cells.

The research combines fluorescence microscopy image analysis with spatial statistics. The image channels include LAMP1-labelled lysosomes and PhTau; actin and, in a second dataset, DAPI provide additional cellular context. Z-stacks are analysed as maximum-intensity projections.

## Aims

* Evaluate Pix2Pix and CycleGAN for translating between lysosome and PhTau fluorescence channels.
* Quantify lysosome abundance and morphology.
* Characterise lysosome spatial organisation using distances, graph-based features, and Ripley’s K-function.
* Compare lysosome measurements between PhTau-positive and PhTau-negative cells.
* Assess how manual lysosome morphology annotations relate to quantitative measurements.

## Repository contents

| Path                                                                   | Contents                                        |
| ---------------------------------------------------------------------- | ----------------------------------------------- |
| [`Processing/`](Processing/)                                           | Image preprocessing workflows.                  |
| [`Image-to-image translation/`](Image-to-image%20translation/)         | Pix2Pix and CycleGAN.                           |
| [`Spatial distributions/`](Spatial%20distributions/)                   | Distance distributions and Ripley’s K-function. |
| [`Graph-based analysis/`](Graph-based%20analysis/)                     | Graph-based features analysis.                  |
| [`Abundance and morphology.ipynb`](Abundance%20and%20morphology.ipynb) | Lysosome abundance and morphology analysis.     |
| [`Annotations.ipynb`](Annotations.ipynb)                               | Phenotype annotations.                          |

## Analysis overview

### Image-to-image translation

Pix2Pix and CycleGAN notebooks are adapted from the ZeroCostDL4Mic toolbox. Pix2Pix uses paired image examples, whereas CycleGAN supports unpaired image-domain translation. The workflows investigate whether information in one fluorescence channel can help predict structure or cell state in another. Model predictions should be interpreted as computational estimates, not as substitutes for experimental measurements.

### Lysosome abundance and morphology

Lysosome properties are quantified from image-derived detections and compared across experimental groups and phenotypes.

### Graph-based analysis

Graphs are created via Delaunay triangulation or distance-based methods; resulting features are quantified and compared across experimental groups.

### Spatial organisation

Analyses include inter-organelle, nearest-neighbour, and lysosome-to-nucleus distance distributions, and Ripley’s K-function with translation edge correction.

## Getting started

1. Clone or download this repository.
2. Open the relevant `.ipynb` notebook in JupyterLab, Jupyter Notebook, or Google Colab, depending on the workflow.
3. Review the notebook from top to bottom before running it. Set the input image, annotation, and output paths to match your local data.
4. Install the packages required by that notebook in an appropriate Python environment.
5. Run the notebook cells in order and inspect intermediate segmentations, detections, and visualisations before interpreting summary measurements.

```bash
git clone https://github.com/cvcapelle-uu/MCLS-major-research-project.git
cd MCLS-major-research-project
```

Image-to-image translation workflows may require separate environments and additional GPU or software configuration; use the setup instructions in the relevant notebook. Python and package versions, model settings, and any changed ZeroCostDL4Mic defaults should be recorded alongside results for reproducibility.

## Reproducibility and interpretation

Results depend on image acquisition, preprocessing, segmentation and spot-extraction settings, cell classification, model hyperparameters, and the spatial-analysis choices. Record these settings and software versions when reproducing an analysis. Validate image-derived detections and model predictions against the source images and available annotations.

## Citation and acknowledgement

If you use this code or adapt its workflows, cite the repository and the associated research report when available. Please also acknowledge the ZeroCostDL4Mic toolbox for workflows derived from it, following its citation guidance.

## License

No license is specified in the repository at the time this README was prepared. Unless a license is added, reuse and redistribution may be restricted by copyright. Add an appropriate license file if you intend to permit reuse.

## Contact

For questions about the project or repository, open a GitHub issue or contact the repository owner through GitHub.
