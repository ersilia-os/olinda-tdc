# olinda-tdc
This repository contains the benchmarking of Olinda v1 using the [Therapeutics Data Commons Datasets](https://tdcommons.ai/)

## Olinda
[Olinda](https://github.com/ersilia-os/olinda) is an automated model distillation pipeline for ML-based (Q)SAR models, currently specific to ZairaChem models.

In short, to use ZairaChem and then distill a model:
```
git clone https://github.com/ersilia-os/zaira-chem.git
cd zaira-chem
bash install_script.sh
```

Model training and prediction:
```
conda activate zairachem
zairachem fit -i <train_data.csv> -m <model_folder>
zairachem predict -i <test_data.csv> -m <model_folder> -o <pred_folder>
zairachem distill -m <model_folder> -o <distilled_model_path>
```

## Classification tasks
We have benchmarked Olinda models against the corresponding ZairaChem models in the [ADMET TDC Leaderboard](https://tdcommons.ai/benchmark/admet_group/overview/). At this stage we have focused only on classification tasks. 

The admet_classifications notebook shows the code to reproduce the model training and evaluation. For simplicity, the automated reports and raw data of the 5-fold evaluations are provided in the /predictions folder.

### Results
| assay                          |   zaira-chem auroc |   zaira-chem stdev |   olinda auroc |   olinda stdev |   delta |   perc_performance |
|:-------------------------------|-------------------:|-------------------:|---------------:|---------------:|--------:|-------------------:|
| Bioavailability_Ma             |              0.693 |              0.009 |          0.676 |          0.022 |  -0.017 |               0.98 |
| HIA_Hou                        |              0.99  |              0.004 |          0.888 |          0.194 |  -0.102 |               0.9  |
| Pgp_Broccatelli                |              0.941 |              0.005 |          0.936 |          0.006 |  -0.005 |               0.99 |
| BBB_Martins                    |              0.921 |              0.007 |          0.899 |          0.009 |  -0.022 |               0.98 |
| CYP2C9_Veith                   |              0.779 |              0.005 |          0.744 |          0.006 |  -0.035 |               0.96 |
| CYP2D6_Veith                   |              0.707 |              0.01  |          0.652 |          0.012 |  -0.055 |               0.92 |
| CYP3A4_Veith                   |              0.858 |              0.007 |          0.846 |          0.003 |  -0.012 |               0.99 |
| CYP2C9_Substrate_CarbonMangels |              0.42  |              0.011 |          0.415 |          0.019 |  -0.005 |               0.99 |
| CYP2D6_Substrate_CarbonMangels |              0.719 |              0.023 |          0.693 |          0.022 |  -0.026 |               0.96 |
| CYP3A4_Substrate_CarbonMangels |              0.633 |              0.01  |          0.615 |          0.01  |  -0.018 |               0.97 |
| hERG                           |              0.861 |              0.005 |          0.843 |          0.021 |  -0.018 |               0.98 |
| AMES                           |              0.853 |              0.005 |          0.823 |          0.005 |  -0.03  |               0.96 |
| DILI                           |              0.933 |              0.012 |          0.914 |          0.023 |  -0.019 |               0.98 |


# About us
The [Ersilia Open Source Initiative](https://ersilia.io) is a Non Profit Organization with the mission is to equip labs, universities and clinics in LMIC with AI/ML tools for infectious disease research.

[Help us](https://ersilia.io/donate) achieve our mission!
