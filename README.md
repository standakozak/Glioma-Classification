# IDH mutation status classification in Grade IV Gliomas

This repository accompanies the seminary paper **IDH mutation status classification in Grade IV Gliomas** written by Stanislav Kozák for Seminar Artificial Intelligence for Medicine (summer semester 2024) at University of Applied Sciences Ingolstadt. The seminary paper is included in the repository files.

It contains own attempt to reproduce results of three studies classifying Grade IV Gliomas (Glioblastoma, IDH-wildtype and Astrocytoma, IDH-mutant) based solely on MRI images and radiomic features.

The code uses dataset presented in Calabrese et al. (2022) which is [publicly available](https://www.cancerimagingarchive.net/collection/ucsf-pdgm).


## Repository Structure
The repository includes Jupyter Notebooks for loading, visualising and preprocessing the data (directory `Dataset handling`), radiomic feature extraction with PyRadiomics (`feature_extraction.ipynb`) and glioma classification with scikit-learn (`classifier.ipynb`).

The [dataset itself](https://www.cancerimagingarchive.net/collection/ucsf-pdgm) is not a part of the repository. However, `classifier.ipynb` can be run without the data as it uses extracted features in `radiomic_features.csv`.

## Dataset and Feature Extraction
Because of limited memory, 60 patients were randomly selected from the dataset. 30 of them had glioblastoma and 30 had astrocytoma.

For each patient, each combination of a sequence (selected from *_T1c_bias, _DWI_bias, _ADC, _DTI_eddy_MD*) and segmentation (*_tumor_segmentation, _brain_segmentation*) were used for the feature extraction.

The extraction was done by PyRadiomics 3.0.1, extracting all 107 supported features for each combination, using default settings and no applied filters. This results in 856 extracted features for each patient.

## ML Models and Feature Selection
TBD

## Evaluation
TBD


## References
Calabrese, E., Villanueva-Meyer, J., Rudie, J., Rauschecker, A., Baid, U., Bakas, S., Cha, S., Mongan, J. & Hess, C. (2022), ‘The University of California San Francisco Preoperative Diffuse Glioma MRI (UCSF-PDGM)(Version 4) [Dataset]’.