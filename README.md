# Bellabeat-Case_Study
This case study is part of Coursera’s Google Data Analytics Capstone Project. 

## Scenario

I am a junior data analyst working for Bellabeat's marketing analyst team. Bellabeat is a high-tech manufacturer of women's health products. Being a successful small company, they have potential to grow larger in the global smart device market. Urska Srsen, cofounder and CEO of Bellabeat, believes that analyzing smart device fitness data could help unlock new growth opportunities. I've been asked to focus on one of Bellabeat's products and analyze smart device data to gain insight on how consumers use their smart devices. The output will then help guide Bellabeat's marketing strategy. I will present my analysis to the Bellabeat executive team along with my high-level recommendations for their marketing strategy. 

## Ask Phase

### Business Task

My goal is to find trends in smart device usage and their application for Bellabeat's customers. Moreover, I will help the marketing team to apply a more targeted strategy. Looking at the data and keeping the business task in mind, I've concluded that the following questions will provide very good results, always in relation to the initial data. Stakeholders of the business task are:

* Urška Sršen: Bellabeat’s co-founder and CEO
* Sando Mur: Mathematician and Bellabeat's co founder; key member of the Bellabeat executive team
* Bellabeat marketing analytics team

Also, by applying the S.M.A.R.T. process I can identify that the data is indeed specific, measurable, action-oriented and relevant. However, I cannot say that the data are time-bound. They are outdated because the entries are from April and May of 2016.

Therefore, according to the previous process, the following questions will help me extract the correct answers to discover the insights needed:

* Correlation between Total Steps and Calories
* Correlation between Total Distance and Calories
* Correlation between AciveMinutes (sum of Very+Fairly) Calories
* Group IDs by Activity levels (Low, Medium, High)
* Average of Active Minutes per day
* Comparison between Lightly Active Minutes and sum of ( Fairly + Very Active MInutes) as IntenseActiveMinutes
* Does average Calories is keeping up with todays standards? (Low, Medium, High Burn) 
* Correlation between TotalSteps and Sleep Duration
* Correlation between (Very+Fairly)Active Minutes and Sleep Duration

*I would also like to study the correlation between Calories and Weight but unfortunately the data for weight measurements is not comprehensive and consistent. Only 8 users logged their weight. 

To answer these questions, the Prepare and Analysis Phases will be completed by using data from the following CSVs:

* dailyActivity_merged1.csv
* sleepDay_merged.csv

### Prepare Phase

Sršen encourages me to use a specific public dataset: [FitBit Fitness Tracker Data]([url](https://www.kaggle.com/datasets/arashnic/fitbit)) . Dataset is available by the user [Mobius]([url](https://www.kaggle.com/arashnic)). The dataset has a license ([CC0: Public Domain]([url](https://creativecommons.org/publicdomain/zero/1.0/))). This Kaggle data set contains personal fitness tracker from thirty FitBit users. Thirty eligible Fitbit users consented to the submission of personal tracker data, including minute-level output for physical activity, heart rate, and sleep monitoring. It includes information about daily activity, steps, and heart rate that can be used to explore the user's habits.

The data will be stored in a generic folder in Google Drive. Inside this folder will be stored every relative file or folder to this case study. All the CSVs with the data provided are in long format. 

According to the R.O.C.C.C. analysis:

Reliability: Not strong due to small sample size (33 individuals) 
Original: Not Strong due to data collection from a third-party provider (Amazon Mechanical Turk)
Comprehensive: Not strong due to small sample size (33 individuals). No data in relation to gender, age, and health conditions. Data is biased (women's sample)  
Current: Not strong due to old data collection (samples of April & May of 2016)
Cited: Not Strong due to data collection from a third-party provider (Amazon Mechanical Turk)

Furthermore the dataset does not contain columns with data of gender, age or residency. 