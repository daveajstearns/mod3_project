# Module 3 Project
### *Classification of Accident Severity*

## Table of Contents
1. Cleaning and preparation - `EDA_&_CLEANING.ipynb`
2. Statistical Testing - `Statistical Tests.ipynb`
3. KNN Modeling - `SMOTE Models.ipynb`
4. RandomForestClassifier Modeling - `mod3_randomforestclassifier.ipynb`
5. Maps - `mod3_maps.ipynb` **one map is contained in `EDA_&_CLEANING.ipynb`**
6. Images - 
      * `Visuals` contains images from KNN Modeling
      * `images_dave` contains images from RFC Modeling
7. Functions - `functions.py`
8. Final cleaned data set - `final_data.csv`

## Abstract
The methods used for this classification project are no different than any other. We spent roughly 80% of our actual working time cleaning and preparing the data for analysis and also for interpretability. This took a considerable dive into how the UK Department for Transport sets up these documents, and also took some time to understand their language as it is slightly different than what we are used to here in the United States. For example, one of the road types we came across was *Unclassified* which, at first glance, seems like a missing value. After further research, we saw that this actually meant a local road. In addition, a *slip road* is what we would call an on-ramp. There were certain nuances we had to overcome. In terms of results, can we classify whether an accident was minor, severe, or fatal? Both of our models ran **recall** and **F1** scores exceeding 83%. We chose **recall** as the primary metric because there is no reason to not overreact to a car crash. We would rather have authorities and Emergency Services be at the ready for a catastrophe even in the event of a misclassified minor fender bender.   

## Introduction
This project uses datasets supplied by data.gov.uk; the United Kingdom's open data effort. The purpose of this project is to build a model that can help predict whether a traffic accident is minor, severe, or fatal. The process used to achieve our results is defined below in our various notebooks regarding cleaning, interpretation, model building, and model evaluation.  
  
The idea for this project stemmed from thinking about the safety of our future roads and how ML and AI can benefit our society. That may sound complex; in layman's terms, we want to see if it is possible to quickly generate a label for a traffic incident to help first responders understand more about what they will encounter on the scene. We can think of our project as an additional piece to a comprehensive vehicle monitoring system(VMS)-one that can quickly read information about the occurrence-and send out an SOS beacon to local authorities with more information about what type of resources they may need. Down the road this may help to streamline the Emergency Care side of the accident, where instead of an ambulance rushing in to the loading bay and workers scramble to find a bed, OR, or doctor, the situation will be running smoothly in the background so the first responders, nurses, and doctors are 100% in sync with the task at hand without having to do any menial tasks.  

You might be asking yourself, *how would this work?* **Ask and you shall be answered!** Let's imagine this event: a car crash on Route 4, and it is during the CoVid-19 days (ironically spoken about in retrospect). The entire coordination of admitting patients into the ER especially with all of these restrictions is probably a pretty tough juggle of factors. How can we make this better, faster, safer?  

Our VMS can read informatin about where the car is on the road, where it has been impacted, and a host of other information regarding acceleration data. In addition, the car knows the owner of the car, it knows almost too much about you. The car "knows" your financial data, the car "knows" where you live or at least where you spend most of your time. This might sound farfetched, but think about what your phone already knows about you. If our VMS can read information coming from a transpiring accident in real time, then it is possible to predict how bad the accident is for the driver. Sometimes big crashes end up with lucky breaks and the driver is fine. Sometimes a small bump can cause a severe concussion. With the information collected we can do a few really important things simultaneously:
1. Determine the **severity** of the accident
2. Alert authorities to the accident and provide detailed location information
3. Notify the closest hospital of a pending admittance

Determining the severity is the first step in this process. This can aid in identifying which hospital to contact. Accident was minor? Maybe we don't need a hospital with a helipad or advanced trauma department. Accident was multi-car, multi-casualty, and violent? Let's contact the closest hospitals with advanced trauma departments and plenty of beds. While it isn't the only step happening at once, it determines which hospital the system chooses to select the driver's (and passengers') admittance to. **At the same time**, we're alerting the authorities to the exact coordinates of the scene and providing detailed information to help them determine how to attack the situation. Finally, the VMS is selecting the hospital for the occupants and preparing their triage report for the hospital. See, this can be extremely helpful.  

Another package we would like to add in the future would be a healthcare app that works in sync with this information, and can select the specific room for the patient, select the nurses and doctors, and initiate those communication corridors. That is how our system will work best.

## Procedure

First, we gathered data from the UK Department for Transport regarding accidents. We chose two out of the three available datasets for 2018. We had data on accidents and the vehicles in those accidents. To merge these two datasets, they provided an accident identifier that allowed us to merge the two. In fact, we noticed that we gained some data back when we merged, which we were happy to see.  

Next, we began reviewing the data and understanding it. There was a key provided that helped us interpret the meanings of the variables. Many of the values were in numerical form but not continuous, rather, signifying some category or event. This was the most labor intensive part of the project. We had over 45 columns, and almost all of them needed review. Some were dropped due to redundancy or unnecessary information. Others were combed through carefully, examining the distributions, at times examining the statistical relationships, and ultimately transformed. You can view the final dataset in the repo by downloading `final_data.csv`.   

Finally, we began to run our models. We chose to try KNN and RandomForestClassifier, and combined them with both cross validation and GridSearchCV. In addition, we performed a Recursive Feature Elimination (RFECV) on the dataset used for RandomForestClassifier (KNN does not support this). This allowed further refinement of the dataset prior to moving into determining the winning model.  

As an extra, the reality of a large class imbalance was present in our data. Our dataset had a minor imbalance between minor and severe, and a much more pronounced class imbalance between minor and fatal. We had to run some statistical tests on this phenomena to understand its presence better. Ultimately, we chose to use SMOTE to correct for the class imbalances. It proved to be a good move and benefitted our models.

## Results



## Discussion

## Conclusion





## References
[Dataset location](https://data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data)
