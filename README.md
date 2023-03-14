
# Regression in 6 steps

This is a 6 step/ notebook process used to explore, predict and evaluate regression based problems. The links and code are focused on Kaggle competitions but can be reused for any regression based problem

1. [EDA ](https://www.kaggle.com/code/slythe/pse3e9-1-eda-model-selection-regression) 
2. [Feature Creation ](https://www.kaggle.com/code/slythe/pse3e9-2-feature-creation-symbolic-transform)
3. [Feature Selection ](https://www.kaggle.com/code/slythe/ps3e9-3-feature-selection-regression)(RFECV and manual selection) 
4. [Single Model Tuning](https://www.kaggle.com/code/slythe/pss3e9-4-single-model-tuning-regression/notebook)
5. [Multi Model CV ](https://www.kaggle.com/code/slythe/pse3e9-5-2-multi-model-cv-all-folds-regression/notebook)  / [Multi Model : best fold ](https://www.kaggle.com/code/slythe/pss3e9-5-1-multi-model-cv-best-fold-regression/notebook)
6.  [Ensembling](https://www.kaggle.com/code/slythe/pss3e09-6-ensembling-regression/notebook)




## Code breakdown


* The first and foremost is an investigation of the data, as this gives insights into the data without being influence by others
* **Step 2** is a separate notebook just for **feature creation**, I use a number of automated and intuitive processes here. My favorite is [Symbolic Regression Transformation](https://gplearn.readthedocs.io/en/stable/index.html) which tries to apply mathematical operations to the features that explain the target. Very interesting but it actually didn't work that well this episode (it did well in episode 5) 
* **Step 3** is a feature selection notebook where I take all the features created in step 2 and run recursive feature elimination on them (manually and automatically using [sklearn's REFCV](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.RFECV.html))
* **Step 4** is self explanatory, I added the features created previously and try optimize the model. I dont like Optuna as it tends to overfit and try do this manually.
* **Step 5** I take every Tuned model and run a nested CV as well as best-in-fold CV. Similar to step 4 just with many models. 
    
    **Note:** I try to save all the validation predictions and test predictions for later use. Also optimizing the validation predictions give a good indication of the models performance (NB dont use the training predictions for this --although I have to for [Multi Model : best fold ](https://www.kaggle.com/code/slythe/pss3e9-5-1-multi-model-cv-best-fold-regression/notebook)
* **Step 6** is to apply ensembling techniques to the outputs from all the above test and validation predictions. Scipy Optimize seems to do very well here as well as calibration using linear models 

