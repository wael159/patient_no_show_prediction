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

**Figure 9:** we can see here that there is a positive correlation between age and the show rate; older people1r0jJ5b6N5Fck4TPuRZd-7dfGGe56gk5B tend to schedule long-term appointments and attend to them.<br><br>

**Analyzing the probability of showing up for waiting time features**<br>
![image](https://drive.google.com/uc?export=view&id=17zRG3GtqzI5q4btlmmtwVYr-5V0Qf3bg)<br>
There is no correlation between the waiting days and the showing up.<br><br>

**Patient by show vs. no show**<br>
![image](https://drive.google.com/uc?export=view&id=1PIg6eVnbgFJcNJKw3cEMmIgkIm_Ewh6h)<br>
**Figure 10:**<br>
- 	(external circle) we can see that approximately 39.1% of the patients have more than one appointment.
- 	(Inner circle)15.3% of the patients have prior appointments and were absent at least once.
- 	22.2% of the patients have more than one appointment and did not miss their appointments.
- 	On the other hand, 1.6% of the patients made more than one appointment, but they missed all the appointments.
- 	(external circle)60.9% of the patients have no prior appointments.
- 	49.9% of the patients have no prior appointments and come to their appointments.
- 	However, 11.4% of the patients have no prior appointments ( make just one appointment) and did not come to their appointments.
