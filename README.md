---
title: Customer dropout membership
researcher: Pedro Sobreiro
date: 30-07-2021
abstract: Prediction of customer dropout with contractual settings
bibliography: "references.bib"
---

# Customer dropout membership :technologist: :moneybag: :chart_with_upwards_trend:

Context:
An organization membership located in Portugal. The organization offers an annual membership
for the members, the service subscription has several payment options:

- Men with a annual fee of 10€
- Women annual fee of 6€
- Correspondent fee 6€
- Retired fee 5€
- Student fee 2.5€
- under-14 fee 1€

In this study, we adopted random survival forests that does not make the proportional hazards 
assumption [@Ehrlinger_2016] and has the flexibility to model survivor curves that are of 
dissimilar shapes for contrasting groups of subjects. 
Random Survival Forest is an extension of Random Forest allowing efficient non-parametric 
analysis of time to event data [@Breiman_2001].
This characteristics allow us to surpass the Cox Regression limitation of the proportional hazard
assumption, requiring to exclude variables which not fulfill the model assumption. 
It was shown by @Breiman_2001 that ensemble learning can be further improved by injecting 
randomization into the base learning process - a method called Random Forests.  
The random survival forest was developed using the package PySurvival [@Fotso_others_2019].
The most relevant variables predicting the dropout are analysed using the log-rank test. 
The metric variables are transformed to categorical using the quartiles to provide a statistical
comparison of groups. 
Was also used the package Lifelines [@Davidson-Pilon_2021] for the kaplan-meier analysis.

The article using above assumptions was developed in RMarkdown and is available in the 
folder [article](./article/) and published [here](https://www.mdpi.com/2079-9292/11/20/3328)

> Sobreiro, P.; Garcia-Alonso, J.; Martinho, D.; Berrocal, J. Hybrid Random Forest Survival Model to Predict Customer Membership Dropout. 
> Electronics 2022, 11, 3328. https://doi.org/10.3390/electronics11203328



# Packages installation

PySurvival is an open source python package for Survival Analysis modeling - the modeling concept used to analyze or predict when an event is likely to happen. It is built upon the most commonly used machine learning packages such NumPy, SciPy and PyTorch.
PySurvival is compatible with Python 2.7-3.7

```
# create environment with python 3.7
conda create --name survival python=3.7
# activate environment
conda activate survival
# package essentials
conda install -c conda-forge jupyter
conda install -c conda-forge jupyterlab
conda install -c conda-forge xlrd
conda install -c conda-forge openpyxl
conda install -c conda-forge lifelines
# install PySurvival dependencies
conda install -c conda-forge numpy
conda install -c conda-forge scipy
conda install -c conda-forge scikit-learn
conda install -c conda-forge pytorch

# install c++ dependencies
sudo apt install gcc-8 g++-8
# edit .bashrc or .zshrc according the terminal used then source
# e.g. source ~/.zshrc
export CXX=/usr/bin/g++-8
export CC=/usr/bin/gcc-8
# install pysurvival after dependencies are resolved by conda
pip install pysurvival
```

Windows installation requires some changes.
Followed this [link](https://github.com/square/pysurvival/issues/8).
Install visual studio build tools [here](https://aka.ms/buildtools)

![img](./figures/png_2142357625300655111.png)

```python
git clone https://github.com/bacalfa/pysurvival.git
python setup.py build_ext --inplace
python setup.py install --user
```

some problems with numpy: pip install numpy==1.19.3

```
@Misc{ pysurvival_cite,
  author = {Stephane Fotso and others},
  title = {{PySurvival}: Open source package for Survival Analysis modeling},
  year = {2019--},
  url = "https://www.pysurvival.io/"
}
```

# Installing in reticulate 


## Windows

There are some issues related to windows installation this tries to 
address that:

```python
conda_create(envname = "rsurvival",
             conda="C:/Users/sobre/AppData/Local/r-miniconda/Scripts/conda.exe",
             forge = TRUE, 
             channel = c("conda-forge","sebp"), 
             packages = c("pandas","seaborn","lifelines","scikit-survival"),
             python_version = "3.7.10")

then install pysurvival using conda environment

conda activate rsurvival

git clone https:/github.com/bacalfa/pysurvival.git
python setup.py build_ext --inplace
python setup.py install --user
```

```{python Py,eval=TRUE,echo=TRUE}
from pysurvival.utils.display import correlation_matrix
import pandas as pd

# some problems in linux need to add openpyxl to read excel file
df = pd.read_excel('../data/membershipData.xlsx',index_col=0,engine = 'openpyxl')

correlation_matrix(df, figure_size=(10,10), text_fontsize=8)
print('olá mundo')
```
