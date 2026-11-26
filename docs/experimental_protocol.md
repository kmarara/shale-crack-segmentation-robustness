# Experimental protocol

**Status:** Provisional protocol, to be finalised after the full article, supplementary information and dataset files have been audited.

## 1. Dataset audit before modelling

Record for every image stack:

- specimen identifier and physical specimen relationships;
- saturation state;
- scan voltage and whether an aluminium ring was present;
- stack dimensions, slice count, pixel spacing and voxel spacing where supplied;
- image format, bit depth and intensity range;
- annotation format, dimensions, class encoding and annotator notes if supplied;
- missing, duplicated, corrupted or unreadable slices;
- whether scans represent repeated observations of the same specimen.

Create a machine-readable manifest. Do not infer missing specimen identifiers from filenames without documenting the inference.

## 2. Leakage control and split design

The independent unit should be the physical specimen, or the highest-level independent scan unit justified by the metadata. Never randomly split neighbouring slices from the same stack across training and test sets.

Preferred design, if there are enough independent groups:

1. Group specimens by condition and identity.
2. Hold out complete specimens for testing.
3. Use grouped cross-validation within the remaining training specimens for model selection.
4. Keep a final specimen-level test set untouched until the pipeline is fixed.

If the dataset contains too few independent specimens for a reliable held-out test, report that limitation. Use grouped cross-validation and present fold-level results rather than pretending that thousands of correlated slices are independent samples.

## 3. Experiments

### E0. Data and label quality audit

Visualise raw CT slices beside manual masks. Check alignment, class encoding, boundary ambiguity, annotation consistency and crack-pixel prevalence. Inspect representative slices from every available condition.

### E1. Transparent baseline

Implement a simple intensity-threshold baseline, with any threshold selection performed using training data only. Consider a small number of documented preprocessing and morphological variants. This baseline is a reference, not a presumed competitor to deep learning.

### E2. Compact learned baseline

If compute and data volume permit, train a standard U-Net as the first learned model. Keep the implementation deliberately small and reproducible. Record architecture, parameter count, optimiser, learning rate, batch size, epoch count, early-stopping rule, augmentations, loss, random seed and hardware.

### E3. Within-condition generalisation

Train and evaluate using grouped specimen splits within a condition, where enough independent specimens exist. This estimates performance without deliberately changing acquisition conditions.

### E4. Cross-condition generalisation

Only if metadata confirms the necessary independent groups, train on one condition and evaluate on another. Candidate contrasts include 100 kV versus 150 kV, with-ring versus without-ring imaging, and saturation-state transfer.

Do not pool or compare conditions as if they were a fully crossed design unless the actual specimen-condition matrix supports that interpretation. Avoid confounding specimen identity with acquisition condition.

### E5. Error and image-quality analysis

Review false positives and false negatives. Explore relationships between error rates and image contrast, noise, local texture, crack thickness and crack-pixel fraction. Treat these as exploratory associations.

## 4. Metrics

Report crack-class metrics, not only aggregate accuracy.

- Dice coefficient / F1 score for the crack class.
- Intersection over Union (IoU) for the crack class.
- Precision and recall for the crack class.
- Specificity and balanced accuracy.
- Confusion matrix and crack prevalence.
- False-positive and false-negative pixel rates.
- Per-specimen and per-stack scores, with fold-level distributions.

For thin cracks, also consider boundary-sensitive metrics if a defensible implementation is available. Do not select metrics after seeing which ones make the model look best.

For crack-volume use, calculate predicted and annotated crack volume only after confirming voxel dimensions and mask semantics. Compare absolute and relative volume error at the specimen or stack level. A good pixel-wise score does not automatically guarantee accurate crack volume.

## 5. Uncertainty and statistical reporting

- Report mean, standard deviation and range across independent specimens or folds.
- Use specimen-level bootstrap intervals only where the number of independent specimens makes this meaningful.
- Do not calculate confidence intervals by treating adjacent slices as independent observations.
- Report the number of specimens, stacks and slices contributing to every result.
- Separate model-selection data from final evaluation data.

## 6. Reproducibility record

Save configuration files, random seeds, package versions, split manifests, training logs, model checkpoints where practical, and exact commands. Keep raw data outside version control. Store derived results only when they can be regenerated or are small and useful.

## 7. Stop/go criteria

Proceed to cross-condition modelling only if the data audit confirms enough independent specimens in the relevant conditions. If not, narrow the project to within-condition specimen-level evaluation and qualitative error analysis. A smaller defensible study is preferable to an invalid comparison.
