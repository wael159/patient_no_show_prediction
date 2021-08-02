# Patient no show prediction 🏥

![image](https://drive.google.com/uc?export=view&id=1PyvXb_SgQaS1CHQdnbEvBHPyjr1QWLuU)

[report summary](https://drive.google.com/file/d/1n4_L_xwyP3Ik31mRwEv7r-IILzpdtd7m/view?usp=sharing)<br>
[Presentaion link ](https://onedrive.live.com/embed?cid=9A8C4DAF1CCF33DC&amp;resid=9A8C4DAF1CCF33DC%21989&amp;authkey=AIRbEZHYmCqIjqw&amp;em=2&amp;wdAr=1.7777777777777777)<br> 
[Summary video 📽️](https://www.youtube.com/watch?v=cFBWBBx65Lw) 



### 🎯 Project goal 
---
20% of the patients missing their appointment without cancellation, which is very costly to healthcare institutions. This project aims to predict if the patient will miss their appointment or not and know why no-shows.<br>
**Bussienss goal** : save money💸 and reduce no shows


### 🔎 Overview 
---
The [Kaggle](https://www.kaggle.com/joniarroba/noshowappointments)  dataset comprised 110k appointments records from public healthcare institutions in a Brazilian city. 
The appointments occurred across a 6-week period in 2016 (27 days ). 
The appointments occurred from 29.4.2016  to 08.06.2016 . the scheduled visits starts  from 10.11.2015 to 8.6.2016.
The data was derived from 62k patients , from 81 neighborhoods.<br>

**The data consists of the following:**
-	**Identifier**: patient id(non-unique), appointment id ( unique).
-	**Patient information** : gender, the health of the patient (hypertension, diabetes, alcoholism, handicap), scholarship, receiving SMS.
-	**Appointment information**: schedule date (with the time) and appointment date(without the time).
-	**Location of the clinic** : clinic's neighborhood.
-	**Target**: show or no show ( 0 or 1) 


### 🗒️ Note 
---
⚠️ Note: *there is 2 folders , one for the data analysis with the data which was loaded from kaggle,i used graphes from plotly so maybe some of the plotly graphs will not appear.
the second one is for machine learning with the cleaned data* .



### Data cleaning:
---
Binary coding for the target 0 = show , 1 = no show , gender 0=male , 1 = female .
Ages under 0 were deleted. There is no null data in the dataset.

### Feature engineering:
---
- **Waiting days** – the difference between the scheduled date and the appointment date, all negative values were dropped.
- **Total disease** – the sum of all the diseases for each patient.
- **Dropping the neighborhood** – if I changed them to dummy, there would be many features, 81 more features, and it may be cause overfitting.
- **Split** the appointment day and scheduled day to day, month, day of the week.
- **Total prior appointments** – the total prior appointment for each patient will be updated  every time the patient make a new appointment
- **Total prior missed appointments** -the Total missed appointment will also be updated every time the patient makes a new appointment.<br>
*The last two features were added in the third step for machine learning
18 features at all, added two other features =20 features

### Descriptive Statistics
---
**Patients show vs. no show:**<br>

![image](https://drive.google.com/uc?export=view&id=1F8E1VnSuWnxiy5_TyIS6ZQ84vqWA2E0O)


 **Figure 1**: we can see from the figure above that 20.2% of the patients missed their appointments.<br><br>
 
 **Patients's distribution by age:**<br>
 ![image](https://drive.google.com/uc?export=view&id=1-XJiAZSOcldASbKURkJaOu7-qktvayoA)<br>
**Figure 2:** The histogram above shows the distribution of the appointments by age and gender. We can see that the median age of the male is 33, 25 % of them in the ages 0-10 years, and 50% above 33 years old. While the median age of the female is 39, 25% of them is between 0-21,50% above 39 years old. Most of the patients are babies – more than 3000 patients are 0 years old.
We can also see an outlier -one of the females is 115 years old; I removed this outlier and took all the ages between 0 – 110.<br><br>

**Patients by Gender**<br>
![image](https://drive.google.com/uc?export=view&id=1Lhx45SDsdvBb0h2e1IGezUmvhXCtbzk3)<br>
**Figure 3 :** **A**-(counterclockwise) we can see that 65% of the patients are female (the inner circle), 78% of them (51.8% of the data) show up to the appointments, while 22% of them are absent(13.2% of the overall patients).35% of the patients who make appointments are male, 80% of them show up (28.0% of the patients), while 20% of them are absent (7.0%).<br>
**B-** The distribution of no-shows by age and gender - we can see that in the range 0-10, there is no difference between the rate of no-shows between males and females. However, from the age range of 10-18, the male has more no show, while from the age 18-60, the female has more no show than male.

**C**: Individuals in different age groups exhibit different No-Show behaviors. For example, infants/boys/girls, teenagers, working-age people, and retired populations will all have different No-Show patterns. We can see from this figure that a high rate of females in the age range 20-30 are absent, while there is a high rate of males in the age range of 10-20 who are absent. <br><br>



**Absence by age range and day of week** <br>

![image](https://drive.google.com/uc?export=view&id=1RU8PJruJy80exdieF3lHEQOeGUhRGovT)<br>
**Figure 4:** **A-** We can see from the heatmap that there is more absent patient in the age range 10-20 on Wednesday. Most patients who missed their appointments are from 0-60 in the days Monday -Wednesday.<br><br>

**Absence by age range and day of week**<br>
![image](https://drive.google.com/uc?export=view&id=1557YvyrUqzTX1vEaqtIKhwFnsydyV2sR)<br>
**Figure 5** - we can see the rate of the show and no show on each day of the week for all the patients, there is no high difference between the days, but we can see that there is more show on Thursday than each day of the week. <br><br>


### Mid-Insights:
---
- 	We must remind or resend an SMS  to the female patients from the age range 20-30 and males from 10-20 ( or to their parents).
- 	Most of the absent patients on Wednesday are patients in the age range of 10-20.
-	 There is more absent patient from Monday to Wednesday in the age range of 0-60.
---

**Patients by background disease** <br><br>
![image](https://drive.google.com/uc?export=view&id=1_KHGikBgHSJICANylNrlXXzzVv_rkqbL)<br>
**Figure 5 :**
**A-** 23.8% of patients have at least one disease, **B-** 63.0% have hypertension, 22.7% with diabetes, 7.8% with alcoholism, and a 6.5% handicap.
**C-** We can see many no-shows from alcoholic females, so maybe we must also remind them or call them.<br><br>

**Patients distribution by background disease**


![image](https://drive.google.com/uc?export=view&id=1_KHGikBgHSJICANylNrlXXzzVv_rkqbL)<br>

**Figure 6 :**
**A-** 23.8% of patients have at least one disease, **B-** 63.0% have hypertension, 22.7% with diabetes, 7.8% with alcoholism, and a 6.5% handicap.
**C-** We can see many no-shows from alcoholic females, so maybe we must also remind them or call them.<br><br>

**Show vs. no show by clinic location**

![image](https://drive.google.com/uc?export=view&id=183gvDB9TBbRsjkg-85mYfZlNf3yb2ggb)<br>

**Figure 7:** we can see here that there is a high rate of absent patients from some of the neighborhoods like nova Palestina.<br><br>

**Show vs. no show by waiting time.**<br>
![image](https://drive.google.com/uc?export=view&id=1i1tJ7VFMdLMDEudvCmq2k8INgEtxbtPJ)<br>
**Figure 8:** the attendance rates of the appointments scheduled for the same day are the highest. The no-showing rate increases as the waiting gets longer. The time that elapses between booking the appointment and the actual appointment is associated with a higher probability of missing the appointment.<br><br>

**Show vs. no-show by receiving SMS or not**


![image](https://drive.google.com/uc?export=view&id=1FIK08V7yyx7XXLTI5mGUnx6z741XvefW)<br>

**Figure 8:**
**1.** SMS rates for people who make the appointment for the same day or within three days are meager - I also saw that the no-show rates are much lower in that time range.
If we interpret the SMS column as an indication of an SMS being sent, it makes sense that hospitals would have a rule/system to not send SMS to people whose appointments are close to the date the appointment was scheduled.
**2.** the second graph is for the distribution of absent patients by the waiting time and receiving SMS; we can see that approximately 50% of the absent patients who wait more than four days did not receive SMS.<br><br>


**Analyzing the probability of showing up for Age feature**<br>

![image](https://drive.google.com/uc?export=view&id=1r0jJ5b6N5Fck4TPuRZd-7dfGGe56gk5B)<br>


**Figure 9:** we can see here that there is a positive correlation between age and the show rate; older people tend to schedule long-term appointments and attend to them.<br><br>

**Analyzing the probability of showing up for waiting time features**<br>
![image](https://drive.google.com/uc?export=view&id=17zRG3GtqzI5q4btlmmtwVYr-5V0Qf3bg)<br>
**Figure 9:** There is no correlation between the waiting days and the showing up.<br><br>

**Patient by show vs. no show**<br>
![image](https://drive.google.com/uc?export=view&id=1PIg6eVnbgFJcNJKw3cEMmIgkIm_Ewh6h)<br>
**Figure 10:**<br>
- 	(external circle) we can see that approximately 39.1% of the patients have more than one appointment.
- 	(Inner circle)15.3% of the patients have prior appointments and were absent at least once.
- 	22.2% of the patients have more than one appointment and did not miss their appointments.
- 	On the other hand, 1.6% of the patients made more than one appointment, but they missed all the appointments.
- 	(external circle)60.9% of the patients have no prior appointments.
- 	49.9% of the patients have no prior appointments and come to their appointments.
- 	However, 11.4% of the patients have no prior appointments ( make just one appointment) and did not come to their appointments.<br><br>

**Features correlation**

Before machine learning, we must check if there is a correlation between the features. In the figure below, we can see that there is no high correlation between the features. (with 17 features)<br>
![image](https://drive.google.com/uc?export=view&id=1HwSkXHRb005xClveg8iKUXxwMe9Fhbj-)<br><br>
![image](https://drive.google.com/uc?export=view&id=1HwCJpdi-PUO5Via-ge7-iCTXpGqAeVBH-)<br><br>
---

### Machine learning <br>
#### Model selection and evaluation <br>
This is a binary classification problem, so that I will use the classification models. Features like the scheduled day and appointment day were split into the day of the month, month, and day of the week. Patient id, appointment id, and the neighborhood were dropped (because there are 81 neighborhoods and there will be many features, and it may be cause overfitting).

#### Step 1 : <br>

**The dataset was split into 80 % of the appointments, with a 20% test data set.**<br>

![image](https://drive.google.com/uc?export=view&id=1jtv4ASUT_kK4hUsMO0YJOrnZlPCJiUJF)<br><br>
**Figure 11**:<br>
Classification reports for the individual classifiers (with the test set), all the classifiers have approximately the same overall accuracy, precision, and recall.<br>
Using five cross-validation folds, the data was fitted on random forest, logistic regression, KNN, naïve Bayes, and tree classification with their default parameter. Then, the models were evaluated based on their accuracy, precision, recall,f1, and roc AUC score, as shown in figure 11 below.
The test set data performance with random forest results in a recall of 21% for the absent patients, a precision of 40% with an overall accuracy of 78%, and an f1 score of 0.28 for the no-show class. I tried to improve the results in step 2.<br><br>




**Figure 12**:<br>
![image](https://drive.google.com/uc?export=view&id=1o7RJyfPNelBRYvc5_uGaKqhkIEAyaU5M)<br><br>

From the results of the different models, we can see the results of precision, recall, f1, accuracy in the train, and validation set (average of 5 fold cross-validation).<br><br>
### Step 2: Class imbalance <br>

There is a Class Imbalance in the data set; the no-show appointments only represent 20.2% of the response variable, appointment status, as seen in the figure above. So, these classifiers may predict the patient who came to their appointments (0).
To improve the results of the models, I tried to balance the data, so I used the SMOTE algorithm.
By utilizing the SMOTE algorithm, "the minority class is over-sampled by creating synthetic examples rather than over-sampling, allowing the classifier to learn the feature/target better.
When evaluating the test data performance after using the SMOTE on the training data, the f1 score of the no show increased in all the classifiers, but it was still not good.<br><br>


![image](https://drive.google.com/uc?export=view&id=13Dwgt1NpldazpKmO003np82guZ_DNWy8)<br><br>
**Figure 13:** classification reports for the individual classifiers with balanced data(by SMOTE).<br><br>

![image](https://drive.google.com/uc?export=view&id=1o7RJyfPNelBRYvc5_uGaKqhkIEAyaU5M)<br><br>
**Figure 14:** The results of the different models after data balancing( with SMOTE) show the results of precision, recall, f1, accuracy in the train, and validation set. (Average of 5 cross-validations).<br><br>

### Step 3 :
In order to improve the results more, I have added two more features for the appointment history of the patient, one of them is for the total prior appointment and the second one is for the total missed appointment. So every time the patient makes a new appointment, the total prior appointment and the total missed appointments will appear beside the patient’s information, and it will be updated when he makes a new appointment.
Patient id is not a unique feature, so some patients make more than one appointment. I did not remove them. I just updated the total prior appointment, and the total missed an appointment for each patient when he makes a new appointment.
I also added the total diseases for each patient. There are 20 features now, and the train set is not balanced. It is still 23% no show and 77 % show.
I checked the accuracy with logistic regression, and I got 94%, precision of 86% for the show; there were also good results from the random forest model, as we can see in Figure (15) <br><br>

![image](https://drive.google.com/uc?export=view&id=1pFpDf0JGz0vk2qSwXT00BP9-2YDZKhzk)<br><br>


**Figure 15:** classification reports for the individual classifiers with the test set.<br>
I checked the accuracy of the train test and the validation set to check if there is overfitting. Unfortunately, there was overfitting in the random forest model, so  I chose the logistic regression model, it has 86% precision,82% recall,f1-score of 84% for the no show label, and 94% accuracy, and there was no overfitting; the results of the train (with five cross-validations) is the same as for the validation set, and there is no overfitting. 
we can the results of all the metrics in the figure below (average of 5 cross-validations)<br><br>

![image](https://drive.google.com/uc?export=view&id=1zdpW_HGbVlkUGb551Po5AJ9k9LdSS9HC)<br><br>


In the figure below, we can see the average validation f1 score with ten cross-validation folds.

![image](https://drive.google.com/uc?export=view&id=1qL1icVQebAl0_zxIfyQSVVN6MOBFCvgn)<br><br>

I also checked the ROC curve, and we can see that we have a good result from the roc graph, as we can see below, with an AUC of 96% <br><br>
![image](https://drive.google.com/uc?export=view&id=1_Tmw8avK3bfACDpqG46GYLc6tXsPPRT2)<br><br>

I also checked the feature importance by using the logistic regression model, and I find that the most important feature is the total prior appointments with a negative value which may predict more the patient who did not miss their appointments. Furthermore, the prior missed appointment with a high positive value predicts the absent patients, as shown in the figure below.<br><br>

![image](https://drive.google.com/uc?export=view&id=1MXooN_H23DqSAxs0rT_3hQXNSwm5noqb)<br><br>
**Figure 16:** feature importance in the logistic regression model.<br><br>

**Advantages of using logistic regression:**<br>
-	does not require high computation power
-	 easy to implement.
-	Easily interpretable.
-	It does not require the scaling of features. Logistic regression provides a probability score for observations.
---
### Conclusion :

In conclusion, it seems that no-shows can be predicted from patient information and appointment data. More information about the clinic’s location (e.g., transport accessibility), type of care sought (e.g., primary, specialist), and the patient (e.g., education, income) would likely improve the model. The model could also benefit from a cost-benefit analysis of possible intervention measures to achieve a balance of precision and recall that would make the most business sense.
-	Patients with a high number of previous No-Shows are more likely to No Show in future appointments.
-	 Appointments booked “Within 24 hours” are less likely to be No Shows as we can show from figure 7.
-	 Patients in different age groups exhibit different No-Show behaviors, as shown in figure 3 and figure 9.
-	 Longer waiting time, more patients will be absent from the appointments, as we can see from figure 7. So, again, this should be a point to be considered to ameliorate.
-	The neighborhood's location may affect the patients to decide whether they show up for their medical appointments; as shown in figure 6, some neighborhoods have a high rate of absent patients.
-	SMS could be a helpful way to remind patients of their appointments, and we can see that many patients did not receive an SMS, as we can see from figure 8.<br><br>

**Recommendations to improve the attendance:**<br>
-	 sending the SMS notification to every patient who made an appointment.
-	Trying to make the appointment as quickly as possible, limit to less than 15 days.
-	Call the patients who received the SMS and missed up their appointment.

 **Limitation:**<br>
-	We were given only a snapshot of complete data (from one month). Therefore, making exact predictions and analyses on snapshot data is difficult, and the analysis might not represent the actual data.
-	The Time details in the Appointment Day were missing, which would help us predict No Show of a patient.
-	The reason for the appointment and the consultation doctor specialization would have helped us a lot in making better analyses and predictions for the No Show of a patient.




