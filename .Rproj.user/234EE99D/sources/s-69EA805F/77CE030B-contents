# Code Book

Describes the variables, the data, and any transformations or work that you performed to clean up the data

## The data used
One of the most exciting areas in all of data science right now is wearable computing - see for example this article . Companies like Fitbit, Nike, and Jawbone Up are racing to develop the most advanced algorithms to attract new users. The data linked to from the course website represent data collected from the accelerometers from the Samsung Galaxy S smartphone.

It can be retrieved from here: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

## The variables
1. url: saves the url to download the data
2. act_labels: Activity labels from the file with the same name, we only use the name
3. features: Feature labels from the file with the same name.
    * Transformations: Name changed
4. index_features: filter indexes of the features that we were looking for (mean|std)
5. measurements: labels extracted by the index_features
    * Transformations: Removed parentheses
6. train: dataframe retrieved from the X_train file
    * Transformations: Select only the columns that we wanted, using index_features and change names for the labels from measurements and finally appended with the other train dataframes
7. trainActivities: Dataframe from the Y_train file
8. trainSubjects: Dataframe from the /train/subject_test file
9. test: dataframe retrieved from the X_test file
    * Transformations: Select only the columns that we wanted, using index_features and change names for the labels from measurements and finally appended with the other test dataframes
10. testActivities: Dataframe from the Y_test file
11. testSubjects: Dataframe from the /test/subject_test file
12. completeDataset: The complete dataset, result by the union of train and test
13. secondDF: Dataframe for the secondary dataset for the 5th requirent (described in the code)
    * Transformations: Melted using reshape2 (aggregated by Subject and then by Activity), applied the mean function via dcast.