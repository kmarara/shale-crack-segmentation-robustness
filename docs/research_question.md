# Research question and hypotheses

## Scope

This project examines the robustness of automated crack segmentation in X-ray CT images of Mancos shale. The target is the crack phase in the manually annotated images. The study will first establish what the released dataset actually contains and how its specimens and scans are related.

## Primary question

How does crack-segmentation performance change when a model is evaluated on CT images acquired under imaging or saturation conditions that differ from those represented in its training data?

## Secondary questions

1. How much does performance vary between independent specimens or CT stacks under nominally similar conditions?
2. Are errors concentrated in low-contrast, thin, disconnected or spatially complex crack regions?
3. Does a simple, transparent baseline provide a useful reference against which a learned segmentation model can be judged?
4. Can image-quality descriptors help explain systematic failure modes?

## Pre-registered working hypotheses

These are hypotheses to test, not established facts.

- H1: A model trained and tested within the same acquisition condition will perform better than a model tested on a distinct acquisition condition, if the latter introduces a meaningful distribution shift.
- H2: Crack recall and crack Dice/IoU will be more sensitive to condition shifts than overall pixel accuracy, because the crack class is expected to occupy a relatively small fraction of pixels.
- H3: Models evaluated on held-out specimens will show greater uncertainty and possibly lower scores than slice-randomised validation, because neighbouring slices can share highly similar textures and crack geometry.
- H4: Image-quality features such as intensity contrast, noise level and local texture will be associated with some segmentation errors. This association will be exploratory and not interpreted as causal.

## Scope boundaries

- Do not assume that every saturation state is paired with every imaging condition. Verify the experimental matrix from the dataset metadata.
- Do not assume that the public dataset reproduces the exact training and validation split in the paper.
- Do not call a comparison a reproduction unless the original preprocessing, split, architecture and training details have been recovered and implemented.
- Do not claim novelty until the original paper, its supplementary information and related work have been reviewed.
- Do not make reservoir-scale claims from image-segmentation metrics alone.

## Intended contribution

A carefully documented, specimen-aware robustness assessment, with transparent baselines, cross-condition evaluation where supported by the data, and an error analysis that identifies when automated crack masks should be treated cautiously.
