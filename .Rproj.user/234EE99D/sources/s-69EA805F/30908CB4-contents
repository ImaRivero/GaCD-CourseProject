#> Getting and Cleaning Data Course Project
#> Author: Imanol Rivero

#> 1. Merges the training and the test sets to create one data set.
#> 2. Extracts only the measurements on the mean and standard deviation for each measurement.
#> 3. Uses descriptive activity names to name the activities in the data set
#> 4. Appropriately labels the data set with descriptive variable names.
#> 5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.


# Packages
library(dplyr)
library(data.table)
library(reshape2)

# Getting the data
url <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
download.file(url, "./data/UCIdata.zip")
unzip("./data/UCIdata.zip")

# Load labels and features
act_labels <- read.table("UCI HAR Dataset/activity_labels.txt",
                         col.names = c("classLabel", "actName"))
features <- read.table("UCI HAR Dataset/features.txt",
                       col.names = c("index", "featureName"))
index_features <- grep("(mean|std)\\(\\)", features[, "featureName"])
measurements <- features[index_features, "featureName"]
measurements <- gsub("[()]", "", measurements) # remove parentheses

# Load train data

train <- read.table("UCI HAR Dataset/train/X_train.txt")
train <- select(train, index_features) # selecting only the columns that we want
setnames(train, colnames(train), measurements)

trainActivities <- read.table("UCI HAR Dataset/train/Y_train.txt",
                              col.names = c("Activity"))
trainSubjects <- read.table("UCI HAR Dataset/train/subject_train.txt",
                           col.names = c("Subject"))
train <- cbind(trainSubjects, trainActivities, train) # Binding all training columns

# Load test data
test <- read.table("UCI HAR Dataset/test/X_test.txt")
test <- select(test, index_features) # selecting only the columns that we want
setnames(test, colnames(test), measurements)

testActivities <- read.table("UCI HAR Dataset/test/Y_test.txt",
                             col.names = c("Activity"))
testSubject <- read.table("UCI HAR Dataset/test/subject_test.txt",
                             col.names = c("Subject"))
test <- cbind(testActivities, testSubject, test)

# Merge datasets
completeDataset <- rbind(train, test)

# The second independent dataset
secondDF <- reshape2::melt(data = completeDataset, id = c("Subject", "Activity")) # Aggregate by Subject and then by Activity
secondDF <- reshape2::dcast(data = secondDF, Subject + Activity ~ variable, fun.aggregate = mean) # Calculates the mean for each combination

# Writing results to files of the tidy datasets
write.table(completeDataset, "tidyDataset.txt", row.name=FALSE)
write.table(secondDF, "tidyDataset_second.txt", row.name=FALSE)
