# Capstone_Project_ML
## Application Screening for DonorChoose.org


## Table of Contents
- [Project Overview](#project-overview)
- [Project Highlights](#project-highlights)
- [Install](#install)
- [Code](#code)
- [Run](#run)
- [Data](#data)


### <a name="project-overview"></a>Project Overview

Founded in 2000 by a high school teacher in the Bronx, DonorsChoose.org empowers public school teachers from across the country to request much-needed materials and experiences for their students. At any given time, there are thousands of classroom requests that can be brought to life with a gift of any amount.

DonorsChoose.org receives hundreds of thousands of project proposals each year for classroom projects in need of funding. Right now, a large number of volunteers is needed to manually screen each submission before it's approved to be posted on the DonorsChoose.org website.

Next year, DonorsChoose.org expects to receive close to 500,000 project proposals. As a result, there are three main problems they need to solve:

How to scale current manual processes and resources to screen 500,000 projects so that they can be posted as quickly and as efficiently as possible

How to increase the consistency of project vetting across different volunteers to improve the experience for teachers

How to focus volunteer time on the applications that need the most assistance

The goal of the competition is to predict whether or not a DonorsChoose.org project proposal submitted by a teacher will be approved, using the text of project descriptions as well as additional metadata about the project, teacher, and school. DonorsChoose.org can then use this information to identify projects most likely to need further review before approval.

With an algorithm to pre-screen applications, DonorsChoose.org can auto-approve some applications quickly so that volunteers can spend their time on more nuanced and detailed project ​vetting processes, including doing more to help teachers develop projects that qualify for specific funding opportunities.

Your machine learning algorithm can help more teachers get funded more quickly, and with less cost to DonorsChoose.org, allowing them to channel even more funding directly to classrooms across the country.


### <a name="project-highlights"></a>Project Highlights

This project is an attempt to solving the Donor Choose Application Screening Competition with decision trees algorithms like Light GBM and XGBoost. 

Things learned and accomplished by completing this project: 

- How to load datasets from files.
- How to perform EDA.
- How to engineer features.
- How to choose a right algorithm.
- How to built a classification model.



### <a name="install"></a>Install

This project requires **Python 2.7** and the following Python libraries installed:

- [NumPy](http://www.numpy.org/)
- [Pandas](http://pandas.pydata.org)
- [matplotlib](http://matplotlib.org/)
- [Seaborn](https://stanford.edu/~mwaskom/software/seaborn/)
- [scikit-learn](http://scikit-learn.org/stable/)
- [XGBoost](https://xgboost.readthedocs.io/en/latest/)

You will also need to have software installed to run and execute a [Jupyter Notebook](http://jupyter.org/)

[Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 


### <a name="code"></a>Code

Data Processing code is provided in the Jupyter notebook `data_processing.ipynb`. Data Analysis and Model Building code is provided in the Jupyter notebook `model_building.ipynb`. 


### <a name="run"></a>Run

In a terminal or command window, navigate to the top-level project directory then move to `/code/` directory and run the following command:

```jupyter notebook data_processing.ipynb```
and
```jupyter notebook model_building.ipynb```

This will open the Jupyter Notebook software and two code files in your browser.


### <a name="data"></a>Data


The competition dataset contains information from teachers' project applications to DonorsChoose.org including teacher attributes, school attributes, and the project proposals including application essays. Your objective is to predict whether or not a DonorsChoose.org project proposal submitted by a teacher will be approved.

File descriptions
- train.csv - the training set
- test.csv - the test set
- resources.csv - resources requested by each proposal; joins with test.csv and train.csv on id
- sample_submission.csv - a sample submission file in the correct format

Data fields
test.csv and train.csv:

- id - unique id of the project application
- teacher_id - id of the teacher submitting the application
- teacher_prefix - title of the teacher's name (Ms., Mr., etc.)
- school_state - US state of the teacher's school
- project_submitted_datetime - application submission timestamp
- project_grade_category - school grade levels (PreK-2, 3-5, 6-8, and 9-12)
- project_subject_categories - category of the project (e.g., "Music & The Arts")
- project_subject_subcategories - sub-category of the project (e.g., "Visual Arts")
- project_title - title of the project
- project_essay_1 - first essay*
- project_essay_2 - second essay*
- project_essay_3 - third essay*
- project_essay_4 - fourth essay*
- project_resource_summary - summary of the resources needed for the project
- teacher_number_of_previously_posted_projects - number of previously posted applications by the submitting teacher
- project_is_approved - whether DonorsChoose proposal was accepted (0="rejected", 1="accepted"); train.csv only

Note: Prior to May 17, 2016, the prompts for the essays were as follows:

- project_essay_1: "Introduce us to your classroom"
- project_essay_2: "Tell us more about your students"
- project_essay_3: "Describe how your students will use the materials you're requesting"
- project_essay_4: "Close by sharing why your project will make a difference"

Starting on May 17, 2016, the number of essays was reduced from 4 to 2, and the prompts for the first 2 essays were changed to the following:

- project_essay_1: "Describe your students: What makes your students special? Specific details about their background, your neighborhood, and your school are all helpful."
- project_essay_2: "About your project: How will these materials make a difference in your students' learning and improve their school lives?"

For all projects with project_submitted_datetime of 2016-05-17 and later, the values of project_essay_3 and project_essay_4 will be NaN.

resources.csv:

Proposals also include resources requested. Each project may include multiple requested resources. Each row in resources.csv corresponds to a resource, so multiple rows may tie to the same project by id.

- id - unique id of the project application; joins with test.csv. and train.csv on id
- description - description of the resource requested
- quantity - quantity of resource requested
- price - price of resource requested
