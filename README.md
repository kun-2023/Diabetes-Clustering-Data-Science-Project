# Diabetes Clustering Data Science Project

## Case description
Here are 10000 diabetic patients’ data on certain health, physical, and biological metrics such as age, waist, blood pressure, cholesterols and so on. The goal here is to cluster those patients, so we can find patterns or similarities among patients. Therefore, doctors could tailor each cluster for recommendations and possible ways to reduce the severity of the diabetes. 
## Executive Summary
Diabetes can affect people who are overweight and underweight, who have a healthy life style with no smoking habits, no alcohol consumption or not. However, according to the data, no smoking could prevent an enlarged waist circumference. High level of physical activities would lead to a low level of blood pressure and a low level of cholesterols. The datasets were clustered in to 9 clusters in terms of physical activity level and smoking status. All those clusters have similar mean for each health metrics to one another.  
## Datasets descriptions
There are 10000 rows and 20 features. And there are over 3000 null values in the alcohol consumption column. 

![image](https://github.com/user-attachments/assets/47b447e1-e2e9-4a45-9b2e-06ff6849b8f6)


  
## Data Cleaning
To fill in the null values in Alcohol_Consumption feature, I decided to replace the null values with the mode values in the column. That is “Moderate”. Also, I decided to turn binary categorical features into binary numerical features with 0s and 1s.
## Part 1: DEA Findings
1.	Most the features are evenly distributed. However, for BMI and HbA1c, some values are distributed more than other values in the same column. It could mean for the diabetics’ people, they come in all shape and sizes. All their healthy metrics look very similar regardless to their physical level and smoking status.

![image](https://github.com/user-attachments/assets/5a4f0236-8a7f-433e-ace4-032d0dee4c34)


 

2.	All those features are not correlated with one another.
![image](https://github.com/user-attachments/assets/3bd54206-1925-41da-a6f9-0a1005956611)

 
3.	For categorical features such as ethnicity, physical activity level, and smoking status. They are also distributed evenly.
![image](https://github.com/user-attachments/assets/aa4b02ed-9b1c-4111-854d-1fee3a33610a)
 

4.	Box distribution between numerical features and categorical features. Asians have lower BMI, but has a higher blood pressure systolic. Hispanic has a higher waist circumference and a higher HbA1c. Black people also has a higher blood pressure Systolic. People with a low activity level have a higher BMI and lower Cholesterol. Current smokers have a higher blood pressure diastolic.

 ![image](https://github.com/user-attachments/assets/72fbeb3f-c58a-4ba2-8337-c4e7f2ed4531)
![image](https://github.com/user-attachments/assets/f250dc94-acb2-4e75-8258-ed476031d249)


 
5.	KDE plot findings. People who don’t smoke have a lower BMI and a smaller waist circumference. And people with high level of activities tend to enjoy a low level of cholesterol and low blood pressures. The insights here is smoke would make people gain weight. Doing physical activities will lower cholesterols and blood pressures. 
  

![image](https://github.com/user-attachments/assets/69311efe-dcac-4af8-9e5c-cb3e3eaa577f)

![image](https://github.com/user-attachments/assets/dfb94d61-e51a-470a-855c-1f921358263d)




 

## Part 2 Machine Learning Model with KMeans Clustering. Round one
1.	Build KMeans clustering models with clusters set between 2 and 15 while calculating silhouette scores for each cluster. Silhouette scores would help identify the best number of clusters. Cluster 4 and 12 have the highest silhouette scores. 

![image](https://github.com/user-attachments/assets/d71d11b2-420d-41fe-a934-144533f657ba)



 

2.	Building a 4-cluster KMeans model. Applied a PCA with two components for visualization purposes. It turns out the cluster was based on ethnicities. It’s shown by the PCA component table and PCA scatter plot. Therefore, it’s invalid. And A new model without Ethnicity shall be retrained.
   
![image](https://github.com/user-attachments/assets/7be71d6a-e432-4fdd-90df-f65308335b24)

## Part 2 Machine Learning Model with KMeans Clustering. Round Two.
1.	Build a series of machine learning kmeans cluster models with clusters between 2 and 15 with their silhouette scores. Cluster 3 and cluster 9 have the highest silhouette scores. Therefore, Kmeans models with clusters of 3 and 9 will be trained.
![image](https://github.com/user-attachments/assets/0c406551-5a2f-4758-af59-a9b63997fb0e)


2.	K=3. This model was clustered by Physical_Activity_Level. Cluster 0: High Level Physical Activity. Cluster 1: Moderate Level Physical Activity. Cluster 2: Low Level Physical Activity. As the PCA scatterplot shows, it clearly has 9 small clusters as the model divide it into 3 clusters. Clearly, 9 cluster is much more appropriate.
 
![image](https://github.com/user-attachments/assets/f20a8c07-34fa-48f1-a922-0a9d798b285a)


3.	K=9. This time the model clustered the datasets based on physical activity level and smoking status.  Cluster 0: Moderate Physical, Current Smoker. Cluster 1: High Physical, Never Smoker.  Cluster 2: Low Physical, Current Smoker. Cluster 3: Moderate Physical, Never Smoker. Cluster 4: High Physical, Former Smoker. Cluster 5: Low Physical, Never Smoker. Cluster 6: High Physical, Current Smoker. Cluster 7: Low Physical, Former Smoker. Cluster 8: Moderate Physical, Former Smoker. The PCA visualization had made it clearly this time. Nine is the right cluster. 

![image](https://github.com/user-attachments/assets/7d4d84d2-8e80-426a-9acd-f2474118f8e4)

 
4.	DEA of the 9 clusters. Most of features would have a similar mean except alcohol consumption, family history of diabetes and previous gestational diabetes. Each cluster has distinctively different rate in those features. 
![image](https://github.com/user-attachments/assets/46115222-9e2f-42c8-90be-6f6708b04bed)
 

## Part 3: Conclusion & Recommendations
* Many never smokers and people with high or moderate physical levels had become diabetic. Most of the metrics have similar distribution for each cluster. However, no smoking and high physical activities do have a positive impact on weights, choleterols and blood pressures.
* For people with low physical activity level and current smokers such as cluster 2. They need to smoke less and start do some exercise.
* For people with low physical activity such as cluster 7 and 5, they need to beef up their activities.
* For people who smoke currently such as cluster 0 and 6, they need to cut back smoking.
* For people with lots of alcohol consumptions such as cluster 3, 6, and 7, they need to cut it back.
