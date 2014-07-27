Samsung_data
============

Getting and Cleaning Data course Project

### Environments:

    The script in the analyzer was tested in R-studio 0.98.953, installed in a Windows 8 x64 system. "reshape2"     and   "stat" library from R-studio are required for the code to run.
    
    
### Functions of the code book: 

1. Reading the raw files into R;
    Since the original data sets are ~80Mb, reading them into RAM may take several minutes.
    Raw data is read into global environment incase further analysis will be done with them.
2. Out of the total 561 variables, extracting ones with "-mean()" or "-std()" in the variable name;
    The name of the variables are extracted from "feature.txt".
    Note that according to "feature_info.txt", some additional measurements have "Mean" in their names, such as          "gravityMean". These measurments are not extracted, leaving total 66 measurements.
3. Labling and merging data;
    Activity names are extracted from "activity_labels.txt". Subject/activity information for measurements are extracted from "subject_.txt" and "y_.txt" files in each sets.
    The activity numbering is replaced by text. Activity names and subject information is merged with the dataset.
    A new column is added for "Data.type", indicating whether the data belongs to test or train groups. Then the train and test groups are merged together.
4. Calculating average for each activity of each subject;
    Measurements with same subject and activity are pooled together for calculating the average for each of the 66 variables. This is achieved by using "split" + "sapply" function in R. Since the number of trials for each subject/activity are not the same, the number of trails are also recorded.
    The output if the final result of these scripts. It is a data.frame with 70 columns and 180 rows. The first 4 rows are ID for Subject, Activity, Data.type (test or train) and Number of Trails. And the rest of the columns are 66 different measurements containing "-mean()" or "-std()" in the variable names. Columns are named with these labels. The data.frame is sorted by the Activity column.
