# Shale Crack Segmentation Robustness

A reproducible investigation of machine-learning-based crack segmentation in X-ray CT images of Mancos shale, with a focus on robustness across imaging and saturation conditions.

## Research status

**Status: protocol development.** No dataset files have yet been downloaded or analysed, and no model has been trained. No performance results are claimed.

## Motivation

Park, Kim, Shim and Kwon (2026) developed a deep-learning framework to distinguish crack evolution from matrix deformation in shale using X-ray CT. Their study benchmarked 13 architectures and reported strong performance for Full-Resolution Residual Networks (FRRN-A and FRRN-B). The associated Mancos shale dataset includes CT image stacks and manual crack annotations under different saturation and imaging conditions.

This project will independently examine how segmentation performance changes when image acquisition or specimen conditions differ between training and evaluation data. It is an exploratory extension, not a claim that the published study failed to address these questions. The precise overlap with the original paper will be assessed after its full methods and supplementary information have been reviewed.

## Primary research question

How robust are baseline automated crack-segmentation methods when evaluated across changes in CT imaging conditions and shale saturation state?

## Planned work

1. Critically review the original paper, including all 13 architectures, training details, validation design and limitations.
2. Audit the public dataset, including specimen identity, image-stack structure, annotations, acquisition conditions and licence.
3. Establish specimen-aware data splits to avoid leakage between neighbouring slices from the same physical specimen.
4. Establish reproducible baseline segmentation and evaluation procedures.
5. Evaluate in-condition performance and, where the dataset supports it, cross-condition generalisation.
6. Report uncertainty, class imbalance, failure cases and limitations transparently.

## Dataset

Park, June-Ho; Kim, Jinwoo; Shim, Seungbo; Kwon, Tae-Hyuk (2026). *Mancos shale X-ray CT and manual annotation dataset*, Version 2. Mendeley Data. https://doi.org/10.17632/dkvhnmwkjg.2

The dataset is not included in this repository. Users should obtain it from Mendeley Data and follow its CC BY 4.0 terms, including attribution. Do not commit raw image stacks or annotations to this repository unless there is a clear, justified need and the licence and storage implications have been checked.

## Related publication

Park, J.H., Kim, J., Shim, S. and Kwon, T.H. (2026). Deep learning-based segmentation framework to decouple matrix deformation and crack evolution in shales using X-ray computed tomography. *International Journal of Rock Mechanics and Mining Sciences*, 202, 106489. https://doi.org/10.1016/j.ijrmms.2026.106489

## Reproducibility principles

- Keep raw data separate from code and derived outputs.
- Record software versions, random seeds, data splits and preprocessing choices.
- Split by independent specimen or CT stack, not randomly by adjacent slices.
- Report crack-class metrics as well as aggregate metrics.
- Distinguish reproduced findings from new exploratory analyses.
- Do not report results until they have been generated and checked.

## Licence

A repository licence will be added after the intended reuse of code and third-party materials has been settled. The dataset's CC BY 4.0 licence does not automatically apply to original code in this repository.
