# OlympicDatathonWork
This is the submission for the Olympic Datathon, by the team consisting of Ammar Salem, Dulnath Jayasinghe, Sofia Pangher and Zain Mobarik.

See the uploaded file for the submission.

README Contents

1. Brieft overview of the Notebook
2. More detailed overview of the Notebook
3. Explanation of Niave Bayes

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


Brief Overview of what's done in the Notebook

We start by inspecting the dataset, the data types, and summary statistics for each attribute

We then look at missing values and their co-incidence in the dataset, with the help of several visualizations.

We look at conditional probabilities of specific medal outcomes, making partial progress towards a Naive Bayes model of medal outcomes.

We also visualize athlete Hieght, Weight and Age distributions with histograms.


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------



Roadmap of the Notebook (More detailed overview)

We begin by inspecting the first section of the dataset, the columns and their data types, and basic descriptive aspects of each column (unique values, number of values in each column etc).

We carry out an extended analysis of missing values:

///////////////////

We begin the analysis of missing values by discussing the handling of missing values for specific attributes in the dataset, and importing a package for analysing missing values(missingno)

We then check the number of missing values for each attribute or column, visualize this (or equivalently the data completeness of each attribute) on a bar chart.

We visualize how attributes' missing values coincide (ie; how a entry value for a given variable being missing correlates with the value of another attribute value for the same entry being missing) with a heatmap.

Then we plot a dendrogram of the attributes based on coinciding missing values. We interpret the missing values visualizations, make informed guesses as to the underlying procceses that give us the observed patterns in missing values, and briefly note the implications for a Naive Bayes model based on the dataset.

/////////////////////////



We then calculate conditional probabilities of achieving particular medal outcomes, conditioning on gender, and discuss the implications for non-exploratory analysis or use of the dataset. Note that the calculation of conditional probabilities was done for the purpose of building a Naive Bayes model of athlete outcomes (the work for this is only partially done)

We then calculate quantiles of the age distribution of athletes (partly because it was neccesary for incorportaing age into the Naive Bayes model), interpret the results and discuss potential implications for some substantive topics of analysis (eg; cross-country comparison).

Next we plot histograms of athlete Height, Weight, and Age, and interpret them to note what they suggest about the underlying distributions for those variables. We also briefly note that this may have implications for regression analysis or hypothesis testing.

We then return to calculating the conditional probabilties required for Naive Bayes; in this section we handle age. We follow a common method of applying Naive Bayes to continuous variables in converting it to four bins of quartiles ( discretising age into four equally-frequent age classes). We then begin calculating the conditional probabilities of each medal outcome given age class, starting with the under-21s quartile.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Explanation of Naive Bayes

This post has a good explanation of Naive Bayes; 
https://stats.stackexchange.com/questions/21822/understanding-naive-bayes

In a nutshell, it relies on the features we're using to predict outcomes being independent of each other; then if we're told the features for something we want to predict for, we multiply the conditional probability of outcome O given feature 1 is the given value by the conditional probability of outcome O given feature 2 is the given value and multiply again by the conditional probability of outcome O given feature 3 is the given value ..... 

We multiply these conditional probabilities for each outcome conditioning on each feature we're already given for the case to be predicted. This gives us values for each outcome that are (proportional to) rough estimates of the likelihood of each outcome obtaining given the features we're told. 

This relies on the features we're using to predict the outcomes being independent of each other (it's what lets us just multiply each pairwise conditional probability). Otherwise, we'd have to condition on all the features we're given JOINTLY taking the values they do ( eg; Winning a Gold medal given younger than 21 AND Male AND less than 150 cm tall AND...). This can run into issues with there not being enough datapoints in that intersection to get a reliable conditional probability, besides the greater difficulties in computing all these values and setting up a system to retrive the values we want. That's why we multiply the pairwise conditional probabiltiies of outcome O given feature F inseatd of conditioning on the intersection of the features.
