# Predict Customer Churn
- Project predicts customer churn for banking customer

## Project descritpion
The project aims at predicting customer churn for banking customers. This is a classification problem. This project uses following approach:

- Load and explore the dataset composed of over 10k samples (EDA - Exploratory data analysis)
- Prepare data for training (feature engineering resulting into 19 features)
- Train two classification models (sklearn random forest and logistic regression) - Random forest has better performance than logistic regression in this case
- Identify most important features influencing the predictions and visualize their impact using SHAP library
- Save best models with their performance metrics
- Use autopep8 module to format the code according to PEP8 standard
- Use pylint linter to improve quality of the code


## Intended project structure for a complete MLOps project
- README.md                  # Project documentation
- data/                      # Data directory
  - raw/                     # Raw data
  - processed/               # Processed data
  - external/                # External data (optional)
- models/                    # Model artifacts and related files
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

## Files and data description
#### Overview of the files and data present in the root directory
The project is organized with the following directory architecture within src folder:
- Folders
    - Data      
        - eda       --> contains output of the data exploration
        - results   --> contains the dataset in csv format
    - images        --> contains model scores, confusion matrix, ROC curve
    - models        --> contains saved models in .pkl format
    - logs          --> log generated druing testing of churn_library.py file

- project files 
    - churn_library.py
    - churn_notebook.ipnyb
    - requirements.txt

- pytest files (unit test file and configuration files)
    - pytest.ini
    - test_churn_with_logging.py

## How to run the project
- The project can be executed with python 3.8 or 3.9 and the appropriate python packages specified in requirements.txt
- Open the project inside vscode devcontainer and install all the dependencies `pip install -r src/requirements.txt`
- To run the project, execute the script `python churn_library.py` from the src folder
- Alternatively, the project can be executed using the jupyter notebook(churn_notebook.ipynb) for a step-by-step approach
- The project script `churn_library.py` has been tested using pytest python package
    - To run the unit tests, simply type `pytest` from the main src folder in the command line
    - Project functions will be automatically tested with log file generated in the logs folder
- Use following command to format/refactor the code using PEP8 style guide line
    autopep8 --in-place --aggressive --aggressive test_churn_with_logging.py
    autopep8 --in-place --aggressive --aggressive churn_library.py
- Use following command for style checking and error spotting
    pylint churn_library.py
    pylint test_churn_with_logging.py
    
## Details of important files
#### devcontainer: 
To run the project on localhost, we have used vscode devcontainer technology which will use Dockerfile to run the project.
Intention behind using devcontainer is to provide separate docker based container environment. All the dependency package installations will happen within the container and will not interfere with host computer installations.

#### churn_library.py:
The churn_library.py is a library of functions to find customers who are likely to churn. All the important functions such as exploratory data analysis function(perform_eda), feature engineering function(perform_feature_engineering), model training function(train_models), confusion matrix function etc resides in chrun_library.py. These functions are are used in notebook and unit tests files. In order to test the code independently, we have used  __name__ == "__main__" block that allows us to run the code  and understand the results for each of the functions and refactor code associated with the original notebook.

we can use command ipython churn_library.py, to run the code below  __name__ == "__main__" block

#### test_churn_with_logging.py:
It Contain unit tests for the churn_library.py functions. Used assert statements to test functions and make sure it work properly. Testing and logging can be completed on the command line i.e running the below code in the terminal should test each of the functions and provide any errors to a file stored in the /logs folder.

pytest churn_script_logging_and_tests.py

## Additional setup
#### CICD pipeline:
- It includes github actions pipeline to deploy the project
    - config        --> prepares and exports environment variables that can be used in different jobs
    - build        --> steps required to build the project can be performed in this job, eg. compile, generate minified files etc
    - test        --> steps to test the project can be performed in this job eg. pylint and pytest activites
    - deploy          --> steps required to deploy project on multiple environments(test, staging, production etc) can be performed in this job
    - announcement          --> once deployement is successfull on production, we can notify people on certain notification channels eg. slack or jira or email

#### Pull request template:
- It helps developers to create great pull request descriptions that meets the organization's standards
- pull_request_template.md contains a template which is used whenever new pull requirest is created and developers should
fill in the details before asking anyone for the code review

#### Pre-commit hook:
- .pre-commit-config.yaml includes what should happen before a successfull commit