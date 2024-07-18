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
Classification models with multiple configurations were trained on the data with repeated 3-Fold Cross Validation. For each model split, the features were normalised by StandardScaler and the most important features were selected through RFECV (using the classifier itself to find the feature importance). The trained models include logistic regression, support vector machines with linear kernel, random forest classifier.


## Evaluation
From the current experiments, logistic regression and support vector machines got moderately good results (MCC 0.486 for logistic regression and 0.464 for SVM). However, those results were achieved with 140 features and after fine-tuning iterations. It is therefore possible, that the results overfitted on the dataset.

Further experiments with more datapoints (> 50 per class) are needed to confirm the mentioned results.


## References
Calabrese, E., Villanueva-Meyer, J., Rudie, J., Rauschecker, A., Baid, U., Bakas, S., Cha, S., Mongan, J. & Hess, C. (2022), ‘The University of California San Francisco Preoperative Diffuse Glioma MRI (UCSF-PDGM)(Version 4) [Dataset]’.