# Overview

The function `run_analysis()` defined in the script `run_analysis.R` performs data cleansing as defined in the course project for the course Getting and Cleaning Data under Coursera.  
The steps are described in more detail as follows:

1. All similar data is merged using the `rbind()` function i.e. files having the same number of columns and referring to the same entities.
2. Only those columns with the mean and standard deviation measures are taken from the whole dataset. After extracting these columns, they are given the correct names, taken from `features.txt`.
3. As activity data is addressed with values 1:6, we take the activity names and IDs from `activity_labels.txt` and they are substituted in the dataset.
4. On the whole dataset, those columns with vague column names are corrected.
5. A new dataset is generated with all the average measures for each subject and activity type (30 subjects * 6 activities = 180 rows). The output file is called 'tidy_data_result.txt'.

# Variables

* `x_train`, `y_train`, `x_test`, `y_test`, `subject_train` and `subject_test` contain the data from the downloaded files.
* `x_data`, `y_data` and `subject_data` merge the previous datasets to further analysis.
* `features` contains the correct names for the `x_data` dataset, which are applied to the column names stored in `mean_and_std_features`, a numeric vector used to extract the desired data.
* A similar approach is taken with activity names through the `activities` variable.
* `all_data` merges `x_data`, `y_data` and `subject_data` in a big dataset.
* `averages_data` contains the relevant averages which will be later stored in a `.txt` file. `ddply()` from the plyr package is used to apply `colMeans()` and ease the development.
