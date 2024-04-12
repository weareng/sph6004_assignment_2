# sph6004_assignment_2

Organisation of directories:  

1. data: contains all csv files 
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
2. data_preprocess: notebooks that helps to preprocess the data 
    1. static_dynamic_preprocess.ipynb 
        1. Preprocess static.csv and dynamic.csv into static_dynamic.csv 
    2. notes_combined.ipynb, notes_embedded.ipynb 
        1. Preprocess notes.csv into notes_combined.csv and notes_embedded.csv 
    3. dataset_preprocess.ipynb 
        1. Creates dataset.csv 
        2. Splits dataset.csv into train_test.csv and validation.csv by patient IDs 
    4. static_dynamic_models: notebooks that contain models that use static_dynamic features for prediction of death and LOS 
    5. notes_models: notebooks that contain models that use notes features for prediction of death and LOS 
    6. ensemble_models: notebook that contain model that combines the output of both static_dynamic_best_model and notes_best_model in prediction of death and LOS 
