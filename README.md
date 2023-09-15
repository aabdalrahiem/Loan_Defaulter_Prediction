Loan Default Prediction
==============================

# **Business KPIs**

While machine learning projects are challenging and complex, it's always
advisable to start them by identifying the goal of the project and the
way it serves the business container in which it lives. One of the ways
is defining the business goals along with the Key Performance Indicators
(KPI).

![A diagram of data analysis Description automatically generated with
medium confidence](./image1.png){width="4.784027777777778in"
height="1.7083333333333333in"}

For a financial company, there are plenty of KPIs that can be utilized
for the purpose of measuring the company's performance. Here, we are
listing some of them (Most of them are related to loan applications):

1.  **Gross Profit Margin:** It measures the profitability of the
    company by quantifying the net income.

2.  **Average Cycle Time:** This KPI is used to optimize the loan
    process. It measures the average time needed from when a client
    applies an application until the loan/credit is approved.

3.  **Application Approval Rate:** This KPI measures the performance of
    the application process. It represents the number of approved
    applications compared to the total number of valid applications.

4.  **Profit Per Loan:** This KPI gives an intuition about how each loan
    comes with a benefit to the company. It measures the total profit
    compared to the number of Disbursed loans.

5.  **Incomplete Application Rate:** It gives an understanding of how
    good and easy the application process is. It measures the number of
    incomplete applications compared to the total number of processed
    applications.

6.  **Customer Acquisition Cost:** This KPI measures the cost of getting
    new customers to have approved loan applications. It compares the
    total costs spent on marketing to the total number of new customers.

# **Problem Statement**

> In order to achieve a high value in the predefined KPIs for the loan
> application process, we have to come up with a solution that can
> improve most of them.
>
> When the company receives a loan application, It has to decide either
> to approve the application or decline it. When a client defaults on
> paying his loan, this may introduce a decrease in the company\'s
> profit (KPI 1).
>
> The most valuable solution is to design a data-driven model that is
> able to identify if an applicant will repay his loan or will default.
> During the application process, if we can quickly classify if the
> client is a defaulter or a repair, this will optimize different
> aspects of the process (KPI 2:KPI 5).
>
> **This way, we will improve 5 KPIs out of the previously defined 6
> KPIs (KPIs A, B, C, D)!**
>
> ![A hand holding a pen and paper Description automatically
> generated](./image2.jpg){width="4.053245844269466in"
> height="1.8565693350831145in"}

# **Dataset**

## Data Description:

> As for most of the ML classification tasks, there should be labeled
> data for the model to be trained and tested on.
>
> The dataset was found on
> [[Kaggle]{.underline}](https://www.kaggle.com/datasets/gauravduttakiit/loan-defaulter?datasetId=807638&sortBy=voteCount&searchQuery=predi&select=columns_description.csv)
> and was proposed to apply exploratory data analysis on it and identify
> patterns of clients who apply to a lending company or a company that
> offers credit services.

The data is combined of three CSV files:

+-------------------+--------------------------------------------------+
| **CSV File**      | **Description**                                  |
+-------------------+--------------------------------------------------+
| app               | -   This file has data columns that contain      |
| lication_data.csv |     > information captured from the loan         |
|                   |     > application filled in with the client at   |
|                   |     > the time of applying for the loan/credit.  |
|                   |                                                  |
|                   | -   Every row is a unique loan application and   |
|                   |     > has a unique ID SK_ID_CURR.                |
|                   |                                                  |
|                   | -   One of the columns has the target variable   |
|                   |     > "TARGET" which contains a binary value. If |
|                   |     > the value is 1, it means that the client   |
|                   |     > was a defaulter; if the value is 0, he     |
|                   |     > repaid the loan.                           |
|                   |                                                  |
|                   | -   The data contains 307511 rows/applications   |
|                   |     > and 122 variables (including the target    |
|                   |     > variable).                                 |
|                   |                                                  |
|                   | -   The data contains mixed variable types       |
|                   |     > (categorical and continuous types).        |
|                   |                                                  |
|                   | -   Some of the categorical variables in the     |
|                   |     > data are multi-class.                      |
+-------------------+--------------------------------------------------+
| previous_data.csv | -   This file contains data of previous          |
|                   |     > applications for clients who have IDs in   |
|                   |     > the application_data file.                 |
|                   |                                                  |
|                   | -   Every row is a unique loan application and   |
|                   |     > has a unique ID SK_ID_PREV.                |
|                   |                                                  |
|                   | -   Each current loan application in the         |
|                   |     > application_data file may have **more      |
|                   |     > than** one previous application for the    |
|                   |     > same client.                               |
|                   |                                                  |
|                   | -   Each current loan application in the         |
|                   |     > application_data file may have **no**      |
|                   |     > previous application for the same client.  |
|                   |                                                  |
|                   | -   Columns (variables) in previous applications |
|                   |     > are not identical to those in the          |
|                   |     > application data.                          |
|                   |                                                  |
|                   | -   The data contains 1670214 rows/applications  |
|                   |     > and 37 variables (including the target     |
|                   |     > variable).                                 |
+-------------------+--------------------------------------------------+
| column            | This file contains a description for each        |
| s_description.csv | column/variable in both the application data and |
|                   | previous data.                                   |
+-------------------+--------------------------------------------------+


Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
