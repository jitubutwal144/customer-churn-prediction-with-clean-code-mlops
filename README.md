### Intended project structure
- README.md                  # Project documentation
- data/                      # Data directory
  - raw/                     # Raw data
  - processed/               # Processed data
  - external/                # External data (optional)
- models/                    # Model artifacts and related files
- notebooks/                 # Jupyter notebooks for exploration and experimentation
- src/                       # Source code directory
  - data/                    # Data-related code
    - preprocessing/         # Data preprocessing scripts and modules
    - validation/            # Data validation scripts and modules
  - models/                  # Model-related code
    - training/              # Model training scripts and modules
    - evaluation/            # Model evaluation scripts and modules
    - serving/               # Model serving scripts and modules
  - infrastructure/          # Infrastructure-related code
    - deployment/            # Deployment scripts and modules
    - monitoring/            # Monitoring scripts and modules
- tests/                     # Unit tests and integration tests
- config/                    # Configuration files
- pipelines/                 # MLOps pipelines (e.g., CI/CD, data pipelines)
- docs/                      # Additional project documentation (e.g., architecture, design)
- scripts/                   # Miscellaneous scripts (e.g., data download, setup)


### Overview
- devcontainer
To run the project on localhost, we have used vscode devcontainer technology which will use Dockerfile to run the project.
Intention behind using devcontainer is to provide separate docker based container environment. All the dependency package installations will happen within the container and will not interfere with host computer installations.

- churn_library.py
The churn_library.py is a library of functions to find customers who are likely to churn. All the important functions such as exploratory data analysis function(perform_eda), feature engineering function(perform_feature_engineering), model training function(train_models), confusion matrix function etc resides in chrun_library.py. These functions are are used in notebook and unit tests files.

In order to test the code independently, we have used  __name__ == "__main__" block that allows us to run the code  and understand the results for each of the functions and refactor code associated with the original notebook.

we can use command ipython churn_library.py, to run the code below  __name__ == "__main__" block

- test_churn_with_logging.py
It Contain unit tests for the churn_library.py functions. Used assert statements to test functions and make sure it work properly. 

Testing and logging can be completed on the command line i.e running the below code in the terminal should test each of the functions and provide any errors to a file stored in the /logs folder.

ipython churn_script_logging_and_tests.py