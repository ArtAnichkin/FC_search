# MACHINE SEARCH AND ANALYSIS OF ZOLEDRONIC ACID ANALOGUES WITH HIGH CYTOTOXICITY 

Bisphosphonate compounds are common concomitant medications used in the treatment of many types of cancer that metastasize to the bone. At the moment, one of the main compounds of this class is zoledronic acid, which preserves bone mineral density by suppressing the activity of osteoclasts


This work is devoted to a machine search for analogues of zoledronic acid with a similar effect on osteoclasts, as well as those with their own high activity against cancer cells.

Our repository contains notebooks and Python models that can predict the toxicity of compounds towards osteoclast FPPS protein and cancer cell lines PC3, MCF7, and also generate new compounds with high activity towards all 3 targets.
<p align="center">
  <img src="https://github.com/ArtAnichkin/FC_search/assets/94009755/11aad50b-9201-4681-8183-b81d905e6a02" />
</p>

## Preparation of data

Data were obtained from the open [ChEMBL](https://www.ebi.ac.uk/chembl/) database. The three datasets include: smiles molecule description, IC50 to FPPS/MCF7/PC3 cell line or protein. The data were cleaned, the IC50 of compounds from different measurement methods was averaged, and duplicates were removed.

Our models were trained on classical chemical descriptors, such as: Morgan Fingerprints, MACCS Fingerprints and other, prepared by [RDKIT](https://www.rdkit.org/) and descriptors prepared by [Mordred](https://github.com/mordred-descriptor/mordred?tab=BSD-3-Clause-1-ov-file#readme). All structures from the dataset corresponding to the FPPS protein were additionally optimized by the [GFN2-xTB](https://xtb-docs.readthedocs.io/en/latest/) functional to calculate charges to clarify the influence of the physics of some fragments on IC50 according to the [paper](https://chemistry-europe.onlinelibrary.wiley.com/doi/10.1002/cmdc.200500059). We publish all prepared datasets in a repository (named it).


## Selection of descriptors and models 

We evaluated the most popular classical machine learning methods (Support Vector Regression, Decision Trees, Gradient Boostin et al) using a combination of chemical descriptors for prediction.

The images below shows the correlations and importance of features estimated using permutation for the final models, which is the best result we were able to get using [Optuna](https://arxiv.org/abs/1907.10902) on [SVR](https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVR.html#sklearn.svm.SVR) regressor models.

<p align="center">
  <img src="https://github.com/ArtAnichkin/FC_search/assets/94009755/6b60ab79-0199-42a4-a24d-ea12fb64925c" />
</p>

## Generation model and samples

For generation, we used a [genetic algorithm](https://pubs.rsc.org/en/content/articlelanding/2021/sc/d1sc00231g), to the basic estimators IC50 of which an additional large cycle estimator and a synthetic availability estimator were added. Examples of generated connections and metrics are in the image below.

<p align="center">
  <img src="https://github.com/ArtAnichkin/FC_search/assets/94009755/f4922122-875f-4334-81dd-a9584869cc57" />
</p>

## How repository work

Datasets and trained models are available at [Google Drive](https://drive.google.com/drive/folders/1WtDQLZIx_Zwt6z04H2ji3JKgEYXwAWhX?usp=sharing)

For data preparation you should run notebook from `/notebooks/preparing_datasets.ipnb` or load data. Path for input files load from corresponding folders in [Google Drive](https://drive.google.com/drive/folders/1WtDQLZIx_Zwt6z04H2ji3JKgEYXwAWhX?usp=sharing).

To get trained models you should run notebook from `/notebooks/fitting_models.ipynb` or load trained models. Path for input files load from corresponding folders in [Google Drive](https://drive.google.com/drive/folders/1WtDQLZIx_Zwt6z04H2ji3JKgEYXwAWhX?usp=sharing). 

To get predictions you should run notebook from `/notebooks/prediction.ipnb`. Path for input file load from corresponding folders in [Google Drive](https://drive.google.com/drive/folders/1WtDQLZIx_Zwt6z04H2ji3JKgEYXwAWhX?usp=sharing).

To get generated structures you should run notebook from `/notebooks/generation.ipnb`. Path for input file load from corresponding folders in [Google Drive](https://drive.google.com/drive/folders/1WtDQLZIx_Zwt6z04H2ji3JKgEYXwAWhX?usp=sharing).

The enviroment for run notebooks locally download `Dockerfile` from `/enviroment` folder.
        
## Acknowledgements

**Work is greatly supported by Non-commercial Foundation for the Advancement of Science and Education INTELLECT**
