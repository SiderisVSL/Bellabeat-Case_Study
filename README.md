# Bellabeat-Case_Study
This case study is part of Coursera’s Google Data Analytics Capstone Project. 

## Scenario

I am a junior data analyst working for Bellabeat's marketing analyst team. Bellabeat is a high-tech manufacturer of women's health products. Being a successful small company, they have potential to grow larger in the global smart device market. Urska Srsen, cofounder and CEO of Bellabeat, believes that analyzing smart device fitness data could help unlock new growth opportunities. I've been asked to focus on one of Bellabeat's products and analyze smart device data to gain insight on how consumers use their smart devices. The output will then help guide Bellabeat's marketing strategy. I will present my analysis to the Bellabeat executive team along with my high-level recommendations for their marketing strategy. 

[CSVs (Results)](https://drive.google.com/drive/folders/1LV5z8p8178mVgGfdfgfn5w7ynIH_v8Ta?usp=sharing)

[CSVs (Cleaned)](https://drive.google.com/drive/folders/1axmDIfaBI13iodEVycJCh5YCyBnsaoKj?usp=sharing)

[CSVs (Queries)](https://drive.google.com/drive/folders/1jXexcqaC7iXHcrR8FfSBh9PIXemHlu7J?usp=sharing) 

[Tableau Public Dashboard Charts](https://public.tableau.com/app/profile/vasileios.sideris/viz/BellabeatCaseStudyDashboardCharts/BellabeatCaseStudyDashboardCharts)


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

Sršen encourages me to use a specific public dataset: [FitBit Fitness Tracker Data](https://www.kaggle.com/datasets/arashnic/fitbit)) . Dataset is available by the user [Mobius](https://www.kaggle.com/arashnic). The dataset has a license ([CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)). This Kaggle data set contains personal fitness tracker from thirty FitBit users. Thirty eligible Fitbit users consented to the submission of personal tracker data, including minute-level output for physical activity, heart rate, and sleep monitoring. It includes information about daily activity, steps, and heart rate that can be used to explore the user's habits.

The data will be stored in a generic folder in Google Drive. Inside this folder will be stored every relative file or folder to this case study. All the CSVs with the data provided are in long format. 

According to the R.O.C.C.C. analysis:

Reliability: Not strong due to small sample size (33 individuals) 
Original: Not Strong due to data collection from a third-party provider (Amazon Mechanical Turk)
Comprehensive: Not strong due to small sample size (33 individuals). No data in relation to gender, age, and health conditions. Data is biased (women's sample)  
Current: Not strong due to old data collection (samples of April & May of 2016)
Cited: Not Strong due to data collection from a third-party provider (Amazon Mechanical Turk)

Furthermore the dataset does not contain columns with data of gender, age or residency. 


### Process Phase

The following phase will be completed with the data of the following CSV files. 

* dailyActivity_merged1.csv
* sleepDay_merged.csv

Since the datasets are very small (940 & 413 rows respectively), the cleaning process will be performed with Microsoft Excel. 
Manipulation and visualization processes will be performed with Google’s Cloud Console: BigQuery and Tableau Public.

#### Microsoft Excel
* Checked the length of the ID. Every ID has 10 characters length. (dailyActivity_merged1) - Used the =LEN function.
* Removed TrackerDistance since it has exactly the same values as TotalDistance column. - (dailyActivity_merged1)
* Removed LoggedActivitiesDistance due to the fact is has only a few entries. 
* Changed the Id column’s format to Number. - (dailyActivity_merged1)
* Changed the ActivityDate column’s format to Date (MM/DD/YY).  (dailyActivity_merged1)
* Changed the Total Steps column’s format to number. (dailyActivity_merged1)
* Changed the TotalDistance column’s format to number with only 2 decimals. (dailyActivity_merged1)
* Removed the Very/Fairly/Lightly and Sedentary ActiveDistance columns. There will be no part of my analysis.  
* Checked for any outliers in TotalSteps,TotalDistance and Calories. (dailyActivity_merged1) - Used the =MAX function. 
* Assuming TotalDistance’s unit is miles, 28.03 miles/day is high but a normal number for a person to walk/run. (dailyActivity_merged1)
* Highest calories recorded (4.800) it is in range for a typical person doing intense activity (4.000 - 6.000) - (dailyActivity_merged1)
* No outliers in column with summarized minutes (max=1440). - (dailyActivity_merged1)
* Saved the file as DailyActicity_cleaned.csv

Checked the length of the ID. Every ID has 10 characters length. (sleepDay_merged) - Used the =LEN function.
Removed the TotalSleepRecords column. This will be no part of my analysis. - (sleepDay_merged)
Changed the Id column’s format to Number. - (sleepDay_merged)
Changed the SleepDay column’s format to Date (MM/DD/YY). - (sleepDay_merged)
Saved the file as SleepDay_cleaned.csv

#### Google’s Cloud Consone: BigQuery

In BigQuery i created a new project “bellab77”. 

Inside the project I created a dataset with the name “bb” and then I uploaded the two csv files, DailyActicity_cleaned.csv and SleepDay.csv. 


### Analyze Phase

#### Query for joining the two tables

![1 SELECT](https://github.com/user-attachments/assets/854ac43c-7371-4028-b95d-c3fb130f5fd7)

#### Correlation between TotalSteps, TotalDistance, ActiveMinutes and Calories

![Screenshot 2024-12-14 at 14 04 14](https://github.com/user-attachments/assets/d65f6c57-a34a-4b4c-9d57-0d041189b921)

#### Group IDs by Activity levels (Low, Medium, High)

![Screenshot 2024-12-14 at 14 05 25](https://github.com/user-attachments/assets/842045e8-36a1-4ad2-849d-0396a18ec3fb)

#### Average of Active Minutes per day

![Screenshot 2024-12-14 at 14 06 06](https://github.com/user-attachments/assets/2bd47caa-da55-4411-bd15-5692dc73888a)

#### Comparison between Lightly Active Minutes and sum of ( Fairly + Very Active MInutes) as IntenseActiveMinutes

![Screenshot 2024-12-14 at 14 06 53](https://github.com/user-attachments/assets/a6de537a-7dbc-4452-ad5e-32a0eae539fb)

#### Does average Calories is keeping up with todays standards? (Low, Medium, High Burn) 

![Screenshot 2024-12-14 at 14 07 38](https://github.com/user-attachments/assets/fd2be884-0467-4b39-a154-005682d50dd9)

#### Correlation between TotalSteps and Sleep Duration

![Screenshot 2024-12-14 at 14 08 32](https://github.com/user-attachments/assets/872f2778-a571-47d9-9272-033bc9b13e8a)

#### Correlation between (Very+Fairly)Active Minutes and Sleep Duration

![Screenshot 2024-12-14 at 14 08 59](https://github.com/user-attachments/assets/e0c881b4-d650-4086-8c5a-04494f945257)


### Share Phase

#### Correlation between TotalSteps and Calories
<img width="2463" alt="Screenshot 2024-12-13 at 04 50 06" src="https://github.com/user-attachments/assets/afea25fc-d7de-46d7-af8d-85befacccae4" />

#### Correlation between TotalDistance and Calories
<img width="2458" alt="Screenshot 2024-12-13 at 04 50 18" src="https://github.com/user-attachments/assets/4832f0ff-f16f-4bc9-b1b6-cb39a45c4462" />

#### Correlation between ActiveMinutes and Calories
<img width="2459" alt="Screenshot 2024-12-13 at 04 50 28" src="https://github.com/user-attachments/assets/e7cdda37-28df-40a7-8fb5-65ddcffd15fb" />

The analysis of the first 3 charts about the correlation between ##### Calories and ##### TotalSteps, ##### TotalDistance, ##### ActiveMinutes, clearly shows a positive correlation in all 3 of them. This coincides with the basic principle of physical activity, increased movement leads to higher calorie loss. On the other hand, a few outliers may represent other intense activities and not necessarily exercise. 

#### Group IDs by Activity levels (Low, Medium, High)
<img width="2460" alt="Screenshot 2024-12-13 at 04 51 10" src="https://github.com/user-attachments/assets/96a93e30-ca13-4292-a8c5-3548db3c7f07" />

The pie chart divides users into three groups based on activity levels - Low, Medium and High Activity. The largest segment of the pie chart consists of Medium Activity users (5.000-10.000 steps). Also High Activity users hold quite a large share. (>10.000 steps). The third and smallest segment is Low Activity users (<5.000 steps)

#### Average of Active Minutes per day
<img width="2455" alt="Screenshot 2024-12-13 at 04 51 32" src="https://github.com/user-attachments/assets/31ea4222-6a01-4bbd-9d67-35fee7fe5245" />

The above bar-chart illustrates the average Active Minutes of the weekdays. We can identify that the highest activity days are Tuesday with 37,29 minutes and Saturday with 37,12 minutes. The days with the lowest activity minutes are Thursday with 32,17 minutes and Friday with 31,37 minutes. This indicates a drop of physical activity towards the end of week. 

#### Correlation between TotalSteps and Sleep Duration
<img width="2458" alt="Screenshot 2024-12-13 at 04 51 47" src="https://github.com/user-attachments/assets/f1d2c8bc-6801-4af8-be35-0156fb21ad38" />

#### Correlation between ActiveMinutes and Sleep Duration
<img width="2462" alt="Screenshot 2024-12-13 at 04 52 20" src="https://github.com/user-attachments/assets/1646a4cb-c5d9-4e53-b0bf-33a5328fe401" />

From the analysis of the above 2 scatterplots, it seems that the correlation between Sleep Duration and TotalSteps/ActiveMinutes has a downward trend line. This indicates a slight negative correlation meaning that as TotalSteps and ActiveMinutes increase, Sleep Duration tends to slightly decrease. Individuals with higher step count, tend to sleep slightly fewer minutes. Also the spread of data points indicates variability. This suggests that step count alone doesn’t increases sleep duration. There are maybe some other factors such as health or lifestyle that affect the duration of sleep.  

#### Does average Calories is keeping up with todays standards? (Low, Medium, High Burn)
<img width="511" alt="Screenshot 2024-12-13 at 06 37 08" src="https://github.com/user-attachments/assets/8d8d79a9-5ae2-41f3-91ed-237f7bc1ad2e" />

The average calorie loss is indeed keeping up with today’s standards. I grouped the average calorie loss by 3 segments. The range between 1.600 - 1.950 calorie loss is a moderate range for women. As we can see from the table, the portion of High Burn consists of 70% (23/33 users), Medium Burn 18% (6/33 users) and Low Burn with 12% (4/33 users). 


### Act Phase

In the last phase I will provide my team with recommendations  for better marketing strategy. 

* Develop campaigns that targets medium activity users to encourage them to be more active

* Create tools to provide a better experience for very active users:
    * Better and more accurate measurements
    * Categorized workouts (running, walking, swimming etc) with help for each one

* Tips or help for better performance
 
* Develop  campaigns for low active users that documents the benefits for workouts. A campaing that persuade them “Start from zero”

* Mobile or watch notifications with a summary of workout details (heartbeat, distance, average pace, etc)

* Mobile or watch notifications of workout’s achievements e.g. “1 mile already!” or “Good work! Keep up!”

* Significant workout plans for losing weight based on height, weight, age

* Better and more detailed measurements for sleep. E.g. stages of sleep (REM - Core - Deep)

* Stages of difficulty for workouts. For example 1 - 10, for 1 to be “Very Easy” and 10 to be “Very Hard” or “Pro”
   














































