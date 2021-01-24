# Roro-Unloading-Times-Prediction

This project aims to predict a unit's lifetime inside Trieste port after arriving with a roro. This waiting time inside Trieste Port can be affected by many factors like urgency of the unit, destination country, arrival day, unit quantities, holidays etc. 

In this project, several regression algorithms are run in order to find a model that predicts this time according to independent factors that may effect it. In the base model, with the help of a grid search cv, best model with best hyperparameters is found. Then this best model is trained with whole data and saved as a Pickle Model.

On live system, I created a Oracle view in order to retrieve list of units that needed to be predicted. In the second python script, it retrieves live data via Oracle integration from this view, then it makes predictions according to pickled model, and finally it records all of these into an Oracle table again with a connection to database. 

Whole script runs periodically during the day, with the help of Microsoft Task Scheduler. 

As a result, it increased the accuracy of waiting time predictions by 50% compared to fixed 4 hour rule, and 40% compared to mean waiting time rule. These predictions are used as inputs of our optimization algorithm that assigns resources to individual units. Such operational time parameters are important for accuracy of the optimization model of course. 
