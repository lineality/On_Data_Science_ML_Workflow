Readme On_Data_Science_ML_Workflow

# On Data Science Machine Learning Workflow

https://docs.google.com/document/d/1Ib_CNXrukZ29A5fVodpH2xaUfOmjjhzK6eesmxjuDsg/

(a rough document, but hopefully a useful starting template, over-simplifying and generalizing across many types of projects)

Analysis Workflow Template v2.1 (Data Science in Python)
In the interest of moving towards a discussion of best practice workflow for analyzing data:

This is a general model, but each project will vary. Sometimes you will start knowing almost everything: task topic, goal target, data, models, etc. Sometimes you may know just the topic, or have just a dataset, or just a target and have to make or discover everything else. Or if you run R&D, you may start with nothing at all. 

1. Goals
State your Goals:
y choice goals:
	- What is your y, what are you trying to predict?
- Where are you? What are you looking at?
- Where do you want to be? What are you looking for?
- How will you get there (to where you want to be)?
- vs. "solving a user problem"...it could be translated into this, but often is not.

What are your end-goals, even if there are also intermediate goals along the way?

Model Choice Goals:
Also, do you have any goals related to model size or model 'explainability' or model flexibility etc? Are the constraints on what kind of model you will, can, or want to use?

e.g. Do you want your target to be categorical or a number range? Do you want to engineer a y from your data, or is y already there as is? 




2.  Standards, Best Practice, and Terminology
Identify Standards, Best Practice, and Terminology that you will (aim to) adhere to:
- PEP8 (Python standards?)
- Unit Tests
- package / library version records documentation (readme)
- repeatability, auditability (?maintain-ability?)
- clarity on hypothesis, null-hypothesis, chosen benchmarks for significance(95%vs. 99%)
https://www.investopedia.com/terms/n/null_hypothesis.asp
- Terminology and Lexicons: Especially when working on cross functional teams, or preparing to explain to others, be aware of what terms you and others are using, and be wary of or aware of terms that may overlap or conflict with terms from another discipline: e.g.

Synonyms for 'y'
- y
- output variable
- Target
- Dependent Variable
- Response
- Response Variable
- Outcome Variable
- Predicted Variable
- Measured Variable
- Explained Variable
- Label


Synonyms for 'X'
- X
- input variable
- Independent Variable
- Explanatory Variable
- Regressor
- Covariate(s)
- Correlate(s)
- Feature(s)
- Class(s)
- Attribute(s)
- Predictor(s)



3. Hardware & Software
Pick hardware and software on which to run:
(Note: you may need to know something about your data before you do this, e.g. distributed massive spark/no-sql data)
	- "local" (your computer hardware) or remote (over the internet)
	- windows or POSIX (unix, BSD, MaxOS, Linux)
	- vim and a terminal
	- Google Colab (a remote debian virtual linux environment)
	- Local jupyter notebook in anaconda-python
	- IDE (integrated development environments)
		- note: for Python-DS, the line between a text editor and an IDE is blurry,
in part because you will be running code sometime in a 'python terminal' (ipython or pipenv shell etc) and sometimes in a 'normal command line terminal'
	- Spyder in Anaconda on your Local Computer
- docker containers, and AWS-EC2
	- etc.


4. Environment(s)
Set up your Virtual Environments, Kernels, etc.
Create and setup environments and virtual environments and begin organizing libraries packages and dependencies:
	- virtual containers:
- pipenv shell
- conda env
- venv
- conda kernel
- pip vs. conda package installs
- best practice: record exact versions of all packages used. (e.g. requirements.txt)
- maybe dockerize your environment so others can recreate it.



5. Software Libraries
Import your (main, initial) libraries noting versions:
	- keep track of what versions you are using and what versions you need of packages
- best practice: document what all of your software package and library versions are
	- os
	- python
	- conda
	- pandas
	- etc.
- maybe create a bundle of that software to be used later by other people


6. Get Data
Get files/data sets/ etc 
- obtaining data: source, scraping
- raw data: issues, file formats
- loaded data: dataframe, arrays, database

Include all data and steps for obtaining data, ideally in a way that can be automated in a notebook. 


7. EDA: Exploratory Data Analysis & Feature Discovery
Initial Exploration 1: first observations, 
	- Is the distribution Normal or is transformation needed?
- Did the data load properly (or at all), header, etc.
- shape: rows, columns
- data types
- NaN (like null or empty values), (but formatted as float64)
- odd characters
- cardinality
- redundancy
- empty columns
- formatting of columns (may look like int but be string or vice versa)
- is it time-series?
- seen knowledge about topic from sources and experts
- other messy or unusual items:
	- e.g. using 999etc instead of NaN or None or ' '
- do you understand what all of the fields/columns are?

EDA initial exploration 2: basic patterns 
- Use basic visualizations to analyze basic patterns in your data.

Tools for Explore:
- pandas profile

EDA initial exploration 3: "Artifacts"
A data-artifact is something that data appears to show but it turns out to be an artifact of how the data was collected or obtained. A classic example is from astronomy, where 'chromatic aberration' can lead to images that differ from real objects.
http://www.vikdhillon.staff.shef.ac.uk/teaching/phy217/telescopes/phy217_tel_refractors.html

	(a nice article on 4 common data exploration and data handling topics)
https://medium.com/@ageitgey/four-basic-data-science-lessons-illustrated-by-covid-19-data-7d94134a5b0e

EDA initial exploration 4: Weed Out
- What will need to be weeded out?
	- redundant features
	- leaky features
	- high cardinality

EDA initial exploration 5: Feature Discovery
- parametric method/model: factor analysis / cPCA/ pPCA / PMF

- non-parametric method/model: infinite latent factor models

https://www.asc.ohio-state.edu/lee.2272/mss/tr890.pdf 


8. Cleaning & Wrangle Data 
- "90% of time will be spent cleaning data"
- You may need to do some cleaning and 'wrangling' just to be able to look at your data at all (before EDA exploratory data analysis)
- standardize wrangling across split sets


9. Formatting, "feature engineering," etc.
- "Tidy" Format (the name of a standard)
	https://en.wikipedia.org/wiki/Tidy_data
	https://cfss.uchicago.edu/notes/tidy-data/
- Explanation: What is "feature" engineering?
	- Literally: making a new column of data (a new "feature") based on existing data


10. Features & Focus
- What is y (what you will predict)
- What X features should you include (/ exclude)
(including features you engineered yourself)
- note: "time-series for splits"
This may not come up until later, but think about what you are looking for and how to take things like the risk of 'time leakage' into account (see here)
https://medium.com/@GeoffreyGordonAshbrook/less-is-more-2070da966db7
	- How to turn data like natural language data into X and Y data:
		Explanation of a Natural Language Model
https://colab.research.google.com/drive/1n0QHVKLmjHhb1J0PVumoxq58-1OevP5b


11. Hypothesis
Articulate your Hypothesis? What is your Null Hypothesis?

12. Baseline Prediction
Establish a baseline and the testing-foundation for your baseline so that you can soundly evaluate the performance of your model (and develop your model making choices for better performance along the way).

12.1. Baseline
Establish A Baseline: Results to compare and score your model’s performance
(car race analogy)
(however narrowly your model wins over the baseline, making a 'better' or 'more useful' model is a binary measure of whether you have succeeded in making a successful model.)

Rules of Thumb for Setting a Baseline:
- For ordinal, continuous 'y' data: 
e.g. mean, median, mode, etc.
- For categorical 'y' data:
The 'majority “class”' is your baseline. (a “class” is a category, majority means the most common/frequent one) 
Python code to see majority class: >>> y_train.value_counts()[:1]
majority class / total = baseline (percent)
- (some say) Start with a kitchen sink “baseline model”:
a “kitchen sink” model as baseline is usually a basic model like a regression with ‘all feature columns' included.

12.2 Get baseline “score”: (is this right?)
- pick score type:
	- Regression:
		- MSE (mean squared error)
		- RMSE (Root mean squared error)
		- cross entropy loss
		- absolute loss
			(MAD mean absolute deviation, manhattan distance)
	- Classification:
- e.g. from confusion matrix:
- accuracy, (majority class mean), etc.
		- precision
		- recall
		- F1 (great self explanatory name, huh?)
	- MSE
	etc.
		
13. Split your Dataset: Make your sets: Train, Val, & Test sets
- issue: random or time based split
- issue: split ratio
(for cross validation:
randomized_searchcv,
(not-preferred-gridsearchcv)
(also,bayes-search?(library?)
Explanation: You are running an experiment where you need to compare your results. You not only need to compare your model to a baseline, but you need to compare how the model works on 'real data' compared with the data that you used to train the model. 


14. "Wrangle" Using a Function
make sure the data processing steps that you did are standardized for easy repetition and application to your split datasets
(for all: train,val,test)		
Create a function to automate the process of cleaning handling and reshaping your data, so that all divisions of split data (and new future data?) can be handled in the same way.  This systematizes what in the past you did through exploration.
Wrangle items:
- duplicates
- outliers
- drop empty data
- some "encoding"
- the formats of dates
- splitting times and dates into separate columns
- feature engineering

Preprocessing of Data (where applicable)
- randomizing order of training data
- normalizing
- one hot encoding
- 

15.  Family of Variables
(Make) Your Family of Variables
Establishing a 'family' of standardized varibles will help regularize the process of making pipelines and running models.
	e.g.
# Set Target & Features
target = 'feature_column_that_is_y_value'
features = ['colum_you_use_1', 'colum_you_use_1', 'etc']


# Wrangle train, validate, and test sets in the same way
train = wrangle(train)
val = wrangle(val)
test = wrangle(test)


# Arrange data into X features matrix and y target vector
X_train = train.drop(columns=target)
y_train = train[target]
X_val = val.drop(columns=target)
y_val = val[target]


16. Try and Compare Suit of Models
Pick what models you will try running. Try and compare multiple types of models if possible. Try to 'argue' why you have picked and not picked types of models based on your situation. 
https://www.datasciencecentral.com/profiles/blogs/40-techniques-used-by-data-scientists

On Model Selection and Consideration:
Unsupervised or Not:
	- Unsupervised Clustering

Supervised:
	- tree or linear

Categorical or Not

Tabular or Not

Neural Networks:
	- pre-trained vectorization
	- pre-trained models

Note:
	XGBoost tends to work well, but will not always be the best.


17. Pre-Pipeline phase
Some say: Before doing a pipeline do a model without the pipeline with each step separately for debugging.


18. Pipeline
Make a pipeline (e.g. sklearn) so that you can easily switch in and out different models and change parameters and hyperparameters and processes.
- If your data is in the form of a family of variables, you can easily run processes in a few short lines.
 
# Feature Scaling
from sklearn.preprocessing import StandardScaler
sc_X = StandardScaler()
X_train = sc_X.fit_transform(X_train)
X_test = sc_X_transform(X_test)


19. .fit .predict
Run Your Model(s): Proverbially ".fit .predict"
Once your data is organized, creating and running and evaluating your model made be unexpectedly brief:
	e.g.
	model = LogisticRegressionCV(cv=5, n_jobs=-1, random_state=42)
model.fit(X_train_scaled, y_train)
model.score(X_val_scaled, y_val)


20. Evaluate, Compare, Refine, Redeploy Models
Evaluate, Compare, Refine, Redeploy Models, adjust hyperparameters, squeeze out large and small improvements.
Tools to evaluate model.
- confusion_matrix+
- PDP
(Note: the term 'deploy' may be used here different than in WEB-product-deployment)


21. Feature Comparison
Formally analyze the roles and relationships between the features columns. 
- Are there interactions between columns?
- What columns have more of an effect?
- As in the case of time leakage, will some columns be disruptive and need to be discarded?

Tools:
- Shapely
https://towardsdatascience.com/how-to-explain-any-machine-learning-model-prediction-30654b0c1c8

22. Pick Final Model
Pick a final model or combination of models to use. (e.g. conventional models are often combined with neural networks)

23. Export Results / Model
Export the final "Test" or other final real-data results (using whole dataset to train)
When your results are the best you can achieve, fully train (and pickle) your model, and apply it to your final test or real world data. 
or, if you are producing a model rather than resulting output, serialize or pickle that model so it can be deployed. 

24. Analyze Performance
Examine the proverbial "accuracy" or score of your model and "publish" your results and commentary.
- Articulate your conclusions in terms of your null hypothesis and the significance of your results.

25. Configure for Deployment
Make any needed changes or write needed code for deploying the model where it will be used. For example, if the model will need to be fit to an endpoint to make predictions, make sure you have the code to accept data for new predictions.

26. Documentation
Review and complete documentation of and for your code.

27. Model Deployment for Users
- API for backends
- interactive web apps

28. Dashboard / Report
- Clear, Concise & Contextual
- Actionable
- Repeatable & Replicable


Note:
Data Visualization and Data Storytelling may be both or either a part of the early processing (helping you to understand how to process the data to begin with) or a later higher-order final product for a stakeholder (helping the stakeholder/user to understand data). It may also play a role in analyzing and tuning the model (understanding feature interactions, prominence, etc., weeding out time-leakage) in the middle. So while 'visualization' is not a single distinct phase of workflow, it may nevertheless be prominent and important. In particular cases you may want to articulate how datavisualization takes roles in exact places in the workflow. 

29. Future Action Plan
- improve model
- using model
- following up
- related models
- needed experiments or tests
- outstanding questions to answer


...


Further Research:
Another person's perspective on this topic:
https://towardsdatascience.com/a-data-science-workflow-26c3f05a010e



