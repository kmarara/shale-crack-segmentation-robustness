# Dataset documentation

## Source

Park, June-Ho; Kim, Jinwoo; Shim, Seungbo; Kwon, Tae-Hyuk (2026). *Mancos shale X-ray CT and manual annotation dataset*, Version 2. Mendeley Data. DOI: https://doi.org/10.17632/dkvhnmwkjg.2

Dataset landing page: https://data.mendeley.com/datasets/dkvhnmwkjg/2

## Confirmed from the public record

The Version 2 record states that the dataset contains:

- X-ray computed tomography images of Mancos shale specimens;
- raw CT image stacks;
- corresponding manual annotations of crack regions;
- saturation states described as as-received, saturated and oven-dried;
- imaging conditions described as 100 kV, 150 kV and imaging with an aluminium ring.

The listed licence is Creative Commons Attribution 4.0 International (CC BY 4.0). Cite the dataset and provide appropriate attribution when reusing material. Check the landing page and any accompanying files for attribution wording and third-party restrictions before redistributing any data.

## Not yet verified

The following details require inspection of the actual downloaded files and metadata:

- exact file and folder names;
- number of specimens, stacks and slices;
- which conditions are paired or repeated on the same specimen;
- image dimensions, bit depth, voxel size and pixel spacing;
- image formats and compression;
- annotation file format and class values;
- whether masks are one-to-one aligned with raw slices;
- whether annotations cover every slice or only selected slices;
- any acquisition metadata, calibration information or readme files;
- whether the Version 2 files differ from Version 1 beyond publication timing or metadata.

Do not infer these details from the abstract or dataset summary.

## Planned audit outputs

After downloading and inspecting the dataset, populate:

1. A file inventory with relative paths, sizes and file types.
2. A specimen and scan manifest.
3. An imaging-condition table.
4. An annotation-format description with example visualisations.
5. A data-integrity report covering missing files, shape mismatches and mask alignment.
6. A citation and licence note.

## Data handling

Do not upload raw CT stacks or annotation files to this repository by default. Keep local copies in a separate data directory excluded from version control. The repository should contain scripts, documentation and small derived outputs only when appropriate.
