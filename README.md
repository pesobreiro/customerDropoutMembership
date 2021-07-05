# Customer dropout membership

Context:
An organization membership located in portugal. The organization offers an annual membership
for the members, the service subscription has several payment options:

- Men with a annual fee of 10€
- Women annual fee of 6€
- Correspondent fee 6€
- Retired fee 5€
- Student fee 2.5€
- under-14 fee 1€

# Methodology

In this study, we adopt random survival forests which have never been used in understanding 
factors affecting membership in a sport club using existing data in a Sport Club. 
The analysis is based on the use of random survival forests in the presence of covariates 
that do not necessarily satisfy the PH assumption. 
Random Survival Forests does not make the proportional hazards assumption (Ehrlinger, 2016) 
and has the flexibility to model survivor curves that are of dissimilar shapes for 
contrastinggroups of subjects. Random Survival Forest is an extension of Random Forest 
allowing efficient non-parametric analysis of time to event data (Breiman, 2001). 
This characteristcs allow us to surpass the Cox Regression limitation of the proportional hazard
assumption, requiring to exclude variables which not fullfill the model assumption. 
It was shown by (Breiman, 2001) that ensemble learning can be further improved by injecting 
randomization into the base learning process - a method called Random Forests.  
The random survival forest was developed using the package PySurvival (Fotso & Others, 2019)
The most relevant variables predicting the dropout are analysed using the log-rank test. 
The metric variables are transformed to categorical using the quartiles to provide a statistical
comparison of groups. 
The survival analysis was conducted using the package Lifelines (Davidson-Pilon et al., 2017).

# Packages instalation

```

# create environment
conda create --name survival
# activate environment
conda activate survival
# package essentials
conda install -c conda-forge jupyter
conda install -c conda-forge jupyterlab
conda install -c conda-forge xlrd
conda install -c conda-forge openpyxl
conda install -c conda-forge lifelines
# install PySurvival
# install c++ dependencies
sudo apt install gcc-8 g++-8
# edit .bashrc or .zshrc according the terminal used then source
# e.g. source ~/.zshrc
export CXX=/usr/bin/g++-8
export CC=/usr/bin/gcc-8
# install pysurvival
pip install pysurvival


jupyter lab --no-browser

```

```

@Misc{ pysurvival_cite,
  author = {Stephane Fotso and others},
  title = {{PySurvival}: Open source package for Survival Analysis modeling},
  year = {2019--},
  url = "https://www.pysurvival.io/"
}

```

# Artigo ascarza


Ascarza, E. (2018). Retention Futility: Targeting High-Risk Customers Might be Ineffective. Journal of Marketing Research, 55(1), 80-98. sim. https://doi.org/10.1509/jmr.16.0163


Example of  Developed actions: 

```
Each month, the company identified the customers who were up for renewal and
split them (randomly and evenly) between a treatment group that received a "thank you" gift
with the letter and a control group that received only the renewal latter.
````

# Aspects to consider 

    - Interpretability from RQ2
    - The business objective is to increase the number of members and organization profits
    - piping several algorithms to improve accuracy. Aka hybrid approach
    -  
