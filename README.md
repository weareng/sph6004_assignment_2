# sph6004_assignment_2

Welcome to Group 3 SPH6004 Assignment 2 Repository!

This repository will contain all our code and models used to predict length of stay. Due to the size of the datasets, they are not uploaded in github, but are stored in our `/Team 3/code/data/` directory. 

In this repository, our files are stored in the following format:

**Organisation of directories**:  
1. data: contains all csv files, stored in `/Team 3/code/data/` directory.
    1. Original files: static.csv, dynamic.csv, notes.csv 
    2. static_dynamic.csv:  
        1. Merger of static.csv and dynamic.csv
    3. notes.csv -> notes_combined.csv 
        1. Remove irrelevant or inconsistent notes 
        2. Combine all notes of a single patient into a single input arranged in time series 
    4. notes_combined.csv -> notes_embedded.csv 
        1. Mahbub method of BioClinicalBERT transformer to tokenise and convert free text notes into a single vector  
    5. dataset.csv  
        1. Entire dataset (not to be used), created by merger of static_dynamic.csv and notes_embedded.csv 
    6. train_test.csv 
        1. 80% of dataset.csv to be used for model training and testing for death prediction and LOS 
    7. validation.csv 
        1. 20% of dataset.csv to be used for final step of validation
    8. `{prediction task}_probability_{model}_{dataset}.csv`
        1. Datasets that we created and used during training and validation of our models
        2. `{prediction task}`: death or los
        3. `{model}`:
           1. `sd_{name}` for models trained on static_dynamic features (e.g. `sd_lstm`)
           2. `n_{name}` for models trained on notes features (e.g. `n_logreg`)
        4. `{dataset}`: traintest or validation
        5. e.g. `sph6004_assignment_2/data/los_probability_sd_lstm_traintest.csv`           
2. data_preprocess: notebooks that helps to preprocess the data 
    1. static_dynamic_preprocess.ipynb 
        1. Preprocessed static.csv and dynamic.csv into static_dynamic.csv 
    2. notes_combined.ipynb, notes_embedded.ipynb 
        1. Preprocessed notes.csv into notes_combined.csv and notes_embedded.csv 
    3. dataset_preprocess.ipynb 
        1. Used to create dataset.csv 
        2. Splits dataset.csv into train_test.csv and validation.csv
3. static_dynamic_models:
    1. Contain models that use static_dynamic features for prediction of death and LOS
    2. Subdirectories are named by the type of models used
        1. e.g. lstm, tcn
        2. `sd_{name}_{prediction task}_{dataset}.ipynb` is the name of the models stored in each subdirectory
            1. `{name}`: name of model, e.g. tcn, lstm
            2. `{prediction task}`: e.g. death, los
            3. `{dataset}`: e.g. traintest, validation
        4. e.g. `sph6004_assignment_2/static_dynamic_models/tcn/sd_tcn_los_validation.ipynb`
        5. `sd_{name}_{prediction task}.keras` is the name of the trained model
4. notes_models:
    1. Contain models that use notes features for prediction of death and LOS
    2. `n_{name}_{prediction task}_{dataset}.ipynb`
        1. `{name}`: name of model, e.g logreg
        2. `{prediction task}`: e.g. death, los
        3. `{dataset}`: e.g. traintest, validation
   3. e.g. `sph6004_assignment_2/notes_models/n_logreg_death_traintest.ipynb`
   4. `n_{name}_{prediction task}.pkl` is the name of the trained model
5. ensemble_models:
    1. Contain models that combines the output of both `sd_{best model name}_{prediction task}_{dataset}.ipynb` and `n_{best model name}_{prediction task}_{dataset}.ipynb` in prediction of death and LOS
    2. `ensb_{name}_{prediction task}_{dataset}.ipynb`
        1. `{name}`: name of ensemble model, e.g. logreg, gnb
        2. `{prediction task}`: e.g. death, los
        3. `{dataset}`: e.g. traintest, validation
    3. e.g. `sph6004_assignment_2/ensemble_models/ensb_logreg_los_validation.ipynb` 
