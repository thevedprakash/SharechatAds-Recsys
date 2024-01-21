Introduction
The archive contains the dataset for Sharechat RecSys Challenge 2023. The data set consists of records that capture user and ad features (categorical, binary, numerical) and whether a click and/or install was generated by the user. It should be noted that in the case of online advertising, it is possible that a user has viewed an ad and then didn’t click on the ad and directly installed the underlying application. The implication of this behavior is that we have records where there is no click but there is an install.

To generate the training and test data, we considered the ad serving data for 22 consecutive dates. The first 21 days form the basis for training data and the 22nd day data is used to generate test data. From this base data, we created impression records, which implies that an ad was viewed by a user. We annotated this data with two fields, is_clicked and is_install, to denote whether there was a click and install done by the user. We can subdivide the whole data set into four non-overlapping subsets using the values of (is_clicked, is_installed) as follows:

1. (0, 0) corresponds to impressions where there were neither clicks nor installs
2. (1, 0) corresponds to impressions which resulted in a click but no install
3. (0, 1) corresponds to impressions where user didn’t clicked but installed the app
4. (1, 1) corresponds to impressions where the user performed a click followed by an install of the app.

To keep the dataset within manageable size and to safeguard the confidential information around click through rates, conversion (install) rates, we differentially downsamples the records corresponding to four subsets above.

Task
The task of the challenge is to predict is_clicked and is_installed for the records in the test set.

Contents of the Archive
The archive contains two folders and the README file (this file). The train folder contains 30 files which represent the training data and the test folder contains 1 file which represents the test data. The files are tab separated.

Training Data:
There are multiple files under the train folder. Each line of the file denotes one impression record. Each file has the following format:

1. The first row is the header row that contains names f_0 to f_79 followed by is_clicked, is_installed.
2. Each line consists of different columns that are tab separated.
3. The data types of different columns are:
   a. RowId(f_0)
   b. Date(f_1)
   c. Categorical features(f_2 to f_32)
   d. Binary features(f_33 to f_41)
   e. Numerical features(f_42 to f_79)
   f. Labels(is_clicked, is_installed)
4. Some of the features may be null, denoted by empty string for the corresponding feature in the tab seperated line
   corresponding to that record

Test Data:
There is a single file in the test folder. The file has identical format as train folder files with the exception that the
two columns (is_clicked, is_installed) are not present

Submission Format:
The format for the submission file should contain three tab separated columns representing RowId corresponding to the
lines in the test data and the corresponding prediction for is_clicked, is_installed.

if you develop local repository first to push changes to remote.
git init
git add .
git commit -m "comment"
create a repository on github
repo : https://github.com/thevedprakash/SharechatAds-Recsys.git
git remote add origin https://github.com/thevedprakash/SharechatAds-Recsys.git

branch : main
git push -u origin branch
